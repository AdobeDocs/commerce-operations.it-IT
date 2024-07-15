---
title: Conversione di file di layout
description: Converte i file di layout XML.
exl-id: 9852b735-9b4b-43ce-887f-5c37d398bbf7
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '82'
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
