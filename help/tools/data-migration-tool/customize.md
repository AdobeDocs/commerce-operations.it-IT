---
title: Personalizzare [!DNL Data Migration Tool]
description: Scopri come personalizzare il [!DNL Data Migration Tool] per trasferire i dati creati dalle estensioni tra il Magento 1 e il Magento 2.
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---


# Configura le [!DNL Data Migration Tool]

A volte il formato e la struttura dei dati creati da [estensioni](https://marketplace.magento.com/extensions.html) Il codice personalizzato o è diverso tra il Magento 1 e il Magento 2. Utilizzare i punti di estensione all&#39;interno di [!DNL Data Migration Tool] per migrare questi dati. Se il formato e la struttura dei dati sono gli stessi, lo strumento può migrare automaticamente i dati senza l&#39;intervento dell&#39;utente.

Durante la migrazione, il [Passaggio mappa](technical-specification.md#map-step) analizza e confronta tutte le tabelle dei Magenti 1 e 2, incluse quelle create dalle estensioni. Se le tabelle sono uguali, lo strumento esegue automaticamente la migrazione dei dati. Se le tabelle sono diverse, lo strumento termina e notifica l’utente.

>[!NOTE]
>
>Leggi la sezione [Specifiche tecniche](technical-specification.md) prima di tentare di estendere [!DNL Data Migration Tool]. Inoltre, rivedi il [Guida alla migrazione](../overview.md) per informazioni generali sull’utilizzo dello strumento di migrazione.


## Modifiche minori al formato dei dati e alla struttura

Nella maggior parte dei casi, il [Passaggio mappa](technical-specification.md#map-step) risolve a sufficienza le modifiche minori del formato dei dati e della struttura utilizzando i seguenti metodi nella `map.xml` file:

- Modificare i nomi di tabelle o campi con le regole di mappatura
- Trasforma i formati di dati con gestori esistenti o con un gestore personalizzato

Di seguito è riportato un esempio di utilizzo delle regole di mappatura e di un gestore. In questo esempio viene utilizzata un&#39;estensione ipotetica del Magento 1 denominata &quot;GreatBlog&quot; che è stata migliorata per il Magento 2.

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

- Non eseguire la migrazione di dati non necessari dal `great_blog_index` tabella indice.
- La tabella `great_blog_publication` è stato rinominato in `great_blog_post` nel Magento 2, quindi i dati vengono migrati alla nuova tabella.
   - La `summary` è stato rinominato in `title`, quindi i dati vengono migrati nel nuovo campo.
   - La `priority` Il campo è stato rimosso e non esiste più nel Magento 2.
   - I dati nel `body` Il campo ha cambiato formato e deve essere elaborato dal gestore personalizzato: `\Migration\Handler\GreatBlog\NewFormat`.
- Una nuova funzionalità di valutazione è stata sviluppata per l&#39;estensione &quot;GreatBlog&quot; nel Magento 2.
   - Nuovo `great_blog_rating` tabella creata.
   - Nuovo `great_blog_post.rating` campo creato.

### Estendi la mappatura in altri passaggi

Altri passaggi supportano la mappatura, ad esempio [Passaggio EAV](technical-specification.md#eav-step) e il Passaggio Attributi del cliente . Questi passaggi eseguono la migrazione di un elenco predefinito di tabelle di Magento. Ad esempio, supponiamo che l&#39;estensione &quot;GreatBlog&quot; abbia un campo aggiuntivo nel `eav_attribute` tabella e nome modificati nel Magento 2. Poiché la tabella viene elaborata dalla [Passaggio EAV](technical-specification.md#eav-step), le regole di mappatura devono essere scritte per `map-eav.xml` file. La `map.xml` e `map-eav.xml` i file utilizzano gli stessi `map.xsd` schema, pertanto le regole di mappatura rimangono le stesse.

## Modifiche principali al formato e alla struttura dei dati

Oltre al Passaggio mappa, ci sono altri passaggi nel `config.xml` file che eseguono la migrazione dei dati con modifiche rilevanti del formato e della struttura, tra cui:

- [Passaggio Di Riscrittura Url](technical-specification.md#url-rewrite-step)
- Passaggio OrderGrids
- [Passaggio EAV](technical-specification.md#eav-step)

A differenza di [Passaggio mappa](technical-specification.md#map-step), questi passaggi eseguono la scansione di un elenco predefinito di tabelle anziché di tutte le tabelle.

Per modifiche principali al formato dei dati e alla struttura, crea un passaggio personalizzato.

### Creare un passaggio personalizzato

Utilizzando lo stesso esempio &quot;GreatBlog&quot;, supponi che l&#39;estensione abbia una tabella nel Magento 1, ma sia stata riprogettata per avere due tabelle nel Magento 2.

Nel Magento 1 c&#39;era un singolo `greatblog_post` tabella:

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

Magento 2 `greatblog_post` la tabella ora si presenta così:

```text
| Field     | Type     |
|-----------|----------|
| post_id   | INT      |
| title     | VARCHAR  |
| content   | TEXT     |
| author_id | SMALLINT |
```

Per migrare tutti i dati dalla struttura delle tabelle precedenti a una nuova, è possibile creare un passaggio personalizzato nella `config.xml` file. Ad esempio:

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

Lo strumento esegue i passaggi in base alla loro posizione nel `config.xml` file; dall&#39;alto verso il basso. Nel nostro esempio, il `GreatBlog Step` corre per ultimo.

I passaggi possono includere quattro tipi di classi:

- Controllo dell’integrità
- Distribuzione dei dati
- Controllo del volume
- Distribuzione delta

>[!NOTE]
>
>Fai riferimento a [Configurazione](technical-specification.md#configuration), [Passaggio interno](technical-specification.md#step-internals), [Fasi](technical-specification.md#step-stages)e [Modalità di esecuzione](technical-specification.md#running-modes) per ulteriori informazioni.


Le query SQL complesse possono essere assemblate all&#39;interno di queste classi per recuperare e migrare i dati. Inoltre, queste tabelle devono essere &quot;ignorate&quot; nel [Passaggio mappa](technical-specification.md#map-step) perché esegue la scansione di tutte le tabelle esistenti e tenta di eseguire la migrazione dei dati a meno che non si trovi nel `<ignore>` del `map.xml` file.

Per il controllo dell’integrità, definisci un file di mappa aggiuntivo nel `config.xml` per verificare che la struttura delle tabelle sia quella prevista.

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

Classe di controllo dell’integrità `Vendor\Migration\Step\GreatBlog\Integrity` Estensioni `Migration\App\Step\AbstractIntegrity` e contiene `perform` metodo di verifica della struttura della tabella:

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

Successivamente, è necessario creare una classe per l&#39;elaborazione e il salvataggio dei dati nel database di Magento 2 `Vendor\Migration\Step\GreatBlog\Data`:

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

In una classe Volume `Vendor\Migration\Step\GreatBlog\Volume`, verifichiamo se i dati sono stati completamente migrati:

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

Per aggiungere la funzionalità di migrazione delta, aggiungi un nuovo gruppo al `deltalog.xml` file. In `group`, specifica il nome delle tabelle da controllare per le modifiche:

```xml
<groups>
    ...
    <group name="delta_greatblog">
        <document key="post_id">greatblog_post</document>
    </group>
</groups>
```

Quindi, crea la `Delta` Classe `Vendor\Migration\Step\GreatBlog\Delta` che si estende `Migration\App\Step\AbstractDelta`:

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

Dopo l’implementazione personalizzata dei passaggi fornita negli esempi, il sistema prende i dati dalla tabella a un Magento 1, li elabora utilizzando `Vendor\Migration\Step\GreatBlog\Data` e memorizzare i dati in due tabelle del Magento 2. I record nuovi e modificati vengono consegnati alla migrazione delta utilizzando `Vendor\Migration\Step\GreatBlog\Delta` classe.

## Metodi di estensione vietati

Dal momento che [!DNL Data Migration Tool] e il Magento 2 sono in costante evoluzione, i passaggi e i gestori esistenti sono soggetti a cambiamenti. Si consiglia vivamente di non ignorare il comportamento di passaggi come il [Passaggio mappa](technical-specification.md#map-step), [Passaggio di riscrittura URL](technical-specification.md#url-rewrite-step), e gestori estendendo le loro classi.

Alcuni passaggi non supportano la mappatura e non possono essere modificati senza modificare il codice. Puoi scrivere un passaggio aggiuntivo che modifica i dati alla fine della migrazione o creare un [Problema GitHub](https://github.com/magento/data-migration-tool/issues) e chiedi un nuovo punto di estensione sul passaggio esistente.
