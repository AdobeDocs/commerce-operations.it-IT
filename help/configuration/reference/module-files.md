---
title: File di configurazione del modulo
description: Scopri come personalizzare un modulo utilizzando i tipi di configurazione.
exl-id: 87433c28-8e3d-43d0-b77e-3ff9a680af5f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '2024'
ht-degree: 0%

---

# Panoramica dei file di configurazione del modulo

Le responsabilità del `config.xml` Il file di configurazione utilizzato nelle versioni precedenti di Commerce ora è suddiviso tra diversi file, situati in varie directory dei moduli. I file di configurazione multipli di Commerce vengono caricati su richiesta solo quando un modulo richiede un tipo di configurazione specifico.

È possibile utilizzare questi file, denominati anche _tipi di configurazione_- per personalizzare aspetti specifici del comportamento del modulo.

Più moduli possono dichiarare file di configurazione che influiscono sullo stesso tipo di configurazione (ad esempio, eventi) e questi file di configurazione multipli vengono uniti.

Di seguito sono riportati i termini comuni utilizzati in questo argomento:

- **Oggetto di configurazione**- Libreria o classe Commerce responsabile della definizione e della convalida del tipo di configurazione. Ad esempio, l’oggetto di configurazione per `config.xml` è [Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php).

- **Fase di configurazione**- Gli stadi sono definiti come _primario_, _globale_, e _area_. Ogni fase determina quando il tipo di configurazione viene caricato e unito con tipi di configurazione con lo stesso nome. Ad esempio: `module.xml` i file vengono uniti con altri `module.xml` file.

- **Ambito di configurazione**- Complementare agli stadi di configurazione, un ambito definisce il modello del tipo di configurazione. Ad esempio: `adminhtml` è un ambito di area caricato con nella fase con altri moduli&#39; `adminhtml` configurazioni. Per ulteriori informazioni, consulta [Moduli e aree](https://developer.adobe.com/commerce/php/architecture/modules/areas/).

## Caricamento della configurazione e unione

Questa sezione descrive come caricare e unire i file di configurazione.

### Come Commerce carica i file di configurazione

Commerce carica i file di configurazione nell’ordine seguente (tutti i percorsi sono relativi alla directory di installazione di Commerce):

