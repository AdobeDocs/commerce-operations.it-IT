---
title: Apache
description: Per installare e configurare il server web Apache per le installazioni locali di Adobe Commerce, segui la procedura riportata di seguito.
exl-id: a9a394c9-389f-42ef-9029-dd22c979cfb8
source-git-commit: f8c5d714a4e96d0508f745d1b7617696c8cc94a7
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---

# Apache

Adobe Commerce supporta Apache 2.4.x.

## Direttive obbligatorie Apache

1. Impostare `AllowEncodedSlashes` nella configurazione del server (a livello globale) o nelle configurazioni dell&#39;host virtuale per evitare di decodificare le barre codificate che potrebbero causare problemi per gli URL. Ad esempio, quando recuperi prodotti con una barra nello SKU tramite l’API, non desideri convertirli. Il blocco campione non è completo e sono necessarie altre direttive.

   ```conf
   <VirtualHost *:443>
     # Allow encoded slashes
     AllowEncodedSlashes NoDecode
   </VirtualHost>
   ```

## Apache riscrive e htaccess

In questo argomento viene illustrato come abilitare le riscritture di Apache 2.4 e specificare un&#39;impostazione per il [file di configurazione distribuito, `.htaccess`](https://github.com/magento/magento2/blob/2.4-develop/.htaccess.sample).

Adobe Commerce utilizza le riscritture del server e `.htaccess` per fornire istruzioni a livello di directory per Apache. Le seguenti istruzioni sono incluse anche in tutte le altre sezioni di questo argomento.

Utilizzare questa sezione per abilitare le riscritture di Apache 2.4 e specificare un&#39;impostazione per il [file di configurazione distribuito, `.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html)

Adobe Commerce utilizza le riscritture del server e `.htaccess` per fornire istruzioni a livello di directory per Apache.

>[!NOTE]
>
>Se non si attivano queste impostazioni, in genere non vengono visualizzati stili nella vetrina o nell’amministratore.

1. Abilita il modulo di riscrittura Apache:

   ```bash
   a2enmod rewrite
   ```

1. Per abilitare l&#39;applicazione all&#39;utilizzo del file di configurazione `.htaccess` distribuito, vedere le linee guida nella [documentazione di Apache 2.4](https://httpd.apache.org/docs/current/mod/mod_rewrite.html).

   >[!TIP]
   >
   >In Apache 2.4, il file di configurazione del sito predefinito del server è `/etc/apache2/sites-available/000-default.conf`.

   Ad esempio, è possibile aggiungere quanto segue alla fine di `000-default.conf`:

   ```
   <Directory "/var/www/html">
       AllowOverride All
   </Directory>
   ```

   >[!NOTE]
   >
   >A volte, potrebbero essere necessari parametri aggiuntivi. Per ulteriori informazioni, consulta la [documentazione di Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).

1. Se hai modificato le impostazioni di Apache, riavvia Apache:

   ```bash
   service apache2 restart
   ```

   >[!NOTE]
   >
   >- Se hai eseguito l&#39;aggiornamento da una versione precedente di Apache, cerca prima `<Directory "/var/www/html">` o `<Directory "/var/www">` in `000-default.conf`.
   >- È necessario modificare il valore di `AllowOverride` nella direttiva per la directory in cui si prevede di installare il software Adobe Commerce. Ad esempio, per eseguire l&#39;installazione nella directory principale dei documenti del server Web, modificare la direttiva in `<Directory /var/www>`.

>[!NOTE]
>
>Se non si attivano queste impostazioni, in genere gli stili non vengono visualizzati nella vetrina o in Amministrazione.

## Moduli richiesti Apache

Adobe Commerce richiede l’installazione dei seguenti moduli Apache:

