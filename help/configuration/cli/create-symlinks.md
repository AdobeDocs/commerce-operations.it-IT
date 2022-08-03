---
title: Creare collegamenti simbolici a file LESS
description: Scopri come creare collegamenti simbolici ai file LESS.
source-git-commit: 96fe0c5eeaa029347c829c39547ee5e473c8d04d
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# Creare collegamenti simbolici a file LESS

{{file-system-owner}}

Per creare collegamenti simbolici a file LESS:

Opzioni di comando:

```bash
bin/magento dev:source-theme:deploy [--type="..."] [--locale="..."] [--area="..."] [--theme="..."] [file1] ... [fileN]
```

>[!INFO]
>
>Durante lo sviluppo, questo comando crea collegamenti simbolici per i file LESS nel `var/view_preprocessed` e `pub/static` cartelle. Questo processo non compila i file LESS in file CSS.

Nella tabella seguente sono illustrati i parametri e i valori di questo comando.

| Parametro | Valore | Obbligatorio |
| --------- | ----- | --------- |
| `--type` | Tipo di file di origine: [less] (impostazione predefinita: &quot;less&quot;)<br>Attualmente, LESS è l&#39;unico tipo di file supportato. | No |
| `--locale` | Codice locale.<br>Per visualizzare l&#39;elenco dei codici internazionali, immettere `bin/magento info:language:list` | No |
| `--area` | Area (`adminhtml` per la zona amministrativa, `frontend` per la vetrina). | No |
| `--theme` | Nome del tema in `<VendorName>/<theme-name>` formato. Ad esempio: `Magento/blank` o `Magento/backend`. | No |
| `<file>` | Elenco separato da spazi dei file CSS da convertire in LESS senza l’estensione CSS. (Il valore predefinito è `css/styles-m css/styles-l`, per il tipo adminhtml `css/styles css/styles-old`) | No |

Ad esempio, per creare file LESS per il tema front-end denominato `VendorName/themeName` in `en_US` impostazioni internazionali che utilizzano un file CSS denominato `<magento_root>/pub/static/frontend/VendorName/themeName/en_US/css/styles-l.css`, immetti il comando seguente:

```bash
bin/magento dev:source-theme:deploy --type="less" --locale="en_US" --area="frontend" --theme="VendorName/themeName" css/styles-l
```

Vengono visualizzati i seguenti messaggi per confermare il successo:

```terminal
Processed Area: frontend, Locale: en_US, Theme: VendorName/themeName, File type: less.
-> css/styles-l.less
Successfully processed.
```

Per creare file LESS per l&#39;amministratore html:

```bash
bin/magento dev:source-theme:deploy --locale="en_US" --area="adminhtml" --theme="Magento/backend" css/styles css/styles-old
```