- Configurazione principale ([app/etc/di.xml](https://github.com/magento/magento2/blob/2.4/app/etc/di.xml)). Questo file viene utilizzato per avviare Commerce.
- Configurazioni globali da moduli (`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/*.xml`). Raccoglie determinati file di configurazione da tutti i moduli e li unisce.
- Configurazione specifica dell&#39;area dai moduli (`<your component base dir>/<vendorname>/<component-type>-<component-name>/etc/<area>/*.xml`). Raccoglie i file di configurazione da tutti i moduli e li unisce nella configurazione globale. Alcune configurazioni specifiche per l’area possono ignorare o estendere la configurazione globale.

dove

- `<your component base dir>` è la directory di base in cui si trova il componente. I valori tipici sono `app/code` o `vendor` relativo alla directory di installazione di Commerce.
- `<vendorname>` è il nome del fornitore del componente; ad esempio, il nome del fornitore di Commerce è `magento`.
- `<component-type>` è uno dei seguenti:

   - `module-`: estensione o modulo.
   - `theme-`: tema.
   - `language-`: pacchetto lingua.

>[!INFO]
>
>Attualmente, i temi si trovano in `<magento_root>/app/design/frontend` o `<magento_root>/app/design/adminhtml`.

- `<component-name>`: nome del componente come definito in [compositore.json](https://github.com/magento/magento2/blob/2.4/composer.json).

### Unione file di configurazione

I nodi nei file di configurazione vengono uniti in base ai relativi XPath completi, per i quali è stato definito un attributo speciale in `$idAttributes` array dichiarato come identificatore. Questo identificatore deve essere univoco per tutti i nodi nidificati sotto lo stesso nodo principale.

Algoritmo di unione delle applicazioni Commerce:

- Se gli identificatori dei nodi sono uguali (o se non è definito alcun identificatore), tutto il contenuto sottostante nel nodo (attributi, nodi secondari e contenuto scalare) viene sovrascritto.
- Se gli identificatori dei nodi non sono uguali, il nodo è un nuovo elemento figlio del nodo principale.
- Se il documento originale ha più nodi con lo stesso identificatore, viene attivato un errore perché gli identificatori non possono essere distinti.

Dopo aver unito i file di configurazione, il documento risultante contiene tutti i nodi dei file originali.

>[!INFO]
>
>È possibile utilizzare [\Magento\Framework\Config\Reader\Filesystem](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php) classe per il debug e per comprendere la logica alla base di [caricatore file di configurazione](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L125) e [unisci configurazioni](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/Reader/Filesystem.php#L144) processo.

## Tipi di configurazione, oggetti e interfacce

Nelle sezioni seguenti vengono fornite informazioni sui tipi di configurazione, sugli oggetti di configurazione corrispondenti e sulle interfacce che è possibile utilizzare per lavorare con gli oggetti:

### Tipi di configurazione e oggetti

La tabella seguente mostra ogni tipo di configurazione e l’oggetto di configurazione Commerce a cui si riferisce.

| File di configurazione | Descrizione | Fase | Oggetto di configurazione |
| --- | --- | --- | --- |
| `address_formats.xml` | Dichiarazione formato indirizzo | primario, globale | [\Magento\Customer\Model\Address\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/Model/Address/Config.php) |
| `acl.xml` | [Elenco di controllo di accesso](https://developer.adobe.com/commerce/webapi/get-started/authentication/#relationship-between-aclxml-and-webapixml) | globale | [\Magento\Framework\Acl\AclResource\Provider](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Acl/AclResource/Provider.php) |
| `analytics.xml` | [Reporting avanzato](https://devdocs.magento.com/guides/v2.4/advanced-reporting/data-collection.html) | primario, globale | [\Magento\Analytics\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/Model/Config/Reader.php) |
| `cache.xml` | Dichiarazione tipo cache | primario, globale | [\Magento\Framework\Cache\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Config/Data.php) |
| `catalog_attributes.xml` | Configurazione attributi catalogo | globale | [\Magento\Catalog\Model\Attribute\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/Attribute/Config/Data.php) |
| `config.php` e `env.php` | [Configurazione della distribuzione](../reference/deployment-files.md) | Questi file sono leggibili/scrivibili dal processore di configurazione interno. | Non ha alcun oggetto, non può essere personalizzato |
| `config.xml` | Configurazione del sistema | primario, globale | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `communication.xml` | [Definisce gli aspetti del sistema della coda di messaggi](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#communicationxml) | globale | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Communication](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Communication.php) |
| `crontab.xml` | [Configura i gruppi cron](../cron/custom-cron-reference.md#configure-cron-groups) | globale | [\Magento\Cron\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Config/Data.php) |
| `cron_groups.xml` | [Specifica le opzioni del gruppo cron](../cron/custom-cron-reference.md) | globale | [\Magento\Cron\Model\Groups\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Cron/Model/Groups/Config/Data.php) |
| `db_schema.xml` | [Schema dichiarativo](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/) | globale | [Magento\Framework\Setup\Declaration\Schema](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/Declaration/Schema/SchemaConfig.php) |
| `di.xml` | [Iniezione di dipendenza](https://developer.adobe.com/commerce/php/development/components/dependency-injection/) configurazione | primario, globale, area | [\Magento\Framework\ObjectManager\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/ObjectManager/Config/Config.php) |
| `eav_attributes.xml` | Fornisce la configurazione degli attributi EAV | globale | [\Magento\Eav\Model\Entity\Attribute\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Eav/Model/Entity/Attribute/Config.php) |
| `email_templates.xml` | Configurazione dei modelli e-mail | globale | [\Magento\Email\Model\Template\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Email/Model/Template/Config/Data.php) |
| `esconfig.xml` | [Configurazione parole non significative per le impostazioni locali del motore di ricerca](../search/search-stopwords.md#create-stopwords-for-a-new-locale) | globale | [\Magento\Elasticsearch\Model\Adapter\Index\Config\EsConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Elasticsearch/Model/Adapter/Index/Config/EsConfig.php) |
| `events.xml` | Configurazione evento/osservatore | globale, area | [\Magento\Framework\Event](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Event.php) |
| `export.xml` | Esporta configurazione entità | globale | [\Magento\ImportExport\Model\Export\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Export/Config.php) |
| `extension_attributes.xml` | [Attributi di estensione](https://developer.adobe.com/commerce/php/development/components/attributes/#extension-attributes) | globale | [\Magento\Framework\Api\ExtensionAttribute\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Api/ExtensionAttribute/Config.php) |
| `fieldset.xml` | Definisce i set di campi | globale | [\Magento\Framework\DataObject\Copy\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DataObject/Copy/Config/Reader.php) |
| `indexer.xml` | [Dichiara gli indicizzatori](https://developer.adobe.com/commerce/php/development/components/indexing/custom-indexer/) | globale | [\Magento\Framework\Indexer\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Indexer/Config/Reader.php) |
| `import.xml` | Dichiara entità di importazione | globale | [\Magento\ImportExport\Model\Import\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/ImportExport/Model/Import/Config.php) |
| `menu.xml` | Definisce le voci di menu per l’Amministratore | adminhtml | [\Magento\Backend\Model\Menu\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Backend/Model/Menu/Config/Reader.php) |
| `module.xml` | Definisce i dati di configurazione del modulo e la dipendenza morbida | primario, globale | [\Magento\Framework\Module\ModuleList\Loader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Module/ModuleList/Loader.php) |
| `mview.xml` | [Configurazione MView](https://developer.adobe.com/commerce/php/development/components/indexing/custom-indexer/#mview-configuration) | primario, globale | [\Magento\Framework\Mview\Config\Data](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Mview/Config/Data.php) |
| `payment.xml` | Configurazione del modulo di pagamento | primario, globale | [\Magento\Payment\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Payment/Model/Config.php) |
| `persistent.xml` | [Magento_Persistente](https://developer.adobe.com/commerce/php/module-reference/module-persistent/) file di configurazione | globale | [\Magento\Persistent\Helper\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Persistent/Helper/Data.php) |
| `pdf.xml` | Impostazioni PDF | globale | [\Magento\Sales\Model\Order\Pdf\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Order/Pdf/Config/Reader.php) |
| `product_options.xml` | Fornisce la configurazione delle opzioni prodotto | globale | [\Magento\Catalog\Model\ProductOptions\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductOptions/Config.php) |
| `product_types.xml` | Definisce il tipo di prodotto | globale | [\Magento\Catalog\Model\ProductTypes\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Catalog/Model/ProductTypes/Config.php) |
| `queue_consumer.xml` | [Definisce la relazione tra una coda esistente e il relativo consumatore](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_consumerxml) | globale | [\Magento\Framework\MessageQueue\Consumer\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Consumer/Config/Xml/Reader.php) |
| `queue_publisher.xml` | [Definisce lo scambio in cui viene pubblicato un argomento.](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_publisherxml) | globale | [\Magento\WebapiAsync\Code\Generator\Config\RemoteServiceReader\Publisher](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Code/Generator/Config/RemoteServiceReader/Publisher.php) |
| `queue_topology.xml` | [Definisce le regole di instradamento dei messaggi, dichiara le code e gli scambi](https://developer.adobe.com/commerce/php/development/components/message-queues/configuration/#queue_topologyxml) | globale | [\Magento\Framework\MessageQueue\Topology\Config\Xml\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/MessageQueue/Topology/Config/Xml/Reader.php) |
| `reports.xml` | [Rapporti avanzati](https://devdocs.magento.com/guides/v2.4/advanced-reporting/report-xml.html) | globale | [\Magento\Analytics\ReportXml\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Analytics/ReportXml/Config.php) |
| `resources.xml` | Definisce la risorsa del modulo | globale | [\Magento\Framework\App\ResourceConnection\Config\Reader](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/ResourceConnection/Config/Reader.php) |
| `routes.xml` | [Percorso](https://developer.adobe.com/commerce/php/development/components/routing/) configurazione | area | [Magento\Framework\App\Route\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Route/Config.php) |
| `sales.xml` | Definisce la configurazione del totale delle vendite | globale | [\Magento\Sales\Model\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Sales/Model/Config/Data.php) |
| `search_engine.xml` | Fornisce la configurazione del motore di ricerca | globale | [Magento\Search\Model\SearchEngine\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Search/Model/SearchEngine/Config.php) |
| `search_request.xml` | Definisce la configurazione della ricerca nel catalogo | globale | [\Magento\Framework\Search\Request\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Search/Request/Config.php) |
| `sections.xml` | Definisce le azioni che attivano l’invalidazione della cache per i blocchi di contenuto privato | front-end | [.LettoreConfigInvalidazioneSezione](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Customer/etc/di.xml#L137-L148) |
| `system.xml` | Definisce le opzioni per la pagina di configurazione del sistema | adminhtml | [\Magento\Framework\App\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config.php) |
| `validation.xml` | File di configurazione convalida modulo | globale | [\Magento\Framework\Validator\Factory](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Validator/Factory.php) |
| `view.xml` | Definisce i valori di configurazione della vista Vendor_Module | globale | [\Magento\Framework\View\Config](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/View/Config.php) |
| `webapi.xml` | [Configura un’API web](https://developer.adobe.com/commerce/php/development/components/web-api/services/) | globale | [\Magento\Webapi\Model\Config](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Webapi/Model/Config.php) |
| `webapi_async.xml` | [Definisce i percorsi personalizzati REST](https://developer.adobe.com/commerce/php/development/components/web-api/custom-routes/) | globale | [\Magento\WebapiAsync\Model\ServiceConfig](https://github.com/magento/magento2/blob/2.4/app/code/Magento/WebapiAsync/Model/ServiceConfig.php) |
| `widget.xml` | Definisce i widget | globale | [\Magento\Widget\Model\Config\Reader](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Widget/Model/Config/Reader.php) |
| `zip_codes.xml` | Definisce il formato del codice postale per ogni paese | globale | [\Magento\Directory\Model\Country\Postcode\Config\Data](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Directory/Model/Country/Postcode/Config/Data.php) |

### Interfacce di configurazione

È possibile interagire con i file di configurazione utilizzando le interfacce in [Magento\Framework\Config](https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/Config).

Queste interfacce possono essere utilizzate [creare un tipo di configurazione](../reference/config-create-types.md#create-configuration-types).

`Magento\Framework\Config` fornisce le seguenti interfacce:

- [Framework\Config\ConverterInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ConverterInterface.php), che converte l&#39;XML in una rappresentazione in memoria delle configurazioni.
- [Framework\Config\InterfacciaDati](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/DataInterface.php), che recupera i dati di configurazione in un ambito specificato.
- [Framework\Config\FileResolverInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/FileResolverInterface.php), che identifica il percorso dei file da leggere [Magento\Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php).
- [Framework\Config\ReaderInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ReaderInterface.php), che legge i dati di configurazione dall&#39;archiviazione e seleziona l&#39;archiviazione da cui legge.

In altre parole, il file system, il database o altri archivi uniscono i file di configurazione in base alle regole di unione e convalidano i file di configurazione con gli schemi di convalida.

- [Framework\Config\SchemaLocatorInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/SchemaLocatorInterface.php), che individua lo schema XSD.
- [Framework\Config\ScopeListInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ScopeListInterface.php), che restituisce un elenco di ambiti.
- [Framework\Config\ValidationStateInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Config/ValidationStateInterface.php), che recupera lo stato di convalida.
