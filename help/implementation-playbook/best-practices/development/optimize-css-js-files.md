---
title: Ottimizzare i file di risorse CSS e JS
description: Scopri come unire e minimizzare i file CSS e JavaScript (JS) per i progetti Adobe Commerce dall’amministratore o dalla riga di comando.
role: Developer
feature: Best Practices
exl-id: ff0bc407-b563-418b-9d6a-7c1dc8f235df
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# Ottimizzare i file di risorse

Per un sito Commerce più reattivo, ottimizza i file di risorse CSS e JavaScript (JS) ed elimina le risorse di blocco del rendering.

- **Ottimizzare i file CSS e JS**- Riduce il tempo necessario per caricare i file CSS e JavaScript (JS) configurando Adobe Commerce per unire, minimizzare e raggruppare file separati in un unico file.
- **Eliminazione delle risorse di blocco del rendering**: prendi in considerazione la distribuzione di funzionalità JS e CSS critiche in linea e il rinvio di tutti gli stili JS/CSS non critici. Per maggiori informazioni, consulta [Eliminazione delle risorse di blocco del rendering](https://web.dev/render-blocking-resources/).

## Prodotti e versioni interessati

[Tutte le versioni supportate, 2.3 e successive](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

## Unire o minimizzare file CSS

Il tempo necessario per caricare i file CSS e JavaScript (JS) può essere ridotto unendo, minimizzando e raggruppando file separati in un singolo file.

>[!IMPORTANT]
>
>Adobe Commerce su infrastruttura cloud viene sempre eseguito in modalità di produzione e non è possibile impostarlo altrimenti, pertanto devi utilizzare il metodo della riga di comando per abilitare l’unione, la minimizzazione e il bundling.

Non unire o raggruppare i file se la distribuzione utilizza HTTP/2. HTTP/2 scarica i file statici in modo asincrono. I browser devono scaricare un intero file unito prima di elaborare il contenuto del file.

### Utilizzo di Admin

Per abilitare l’unione o la minimizzazione CSS, vai in [!UICONTROL **Amministratore** > **Negozi** > **Impostazione** > **Configurazione** > **Avanzate** > **Sviluppatore** > **Impostazioni CSS**].

### Utilizzo della riga di comando

Per abilitare l’unione CSS in Adobe Commerce sull’infrastruttura cloud:

1. Esegui questo comando localmente:

   ```bash
   bin/magento config:set --lock-config dev/css/merge_css_files 1
   ```

1. Conferma modifiche a `app/etc/config.php` e ridistribuirli.

Per abilitare la minimizzazione CSS in Adobe Commerce sull’infrastruttura cloud:

1. Esegui questo comando localmente:

   ```bash
   bin/magento config:set --lock-config dev/css/minify_files 1
   ```

1. Conferma modifiche a `app/etc/config.php` e ridistribuirli.

## Minimizza file JS

### Utilizzo di Admin

Il giorno *Amministratore* barra laterale, vai a **Negozi** > **Impostazioni** > **Configurazione** > **Avanzate** > **Sviluppatore** > **Impostazioni JavaScript**.

### Utilizzo della riga di comando

Per abilitare la minimizzazione JS in Adobe Commerce sull’infrastruttura cloud:

1. Esegui questo comando localmente:

   ```bash
   bin/magento config:set --lock-config dev/js/minify_files 1
   ```

1. Conferma modifiche a `app/etc/config.php` e ridistribuirli.

## Unire e raggruppare file JS

In Amministrazione Commerce puoi attivare l’unione o il bundling (l’unione e il bundling non possono essere abilitati contemporaneamente): [!UICONTROL **Negozi** > **Impostazioni** > **Configurazione** > **Avanzate** > **Sviluppatore** > **Impostazioni JavaScript**].

Puoi anche abilitare il bundling integrato di Adobe Commerce (bundling di base) dalla riga di comando:

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

## Informazioni aggiuntive

- [Impostazioni di ottimizzazione lato client](../../../performance/configuration.md#client-side-optimization-settings)
- [Guida utente: ottimizzazione dei file di risorse](https://docs.magento.com/user-guide/system/file-optimization.html)
- [Guida per gli sviluppatori di Frontend: unione CSS, minimizzazione e prestazioni del sito](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
- [Bundle JavaScript avanzato](../../../performance/advanced-js-bundling.md)
