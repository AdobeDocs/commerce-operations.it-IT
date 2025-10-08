---
title: Conversione di file di layout
description: Scopri come convertire i file di layout XML utilizzando gli strumenti della riga di comando di Adobe Commerce. Scopri gli aggiornamenti dei fogli di stile XSLT e i processi di conversione dei file.
exl-id: 9852b735-9b4b-43ce-887f-5c37d398bbf7
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '98'
ht-degree: 0%

---

# Conversione di file di layout XML

{{file-system-owner}}

Utilizzare questo comando per aggiornare i file XML di layout se si aggiorna il foglio di stile XSLT (Extensible Stylesheet Language Transformations) corrispondente.

- [Istruzioni di layout](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-instructions/)
- [Tipi di file di layout](https://developer.adobe.com/commerce/frontend-core/guide/layouts/types/)

Opzioni comando:

```bash
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

Dove:

- `{xml file}`: percorso completo e nome di file di un file XML di layout da convertire (obbligatorio)
- `{xslt stylesheet}`—è il percorso completo e il nome di un file del foglio di stile XSLT da utilizzare per la conversione (obbligatorio)
- `-o|--overwrite`: includere questa opzione per sovrascrivere il file XML esistente
