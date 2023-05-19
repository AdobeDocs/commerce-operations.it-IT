---
title: Personalizzare [!DNL Data Migration Tool]
description: Scopri come personalizzare [!DNL Data Migration Tool] per trasferire i dati creati dalle estensioni tra il Magento 1 e il Magento 2.
exl-id: a5c1575f-9d77-416e-91fe-a82905ef2e1c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---

# Configurare [!DNL Data Migration Tool]

A volte il formato e la struttura dei dati creati da [estensioni](https://marketplace.magento.com/extensions.html) Il codice personalizzato di o è diverso tra il Magento 1 e il Magento 2. Utilizzare i punti di estensione all’interno di [!DNL Data Migration Tool] per migrare questi dati. Se il formato e la struttura dei dati sono identici, lo strumento può eseguire automaticamente la migrazione dei dati senza l’intervento dell’utente.

Durante la migrazione, [Passaggio mappa](technical-specification.md#map-step) analizza e confronta tutte le tabelle del Magento 1 e del Magento 2, incluse quelle create dalle estensioni. Se le tabelle sono le stesse, lo strumento migra automaticamente i dati. Se le tabelle sono diverse, lo strumento termina e invia una notifica all&#39;utente.

>[!NOTE]
>
>Leggi le [Specifiche tecniche](technical-specification.md) prima di tentare di estendere [!DNL Data Migration Tool]. Inoltre, controlla [Guida alla migrazione](../overview.md) per informazioni generali sull’utilizzo dello strumento di migrazione.


## Modifiche minori al formato e alla struttura dei dati

Nella maggior parte dei casi, il [Passaggio mappa](technical-specification.md#map-step) risolve in modo sufficiente le modifiche minori al formato e alla struttura dei dati utilizzando i seguenti metodi nella `map.xml` file:

- Modificare i nomi di tabelle o campi con regole di mappatura
- Trasforma i formati di dati con gestori esistenti o personalizzati

Di seguito è riportato un esempio di utilizzo di regole di mappatura e di un gestore. In questo esempio viene utilizzata un&#39;ipotetica estensione del Magento 1 denominata &quot;GreatBlog&quot;, che è stata migliorata per il Magento 2.

```xml
<source>
    <document_rules>
        <ignore>
            <document>great_blog_index</document>
        </ignore>
        <rename>
            <document>great_blog_publication</document>
            <to>great_blog_post</to>
        </rename>
    </document_rules>
    <field_rules>
        <move>
            <field>great_blog_publication.summary</field>
            <to>great_blog_post.title</to>
        </move>
        <ignore>
            <field>great_blog_publication.priority</field>
        </ignore>
        <transform>
            <field>great_blog_publication.body</field>
            <handler class="\Migration\Handler\GreatBlog\NewFormat">
                <param name="switch" value="yes" />
            </handler>
        </transform>
    </field_rules>
</source>
<destination>
    <document_rules>
        <ignore>
            <document>great_blog_rating</document>
        </ignore>
    </document_rules>
    <field_rules>
        <ignore>
            <field>great_blog_post.rating</field>
        </ignore>
    </field_rules>
</destination>
```

- Non eseguire la migrazione di dati non necessari da `great_blog_index` tabella indice.
- Tabella `great_blog_publication` è stato rinominato in `great_blog_post` nel Magento 2, quindi i dati vengono migrati alla nuova tabella.
   - Il `summary` il campo è stato rinominato in `title`, quindi i dati vengono migrati al nuovo campo.
   - Il `priority` è stato rimosso e non esiste più nel Magento 2.
   - I dati in `body` il campo ha cambiato formato e deve essere elaborato dal gestore personalizzato: `\Migration\Handler\GreatBlog\NewFormat`.
- Una nuova funzione di valutazione è stata sviluppata per l&#39;estensione &quot;GreatBlog&quot; nel Magento 2.
   - Una nuova `great_blog_rating` tabella creata.
   - Una nuova `great_blog_post.rating` è stato creato.

### Estendere la mappatura in altri passaggi

Altri passaggi supportano la mappatura, ad esempio [Passaggio EAV](technical-specification.md#eav-step) e il passaggio Attributi del cliente. Questi passaggi eseguono la migrazione di un elenco predefinito di tabelle di Magento. Ad esempio, supponiamo che l&#39;estensione &quot;GreatBlog&quot; abbia un campo aggiuntivo nel `eav_attribute` e il nome è stato modificato nel Magento 2. Poiché la tabella viene elaborata da [Passaggio EAV](technical-specification.md#eav-step), le regole di mappatura devono essere scritte per `map-eav.xml` file. Il `map.xml` e `map-eav.xml` i file utilizzano lo stesso `map.xsd` dello schema, in modo che le regole di mappatura rimangano le stesse.

## Modifiche principali al formato e alla struttura dei dati

Oltre al Passaggio mappa, in sono disponibili altri passaggi `config.xml` file per la migrazione dei dati con modifiche principali di formato e struttura, tra cui:

- [Passaggio Riscrittura Url](technical-specification.md#url-rewrite-step)
- Passaggio OrderGrids
- [Passaggio EAV](technical-specification.md#eav-step)

A differenza della [Passaggio mappa](technical-specification.md#map-step), questi passaggi eseguono la scansione di un elenco predefinito di tabelle anziché di tutte le tabelle.

Per modifiche principali al formato e alla struttura dei dati, crea un passaggio personalizzato.

### Creare un passaggio personalizzato

Utilizzando lo stesso esempio di &quot;GreatBlog&quot;, supponiamo che l’estensione abbia una tabella nel Magento 1, ma sia stata riprogettata per avere due tabelle nel Magento 2.

Nel Magento 1, c&#39;era un solo `greatblog_post` tabella:

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
| tags      | TEXT     |
```

Nel Magento 2, una nuova tabella per i tag `greatblog_post_tags` è stato introdotto:

```text
| Field      | Type     |
|------------|----------|
| post_id    | INT      |
| tag        | VARCHAR  |
| sort_order | SMALLINT |
```

MAGENTO 2 `greatblog_post` la tabella ora si presenta così:

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
```

Per migrare tutti i dati dalla vecchia struttura delle tabelle a una nuova, puoi creare un passaggio personalizzato in `config.xml` file. Ad esempio:

```xml
<steps mode="data">
    ...
    <step title="GreatBlog Step">
        <integrity>Vendor\Migration\Step\GreatBlog\Integrity</integrity>
        <data>Vendor\Migration\Step\GreatBlog\Data</data>
        <volume>Vendor\Migration\Step\GreatBlog\Volume</volume>
    </step>
</steps>
<steps mode="delta">
    ...
    <step title="GreatBlog Step">
        <delta>Vendor\Migration\Step\GreatBlog\Delta</delta>
        <volume>Vendor\Migration\Step\GreatBlog\Volume</volume>
    </step>
</steps>
```

Lo strumento esegue i passi in base alla loro posizione all&#39;interno della `config.xml` dall&#39;alto verso il basso. Nel nostro esempio, il `GreatBlog Step` viene eseguito per ultimo.

I passaggi possono includere quattro tipi di classi:

- Controllo dell’integrità
- Distribuzione dei dati
- Controllo volume
- Consegna delta

>[!NOTE]
>
>Fai riferimento a [Configurazione](technical-specification.md#configuration), [Interni del passaggio](technical-specification.md#step-internals), [Fasi](technical-specification.md#step-stages), e [Modalità di esecuzione](technical-specification.md#running-modes) per ulteriori informazioni.


In queste classi è possibile assemblare query SQL complesse per recuperare e migrare i dati. Inoltre, queste tabelle devono essere &quot;ignorate&quot; nella sezione [Passaggio mappa](technical-specification.md#map-step) perché analizza tutte le tabelle esistenti e tenta di migrare i dati a meno che non si trovino nel `<ignore>` tag di `map.xml` file.

Per il controllo dell&#39;integrità, definisci un file di mappa aggiuntivo in `config.xml` per verificare che la struttura delle tabelle sia quella prevista.

```xml
<config xmlns:xs="http://www.w3.org/2001/XMLSchema-instance"
        xs:noNamespaceSchemaLocation="urn:magento:module:Magento_DataMigrationTool:etc/config.xsd">
    ...
    <options>
        ...
        <greatblog_map_file>app/code/Vendor/Migration/etc/opensource-to-opensource/map-greatblog.xml</greatblog_map_file>
        ...
    </options>
</config>
```

File mappa `map-greatblog.xml`:

```xml
<map xmlns:xs="http://www.w3.org/2001/XMLSchema-instance"
     xs:noNamespaceSchemaLocation="urn:magento:module:Magento_DataMigrationTool:etc/map.xsd">
    <source>
        <field_rules>
            <ignore>
                <field>greatblog_post.tags</field>
            </ignore>
        </field_rules>
    </source>
    <destination>
        <document_rules>
            <ignore>
                <document>greatblog_post_tags</document>
            </ignore>
        </document_rules>
    </destination>
</map>
```

Classe di controllo dell&#39;integrità `Vendor\Migration\Step\GreatBlog\Integrity` si estende `Migration\App\Step\AbstractIntegrity` e contiene `perform` metodo di verifica della struttura della tabella:

```php
class Integrity extends \Migration\App\Step\AbstractIntegrity
{
    ...
    /**
     * Integrity constructor.
     * @param ProgressBar\LogLevelProcessor $progress
     * @param Logger $logger
     * @param Config $config
     * @param ResourceModel\Source $source
     * @param ResourceModel\Destination $destination
     * @param MapFactory $mapFactory
     * @param string $mapConfigOption
     */
    public function __construct(
        ProgressBar\LogLevelProcessor $progress,
        Logger $logger,
        Config $config,
        ResourceModel\Source $source,
        ResourceModel\Destination $destination,
        MapFactory $mapFactory,
        $mapConfigOption = 'greatblog_map_file'
    ) {
        parent::__construct($progress, $logger, $config, $source, $destination, $mapFactory, $mapConfigOption);
    }

    /**
     * @inheritDoc
     */
    public function perform()
    {
        $this->progress->start($this->getIterationsCount());
        $this->check(['greatblog_post'], MapInterface::TYPE_SOURCE);
        $this->check(['greatblog_post', 'greatblog_post_tags'], MapInterface::TYPE_DEST);
        $this->progress->finish();
        return $this->checkForErrors();
    }
    ...
}
```

Successivamente, è necessario creare una classe per l&#39;elaborazione e il salvataggio dei dati nel database del Magento 2 `Vendor\Migration\Step\GreatBlog\Data`:

```php
class Data implements \Migration\App\Step\StageInterface
{
    ...
    /**
     * Data constructor.
     *
     * @param ProgressBar\LogLevelProcessor $progress
     * @param ResourceModel\Source $source
     * @param ResourceModel\Destination $destination
     * @param ResourceModel\RecordFactory $recordFactory
     * @param RecordTransformerFactory $recordTransformerFactory
     * @param MapFactory $mapFactory
     */
    public function __construct(
        ProgressBar\LogLevelProcessor $progress,
        ResourceModel\Source $source,
        ResourceModel\Destination $destination,
        ResourceModel\RecordFactory $recordFactory,
        RecordTransformerFactory $recordTransformerFactory,
        MapFactory $mapFactory
    ) {
        $this->progress = $progress;
        $this->destination = $destination;
        $this->recordFactory = $recordFactory;
        $this->source = $source;
        $this->recordTransformerFactory = $recordTransformerFactory;
        $this->map = $mapFactory->create('greatblog_map_file');
    }

    /**
     * @inheritDoc
     */
    public function perform()
    {
        $sourceDocName = 'greatblog_post';
        $sourceDocument = $this->source->getDocument($sourceDocName);
        $destinationDocName = 'greatblog_post';
        $destinationDocument = $this->destination->getDocument($destinationDocName);
        /** @var \Migration\RecordTransformer $recordTransformer */
        $recordTransformer = $this->recordTransformerFactory->create(
            [
                'sourceDocument' => $sourceDocument,
                'destDocument'   => $destinationDocument,
                'mapReader'      => $this->map
            ]
        );
        $recordTransformer->init();

        $this->progress->start($this->source->getRecordsCount($sourceDocName));
        $pageNumber = 0;
        while (!empty($items = $this->source->getRecords($sourceDocName, $pageNumber))) {
            $pageNumber++;
            $recordsToSave = $destinationDocument->getRecords();
            foreach ($items as $item) {
                $sourceRecord = $this->recordFactory->create(
                    ['document' => $sourceDocument, 'data' => $item]
                );
                $destinationRecord = $this->recordFactory->create(['document' => $destinationDocument]);
                $recordTransformer->transform($sourceRecord, $destinationRecord);
                $recordsToSave->addRecord($destinationRecord);
            }
            $this->destination->saveRecords($destinationDocName, $recordsToSave);

            $tags = $this->getTags($items);
            $this->destination->saveRecords('greatblog_post_tags', $tags);
            $this->progress->advance();
        }

        $this->progress->finish();
        return true;
    }
    ...
}
```

In una classe Volume `Vendor\Migration\Step\GreatBlog\Volume`, verifichiamo che i dati siano stati completamente migrati:

```php
class Volume extends \Migration\App\Step\AbstractVolume
{
    ...
    /**
     * @inheritdoc
     */
    public function perform()
    {
        $documentName = 'greatblog_post';
        $sourceCount = $this->source->getRecordsCount($documentName);
        $destinationCount = $this->destination->getRecordsCount($documentName);
        if ($sourceCount != $destinationCount) {
            $this->errors[] = sprintf(
                'Mismatch of entities in the document: %s Source: %s Destination: %s',
                $documentName,
                $sourceCount,
                $destinationCount
            );
        }

        return $this->checkForErrors(Logger::ERROR);
    }
    ...
}
```

Per aggiungere la funzionalità di migrazione delta, aggiungi un nuovo gruppo al `deltalog.xml` file. In entrata `group`, specificare il nome delle tabelle da controllare per le modifiche:

```xml
<groups>
    ...
    <group name="delta_greatblog">
        <document key="post_id">greatblog_post</document>
    </group>
</groups>
```

Quindi, crea il `Delta` classe `Vendor\Migration\Step\GreatBlog\Delta` che si estende `Migration\App\Step\AbstractDelta`:

```php
class Delta extends \Migration\App\Step\AbstractDelta
{
    /**
     * @var string
     */
    protected $mapConfigOption = 'greatblog_map_file';

    /**
     * @var string
     */
    protected $groupName = 'delta_greatblog';

    /**
     * @inheritDoc
     */
    public function perform()
    {
        $sourceDocumentName = 'greatblog_post';
        $idKeys = ['post_id'];
        $page = 0;
        while (!empty($items = $this->source->getChangedRecords($sourceDocumentName, $idKeys, $page++))) {
            $this->destination->deleteRecords(
                'greatblog_post_tags',
                $idKeys,
                $items
            );

            $tags = $this->getTags($items);
            $this->destination->saveRecords('greatblog_post_tags', $tags);
        }

        //parent class takes care of greatblog_post records automatically
        return parent::perform();
    }
}
```

Dopo l’implementazione del passaggio personalizzato fornito negli esempi, il sistema prende i dati dalla tabella del singolo Magento 1 ed elaborarli utilizzando `Vendor\Migration\Step\GreatBlog\Data` e memorizzare i dati in due tabelle del Magento 2. I record nuovi e modificati vengono consegnati durante la migrazione delta utilizzando `Vendor\Migration\Step\GreatBlog\Delta` classe.

## Metodi di estensione proibiti

Poiché il [!DNL Data Migration Tool] Il Magento 2 è in continua evoluzione e le fasi e i gestori esistenti sono soggetti a modifiche. Si consiglia vivamente di non ignorare il comportamento di passaggi come [Passaggio mappa](technical-specification.md#map-step), [Passaggio di riscrittura URL](technical-specification.md#url-rewrite-step), e i gestori estendendo le relative classi.

Alcuni passaggi non supportano la mappatura e non possono essere modificati senza modificare il codice. È possibile scrivere un ulteriore passaggio che modifichi i dati al termine della migrazione oppure creare un [Problema GitHub](https://github.com/magento/data-migration-tool/issues) e chiedere un nuovo punto di estensione sul passaggio esistente.
