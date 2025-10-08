---
title: Creare collegamenti simbolici a file LESS
description: Scopri come creare collegamenti simbolici a file LESS per lo sviluppo Adobe Commerce. Scopri il collegamento dei fogli di stile e l’ottimizzazione del flusso di lavoro di sviluppo.
exl-id: 58a6123a-28b4-445b-b3f9-f524233ac127
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---

# Creare collegamenti simbolici a file LESS

{{file-system-owner}}

Per creare collegamenti simbolici a file LESS:

Opzioni comando:

```bash
bin/magento dev:source-theme:deploy [--type="..."] [--locale="..."] [--area="..."] [--theme="..."] [file1] ... [fileN]
```

>[!INFO]
>
>Durante lo sviluppo, questo comando crea symlink per i file LESS nelle cartelle `var/view_preprocessed` e `pub/static`. Questo processo non compila file LESS in file CSS.

Nella tabella seguente vengono illustrati i parametri e i valori di questo comando.

| Parametro | Valore | Obbligatorio |
| --------- | ----- | --------- |
| `--type` | Tipo di file di origine: [less] (impostazione predefinita: &quot;less&quot;)<br>Attualmente, LESS è l&#39;unico tipo di file supportato. | No |
| `--locale` | Codice lingua.<br>Per visualizzare l&#39;elenco dei codici locali, immettere `bin/magento info:language:list` | No |
| `--area` | Area (`adminhtml` per l&#39;area amministrativa, `frontend` per la vetrina). | No |
| `--theme` | Nome tema in formato `<VendorName>/<theme-name>`. Ad esempio, `Magento/blank` o `Magento/backend`. | No |
| `<file>` | Elenco separato da spazi di file CSS da convertire in LESS senza estensione CSS. Il valore predefinito è `css/styles-m css/styles-l`, per il tipo adminhtml `css/styles css/styles-old` | No |

Ad esempio, per creare un file LESS per il tema front-end denominato `VendorName/themeName` nelle impostazioni locali di `en_US` utilizzando un file CSS denominato `<magento_root>/pub/static/frontend/VendorName/themeName/en_US/css/styles-l.css`, immettere il comando seguente:

```bash
bin/magento dev:source-theme:deploy --type="less" --locale="en_US" --area="frontend" --theme="VendorName/themeName" css/styles-l
```

Per confermare il successo, vengono visualizzati i seguenti messaggi:

```
Processed Area: frontend, Locale: en_US, Theme: VendorName/themeName, File type: less.
-> css/styles-l.less
Successfully processed.
```

Per creare MENO file per l&#39;amministratore:

```bash
bin/magento dev:source-theme:deploy --locale="en_US" --area="adminhtml" --theme="Magento/backend" css/styles css/styles-old
```
