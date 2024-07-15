---
title: Configurare Nginx per il motore di ricerca
description: Segui questi passaggi per configurare un motore di ricerca con il server web Nginx per le installazioni locali di Adobe Commerce.
feature: Install, Search
exl-id: 8d2f8695-e30a-4acc-bba3-d122212b0a53
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '603'
ht-degree: 0%

---

# Configurare Nginx per il motore di ricerca

{{$include /help/_includes/web-server-communication.md}}

## Configurare un proxy

>[!NOTE]
>
>Il supporto di OpenSearch è stato aggiunto nella versione 2.4.4. OpenSearch è un fork di Elasticsearch compatibile. Per ulteriori informazioni, vedere [Migrare l&#39;Elasticsearch a OpenSearch](../../../upgrade/prepare/opensearch-migration.md).

In questa sezione viene illustrato come configurare nginx come proxy *unsecure* in modo che Adobe Commerce possa utilizzare un motore di ricerca in esecuzione su questo server. In questa sezione non viene illustrata la configurazione dell&#39;autenticazione HTTP Basic, argomento trattato in [Comunicazione sicura con nginx](#secure-communication-with-nginx).

>[!NOTE]
>
>Il motivo per cui il proxy non è protetto in questo esempio è che è più facile impostare e verificare. Puoi utilizzare TLS con questo proxy se lo desideri; a questo scopo, assicurati di aggiungere le informazioni proxy alla configurazione del blocco server protetto.

### Specificare file di configurazione aggiuntivi nella configurazione globale

Verificare che il file `/etc/nginx/nginx.conf` globale contenga la riga seguente in modo da caricare gli altri file di configurazione descritti nelle sezioni seguenti:

```conf
include /etc/nginx/conf.d/*.conf;
```

### Configurare nginx come proxy

Questa sezione illustra come specificare chi può accedere al server nginx.

1. Utilizzare un editor di testo per creare un file `/etc/nginx/conf.d/magento_es_auth.conf` con il contenuto seguente:

   ```conf
   server {
      listen 8080;
      location /_cluster/health {
         proxy_pass http://localhost:9200/_cluster/health;
      }
   }
   ```

1. Inginx di riavvio:

   ```bash
   service nginx restart
   ```

1. Verificare il funzionamento del proxy immettendo il comando seguente:

   ```bash
   curl -i http://localhost:<proxy port>/_cluster/health
   ```

   Ad esempio, se il proxy utilizza la porta 8080:

   ```bash
   curl -i http://localhost:8080/_cluster/health
   ```

   Messaggi simili alla seguente visualizzazione per indicare il successo:

   ```terminal
   HTTP/1.1 200 OK
   Date: Tue, 23 Feb 2019 20:38:03 GMT
   Content-Type: application/json; charset=UTF-8
   Content-Length: 389
   Connection: keep-alive
   
   {"cluster_name":"elasticsearch","status":"yellow","timed_out":false,"number_of_nodes":1,"number_of_data_nodes":1,"active_primary_shards":5,"active_shards":5,"relocating_shards":0,"initializing_shards":0,"unassigned_shards":5,"delayed_unassigned_shards":0,"number_of_pending_tasks":0,"number_of_in_flight_fetch":0,"task_max_waiting_in_queue_millis":0,"active_shards_percent_as_number":50.0}
   ```

## Comunicazione sicura con nginx

In questa sezione viene illustrato come configurare l&#39;autenticazione di base HTTP [HTTP](https://nginx.org/en/docs/http/ngx_http_auth_basic_module.html) con il proxy protetto. L’utilizzo congiunto dell’autenticazione TLS e HTTP Basic impedisce a chiunque di intercettare le comunicazioni con Elasticsearch, OpenSearch o con il server dell’applicazione.

Poiché nginx supporta in modo nativo l&#39;autenticazione HTTP Basic, è consigliabile sostituirla, ad esempio, con [Autenticazione digest](https://www.nginx.com/resources/wiki/modules/auth_digest/), che non è consigliata in produzione.

Risorse aggiuntive:

* [Impostare l&#39;autenticazione tramite password con Nginx su Ubuntu 14.04 (Oceano digitale)](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
* [Autenticazione HTTP Di Base Con Nginx (HowtoForge)](https://www.howtoforge.com/basic-http-authentication-with-nginx)
* [Esempio di configurazioni Nginx per Elasticsearch](https://gist.github.com/karmi/b0a9b4c111ed3023a52d)

Per ulteriori informazioni, consulta le sezioni seguenti:

* [Creare le password](#create-a-password)
* [Configurare l’accesso a nginx](#set-up-access-to-nginx)
* [Impostare un contesto limitato per il motore di ricerca](#set-up-a-restricted-context-for-the-search-engine)
* [Verificare che la comunicazione sia sicura](#secure-communication-with-nginx)

### Creare una password

È consigliabile utilizzare il comando Apache `htpasswd` per codificare le password per un utente con accesso a Elasticsearch o OpenSearch (denominato `magento_elasticsearch` in questo ).

Per creare una password:

1. Immettere il comando seguente per determinare se `htpasswd` è già installato:

   ```bash
   which htpasswd
   ```

   Se viene visualizzato un percorso, questo verrà installato. Se il comando non restituisce alcun output, `htpasswd` non verrà installato.

1. Se necessario, installare `htpasswd`:

   * Ubuntu: `apt-get -y install apache2-utils`
   * CentOS: `yum -y install httpd-tools`

1. Creare una directory `/etc/nginx/passwd` per archiviare le password:

   ```bash
   mkdir -p /etc/nginx/passwd
   ```

   ```bash
   htpasswd -c /etc/nginx/passwd/.<filename> <username>
   ```

   >[!WARNING]
   >
   >Per motivi di sicurezza, `<filename>` deve essere nascosto, ovvero deve iniziare con un punto.

1. *(facoltativo).* Per aggiungere un altro utente al file della password, immettere lo stesso comando senza l&#39;opzione `-c` (crea):

   ```bash
   htpasswd /etc/nginx/passwd/.<filename> <username>
   ```

1. Verificare che il contenuto di `/etc/nginx/passwd` sia corretto.

### Configurare l’accesso a nginx

Questa sezione illustra come specificare chi può accedere al server nginx.

>[!WARNING]
>
>L&#39;esempio mostrato è per un proxy *unsecure*. Per utilizzare un proxy protetto, aggiungere i seguenti contenuti (ad eccezione della porta di ascolto) al blocco del server protetto.

Utilizza un editor di testo per modificare `/etc/nginx/conf.d/magento_es_auth.conf` (non protetto) o il blocco del server protetto con i seguenti contenuti:

```conf
server {
  listen 8080;
  server_name 127.0.0.1;

  location / {
   limit_except HEAD {
      auth_basic "Restricted";
      auth_basic_user_file  /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   }
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  }

  location /_aliases {
   auth_basic "Restricted";
   auth_basic_user_file  /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
  }

  include /etc/nginx/auth/*.conf;
}
```

>[!NOTE]
>
>La porta di ascolto del motore di ricerca mostrata nell&#39;esempio precedente è solo un esempio. Per motivi di sicurezza, è consigliabile utilizzare una porta di ascolto non predefinita.

### Impostare un contesto limitato per il motore di ricerca

Questa sezione illustra come specificare chi può accedere al server del motore di ricerca.

1. Immetti il seguente comando per creare una directory in cui memorizzare la configurazione di autenticazione:

   ```bash
   mkdir /etc/nginx/auth/
   ```

1. Utilizzare un editor di testo per creare un file `/etc/nginx/auth/magento_elasticsearch.conf` con il contenuto seguente:

   ```conf
   location /elasticsearch {
   auth_basic "Restricted - elasticsearch";
   auth_basic_user_file /etc/nginx/passwd/.htpasswd_magento_elasticsearch;
   
   proxy_pass http://127.0.0.1:9200;
   proxy_redirect off;
   proxy_set_header Host $host;
   proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
   }
   ```

1. Se si imposta un proxy protetto, eliminare `/etc/nginx/conf.d/magento_es_auth.conf`.
1. Riavvia nginx e continua con la sezione successiva:

   ```bash
   service nginx restart
   ```

#### Verifica

{{$include /help/_includes/verify-secure-communication.md}}
