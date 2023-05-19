---
title: Tipi di configurazione
description: Crea o estende i tipi di configurazione.
exl-id: 4390c310-b35a-431a-859f-3fd46d8ba6bf
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 0%

---

# Tipi di configurazione

## Estendere i tipi di configurazione

Per estendere un tipo di configurazione esistente, devi solo creare un file di configurazione nel modulo.

Ad esempio, per aggiungere un osservatore evento, puoi creare `app/code/{VendorName}/{ModuleName}/etc/events.xml` e dichiarare un nuovo osservatore.

Poiché il tipo di configurazione dell’evento esiste in Commerce, il caricatore e il `events.xsd` lo schema di convalida è già presente e funzionante.

Nuovo `events.xml` viene automaticamente raccolto dal modulo e unito ad altri `events.xml` file per altri moduli.

## Creare tipi di configurazione

Per creare un tipo di configurazione, devi aggiungere almeno:

- Un caricatore
- Schema di convalida XSD
- File di configurazione XML

Ad esempio, per introdurre un adattatore per un nuovo server di ricerca che consenta alle estensioni di configurare il modo in cui le relative entità vengono indicizzate in tale server, crea:

- Un caricatore
- Un file di schema XSD
- Un file di configurazione con nome appropriato. Ad esempio: `search.xml`. Questo file viene letto e convalidato in base allo schema.
- Qualsiasi altra classe necessaria per il tuo lavoro.

>[!INFO]
>
>Se i nuovi moduli dispongono di `search.xml` file, vengono uniti al file al momento del caricamento.

### Esempi di utilizzo

Per creare un tipo di configurazione:

1. Crea il file XSD.
1. Crea il file XML.
1. Definisci l’oggetto di configurazione nel `di.xml`.

   L&#39;esempio seguente dal modulo Magento_Sales [di.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/di.xml) illustra l&#39;aspetto di un oggetto di configurazione.

   ```xml
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
   
       <type name="Magento\Sales\Model\Order\Pdf\Config\Reader">
           <arguments>
               <argument name="fileName" xsi:type="string">pdf.xml</argument>
               <argument name="converter" xsi:type="object">Magento\Sales\Model\Order\Pdf\Config\Converter</argument>
               <argument name="schemaLocator" xsi:type="object">Magento\Sales\Model\Order\Pdf\Config\SchemaLocator</argument>
           </arguments>
       </type>
   
       <virtualType name="pdfConfigDataStorage" type="Magento\Framework\Config\Data">
           <arguments>
               <argument name="reader" xsi:type="object">Magento\Sales\Model\Order\Pdf\Config\Reader</argument>
               <argument name="cacheId" xsi:type="string">sales_pdf_config</argument>
           </arguments>
       </virtualType>
   
       <type name="Magento\Sales\Model\Order\Pdf\Config">
           <arguments>
               <argument name="dataStorage" xsi:type="object">pdfConfigDataStorage</argument>
           </arguments>
       </type>
   </config>
   ```

   - Il primo nodo di tipo imposta il nome del file del Reader, associato `Converter` e `SchemaLocator` classi.
   - Quindi, il `pdfConfigDataStorage` nodo di tipo virtuale associa la classe reader a un&#39;istanza di [Magento\Framework\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Data.php).
   - Infine, l’ultimo nodo di tipo collega il tipo virtuale di dati di configurazione al [Magento\Sales\Model\Order\Pdf\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config.php) che viene utilizzata per la lettura effettiva dei valori in da quelli [pdf.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/pdf.xml) file.

1. Definire un lettore estendendolo [Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) e riscrivi i seguenti parametri:

   ```php
   $_idAttributes // Array of node attribute IDs.
   ```

**Esempio:**

```php
<?php
/**
 * Copyright © Magento, Inc. All rights reserved.
 * See COPYING.txt for license details.
 */

namespace Vendor\ModuleName\Model\Config;

use Magento\Framework\Config\Reader\Filesystem;

class Reader extends Filesystem
{
    /**
     * List of identifier attributes for merging
     *
     * @var array
     */
    protected $_idAttributes = [
         '</path/to/node_in_your_xml_file>'        => '<identifierAttributeName>',
         '</path/to/other/node_in_your_xml_file>'  => '<identifierAttributeName>',
    ];
}
```

>[!INFO]
>
>Se preferisci creare una versione personalizzata del lettore, puoi farlo implementando `\Magento\Framework\Config\ReaderInterface`. Consulta [Lettore di configurazione Magento_Analytics](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config/Reader.php)

Dopo aver definito il lettore, utilizzalo per raccogliere, unire, convalidare e convertire i file di configurazione in una rappresentazione array interna.

## Convalidare un tipo di configurazione

Ogni file di configurazione viene convalidato in base a uno schema specifico per il relativo tipo di configurazione. Esempio: eventi che, nelle versioni precedenti di Commerce, erano configurati in `config.xml`, sono ora configurati in `events.xml`.

I file di configurazione possono essere convalidati prima (facoltativo) e dopo qualsiasi unione di più file che influiscono sullo stesso tipo di configurazione. A meno che le regole di convalida per i singoli file e i file uniti non siano identiche, è necessario fornire due schemi per la convalida dei file di configurazione:

- Schema per convalidare un singolo utente
- Schema per convalidare un file unito

I nuovi file di configurazione devono essere accompagnati da schemi di convalida XSD. Un file di configurazione XML e il relativo file di convalida XSD devono avere lo stesso nome.

Se è necessario utilizzare due file XSD per un singolo file XML, i nomi degli schemi devono essere riconoscibili e associati al file XML.
Se si dispone di `events.xml` file e una prima `events.xsd` file, i file XSD per il file unito `events.xml` il file potrebbe essere denominato `events_merged.xsd`.
Per garantire la convalida di un file XML tramite il file XSD appropriato, è necessario aggiungere il nome URN (Uniform Resource Name) al file XSD nel file XML. Ad esempio:

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager:etc/config.xsd">
```

L’IDE può convalidare i file di configurazione sia in fase di esecuzione che durante lo sviluppo.
