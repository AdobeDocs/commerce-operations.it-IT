---
title: Ottimizzare i file di risorse CSS e JS
description: Scopri come unire e minimizzare i file CSS e JavaScript (JS) per i progetti Adobe Commerce dall’amministratore o dalla riga di comando.
role: Developer
feature: Best Practices
exl-id: ff0bc407-b563-418b-9d6a-7c1dc8f235df
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# Ottimizzare i file di risorse

Per un sito Commerce più dinamico, ottimizza i file di risorse CSS e JavaScript (JS) ed elimina le risorse che bloccano il rendering.

- **Ottimizza i file** CSS e JS: riduci il tempo necessario per caricare i file CSS e JavaScript (JS) configurando Adobe Systems Commerce per unire, minimizzare e raggruppare file separati in un unico file.
- **Eliminazione delle risorse** che bloccano il rendering: valuta la possibilità di fornire funzionalità JS e CSS critico in linea e di rinviare tutti gli stili JS/CSS non critico. Per istruzioni, vedi [Eliminare le risorse](https://web.dev/render-blocking-resources/) che bloccano il rendering.

## Prodotti e versioni interessati

[Tutte le versioni supportate, 2.3 e successive](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

## Unire o minimizzare file CSS

Il tempo necessario per caricare i file CSS e JavaScript (JS) può essere ridotto unendo, minimizzando e raggruppando file separati in un unico file.

>[!IMPORTANT]
>
>Adobe Systems Commerce su infrastruttura cloud viene sempre eseguito in modalità Produzione e non è possibile impostarlo altrimenti, pertanto è necessario utilizzare il metodo della riga di comando per abilitare l&#39;unione, la minimizzazione e il raggruppamento.

Non unire o raggruppare i file se la distribuzione utilizza HTTP/2. HTTP/2 scarica i file statici in modo asincrono. I browser devono scaricare un intero file unito prima di elaborare il contenuto del file.

### Utilizzo di Admin

Per abilitare l&#39;unione o la minimizzazione dei CSS, accedi alla [!UICONTROL **sezione Admin** > **Stores** > **Impostazione** > **configurazione** > **Avanzate** > **Developer** > **CSS Impostazioni**].

### Utilizzo della riga di comando

Per abilitare l&#39;unione dei CSS in Adobe Systems Commerce in infrastruttura cloud:

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

1. Eseguire il commit delle modifiche apportate al `app/etc/config.php` file e ridistribuirlo.

## Minimizza i file JS

### Utilizzo di Admin

*Nella barra laterale Amministratore*, vai a **Stores** > **Impostazioni** > **Configuration** > **Avanzate >** **Developer** > **JavaScript Impostazioni**.

### Utilizzo della riga di comando

Per abilitare la minimizzazione JS in Adobe Systems Commerce sul infrastruttura cloud:

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

## Informazioni aggiuntive

- [Impostazioni di ottimizzazione lato client](../../../performance/configuration.md#client-side-optimization-settings)
- [Guida utente: Ottimizzazione dei file di risorse](https://experienceleague.adobe.com/it/docs/commerce-admin/systems/tools/developer-tools#optimizing-resource-files)
- [Guida per sviluppatori frontend: fusione, minimizzazione e prestazioni del sito CSS](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
- [Avanzate JavaScript raggruppamento](../../../performance/advanced-js-bundling.md)
