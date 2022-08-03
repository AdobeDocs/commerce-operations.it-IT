---
title: PHP cron sicuro
description: Limita l'utente che può eseguire il file cron.php in un browser.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '938'
ht-degree: 1%

---


# PHP cron sicuro

Questo argomento illustra come garantire `pub/cron.php` per evitare che venga utilizzato in un maligno sfruttamento. Se non si protegge cron, qualsiasi utente potrebbe potenzialmente eseguire cron per attaccare la tua applicazione Commerce.

Il lavoro cron esegue diverse attività pianificate ed è una parte fondamentale della configurazione Commerce. Le attività pianificate includono, tra l’altro:

- Reindicizzazione
- Generazione di e-mail
- Generazione delle newsletter
- Generazione di sitemap

>[!INFO]
>
>Fai riferimento a [Configurare ed eseguire cron](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) per ulteriori informazioni sui gruppi cron.

Puoi eseguire un lavoro cron nei seguenti modi:

- Utilizzo della [`magento cron:run`](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) comando dalla riga di comando o in una crontab
- Accesso `pub/cron.php?[group=<name>]` in un browser web

>[!INFO]
>
>Non è necessario eseguire alcuna operazione se si utilizza il [`magento cron:run`](../cli/configure-cron-jobs.md#run-cron-from-the-command-line) per eseguire cron perché utilizza un processo diverso che è già sicuro.

## Cron sicuro con Apache

Questa sezione illustra come proteggere cron utilizzando l’autenticazione HTTP Basic con Apache. Queste istruzioni sono basate su Apache 2.2 con CentOS 6. Per ulteriori informazioni, consulta una delle risorse seguenti:

- [Esercitazione sull’autenticazione e l’autorizzazione di Apache 2.2](https://httpd.apache.org/docs/2.2/howto/auth.html)
- [Esercitazione sull’autenticazione e l’autorizzazione di Apache 2.4](https://httpd.apache.org/docs/2.4/howto/auth.html)

### Creazione di un file di password

Per motivi di sicurezza, è possibile individuare il file della password ovunque tranne il docroot del server web. In questo esempio, il file della password viene archiviato in una nuova directory.

Immetti i seguenti comandi come utente con `root` privilegi:

```bash
mkdir -p /usr/local/apache/password
```

```bash
htpasswd -c /usr/local/apache/password/passwords <username>
```

Dove `<username>` può essere l&#39;utente del server web o un altro utente. In questo esempio, utilizziamo l’utente del server web, ma la scelta dell’utente dipende da te.

Segui le istruzioni visualizzate sullo schermo per creare una password per l’utente.

Per aggiungere un altro utente al file della password, immetti il seguente comando come utente con `root` privilegi:

```bash
htpasswd /usr/local/apache/password/passwords <username>
```

### Aggiungi utenti per creare un gruppo cron autorizzato (facoltativo)

È possibile abilitare più utenti all&#39;esecuzione del cron aggiungendo questi utenti al file della password, incluso un file di gruppo.

Per aggiungere un altro utente al file della password:

```bash
htpasswd /usr/local/apache/password/passwords <username>
```

Per creare un gruppo autorizzato, creare un file di gruppo in un punto qualsiasi al di fuori del docroot del server web. Il file di gruppo specifica il nome del gruppo e gli utenti del gruppo. In questo esempio, il nome del gruppo è `MagentoCronGroup`.

```bash
vim /usr/local/apache/password/group
```

Contenuto del file:

```text
MagentoCronGroup: <username1> ... <usernameN>
```

### Protezione della cron in `.htaccess`

Per proteggere cron in `.htaccess` file:

1. Accedi al tuo server Commerce come proprietario del file system o passa a .
1. Apri `<magento_root>/pub/.htaccess` in un editor di testo.

   (Perché `cron.php` si trova in `pub` directory, modificare `.htaccess` Solo.)

1. _Cron access per uno o più utenti._ Sostituire l&#39;esistente `<Files cron.php>` direttiva con le seguenti caratteristiche:

   ```conf
   <Files cron.php>
      AuthType Basic
      AuthName "Cron Authentication"
      AuthUserFile /usr/local/apache/password/passwords
      Require valid-user
   </Files>
   ```

1. _Cron access per un gruppo._ Sostituire l&#39;esistente `<Files cron.php>` direttiva con le seguenti caratteristiche:

   ```conf
   <Files cron.php>
      AuthType Basic
      AuthName "Cron Authentication"
      AuthUserFile /usr/local/apache/password/passwords
      AuthGroupFile <path to optional group file>
      Require group <name>
   </Files>
   ```

1. Salva le modifiche in `.htaccess` e esci dall’editor di testo.
1. Continua con [Verifica che cron sia sicuro](#verify-cron-is-secure).

## Cron sicuro con Nginx

Questa sezione illustra come proteggere cron utilizzando il server web Nginx. È necessario eseguire le seguenti attività:

1. Imposta un file di password crittografata per Nginx
1. Modifica la configurazione dell&#39;indice in modo che faccia riferimento al file della password quando accedi `pub/cron.php`

### Creazione di un file di password

Per creare un file password prima di continuare, consulta una delle risorse seguenti:

- [Come impostare l&#39;autenticazione tramite password con Nginx su Ubuntu 14.04 (DigitalOcean)](https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04)
- [Autenticazione HTTP di base con nonx (howtoforge)](https://www.howtoforge.com/basic-http-authentication-with-nginx)

### Protezione della cron in `nginx.conf.sample`

Commerce fornisce un file di configurazione nginx di esempio ottimizzato preconfigurato. È consigliabile modificarlo per proteggere cron.

1. Aggiungi quanto segue al tuo [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) file:

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

1. Riavvia l&#39;allegato:

```bash
systemctl restart nginx
```

1. Continua con [Verifica che cron sia sicuro](#verify-cron-is-secure).

## Verifica che cron sia sicuro

Il modo più semplice per verificare che `pub/cron.php` è sicuro di verificare che stia creando righe nel `cron_schedule` tabella di database dopo aver impostato l&#39;autenticazione tramite password. In questo esempio vengono utilizzati i comandi SQL per controllare il database, ma è possibile utilizzare lo strumento desiderato.

>[!INFO]
>
>La `default` cron in esecuzione in questo esempio viene eseguito in base alla pianificazione definita in `crontab.xml`. Alcuni lavori cron vengono eseguiti solo una volta al giorno. La prima volta che esegui cron dal browser, la `cron_schedule` la tabella viene aggiornata, ma successiva `pub/cron.php` le richieste vengono eseguite alla pianificazione configurata.

**Per verificare che cron sia sicuro**:

1. Accedi al database come utente del database Commerce o come `root`.

   Ad esempio:

   ```bash
   mysql -u magento -p
   ```

1. Utilizzare il database Commerce:

   ```shell
   use <database-name>;
   ```

   Ad esempio:

   ```shell
   use magento;
   ```

1. Elimina tutte le righe dal `cron_schedule` tabella di database:

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

1. Quando richiesto, immetti il nome e la password di un utente autorizzato. Nella figura seguente viene illustrato un esempio.

   ![Autorizzazione cron tramite HTTP Basic](../../assets/configuration/cron-auth.png)

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

## Eseguire cron da un browser web

Puoi eseguire cron in qualsiasi momento, ad esempio durante lo sviluppo, utilizzando un browser web.

>[!WARNING]
>
>Do _not_ eseguire cron in un browser senza prima fissarlo.

Se utilizzi un server web Apache, devi rimuovere la restrizione dal `.htaccess` prima di eseguire cron in un browser:

1. Accedi al tuo server Commerce come utente con autorizzazioni per scrivere nel file system Commerce.
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

   Puoi quindi eseguire cron in un browser Web come segue:

   ```text
   <your hostname or IP>/<Commerce root>/pub/cron.php[?group=<group name>]
   ```

Dove:

- `<your hostname or IP>` è il nome host o l’indirizzo IP dell’installazione Commerce
- `<Commerce root>` è la directory relativa al docroot del server Web in cui è stato installato il software Commerce

   L’URL esatto utilizzato per eseguire l’applicazione Commerce dipende dalla configurazione del server web e dell’host virtuale.

- `<group name>` è un nome di gruppo cron valido (facoltativo)

Ad esempio:

```http
https://magento.example.com/magento2/pub/cron.php?group=index
```

>[!INFO]
>
>Devi eseguire il cron due volte: prima di scoprire le attività da eseguire e di nuovo per eseguire le attività stesse. Fai riferimento a [Configurare ed eseguire cron](../cli/configure-cron-jobs.md) per ulteriori informazioni sui gruppi cron.
