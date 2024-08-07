---
title: Cron PHP sicuro
description: Limita gli utenti che possono eseguire il file cron.php in un browser.
feature: Configuration, Security
exl-id: c81fcab2-1ee3-4ec7-a300-0a416db98614
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '924'
ht-degree: 1%

---

# Cron PHP sicuro

In questo argomento viene illustrata la protezione di `pub/cron.php` per impedirne l&#39;utilizzo in un exploit dannoso. Se non proteggi cron, qualsiasi utente potrebbe potenzialmente eseguire cron per attaccare l’applicazione Commerce.

Il processo cron esegue diverse attività pianificate ed è una parte fondamentale della configurazione del Commerce. Le attività pianificate includono, tra l&#39;altro:

- Reindicizzazione
- Generazione di e-mail
- Generazione di newsletter
- Generazione di Sitemap

>[!INFO]
>
>Fare riferimento a [Configurare ed eseguire cron](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) per ulteriori informazioni sui gruppi cron.

È possibile eseguire un processo cron nei modi seguenti:

- Utilizzo del comando [`magento cron:run`](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) dalla riga di comando o in una scheda cronologica
- Accesso a `pub/cron.php?[group=<name>]` in un browser Web

>[!INFO]
>
>Non è necessario eseguire alcuna operazione se si utilizza il comando [`magento cron:run`](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) per eseguire cron perché utilizza un processo diverso già protetto.

## Cron sicuro con Apache

Questa sezione illustra come proteggere il cron utilizzando l’autenticazione HTTP Basic con Apache. Queste istruzioni sono basate su Apache 2.2 con CentOS 6. Per ulteriori informazioni, consulta una delle risorse seguenti:

