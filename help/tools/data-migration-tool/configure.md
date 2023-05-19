---
title: Configurare [!DNL Data Migration Tool]
description: Scopri i due metodi per configurare [!DNL Data Migration Tool] trasferire dati tra il Magento 1 e il Magento 2.
exl-id: 273be997-8085-4488-a455-f6005a85b406
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '789'
ht-degree: 0%

---

# Configurare [!DNL Data Migration Tool]

Dopo aver installato [!DNL Data Migration Tool], la seguente directory contiene i file di mappatura e configurazione:

* Magento Open Source:
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-opensource`: configurazione e script per la migrazione dal Magento Open Source 1 al Magento Open Source 2

* Adobe Commerce:
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-commerce`: configurazione e script per la migrazione dal Magento Open Source 1 ad Adobe Commerce 2
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/commerce-to-commerce`: configurazione e script per la migrazione da Adobe Commerce 1 a Adobe Commerce 2

Le directory precedenti contengono sottodirectory per ogni versione supportata.

## Configurazione della migrazione

Esistono due modi per configurare [!DNL Data Migration Tool]:

* Configurare [!DNL Data Migration Tool] in un modulo separato (consigliato)
* Modificare il [!DNL Data Migration Tool] configurazione in `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/` directory.

Per utilizzare il controllo del codice sorgente per gestire la configurazione della migrazione e utilizzarla per la distribuzione, è necessario creare un modulo separato.
Se si prevede di eseguire [!DNL Data Migration Tool] solo in locale, è possibile modificare i file in `<your Magento 2 install dir>/vendor/magento/data-migration-tool/` direttamente dalla directory.

### Configurare la migrazione in un modulo separato

Prima di eseguire la migrazione dei dati, è necessario creare un modulo Magento 2.

1. Creazione di un modulo Magento 2.

   * `<your Magento 2 install dir>/app/code/Vendor/Migration/composer.json`

   ```json
   {
       "name": "vendor/migration",
       "description": "Providing config for migration",
       "config": {
           "sort-packages": true
       },
       "require": {
           "magento/framework": "*",
           "magento/data-migration-tool": "*"
       },
       "type": "magento2-module",
       "autoload": {
           "files": [
               "registration.php"
           ],
           "psr-4": {
               "Vendor\\Migration\\": ""
           }
       },
       "version": "1.0.0"
   }
   ```

   * `<your Magento 2 install dir>/app/code/Vendor/Migration/registration.php`

   ```php
   <?php
   
   \Magento\Framework\Component\ComponentRegistrar::register(
       \Magento\Framework\Component\ComponentRegistrar::MODULE,
       'Vendor_Migration',
       __DIR__
   );
   ```

   * `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/module.xml`

   ```xml
   <?xml version="1.0"?>
   
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
           xsi:noNamespaceSchemaLocation="urn:magento:framework:Module/etc/module.xsd">
       <module name="Vendor_Migration" setup_version="1.0.0">
           <sequence>
               <module name="Magento_DataMigrationTool"/>
           </sequence>
       </module>
   </config>
   ```

1. Copia il `config.xml.dist` file di configurazione dalla directory appropriata del file [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>`) nel `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/config.xml` file.

   Ad esempio, se esegui la migrazione `Magento 1.9.3.6 Community Edition` a `Magento 2 Open Source`:

   ```bash
   cd <your Magento 2 install dir>
   ```

   ```bash
   cp vendor/magento/data-migration-tool/etc/opensource-to-opensource/1.9.3.6/config.xml.dist app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.3.6/config.xml
   ```

1. In `config.xml` file, è necessario impostare i dettagli di accesso ai database M1 e M2 e alla chiave di crittografia.

1. Se nell&#39;archivio M1 sono presenti modifiche personalizzate, è necessario mappare il resto dei file di configurazione alle personalizzazioni dell&#39;archivio del Magento 1. Consulta [Utilizzare i file di configurazione e mappatura](#migration-config).

### Configurare la migrazione in `vendor` cartella

Prima di eseguire la migrazione dei dati, è necessario creare una `config.xml` file di configurazione dall’esempio fornito.

Per configurare [!DNL Data Migration Tool] migrazione:

1. Accedere al server applicazioni come, o passare a, [proprietario del file system](../../installation/prerequisites/file-system/overview.md).

1. Passa alla seguente directory:

   ```bash
   <your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>
   ```

1. Immetti il seguente comando per creare un `config.xml` dal campione fornito:

   ```bash
   cp config.xml.dist config.xml
   ```

1. Apri `config.xml` in un editor di testo.

1. Il file config.xml deve contenere almeno i dettagli di accesso ai database M1 e M2 e le chiavi di crittografia.

   ```xml
   <source>
      <database host="127.0.0.1" name="magento1" user="root"/>
   </source>
   <destination>
      <database host="127.0.0.1" name="magento2" user="root"/>
   </destination>
   <options>
      <crypt_key />
   </options>
   ```

   Il &lt;crypt_key> il tag deve contenere un valore. Lo si può trovare all&#39;interno del `<key>` , che si trova nel file app/etc/local.xml nell’istanza Magento 1.

   Parametri facoltativi:

   * Password utente database: `password=<password>`
   * Porta personalizzata del database: `port=<port>`
   * Prefisso tabella: `<source_prefix>`, `<dest_prefix>`

   Ad esempio, se il nome utente del proprietario del database è `root` con password `pass` e utilizzi il prefisso `magento1` nel database del Magento 1, utilizza quanto segue in `config.xml`:

   ```xml
   <source>
      <database host="127.0.0.1" name="magento1" user="root" password="pass"/>
   </source>
   <destination>
      <database host="127.0.0.1" name="magento2" user="root" password="pass"/>
   </destination>
   <options>
      <source_prefix>magento1</source_prefix>
      <crypt_key>f3e25abe619dae2387df9fs594f01985</crypt_key>
   </options>
   ```

