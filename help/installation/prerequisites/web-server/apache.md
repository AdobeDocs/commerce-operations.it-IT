---
title: Apache
description: Segui questi passaggi per installare e configurare il server web Apache per le installazioni on-premise di Adobe Commerce e Magenti Open Source.
source-git-commit: 61638d373408d9a7c3c3a935eee61927acfac7a6
workflow-type: tm+mt
source-wordcount: '844'
ht-degree: 0%

---


# Apache

Adobe Commerce supporta Apache 2.4.x.

## Apache direttive richieste

1. Imposta `AllowEncodedSlashes` nella configurazione del server (a livello globale) o nelle configurazioni dell’host virtuale per evitare la decodifica delle barre codificate che possono causare problemi agli URL. Ad esempio, quando recuperi prodotti con una barra nello SKU tramite l’API, non vuoi che venga convertita. Il blocco di esempio non è completo e sono necessarie altre direttive.

   ```conf
   <VirtualHost *:443>
     # Allow encoded slashes
     AllowEncodedSlashes NoDecode
   </VirtualHost>
   ```

## Apache riscrive e htaccess

Questo argomento illustra come abilitare la riscrittura di Apache 2.4 e specificare un&#39;impostazione per la [file di configurazione distribuito, `.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html).

Adobe Commerce e Magenti Open Source utilizzano le riscritture del server e `.htaccess` fornire istruzioni a livello di directory per Apache. Le istruzioni seguenti sono incluse anche in tutte le altre sezioni di questo argomento.

Usa questa sezione per abilitare le riscritture Apache 2.4 e specifica un&#39;impostazione per [file di configurazione distribuito, `.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html)

Adobe Commerce e Magenti Open Source utilizzano le riscritture del server e `.htaccess` fornire istruzioni a livello di directory per Apache.

>[!NOTE]
>
>In genere, se non si abilita queste impostazioni, non verrà visualizzato alcuno stile sulla vetrina o sull&#39;amministratore.

1. Attiva il modulo di riscrittura Apache:

   ```bash
   a2enmod rewrite
   ```

1. Per abilitare l&#39;applicazione all&#39;utilizzo del `.htaccess` file di configurazione, consulta le linee guida [Documentazione di Apache 2.4](https://httpd.apache.org/docs/current/mod/mod_rewrite.html).

   >[!TIP]
   >
   >In Apache 2.4, il file di configurazione del sito predefinito del server è `/etc/apache2/sites-available/000-default.conf`.

   Ad esempio, puoi aggiungere quanto segue alla fine di `000-default.conf`:

   ```terminal
   <Directory "/var/www/html">
       AllowOverride All
   </Directory>
   ```

   >[!NOTE]
   >
   >A volte potrebbero essere necessari parametri aggiuntivi. Per ulteriori informazioni, consulta la sezione [Documentazione di Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).

1. Se hai modificato le impostazioni di Apache, riavvia Apache:

   ```bash
   service apache2 restart
   ```

   >[!NOTE]
   >
   >- Se hai effettuato l’aggiornamento da una versione precedente di Apache, cerca prima `<Directory "/var/www/html">` o `<Directory "/var/www">` in `000-default.conf`.
   >- È necessario modificare il valore di `AllowOverride` nella direttiva per la directory in cui si prevede di installare il software Adobe Commerce o Magenti Open Source. Ad esempio, per installare nel docroot del server web, modifica la direttiva in `<Directory /var/www>`.


>[!NOTE]
>
>In genere, se non si attivano queste impostazioni, gli stili non vengono visualizzati nella vetrina o in Admin.

## Moduli richiesti Apache

Adobe Commerce e Magenti Open Source richiedono l’installazione dei seguenti moduli Apache:

