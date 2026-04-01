---
title: Installare Apache per le distribuzioni locali
description: Scopri come installare e configurare Apache per le distribuzioni Adobe Commerce on-premise. Abilita i moduli richiesti, le riscritture e le impostazioni ".htaccess".
feature: Install, Configuration
badgePaas: label="On-premise" type="Informative" url="https://experienceleague.adobe.com/it/docs/commerce/user-guides/product-solutions" tooltip="Applicabile solo ai progetti locali di Adobe Commerce."
exl-id: a9a394c9-389f-42ef-9029-dd22c979cfb8
source-git-commit: 352a71cb88ff38c0920201f49f1d7b889509fd61
workflow-type: tm+mt
source-wordcount: '1015'
ht-degree: 0%

---

# Installare Apache per le distribuzioni locali {#apache}

Questa guida illustra come installare Apache per le distribuzioni Adobe Commerce on-premise e configurare le impostazioni Apache richieste da Commerce. Include i requisiti Apache condivisi e le procedure specifiche per il sistema operativo per Ubuntu e CentOS. Adobe consiglia di seguire le istruzioni di configurazione fornite in questa guida per preservare sia la funzionalità che la sicurezza dell’applicazione Commerce.

Adobe supporta le versioni di Apache elencate in [requisiti di sistema](../../system-requirements.md) per la versione di Adobe Commerce in uso. Le versioni supportate variano a seconda della versione. Apache richiede anche una configurazione PHP supportata. Per i requisiti PHP correlati, vedere [Impostazioni PHP](../php-settings.md).

Inizia con la sezione corrispondente al tuo ambiente:

