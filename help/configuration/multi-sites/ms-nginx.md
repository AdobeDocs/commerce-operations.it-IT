---
title: Configurazione di più siti web con Nginx
description: Segui questa esercitazione per configurare più siti web con Node.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '959'
ht-degree: 0%

---


# Configurazione di più siti web con Nginx

Presupponiamo che:

- Si sta lavorando su una macchina di sviluppo (laptop, macchina virtuale o simili).

   Potrebbero essere necessarie attività aggiuntive per distribuire più siti web in un ambiente in hosting; per ulteriori informazioni, consulta il provider di hosting .

   Sono necessarie ulteriori attività per configurare Adobe Commerce sull’infrastruttura cloud. Dopo aver completato le attività discusse in questo argomento, vedi [Configurazione di più siti web o negozi](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) in _Guida a Commerce on Cloud Infrastructure_.

- Accetti più domini in un file host virtuale o utilizzi un host virtuale per sito web; i file di configurazione dell&#39;host virtuale si trovano in `/etc/nginx/sites-available`.
- Utilizzi le `nginx.conf.sample` fornito da Commerce solo con le modifiche discusse in questa esercitazione.
- Il software Commerce è installato in `/var/www/html/magento2`.
- Sono disponibili due siti web diversi da quelli predefiniti:

   - `french.mysite.mg` con codice del sito web `french` e memorizzare il codice della vista `fr`
   - `german.mysite.mg` con codice del sito web `german` e memorizzare il codice della vista `de`
   - `mysite.mg` è la visualizzazione predefinita del sito web e dello store