Al termine, salva le modifiche apportate a `config.xml` ed esci dall’editor di testo.

### Connetti utilizzando il protocollo TLS

È inoltre possibile connettersi a un database utilizzando il protocollo TLS, ovvero le chiavi di crittografia pubbliche/private. Aggiungi i seguenti attributi facoltativi alla `database` elemento:

* `ssl_ca`
* `ssl_cert`
* `ssl_key`

Ad esempio:

```xml
<source>
    <database host="localhost" name="magento1" user="root" ssl_ca="/path/to/file" ssl_cert="/path/to/file" ssl_key="/path/to/file"/>
</source>
<destination>
    <database host="localhost" name="magento2" user="root" ssl_ca="/path/to/file" ssl_cert="/path/to/file" ssl_key="/path/to/file"/>
</destination>
```

## Utilizzare i file di configurazione e mappatura

Il [!DNL Data Migration Tool] utilizza *file di mappatura* per consentire l&#39;esecuzione di mapping di database personalizzati tra i database del Magento 1 e del Magento 2, inclusi:

* Modifica dei nomi delle tabelle

* Modifica dei nomi dei campi

* Ignorare tabelle o campi

* Adattare il trasferimento dei dati di un campo al formato Magento 2

I file di mappatura per le versioni di Magento supportate si trovano nelle sottodirectory di `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc`

Per utilizzare i file di mappatura:

1. Copia da `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>/` a `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/` e rimuovere `.dist` estensione.

1. Aggiornare il percorso del file appena copiato in `<options>` nodo di `config.xml`. Il percorso aggiornato deve essere uno dei seguenti:

   1. Percorso assoluto del file, ad esempio `/var/www/html/app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. percorso file relativo del modulo magento/data-migration-tool: `etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. Percorso file relativo alla directory principale del Magento: `app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`

Il `<Magento 2 dir>/vendor/magento/data-migration-tool/etc` e `<Magento 2 dir>/vendor/magento/data-migration-tool/etc/<ce version>` Le directory contengono i seguenti file di configurazione:

Anche se utilizzi il `map.xml.dist` file nella maggior parte dei casi, la tabella seguente illustra ogni mappatura e altri file.

| Nome file di mappatura | Descrizione |
| --- | --- |
| `class-map.xml.dist` | Dizionario delle mappature di classe tra il Magento 1 e il Magento 2 |
| `config.xml.dist` | File di configurazione principale che specifica le configurazioni del database del Magento 1 e del Magento 2, la configurazione dei passaggi e i collegamenti ai file di mappatura |
| *Solo Adobe Commerce*. `customer-attr-document-groups.xml.dist` | Elenco di tabelle utilizzate nel passaggio Attributi cliente personalizzati. |
| *Solo Adobe Commerce*. `customer-attr-map.xml.dist` | File di mappa utilizzato nel passaggio Attributi del cliente personalizzati. |
| `deltalog.xml.dist` | Contiene l&#39;elenco delle tabelle necessarie per l&#39;impostazione delle routine di database. |
| `eav-attribute-groups.xml.dist` | Contiene un elenco di attributi utilizzati in ciascun passaggio. |
| `eav-document-groups.xml.dist` | Contiene un elenco di tabelle utilizzate in ciascun passaggio. |
| `log-document-groups.xml.dist` | Contiene l’elenco delle tabelle utilizzate nel passaggio del registro. |
| `map-eav.xml.dist` | File di mappa utilizzato nel passaggio EAV. |
| `map-log.xml.dist` | File di mappatura del registro. |
| *Solo Adobe Commerce*. `map-sales.xml.dist` | File di mapping utilizzato nel passaggio Ordine di vendita. |
| `map.xml.dist` | File di mappatura necessario per il passaggio di mappatura. |
| `settings.xml.dist` | Impostazione del file di configurazione della migrazione che specifica le regole necessarie per la migrazione del `core_config_data` tabella. |
| `customer-attribute-groups.xml.dist` | Contiene un elenco di attributi utilizzati nel passaggio Attributi del cliente. |
| `customer-document-groups.xml.dist` | Contiene un elenco di tabelle utilizzate nel passaggio Attributi del cliente. |
| `map-customer.xml.dist` | File di mappa utilizzato nel passaggio Attributi del cliente. |
| `order-grids-document-groups.xml.dist` | Contiene un elenco di tabelle utilizzate nel passo OrderGrids. |
| `map-document-groups.xml.dist` | Definisce quali campi vengono aggiornati quando si verificano duplicazioni all’inserimento dei dati |
| `map-stores.xml.dist` | File mappa utilizzato nel passaggio Archivi. |
| `map-tier-price.xml.dist` | File di mappa utilizzato nel passo prezzo di livello. |
| *Solo Adobe Commerce*. `visual_merchandiser_map.xml.dist` | File mappa utilizzato nel passaggio di VisualMerchandiser. |
| *Solo Adobe Commerce*. `visual_merchandiser_attribute_groups.xml.dist` | Elenco di attributi utilizzati nel passaggio di VisualMerchandiser. |
| *Solo Adobe Commerce*. `visual_merchandiser_document_groups.xml.dist` | Contiene un elenco di tabelle utilizzate nel passaggio di VisualMerchandiser. |

Puoi consultare [[!DNL Data Migration Tool] Specifiche tecniche](technical-specification.md) per ulteriori dettagli.
