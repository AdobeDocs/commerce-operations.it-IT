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

In un&#39;installazione standard con un server Web Apache, Adobe Commerce viene installato nella directory principale Web predefinita: `/var/www/html/magento2`.

La directory `magento2/` contiene quanto segue:

- `pub/`
- `setup/`
- `var/`

L&#39;applicazione è servita da `/var/www/html/magento2/pub`. Il resto del file system è vulnerabile perché è accessibile da un browser.
L&#39;impostazione della directory Web `pub/` impedisce ai visitatori del sito di accedere ad aree sensibili del file system da un browser.

In questo argomento viene descritto come modificare la directory principale dei documenti Apache in un&#39;istanza esistente per distribuire i file dalla directory `pub/`, che è più sicura.

## Nota sull&#39;indice

Se si utilizza [nginx](../prerequisites/web-server/nginx.md) e il file [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) incluso nella directory di installazione, è probabile che si stiano già distribuendo file dalla directory `pub/`.

Se utilizzata nel blocco del server che definisce il sito, la configurazione di `nginx.conf.sample` sostituisce le impostazioni della directory principale dei documenti del server per distribuire i file dalla directory di `pub/`. Ad esempio, vedi l’ultima riga nella seguente configurazione:

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
>Per ulteriori informazioni, consultare [Prerequisiti](../prerequisites/overview.md) e la [Guida all&#39;installazione](../overview.md).

## &#x200B;1. Modifica la configurazione del server

Il nome e la posizione del file host virtuale dipendono dalla versione di Apache in esecuzione. Questo esempio mostra il nome e la posizione del file host virtuale in Apache v2.4.

1. Accedere al server applicazioni.
1. Modifica il file host virtuale:

   ```bash
   vim /etc/apache2/sites-available/000-default.conf
   ```

1. Aggiungere il percorso della directory `pub/` alla direttiva `DocumentRoot`:

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

## &#x200B;2. Aggiorna l’URL di base

Se si è aggiunto un nome di directory al nome host o all&#39;indirizzo IP del server per creare l&#39;URL di base al momento dell&#39;installazione dell&#39;applicazione (ad esempio `http://192.168.33.10/magento2`), è necessario rimuoverlo.

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

## &#x200B;3. Aggiornare il file env.php

Aggiungere il nodo seguente al file `env.php`.

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

Per ulteriori informazioni, fare riferimento al [riferimento env.php](../../configuration/reference/config-reference-envphp.md).

## &#x200B;4. Cambiare modalità

[Le modalità applicazione](../../configuration/bootstrap/application-modes.md), che includono `production` e `developer`, sono progettate per migliorare la sicurezza e semplificare lo sviluppo. Come suggeriscono i nomi, è necessario passare alla modalità `developer` quando si estende o si personalizza l&#39;applicazione e passare alla modalità `production` quando l&#39;esecuzione avviene in un ambiente live.

Il passaggio da una modalità all’altra è un passaggio importante per verificare che la configurazione del server funzioni correttamente. È possibile passare da una modalità all&#39;altra utilizzando lo strumento CLI:

1. Vai alla directory di installazione.
1. Passa alla modalità `production`.

   ```bash
   bin/magento deploy:mode:set production
   ```

   ```bash
   bin/magento cache:flush
   ```

1. Aggiorna il browser e verifica che la vetrina sia visualizzata correttamente.
1. Passa alla modalità `developer`.

   ```bash
   bin/magento deploy:mode:set developer
   ```

   ```bash
   bin/magento cache:flush
   ```

1. Aggiorna il browser e verifica che la vetrina sia visualizzata correttamente.

## &#x200B;5. Verificare la vetrina

Vai alla vetrina in un browser web per verificare che tutto funzioni.

1. Apri un browser web e immetti il nome host o l’indirizzo IP del server nella barra degli indirizzi. Ad esempio, `http://192.168.33.10`.

   La figura seguente mostra una pagina di vetrina di esempio. Se viene visualizzato come segue, l&#39;installazione è stata completata correttamente.

   ![Storefront che verifica la corretta installazione](../../assets/installation/install-success_store.png)

   Consulta la [sezione per la risoluzione dei problemi](https://support.magento.com/hc/en-us/articles/360032994352) se nella pagina viene visualizzato il valore 404 (Non trovato) o se non è possibile caricare altre risorse come immagini, CSS e JS.

1. Provare ad accedere a una directory dell&#39;applicazione da un browser. Aggiungi il nome della directory al nome host o all’indirizzo IP del server nella barra degli indirizzi:

   Se viene visualizzato il messaggio 404 o &quot;Accesso negato&quot;, l&#39;accesso al file system è stato limitato.

   ![Accesso negato](../../assets/installation/access-denied.png)
