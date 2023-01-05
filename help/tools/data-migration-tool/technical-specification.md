---
title: "[!DNL Data Migration Tool] specifica tecnica"
description: "Scopri i dettagli di implementazione del [!DNL Data Migration Tool] e come estendere il trasferimento dei dati tra il Magento 1 e il Magento 2."
source-git-commit: c56cc6d97f69770aa718333c02514ab3cfce774c
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# [!DNL Data Migration Tool] specifica tecnica

Questa sezione descrive [!DNL Data Migration Tool] dettagli di implementazione e modalità di estensione delle sue funzionalità.

## Repository

Per accedere al [!DNL Data Migration Tool] codice sorgente, vedi GitHub [archivio](https://github.com/magento/data-migration-tool).

## Requisiti di sistema

La [requisiti di sistema](../../installation/system-requirements.md) per [!DNL Data Migration Tool] sono le stesse del Magento 2.

## Struttura interna

### Struttura directory

Il diagramma seguente rappresenta la struttura di directory di [!DNL Data Migration Tool]:

```terminal
├── etc                                    --- all configuration files
│   ├── opensource-to-opensource            --- configuration files for migration from Magento Open Source 1 to Magento Open Source 2
│   │   ├── 1.9.1.1
│   │   │   ├── config.xml.dist
│   │   │   └── map.xml.dist
│   │   ├── 1.9.2.0
│   │   │   ├── config.xml.dist
│   │   │   └── map.xml.dist
│   │   ├── ........
│   │   ├── class-map.xml.dist
│   │   ├── deltalog.xml.dist
│   │   └── settings.xml.dist
│   │   ├── ........
│   ├── opensource-to-commerce              --- configuration files for migration from Magento Open Source 1 to Adobe Commerce 2
│   ├── commerce-to-commerce                --- configuration files for migration from Adobe Commerce 1 to Adobe Commerce 2
│   ├── class-map.xsd
│   ├── config.xsd
│   ├── map.xsd
│   └── settings.xsd
├── src
│   └── Migration
│       ├── App                             --- application framework
│       ├── Console
│       ├── Handler                         --- handlers are used by map files
│       │   ├── AbstractHandler.php
│       │   ├── AddPrefix.php
│       │   ├── ConvertIp.php
│       │   ├── ........
│       ├── Logger
│       ├── Reader
│       ├── Mode
│       │   ├── AbstractMode.php
│       │   ├── Data.php
│       │   ├── Delta.php
│       │   └── Settings.php
│       ├── ResourceModel                   --- contains [adapter](https://glossary.magento.com/adapter) for connection to data storage and classes to work with structured data
│       │   ├── Adapter
│       │   │   └── Mysql.php
│       │   ├── AbstractCollection.php
│       │   ├── AbstractResource.php
│       │   ├── AdapterInterface.php
│       │   ├── Destination.php
│       │   ├── Document.php
│       │   ├── Record.php
│       │   ├── Source.php
│       │   └── Structure.php
│       ├── Config.php
│       ├── [Exception](https://glossary.magento.com/exception).php
│       └── Step                            --- functionality for migrating specific data
│           ├── Eav
│           │   ├── Data.php
│           │   ├── Helper.php
│           │   ├── InitialData.php
│           │   ├── Integrity.php
│           │   └── Volume.php
│           ├── Map
│           │   ├── Data.php
│           │   ├── Delta.php
│           │   ├── Helper.php
│           │   ├── Integrity.php
│           │   └── Volume.php
│           ├── UrlRewrite
│           │   ├── Version11300to2000.php
│           │   ├── Version11410to2000.php
│           │   └── Version191to2000.php
│           ├── ..........
└── tests
    ├── integration
    ├── static
    └── unit
```

## Punto di ingresso

Lo script che esegue il processo di migrazione si trova in: `magento-root/bin/magento`.

## Configurazione

Lo schema per la configurazione `config.xsd` si trova nel `etc/` directory. Il file di configurazione predefinito (`config.xml.dist`) viene creata per ogni versione di Magento 1.x. Si trova in una directory separata sotto `etc/`.

Il file di configurazione predefinito può essere sostituito da uno personalizzato (vedi [sintassi del comando](migrate-data/overview.md#command-syntax)).

Il file di configurazione ha la seguente struttura:

```xml
<config xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="config.xsd">
    <steps mode="settings">
        <step title="Settings step">
            <integrity>Migration\Step\Settings</integrity>
            <data>Migration\Step\Settings</data>
        </step>
    </steps>
    <steps mode="data">
        <step title="Map step">
            <integrity>Migration\Step\Map\Integrity</integrity>
            <data>Migration\Step\Map\Data</data>
            <volume>Migration\Step\Map\Volume</volume>
        </step>
        ...
    </steps>
    <steps mode="delta">
        <step title="Map step">
            <delta>Migration\Step\Map\Delta</delta>
            <volume>Migration\Step\Map\Volume</volume>
        </step>
        ...
    </steps>
    <source>
        <database host="localhost" name="magento1" user="root" password=""/>
    </source>
    <destination>
        <database host="localhost" name="magento2" user="root" password=""/>
    </destination>
    <options>
        <map_file>map-file.xml</map_file>
        <settings_map_file>settings-map-file.xml</settings_map_file>
        <bulk_size>100</bulk_size>
        <custom_option>custom_option_value</custom_option>
        <source_prefix />
        <dest_prefix />
        ...
    </options>
</config>
```

* passaggi : descrive tutti i passaggi elaborati durante la migrazione

* source : configurazione per l’origine dati. Tipi di origine disponibili: database

* destinazione : configurazione per la destinazione dei dati. Tipi di destinazione disponibili: database

* options - elenco di parametri. Contiene i parametri obbligatori (file_mappa, file_mappa_impostazioni, dimensione_bulk) e facoltativi (opzione_personalizzata, nome_classe_adattatore_risorsa, prefisso_sorgente, prefisso_dest, file_registro)

Opzione Cambia prefisso nel caso in cui il Magento sia stato installato con prefisso nelle tabelle del database. Può essere impostato per le banche dati di Magento 1 e Magento 2. Utilizzare di conseguenza le opzioni di configurazione &quot;source_prefix&quot; e &quot;dest_prefix&quot;.

I dati di configurazione sono accessibili con `\Migration\Config` classe.

## Passaggi disponibili

| Documento | Campo |
|---|---|
| `step` | Nodo di secondo livello all&#39;interno del nodo Passaggi. La descrizione della fase pertinente deve essere specificata nella `title` attributo. |
| `integrity` | Specifica la classe PHP responsabile del controllo dell&#39;integrità. Confronta i nomi dei campi, i tipi e altre informazioni della tabella per verificare la compatibilità tra le strutture di dati dei Magenti 1 e 2. |
| `data` | Specifica la classe PHP responsabile del controllo dei dati. Trasferisce i dati, tabella per tabella, dal Magento 1 al Magento 2. |
| `volume` | Specifica la classe PHP responsabile del controllo del volume. Confronta il numero di record tra tabelle per verificare che il trasferimento sia stato eseguito correttamente. |
| `delta` | Specifica la classe PHP responsabile del controllo delta. Trasferisce il delta dal Magento 1 al Magento 2 dopo la migrazione completa dei dati. |

## Attributi delle informazioni del database di origine

| Documento | Campo | Obbligatorio |
|---|---|---|
| `name` | Nome del database del server di Magento 1. | sì |
| `host` | Indirizzo IP host del server Magento 1. | sì |
| `port` | Numero di porta del server Magento 1. | no |
| `user` | Nome utente del database server di Magento 1. | sì |
| `password` | Password del database server di Magento 1. | sì |
| `ssl_ca` | Percorso del file dell’autorità di certificazione SSL. | no |
| `ssl_cert` | Percorso del file di certificato SSL. | no |
| `ssl_key` | Percorso del file della chiave SSL. | no |

## Attributi delle informazioni del database di destinazione

| Documento | Campo | Obbligatorio |
|---|---|---|
| `name` | Nome del database del server di Magento 2. | sì |
| `host` | Indirizzo IP host del server Magento 2. | sì |
| `port` | Numero di porta del server Magento 2. | no |
| `user` | Nome utente del database server di Magento 2. | sì |
| `password` | Password del database server di Magento 2. | sì |
| `ssl_ca` | Percorso del file dell’autorità di certificazione SSL. | no |
| `ssl_cert` | Percorso del file di certificato SSL. | no |
| `ssl_key` | Percorso del file della chiave SSL. | no |

## Connessione tramite il protocollo TLS

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

## Passaggio interno

Il processo di migrazione consiste di passaggi.

Step è un’unità che fornisce funzionalità necessarie per la migrazione di alcuni dati separati. Il passaggio può essere costituito da una o più fasi (controllo dell’integrità, dati, controllo del volume e delta).

Per impostazione predefinita, sono disponibili diversi passaggi ([Mappa](#map-step), [EAV](#eav), [Riscrittura URL](#url-rewrite-step)e così via). Facoltativamente puoi aggiungere anche i tuoi passaggi.

Le classi relative ai passaggi si trovano nella directory src/Migration/Step .

Per eseguire una classe Step, la classe deve essere definita nel file config.xml.

```xml
<config xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="config.xsd">
    <steps mode="mode_name">
        <step title="Step Name">
            <integrity>Migration\Step\StepName\Integrity</integrity>  <!-- integrity check stage of the step -->
            <data>Migration\Step\StepName\Data</data>
            <volume>Migration\Step\StepName\Volume</volume>
        </step>
        ...
    </steps>
    ...
</config>
```

Ogni classe di stage deve implementare StageInterface.

```php
class StageClass implements StageInterface
{
  /**
   * Perform the stage
   *
   * @return bool
   */
  public function perform()
  {
  }
}
```

Se lo stadio dati supporta il rollback, deve implementare il `RollbackInterface` interfaccia.

La visualizzazione del passaggio in esecuzione è fornita dal componente ProgressBar di Symfony (vedi [Barra di avanzamento](https://symfony.com/doc/current/components/console/helpers/progressbar.html)). Accedi a questo componente in un passaggio come LogLevelProcessor.

I principali metodi di utilizzo sono:

```xml
$this->progress->start();
$this->progress->advance();
$this->progress->finish();
```

## Fasi

### Controllo dell’integrità

Ogni passaggio deve verificare che la struttura dell’origine dati (Magento 1 per impostazione predefinita) e la struttura della destinazione dei dati (Magento 2) siano compatibili. In caso contrario, viene visualizzato un errore con entità non compatibili. Nel caso in cui i campi abbiano tipi di dati diversi (lo stesso campo ha un tipo di dati decimale nel Magento 1 e un numero intero nel Magento 2), viene visualizzato un messaggio di avviso (tranne quando è stato incluso nel file Mappa).

### Trasferimento dati

Se viene passato il controllo dell’integrità, il trasferimento dei dati è in esecuzione. Se vengono visualizzati degli errori, il rollback viene eseguito per ripristinare lo stato precedente del Magento 2. Se una classe step implementa il `RollbackInterface` quindi il metodo di rollback viene eseguito in caso di errore.

### Controllo volume

Dopo la migrazione dei dati, il controllo del volume fornisce un controllo aggiuntivo sul corretto trasferimento di tutti i dati.

### Consegna delta

La funzionalità Delta è responsabile della distribuzione del resto dei dati aggiunti dopo la migrazione principale.

## Modalità di esecuzione

Lo strumento deve essere eseguito in tre diverse modalità, in particolare in ordine:

1. impostazioni - migrazione delle impostazioni di sistema
1. dati - migrazione principale dei dati
1. delta : migrazione del resto dei dati aggiunti dopo la migrazione principale

Ogni modalità dispone di un proprio elenco di passaggi da eseguire. Vedi config.xml

### Modalità di migrazione impostazioni

La modalità di migrazione delle impostazioni di questo strumento viene utilizzata per trasferire le seguenti entità:

1. Siti web, store, viste store.
1. Configurazione dello store (principalmente Stores->Configurazione in M2 o System->Configurazione in M1)

Tutte le configurazioni dell&#39;archivio mantengono i propri dati nella tabella core_config_data nel database. Il file settings.xml contiene regole per questa tabella applicate durante il processo di migrazione. Questo file descrive le impostazioni che devono essere ignorate, rinominate o modificate. il file settings.xml ha la seguente struttura:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<settings xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="settings.xsd">
    <key>
        <ignore>
            <path>path/to/ignore*</path>
        </ignore>
        <rename>
            <path>path/to/rename</path>
            <to>new/path/renamed</to>
        </rename>
    <key>
    <value>
        <transform>
            <path>some/key/to/change</path>
            <handler class="Some\Handler\Class"/>
        </transform>
    </value>
</settings>
```

Sotto il nodo `<key>` esistono regole che funzionano con la colonna &quot;path&quot; nel `core_config_data` tabella. `<ignore>` le regole impediscono allo strumento di trasferire alcune impostazioni. I caratteri jolly possono essere utilizzati in questo nodo. Tutte le altre impostazioni non elencate nel `<ignore>` vengono migrati i nodi. Se il percorso di un&#39;impostazione viene modificato nel Magento 2, è necessario aggiungerlo a `//key/rename` nodo, dove il vecchio percorso indica in `//key/rename/path` nodo e nuovo percorso indica in `//key/rename/to` nodo.

Sotto il nodo `<value>`, esistono regole che funzionano con la colonna &quot;value&quot; nel `core_config_data` tabella. Queste regole mirano a trasformare il valore delle impostazioni da parte dei gestori (classi che implementano `Migration\Handler\HandlerInterface`) e adattarla per il Magento 2.

### Modalità di migrazione dei dati

In questa modalità, la maggior parte dei dati viene migrata. Prima della migrazione dei dati, le fasi di controllo dell’integrità vengono eseguite per ogni passaggio. Se il controllo di integrità viene superato, la [!DNL Data Migration Tool] installa le tabelle del catalogo (con prefisso `m2_cl_*`) e i trigger corrispondenti al database di Magento 1 ed esegue la fase di migrazione dei dati dei passaggi. Quando la migrazione viene completata senza errori, il controllo del volume verifica la coerenza dei dati. Se esegui la migrazione dell’archivio live, può essere visualizzato un messaggio di avviso. Non preoccuparti, la migrazione delta si occupa di questi dati incrementali. I passaggi più importanti per la migrazione sono Mappa, Riscrittura URL ed EAV.

#### Passaggio mappa

La fase mappa è responsabile del trasferimento della maggior parte dei dati dal Magento 1 al Magento 2. Questo passaggio legge le istruzioni dal file map.xml (che si trova nel `etc/` ). Il file descrive le differenze tra le strutture di dati di origine (Magento 1) e destinazione (Magento 2). Nel caso in cui il Magento 1 contenga tabelle o campi appartenenti ad alcuni [estensione](https://glossary.magento.com/extension) che non esiste nel Magento 2, allora queste entità possono essere posizionate qui per ignorarle tramite il Passaggio mappa. In caso contrario, viene visualizzato un messaggio di errore.

Il file mappa ha il formato seguente:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<map xmlns:xs="http://www.w3.org/2001/XMLSchema-instance" xs:noNamespaceSchemaLocation="map.xsd">
    <source>
        <document_rules>
            <ignore>
                <document>some_document2</document>
            </ignore>
            <rename>
                <document>some_document</document>
                <to>some_dest_document</to>
            </rename>
            <log_changes>
                <document key="primary_key">some_dest_document</document>
            </log_changes>
        </document_rules>

        <field_rules>
            <move>
                <field>some_document1.field1</field>
                <to>some_document1.field2</to>
            </move>
            <ignore>
                <field>some_document3.field8</field>
            </ignore>
            <transform>
                <field>some_document1.field1</field>
                <handler class="\Migration\Handler\Convert">
                    <param name="map" value="[value1:value2;value3:value4;value5:value6;]" />
                </handler>
            </transform>
        </field_rules>
    </source>
    <destination>
        <document_rules>
            <ignore>
                <document>some_document8</document>
            </ignore>
        </document_rules>

        <field_rules>
            <transform>
                <field>some_document5.field3</field>
                <handler class="\Migration\Handler\SetValue">
                    <param name="value" value="10" />
                </handler>
            </transform>
        </field_rules>
    </destination>
</map>
```

Zone:

* *source* - contiene regole del database di origine

* *destinazione* - contiene regole del database di destinazione

Opzioni:

* *ignore* - documento, campo o tipo di dati contrassegnati con questa opzione viene ignorato

* *rinomina* - descrive le relazioni dei nomi tra documenti con un nome diverso. In un caso in cui il nome del documento di destinazione non è lo stesso del documento di origine, è possibile utilizzare l&#39;opzione Rinomina per impostare il nome del documento di origine in modo simile al nome della tabella di destinazione

* *spostare* - imposta la regola per spostare il campo specificato dal documento di origine al documento di destinazione. NOTA: il nome del documento di destinazione deve essere lo stesso con il nome del documento di origine. Se i nomi dei documenti di origine e di destinazione sono diversi, è necessario utilizzare l&#39;opzione Rinomina per il documento che contiene campi spostati

* *trasformare* - è un’opzione che consente all’utente di eseguire la migrazione dei campi in base al comportamento descritto nei gestori

* *handler* - descrive il comportamento di trasformazione per i campi. Per chiamare il gestore, è necessario specificare un nome di classe del gestore in un `<handler>` tag . Utilizza la `<param>` tag con il nome del parametro e i dati del valore per passarlo al gestore

**Origine** operazioni disponibili:

| Documento | Campo |
|--- |--- |
| ignora rinomina | ignora trasformazione spostamento |

**Destinazione** operazioni disponibili:

| Documento | Campo |
|--- |--- |
| ignore | Ignora trasformazione |

#### Caratteri jolly

Per ignorare i documenti con parti simili (`document_name_1`, `document_name_2`), puoi utilizzare la funzionalità jolly . Put `*` simbolo invece della parte ripetuta (`document_name_*`) e questa maschera copre tutti i documenti di origine o di destinazione che soddisfano questa maschera.

#### Passaggio di riscrittura URL

Questo passaggio è complesso perché ci sono molti algoritmi diversi sviluppati nel Magento 1 che non sono compatibili con il Magento 2. Per le diverse versioni del Magento 1, possono esserci diversi algoritmi. Quindi nella cartella Step/UrlRewrite ci sono classi sviluppate per alcune versioni particolari di Magento e Migration\Step\UrlRewrite\Version191to2000 is one of them. Può trasferire i dati di riscrittura URL dal Magento 1.9.1 al Magento 2.

#### Passaggio EAV

Questo passaggio trasferisce tutti gli attributi (prodotto, cliente, RMA) dal Magento 1 al Magento 2. Utilizza il file map-eav.xml che contiene regole simili a quelle presenti nel file map.xml per casi specifici di elaborazione dei dati.

Alcune delle tabelle elaborate nel passaggio :

* `eav_attribute`
* `eav_attribute_group`
* `eav_attribute_set`
* `eav_entity_attribute`
* `catalog_eav_attribute`
* `customer_eav_attribute`
* `eav_entity_type`

### Modalità di migrazione delta

Dopo la migrazione principale, potrebbero essere stati aggiunti dati aggiuntivi al database di Magento 1 (ad esempio, da parte dei clienti su storefront). Per tenere traccia di questi dati, lo strumento imposta i trigger del database per le tabelle all&#39;inizio del processo di migrazione. Per ulteriori informazioni, consulta [Eseguire la migrazione dei dati creati da estensioni di terze parti](migrate-data/delta.md#migrate-data-created-by-third-party-extensions).

## Origini dati

Per raggiungere le origini dati di Magento 1 e Magento 2 e utilizzare i relativi dati (selezionare, aggiornare, inserire, eliminare) sono presenti molte classi nella cartella Resource. Migration\ResourceModel\Source e Migration\ResourceModel\Destination sono le classi principali. Tutti i passaggi di migrazione lo utilizzano per funzionare con i dati. Questi dati sono contenuti in classi come Migration\ResourceModel\Document, Migration\ResourceModel\Record, Migration\ResourceModel\Structure, ecc.

Ecco un diagramma di classe di queste classi:

![Struttura dei dati degli strumenti di migrazione](../../assets/data-migration/MmigrationToolDataStructure.png)

## Registrazione

Per implementare l&#39;output del processo di migrazione e controllare tutti i livelli possibili PSR logger, che viene utilizzato nel Magento, viene applicato. `\Migration\Logger\Logger` è stata implementata per fornire funzionalità di registrazione. Per utilizzare il logger, è necessario inserirlo tramite costruttore [iniezione di dipendenza](https://glossary.magento.com/dependency-injection).

```php
class SomeClass
{
    ...
    protected $logger;

    public function __construct(\Migration\Logger\Logger $logger)
    {
        $this->logger = $logger;
    }
    ...
}
```

In seguito, è possibile utilizzare questa classe per la registrazione di alcuni eventi:

```php
$this->logger->info("Some information message");
$this->logger->debug("Some debug message");
$this->logger->error("Message about error operation");
$this->logger->warning("Some warning message");
```

C&#39;è la possibilità di personalizzare dove le informazioni di log devono essere scritte. Puoi farlo aggiungendo handler al logger utilizzando il metodo pushHandler() del logger. Ogni handler dovrebbe implementare `\Monolog\Handler\HandlerInterface` interfaccia. Per il momento esistono due gestori:

* ConsoleHandler: scrive i messaggi nella console

* FileHandler: scrive i messaggi nel file di registro impostato nell&#39;opzione di configurazione &quot;log_file&quot;

Inoltre è possibile implementare qualsiasi gestore aggiuntivo. C&#39;è una serie di gestori nel framework di Magento. Esempio di aggiunta di gestori al logger:

```php
// $this->consoleHandler is the object of Migration\Logger\ConsoleHandler class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushHandler($this->consoleHandler);
```

Per impostare dati aggiuntivi per il logger (modalità corrente, nome tabella) è possibile utilizzare i processori logger. Esiste un processore (MessageProcessor) esistente. Viene creato per aggiungere dati &quot;extra&quot; per la registrazione dei messaggi e viene chiamato ogni volta che viene eseguito il metodo di log. MessageProcessor ha protetto $extra var, che contiene valori vuoti per &#39;mode&#39;, &#39;stage&#39;, &#39;step&#39; e &#39;table&#39;. I dati aggiuntivi possono essere trasmessi al processore come secondo parametro (contesto) per il metodo di log. Set di dati aggiuntivi al processore in AbstractStep->runStage (passare la modalità corrente, lo stadio e il passo al processore) e classi di dati in cui usato logger->metodo debug (passare il nome della tabella di migrazione). Esempio di aggiunta di processori al logger:

```php
// $this->processoris the object of Migration\Logger\messageProcessor class
// $this->logger is the object of Migration\Logger\Logger class
$this->logger->pushProcessor([$this->processor, 'setExtra']);
// As a second array value you need to pass method that should be executed when processor called
```

Esiste la possibilità di stabilire il livello di verbosità. Per il momento ci sono tre livelli:

* `ERROR` (scrive solo gli errori nel registro)
* `INFO` (solo informazioni importanti vengono scritte nel registro, valore predefinito)
* `DEBUG` (tutto è scritto)

Il livello di log della verbosità può essere impostato separatamente per ogni handler chiamando `setLevel()` metodo . Se desideri impostare il livello di verbosità tramite il parametro della riga di comando, devi modificare l&#39;opzione &#39;verbose&#39; all&#39;avvio dell&#39;applicazione.

È possibile formattare i messaggi di log con il formattatore monologo. Per far funzionare la funzionalità di formattazione, è necessario specificare il gestore di registro utilizzando `setFormatter()` metodo . Attualmente, è disponibile una classe formattatore (`MessageFormatter`) che imposta un determinato formato (dipende dal livello di verbosità) durante la gestione dei messaggi (tramite `format()` metodo eseguito dal gestore).

La manipolazione del logger (aggiunta di gestori e processori) e l&#39;elaborazione in modalità dettagliata viene eseguita in `process()` metodo `Migration\Logger\Manager` classe. Il metodo viene chiamato all&#39;avvio dell&#39;applicazione.

## Prove automatiche

Sono disponibili tre tipi di test [!DNL Data Migration Tool]:

* Statico
* Unità
* Integrazione

Si trovano nell&#39;utensile `tests/` che è lo stesso del tipo di prova (le prove di unità si trovano nella `tests/unit` ). Per avviare il test, dovresti aver installato phpunit. Cambia la directory corrente nella directory di test e avvia phpunit. Ad esempio:

```bash
[10:32 AM]-[vagrant@debian-70rc1-x64-vbox4210]-[/var/www/magento2/vendor/magento/data-migration-tool]-[git master]
$ cd tests/unit
```

```bash
[10:33 AM]-[vagrant@debian-70rc1-x64-vbox4210]-[/var/www/magento2/vendor/magento/data-migration-tool/tests/unit]-[git master]
$ phpunit
PHPUnit 8.1.0 by Sebastian Bergmann.
....
```
