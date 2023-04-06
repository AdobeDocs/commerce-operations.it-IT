---
title: Modificare il docroot per migliorare la sicurezza
description: Impedisci l’accesso non autorizzato basato su browser al file system locale Adobe Commerce o Magenti Open Source.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '592'
ht-degree: 0%

---


# Modificare il docroot per migliorare la sicurezza

In un’installazione standard con un server web Apache, Adobe Commerce e Magenti Open Source vengono installati nella Web root predefinita: `/var/www/html/magento2`.

La `magento2/` la directory contiene quanto segue:

- `pub/`
- `setup/`
- `var/`

L&#39;applicazione viene servita da `/var/www/html/magento2/pub`. Il resto del file system è vulnerabile perché è accessibile da un browser.
Impostazione della webroot su `pub/` impedisce ai visitatori del sito di accedere ad aree sensibili del file system da un browser.

Questo argomento descrive come modificare il docroot Apache su un&#39;istanza esistente per elaborare i file dal `pub/` directory, più sicura.

## Una nota sull&#39;allegato

Se utilizzi [nginx](../prerequisites/web-server/nginx.md) e [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) file incluso nella directory di installazione, probabilmente stai già servendo i file dalla `pub/` directory.

Se utilizzato nel blocco server che definisce il sito, la `nginx.conf.sample` la configurazione sostituisce le impostazioni docroot del server per elaborare i file dal `pub/` directory. Ad esempio, consulta l’ultima riga nella configurazione seguente:

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

Per completare questa esercitazione, devi accedere a un&#39;installazione funzionante in esecuzione su un [LAMPADA](https://en.wikipedia.org/wiki/LAMP_(software_bundle)) stack:

- Linux
- Apache (2.4+)
- MySQL (5.7+)
- PHP (7.4)
- Elasticsearch (7.x) o OpenSearch (1.2)
- Adobe Commerce o Magento Open Source (2.4+)

>[!NOTE]
>
>Fai riferimento a [Prerequisiti](../prerequisites/overview.md) e [Guida all’installazione](../overview.md) per ulteriori informazioni.

## 1. Modifica la configurazione del server

Il nome e la posizione del file host virtuale dipendono dalla versione di Apache in esecuzione. Questo esempio mostra il nome e la posizione del file host virtuale in Apache v2.4.

1. Accedi al server delle applicazioni.
1. Modifica il file host virtuale:

   ```bash
   vim /etc/apache2/sites-available/000-default.conf
   ```

1. Aggiungi il percorso al `pub/` nella directory `DocumentRoot` direttiva:

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

## 2. Aggiorna l&#39;URL di base

Se hai aggiunto un nome di directory all’hostname o all’indirizzo IP del server per creare l’URL di base quando hai installato l’applicazione (ad esempio `http://192.168.33.10/magento2`), è necessario rimuoverlo.

>[!NOTE]
>
>Sostituisci `192.168.33.10` con il nome host del server.

1. Accedi al database:

   ```bash
   mysql -u <user> -p
   ```

1. Specifica il database creato al momento dell&#39;installazione dell&#39;applicazione:

   ```shell
   use <database-name>
   ```

1. Aggiorna l&#39;URL di base:

   ```shell
   UPDATE core_config_data SET value='http://192.168.33.10' WHERE path='web/unsecure/base_url';
   ```

## 3. Aggiorna il file env.php

Aggiungi il seguente nodo al `env.php` file.

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

Fai riferimento a [riferimento env.php](../../configuration/reference/config-reference-envphp.md) per ulteriori informazioni.

## 4. Modalità di commutazione

[Modalità di applicazione](../../configuration/bootstrap/application-modes.md), che includono `production` e `developer`, sono concepite per migliorare la sicurezza e facilitare lo sviluppo. Come suggeriscono i nomi, è necessario passare a `developer` quando si estende o si personalizza l&#39;applicazione e si passa a `production` in un ambiente live.

Il passaggio tra le modalità è un passo importante per verificare che la configurazione del server funzioni correttamente. È possibile passare da una modalità all’altra utilizzando lo strumento CLI:

1. Vai alla directory di installazione.
1. Passa a `production` modalità.

   ```bash
   bin/magento deploy:mode:set production
   ```

   ```bash
   bin/magento cache:flush
   ```

1. Aggiorna il browser e verifica che la vetrina venga visualizzata correttamente.
1. Passa a `developer` modalità.

   ```bash
   bin/magento deploy:mode:set developer
   ```

   ```bash
   bin/magento cache:flush
   ```

1. Aggiorna il browser e verifica che la vetrina venga visualizzata correttamente.

## 5. Verifica la vetrina

Vai alla vetrina in un browser web per verificare che tutto funzioni.

1. Apri un browser web e immetti il nome host o l’indirizzo IP del server nella barra degli indirizzi. Ad esempio: `http://192.168.33.10`.

   La figura seguente mostra una pagina di esempio di vetrina. Se viene visualizzato come segue, l&#39;installazione è stata un successo!

   ![Storefront che verifica un&#39;installazione riuscita](../../assets/installation/install-success_store.png)

   Fai riferimento a [sezione sulla risoluzione dei problemi](https://support.magento.com/hc/en-us/articles/360032994352) se la pagina visualizza un 404 (Non trovato) o non riesce a caricare altre risorse come immagini, CSS e JS.

1. Prova ad accedere a una directory applicativa da un browser. Aggiungi il nome della directory al nome host o all&#39;indirizzo IP del server nella barra degli indirizzi:

   Se viene visualizzato un messaggio 404 o &quot;Accesso negato&quot;, l&#39;accesso al file system è stato limitato.

   ![Accesso negato](../../assets/installation/access-denied.png)
