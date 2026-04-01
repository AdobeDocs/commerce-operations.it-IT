---
title: Installare Nginx per le distribuzioni locali
description: Scopri come installare e configurare il server web Nginx per le distribuzioni Adobe Commerce on-premise. Configurare PHP-FPM e l'host virtuale.
feature: Install, Configuration
badgePaas: label="On-premise" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Applicabile solo ai progetti locali di Adobe Commerce."
exl-id: 041ddb9d-868e-4021-9388-1c9ea11bfd8f
source-git-commit: 352a71cb88ff38c0920201f49f1d7b889509fd61
workflow-type: tm+mt
source-wordcount: '1430'
ht-degree: 0%

---

# Installare Nginx per le distribuzioni locali {#nginx}

Questa guida illustra come installare Nginx per le distribuzioni Adobe Commerce on-premise e configurare le impostazioni Nginx richieste da Commerce. Include procedure specifiche per il sistema operativo per Ubuntu e CentOS, oltre a indicazioni per la configurazione di PHP-FPM. Adobe consiglia di seguire le istruzioni di configurazione fornite in questa guida per preservare sia la funzionalità che la sicurezza dell’applicazione Commerce.

Adobe supporta le versioni Nginx elencate nei [requisiti di sistema](../../system-requirements.md) per la versione di Adobe Commerce in uso. Le versioni supportate variano a seconda della versione. Nginx richiede anche una configurazione PHP-FPM supportata. Per i requisiti PHP correlati, vedere [PHP](../php-settings.md).

## Installazione su Ubuntu

Usa questa sezione per installare Adobe Commerce su Ubuntu con Nginx, PHP e MySQL.

### Installa Nginx

```bash
sudo apt -y install nginx
```

