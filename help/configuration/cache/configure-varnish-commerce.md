---
title: Configurazione vernice per Commerce
description: Scopri come aggiornare e gestire il file di configurazione di Vernice per l’applicazione Commerce.
feature: Configuration, Cache, SCD
exl-id: 6c007ff9-493f-4df2-b7b4-438b41fd7e37
source-git-commit: 11ccc59230a7a0d1768c043c39df43c7df031efd
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# Configurare l’applicazione Commerce per l’utilizzo di vernice

Per configurare Commerce per l’utilizzo di Vernice:

1. Accedi all’amministratore come amministratore.
1. Clic **[!UICONTROL Stores]** > Impostazioni > **Configurazione** > **Avanzate** > **Sistema** > **Cache a pagina intera**.
1. Dalla sezione **[!UICONTROL Caching Application]** , fare clic su **Caching vernice**.
1. Immetti un valore in **[!UICONTROL TTL for public content]** campo.
1. Espandi **[!UICONTROL Varnish Configuration]** e immettere le seguenti informazioni:

   | Campo | Descrizione |
   | ----- | ----------- |
   | Elenco di accesso | Inserisci il nome host completo, l’indirizzo IP o [Routing tra domini diversi senza classificazione (CIDR)](https://www.digitalocean.com/community/tutorials/understanding-ip-addresses-subnets-and-cidr-notation-for-networking) notazione Intervallo di indirizzi IP per cui annullare la validità del contenuto. Consulta [Cancellazione cache vernice](https://varnish-cache.org/docs/3.0/tutorial/purging.html). |
   | Host back-end | Immettere il nome host completo o l&#39;indirizzo IP e la porta di ascolto della vernice _backend_ o _server di origine_ ovvero il server che fornisce il contenuto accelera la visualizzazione di Vernice. In genere, si tratta del server web. Consulta [Vernice dei server back-end della cache](https://www.varnish-cache.org/docs/trunk/users-guide/vcl-backends.html). |
   | Porta back-end | Porta di ascolto del server di origine. |
   | Periodo di tolleranza | Determina per quanto tempo Vernice fornisce contenuti non aggiornati se il backend non risponde. Il valore predefinito è 300 secondi. |
   | Gestisce le dimensioni dei parametri  [!BADGE 2.4.7-beta]{type=Informative url="/help/release/release-notes/commerce/2-4-7.md" tooltip="Disponibile solo nella versione 2.4.7-beta"} | Specifica il numero massimo di [maniglie di layout](https://developer.adobe.com/commerce/frontend-core/guide/layouts/#layout-handles) da elaborare su [`{BASE-URL}/page_cache/block/esi`](use-varnish-esi.md) Endpoint HTTP per il caching di pagine intere. La limitazione delle dimensioni può migliorare la sicurezza e le prestazioni. Il valore predefinito è 100. |

1. Clic **Salva configurazione**.

È inoltre possibile attivare la vernice dalla riga di comando, anziché accedere all&#39;amministratore, utilizzando lo strumento dell&#39;interfaccia della riga di comando C:

```bash
bin/magento config:set --scope=default --scope-code=0 system/full_page_cache/caching_application 2
```

## Esportare un file di configurazione vernice

Per esportare un file di configurazione vernice dall&#39;amministratore:

1. Fai clic su uno dei pulsanti di esportazione per creare un’ `varnish.vcl` può essere usato con vernice.

   Ad esempio, se si dispone di vernice 4, fare clic su **Esporta VCL per vernice 4**

   Nella figura seguente viene illustrato un esempio:

   ![Configurare Commerce per l’utilizzo di Vernice nell’amministratore](../../assets/configuration/varnish-admin-22.png)

1. Esegui il backup del file esistente `default.vcl`. Quindi rinomina il `varnish.vcl` file appena esportato in `default.vcl`. Quindi copia il file in `/etc/varnish/` directory.

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak2
   ```

   ```bash
   mv <download_directory>/varnish.vcl default.vcl
   ```

   ```bash
   cp <download_directory>/default.vcl /etc/varnish/default.vcl
   ```

1. Adobe consigliato di aprire `default.vcl` e modificare il valore di `acl purge` all&#39;indirizzo IP dell&#39;host Vernice. È possibile specificare più host su righe separate oppure utilizzare anche la notazione CIDR.

   Ad esempio:

   ```conf
    acl purge {
       "localhost";
    }
   ```

1. Se desideri personalizzare la configurazione dei controlli di integrità Vagrant, della modalità di tolleranza o della modalità santo, consulta [Configurazione vernice avanzata](config-varnish-advanced.md).

1. Riavvia Varnish e il tuo server web:

   ```bash
   service varnish restart
   ```

   ```bash
   service httpd restart
   ```

## Memorizza nella cache i file statici

I file statici non devono essere memorizzati in cache per impostazione predefinita, ma se desideri memorizzarli in cache, puoi modificare la sezione `Static files caching` nel file VCL, avere il seguente contenuto:

```conf
# Static files should not be cached by default
  return (pass);

# But if you use a few locales and do not use CDN you can enable caching static files by commenting previous line (#return (pass);) and uncommenting next 3 lines
  #unset req.http.Https;
  #unset req.http./* {{ ssl_offloaded_header }} */;
  #unset req.http.Cookie;
```

È necessario apportare queste modifiche prima di configurare Commerce per l’utilizzo di Vernice.
