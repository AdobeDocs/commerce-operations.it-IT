---
title: Configura le [!DNL Data Migration Tool]
description: Scopri i due metodi per configurare il [!DNL Data Migration Tool] trasferire i dati tra il Magento 1 e il Magento 2.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '792'
ht-degree: 0%

---


# Configura le [!DNL Data Migration Tool]

Dopo aver installato [!DNL Data Migration Tool], la seguente directory contiene i file di mappatura e configurazione:

* Magento Open Source:
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-opensource`: Configurazione e script per la migrazione dal Magento Open Source 1 al Magento Open Source 2

* Adobe Commerce:
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/opensource-to-commerce`: Configurazione e script per la migrazione dal Magento Open Source 1 ad Adobe Commerce 2
   * `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/commerce-to-commerce`: Configurazione e script per la migrazione da Adobe Commerce 1 ad Adobe Commerce 2

Le directory precedenti contengono sottodirectory per ogni versione supportata.

## Configurazione della migrazione

Esistono due modi per configurare il [!DNL Data Migration Tool]:

* Configura le [!DNL Data Migration Tool] in un modulo separato (consigliato)
* Modificare la [!DNL Data Migration Tool] nella configurazione `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/` directory.

Per gestire la configurazione di migrazione e utilizzarla per la distribuzione tramite il controllo del codice sorgente, è necessario creare un modulo separato.
Se intendi eseguire il [!DNL Data Migration Tool] solo localmente, puoi modificare i file nella `<your Magento 2 install dir>/vendor/magento/data-migration-tool/` direttamente.

### Configurare la migrazione in un modulo separato

Prima di eseguire la migrazione di qualsiasi dato, è necessario creare un modulo Magento 2.

1. Crea un modulo di Magento 2.

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

1. Copia il `config.xml.dist` file di configurazione dalla directory appropriata del [!DNL Data Migration Tool] (`<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>`) nel `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/config.xml` file.

   Ad esempio, se esegui la migrazione `Magento 1.9.3.6 Community Edition` a `Magento 2 Open Source`:

   ```bash
   cd <your Magento 2 install dir>
   ```

   ```bash
   cp vendor/magento/data-migration-tool/etc/opensource-to-opensource/1.9.3.6/config.xml.dist app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.3.6/config.xml
   ```

1. In `config.xml` file, è necessario impostare i dettagli di accesso ai database M1 e M2 e la chiave di crittografia.

1. Se l&#39;archivio M1 presenta modifiche personalizzate, è necessario mappare il resto dei file di configurazione alle personalizzazioni dell&#39;archivio del Magento 1. Vedi [Operazioni con file di configurazione e mappatura](#migration-config).

### Configura la migrazione in `vendor` cartella

Prima di eseguire la migrazione di qualsiasi dato, devi creare una `config.xml` file di configurazione dall&#39;esempio fornito.

Per configurare le [!DNL Data Migration Tool] per la migrazione:

1. Accedi al server delle applicazioni come o passa a [proprietario del file system](../../installation/prerequisites/file-system/overview.md).

1. Passa alla seguente directory:

   ```bash
   <your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>
   ```

1. Immetti il seguente comando per creare un `config.xml` dal campione fornito:

   ```bash
   cp config.xml.dist config.xml
   ```

1. Apri `config.xml` in un editor di testo.

1. Come minimo, il file config.xml deve contenere i dettagli di accesso ai database M1 e M2 e le chiavi di crittografia.

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

   La &lt;crypt_key> Il tag deve contenere un valore. Puoi trovarlo all&#39;interno della `<key>` , che si trova nel file app/etc/local.xml sull’istanza di Magento 1.

   Parametri opzionali:

   * Password utente database: `password=<password>`
   * Porta personalizzata del database: `port=<port>`
   * Prefisso tabella: `<source_prefix>`, `<dest_prefix>`

   Ad esempio, se il nome utente del proprietario del database è `root` con password `pass` e si utilizza il prefisso `magento1` nel database di Magento 1, utilizza quanto segue in `config.xml`:

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

Al termine, salva le modifiche apportate a `config.xml` e esci dall’editor di testo.

### Connessione tramite il protocollo TLS

Puoi anche connetterti a un database utilizzando il protocollo TLS (ovvero utilizzando chiavi di crittografia pubblica/privata). Aggiungi i seguenti attributi facoltativi al `database` elemento:

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

## Operazioni con file di configurazione e mappatura

La [!DNL Data Migration Tool] utilizza *file di mappatura* per consentire la mappatura personalizzata del database tra i database di Magento 1 e Magento 2, tra cui:

* Modifica dei nomi delle tabelle

* Modifica dei nomi dei campi

