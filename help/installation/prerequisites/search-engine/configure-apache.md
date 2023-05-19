---
title: Configurare Apache per il motore di ricerca
description: Per configurare un motore di ricerca con il server web Apache per le installazioni locali di Adobe Commerce e Magenti Open Source, segui la procedura riportata di seguito.
exl-id: b35c95a7-0c00-48e5-b37d-7c9e17feebec
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '651'
ht-degree: 0%

---

# Configurare Apache per il motore di ricerca

{{$include /help/_includes/web-server-communication.md}}

## Configurare un proxy

>[!NOTE]
>
>Il supporto di OpenSearch è stato aggiunto nella versione 2.4.4. OpenSearch è un fork di Elasticsearch compatibile. Consulta [Migra Elasticsearch a OpenSearch](../../../upgrade/prepare/opensearch-migration.md) per ulteriori informazioni.

Questa sezione illustra come configurare Apache come *non sicuro* in modo che Adobe Commerce possa utilizzare un motore di ricerca in esecuzione su questo server. Questa sezione non tratta la configurazione dell’autenticazione HTTP Basic; questo argomento è trattato in [Comunicazione sicura con Apache](#secure-communication-with-apache).

>[!NOTE]
>
>Il motivo per cui il proxy non è protetto in questo esempio è che è più facile impostare e verificare. È possibile utilizzare TLS con questo proxy. Se lo desideri, assicurati di aggiungere le informazioni proxy alla configurazione host virtuale protetta.

### Configurare un proxy per Apache 2.4

Questa sezione illustra come configurare un proxy utilizzando un host virtuale.

1. Abilita `mod_proxy` come segue:

   ```bash
   a2enmod proxy_http
   ```

1. Utilizza un editor di testo per aprire `/etc/apache2/sites-available/000-default.conf`
1. Aggiungi la seguente direttiva nella parte superiore del file:

   ```conf
   Listen 8080
   ```

1. Aggiungi quanto segue nella parte inferiore del file:

   ```conf
   <VirtualHost *:8080>
       ProxyPass "/" "http://localhost:9200/"
       ProxyPassReverse "/" "http://localhost:9200/"
   </VirtualHost>
   ```

1. Riavvia Apache:

   ```bash
   service apache2 restart
   ```

1. Verificare il funzionamento del proxy immettendo il comando seguente:

   ```bash
   curl -i http://localhost:<proxy port>/_cluster/health
   ```

   Ad esempio, se utilizzi Elasticsearch e il tuo proxy utilizza la porta 8080:

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

## Comunicazione sicura con Apache

Questa sezione illustra come proteggere la comunicazione tra Apache e il motore di ricerca utilizzando [HTTP Basic](https://datatracker.ietf.org/doc/html/rfc2617) autenticazione con Apache. Per ulteriori opzioni, consulta una delle risorse seguenti:

* [Tutorial sull’autenticazione e l’autorizzazione di Apache 2.4](https://httpd.apache.org/docs/2.4/howto/auth.html)

Vedere una delle sezioni seguenti:

* [Creare un file di password](#create-a-password)
* [Configurare l&#39;host virtuale protetto](#secure-communication-with-apache)

### Creare una password

Per motivi di sicurezza, è possibile individuare il file della password in qualsiasi punto, ad eccezione della directory principale dei documenti del server Web. In questo esempio viene illustrato come memorizzare il file della password in una nuova directory.

#### Se necessario, installare htpasswd

Innanzitutto, verifica di disporre di Apache `htpasswd` L&#39;utilità viene installata come segue:

1. Immetti il seguente comando per determinare se `htpasswd` è già installato:

   ```bash
   which htpasswd
   ```

   Se viene visualizzato un percorso, questo viene installato; se il comando non restituisce alcun output, `htpasswd` non è installato.

1. Se necessario, installare `htpasswd`:

   * Ubuntu: `apt-get -y install apache2-utils`
   * CentOS: `yum -y install httpd-tools`

#### Creare un file di password

Immetti i seguenti comandi come utente con `root` privilegi:

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.<password file name> <username>
```

Dove

* `<username>` può essere:

   * Configurazione di cron: l’utente del server web o un altro utente.

   In questo esempio, utilizziamo l’utente del server web, ma la scelta dell’utente dipende da te.

   * Elasticsearch di configurazione: l’utente è denominato `magento_elasticsearch` in questo esempio


* `<password file name>` deve essere un file nascosto (inizia con `.`) e deve riflettere il nome dell&#39;utente. Per ulteriori informazioni, consulta gli esempi più avanti in questa sezione.

Seguire le istruzioni visualizzate per creare una password per l&#39;utente.

#### Esempi

**Esempio 1: cron**
Devi impostare l’autenticazione per un solo utente per cron; in questo esempio, utilizziamo l’utente del server web. Per creare un file di password per l&#39;utente del server Web, immettere i seguenti comandi:

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd apache
```

**Esempio 2: Elasticsearch**
Devi impostare l’autenticazione per due utenti: uno con accesso a nginx e uno con accesso a Elasticsearch. Per creare file di password per questi utenti, immetti i seguenti comandi:

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/.htpasswd_elasticsearch magento_elasticsearch
```

#### Aggiungi altri utenti

Per aggiungere un altro utente al file della password, immettere il comando seguente come utente con `root` privilegi:

```bash
htpasswd /usr/local/apache/password/.htpasswd <username>
```

### Comunicazione sicura con Apache

Questa sezione illustra come impostare [Autenticazione HTTP Basic](https://httpd.apache.org/docs/2.2/howto/auth.html). L’utilizzo congiunto dell’autenticazione TLS e HTTP Basic impedisce a chiunque di intercettare le comunicazioni con Elasticsearch, OpenSearch o con il server dell’applicazione.

Questa sezione illustra come specificare chi può accedere al server Apache.

1. Utilizza un editor di testo per aggiungere i seguenti contenuti all’host virtuale protetto.

   * Apache 2.4: Modifica `/etc/apache2/sites-available/default-ssl.conf`

   ```conf
   <Proxy *>
       Order deny,allow
       Allow from all
   
       AuthType Basic
       AuthName "Elasticsearch Server" # or OpenSearch Server
       AuthBasicProvider file
       AuthUserFile /usr/local/apache/password/.htpasswd_elasticsearch
       Require valid-user
   
     # This allows OPTIONS-requests without authorization
     <LimitExcept OPTIONS>
           Require valid-user
     </LimitExcept>
   </Proxy>
   ```

1. Se hai aggiunto il precedente all’host virtuale protetto, rimuovi `Listen 8080` e `<VirtualHost *:8080>` direttive aggiunte in precedenza all&#39;host virtuale non protetto.

1. Salva le modifiche, esci dall’editor di testo e riavvia Apache:

   * CentOS: `service httpd restart`
   * Ubuntu: `service apache2 restart`

#### Verifica

{{$include /help/_includes/verify-secure-communication.md}}
