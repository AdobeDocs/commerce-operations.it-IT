---
title: Comprendere l’ambito dell’aggiornamento
description: Scopri le modifiche non compatibili con le versioni precedenti di una versione che potrebbero influire sui moduli personalizzati di Adobe Commerce o di Magento Open Source o sulle estensioni di terze parti.
exl-id: dab2a14f-dbf0-422e-afb4-642e2220ec7a
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '901'
ht-degree: 0%

---

# Comprendere l&#39;ambito dell&#39;aggiornamento

Rivedi [note sulla versione](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html) comprendere l’ambito di una versione, inclusi miglioramenti, correzioni di bug e problemi noti che potrebbero interessare moduli personalizzati e di terze parti.

## Modifiche non compatibili con le versioni precedenti

Le versioni di Adobe Commerce possono contenere modifiche non compatibili con le versioni precedenti. Consulta la documentazione sulle modifiche non compatibili con le versioni precedenti. Vedi quanto segue:

- **[Elementi di rilievo della modifica principale](https://devdocs.magento.com/guides/v2.4/release-notes/backward-incompatible-changes/index.html)**- Modifiche che hanno un impatto notevole e richiedono una spiegazione dettagliata e istruzioni speciali per garantire che i moduli di terze parti continuino a funzionare.
- **[Riferimento modifica minore](https://devdocs.magento.com/guides/v2.4/release-notes/backward-incompatible-changes/reference.html)**- Documentazione di riferimento generata dalla base di codice che descrive modifiche minori a classi, appartenenza API, database, iniezione di dipendenza, interfacce, layout, sistema e XSD.

## Estensioni di terze parti

I nuovi criteri di compatibilità di Adobe Commerce Marketplace garantiscono che _tutto_ Le estensioni elencate sono compatibili con l’ultima versione rilasciata entro 30 giorni dalla data GA. Per questo motivo, è importante ottenere le estensioni di terze parti, quando possibile, tramite il Marketplace.

## Moduli personalizzati

Tutti i moduli personalizzati devono essere verificati rispetto alla versione di destinazione a cui stai cercando di effettuare l’aggiornamento. Si tratta del processo di aggiornamento più dispendioso in termini di tempo e risorse. Durante la valutazione dei moduli personalizzati, è necessario cercare modifiche non compatibili con le versioni precedenti e tenere conto delle nuove pratiche, ad esempio la scomposizione del controller. Per ulteriori informazioni, consulta [note sulla versione](https://devdocs.magento.com/guides/v2.4/release-notes/bk-release-notes.html). Inoltre, assicurati di seguire [best practice](https://developer.adobe.com/commerce/php/best-practices/extensions/) per lo sviluppo di moduli.

## [!DNL Upgrade Compatibility Tool]

Il [!DNL Upgrade Compatibility Tool] è uno strumento della riga di comando che analizza l’istanza per potenziali problemi di aggiornamento. Verifica la presenza di problemi tra la versione corrente installata e la versione a cui stai tentando di effettuare l’aggiornamento.

L’utilizzo di questo strumento riduce lo sforzo richiesto al team per comprendere l’ambito e l’impatto di un aggiornamento. Consente di evitare i problemi di codice comuni durante l&#39;aggiornamento e fornisce indicazioni chiare su come risolvere i problemi identificati. Consente inoltre di assegnare la priorità ai problemi più critici necessari per garantire il successo dell&#39;aggiornamento, risparmiando tempo e costi.

Consulta le sezioni seguenti per iniziare a utilizzare [!DNL Upgrade Compatibility Tool]. Consulta la [!DNL Upgrade Compatibility Tool] [guida](../upgrade-compatibility-tool/overview.md) per ulteriori dettagli tecnici e casi d’uso avanzati.

### Scarica lo strumento

Utilizza Composer per scaricare lo strumento. Richiede PHP 7.3 o versione successiva, almeno 2 GB di RAM, Node.js (se stai verificando la compatibilità con GraphQL) e una licenza Adobe Commerce.

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

### Eseguire lo strumento

Per analizzare l’istanza e verificare la presenza di errori, avvisi e problemi critici:

```bash
bin/uct upgrade:check <dir> -c <coming version> 
```

>[!NOTE]
>
> Il `<dir>` è la directory in cui è memorizzata la base di codice. Il `-c` confronta la base di codice con la versione specificata.

Per identificare i problemi più critici che il team deve risolvere:

```bash
bin/uct upgrade:check /path/to/magento/ --ignore-current-compatibility-issues –min-issue-level critical --vanilla-dir /path/to/vanilla/code/ /path/to/magento/app/code/Vendor/
```

Altre opzioni da utilizzare con questo comando sono:

- `--ignore-current-version-compatibility-issues`- Elimina tutti i problemi critici, gli errori e gli avvisi noti relativi alla versione corrente. Vengono visualizzati solo errori relativi alla versione che si sta tentando di aggiornare.

- `--min-issue-level`- Consente di impostare il livello di problema minimo per assegnare la priorità solo ai problemi più importanti con l&#39;aggiornamento. Le opzioni sono avvertenza, errore e critico in ordine crescente di gravità.

- `-m | [=MODULE-PATH]`- Se si desidera analizzare solo un determinato fornitore, modulo o directory, è possibile specificare anche il percorso come opzione.

- `--vanilla-dir`- Consente di controllare il codice di base per qualsiasi implementazione non standard di funzioni o personalizzazioni. È importante che queste vengano pulite in anticipo. Un’istanza &quot;vanilla&quot; della tua versione viene scaricata automaticamente come riferimento.

  >[!NOTE]
  >
  > Questa operazione può essere eseguita anche con `core:code:changes` nello strumento).

### Analizzare l’output

Il [!DNL Upgrade Compatibility Tool] esporta un file JSON che identifica il codice o i moduli interessati, la gravità e una descrizione del problema per ogni problema riscontrato. Inoltre, genera un rapporto di riepilogo con un punteggio di complessità, che consente al team di comprendere approssimativamente ciò che serve per effettuare l’aggiornamento alla versione più recente. Più basso è il punteggio di complessità, più facile sarà eseguire l&#39;aggiornamento.

L’output seguente mostra un esempio di rapporto di riepilogo:

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

### Suggerimenti e consigli

Tutti i problemi identificati dallo strumento sono elencati nel rapporto con codici di errore specifici. Utilizza il [riferimento messaggio di errore](../upgrade-compatibility-tool/error-messages.md) per ottenere ulteriori dettagli su ciascun problema. In Adobe vengono inoltre forniti suggerimenti per la risoluzione di ogni tipo di problema, in modo da poter pianificare i passaggi di correzione.

Utilizza il rapporto per stimare lo sforzo necessario per aggiornare il codice per l’aggiornamento. In base alla tua esperienza, puoi stimare lo sforzo necessario per eseguire l’aggiornamento in base al numero totale di problemi identificati e alla gravità dei problemi. Poiché si tratta di uno strumento da riga di comando, puoi incorporarlo nelle suite di test automatizzati e di controllo del codice e utilizzare l’output JSON per generare i rapporti.

È consigliabile salvare i risultati di ogni progetto di aggiornamento in modo da poter confrontare i risultati futuri dell’aggiornamento con quelli precedenti. Con l’utilizzo continuo, inizierai a sviluppare una buona percezione del livello di impegno necessario per l’aggiornamento alla versione successiva solo dal rapporto di riepilogo fornito dallo strumento.

È inoltre consigliabile eseguire regolarmente lo strumento durante l’aggiornamento per avere visibilità sull’avanzamento. Il numero di problemi dovrebbe diminuire man mano che vengono risolti. Questo aiuta anche il tuo team a decidere l’approccio migliore per distribuire il lavoro.

Il [!DNL Upgrade Compatibility Tool] continua a essere migliorato e le versioni future includeranno funzioni quali correzioni automatiche per aiutarti a risolvere i problemi il più rapidamente possibile. Gli ultimi miglioramenti rilasciati a gennaio 2022 includono test di compatibilità PHP 8.1 e funzionalità di visualizzazione HTML che consentono di identificare rapidamente le aree che potrebbero richiedere più lavoro per l’aggiornamento.
