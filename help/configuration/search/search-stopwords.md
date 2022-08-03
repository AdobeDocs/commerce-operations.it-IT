---
title: Configurare le parole chiave di ricerca
description: Scopri come gestire le parole chiave per Adobe Commerce utilizzando i file CSV.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 0%

---


# Configurare le parole chiave di ricerca

In generale, _cronaca_ sono parole comuni che i motori di ricerca escludono dopo l’elaborazione del testo. In origine, quando lo spazio su disco e la memoria erano estremamente limitati, ogni kilobyte salvato significava un significativo miglioramento delle prestazioni. Pertanto, i motori di ricerca hanno ottenuto dei vantaggi in termini di prestazioni ignorando determinate parole e mantenendo l&#39;indice ridotto.

Anche se oggi disponiamo di più storage, le prestazioni sono ancora importanti. Elasticsearch e OpenSearch, come altri motori di ricerca, utilizzano ancora le parole chiave per migliorare le prestazioni.

Devi gestire le parole rapide utilizzando i file CSV che si trovano in `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` o `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/` a seconda di come è stato installato il software Commerce.

Per ulteriori informazioni sull&#39;utilizzo delle parole chiave da parte di Elasticsearch e OpenSearch, consulta le risorse seguenti:

- [Parole di arresto: Prestazioni e precisione](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords.html)
- [Pro e Cons di Stopwords](https://www.elastic.co/guide/en/elasticsearch/guide/current/pros-cons-stopwords.html)
- [Utilizzo delle parole](https://www.elastic.co/guide/en/elasticsearch/guide/current/using-stopwords.html)
- [Stopwords e prestazioni](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords-performance.html)

## Configurare le parole chiave

Le parole di arresto si trovano nella `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` directory. Adobe Commerce e Magenti Open Source vengono forniti con un file CSV contenente parole di stop per le impostazioni internazionali predefinite e un file aggiuntivo, `stopwords.csv`, che ha le parole chiave per tutte le impostazioni internazionali che non sono rappresentate da un altro file CSV.

Durata predefinita del file di parole non arrivate a termine [cache](https://glossary.magento.com/cache) è di 15 minuti.

### Modificare le parole rapide per un&#39;impostazione internazionale esistente

**Per modificare le parole rapide**:

1. Accedi al server Commerce o passa a [proprietario del file system](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Utilizza un editor di testo per aprire un file di interruzione nel `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` directory.

   I file CSV utilizzano la convenzione di denominazione `stopwords_<locale_code>.csv`. Ad esempio, il nome del file stopword tedesco `stopwords_de_DE.csv`.

1. Aggiungere parole, rimuovere parole o modificare parole nel file.

   (Ogni interruzione in un file inizia su una nuova riga.)

1. Salva le modifiche e esci dall’editor di testo.
1. Pulisci la cache di configurazione.

   - Amministratore: **Sistema** > Strumenti > **Gestione cache**. Seleziona la **Configurazione** e, dall&#39;elenco sopra di esso, fai clic su **Aggiorna**. Fai clic su **Invia** per completare l’azione.

   - Riga di comando: Come proprietario del file system, immettere il comando seguente:

      ```bash
      php <magento_root>/bin/magento cache:clean config
      ```

1. Controlla i risultati cercando i termini sul tuo [vetrina](https://glossary.magento.com/storefront).

### Crea parole rapide per una nuova impostazione internazionale

**Per aggiungere parole rapide a un&#39;impostazione internazionale**:

1. Accedi al server Commerce o passa a [proprietario del file system](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).

1. Utilizzare un editor di testo per creare un file di interruzione denominato `stopwords_<locale_code>.csv` in `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` directory.

   Ad esempio, per creare parole chiave per le impostazioni internazionali italiane, denominare il file `stopwords_it_IT.csv`.

1. Nel file di cronometro, assicurarsi che ogni parola di arresto si trovi su una riga separata.
1. Salva le modifiche e esci dall’editor di testo.
1. Nella stessa directory, apri `esconfig.xml` in un editor di testo.
1. Aggiungi una riga a `esconfig.xml` come segue:

   ```xml
   <LOCALE_CODE>stopwords_LOCALE_CODE.csv</LOCALE_CODE>
   ```

   Ad esempio, per aggiungere un file di stop italiano, aggiungi la seguente riga:

   ```xml
   <it_IT>stopwords_it_IT.csv</it_IT>
   ```

1. Salva le modifiche apportate a `esconfig.xml` e esci dall’editor di testo.
1. Pulisci la cache di configurazione.

   - Amministratore: **Sistema** > Strumenti > **Gestione cache**. Seleziona la **Configurazione** e, dall&#39;elenco sopra di esso, fai clic su **Aggiorna**. Fai clic su **Invia** per completare l’azione.

   - Riga di comando: Come proprietario del file system, immettere il comando seguente:

      ```bash
      php <magento_root>/bin/magento magento cache:clean config
      ```

1. Controlla i risultati cercando i termini sulla vetrina.

## Modificare la directory di interruzione

In questa sezione viene illustrato come modificare facoltativamente la directory di parole di arresto predefinita da una delle seguenti opzioni:

- `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`
- `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`

Il percorso dipende dalla modalità di installazione del software Commerce. Se hai clonato l’archivio GitHub Magento 2, il percorso si trova in `app/code`. Se hai installato un archivio compresso o un metapackage, il percorso si trova in `vendor`.

**Per modificare la directory**:

1. Come proprietario del file system, apri l&#39;Elasticsearch `di.xml` in un editor di testo.

   Se hai clonato l’archivio, si trova in `app/code/Magento/Elasticsearch/etc/di.xml`

   Se hai un archivio o il metapackage, si trova in `vendor/magento/module-elasticsearch/etc/di.xml`

1. Modifica il valore di `stopwordsDirectory` nella directory desiderata:

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
           <argument name="stopwordsDirectory" xsi:type="string">app/code/Magento/Elasticsearch/etc/stopwords</argument>
       </arguments>
   </type>
   ```

1. Salva le modifiche in `di.xml` e esci dall’editor di testo.

## Per modificare la directory dal modulo

1. [Creare un modulo](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/module-file-structure.html)
1. Nel modulo `etc/di.xml` aggiungi le istruzioni:

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
          <argument name="stopwordsModule" xsi:type="string">Your_Module</argument>
          <argument name="stopwordsDirectory" xsi:type="string">stopwords</argument>
       </arguments>
   </type>
   ```

1. Nel modulo , crea la directory `etc/stopwords`, con il file CSV corrispondente.

1. Salva le modifiche in `di.xml` e esci dall’editor di testo.