* Ignorare tabelle o campi

* Adattare il trasferimento dei dati di un campo al formato Magento 2

I file di mappatura per le versioni di Magento supportate si trovano nelle sottodirectory di `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc`

Per utilizzare i file di mappatura:

1. Copiali da `<your Magento 2 install dir>/vendor/magento/data-migration-tool/etc/<migration edition>/<ce or version>/` a `<your Magento 2 install dir>/app/code/Vendor/Migration/etc/<migration edition>/<ce or version>/` e rimuovere `.dist` [estensione](https://glossary.magento.com/extension).

1. Aggiorna il percorso del file appena copiato nel `<options>` nodo `config.xml`. Il percorso aggiornato deve essere uno dei seguenti:

   1. Percorso assoluto del file, ad esempio g. `/var/www/html/app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. percorso relativo del file del modulo magento/data-migration-tool: `etc/opensource-to-opensource/1.9.4.1/map.xml`
   1. Percorso file relativo alla directory principale del Magento: `app/code/Vendor/Migration/etc/opensource-to-opensource/1.9.4.1/map.xml`

La `<Magento 2 dir>/vendor/magento/data-migration-tool/etc` e `<Magento 2 dir>/vendor/magento/data-migration-tool/etc/<ce version>` Le directory contengono i seguenti file di configurazione:

Anche se stai lavorando con il `map.xml.dist` nella maggior parte dei casi, la tabella seguente illustra ogni mappatura e altri file.

| Nome file mapping | Descrizione |
| --- | --- |
| `class-map.xml.dist` | Dizionario delle mappature delle classi tra il Magento 1 e il Magento 2 |
| `config.xml.dist` | File di configurazione principale che specifica le configurazioni del database del Magento 1 e del Magento 2, la configurazione dei passaggi e i collegamenti alla mappatura dei file |
| *Solo Adobe Commerce*. `customer-attr-document-groups.xml.dist` | Elenco di tabelle utilizzate nel passaggio Attributi cliente personalizzati. |
| *Solo Adobe Commerce*. `customer-attr-map.xml.dist` | Mappa il file utilizzato nel passaggio Attributi del cliente personalizzati. |
| `deltalog.xml.dist` | Contiene l&#39;elenco delle tabelle necessarie per l&#39;impostazione delle routine di database. |
| `eav-attribute-groups.xml.dist` | Contiene l’elenco degli attributi utilizzati in Eav Step. |
| `eav-document-groups.xml.dist` | Contiene l’elenco delle tabelle utilizzate in Eav Step. |
| `log-document-groups.xml.dist` | Contiene l’elenco delle tabelle utilizzate in Log Step. |
| `map-eav.xml.dist` | Mappa il file utilizzato in EAV Step. |
| `map-log.xml.dist` | File di mappatura del registro. |
| *Solo Adobe Commerce*. `map-sales.xml.dist` | Mappa il file utilizzato in Passaggio ordine di vendita. |
| `map.xml.dist` | File di mappatura necessario per il passaggio mappa. |
| `settings.xml.dist` | Impostazione del file di configurazione della migrazione che specifica le regole necessarie per la migrazione del `core_config_data` tabella. |
| `customer-attribute-groups.xml.dist` | Contiene l&#39;elenco degli attributi utilizzati nel passaggio Attributi del cliente. |
| `customer-document-groups.xml.dist` | Contiene l&#39;elenco delle tabelle utilizzate nel passaggio Attributi del cliente. |
| `map-customer.xml.dist` | Mappa il file utilizzato nel passaggio Attributi del cliente. |
| `order-grids-document-groups.xml.dist` | Contiene l&#39;elenco delle tabelle utilizzate in OrderGrids Step. |
| `map-document-groups.xml.dist` | Definisce quali campi vengono aggiornati quando si verificano duplicati all’inserimento dei dati |
| `map-stores.xml.dist` | Mappa il file utilizzato in Stores Step. |
| `map-tier-price.xml.dist` | Mappa il file utilizzato in Fase del prezzo di livello. |
| *Solo Adobe Commerce*. `visual_merchandiser_map.xml.dist` | Mappa il file utilizzato in VisualMerchandiser Step. |
| *Solo Adobe Commerce*. `visual_merchandiser_attribute_groups.xml.dist` | Contiene l&#39;elenco degli attributi utilizzati in VisualMerchandiser Step. |
| *Solo Adobe Commerce*. `visual_merchandiser_document_groups.xml.dist` | Contiene l&#39;elenco delle tabelle utilizzate in VisualMerchandiser Step. |

Puoi fare riferimento a [[!DNL Data Migration Tool] Specifiche tecniche](technical-specification.md) per ulteriori dettagli.
