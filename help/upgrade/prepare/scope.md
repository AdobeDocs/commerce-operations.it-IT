---
title: Comprendere l'ambito dell'aggiornamento
description: Scopri le modifiche incompatibili con le versioni precedenti in una versione che potrebbero avere un impatto sui moduli personalizzati Adobe Commerce o Magenti Open Source o sulle estensioni di terze parti.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '916'
ht-degree: 0%

---


# Comprendere l’ambito dell’aggiornamento

Consulta la sezione [note sulla versione](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html) per comprendere l’ambito di una versione, inclusi miglioramenti, correzioni di bug e problemi noti che potrebbero interessare moduli di terze parti e personalizzati.

## Modifiche incompatibili con le versioni precedenti

Le versioni Adobe Commerce e Magenti Open Source possono contenere modifiche incompatibili con le versioni precedenti. Consulta la documentazione sulle modifiche non compatibili con le versioni precedenti, consulta quanto segue:

- **[Elementi principali da modificare](https://devdocs.magento.com/guides/v2.4/release-notes/backward-incompatible-changes/index.html)**- Modifiche che hanno un impatto rilevante e richiedono spiegazioni dettagliate e istruzioni speciali per garantire il funzionamento dei moduli di terze parti.
- **[Riferimento per la modifica secondaria](https://devdocs.magento.com/guides/v2.4/release-notes/backward-incompatible-changes/reference.html)**- Documentazione di riferimento generata dalla base di codice che descrive modifiche minori alle classi, appartenenza API, database, iniezione di dipendenza, interfacce, layout, sistema e XSD.

## Estensioni di terze parti

La nuova politica di compatibilità di Adobe Commerce Marketplace assicura che _tutto_ le estensioni elencate sono compatibili con l’ultima versione rilasciata entro 30 giorni dalla data GA. Per questo motivo, è importante ottenere estensioni di terze parti, quando possibile, tramite Marketplace.

## Moduli personalizzati

Tutti i moduli personalizzati devono essere verificati rispetto alla versione di destinazione a cui si desidera effettuare l’aggiornamento. Questo è il processo più lungo e laborioso di un aggiornamento, Durante la valutazione dei moduli personalizzati, è necessario cercare le modifiche incompatibili con le versioni precedenti e conoscere nuove pratiche, come la decomposizione del controller. Per ulteriori informazioni, consulta la sezione [note sulla versione](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html). Inoltre, assicurati di seguire [best practice](https://devdocs.magento.com/guides/v2.4/ext-best-practices/extension-coding/common-programming-bp.html) per lo sviluppo del modulo.

## Strumento di compatibilità per l’aggiornamento

Lo strumento di compatibilità per l’aggiornamento è uno strumento a riga di comando che analizza l’istanza per potenziali problemi di aggiornamento. Controlla i problemi tra la versione corrente installata e la versione a cui si sta tentando di eseguire l&#39;aggiornamento.

L’utilizzo di questo strumento riduce lo sforzo richiesto al team per comprendere l’ambito e l’impatto di un aggiornamento. Consente di evitare problemi di codice comuni durante l&#39;aggiornamento e fornisce indicazioni chiare su come risolvere i problemi identificati. Inoltre, aiuta a dare la priorità ai problemi più critici necessari per garantire un aggiornamento di successo, risparmiando tempo e costi durante l&#39;aggiornamento.

Per iniziare a utilizzare lo strumento di compatibilità per l’aggiornamento, consulta le sezioni seguenti. Consulta lo strumento di compatibilità per l’aggiornamento [guida](../upgrade-compatibility-tool/overview.md) per ulteriori dettagli tecnici e casi di utilizzo avanzati.

### Scarica lo strumento

Utilizza Compositore per scaricare lo strumento. Richiede PHP 7.3 o versione successiva, almeno 2 GB di RAM, Node.js (se stai controllando la compatibilità GraphQL) e una licenza Adobe Commerce.

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

### Esegui lo strumento

Per analizzare la tua istanza e verificare la presenza di errori, avvisi e problemi critici:

```bash
bin/uct upgrade:check <dir> -c <coming version> 
```

>[!NOTE]
>
> La `<dir>` argomento è la directory in cui viene memorizzata la base di codice. La `-c` confronta la base di codice con la versione specificata (ad esempio, 2.4.4).

Per identificare i problemi più critici che il tuo team deve risolvere:

```bash
bin/uct upgrade:check /path/to/magento/ --ignore-current-compatibility-issues –min-issue-level critical --vanilla-dir /path/to/vanilla/code/ /path/to/magento/app/code/Vendor/
```

Altre opzioni da utilizzare con questo comando sono:

- `--ignore-current-version-compatibility-issues`- Elimina tutti i problemi critici noti, gli errori e gli avvisi relativi alla versione corrente. Fornisce solo errori rispetto alla versione che si sta tentando di aggiornare.

- `--min-issue-level`: ti consente di impostare il livello minimo di problema per dare priorità solo ai problemi più importanti con l’aggiornamento. Le opzioni sono avvisi, errori e critiche in ordine crescente di gravità.

- `-m | [=MODULE-PATH]`- Se si desidera analizzare solo un determinato fornitore, modulo o directory, è possibile specificare anche il percorso come opzione.

- `--vanilla-dir`- Consente di controllare il codice di base per qualsiasi implementazione non standard di funzionalità o personalizzazioni. E&#39; importante che queste vengano ripulite in anticipo. Un&#39;istanza di vaniglia della tua versione viene scaricata automaticamente come riferimento.

   >[!NOTE]
   >
   > Questo può essere fatto anche con il `core:code:changes` nello strumento).

### Analizzare l&#39;output

Lo strumento di compatibilità per l’aggiornamento esporta un file JSON che identifica il codice o i moduli interessati, la gravità e una descrizione del problema per ogni problema riscontrato. Inoltre, genera un rapporto di riepilogo con un punteggio di complessità, che consente al tuo team di comprendere più o meno ciò che serve per eseguire l’aggiornamento alla versione più recente. Più basso è il punteggio di complessità, più facile sarà eseguire l&#39;aggiornamento.

Il seguente output mostra un esempio di rapporto di riepilogo:

```console
 ------------------------ --------
  Installed version        2.4.2
  Adobe Commerce version   2.4.3
  Running time             0m:48s
  Checked modules          14
  Core checked modules     0
  Core modified files      0
  % core modified files    0.00
  PHP errors found         109
  PHP warnings found       0
  GraphQL errors found     0
  GraphQL warnings found   0
  Total errors found       109
  Total warnings found     0
  Complexity score         218
 ------------------------ --------
```

### Suggerimenti

Tutti i problemi identificati dallo strumento sono elencati nel rapporto con codici di errore specifici. Utilizza la [riferimento a un messaggio di errore](../upgrade-compatibility-tool/error-messages.md) per ottenere ulteriori dettagli su ogni problema. In Adobe sono inoltre disponibili suggerimenti per correggere ogni tipo di problema in modo da poter pianificare i passaggi per l’aggiornamento.

Utilizza il rapporto per stimare il tempo necessario per aggiornare il codice per l&#39;aggiornamento. In base all’esperienza, puoi stimare lo sforzo necessario per effettuare l’aggiornamento in base al numero totale di problemi identificati e alla gravità dei problemi. Poiché si tratta di uno strumento a riga di comando, puoi incorporarlo nelle suite di test e di controllo del codice automatizzati e utilizzare l’output JSON per generare i rapporti.

È consigliabile salvare i risultati di ogni progetto di aggiornamento in modo da poter confrontare i risultati futuri dell’aggiornamento con i risultati precedenti. Con un utilizzo continuo, inizierai a sviluppare un’idea del livello di impegno necessario per eseguire l’aggiornamento alla versione successiva, partendo dal rapporto di riepilogo fornito dallo strumento.

Inoltre, consigliamo di eseguire regolarmente lo strumento mentre lavori all’aggiornamento per avere una visibilità sull’avanzamento. Il numero di problemi dovrebbe diminuire man mano che li correggi. Questo aiuta anche il tuo team a decidere l&#39;approccio migliore per distribuire il lavoro.

Le versioni future dello strumento incorporeranno test e autocorrezioni di compatibilità PHP 8.1 per aiutarti a risolvere i problemi il più rapidamente possibile.
