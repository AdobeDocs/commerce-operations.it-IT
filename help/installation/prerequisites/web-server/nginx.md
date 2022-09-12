---
title: Nginx
description: Segui questi passaggi per installare e configurare il server web Nginx per le installazioni on-premise di Adobe Commerce e Magenti Open Source.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '1180'
ht-degree: 0%

---


# Nginx

Adobe Commerce supporta l’allegato 1.18 (o [versione principale più recente](https://nginx.org/en/linux_packages.html#mainline)). È inoltre necessario installare la versione più recente di `php-fpm`.

Le istruzioni di installazione variano in base al sistema operativo in uso. Vedi [PHP](../php-settings.md) per informazioni.

## Ubuntu

La sezione seguente descrive come installare Adobe Commerce e Magenti Open Source 2.x su Ubuntu utilizzando gli allegati, PHP e MySQL.

### Installa nginx

```bash
sudo apt -y install nginx
```

È inoltre possibile [genera nginx dalla sorgente](https://www.armanism.com/blog/install-nginx-on-ubuntu)

Dopo aver completato le sezioni seguenti e installato l’applicazione, utilizzeremo un file di configurazione di esempio per [configura nginx](#configure-nginx).

### Installare e configurare php-fpm

Adobe Commerce e Magenti Open Source richiedono diversi [Estensioni PHP](../php-settings.md) per funzionare correttamente. Oltre a queste estensioni, devi anche installare e configurare il `php-fpm` estensione se utilizzi l&#39;indice.

Installazione e configurazione `php-fpm`:

1. Installa `php-fpm` e `php-cli`:

   ```bash
   apt-get -y install php7.2-fpm php7.2-cli
   ```

   >[!NOTE]
   >
   >Questo comando installa la versione più recente disponibile di PHP 7.2.X. Vedi [requisiti di sistema](../../system-requirements.md) per le versioni PHP supportate.

1. Apri `php.ini` file in un editor:

   ```bash
   vim /etc/php/7.2/fpm/php.ini
   ```

   ```bash
   vim /etc/php/7.2/cli/php.ini
   ```

1. Modifica entrambi i file in modo che corrispondano alle seguenti righe:

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >È consigliabile impostare il limite di memoria su 2 G durante il test di Adobe Commerce e Magento Open Source. Fai riferimento a [Impostazioni PHP richieste](../php-settings.md) per ulteriori informazioni.

1. Salva e esci dall’editor.

1. Riavvia `php-fpm` servizio:

   ```bash
   systemctl restart php7.2-fpm
   ```

### Installare e configurare MySQL

Fai riferimento a [MySQL](../database/mysql.md) per ulteriori informazioni.

### Installare e configurare

Esistono diversi modi per scaricare Adobe Commerce e Magento Open Source, tra cui:

* [Ottieni il metapackage del Compositore](../../composer.md)

* [Clonare l’archivio git](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

Questo esempio mostra un&#39;installazione basata su Compositore utilizzando la riga di comando.

1. Come [proprietario del file system](../file-system/overview.md), accedi al server delle applicazioni.

1. Passare alla directory docroot del server Web o a una directory configurata come docroot host virtuale. Per questo esempio, utilizziamo il valore predefinito Ubuntu `/var/www/html`.

   ```bash
   cd /var/www/html
   ```

1. Installa Compositore a livello globale. Il Compositore è necessario per aggiornare le dipendenze prima di installare Adobe Commerce o Magento Open Source:

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Crea un progetto Composer utilizzando il metapackage Magenti Open Source o Adobe Commerce.

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Quando richiesto, immetti il [chiavi di autenticazione](../authentication-keys.md). Le _chiave pubblica_ è il tuo nome utente; le _chiave privata_ è la tua password.

1. Impostare le autorizzazioni di lettura e scrittura per il gruppo di server web prima di installare l&#39;applicazione. Questo è necessario in modo che la riga di comando possa scrivere file nel file system.

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

1. Installa da [riga di comando](../../advanced.md). Questo esempio presuppone che la directory di installazione sia denominata `magento2ee`, `db-host` si trova sulla stessa macchina (`localhost`) e che la `db-name`, `db-user`e `db-password` sono tutti `magento`:

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=magento \
   --db-user=magento \
   --db-password=magento \
   --backend-frontname=admin \
   --admin-firstname=admin \
   --admin-lastname=admin \
   --admin-email=admin@admin.com \
   --admin-user=admin \
   --admin-password=admin123 \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1 \
   --search-engine=elasticsearch7 \
   --elasticsearch-host=es-host.example.com \
   --elasticsearch-port=9200
   ```

1. Passa alla modalità sviluppatore:

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Configura nginx

È consigliabile configurare l’indice utilizzando `nginx.conf.sample` file di configurazione fornito nella directory di installazione e nell’host virtuale di input.

Queste istruzioni presuppongono l&#39;utilizzo della posizione predefinita Ubuntu per l&#39;host virtuale nginx (ad esempio, `/etc/nginx/sites-available`) e docroot predefinito Ubuntu (ad esempio, `/var/www/html`), tuttavia, è possibile modificare queste posizioni in base all’ambiente utilizzato.

1. Crea un nuovo host virtuale per il sito:

   ```bash
   vim /etc/nginx/sites-available/magento
   ```

1. Aggiungi la seguente configurazione:

   ```conf
   upstream fastcgi_backend {
     server  unix:/run/php/php7.2-fpm.sock;
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
   >La `include` direttiva deve puntare al file di configurazione nginx di esempio nella directory di installazione.

1. Sostituisci `www.magento-dev.com` con il nome di dominio. Questo deve corrispondere all&#39;URL di base specificato durante l&#39;installazione di Adobe Commerce o Magenti Open Source.

1. Salva e esci dall’editor.

1. Attiva l&#39;host virtuale appena creato creando un link simbolico ad esso nel `/etc/nginx/sites-enabled` directory:

   ```bash
   ln -s /etc/nginx/sites-available/magento /etc/nginx/sites-enabled
   ```

1. Verifica che la sintassi sia corretta:

   ```bash
   nginx -t
   ```

1. Riavvia l&#39;indice:

   ```bash
   systemctl restart nginx
   ```

### Verificare l’installazione

Apri un browser web e passa all’URL di base del sito in [verifica l&#39;installazione](../../next-steps/verify.md).

## CentOS 7

La sezione seguente descrive come installare Adobe Commerce e Magenti Open Source 2.x su CentOS 7 utilizzando gli allegati, PHP e MySQL.

### Installa nginx

```bash
yum -y install epel-release
```

```bash
yum -y install nginx
```

Al termine dell&#39;installazione, avviare l&#39;indice e configurarlo per avviarlo al momento dell&#39;avvio:

```bash
systemctl start nginx
```

```bash
systemctl enable nginx
```

Dopo aver completato le sezioni seguenti e installato l’applicazione, utilizzeremo un file di configurazione di esempio per configurare l’allegato.

### Installare e configurare php-fpm

Adobe Commerce e Magenti Open Source richiedono diversi [PHP](../php-settings.md) le estensioni funzionino correttamente. Oltre a queste estensioni, devi anche installare e configurare il `php-fpm` Se utilizzi l&#39;indice.

1. Installa `php-fpm`:

   ```bash
   yum -y install php70w-fpm
   ```

1. Apri `/etc/php.ini` in un editor.

1. Rimuovi il commento da `cgi.fix_pathinfo` e modifica il valore in `0`.

1. Modifica il file in modo che corrisponda alle seguenti righe:

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >È consigliabile impostare il limite di memoria su 2 G durante il test di Adobe Commerce o Magento Open Source. Fai riferimento a [Impostazioni PHP richieste](../php-settings.md) per ulteriori informazioni.

1. Rimuovi il commento alla directory del percorso della sessione e imposta il percorso:

   ```conf
   session.save_path = "/var/lib/php/session"
   ```

1. Salva e esci dall’editor.

1. Apri `/etc/php-fpm.d/www.conf` in un editor.

1. Modifica il file in modo che corrisponda alle seguenti righe:

   ```conf
   user = nginx
   group = nginx
   listen = /run/php-fpm/php-fpm.sock
   listen.owner = nginx
   listen.group = nginx
   listen.mode = 0660
   ```

1. Rimuovi il commento dalle righe di ambiente:

   ```conf
   env[HOSTNAME] = $HOSTNAME
   env[PATH] = /usr/local/bin:/usr/bin:/bin
   env[TMP] = /tmp
   env[TMPDIR] = /tmp
   env[TEMP] = /tmp
   ```

1. Salva e esci dall’editor.

1. Crea una directory per il percorso della sessione PHP e cambia il proprietario in `apache` utente e gruppo:

   ```bash
   mkdir -p /var/lib/php/session/
   ```

   ```bash
   chown -R apache:apache /var/lib/php/
   ```

1. Crea una directory per il percorso della sessione PHP e cambia il proprietario in `apache` utente e gruppo:

   ```bash
   mkdir -p /run/php-fpm/
   ```

   ```bash
   chown -R apache:apache /run/php-fpm/
   ```

1. Avvia la `php-fpm` servizio e configuralo per l&#39;avvio al momento dell&#39;avvio:

   ```bash
   systemctl start php-fpm
   ```

   ```bash
   systemctl enable php-fpm
   ```

1. Verifica che `php-fpm` servizio in esecuzione:

   ```bash
   netstat -pl | grep php-fpm.sock
   ```

### Installare e configurare MySQL

Fai riferimento a [MySQL](..//database/mysql.md) per ulteriori informazioni.

### Installare e configurare

Esistono diversi modi per scaricare Adobe Commerce e il Magento Open Source, tra cui:

* [Ottieni il metapackage del Compositore](../../composer.md)

* [Clonare l’archivio git](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

Questo esempio mostra un&#39;installazione basata su Compositore utilizzando la riga di comando.

1. Come [proprietario del file system](../file-system/overview.md), accedi al server delle applicazioni.

1. Passare alla directory docroot del server Web o a una directory configurata come docroot host virtuale. Per questo esempio, utilizziamo il valore predefinito Ubuntu `/var/www/html`.

   ```bash
   cd /var/www/html
   ```

1. Installa Compositore a livello globale. Il Compositore è necessario per aggiornare le dipendenze prima di installare Adobe Commerce o Magento Open Source:

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Crea un progetto Composer utilizzando il metapackage Magenti Open Source o Adobe Commerce.

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Quando richiesto, immetti il [chiavi di autenticazione](../authentication-keys.md). Le _chiave pubblica_ è il tuo nome utente; le _chiave privata_ è la tua password.

1. Impostare le autorizzazioni di lettura e scrittura per il gruppo di server web prima di installare l&#39;applicazione. Questo è necessario in modo che la riga di comando possa scrivere file nel file system.

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

1. Installa da [riga di comando](../../advanced.md). Questo esempio presuppone che la directory di installazione sia denominata `magento2ee`, `db-host` si trova sulla stessa macchina (`localhost`) e che la `db-name`, `db-user`e `db-password` sono tutti `magento`:

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=magento \
   --db-user=magento \
   --db-password=magento \
   --backend-frontname=admin \
   --admin-firstname=admin \
   --admin-lastname=admin \
   --admin-email=admin@admin.com \
   --admin-user=admin \
   --admin-password=admin123 \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1
   ```

1. Passa alla modalità sviluppatore:

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Configura nginx

È consigliabile configurare l’indice utilizzando `nginx.conf.sample` file di configurazione fornito nella directory di installazione e nell’host virtuale di input.

Queste istruzioni presuppongono l&#39;utilizzo della posizione predefinita CentOS per l&#39;host virtuale nginx (ad esempio, `/etc/nginx/conf.d`) e docroot predefinito (ad esempio, `/usr/share/nginx/html`), tuttavia, è possibile modificare queste posizioni in base all’ambiente utilizzato.

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
   >La `include` direttiva deve puntare al file di configurazione nginx di esempio nella directory di installazione.

1. Sostituisci `www.magento-dev.com` con il nome di dominio.

1. Salva e esci dall’editor.

1. Verifica che la sintassi sia corretta:

   ```bash
   nginx -t
   ```

1. Riavvia l&#39;indice:

   ```bash
   systemctl restart nginx
   ```

### Configurare SELinux e Firewald

SELinux è abilitato per impostazione predefinita su CentOS 7. Usa il seguente comando per vedere se è in esecuzione:

```bash
sestatus
```

Per configurare SELinux e firewald:

1. Installa gli strumenti di gestione SELinux:

   ```bash
   yum -y install policycoreutils-python
   ```

1. Esegui i seguenti comandi per modificare il contesto di sicurezza della directory di installazione:

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

1. Installa il pacchetto firewalld:

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

1. Esegui i seguenti comandi per aprire le porte per HTTP e HTTPS in modo da poter accedere all’URL di base da un browser Web:

   ```bash
   firewall-cmd --permanent --add-service=http
   ```

   ```bash
   firewall-cmd --permanent --add-service=https
   ```

   ```bash
   firewall-cmd --reload
   ```

### Verificare l’installazione

Apri un browser web e passa all’URL di base del sito in [verifica l&#39;installazione](../../next-steps/verify.md).
