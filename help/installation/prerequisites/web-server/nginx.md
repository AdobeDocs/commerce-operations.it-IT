---
title: Nginx
description: Segui questi passaggi per installare e configurare il server web Nginx per le installazioni locali di Adobe Commerce.
exl-id: 041ddb9d-868e-4021-9388-1c9ea11bfd8f
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '1134'
ht-degree: 0%

---

# Nginx

Adobe Commerce supporta nginx 1.x (o il [versione principale più recente](https://nginx.org/en/linux_packages.html#mainline)). È inoltre necessario installare la versione più recente di `php-fpm`.

Le istruzioni di installazione variano in base al sistema operativo in uso. Consulta [PHP](../php-settings.md) per informazione.

## Ubuntu

La sezione seguente descrive come installare Adobe Commerce 2.x su Ubuntu utilizzando nginx, PHP e MySQL.

### Installa nginx

```bash
sudo apt -y install nginx
```

È inoltre possibile [build index from source](https://www.armanism.com/blog/install-nginx-on-ubuntu)

Dopo aver completato le sezioni seguenti e aver installato l’applicazione, utilizzeremo un file di configurazione di esempio per [configura nginx](#configure-nginx).

### Installare e configurare php-fpm

Adobe Commerce richiede diversi [Estensioni PHP](../php-settings.md) per funzionare correttamente. Oltre a queste estensioni, devi anche installare e configurare il `php-fpm` se utilizzi nginx.

Per installare e configurare `php-fpm`:

1. Installa `php-fpm` e `php-cli`:

   ```bash
   apt-get -y install php7.2-fpm php7.2-cli
   ```

   >[!NOTE]
   >
   >Con questo comando viene installata la versione più recente disponibile di PHP 7.2.X. Consulta [requisiti di sistema](../../system-requirements.md) per le versioni PHP supportate.

1. Apri `php.ini` file in un editor:

   ```bash
   vim /etc/php/7.2/fpm/php.ini
   ```

   ```bash
   vim /etc/php/7.2/cli/php.ini
   ```

1. Modificate entrambi i file in modo che corrispondano alle seguenti righe:

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >È consigliabile impostare il limite di memoria su 2 G durante il test di Adobe Commerce. Fai riferimento a [Impostazioni PHP richieste](../php-settings.md) per ulteriori informazioni.

1. Salva ed esci dall’editor.

1. Riavvia il `php-fpm` servizio:

   ```bash
   systemctl restart php7.2-fpm
   ```

### Installare e configurare MySQL

Fai riferimento a [MySQL](../database/mysql.md) per ulteriori informazioni.

### Installare e configurare

Esistono diversi modi per scaricare Adobe Commerce, tra cui:

* [Ottieni il metapacchetto Compositore](../../composer.md)

* [Clona l’archivio Git](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

Questo esempio mostra un&#39;installazione basata su Compositore utilizzando la riga di comando.

1. Come [proprietario del file system](../file-system/overview.md), accedere al server applicazioni.

1. Passare alla directory principale dei documenti del server Web o a una directory configurata come directory principale dei documenti host virtuale. In questo esempio viene utilizzato il valore predefinito Ubuntu `/var/www/html`.

   ```bash
   cd /var/www/html
   ```

1. Installa Compositore a livello globale. Il Compositore è necessario per aggiornare le dipendenze prima di installare Adobe Commerce o Magento Open Source:

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Crea un progetto Compositore utilizzando il Magento Open Source o il metapacchetto Adobe Commerce.

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Quando richiesto, immetti [chiavi di autenticazione](../authentication-keys.md). Il tuo _chiave pubblica_ è il tuo nome utente; il tuo _chiave privata_ è la password.

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

1. Installa da [riga di comando](../../advanced.md). In questo esempio si presuppone che la directory di installazione sia denominata `magento2ee`, il `db-host` si trova sullo stesso computer (`localhost`) e che il `db-name`, `db-user`, e `db-password` sono tutti `magento`:

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

### Configura indice

È consigliabile configurare Inginx utilizzando `nginx.conf.sample` file di configurazione fornito nella directory di installazione e nell&#39;host virtuale nginx.

Queste istruzioni presuppongono l’utilizzo della posizione predefinita di Ubuntu per l’host virtuale successivo (ad esempio, `/etc/nginx/sites-available`) e directory principale dei documenti predefinita di Ubuntu (ad esempio, `/var/www/html`), tuttavia, è possibile modificare queste posizioni in base all&#39;ambiente in uso.

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
   >Il `include` la direttiva deve puntare al file di configurazione nginx di esempio nella directory di installazione.

1. Sostituisci `www.magento-dev.com` con il tuo nome di dominio. Deve corrispondere all’URL di base specificato durante l’installazione di Adobe Commerce o Magento Open Source.

1. Salva ed esci dall’editor.

1. Attiva l&#39;host virtuale appena creato creando un collegamento simbolico nel `/etc/nginx/sites-enabled` directory:

   ```bash
   ln -s /etc/nginx/sites-available/magento /etc/nginx/sites-enabled
   ```

1. Verifica che la sintassi sia corretta:

   ```bash
   nginx -t
   ```

1. Inginx di riavvio:

   ```bash
   systemctl restart nginx
   ```

### Verificare l&#39;installazione

Apri un browser web e passa all’URL di base del sito per [verificare l’installazione](../../next-steps/verify.md).

## CentOS 7

La sezione seguente descrive come installare Adobe Commerce 2.x su CentOS 7 utilizzando nginx, PHP e MySQL.

### Installa nginx

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

Dopo aver completato le sezioni seguenti e aver installato l’applicazione, utilizzeremo un file di configurazione di esempio per configurare nginx.

### Installare e configurare php-fpm

Adobe Commerce richiede diversi [PHP](../php-settings.md) per funzionare correttamente. Oltre a queste estensioni, devi anche installare e configurare il `php-fpm` se utilizzi nginx.

1. Installa `php-fpm`:

   ```bash
   yum -y install php70w-fpm
   ```

1. Apri `/etc/php.ini` in un editor.

1. Rimuovi commento da `cgi.fix_pathinfo` e modifica il valore in `0`.

1. Modifica il file in modo che corrisponda alle righe seguenti:

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >È consigliabile impostare il limite di memoria su 2 G durante il test di Adobe Commerce o Magento Open Source. Fai riferimento a [Impostazioni PHP richieste](../php-settings.md) per ulteriori informazioni.

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

1. Creare una directory per il percorso della sessione PHP e cambiare il proprietario in `apache` utente e gruppo:

   ```bash
   mkdir -p /var/lib/php/session/
   ```

   ```bash
   chown -R apache:apache /var/lib/php/
   ```

1. Creare una directory per il percorso della sessione PHP e cambiare il proprietario in `apache` utente e gruppo:

   ```bash
   mkdir -p /run/php-fpm/
   ```

   ```bash
   chown -R apache:apache /run/php-fpm/
   ```

1. Avvia il `php-fpm` e configurarlo per l&#39;avvio al momento dell&#39;avvio:

   ```bash
   systemctl start php-fpm
   ```

   ```bash
   systemctl enable php-fpm
   ```

1. Verificare che `php-fpm` servizio in esecuzione:

   ```bash
   netstat -pl | grep php-fpm.sock
   ```

### Installare e configurare MySQL

Fai riferimento a [MySQL](..//database/mysql.md) per ulteriori informazioni.

### Installare e configurare

Esistono diversi modi per scaricare Adobe Commerce, tra cui:

* [Ottieni il metapacchetto Compositore](../../composer.md)

* [Clona l’archivio Git](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

Questo esempio mostra un&#39;installazione basata su Compositore utilizzando la riga di comando.

1. Come [proprietario del file system](../file-system/overview.md), accedere al server applicazioni.

1. Passare alla directory principale dei documenti del server Web o a una directory configurata come directory principale dei documenti host virtuale. In questo esempio viene utilizzato il valore predefinito Ubuntu `/var/www/html`.

   ```bash
   cd /var/www/html
   ```

1. Installa Compositore a livello globale. Il Compositore è necessario per aggiornare le dipendenze prima di installare Adobe Commerce o Magento Open Source:

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Crea un progetto Compositore utilizzando il Magento Open Source o il metapacchetto Adobe Commerce.

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Quando richiesto, immetti [chiavi di autenticazione](../authentication-keys.md). Il tuo _chiave pubblica_ è il tuo nome utente; il tuo _chiave privata_ è la password.

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

1. Installa da [riga di comando](../../advanced.md). In questo esempio si presuppone che la directory di installazione sia denominata `magento2ee`, il `db-host` si trova sullo stesso computer (`localhost`) e che il `db-name`, `db-user`, e `db-password` sono tutti `magento`:

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

### Configura indice

È consigliabile configurare Inginx utilizzando `nginx.conf.sample` file di configurazione fornito nella directory di installazione e nell&#39;host virtuale nginx.

Queste istruzioni presuppongono l’utilizzo della posizione predefinita di CentOS per l’host virtuale successivo (ad esempio, `/etc/nginx/conf.d`) e directory principale dei documenti predefinita (ad esempio, `/usr/share/nginx/html`), tuttavia, è possibile modificare queste posizioni in base all&#39;ambiente in uso.

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
   >Il `include` la direttiva deve puntare al file di configurazione nginx di esempio nella directory di installazione.

1. Sostituisci `www.magento-dev.com` con il tuo nome di dominio.

1. Salva ed esci dall’editor.

1. Verifica che la sintassi sia corretta:

   ```bash
   nginx -t
   ```

1. Inginx di riavvio:

   ```bash
   systemctl restart nginx
   ```

### Configurare SELinux e Firewall

SELinux è abilitato per impostazione predefinita su CentOS 7. Utilizza il seguente comando per verificare se è in esecuzione:

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

Apri un browser web e passa all’URL di base del sito per [verificare l’installazione](../../next-steps/verify.md).
