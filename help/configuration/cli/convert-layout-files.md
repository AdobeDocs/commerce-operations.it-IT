---
title: Conversione di file di layout
description: Convertire file di layout XML.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---


# Conversione di file di layout XML

{{file-system-owner}}

Utilizzare questo comando per aggiornare i file XML di layout se si aggiorna il foglio di stile XSLT (Extensible Stylesheet Language Transformations) corrispondente.

- [Istruzioni di layout](https://developer.adobe.com/commerce/frontend-core/guide/layouts/xml-instructions/)
- [Tipi di file di layout](https://developer.adobe.com/commerce/frontend-core/guide/layouts/types/)

Opzioni di comando:

```bash
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

Dove:

- `{xml file}`—è il percorso completo e il nome file di un file XML di layout da convertire (obbligatorio)
- `{xslt stylesheet}`—è il percorso completo e il nome file di un file foglio di stile XSLT da utilizzare per la conversione (obbligatorio)
- `-o|--overwrite`- includi questa opzione per sovrascrivere il file XML esistente
