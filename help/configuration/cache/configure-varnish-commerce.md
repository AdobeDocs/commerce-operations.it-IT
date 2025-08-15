---
title: Configurazione vernice per Commerce
description: Scopri come aggiornare e gestire il file di configurazione di Vernice per l’applicazione Commerce.
feature: Configuration, Cache, SCD
exl-id: 6c007ff9-493f-4df2-b7b4-438b41fd7e37
source-git-commit: 602a1ef82fcb8d30ff027db0fe0aacb981c7e08e
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---

# Configurare l&#39;applicazione Commerce per l&#39;utilizzo di Vernice

Per configurare Commerce per l&#39;utilizzo di Vernice:

1. Accedi all’amministratore come amministratore.
1. Fai clic su **[!UICONTROL Stores]** > Impostazioni > **Configurazione** > **Avanzate** > **Sistema** > **Cache a pagina intera**.
1. Dall&#39;elenco **[!UICONTROL Caching Application]**, fare clic su **Memorizzazione in cache vernice**.
1. Immettere un valore nel campo **[!UICONTROL TTL for public content]**.
1. Espandere **[!UICONTROL Varnish Configuration]** e immettere le informazioni seguenti:

   | Campo | Descrizione |
   | ----- | ----------- |
   | Elenco di accesso | Immettere il nome host completo, l&#39;indirizzo IP o l&#39;intervallo di indirizzi IP con notazione [ di tipo ](https://www.digitalocean.com/community/tutorials/understanding-ip-addresses-subnets-and-cidr-notation-for-networking)Classless Inter-Domain Routing (CIDR) per cui annullare la validità del contenuto. Vedi [Rimozione cache vernice](https://varnish-cache.org/docs/3.0/tutorial/purging.html). |
   | Host back-end | Immettere il nome host completo o l&#39;indirizzo IP e la porta di ascolto del server di origine _backend_ o _vernice_, ovvero il server che fornisce il contenuto, che verrà accelerato da Vernice. In genere, si tratta del server web. Vedi [Server back-end della cache di vernice](https://www.varnish-cache.org/docs/trunk/users-guide/vcl-backends.html). |
   | Porta back-end | Porta di ascolto del server di origine. |
   | Periodo di tolleranza | Determina per quanto tempo Vernice fornisce contenuti non aggiornati se il backend non risponde. Il valore predefinito è 300 secondi. |
   | Gestisce le dimensioni dei parametri | Specifica il numero massimo di [handle di layout](https://developer.adobe.com/commerce/frontend-core/guide/layouts/#layout-handles) da elaborare sull&#39;endpoint HTTP [`{BASE-URL}/page_cache/block/esi`](use-varnish-esi.md) per il caching a pagina intera. La limitazione delle dimensioni può migliorare la sicurezza e le prestazioni. Il valore predefinito è 100. |

1. Fai clic su **Salva configurazione**.

È inoltre possibile attivare la vernice dalla riga di comando, anziché accedere all&#39;amministratore, utilizzando lo strumento dell&#39;interfaccia della riga di comando C:

```bash
bin/magento config:set --scope=default --scope-code=0 system/full_page_cache/caching_application 2
```

## Esportare un file di configurazione vernice

Per esportare un file di configurazione vernice dall&#39;amministratore:

1. Fare clic su uno dei pulsanti di esportazione per creare un `varnish.vcl` utilizzabile con vernice.

   Ad esempio, se si dispone di vernice 4, fare clic su **Esporta VCL per vernice 4**

   Nella figura seguente viene illustrato un esempio:

   ![Configura Commerce per l&#39;utilizzo di Vernice nell&#39;amministratore](../../assets/configuration/varnish-admin-22.png)

1. Esegui il backup di `default.vcl` esistente. Quindi rinominare il file `varnish.vcl` appena esportato in `default.vcl`. Copiare quindi il file nella directory `/etc/varnish/`.

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak2
   ```

   ```bash
   mv <download_directory>/varnish.vcl default.vcl
   ```

   ```bash
   cp <download_directory>/default.vcl /etc/varnish/default.vcl
   ```

1. Adobe consiglia di aprire `default.vcl` e modificare il valore di `acl purge` nell&#39;indirizzo IP dell&#39;host Vernice. È possibile specificare più host su righe separate oppure utilizzare anche la notazione CIDR.

   Ad esempio:

   ```conf
    acl purge {
       "localhost";
    }
   ```

1. Se si desidera personalizzare i controlli di integrità Vagrant o la configurazione della modalità di tolleranza o della modalità di santo, vedere [Configurazione avanzata vernice](config-varnish-advanced.md).

1. Riavvia Varnish e il tuo server web:

   ```bash
   service varnish restart
   ```

   ```bash
   service httpd restart
   ```

## Memorizza nella cache i file statici

Per impostazione predefinita, i file statici non devono essere memorizzati in cache, ma se desideri memorizzarli in cache, puoi modificare la sezione `Static files caching` nel file VCL in modo che abbia il seguente contenuto:

```conf
# Static files should not be cached by default
  return (pass);

# But if you use a few locales and do not use CDN you can enable caching static files by commenting previous line (#return (pass);) and uncommenting next 3 lines
  #unset req.http.Https;
  #unset req.http./* {{ ssl_offloaded_header }} */;
  #unset req.http.Cookie;
```

È necessario apportare queste modifiche prima di configurare Commerce per l&#39;utilizzo di Vernice.
