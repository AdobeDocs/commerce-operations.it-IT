---
title: Ottimizzare i file di risorse CSS e JS
description: Scopri come unire e minimizzare i file CSS e JavaScript (JS) per i progetti Adobe Commerce dall’amministratore o dalla riga di comando.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 052aa61e2bb59ae11b90b5401ce6426dec9c6046
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Ottimizzare i file di risorse

Per un sito Commerce più reattivo, ottimizza i file di risorse CSS e JavaScript (JS) ed elimina le risorse di rendering-blocco.

- **Ottimizzare i file CSS e JS**: riduci il tempo necessario per caricare i file CSS e JavaScript (JS) configurando Adobe Commerce per l’unione, la minimizzazione e il raggruppamento di file separati in un unico file.
- **Eliminare le risorse di rendering-blocco**- Considera la distribuzione di funzionalità JS e CSS critiche in linea e il rinvio di tutti gli stili JS/CSS non critici. Per maggiori informazioni, vedi [Eliminare le risorse di rendering-blocco](https://web.dev/render-blocking-resources/).

## Prodotti e versioni interessati

[Tutte le versioni supportate, 2.3 e successive](../../../release/versions.md) di:

- Adobe Commerce su infrastruttura cloud
- Adobe Commerce on-premise
- Magento Open Source

## Unione o riduzione dei file CSS

Il tempo necessario per caricare i file CSS e JavaScript (JS) può essere ridotto unendo, minimizzando e raggruppando file separati in un unico file.

>[!IMPORTANT]
>
>Adobe Commerce sull’infrastruttura cloud viene sempre eseguito in modalità Produzione e non è possibile impostarlo altrimenti, pertanto devi utilizzare il metodo della riga di comando per abilitare l’unione, la minimizzazione e il bundling.

### Utilizzo di Admin

Per abilitare l’unione o la minimizzazione CSS, passa alla [!UICONTROL **Amministratore** > **Negozi** > **Impostazione** > **Configurazione** > **Avanzate** > **Sviluppatore** > **Impostazioni CSS**].

### Utilizzo della riga di comando

Per abilitare l’unione CSS in Adobe Commerce sull’infrastruttura cloud:

1. Esegui questo comando localmente:

   ```bash
   bin/magento config:set --lock-config dev/css/merge_css_files 1
   ```

1. Conferma le modifiche apportate al `app/etc/config.php` e ridistribuisci.

Per abilitare la minimizzazione CSS in Adobe Commerce sull’infrastruttura cloud:

1. Esegui questo comando localmente:

   ```bash
   bin/magento config:set --lock-config dev/css/minify_files 1
   ```

1. Conferma le modifiche apportate al `app/etc/config.php` e ridistribuisci.

## Minimizzare i file JS

### Utilizzo di Admin

Sulla *Amministratore* barra laterale, vai a **Negozi** > **Impostazioni** > **Configurazione** > **Avanzate** > **Sviluppatore** > **Impostazioni JavaScript**.

### Utilizzo della riga di comando

Per abilitare la minimizzazione JS in Adobe Commerce sull&#39;infrastruttura cloud:

1. Esegui questo comando localmente:

   ```bash
   bin/magento config:set --lock-config dev/js/minify_files 1
   ```

1. Conferma le modifiche apportate al `app/etc/config.php` e ridistribuisci.

## Unire e raggruppare file JS

Puoi attivare l’unione o il bundling nell’amministratore di Commerce (l’unione e il bundling non possono essere abilitati allo stesso tempo): [!UICONTROL **Negozi** > **Impostazioni** > **Configurazione** > **Avanzate** > **Sviluppatore** > **Impostazioni JavaScript**].

Puoi anche abilitare il bundling integrato di Adobe Commerce (bundling di base) dalla riga di comando:

```bash
php -f bin/magento config:set dev/js/enable_js_bundling 1
```

## Informazioni aggiuntive

- [Impostazioni di ottimizzazione lato client](../../../performance/configuration.md#client-side-optimization-settings)
- [Guida utente: Ottimizzazione dei file di risorse](https://docs.magento.com/user-guide/system/file-optimization.html)
- [Guida per gli sviluppatori front-end: Unione CSS, minimizzazione e prestazioni del sito](https://developer.adobe.com/commerce/frontend-core/guide/css/#css-merging-minification-and-performance)
