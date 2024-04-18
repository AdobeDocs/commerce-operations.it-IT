---
title: Modifica la directory principale dei documenti per migliorare la sicurezza
description: Impedisci l’accesso non autorizzato al file system locale di Adobe Commerce basato su browser.
feature: Install, Security
exl-id: aabe148d-00c8-4011-a629-aa5abfa6c682
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---

# Modifica la directory principale dei documenti per migliorare la sicurezza

In un’installazione standard con un server web Apache, Adobe Commerce viene installato sulla directory principale web predefinita: `/var/www/html/magento2`.

Il `magento2/` la directory contiene quanto segue:

- `pub/`
- `setup/`
- `var/`

L’applicazione viene trasmessa da `/var/www/html/magento2/pub`. Il resto del file system è vulnerabile perché è accessibile da un browser.
Impostazione di Webroot su `pub/` impedisce ai visitatori del sito di accedere ad aree sensibili del file system da un browser.

Questo argomento descrive come modificare la directory principale dei documenti Apache su un’istanza esistente per distribuire i file dalla directory `pub/` , che è più sicuro.

## Nota sull&#39;indice

Se sta usando [nginx](../prerequisites/web-server/nginx.md) e [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) file incluso nella directory di installazione, probabilmente i file sono già in uso da `pub/` directory.

Se utilizzato nel blocco del server che definisce il sito, il `nginx.conf.sample` sostituisce le impostazioni della directory principale dei documenti del server per distribuire i file da `pub/` directory. Ad esempio, vedi l’ultima riga nella seguente configurazione:

```conf
# /etc/nginx/sites-available/magento

upstream fastcgi_backend {
   server  unix:/run/php/php7.4-fpm.sock;
}

server {

         listen 80;
         server_name 192.168.33.10;
         set $MAGE_ROOT /var/www/html/magento2ce;
         include /var/www/html/magento2ce/nginx.conf.sample;
}
```

## Prima di iniziare

Per completare questa esercitazione, è necessario accedere a un&#39;installazione funzionante in esecuzione su uno stack LAMP:

- Linux
- Apache (2.4+)
- MySQL (5.7+)
- PHP (7.4)
- Elasticsearch (7.x) o OpenSearch (1.2)
- Adobe Commerce (2.4+)

>[!NOTE]
>
>Fai riferimento a [Prerequisiti](../prerequisites/overview.md) e [Guida all’installazione](../overview.md) per ulteriori informazioni.

## 1. Modifica la configurazione del server

Il nome e la posizione del file host virtuale dipendono dalla versione di Apache in esecuzione. Questo esempio mostra il nome e la posizione del file host virtuale in Apache v2.4.

1. Accedere al server applicazioni.
1. Modifica il file host virtuale:

   ```bash
   vim /etc/apache2/sites-available/000-default.conf
   ```

1. Aggiungi il percorso al tuo `pub/` alla directory `DocumentRoot` direttiva:

   ```conf
   <VirtualHost *:80>
   
            ServerAdmin webmaster@localhost
            DocumentRoot /var/www/html/magento2ce/pub
   
            ErrorLog ${APACHE_LOG_DIR}/error.log
            CustomLog ${APACHE_LOG_DIR}/access.log combined
   
            <Directory "/var/www/html">
                        AllowOverride all
            </Directory>
    </VirtualHost>
   ```

1. Riavvia Apache:

   ```bash
   systemctl restart apache2
   ```

## 2. Aggiorna l’URL di base

Se hai aggiunto un nome di directory al nome host o all’indirizzo IP del server per creare l’URL di base quando hai installato l’applicazione (ad esempio `http://192.168.33.10/magento2`), è necessario rimuoverlo.

>[!NOTE]
>
>Sostituisci `192.168.33.10` con il nome host del server.

1. Accedi al database:

   ```bash
   mysql -u <user> -p
   ```

1. Specificare il database creato al momento dell&#39;installazione dell&#39;applicazione:

   ```shell
   use <database-name>
   ```

1. Aggiornare l’URL di base:

   ```shell
   UPDATE core_config_data SET value='http://192.168.33.10' WHERE path='web/unsecure/base_url';
   ```

## 3. Aggiornare il file env.php

Aggiungi il seguente nodo alla `env.php` file.

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

Consulta la sezione [riferimento env.php](../../configuration/reference/config-reference-envphp.md) per ulteriori informazioni.

## 4. Cambiare modalità

[Modalità di applicazione](../../configuration/bootstrap/application-modes.md), che includono `production` e `developer`, sono progettate per migliorare la sicurezza e semplificare lo sviluppo. Come suggeriscono i nomi, è necessario passare a `developer` quando si estende o si personalizza l&#39;applicazione e si passa a `production` in esecuzione in un ambiente live.

Il passaggio da una modalità all’altra è un passaggio importante per verificare che la configurazione del server funzioni correttamente. È possibile passare da una modalità all&#39;altra utilizzando lo strumento CLI:

1. Vai alla directory di installazione.
1. Passa a `production` modalità.

   ```bash
   bin/magento deploy:mode:set production
   ```

   ```bash
   bin/magento cache:flush
   ```

1. Aggiorna il browser e verifica che la vetrina sia visualizzata correttamente.
1. Passa a `developer` modalità.

   ```bash
   bin/magento deploy:mode:set developer
   ```

   ```bash
   bin/magento cache:flush
   ```

1. Aggiorna il browser e verifica che la vetrina sia visualizzata correttamente.

## 5. Verificare la vetrina

Vai alla vetrina in un browser web per verificare che tutto funzioni.

1. Apri un browser web e immetti il nome host o l’indirizzo IP del server nella barra degli indirizzi. Ad esempio: `http://192.168.33.10`.

   La figura seguente mostra una pagina di vetrina di esempio. Se viene visualizzato come segue, l&#39;installazione è stata completata correttamente.

   ![Storefront che verifica la corretta installazione](../../assets/installation/install-success_store.png)

   Consulta la sezione [sezione risoluzione dei problemi](https://support.magento.com/hc/en-us/articles/360032994352) se la pagina mostra un errore 404 (Non trovato) o se non riesce a caricare altre risorse come immagini, CSS e JS.

1. Provare ad accedere a una directory dell&#39;applicazione da un browser. Aggiungi il nome della directory al nome host o all’indirizzo IP del server nella barra degli indirizzi:

   Se viene visualizzato il messaggio 404 o &quot;Accesso negato&quot;, l&#39;accesso al file system è stato limitato.

   ![Accesso negato](../../assets/installation/access-denied.png)
