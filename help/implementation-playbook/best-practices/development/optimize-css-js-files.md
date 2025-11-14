---
title: Ottimizzare i file di risorse CSS e JS
description: Scopri come unire e minimizzare i file CSS e JavaScript (JS) per i progetti Adobe Commerce dall’amministratore o dalla riga di comando.
role: Developer
feature: Best Practices
exl-id: ff0bc407-b563-418b-9d6a-7c1dc8f235df
source-git-commit: 19f874130645fcabe3178a37ec6dedcf75b93afa
workflow-type: tm+mt
source-wordcount: '430'
ht-degree: 0%

---

# Ottimizzare i file di risorse

Per un sito Commerce più reattivo, ottimizza i file di risorse CSS e JavaScript (JS) ed elimina le risorse di blocco del rendering.

- **Ottimizza file CSS e JS**—Riduci il tempo necessario per caricare i file CSS e JavaScript (JS) configurando Adobe Commerce per unire, minimizzare e raggruppare file separati in un unico file.
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

Per abilitare l&#39;unione o la minimizzazione CSS, vai in [!UICONTROL **Amministrazione** > **Archivi** > **Impostazione** > **Configurazione** > **Avanzate** > **Sviluppatore** > **Impostazioni CSS**].

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

### Utilizzo di Admin

Nella barra laterale *Amministratore*, vai a **Archivi** > **Impostazioni** > **Configurazione** > **Avanzate** > **Sviluppatore** > **Impostazioni JavaScript**.

### Utilizzo della riga di comando

Per abilitare la minimizzazione JS in Adobe Commerce sull’infrastruttura cloud:

1. Esegui questo comando localmente:

   ```bash
   bin/magento config:set --lock-config dev/js/minify_files 1
   ```

1. Eseguire il commit delle modifiche nel file `app/etc/config.php` e ridistribuirle.

## Unire e raggruppare file JS

È possibile attivare l&#39;unione o il raggruppamento in Amministrazione Commerce (l&#39;unione e il raggruppamento non possono essere attivati contemporaneamente): [!UICONTROL **Archivi** > **Impostazioni** > **Configurazione** > **Avanzate** > **Sviluppatore** > **Impostazioni JavaScript**].

Puoi anche abilitare il bundling integrato di Adobe Commerce (bundling di base) dalla riga di comando:

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

## Differire gli script di intestazione non critici

Posticipa automaticamente gli script Javascript non critici caricati nella sezione head abilitando questa impostazione: [!UICONTROL **Arches** > **Settings** > **Configuration** > **Advanced** > **Developer** > **JavaScript Settings**].

Puoi anche abilitare questo flag dalla riga di comando:

```bash
php -f bin/magento config:set dev/js/defer_non_critical 1
```

## Informazioni aggiuntive

- [Impostazioni di ottimizzazione lato client](../../../performance/configuration.md#client-side-optimization-settings)
- [Guida utente: ottimizzazione dei file di risorse](https://experienceleague.adobe.com/it/docs/commerce-admin/systems/tools/developer-tools#optimizing-resource-files)
- [Guida per gli sviluppatori front-end: unione CSS, minimizzazione e prestazioni del sito](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
- [Bundling JavaScript avanzato](../../../performance/advanced-js-bundling.md)