>[!TIP]
>
>Fai riferimento a [Creare siti web](ms-admin.md#step-2-create-websites) e [Creare viste store](ms-admin.md#step-4-create-store-views) per informazioni su come individuare questi valori.

Di seguito è riportata una roadmap per la configurazione di più siti web con l’allegato:

1. [Configurare siti web, negozi e viste store](ms-admin.md) nell&#39;amministratore.
1. Crea un [Nginx host virtuale](#step-2-create-nginx-virtual-hosts)) per mappare molti siti web o un host virtuale Nginx per sito web Commerce (passaggi descritti di seguito).
1. Passa i valori della [Variabili di MAGE](ms-overview.md) `$MAGE_RUN_TYPE` e `$MAGE_RUN_CODE` per l&#39;inserimento utilizzando il Magento fornito `nginx.conf.sample` (Procedura dettagliata di seguito).

   - `$MAGE_RUN_TYPE` può essere `store` o `website`:

      - Utilizzo `website` per caricare il sito web nella vetrina.
      - Utilizzo `store` per caricare qualsiasi vista store nella vetrina.
   - `$MAGE_RUN_CODE` è il codice univoco della visualizzazione del sito web o del negozio che corrisponde a `$MAGE_RUN_TYPE`.


1. Aggiorna la configurazione dell’URL di base sull’amministratore Commerce.

## Passaggio 1: Crea siti web, store e visualizzazioni store nell’Admin

Vedi [Configurazione di più siti web, negozi e viste store nell’Admin](ms-admin.md).

## Passaggio 2: Creare host virtuali nginx

Questo passaggio illustra come caricare i siti web sulla vetrina. È possibile utilizzare siti web o viste store; se utilizzi le viste store, devi regolare di conseguenza i valori dei parametri. Devi completare le attività di questa sezione come utente con `sudo` privilegi.

Utilizzando una sola [file host virtuale nginx](#step-2-create-nginx-virtual-hosts), puoi mantenere semplice e pulita la configurazione dell’nginx. Utilizzando diversi file host virtuali, è possibile personalizzare ogni archivio (per utilizzare una posizione personalizzata per `french.mysite.mg` per esempio).

**Per creare un host virtuale** (semplificato):

Questa configurazione si espande [configurazione nginx](../../installation/prerequisites/web-server/nginx.md).

1. Apri un editor di testo e aggiungi il seguente contenuto a un nuovo file denominato `/etc/nginx/sites-available/magento`:

   ```conf
   map $http_host $MAGE_RUN_CODE {
       default '';
       french.mysite.mg french;
       german.mysite.mg german;
   }
   
   server {
       listen 80;
       server_name mysite.mg french.mysite.mg german.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. Salva le modifiche apportate ai file e esci dall’editor di testo.
1. Verifica la configurazione del server:

   ```bash
   nginx -t
   ```

1. In caso di esito positivo, viene visualizzato il seguente messaggio:

   ```terminal
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   Se vengono visualizzati degli errori, controlla la sintassi dei file di configurazione dell&#39;host virtuale.

1. Crea un collegamento simbolico nel `/etc/nginx/sites-enabled` directory:

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/magento magento
   ```

Per maggiori dettagli sulla direttiva sulla mappa, vedi [la documentazione dell&#39;allegato sulla direttiva sulla mappa](http://nginx.org/en/docs/http/ngx_http_map_module.html#map).


**Per creare più host virtuali**:

1. Apri un editor di testo e aggiungi il seguente contenuto a un nuovo file denominato `/etc/nginx/sites-available/french.mysite.mg`:

   ```conf
   server {
       listen 80;
       server_name french.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       set $MAGE_RUN_CODE french;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. Crea un altro file denominato `german.mysite.mg` nella stessa directory con i seguenti contenuti:

   ```conf
   server {
       listen 80;
       server_name german.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       set $MAGE_RUN_CODE german;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. Salva le modifiche apportate ai file e esci dall’editor di testo.
1. Verifica la configurazione del server:

   ```bash
   nginx -t
   ```

1. In caso di esito positivo, viene visualizzato il seguente messaggio:

   ```terminal
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   Se vengono visualizzati degli errori, controlla la sintassi dei file di configurazione dell&#39;host virtuale.

1. Creare collegamenti simbolici nel `/etc/nginx/sites-enabled` directory:

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/french.mysite.mg french.mysite.mg
   ```

   ```bash
   ln -s /etc/nginx/sites-available/german.mysite.mg german.mysite.mg
   ```

## Passaggio 3: Modifica nginx.conf.sample

>[!TIP]
>
>Non modificare il `nginx.conf.sample` file; si tratta di un file Commerce di base che può essere aggiornato con ogni nuova versione. Invece, copia il `nginx.conf.sample` file, rinominarlo e quindi modificare il file copiato.

**Per modificare il punto di ingresso PHP per l&#39;applicazione principale**:

Per modificare il `nginx.conf.sample` file**:

1. Apri un editor di testo e controlla il `nginx.conf.sample` file ,`<magento2_installation_directory>/nginx.conf.sample`. Cerca la sezione seguente:

   ```conf
   # PHP entry point for main application
   location ~ (index|get|static|report|404|503|health_check)\.php$ {
       try_files $uri =404;
       fastcgi_pass   fastcgi_backend;
       fastcgi_buffers 1024 4k;
   
       fastcgi_param  PHP_FLAG  "session.auto_start=off \n suhosin.session.cryptua=off";
       fastcgi_param  PHP_VALUE "memory_limit=1G \n max_execution_time=18000";
       fastcgi_read_timeout 600s;
       fastcgi_connect_timeout 600s;
   
       fastcgi_index  index.php;
       fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
       include        fastcgi_params;
   }
   ```

1. Aggiorna `nginx.conf.sample` file con le due righe seguenti prima dell&#39;istruzione include:

   ```conf
   fastcgi_param MAGE_RUN_TYPE $MAGE_RUN_TYPE;
   fastcgi_param MAGE_RUN_CODE $MAGE_RUN_CODE;
   ```

Un esempio di punto di ingresso PHP aggiornato per l&#39;applicazione principale è il seguente:

```conf
# PHP entry point for main application

location ~ (index|get|static|report|404|503|health_check)\.php$ {
    try_files $uri =404;
    fastcgi_pass   fastcgi_backend;
    fastcgi_buffers 1024 4k;

    fastcgi_param  PHP_FLAG  "session.auto_start=off \n suhosin.session.cryptua=off";
    fastcgi_param  PHP_VALUE "memory_limit=1G \n max_execution_time=18000";
    fastcgi_read_timeout 600s;
    fastcgi_connect_timeout 600s;

    fastcgi_index  index.php;
    fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
    # START - Multisite customization
    fastcgi_param MAGE_RUN_TYPE $MAGE_RUN_TYPE;
    fastcgi_param MAGE_RUN_CODE $MAGE_RUN_CODE;
    # END - Multisite customization
    include        fastcgi_params;
}
```

## Passaggio 4: Aggiorna la configurazione dell&#39;URL di base

È necessario aggiornare l’URL di base per `french` e `german` siti web nell’amministratore Commerce.

### Aggiorna URL base sito Web francese

1. Accedi all’amministratore Commerce e passa a **Negozi** > **Impostazioni** > **Configurazione** > **Generale** > **Web**.
1. Modificare la _ambito di configurazione_ al `french` sito web.
1. Espandi **URL di base** e aggiorna la sezione **URL di base** e **URL collegamento di base** valore a `http://french.magento24.com/`.
1. Espandi **URL di base (sicuro)** e aggiorna la sezione **URL di base sicuro** e **URL collegamento di base sicuro** valore a `https://french.magento24.com/`.
1. Fai clic su **Salva configurazione** e salva le modifiche di configurazione.

### Aggiorna URL di base sito Web tedesco

1. Accedi all’amministratore Commerce e passa a **Negozi** > **Impostazioni** > **Configurazione** > **Generale** > **Web**.
1. Modificare la _ambito di configurazione_ al `german` sito web.
1. Espandi **URL di base** e aggiorna la sezione **URL di base** e **URL collegamento di base** valore a `http://german.magento24.com/`.
1. Espandi **URL di base (sicuro)** e aggiorna la sezione **URL di base sicuro** e **URL collegamento di base sicuro** valore a `https://german.magento24.com/`.
1. Fai clic su **Salva configurazione** e salva le modifiche di configurazione.

### Pulisci la cache

Esegui il seguente comando per pulire il `config` e `full_page` cache.

```bash
bin/magento cache:clean config full_page
```

## Verificare il sito

A meno che il DNS non sia configurato per gli URL degli archivi, devi aggiungere un percorso statico all&#39;host nel tuo `hosts` file:

1. Individuare il sistema operativo `hosts` file.
1. Aggiungi il percorso statico nel formato:

   ```conf
   <ip-address> french.mysite.mg
   <ip-address> german.mysite.mg
   ```

1. Vai a uno dei seguenti URL nel browser:

   ```http
   http://mysite.mg/admin
   http://french.mysite.mg/frenchstoreview
   http://german.mysite.mg/germanstoreview
   ```

>[!INFO]
>
>- Potrebbero essere necessarie attività aggiuntive per distribuire più siti web in un ambiente in hosting; per ulteriori informazioni, consulta il provider di hosting .
>- Sono necessarie attività aggiuntive per configurare Adobe Commerce sull’infrastruttura cloud; vedere [Configurazione di più siti Web o negozi Cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) in _Guida a Commerce on Cloud Infrastructure_.


### Risoluzione dei problemi

- Se i siti francesi e tedeschi restituiscono 404 ma l&#39;amministratore carica, assicurati di aver completato il processo [Passaggio 6: Aggiungi il codice store all&#39;URL di base](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- Se tutti gli URL restituiscono 404 s, assicurati di aver riavviato il server web.
- Se l&#39;amministratore non funziona correttamente, assicurati di configurare correttamente gli host virtuali.