- [Esercitazione di autenticazione e autorizzazione di Apache 2.2](https://httpd.apache.org/docs/2.2/howto/auth.html)
- [Esercitazione di autenticazione e autorizzazione di Apache 2.4](https://httpd.apache.org/docs/2.4/howto/auth.html)

### Creare un file di password

Per motivi di sicurezza, è possibile individuare il file della password in qualsiasi punto, ad eccezione della directory principale dei documenti del server Web. In questo esempio, il file della password viene archiviato in una nuova directory.

Immettere i seguenti comandi come utente con privilegi `root`:

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/passwords <username>
```

Dove `<username>` può essere l&#39;utente del server Web o un altro utente. In questo esempio, utilizziamo l’utente del server web, ma la scelta dell’utente dipende da te.

Seguire le istruzioni visualizzate per creare una password per l&#39;utente.

Per aggiungere un altro utente al file della password, immettere il comando seguente come utente con privilegi `root`:

```bash
htpasswd /usr/local/apache/password/passwords <username>
```

### Aggiungere utenti per creare un gruppo cron autorizzato (facoltativo)

Per consentire l&#39;esecuzione di cron da parte di più utenti, aggiungerli al file della password, incluso un file di gruppo.

Per aggiungere un altro utente al file password:

```bash
htpasswd /usr/local/apache/password/passwords <username>
```

Per creare un gruppo autorizzato, creare un file di gruppo in qualsiasi punto all&#39;esterno della docroot del server Web. Il file di gruppo specifica il nome del gruppo e gli utenti del gruppo. In questo esempio, il nome del gruppo è `MagentoCronGroup`.

```bash
vim /usr/local/apache/password/group
```

Contenuto del file:

```text
MagentoCronGroup: <username1> ... <usernameN>
```

### Cron protetto in `.htaccess`

Per proteggere cron nel file `.htaccess`:

1. Accedi al server Commerce come proprietario del file system o passa a tale proprietario.
1. Apri `<magento_root>/pub/.htaccess` in un editor di testo.

   Poiché `cron.php` si trova nella directory `pub`, modificare solo `.htaccess`.

1. _Accesso Cron per uno o più utenti._ Sostituisci la direttiva `<Files cron.php>` esistente con quanto segue:

   ```conf
   <Files cron.php>
      AuthType Basic
      AuthName "Cron Authentication"
      AuthUserFile /usr/local/apache/password/passwords
      Require valid-user
   </Files>
   ```

1. _Accesso al controllo per un gruppo._ Sostituisci la direttiva `<Files cron.php>` esistente con quanto segue:

   ```conf
   <Files cron.php>
      AuthType Basic
      AuthName "Cron Authentication"
      AuthUserFile /usr/local/apache/password/passwords
      AuthGroupFile <path to optional group file>
      Require group <name>
   </Files>
   ```

1. Salvare le modifiche apportate a `.htaccess` e uscire dall&#39;editor di testo.
1. Continuare con [Verificare che cron sia protetto](#verify-cron-is-secure).

## Cron sicuro con Nginx

Questa sezione descrive come proteggere cron utilizzando il server web Nginx. È necessario eseguire le seguenti attività:

1. Impostare un file password crittografato per Nginx
1. Modifica la configurazione nginx in modo che faccia riferimento al file password quando accedi `pub/cron.php`

### Crea un file di password

Consultare una delle risorse seguenti per creare un file di password prima di continuare:

- [Impostare l&#39;autenticazione tramite password con Nginx su Ubuntu 14.04 (DigitalOcean)](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
- [Autenticazione HTTP di base con Nginx (howtoforge)](https://www.howtoforge.com/basic-http-authentication-with-nginx)

### Cron protetto in `nginx.conf.sample`

Commerce fornisce un esempio ottimizzato di file di configurazione nginx pronto all’uso. È consigliabile modificarlo per proteggere il cron.

1. Aggiungi quanto segue al file [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample):

   ```conf
   #Securing cron
   location ~ cron\.php$ {
      auth_basic "Cron Authentication";
      auth_basic_user_file /etc/nginx/.htpasswd;
   
      try_files $uri =404;
      fastcgi_pass   fastcgi_backend;
      fastcgi_buffers 1024 4k;
   
      fastcgi_read_timeout 600s;
      fastcgi_connect_timeout 600s;
   
      fastcgi_index  index.php;
      fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
      include        fastcgi_params;
   }
   ```

1.Inginx di riavvio:

```bash
systemctl restart nginx
```

1. Continuare con [Verificare che cron sia protetto](#verify-cron-is-secure).

## Verificare che il cron sia sicuro

Il modo più semplice per verificare che `pub/cron.php` sia protetto consiste nel verificare che stia creando righe nella tabella del database `cron_schedule` dopo aver impostato l&#39;autenticazione tramite password. In questo esempio vengono utilizzati i comandi SQL per controllare il database, ma è possibile utilizzare qualsiasi strumento desiderato.

>[!INFO]
>
>Il cron `default` in esecuzione in questo esempio viene eseguito in base alla pianificazione definita in `crontab.xml`. Alcuni processi cron vengono eseguiti solo una volta al giorno. La prima volta che si esegue cron dal browser, la tabella `cron_schedule` viene aggiornata, ma le successive `pub/cron.php` richieste vengono eseguite con la pianificazione configurata.

**Verificare che il cron sia protetto**:

1. Accedere al database come utente del database Commerce o come `root`.

   Ad esempio:

   ```bash
   mysql -u magento -p
   ```

1. Utilizzare il database di Commerce:

   ```shell
   use <database-name>;
   ```

   Ad esempio:

   ```shell
   use magento;
   ```

1. Elimina tutte le righe della tabella di `cron_schedule` database:

   ```shell
   TRUNCATE TABLE cron_schedule;
   ```

1. Esegui cron da un browser:

   ```shell
   http[s]://<Commerce hostname or ip>/cron.php?group=default
   ```

   Ad esempio:

   ```shell
   http://magento.example.com/cron.php?group=default
   ```

1. Quando richiesto, immettere il nome e il password di un utente autorizzato. Nella figura seguente viene illustrato un esempio.

   ![Autorizzazione di cron tramite HTTP Basic](../../assets/configuration/cron-auth.png)

1. Verifica che le righe siano state aggiunte alla tabella:

   ```shell
   SELECT * from cron_schedule;
   
   mysql> SELECT * from cron_schedule;
   +-------------+-----------------------------------------------+---------+----------+---------------------+---------------------+-------------+-------------+
   | schedule_id | job_code                             | status  | messages | created_at        | scheduled_at      | executed_at | finished_at |
   +-------------+-----------------------------------------------+---------+----------+---------------------+---------------------+-------------+-------------+
   |         1 | catalog_product_outdated_price_values_cleanup | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         2 | sales_grid_order_async_insert             | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         3 | sales_grid_order_invoice_async_insert       | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         4 | sales_grid_order_shipment_async_insert      | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         5 | sales_grid_order_creditmemo_async_insert     | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         6 | sales_send_order_emails                  | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         7 | sales_send_order_invoice_emails            | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         8 | sales_send_order_shipment_emails           | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |         9 | sales_send_order_creditmemo_emails         | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |        10 | newsletter_send_all                     | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:25:00 | NULL      | NULL      |
   |        11 | captcha_delete_old_attempts               | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:30:00 | NULL      | NULL      |
   |        12 | captcha_delete_expired_images             | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:30:00 | NULL      | NULL      |
   |        13 | outdated_authentication_failures_cleanup     | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   |        14 | magento_newrelicreporting_cron            | pending | NULL    | 2017-09-27 14:24:17 | 2017-09-27 14:24:00 | NULL      | NULL      |
   +-------------+-----------------------------------------------+---------+----------+---------------------+---------------------+-------------+-------------+
   14 rows in set (0.00 sec)
   ```

## Eseguire cron da un browser Web

Puoi eseguire cron in qualsiasi momento, ad esempio durante lo sviluppo, utilizzando un browser web.

>[!WARNING]
>
>_non_ eseguire cron in un browser senza prima proteggerlo.

Se si utilizza un server Web Apache, è necessario rimuovere la restrizione dal file `.htaccess` prima di poter eseguire cron in un browser:

1. Accedi al server Commerce come utente con autorizzazioni di scrittura nel file system di Commerce.
1. Apri uno dei seguenti elementi in un editor di testo (a seconda del punto di ingresso al Magento):

   ```text
   <magento_root>/pub/.htaccess
   <magento_root>/.htaccess
   ```

1. Elimina o commenta quanto segue:

   ```conf
   ## Deny access to cron.php
     <Files cron.php>
        order allow,deny
        deny from all
     </Files>
   ```

   Ad esempio:

   ```conf
   ## Deny access to cron.php
      #<Files cron.php>
         # order allow,deny
         # deny from all
      #</Files>
   ```

1. Salva le modifiche e esci dall’editor di testo.

   È quindi possibile eseguire cron in un browser Web nel modo seguente:

   ```text
   <your hostname or IP>/<Commerce root>/pub/cron.php[?group=<group name>]
   ```

Dove:

- `<your hostname or IP>` è il nome host o l&#39;indirizzo IP dell&#39;installazione di Commerce
- `<Commerce root>` è la directory relativa alla directory principale dei documenti del server Web in cui è stato installato il software Commerce

  L’URL esatto utilizzato per eseguire l’applicazione Commerce dipende dalla configurazione del server web e dell’host virtuale.

- `<group name>` è un nome di gruppo cron valido (facoltativo)

Ad esempio:

```http
https://magento.example.com/magento2/pub/cron.php?group=index
```

>[!INFO]
>
>È necessario eseguire cron due volte: prima per scoprire le attività da eseguire e di nuovo per eseguire le attività stesse. Fare riferimento a [Configurare ed eseguire cron](../cli/configure-cron-jobs.md) per ulteriori informazioni sui gruppi cron.