- [mod_deflate.c](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html)
- [mod_expires.c](https://httpd.apache.org/docs/2.4/mod/mod_expires.html)
- [mod_headers.c](https://httpd.apache.org/docs/2.4/mod/mod_headers.html)
- [mod_rewrite.c](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html)
- [mod_security.c](https://modsecurity.org)
- [mod_ssl.c](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html)

## Verificare la versione Apache

Per verificare la versione di Apache in esecuzione, immetti:

```bash
apache2 -v
```

Il risultato viene visualizzato in modo simile al seguente:

```terminal
Server version: Apache/2.4.04 (Ubuntu)
Server built: Jul 22 2020 14:35:32
```

- Se Apache è *not* installati, vedere:
   - [Installazione o aggiornamento di Apache su Ubuntu](#installing-apache-on-ubuntu)
   - [Installazione di Apache su CentOS](#installing-apache-on-centos)

## Installazione o aggiornamento di Apache su Ubuntu

Nelle sezioni seguenti viene illustrato come installare o aggiornare Apache:

- Installa Apache
- Aggiornamento ad Apache 2.4 su Ubuntu per utilizzare PHP 7.4.

### Installazione di Apache su Ubuntu

Per installare la versione predefinita di Apache:

1. Installa Apache

   ```bash
   apt-get -y install apache2
   ```

1. Verifica l’installazione.

   ```bash
   apache2 -v
   ```

   Il risultato viene visualizzato in modo simile al seguente:

   ```terminal
   Server version: Apache/2.4.18 (Ubuntu)
   Server built: 2020-04-15T18:00:57
   ```

1. Abilita [riscrive e `.htaccess`](#apache-rewrites-and-htaccess).

### Aggiornamento di Apache su Ubuntu

Per effettuare l’aggiornamento ad Apache 2.4:

1. Aggiungi il `ppa:ondrej` archivio, che ha Apache 2.4:

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-add-repository ppa:ondrej/apache2
   ```

   ```bash
   apt-get -y update
   ```

1. Installa Apache 2.4:

   ```bash
   apt-get install -y apache2
   ```

   >[!NOTE]
   >
   >Se il comando &#39;apt-get install&#39; non riesce a causa di dipendenze non soddisfatte, consulta una risorsa come [https://askubuntu.com/](https://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa).

1. Verifica l’installazione.

   ```bash
   apache2 -v
   ```

   Devono essere visualizzati messaggi simili ai seguenti:

   ```terminal
   Server version: Apache/2.4.10 (Ubuntu)
   Server built: Jul 22 2020 22:46:25
   ```

1. Abilita [riscrive e `.htaccess`](#apache-rewrites-and-htaccess).

## Installazione di Apache su CentOS

Adobe Commerce e Magenti Open Source richiedono la riscrittura del server tramite Apache. È inoltre necessario specificare il tipo di direttive che è possibile utilizzare in `.htaccess`, utilizzato dall&#39;applicazione per specificare le regole di riscrittura.

L’installazione e la configurazione di Apache è fondamentalmente un processo in tre fasi: installare il software, attivare le riscritture e specificare `.htaccess` direttive.

### Installazione di Apache

1. Installa Apache 2.4 se non lo hai già fatto.

   ```bash
   yum -y install httpd
   ```

1. Verifica l’installazione:

   ```bash
   httpd -v
   ```

   Messaggi simili alla seguente visualizzazione per confermare che l&#39;installazione è riuscita:

   ```terminal
   Server version: Apache/2.4.40 (Unix)
   Server built: Oct 16 2020 14:48:21
   ```

1. Procedi alla sezione successiva.

   >[!NOTE]
   >
   >Anche se Apache 2.4 è fornito per impostazione predefinita con CentOS, consulta la sezione seguente per configurarlo.

### Abilita riscritture e .htaccess per CentOS

1. Apri `/etc/httpd/conf/httpd.conf` file per la modifica:

   ```bash
   vim /etc/httpd/conf/httpd.conf`
   ```

1. Individua il blocco che inizia con:

   ```conf
   <Directory "/var/www/html">
   ```

1. Modifica il valore di `AllowOverride` a `All`.

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
   >I valori precedenti per `Order` potrebbe non funzionare in tutti i casi. Per ulteriori informazioni, consulta la documentazione di Apache ([2,4](https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#order)).

1. Salva il file e esci dall’editor di testo.

1. Per applicare le impostazioni Apache, riavvia Apache.

   ```bash
   service apache2 restart
   ```

>[!NOTE]
>
>In genere, se non si abilita queste impostazioni, non verrà visualizzato alcuno stile sulla vetrina o sull&#39;amministratore.

### Abilita riscritture e .htaccess per Ubuntu

1. Apri `/etc/apache2/sites-available/default` file per la modifica:

   ```bash
   vim /etc/apache2/sites-available/default
   ```

1. Individua il blocco che inizia con:

   `<Directory "/var/www/html">`

1. Modifica il valore di `AllowOverride` a `All`.

   Ad esempio:

   ```conf
   <Directory "/var/www/html">
     Options Indexes FollowSymLinks MultiViews
     AllowOverride All
     Order allow,deny
     Allow from all
   </Directory>
   ```

1. Salva il file e esci dall’editor di testo.

1. Configura Apache per utilizzare la funzione `mod_rewrite` modulo:

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

## Risoluzione degli errori 403 (proibito)

Se incontri 403 Errori proibiti quando tenti di accedere al sito, puoi aggiornare la configurazione Apache o la configurazione dell&#39;host virtuale per consentire ai visitatori del sito:

### Risoluzione degli errori 403 non consentiti per Apache 2.4

Per consentire ai visitatori del sito web di accedere al sito, utilizza uno dei [Richiedi direttive](https://httpd.apache.org/docs/2.4/howto/access.html).

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
>I valori precedenti per `Order` potrebbe non funzionare in tutti i casi. Per ulteriori informazioni, consulta la sezione [Documentazione di Apache](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).
