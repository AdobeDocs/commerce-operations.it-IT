---
title: Configurare più siti Web con Nginx
description: Segui questo tutorial per configurare più siti web con Nginx.
exl-id: f13926a2-182c-4ce2-b091-19c5f978f267
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '943'
ht-degree: 0%

---

# Configurare più siti Web con Nginx

Si presuppone che:

- Stai lavorando su una macchina di sviluppo (laptop, macchina virtuale o simile).

  Potrebbero essere necessarie attività aggiuntive per distribuire più siti web in un ambiente ospitato; per ulteriori informazioni, rivolgiti al provider di hosting.

  Sono necessarie attività aggiuntive per configurare l’infrastruttura cloud di Adobe Commerce. Dopo aver completato le attività descritte in questo argomento, vedere [Configurare più siti Web o store](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=it) nella _guida di Commerce sull&#39;infrastruttura cloud_.

- Accettare più domini in un file host virtuale o utilizzare un host virtuale per sito Web. I file di configurazione host virtuale si trovano in `/etc/nginx/sites-available`.
- Utilizza `nginx.conf.sample` fornito da Commerce con le sole modifiche descritte in questa esercitazione.
- Software Commerce installato in `/var/www/html/magento2`.
- Sono disponibili due siti Web diversi da quello predefinito:

   - `french.mysite.mg` con codice sito Web `french` e codice visualizzazione archivio `fr`
   - `german.mysite.mg` con codice sito Web `german` e codice visualizzazione archivio `de`
   - `mysite.mg` è il sito Web predefinito e la visualizzazione predefinita dello store

