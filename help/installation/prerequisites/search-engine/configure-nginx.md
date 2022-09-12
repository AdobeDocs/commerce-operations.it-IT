---
title: Configura Nginx per il motore di ricerca
description: Segui questi passaggi per configurare un motore di ricerca con il server web Nginx per le installazioni on-premise di Adobe Commerce e Magenti Open Source.
source-git-commit: a0f2c6480edcda5540ca83835580d18f401de72f
workflow-type: tm+mt
source-wordcount: '652'
ht-degree: 0%

---


# Configura Nginx per il motore di ricerca

{{$include /help/_includes/web-server-communication.md}}

## Configurare un proxy

>[!NOTE]
>
>Il supporto OpenSearch è stato aggiunto in 2.4.4. OpenSearch è un fork di Elasticsearch compatibile. Tutte le istruzioni per configurare l&#39;Elasticsearch 7 si applicano a OpenSearch. Vedi [Migrazione di Elasticsearch a OpenSearch](../../../upgrade/prepare/opensearch-migration.md) per ulteriori informazioni.

Questa sezione illustra come configurare l’allegato come *non protetto* in modo che Adobe Commerce o Magento Open Source possano utilizzare un motore di ricerca in esecuzione su questo server. In questa sezione non viene discussa la configurazione dell&#39;autenticazione HTTP Basic; di cui all&#39; [Comunicazione sicura con l&#39;allegato](#secure-communication-with-nginx).

>[!NOTE]
>
>Il motivo per cui il proxy non è protetto in questo esempio è che è più semplice configurarlo e verificarlo. Puoi utilizzare TLS con questo proxy, se lo desideri; a questo scopo, assicurati di aggiungere le informazioni proxy alla configurazione del blocco del server protetto.

### Specificare file di configurazione aggiuntivi nella configurazione globale

Assicurati che il tuo globale `/etc/nginx/nginx.conf` contiene la riga seguente in modo da caricare gli altri file di configurazione descritti nelle sezioni seguenti:

```conf
include /etc/nginx/conf.d/*.conf;
```

### Imposta l&#39;allegato come proxy

Questa sezione illustra come specificare gli utenti che possono accedere al [nginx](https://glossary.magento.com/nginx) server.

1. Utilizzare un editor di testo per creare un file `/etc/nginx/conf.d/magento_es_auth.conf` con i seguenti contenuti:

   ```conf
   server {
      listen 8080;
      location /_cluster/health {
         proxy_pass http://localhost:9200/_cluster/health;
      }
   }
   ```

1. Riavvia l&#39;indice:

   ```bash
   service nginx restart
   ```

1. Verifica il funzionamento del proxy immettendo il seguente comando:

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

## Comunicazione sicura con l&#39;allegato

Questa sezione illustra come configurare [Autenticazione HTTP Basic](https://nginx.org/en/docs/http/ngx_http_auth_basic_module.html) con il proxy sicuro. L’utilizzo dell’autenticazione TLS e HTTP Basic impedisce a chiunque di intercettare le comunicazioni con Elasticsearch o con il server Adobe Commerce o Magenti Open Source.

Poiché nginx supporta in modo nativo l’autenticazione HTTP Basic, è consigliabile eseguirla, ad esempio [Autenticazione digest](https://www.nginx.com/resources/wiki/modules/auth_digest/), che non è consigliato in produzione.

Risorse aggiuntive:

* [Come impostare l&#39;autenticazione tramite password con Nginx su Ubuntu 14.04 (Oceano Digitale)](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
* [Autenticazione HTTP di base con nonx (HowtoForge)](https://www.howtoforge.com/basic-http-authentication-with-nginx)
* [Esempi di configurazioni Nginx per Elasticsearch](https://gist.github.com/karmi/b0a9b4c111ed3023a52d)

Per ulteriori informazioni, consulta le sezioni seguenti:

* [Creare password](#create-a-password)
* [Imposta l&#39;accesso all&#39;allegato](#set-up-access-to-nginx)
* [Configurare un contesto limitato per il motore di ricerca](#set-up-a-restricted-context-for-the-search-engine)
* [Verifica che la comunicazione sia sicura](#secure-communication-with-nginx)

### Creare una password

Si consiglia di utilizzare Apache `htpasswd` per codificare le password di un utente con accesso ad Elasticsearch o OpenSearch (denominato `magento_elasticsearch` in questo esempio).

Per creare una password:

1. Immetti il seguente comando per determinare se `htpasswd` è già installato:

   ```bash
   which htpasswd
   ```

   Se viene visualizzato un percorso, questo viene installato; se il comando non restituisce alcun output, `htpasswd` non è installato.

1. Se necessario, installa `htpasswd`:

   * Ubuntu: `apt-get -y install apache2-utils`
   * CentOS: `yum -y install httpd-tools`

1. Crea un `/etc/nginx/passwd` directory in cui memorizzare le password:

   ```bash
   mkdir -p /etc/nginx/passwd
   ```

   ```bash
   htpasswd -c /etc/nginx/passwd/.<filename> <username>
   ```

   >[!WARNING]
   >
   >Per motivi di sicurezza, `<filename>` devono essere nascosti; cioè, deve iniziare con un punto.

1. *(Facoltativo).* Per aggiungere un altro utente al file della password, immetti lo stesso comando senza `-c` (crea) opzione:

   ```bash
   htpasswd /etc/nginx/passwd/.<filename> <username>
   ```

1. Verifica che il contenuto di `/etc/nginx/passwd` è corretta.

### Imposta l&#39;accesso all&#39;allegato

Questa sezione illustra come specificare gli utenti che possono accedere al server nginx.

>[!WARNING]
>
>L’esempio mostrato è per un *non protetto* proxy Per utilizzare un proxy sicuro, aggiungi i seguenti contenuti (ad eccezione della porta di ascolto) al blocco del server protetto.

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
>La porta di ascolto del motore di ricerca mostrata nell’esempio precedente sono solo esempi. Per motivi di sicurezza, è consigliabile utilizzare una porta di ascolto non predefinita.

### Configurare un contesto limitato per il motore di ricerca

Questa sezione illustra come specificare gli utenti che possono accedere al server del motore di ricerca.

1. Immetti il seguente comando per creare una directory in cui memorizzare la configurazione di autenticazione:

   ```bash
   mkdir /etc/nginx/auth/
   ```

1. Utilizzare un editor di testo per creare un file `/etc/nginx/auth/magento_elasticsearch.conf` con i seguenti contenuti:

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

1. Se imposti un proxy protetto, elimina `/etc/nginx/conf.d/magento_es_auth.conf`.
1. Riavvia l&#39;allegato e continua con la sezione successiva:

   ```bash
   service nginx restart
   ```

#### Verifica

{{$include /help/_includes/verify-secure-communication.md}}
