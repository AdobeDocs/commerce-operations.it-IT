---
title: Configurare i termini di ricerca
description: Scopri come gestire le parole chiave per Adobe Commerce utilizzando i file CSV.
feature: Configuration, Search
exl-id: 75320868-9939-4a6e-8dbb-73ca68c9f0ee
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 0%

---

# Configurare i termini di ricerca

In generale, _stopwords_ sono parole comuni che i motori di ricerca filtrano dopo l&#39;elaborazione del testo. In origine, quando lo spazio su disco e la memoria erano estremamente limitati, ogni kilobyte risparmiato significava un miglioramento significativo delle prestazioni. Pertanto, i motori di ricerca hanno ottenuto miglioramenti delle prestazioni ignorando determinate parole e mantenendo piccolo l’indice.

Anche se oggi abbiamo più storage, le prestazioni sono ancora importanti. Elasticsearch e OpenSearch, come altri motori di ricerca, usano ancora i termini di arresto per migliorare le prestazioni.

È necessario gestire le parole non significative utilizzando i file CSV che si trovano nella directory `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` o nella directory `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`, a seconda di come è stato installato il software Commerce.

Per ulteriori informazioni sull&#39;utilizzo dei termini di arresto in Elasticsearch e OpenSearch, vedere le risorse seguenti:

- [Parole Chiuse: Prestazioni Rispetto A Precision](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords.html)
- [Pro e contro di parole bloccate](https://www.elastic.co/guide/en/elasticsearch/guide/current/pros-cons-stopwords.html)
- [Utilizzo di parole non significative](https://www.elastic.co/guide/en/elasticsearch/guide/current/using-stopwords.html)
- [Parole di arresto e prestazioni](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords-performance.html)

## Configurare le parole d&#39;arresto

Le parole non significative si trovano nella directory `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`. In Adobe Commerce è disponibile un file CSV contenente i termini per le impostazioni internazionali predefinite e un file aggiuntivo, `stopwords.csv`, contenente i termini per le impostazioni locali non rappresentate da un altro file CSV.

La durata predefinita per la cache dei file di parole non significative è di 15 minuti.

### Modificare le parole non significative per una lingua esistente

**Per modificare le parole non significative**:

1. Accedi al tuo server Commerce o passa a [proprietario del file system](../../installation/prerequisites/file-system/overview.md).
1. Utilizzare un editor di testo per aprire un file di parametri nella directory `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`.

   I file CSV utilizzano la convenzione di denominazione `stopwords_<locale_code>.csv`. Ad esempio, il nome del file di parole non significative tedesco è `stopwords_de_DE.csv`.

1. Aggiungere parole, rimuovere parole o modificare parole nel file.

   (Ogni parola d&#39;arresto in un file inizia su una nuova riga.)

1. Salva le modifiche e esci dall’editor di testo.
1. Pulisci la cache di configurazione.

   - Amministratore: **Sistema** > Strumenti > **Gestione cache**. Selezionare la casella di controllo **Configurazione** e fare clic su **Aggiorna** dall&#39;elenco precedente. Fai clic su **Invia** per completare l&#39;azione.

   - Riga di comando: come proprietario del file system, immettere il comando seguente:

     ```bash
     php <magento_root>/bin/magento cache:clean config
     ```

1. Controlla i risultati cercando i termini nella vetrina.

### Creazione di parole non significative per una nuova lingua

**Per aggiungere parole non significative per una lingua**:

1. Accedi al tuo server Commerce o passa a [proprietario del file system](../../installation/prerequisites/file-system/overview.md).

1. Utilizzare un editor di testo per creare un file di parole d&#39;ordine denominato `stopwords_<locale_code>.csv` nella directory `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`.

   Ad esempio, per creare parole non significative per le impostazioni internazionali italiane, assegnare al file il nome `stopwords_it_IT.csv`.

1. Nel file di parametri verificare che ogni indicatore di stato si trovi su una riga separata.
1. Salva le modifiche e esci dall’editor di testo.
1. Nella stessa directory, aprire `esconfig.xml` in un editor di testo.
1. Aggiungere una riga a `esconfig.xml` come segue:

   ```xml
   <LOCALE_CODE>stopwords_LOCALE_CODE.csv</LOCALE_CODE>
   ```

   Ad esempio, per aggiungere un file di parola d&#39;arresto italiano, aggiungete la seguente riga:

   ```xml
   <it_IT>stopwords_it_IT.csv</it_IT>
   ```

1. Salvare le modifiche apportate a `esconfig.xml` e uscire dall&#39;editor di testo.
1. Pulisci la cache di configurazione.

   - Amministratore: **Sistema** > Strumenti > **Gestione cache**. Selezionare la casella di controllo **Configurazione** e fare clic su **Aggiorna** dall&#39;elenco precedente. Fai clic su **Invia** per completare l&#39;azione.

   - Riga di comando: come proprietario del file system, immettere il comando seguente:

     ```bash
     php <magento_root>/bin/magento magento cache:clean config
     ```

1. Controlla i risultati cercando i termini nella vetrina.

## Cambia la directory di parole d&#39;arresto

In questa sezione viene illustrato come modificare la directory di default dei parametri di arresto da una delle seguenti opzioni:

- `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`
- `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`

La posizione dipende da come è stato installato il software Commerce. Se hai clonato l&#39;archivio GitHub di Magento 2, il percorso si trova in `app/code`. Se è stato installato un archivio compresso o un metapacchetto, il percorso si trova in `vendor`.

**Per modificare la directory**:

1. Come proprietario del file system, aprire Elasticsearch `di.xml` in un editor di testo.

   Se l&#39;archivio è stato clonato, si trova in `app/code/Magento/Elasticsearch/etc/di.xml`

   Se hai ottenuto un archivio o il metapacchetto, si trova in `vendor/magento/module-elasticsearch/etc/di.xml`

1. Modificare il valore di `stopwordsDirectory` nella directory desiderata:

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
           <argument name="stopwordsDirectory" xsi:type="string">app/code/Magento/Elasticsearch/etc/stopwords</argument>
       </arguments>
   </type>
   ```

1. Salvare le modifiche apportate a `di.xml` e uscire dall&#39;editor di testo.

## Per cambiare la directory dal modulo

1. [Crea un modulo](https://developer.adobe.com/commerce/php/development/build/component-file-structure/)
1. Nel modulo `etc/di.xml` aggiungi istruzioni:

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
          <argument name="stopwordsModule" xsi:type="string">Your_Module</argument>
          <argument name="stopwordsDirectory" xsi:type="string">stopwords</argument>
       </arguments>
   </type>
   ```

1. Nel modulo creare la directory `etc/stopwords` con il file CSV corrispondente.

1. Salvare le modifiche apportate a `di.xml` e uscire dall&#39;editor di testo.