>[!TIP]
>
>Per informazioni su come individuare questi valori, consultare [Crea siti Web](ms-admin.md#step-2-create-websites) e [Crea visualizzazioni archivio](ms-admin.md#step-4-create-store-views).

Di seguito è riportata una roadmap per la configurazione di più siti Web con nginx:

1. [Configura siti Web, archivi e visualizzazioni dello store](ms-admin.md) nell&#39;amministratore.
1. Creare un [host virtuale Nginx](#step-2-create-nginx-virtual-hosts)) per mappare molti siti Web o un host virtuale Nginx per sito Web Commerce (passaggi descritti di seguito).
1. Passa i valori delle [variabili MAGE](ms-overview.md) `$MAGE_RUN_TYPE` e `$MAGE_RUN_CODE` a nginx utilizzando `nginx.conf.sample` fornito da Magento (passaggi descritti di seguito).

   - `$MAGE_RUN_TYPE` può essere `store` o `website`:

      - Utilizza `website` per caricare il tuo sito Web nella vetrina.
      - Utilizza `store` per caricare qualsiasi visualizzazione dello store nella tua vetrina.

   - `$MAGE_RUN_CODE` è il codice univoco di visualizzazione del sito Web o dello store che corrisponde a `$MAGE_RUN_TYPE`.

1. Aggiorna la configurazione dell’URL di base nell’amministratore di Commerce.

## Passaggio 1: creare siti web, store e visualizzazioni dello store in Admin

Vedere [Configurare più siti Web, store e visualizzazioni dello store in Admin](ms-admin.md).

## Passaggio 2: creare host virtuali di base

Questo passaggio illustra come caricare i siti web sulla vetrina. È possibile utilizzare siti Web o visualizzazioni archivio; se si utilizzano le visualizzazioni archivio, è necessario modificare di conseguenza i valori dei parametri. È necessario completare le attività in questa sezione come utente con privilegi `sudo`.

Utilizzando un solo file host virtuale [nginx](#step-2-create-nginx-virtual-hosts), puoi mantenere la configurazione nginx semplice e pulita. Utilizzando diversi file host virtuali, è possibile personalizzare ogni archivio, ad esempio per utilizzare un percorso personalizzato per `french.mysite.mg`.

**Per creare un host virtuale** (semplificato):

Questa configurazione si espande dopo [configurazione nginx](../../installation/prerequisites/web-server/nginx.md).

1. Aprire un editor di testo e aggiungere il contenuto seguente a un nuovo file denominato `/etc/nginx/sites-available/magento`:

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

   ```
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   Se vengono visualizzati degli errori, controllare la sintassi dei file di configurazione dell&#39;host virtuale.

1. Creare un collegamento simbolico nella directory `/etc/nginx/sites-enabled`:

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/magento magento
   ```

Per ulteriori dettagli sulla direttiva mappa, consulta la [documentazione nginx sulla direttiva mappa](http://nginx.org/en/docs/http/ngx_http_map_module.html#map).


**Per creare più host virtuali**:

1. Aprire un editor di testo e aggiungere il contenuto seguente a un nuovo file denominato `/etc/nginx/sites-available/french.mysite.mg`:

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

1. Creare un altro file denominato `german.mysite.mg` nella stessa directory con il contenuto seguente:

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

   ```
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   Se vengono visualizzati degli errori, controllare la sintassi dei file di configurazione dell&#39;host virtuale.

1. Creare collegamenti simbolici nella directory `/etc/nginx/sites-enabled`:

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
>Non modificare il file `nginx.conf.sample`; si tratta di un file Commerce di base che può essere aggiornato a ogni nuova versione. Copiare il file `nginx.conf.sample`, rinominarlo e quindi modificare il file copiato.

**Per modificare il punto di ingresso PHP per l&#39;applicazione principale**:

Per modificare il file `nginx.conf.sample`**:

1. Apri un editor di testo e controlla il file `nginx.conf.sample` ,`<magento2_installation_directory>/nginx.conf.sample`. Cerca la sezione seguente:

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

1. Aggiornare il file `nginx.conf.sample` con le due righe seguenti prima dell&#39;istruzione include:

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

È necessario aggiornare l&#39;URL di base per i siti Web `french` e `german` nell&#39;amministratore Commerce.

### Aggiorna URL di base sito Web francese

1. Accedi all&#39;amministratore di Commerce e passa a **Archivi** > **Impostazioni** > **Configurazione** > **Generale** > **Web**.
1. Modificare l&#39;ambito di configurazione __ nel sito Web `french`.
1. Espandere la sezione **URL di base** e aggiornare il valore **URL di base** e **URL di collegamento di base** a `http://french.magento24.com/`.
1. Espandere la sezione **URL di base (protetto)** e aggiornare il valore **URL di base protetto** e **URL collegamento di base protetto** in `https://french.magento24.com/`.
1. Fai clic su **Salva configurazione** e salva le modifiche alla configurazione.

### Aggiorna URL base sito Web tedesco

1. Accedi all&#39;amministratore di Commerce e passa a **Archivi** > **Impostazioni** > **Configurazione** > **Generale** > **Web**.
1. Modificare l&#39;ambito di configurazione __ nel sito Web `german`.
1. Espandere la sezione **URL di base** e aggiornare il valore **URL di base** e **URL di collegamento di base** a `http://german.magento24.com/`.
1. Espandere la sezione **URL di base (protetto)** e aggiornare il valore **URL di base protetto** e **URL collegamento di base protetto** in `https://german.magento24.com/`.
1. Fai clic su **Salva configurazione** e salva le modifiche alla configurazione.

### Pulizia cache

Eseguire il comando seguente per pulire le cache `config` e `full_page`.

```bash
bin/magento cache:clean config full_page
```

## Verifica il sito

A meno che il DNS non sia configurato per gli URL dei tuoi archivi, devi aggiungere una route statica all&#39;host nel file `hosts`:

1. Individuare il file `hosts` del sistema operativo.
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
>- Sono necessarie attività aggiuntive per configurare Adobe Commerce sull&#39;infrastruttura cloud; consulta [Configurare più siti Web o store Cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html?lang=it) nella _Guida di Commerce sull&#39;infrastruttura cloud_.

### Risoluzione dei problemi

- Se i siti francese e tedesco restituiscono 404 secondi ma l&#39;amministratore si carica, assicurati di aver completato [Passaggio 6: aggiungi il codice dello store all&#39;URL di base](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- Se tutti gli URL restituiscono il codice 404, assicurati di aver riavviato il server web.
- Se l&#39;amministratore non funziona correttamente, verificare di aver configurato correttamente gli host virtuali.
