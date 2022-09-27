---
title: Configurare Varnish per Commerce
description: Scopri come aggiornare e gestire il file di configurazione Varnish per l’applicazione Commerce.
source-git-commit: d451ea025a6f4fc8a4a9f15ca83896a63058a3a0
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---


# Configurare l’applicazione Commerce per l’utilizzo di Varnish

Per configurare Commerce per l’utilizzo di Varnish:

1. Accedi all’amministratore come amministratore.
1. Fai clic su **[!UICONTROL Stores]** > Impostazioni > **Configurazione** > **Avanzate** > **Sistema** > **Cache a pagina intera**.
1. Da **[!UICONTROL Caching Application]** elenco, fai clic su **Memorizzazione in cache in vernice**.
1. Immetti un valore nel **[!UICONTROL TTL for public content]** campo .
1. Espandi **[!UICONTROL Varnish Configuration]** e inserire le seguenti informazioni:

   | Campo | Descrizione |
   | ----- | ----------- |
   | Elenco di accesso | Immettere il nome host completo, l&#39;indirizzo IP o [Routing tra domini diversi (CIDR)](https://www.digitalocean.com/community/tutorials/understanding-ip-addresses-subnets-and-cidr-notation-for-networking) l’intervallo di indirizzi IP della notazione per il quale annullare la validità del contenuto. Vedi [Rimozione della cache vernice](https://varnish-cache.org/docs/3.0/tutorial/purging.html). |
   | Host back-end | Inserisci il nome host completo o l&#39;indirizzo IP e ascolta la porta della Vernish _backend_ o _server di origine_; in altre parole, il server che fornisce il contenuto Varnish accelera. In genere, si tratta del server web. Vedi [Server back-end cache verniciati](https://www.varnish-cache.org/docs/trunk/users-guide/vcl-backends.html). |
   | Porta back-end | Porta di ascolto del server di origine. |
   | Periodo di tolleranza | Il periodo di tolleranza determina per quanto tempo la funzione Vernice fornisce contenuti non aggiornati se il backend non è reattivo. Il valore predefinito è 300 secondi. |

1. Fai clic su **Salva configurazione**.

È inoltre possibile attivare la vernice dalla riga di comando, anziché accedere all’amministratore, utilizzando lo strumento di interfaccia della riga di comando C:

```bash
bin/magento config:set --scope=default --scope-code=0 system/full_page_cache/caching_application 2
```

## Esportare un file di configurazione Varnish

Per esportare un file di configurazione Varnish dall’amministratore:

1. Fai clic su uno dei pulsanti di esportazione per creare un `varnish.vcl` si può usare con Vernish.

   Ad esempio, se disponi di Varnish 4, fai clic su **Esportazione VCL per vernice 4**

   La figura seguente mostra un esempio:

   ![Configurare Commerce per utilizzare Varnish nell’amministrazione](../../assets/configuration/varnish-admin-22.png)

1. Esegui il backup della `default.vcl`. Quindi rinomina la `varnish.vcl` file appena esportato in `default.vcl`. Quindi copia il file nel `/etc/varnish/` directory.

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak2
   ```

   ```bash
   mv <download_directory>/varnish.vcl default.vcl
   ```

   ```bash
   cp <download_directory>/default.vcl /etc/varnish/default.vcl
   ```

1. Adobe consiglia di aprire `default.vcl` e modificare il valore di `acl purge` all&#39;indirizzo IP dell&#39;host Varnish. (È possibile specificare più host su linee separate oppure utilizzare anche la notazione CIDR).

   Ad esempio:

   ```conf
    acl purge {
       "localhost";
    }
   ```

1. Se desideri personalizzare i controlli di integrità Vagrant o la modalità di grazia o la configurazione della modalità saint, consulta [Configurazione avanzata della vernice](config-varnish-advanced.md).

1. Riavvia Varnish e il tuo server web:

   ```bash
   service varnish restart
   ```

   ```bash
   service httpd restart
   ```

## File statici della cache

I file statici non devono essere memorizzati nella cache per impostazione predefinita, ma se desideri memorizzarli nella cache, puoi modificare la sezione `Static files caching` nella VCL avere il seguente contenuto:

```conf
# Static files should not be cached by default
  return (pass);

# But if you use a few locales and do not use CDN you can enable caching static files by commenting previous line (#return (pass);) and uncommenting next 3 lines
  #unset req.http.Https;
  #unset req.http./* {{ ssl_offloaded_header }} */;
  #unset req.http.Cookie;
```

È necessario apportare queste modifiche prima di configurare Commerce per utilizzare Varnish.
