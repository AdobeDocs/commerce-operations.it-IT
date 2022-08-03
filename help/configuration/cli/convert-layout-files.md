---
title: Conversione di file di layout
description: Convertire file di layout XML.
source-git-commit: 02f02393878d04b4a0fcdae256ac1ac5dd13b7f6
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---


# Conversione di file di layout XML

{{file-system-owner}}

Utilizzare questo comando per aggiornare i file XML di layout se si aggiorna il foglio di stile XSLT (Extensible Stylesheet Language Transformations) corrispondente.

- [Istruzioni di layout](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/layouts/xml-instructions.html)
- [Tipi di file di layout](https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/layouts/layout-types.html)

Opzioni di comando:

```bash
bin/magento dev:xml:convert [-o|--overwrite] {xml file} {xslt stylesheet}
```

Dove:

- `{xml file}`—è il percorso completo e il nome file di un file XML di layout da convertire (obbligatorio)
- `{xslt stylesheet}`—è il percorso completo e il nome file di un file foglio di stile XSLT da utilizzare per la conversione (obbligatorio)
- `-o|--overwrite`- includi questa opzione per sovrascrivere il file XML esistente