- Se Apache è già installato, inizia con [Rivedi i requisiti di Apache](#review-apache-requirements).
- Se devi installare o aggiornare Apache su Ubuntu, passa a [Installa o aggiorna Apache su Ubuntu](#installing-or-upgrading-apache-on-ubuntu).
- Se devi installare Apache su CentOS, passa a [Installa Apache su CentOS](#installing-apache-on-centos).

## Verifica i requisiti di Apache

Completa questi requisiti su qualsiasi server Apache che ospita Adobe Commerce.

### Configurare le direttive richieste

Impostare `AllowEncodedSlashes` nella configurazione del server (a livello globale) o nelle configurazioni dell&#39;host virtuale per evitare di decodificare le barre codificate che possono causare problemi per gli URL. Ad esempio, quando recuperi prodotti con una barra nello SKU tramite l’API, non desideri convertire la barra. Il seguente blocco di esempio non è completo e sono necessarie altre direttive.

```conf
<VirtualHost *:443>
  # Allow encoded slashes
  AllowEncodedSlashes NoDecode
</VirtualHost>
```

### Configurare riscritture e .htaccess {#apache-rewrites-and-htaccess}

Utilizzare questa sezione per abilitare Apache riscrive e configurare il [file `.htaccess` distribuito](https://httpd.apache.org/docs/current/howto/htaccess.html). Adobe Commerce utilizza le riscritture del server e `.htaccess` per fornire istruzioni a livello di directory per Apache.

>[!IMPORTANT]
>
>Se non si attivano queste impostazioni, in genere non vengono visualizzati stili nella vetrina o nell’amministratore. Può anche impedire ad Apache di applicare le protezioni di sicurezza di Adobe Commerce definite in `.htaccess`.

1. Abilita il modulo di riscrittura Apache:

   ```bash
   a2enmod rewrite
   ```

1. Abilitare l&#39;applicazione per utilizzare il file di configurazione `.htaccess` distribuito.

   1. In Ubuntu, modificare `/etc/apache2/sites-available/000-default.conf`. Per altri layout Apache o se sono necessari parametri aggiuntivi, consulta la [documentazione Apache](https://httpd.apache.org/docs/current/mod/mod_rewrite.html) e la [documentazione sul controllo degli accessi Apache](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).

   1. Aggiungere o aggiornare la direttiva `AllowOverride` per la directory in cui si intende installare Adobe Commerce.

   Se ad esempio si installa Adobe Commerce nel `docroot` predefinito, aggiungere il blocco seguente a `000-default.conf`:

   ```conf
   <Directory "/var/www/html">
     AllowOverride All
   </Directory>
   ```

   >[!NOTE]
   >
   >Se hai eseguito l&#39;aggiornamento da una versione precedente di Apache, cerca prima un blocco `<Directory "/var/www/html">` o `<Directory "/var/www">` esistente in `000-default.conf`. Se installi Adobe Commerce in un altro `docroot`, aggiorna il blocco `<Directory>` corrispondente per quel percorso.

1. Riavvia Apache per applicare le modifiche:

   ```bash
   service apache2 restart
   ```

### Installare i moduli richiesti

Adobe Commerce richiede l’installazione dei seguenti moduli Apache:

- [mod_deflate.c](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html)
- [mod_expires.c](https://httpd.apache.org/docs/2.4/mod/mod_expires.html)
- [mod_headers.c](https://httpd.apache.org/docs/2.4/mod/mod_headers.html)
- [mod_rewrite.c](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html)
- [mod_security.c](https://modsecurity.org)
- [mod_ssl.c](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html)

## Verifica che Apache sia installato

Per verificare che Apache sia installato e visualizzare la versione corrente, immetti:

```bash
apache2 -v
```

Il risultato mostra informazioni simili alle seguenti:

```text
Server version: Apache/<installed-version>
Server built: <build-date>
```

- Se Apache è installato *not*, vedi:
   - [Installare o aggiornare Apache su Ubuntu](#installing-or-upgrading-apache-on-ubuntu)
   - [Installare Apache su CentOS](#installing-apache-on-centos)

## Installare o aggiornare Apache su Ubuntu {#installing-or-upgrading-apache-on-ubuntu}

L’installazione e la configurazione di Apache su Ubuntu è un processo in tre fasi:

1. Installare il software.
1. Abilita riscritture.
1. Specificare `.htaccess` direttive.

Quando si configura la riscrittura del server Apache, è necessario specificare il tipo di direttive che è possibile utilizzare in `.htaccess`, utilizzate dall&#39;applicazione per specificare le regole di riscrittura e le protezioni di sicurezza.

### Installare Apache su Ubuntu

1. Installa Apache se non lo hai già fatto:

   ```bash
   apt-get -y install apache2
   ```

1. Verificare l&#39;installazione:

   ```bash
   apache2 -v
   ```

   Vengono visualizzati messaggi simili al seguente per confermare che l’installazione è andata a buon fine:

   ```text
   Server version: Apache/<installed-version>
   Server built: <build-date>
   ```

1. Procedi alla sezione successiva.

   >[!NOTE]
   >
   >Anche se Apache viene fornito per impostazione predefinita con Ubuntu, consulta la sezione seguente per configurarlo.

### Aggiornamento di Apache su Ubuntu

Se Apache è già installato e si utilizza una versione precedente a `2.4`, eseguire l&#39;aggiornamento ad Apache `2.4` o alla versione più recente supportata dalla versione di Adobe Commerce distribuita. Consulta [requisiti di sistema](../../system-requirements.md).

1. Aggiorna informazioni pacchetto:

   ```bash
   apt-get -y update
   ```

1. Se necessario, aggiungi un archivio che fornisce una versione supportata di Apache per il tuo ambiente.

1. Installare o aggiornare Apache:

   ```bash
   apt-get install -y apache2
   ```

   >[!NOTE]
   >
   >Se il comando `apt-get install` non riesce a causa di dipendenze non soddisfatte, consultare la documentazione del pacchetto del sistema operativo o le risorse di supporto per la distribuzione.

1. Verificare l&#39;installazione:

   ```bash
   apache2 -v
   ```

1. Verifica che la versione installata corrisponda alla versione supportata per la tua versione di Adobe Commerce in [requisiti di sistema](../../system-requirements.md).

1. Abilita [riscritture e `.htaccess` per Ubuntu](#enable-rewrites-and-htaccess-for-ubuntu).

### Abilita riscritture e .htaccess per Ubuntu

1. Apri il file `/etc/apache2/sites-available/000-default.conf` per la modifica:

   ```bash
   vim /etc/apache2/sites-available/000-default.conf
   ```

1. Individua il blocco che inizia con:

   ```conf
   <Directory "/var/www/html">
   ```

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

>[!IMPORTANT]
>
>Se non si attivano queste impostazioni, in genere non vengono visualizzati stili nella vetrina o nell’amministratore. Può anche impedire ad Apache di applicare le protezioni di sicurezza di Adobe Commerce definite in `.htaccess`.

## Installare Apache su CentOS {#installing-apache-on-centos}

L’installazione e la configurazione di Apache su CentOS è un processo in tre fasi:

1. Installare il software
2. Abilita riscritture
3. Specificare `.htaccess` direttive.

Quando si configura la riscrittura del server Apache, è necessario specificare il tipo di direttive che è possibile utilizzare in `.htaccess`, utilizzate dall&#39;applicazione per specificare le regole di riscrittura e le protezioni di sicurezza.

### Installazione di Apache

1. Se non lo hai già fatto, installa Apache.

   ```bash
   yum -y install httpd
   ```

1. Verificare l&#39;installazione:

   ```bash
   httpd -v
   ```

   Vengono visualizzati messaggi simili al seguente per confermare che l’installazione è andata a buon fine:

   ```text
   Server version: Apache/<installed-version>
   Server built: <build-date>
   ```

1. Procedi alla sezione successiva.

   >[!NOTE]
   >
   >Anche se Apache viene fornito per impostazione predefinita con CentOS, consulta la sezione seguente per configurarlo.

### Abilita riscritture e .htaccess per CentOS

1. Apri il file `/etc/httpd/conf/httpd.conf` per la modifica:

   ```bash
   vim /etc/httpd/conf/httpd.conf
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
   >I valori precedenti per `Order` potrebbero non funzionare in tutti i casi. Per ulteriori informazioni, consulta la [documentazione di Apache](https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#order).

1. Salvate il file e uscite dall&#39;editor di testo.

1. Per applicare le impostazioni Apache, riavvia Apache.

   ```bash
   systemctl restart httpd
   ```

>[!IMPORTANT]
>
>Se non si attivano queste impostazioni, in genere non vengono visualizzati stili nella vetrina o nell’amministratore. Può anche impedire ad Apache di applicare le protezioni di sicurezza di Adobe Commerce definite in `.htaccess`.

## Risoluzione degli errori 403 (non consentito)

Se rilevi 403 errori non consentiti durante il tentativo di accesso al sito, puoi aggiornare la configurazione Apache o l’host virtuale per abilitare i visitatori al sito:

### Risolvere gli errori non consentiti 403 per Apache

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