- [mod_deflate.c](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html)
- [mod_expires.c](https://httpd.apache.org/docs/2.4/mod/mod_expires.html)
- [mod_headers.c](https://httpd.apache.org/docs/2.4/mod/mod_headers.html)
- [mod_rewrite.c](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html)
- [mod_security.c](https://modsecurity.org)
- [mod_ssl.c](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html)

## Verifica la versione di Apache

Per verificare la versione di Apache in esecuzione, immetti:

```bash
apache2 -v
```

Il risultato è simile al seguente:

```
Server version: Apache/2.4.04 (Ubuntu)
Server built: Jul 22 2020 14:35:32
```

- Se Apache è installato *not*, vedi:
   - [Installazione o aggiornamento di Apache su Ubuntu](#installing-apache-on-ubuntu)
   - [Installazione di Apache su CentOS](#installing-apache-on-centos)

## Installazione o aggiornamento di Apache su Ubuntu

Le sezioni seguenti spiegano come installare o aggiornare Apache:

- Installare Apache
- Effettua l’aggiornamento ad Apache 2.4 su Ubuntu per utilizzare PHP 7.4.

### Installazione di Apache su Ubuntu

Per installare la versione predefinita di Apache:

1. Installare Apache

   ```bash
   apt-get -y install apache2
   ```

1. Verificare l&#39;installazione.

   ```bash
   apache2 -v
   ```

   Il risultato è simile al seguente:

   ```
   Server version: Apache/2.4.18 (Ubuntu)
   Server built: 2020-04-15T18:00:57
   ```

1. Abilita [riscritture e `.htaccess`](#apache-rewrites-and-htaccess).

### Aggiornamento di Apache su Ubuntu

Per effettuare l’aggiornamento ad Apache 2.4:

1. Aggiungi l&#39;archivio `ppa:ondrej`, che ha Apache 2.4:

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-add-repository ppa:ondrej/apache2
   ```

   ```bash
   apt-get -y update
   ```

1. Installare Apache 2.4:

   ```bash
   apt-get install -y apache2
   ```

   >[!NOTE]
   >
   >Se il comando &#39;apt-get install&#39; non riesce a causa di dipendenze non soddisfatte, consultare una risorsa come [https://askubuntu.com/](https://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa).

1. Verificare l&#39;installazione.

   ```bash
   apache2 -v
   ```

   Dovrebbero essere visualizzati messaggi simili ai seguenti:

   ```
   Server version: Apache/2.4.10 (Ubuntu)
   Server built: Jul 22 2020 22:46:25
   ```

1. Abilita [riscritture e `.htaccess`](#apache-rewrites-and-htaccess).

## Installazione di Apache su CentOS

Adobe Commerce richiede la riscrittura del server Apache. È inoltre necessario specificare il tipo di direttive che è possibile utilizzare in `.htaccess`, utilizzate dall&#39;applicazione per specificare le regole di riscrittura.

L&#39;installazione e la configurazione di Apache sono fondamentalmente tre passaggi: installare il software, abilitare le riscritture e specificare `.htaccess` direttive.

### Installazione di Apache

1. Se non lo hai già fatto, installa Apache 2.4.

   ```bash
   yum -y install httpd
   ```

1. Verificare l&#39;installazione:

   ```bash
   httpd -v
   ```

   Vengono visualizzati messaggi simili al seguente per confermare che l’installazione è andata a buon fine:

   ```
   Server version: Apache/2.4.40 (Unix)
   Server built: Oct 16 2020 14:48:21
   ```

1. Procedi alla sezione successiva.

   >[!NOTE]
   >
   >Anche se Apache 2.4 è fornito per impostazione predefinita con CentOS, consulta la sezione seguente per configurarlo.

### Abilita riscritture e .htaccess per CentOS

1. Apri il file `/etc/httpd/conf/httpd.conf` per la modifica:

   ```bash
   vim /etc/httpd/conf/httpd.conf`
   ```

1. Individua il blocco che inizia con:

   ```conf
   <Directory "/var/www/html">
   ```

1. Modificare il valore di `AllowOverride` in `All`.

   Ad esempio:

   ```conf
   <Directory "/var/www/">
     Options Indexes FollowSymLinks MultiViews
     AllowOverride All
     Order allow,deny
     Allow from all
   </Directory>
   ```

   >[!NOTE]
   >
   >I valori precedenti per `Order` potrebbero non funzionare in tutti i casi. Per ulteriori informazioni, consulta la documentazione di Apache ([2.4](https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#order)).

1. Salvate il file e uscite dall&#39;editor di testo.

1. Per applicare le impostazioni Apache, riavvia Apache.

   ```bash
   service apache2 restart
   ```

>[!NOTE]
>
>Se non si attivano queste impostazioni, in genere non vengono visualizzati stili nella vetrina o nell’amministratore.

### Abilita riscritture e .htaccess per Ubuntu

1. Apri il file `/etc/apache2/sites-available/default` per la modifica:

   ```bash
   vim /etc/apache2/sites-available/default
   ```

1. Individua il blocco che inizia con:

   `<Directory "/var/www/html">`

1. Modificare il valore di `AllowOverride` in `All`.

   Ad esempio:

   ```conf
   <Directory "/var/www/html">
     Options Indexes FollowSymLinks MultiViews
     AllowOverride All
     Order allow,deny
     Allow from all
   </Directory>
   ```

1. Salvate il file e uscite dall&#39;editor di testo.

1. Configurare Apache per l&#39;utilizzo del modulo `mod_rewrite`:

   ```bash
   cd /etc/apache2/mods-enabled
   ```

   ```bash
   ln -s ../mods-available/rewrite.load
   ```

1. Riavvia Apache per applicare le modifiche:

   ```bash
   service apache2 restart
   ```

## Risoluzione degli errori 403 (non consentito)

Se rilevi 403 errori non consentiti durante il tentativo di accesso al sito, puoi aggiornare la configurazione Apache o l’host virtuale per abilitare i visitatori al sito:

### Risoluzione di errori 403 non consentiti per Apache 2.4

Per consentire ai visitatori del sito Web di accedere al sito, utilizzare una delle [direttive obbligatorie](https://httpd.apache.org/docs/2.4/howto/access.html).

Ad esempio:

```conf
<Directory "/var/www/">
  Options Indexes FollowSymLinks MultiViews
  AllowOverride All
  Order allow,deny
  Require all granted
</Directory>
```

>[!NOTE]
>
>I valori precedenti per `Order` potrebbero non funzionare in tutti i casi. Per ulteriori informazioni, consulta la [documentazione di Apache](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).
