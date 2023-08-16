---
title: Configurare più siti Web con Nginx
description: Segui questo tutorial per configurare più siti web con Nginx.
exl-id: f13926a2-182c-4ce2-b091-19c5f978f267
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '959'
ht-degree: 0%

---

# Configurare più siti Web con Nginx

Si presuppone che:

- Stai lavorando su una macchina di sviluppo (laptop, macchina virtuale o simile).

  Potrebbero essere necessarie attività aggiuntive per distribuire più siti web in un ambiente ospitato; per ulteriori informazioni, rivolgiti al provider di hosting.

  Sono necessarie attività aggiuntive per configurare l’infrastruttura cloud di Adobe Commerce. Dopo aver completato le attività descritte in questo argomento, vedere [Configurazione di più siti Web o store](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) nel _Guida di Commerce su infrastruttura cloud_.

- Accetti più domini in un file host virtuale o utilizzi un host virtuale per sito Web; i file di configurazione host virtuale si trovano in `/etc/nginx/sites-available`.
- Utilizzi il `nginx.conf.sample` fornite da Commerce con solo le modifiche descritte in questa esercitazione.
- Il software Commerce è installato in `/var/www/html/magento2`.
- Sono disponibili due siti Web diversi da quello predefinito:

   - `french.mysite.mg` con il codice del sito web `french` e memorizza il codice di visualizzazione `fr`
   - `german.mysite.mg` con il codice del sito web `german` e memorizza il codice di visualizzazione `de`
   - `mysite.mg` è il sito Web predefinito e la vista store predefinita

