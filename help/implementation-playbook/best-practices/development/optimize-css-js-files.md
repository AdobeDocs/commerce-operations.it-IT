---
title: Ottimizzare i file di risorse CSS e JS
description: Scopri come unire e minimizzare i file CSS e JavaScript (JS) per i progetti Adobe Commerce dall’amministratore o dalla riga di comando.
role: Developer
feature: Best Practices
exl-id: ff0bc407-b563-418b-9d6a-7c1dc8f235df
source-git-commit: a08560eb307638a36fdc52224c41bdf2c5d47763
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# Ottimizzare i file di risorse

Per un sito Commerce più reattivo, ottimizza i file di risorse CSS e JavaScript (JS) ed elimina le risorse di blocco del rendering.

- **Ottimizza file CSS e JS**—Riduci il tempo necessario per caricare i file CSS e JavaScript (JS) configurando Adobe Commerce per minimizzare e raggruppare i file.
- **Eliminazione delle risorse di blocco del rendering**. Si consiglia di fornire funzionalità JS e CSS critiche in linea e di differire tutti gli stili JS/CSS non critici. Per maggiori informazioni, vedere [Eliminare le risorse di blocco del rendering](https://web.dev/render-blocking-resources/).

## Prodotti e versioni interessati

[Tutte le versioni supportate, 2.3 e successive](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

## Unire o minimizzare file CSS

Il tempo necessario per caricare i file CSS e JavaScript (JS) può essere ridotto unendo, minimizzando e raggruppando file separati in un unico file.

>[!IMPORTANT]
>
>Adobe Commerce su infrastruttura cloud viene sempre eseguito in modalità di produzione e non è possibile impostarlo altrimenti, pertanto devi utilizzare il metodo della riga di comando per abilitare l’unione, la minimizzazione e il bundling.

Non unire o raggruppare i file se la distribuzione utilizza HTTP/2. HTTP/2 scarica i file statici in modo asincrono. I browser devono scaricare un intero file unito prima di elaborare il contenuto del file.

### Utilizzo di Admin

Per abilitare l&#39;unione o la minimizzazione CSS, vai in **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL CSS Settings]**.

### Utilizzo della riga di comando

Per abilitare l’unione CSS in Adobe Commerce sull’infrastruttura cloud:

1. Esegui questo comando localmente:

   ```bash
   bin/magento config:set --lock-config dev/css/merge_css_files 1
   ```

1. Eseguire il commit delle modifiche nel file `app/etc/config.php` e ridistribuirle.

Per abilitare la minimizzazione CSS in Adobe Commerce sull’infrastruttura cloud:

1. Esegui questo comando localmente:

   ```bash
   bin/magento config:set --lock-config dev/css/minify_files 1
   ```

1. Eseguire il commit delle modifiche nel file `app/etc/config.php` e ridistribuirle.

## Minimizza file JS

### Utilizzo di [!UICONTROL Admin]

Nella barra laterale [!UICONTROL Admin], vai a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL JavaScript Settings]**.

### Utilizzo della riga di comando

Per abilitare la minimizzazione JS in Adobe Commerce sull’infrastruttura cloud:

1. Esegui questo comando localmente:

   ```bash
   bin/magento config:set --lock-config dev/js/minify_files 1
   ```

1. Eseguire il commit delle modifiche nel file `app/etc/config.php` e ridistribuirle.

## File JS del bundle

È possibile abilitare il bundle in Commerce [!UICONTROL Admin]: **[!UICONTROL Stores]** > ***[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL Developer]** > **[!UICONTROL JavaScript Settings]**.

>[!NOTE]
>
>Impossibile abilitare contemporaneamente l’unione e il bundling.

Puoi anche abilitare il bundling integrato di Adobe Commerce (bundling di base) dalla riga di comando:

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

## Unisci file JS (scelta non consigliata) {#merge-js-files}

>[!WARNING]
>
>Non è consigliabile abilitare **[!UICONTROL Merge JavaScript Files]**. Questa impostazione è stata progettata solo per il JavaScript caricato in modo sincrono nella sezione **[!UICONTROL HEAD]** della pagina e può causare il malfunzionamento del bundling e della logica [!DNL RequireJS]. Viene mantenuto solo per la compatibilità con le versioni precedenti e non offre vantaggi in termini di prestazioni quando HTTP/2 è abilitato.
>
>Se sono stati attivati **[!UICONTROL Merge JavaScript Files]** e si verificano problemi, provare a disattivarli prima di applicare le patch. Se non puoi disabilitare l&#39;unione, consulta [ACSD-67908](../../../tools/quality-patches-tool/patches-available-in-qpt/v1-1-73/acsd-67908.md).

## Informazioni aggiuntive

- [Impostazioni di ottimizzazione lato client](../../../performance/configuration.md#client-side-optimization-settings)
- [Suggerimenti per il bundling](../../../performance/configuration.md#bundling-tips) in *Best practice per la configurazione*: strumenti di bundle di terze parti, HTTP/2 e indicazioni su unione JS e CSS obsoleta
- [Guida utente: ottimizzazione dei file di risorse](https://experienceleague.adobe.com/it/docs/commerce-admin/systems/tools/developer-tools#optimizing-resource-files)
- [Guida per gli sviluppatori front-end: unione CSS, minimizzazione e prestazioni del sito](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
- [Bundling JavaScript avanzato](../../../performance/advanced-js-bundling.md)
