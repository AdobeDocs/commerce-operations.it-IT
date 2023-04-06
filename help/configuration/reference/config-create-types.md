---
title: Tipi di configurazione
description: Crea o estendi i tipi di configurazione.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 0%

---


# Tipi di configurazione

## Estendi i tipi di configurazione

Per estendere un tipo di configurazione esistente, devi solo creare un file di configurazione nel modulo.

Ad esempio, per aggiungere un osservatore evento, puoi creare `app/code/{VendorName}/{ModuleName}/etc/events.xml` e dichiarare un nuovo osservatore.

Poiché il tipo di configurazione dell’evento esiste in Commerce, il caricatore e il `events.xsd` la convalida dello schema è già presente e funzionale.

La nuova `events.xml` viene raccolto automaticamente dal modulo e unito ad altri `events.xml` file per altri moduli.

## Creare tipi di configurazione

Per creare un tipo di configurazione, devi aggiungere almeno:

- Caricatore
- Schema di convalida XSD
- File di configurazione XML

Ad esempio, per introdurre una scheda per un nuovo server di ricerca che consenta alle estensioni di configurare la modalità di indicizzazione delle entità in tale server, crea:

- Caricatore
- Un file di schema XSD
- Un file di configurazione con nome appropriato. Ad esempio: `search.xml`. Questo file viene letto e convalidato in base allo schema.
- Qualsiasi altra classe richiesta per il tuo lavoro.

>[!INFO]
>
>Se i nuovi moduli hanno una `search.xml` vengono uniti al file quando viene caricato.

### Esempi di utilizzo

Per creare un tipo di configurazione:

1. Crea il tuo file XSD.
1. Crea il file XML.
1. Definire l&#39;oggetto di configurazione nel `di.xml`.

   Esempio del modulo Magento_Sales [di.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/di.xml) illustra l&#39;aspetto di un oggetto di configurazione.

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

   - Il primo nodo di tipo imposta il nome del Reader, associato `Converter` e `SchemaLocator` classi.
   - Quindi, il `pdfConfigDataStorage` il nodo del tipo virtuale associa la classe del lettore a un&#39;istanza di [Magento\Framework\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Data.php).
   - Infine, l&#39;ultimo nodo di tipo associa il tipo di dati virtuale alla configurazione [Magento\Sales\Model\Order\Pdf\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config.php) Classe , che viene utilizzato per leggere effettivamente i valori in da quelli [pdf.xml](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/etc/pdf.xml) file.

1. Definire un lettore estendendo [Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) e riscrivi i seguenti parametri:

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
>Se preferisci creare una tua versione del lettore, puoi farlo implementando `\Magento\Framework\Config\ReaderInterface`. Vedi [Lettore di configurazione Magento_Analytics](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config/Reader.php)

Dopo aver definito il lettore, utilizzalo per raccogliere, unire, convalidare e convertire i file di configurazione in una rappresentazione di array interna.

## Convalida di un tipo di configurazione

Ciascun file di configurazione viene convalidato in base a uno schema specifico per il relativo tipo di configurazione. Esempio: eventi che, nelle versioni Commerce precedenti, erano configurati in `config.xml`ora sono configurati in `events.xml`.

I file di configurazione possono essere convalidati sia prima (facoltativo) che dopo qualsiasi unione di più file che influiscono sullo stesso tipo di configurazione. A meno che le regole di convalida per i singoli file e i file uniti non siano identiche, è necessario fornire due schemi per la convalida dei file di configurazione:

- Schema per convalidare un singolo
- Schema per la convalida di un file unito

I nuovi file di configurazione devono essere accompagnati da schemi di convalida XSD. Un file di configurazione XML e il relativo file di convalida XSD devono avere lo stesso nome.

Se è necessario utilizzare due file XSD per un singolo file XML, i nomi degli schemi devono essere riconoscibili e associati al file XML.
Se hai un `events.xml` e un primo `events.xsd` file, i file XSD per l&#39;unione `events.xml` file con nome `events_merged.xsd`.
Per garantire la convalida di un file XML tramite un file XSD appropriato, è necessario aggiungere l&#39;URL (Uniform Resource Name) al file XSD nel file XML. Ad esempio:

```xml
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager:etc/config.xsd">
```

L’IDE può convalidare i file di configurazione sia in fase di runtime che durante lo sviluppo.