>[!TIP]
>
>Fai riferimento a [Creare siti Web](ms-admin.md#step-2-create-websites) e [Creare le visualizzazioni dello store](ms-admin.md#step-4-create-store-views) per informazioni su come individuare questi valori.

Di seguito è riportata una roadmap per la configurazione di più siti Web con nginx:

1. [Configurare siti Web, store e visualizzazioni dello store](ms-admin.md) in Admin.
1. Creare un [Host virtuale Nginx](#step-2-create-nginx-virtual-hosts)) per mappare molti siti web o un host virtuale Nginx per sito web Commerce (passaggi descritti di seguito).
1. Passa i valori di [Variabili immagine](ms-overview.md) `$MAGE_RUN_TYPE` e `$MAGE_RUN_CODE` a nginx utilizzando il Magento fornito `nginx.conf.sample` (passaggi descritti di seguito).

   - `$MAGE_RUN_TYPE` può essere `store` o `website`:

      - Utilizzare `website` per caricare il sito web nella vetrina.
      - Utilizzare `store` per caricare qualsiasi visualizzazione store nella vetrina.

   - `$MAGE_RUN_CODE` è il codice univoco di visualizzazione del sito web o dello store che corrisponde a `$MAGE_RUN_TYPE`.

1. Aggiorna la configurazione dell’URL di base nell’amministratore Commerce.

## Passaggio 1: creare siti web, store e visualizzazioni dello store in Admin

Consulta [Configurare più siti web, store e visualizzazioni dello store in Admin](ms-admin.md).

## Passaggio 2: creare host virtuali di base

Questo passaggio illustra come caricare i siti web sulla vetrina. È possibile utilizzare siti Web o visualizzazioni archivio; se si utilizzano le visualizzazioni archivio, è necessario modificare di conseguenza i valori dei parametri. Devi completare le attività in questa sezione come utente con `sudo` privilegi.

Utilizzando solo un [File host virtuale nginx](#step-2-create-nginx-virtual-hosts), è possibile mantenere la configurazione nginx semplice e pulita. Utilizzando diversi file host virtuali, è possibile personalizzare ogni archivio (per utilizzare un percorso personalizzato per `french.mysite.mg` ad esempio).

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

1. Salvare le modifiche apportate ai file e uscire dall&#39;editor di testo.
1. Verifica la configurazione del server:

   ```bash
   nginx -t
   ```

1. In caso di esito positivo, viene visualizzato il seguente messaggio:

   ```terminal
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   Se vengono visualizzati degli errori, controllare la sintassi dei file di configurazione dell&#39;host virtuale.

1. Creare un collegamento simbolico in `/etc/nginx/sites-enabled` directory:

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/magento magento
   ```

Per maggiori dettagli sulla direttiva mappa, vedi [Documentazione di nginx sulla direttiva mappa](http://nginx.org/en/docs/http/ngx_http_map_module.html#map).


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

1. Salvare le modifiche apportate ai file e uscire dall&#39;editor di testo.
1. Verifica la configurazione del server:

   ```bash
   nginx -t
   ```

1. In caso di esito positivo, viene visualizzato il seguente messaggio:

   ```terminal
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   Se vengono visualizzati degli errori, controllare la sintassi dei file di configurazione dell&#39;host virtuale.

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

## Passaggio 3: modificare nginx.conf.sample

>[!TIP]
>
>Non modificare `nginx.conf.sample` ; si tratta di un file Commerce di base che può essere aggiornato con ogni nuova versione. È sufficiente copiare `nginx.conf.sample` file, rinominarlo e quindi modificare il file copiato.

**Per modificare il punto di ingresso PHP per l&#39;applicazione principale**:

Per modificare `nginx.conf.sample` file**:

1. Apri un editor di testo e controlla `nginx.conf.sample` file ,`<magento2_installation_directory>/nginx.conf.sample`. Cerca la sezione seguente:

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

1. Aggiornare il `nginx.conf.sample` file con le due righe seguenti prima dell&#39;istruzione include:

   ```conf
   fastcgi_param MAGE_RUN_TYPE $MAGE_RUN_TYPE;
   fastcgi_param MAGE_RUN_CODE $MAGE_RUN_CODE;
   ```

Un esempio di punto di ingresso PHP aggiornato per l’applicazione principale è simile al seguente:

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

## Passaggio 4: aggiornare la configurazione dell’URL di base

È necessario aggiornare l’URL di base per `french` e `german` siti web nell’amministratore di Commerce.

### Aggiorna URL di base sito Web francese

1. Accedi all’amministratore di Commerce e passa a **Negozi** > **Impostazioni** > **Configurazione** > **Generale** > **Web**.
1. Modificare il _ambito di configurazione_ al `french` sito Web.
1. Espandi **URL di base** e aggiorna il **URL di base** e **URL collegamento base** valore per `http://french.magento24.com/`.
1. Espandi **URL di base (protetto)** e aggiorna il **URL di base sicuro** e **URL collegamento base sicuro** valore per `https://french.magento24.com/`.
1. Clic **Salva configurazione** e salva le modifiche alla configurazione.

### Aggiorna URL base sito Web tedesco

1. Accedi all’amministratore di Commerce e passa a **Negozi** > **Impostazioni** > **Configurazione** > **Generale** > **Web**.
1. Modificare il _ambito di configurazione_ al `german` sito Web.
1. Espandi **URL di base** e aggiorna il **URL di base** e **URL collegamento base** valore per `http://german.magento24.com/`.
1. Espandi **URL di base (protetto)** e aggiorna il **URL di base sicuro** e **URL collegamento base sicuro** valore per `https://german.magento24.com/`.
1. Clic **Salva configurazione** e salva le modifiche alla configurazione.

### Pulizia cache

Esegui il comando seguente per pulire `config` e `full_page` cache.

```bash
bin/magento cache:clean config full_page
```

## Verifica il sito

A meno che il DNS non sia configurato per gli URL dei tuoi archivi, devi aggiungere una route statica all&#39;host nel tuo `hosts` file:

1. Individuazione del sistema operativo `hosts` file.
1. Aggiungi la route statica nel formato:

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
>- Potrebbero essere necessarie attività aggiuntive per distribuire più siti web in un ambiente ospitato; per ulteriori informazioni, rivolgiti al provider di hosting.
>- Sono necessarie attività aggiuntive per configurare l’infrastruttura cloud di Adobe Commerce; consulta [Configurare più siti web o store Cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) nel _Guida di Commerce su infrastruttura cloud_.

### Risoluzione dei problemi

- Se i siti francese e tedesco restituiscono 404 secondi ma l’amministratore carica, assicurati di aver completato [Passaggio 6: aggiungi il codice dello store all’URL di base](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- Se tutti gli URL restituiscono il codice 404, assicurati di aver riavviato il server web.
- Se l&#39;amministratore non funziona correttamente, verificare di aver configurato correttamente gli host virtuali.