Puoi anche [generare Nginx dall&#39;origine](https://www.armanism.com/blog/install-nginx-on-ubuntu).

Dopo aver completato le sezioni seguenti e aver installato l&#39;applicazione, utilizzare il file di configurazione di esempio per [configurare Nginx](#configure-nginx). Questa configurazione consigliata preserva sia la funzionalità che la sicurezza dell’applicazione Commerce.

### Installare e configurare PHP-FPM

Adobe Commerce richiede diverse [estensioni PHP](../php-settings.md) per funzionare correttamente. Oltre a queste estensioni, se utilizzi Nginx devi installare e configurare l&#39;estensione `php-fpm`.

Per installare e configurare `php-fpm`:

1. Installa i pacchetti `php-fpm` e `php-cli` per la versione PHP supportata dalla versione Adobe Commerce. In Ubuntu, i nomi dei pacchetti in genere seguono questo pattern:

   ```bash
   apt-get -y install php<php-version>-fpm php<php-version>-cli
   ```

   >[!NOTE]
   >
   >Sostituisci `<php-version>` con la versione secondaria PHP supportata elencata in [requisiti di sistema](../../system-requirements.md) per la versione di Adobe Commerce che stai installando. Utilizzare lo stesso valore nei percorsi dei file, nel nome del servizio e nel percorso del socket nei passaggi seguenti.

1. Apri i file `php.ini` in un editor:

   ```bash
   vim /etc/php/<php-version>/fpm/php.ini
   ```

   ```bash
   vim /etc/php/<php-version>/cli/php.ini
   ```

1. Modificate entrambi i file in modo che corrispondano alle seguenti righe:

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Adobe consiglia di impostare il limite di memoria su 2 GB durante il test di Adobe Commerce. Per ulteriori informazioni, consultare [Impostazioni PHP richieste](../php-settings.md).

1. Salva ed esci dall’editor.

1. Riavviare il servizio `php-fpm`:

   ```bash
   systemctl restart php<php-version>-fpm
   ```

### Installare e configurare MySQL

Per ulteriori informazioni, consultare [MySQL](../database/mysql.md).

### Installare Adobe Commerce

Puoi scaricare Adobe Commerce in diversi modi:

* [Ottieni il metapacchetto Compositore](../../composer.md)

* [Clona l&#39;archivio Git](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)

Questo esempio mostra un&#39;installazione basata su Compositore utilizzando la riga di comando.

1. In qualità di [proprietario del file system](../file-system/overview.md), accedi al server applicazioni.

1. Passare alla directory principale dei documenti del server Web o a una directory configurata come directory principale dei documenti host virtuale. In questo esempio viene utilizzato il valore predefinito di Ubuntu `/var/www/html`.

   ```bash
   cd /var/www/html
   ```

1. Installa Compositore a livello globale. Il Compositore è necessario per aggiornare le dipendenze prima di installare Adobe Commerce:

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Crea un progetto Compositore utilizzando il metapacchetto Adobe Commerce.

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Quando richiesto, immetti le [chiavi di autenticazione](../authentication-keys.md). La _chiave pubblica_ è il tuo nome utente; la tua _chiave privata_ è la tua password.

1. Impostare le autorizzazioni di lettura/scrittura per il gruppo di server Web prima di installare l&#39;applicazione. Ciò è necessario affinché la riga di comando possa scrivere file nel file system.

   ```bash
   cd /var/www/html/<magento install directory>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :www-data . # Ubuntu
   ```

   ```bash
   chmod u+x bin/magento
   ```

1. Installa dalla [riga di comando](../../advanced.md). In questo esempio si presuppone che la directory di installazione sia denominata `magento2ee` e che l&#39;host del database si trovi nello stesso computer (`localhost`):

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=<db-name> \
   --db-user=<db-user> \
   --db-password=<db-password> \
   --backend-frontname=<backend-uri> \
   --admin-firstname=<admin-first-name> \
   --admin-lastname=<admin-last-name> \
   --admin-email=<admin-email> \
   --admin-user=<admin-user> \
   --admin-password=<admin-password> \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1 \
   --search-engine=<search-engine-value> \
   --<search-engine-host-parameter>=search-host.example.com \
   --<search-engine-port-parameter>=9200
   ```

   >[!NOTE]
   >
   >Utilizza il valore `--search-engine` e le opzioni host/porta corrispondenti richieste dalla versione di Adobe Commerce che stai installando. Per le versioni precedenti alla 2.4.6, utilizzare `elasticsearch7` con le opzioni `--elasticsearch-*` per Elasticsearch 7 o OpenSearch. Per le versioni 2.4.6 e successive, utilizza il valore del motore di ricerca e le opzioni CLI corrispondenti supportate da tale versione.

1. Passa alla modalità sviluppatore:

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Configurare Nginx

Adobe consiglia di configurare Nginx utilizzando il file di configurazione `nginx.conf.sample` fornito nella directory di installazione e la configurazione dell&#39;host virtuale Nginx per preservare sia la funzionalità che la sicurezza dell&#39;applicazione Commerce.

>[!IMPORTANT]
>
>Il file `nginx.conf.sample` fornisce il routing dell&#39;applicazione richiesto e le regole di protezione avanzata. Ad esempio, limita l’esecuzione di script dannosi caricati sul server. Se non utilizzi questo file o non ne modifichi le regole, sei responsabile dell’implementazione di controlli di sicurezza equivalenti nella configurazione di indice personalizzata.

Queste istruzioni presuppongono l&#39;utilizzo della posizione predefinita Ubuntu per l&#39;host virtuale Nginx, ad esempio `/etc/nginx/sites-available`, e della directory principale dei documenti predefinita Ubuntu, ad esempio `/var/www/html`. Puoi modificare queste posizioni in base all’ambiente in uso.

1. Crea un nuovo host virtuale per il sito:

   ```bash
   vim /etc/nginx/sites-available/magento
   ```

1. Aggiungi la seguente configurazione:

   ```conf
   upstream fastcgi_backend {
     server  unix:/run/php/php<php-version>-fpm.sock;
   }
   
   server {
   
     listen 80;
     server_name www.magento-dev.com;
     set $MAGE_ROOT /var/www/html/magento2;
     include /var/www/html/magento2/nginx.conf.sample;
   }
   ```

   >[!NOTE]
   >
   >La direttiva `include` deve puntare al file di configurazione nginx di esempio nella directory di installazione.

1. Sostituisci `www.magento-dev.com` con il tuo nome di dominio. Deve corrispondere all’URL di base specificato durante l’installazione di Adobe Commerce.

1. Salva ed esci dall’editor.

1. Attivare l&#39;host virtuale appena creato creando un collegamento simbolico nella directory `/etc/nginx/sites-enabled`:

   ```bash
   ln -s /etc/nginx/sites-available/magento /etc/nginx/sites-enabled
   ```

1. Verifica che la sintassi sia corretta:

   ```bash
   nginx -t
   ```

1. Riavvia Nginx:

   ```bash
   systemctl restart nginx
   ```

### Verificare l&#39;installazione

Per verificare l’installazione, apri un browser web e passa all’URL di base del sito. Per ulteriori informazioni, vedere [Verificare l&#39;installazione](../../next-steps/verify.md).

## Installazione su CentOS 7

Usa questa sezione per installare Adobe Commerce su CentOS 7 con Nginx, PHP e MySQL.

### Installa Nginx

```bash
yum -y install epel-release
```

```bash
yum -y install nginx
```

Al termine dell&#39;installazione, avviare Index e configurarlo per avviarlo al momento dell&#39;avvio:

```bash
systemctl start nginx
```

```bash
systemctl enable nginx
```

Dopo aver completato le sezioni seguenti e aver installato l’applicazione, utilizza un file di configurazione di esempio per configurare Nginx.

### Installare e configurare PHP-FPM

Adobe Commerce richiede diverse estensioni [PHP](../php-settings.md) per funzionare correttamente. Oltre a queste estensioni, se utilizzi Nginx devi installare e configurare l&#39;estensione `php-fpm`.

1. Installa `php-fpm`:

   ```bash
   yum -y install <php-fpm-package>
   ```

1. Aprire il file `/etc/php.ini` in un editor.

   >[!NOTE]
   >
   >Installa il pacchetto che fornisce `php-fpm` per la versione PHP supportata dalla versione Adobe Commerce che stai installando. I nomi dei pacchetti variano a seconda dell’archivio e del sistema operativo. Consulta [requisiti di sistema](../../system-requirements.md).

1. Rimuovere il commento dalla riga `cgi.fix_pathinfo` e modificare il valore in `0`.

1. Modifica il file in modo che corrisponda alle righe seguenti:

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Adobe consiglia di impostare il limite di memoria su 2 GB durante il test di Adobe Commerce. Per ulteriori informazioni, consultare [Impostazioni PHP richieste](../php-settings.md).

1. Rimuovere il commento dalla directory del percorso di sessione e impostare il percorso:

   ```conf
   session.save_path = "/var/lib/php/session"
   ```

1. Salva ed esci dall’editor.

1. Apri `/etc/php-fpm.d/www.conf` in un editor.

1. Modifica il file in modo che corrisponda alle righe seguenti:

   ```conf
   user = nginx
   group = nginx
   listen = /run/php-fpm/php-fpm.sock
   listen.owner = nginx
   listen.group = nginx
   listen.mode = 0660
   ```

1. Rimuovi commento dalle righe ambiente:

   ```conf
   env[HOSTNAME] = $HOSTNAME
   env[PATH] = /usr/local/bin:/usr/bin:/bin
   env[TMP] = /tmp
   env[TMPDIR] = /tmp
   env[TEMP] = /tmp
   ```

1. Salva ed esci dall’editor.

1. Creare una directory per il percorso della sessione PHP e impostare il proprietario sull&#39;utente e sul gruppo `nginx`:

   ```bash
   mkdir -p /var/lib/php/session/
   ```

   ```bash
   chown -R nginx:nginx /var/lib/php/
   ```

1. Creare una directory per il socket PHP-FPM e impostare il proprietario sull&#39;utente e sul gruppo `nginx`:

   ```bash
   mkdir -p /run/php-fpm/
   ```

   ```bash
   chown -R nginx:nginx /run/php-fpm/
   ```

1. Avviare il servizio `php-fpm` e configurarlo per l&#39;avvio al momento dell&#39;avvio:

   ```bash
   systemctl start php-fpm
   ```

   ```bash
   systemctl enable php-fpm
   ```

1. Verificare che il servizio `php-fpm` sia in esecuzione:

   ```bash
   netstat -pl | grep php-fpm.sock
   ```

### Installare e configurare MySQL

Per ulteriori informazioni, consultare [MySQL](../database/mysql.md).

### Installare Adobe Commerce

Puoi scaricare Adobe Commerce in diversi modi:

* [Ottieni il metapacchetto Compositore](../../composer.md)

* [Clona l&#39;archivio Git](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)

Questo esempio mostra un&#39;installazione basata su Compositore utilizzando la riga di comando.

1. In qualità di [proprietario del file system](../file-system/overview.md), accedi al server applicazioni.

1. Passare alla directory principale dei documenti del server Web o a una directory configurata come directory principale dei documenti host virtuale. Per questo esempio, utilizzare l&#39;impostazione predefinita di CentOS `/usr/share/nginx/html`.

   ```bash
   cd /usr/share/nginx/html
   ```

1. Installa Compositore a livello globale. Il Compositore è necessario per aggiornare le dipendenze prima di installare Adobe Commerce:

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Crea un progetto Compositore utilizzando il metapacchetto Adobe Commerce.

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Quando richiesto, immetti le [chiavi di autenticazione](../authentication-keys.md). La _chiave pubblica_ è il tuo nome utente; la tua _chiave privata_ è la tua password.

1. Impostare le autorizzazioni di lettura/scrittura per il gruppo di server Web prima di installare l&#39;applicazione. Ciò è necessario affinché la riga di comando possa scrivere file nel file system.

   ```bash
   cd /usr/share/nginx/html/<magento install directory>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :nginx . # CentOS
   ```

   ```bash
   chmod u+x bin/magento
   ```

1. Installa dalla [riga di comando](../../advanced.md). In questo esempio si presuppone che la directory di installazione sia denominata `magento2ee` e che l&#39;host del database si trovi nello stesso computer (`localhost`):

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=<db-name> \
   --db-user=<db-user> \
   --db-password=<db-password> \
   --backend-frontname=<backend-uri> \
   --admin-firstname=<admin-first-name> \
   --admin-lastname=<admin-last-name> \
   --admin-email=<admin-email> \
   --admin-user=<admin-user> \
   --admin-password=<admin-password> \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1
   ```

1. Passa alla modalità sviluppatore:

   ```bash
   cd /usr/share/nginx/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Configurare Nginx

È consigliabile configurare Nginx utilizzando il file `nginx.conf.sample` nella directory di installazione e la configurazione dell&#39;host virtuale Nginx.

>[!IMPORTANT]
>
>Il file `nginx.conf.sample` fornisce il routing dell&#39;applicazione richiesto e le regole di protezione avanzata. Ad esempio, limita l’esecuzione di script dannosi caricati sul server. Se non utilizzi questo file o non ne modifichi le regole, sei responsabile dell’implementazione di controlli di sicurezza equivalenti nella configurazione di indice personalizzata.

Queste istruzioni presuppongono l&#39;utilizzo della posizione predefinita di CentOS per l&#39;host virtuale Nginx, ad esempio `/etc/nginx/conf.d`, e della directory principale dei documenti predefinita, ad esempio `/usr/share/nginx/html`. Puoi modificare queste posizioni in base all’ambiente in uso.

1. Crea un nuovo host virtuale per il sito:

   ```bash
   vim /etc/nginx/conf.d/magento.conf
   ```

1. Aggiungi la seguente configurazione:

   ```conf
   upstream fastcgi_backend {
     server  unix:/run/php-fpm/php-fpm.sock;
   }
   
   server {
   
     listen 80;
     server_name www.magento-dev.com;
     set $MAGE_ROOT /usr/share/nginx/html/magento2;
     include /usr/share/nginx/html/magento2/nginx.conf.sample;
   }
   ```

   >[!NOTE]
   >
   >La direttiva `include` deve puntare al file di configurazione nginx di esempio nella directory di installazione.

1. Sostituisci `www.magento-dev.com` con il tuo nome di dominio.

1. Salva ed esci dall’editor.

1. Verifica che la sintassi sia corretta:

   ```bash
   nginx -t
   ```

1. Riavvia Nginx:

   ```bash
   systemctl restart nginx
   ```

### Configurare SELinux e firewalld

SELinux è abilitato per impostazione predefinita su CentOS 7. Utilizza il seguente comando per confermare che è in esecuzione:

```bash
sestatus
```

Per configurare SELinux e firewalld:

1. Installare gli strumenti di gestione SELinux:

   ```bash
   yum -y install policycoreutils-python
   ```

1. Eseguire i comandi seguenti per modificare il contesto di protezione per la directory di installazione:

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/app/etc(/.*)?'
   ```

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/var(/.*)?'
   ```

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/pub/media(/.*)?'
   ```

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/pub/static(/.*)?'
   ```

   ```bash
   restorecon -Rv '/usr/share/nginx/html/magento2/'
   ```

1. Installare il pacchetto firewalld:

   ```bash
   yum -y install firewalld
   ```

1. Avviare il servizio firewall e configurarlo per l&#39;avvio al momento dell&#39;avvio:

   ```bash
   systemctl start firewalld
   ```

   ```bash
   systemctl enable firewalld
   ```

1. Esegui i seguenti comandi per aprire le porte per HTTP e HTTPS in modo da poter accedere all’URL di base da un browser web:

   ```bash
   firewall-cmd --permanent --add-service=http
   ```

   ```bash
   firewall-cmd --permanent --add-service=https
   ```

   ```bash
   firewall-cmd --reload
   ```

### Verificare l&#39;installazione

Per verificare l’installazione, apri un browser web e passa all’URL di base del sito. Per ulteriori informazioni, vedere [Verificare l&#39;installazione](../../next-steps/verify.md).
