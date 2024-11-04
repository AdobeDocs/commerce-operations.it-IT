---
title: Comprendere l'ambito dell'aggiornamento
description: Scopri di modifiche incompatibili con le versioni precedenti in una versione che potrebbero influire sui moduli personalizzati di Adobe Systems Commerce o sulle estensioni di terze parti.
exl-id: dab2a14f-dbf0-422e-afb4-642e2220ec7a
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '897'
ht-degree: 0%

---

# Comprendere il ambito dell&#39;aggiornamento

Esaminare la [note sulla versione](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/overview) per comprendere il ambito di una versione, inclusi miglioramenti, correzioni di bug e problemi noti che potrebbero influire su moduli personalizzati e di terze parti.

## Modifiche incompatibili con le versioni precedenti

Le versioni di Adobe Systems Commerce possono contenere modifiche incompatibili con le versioni precedenti. Consulta la nostra documentazione sulle modifiche incompatibili con le versioni precedenti, consulta quanto segue:

- **[Modifiche principali in evidenza](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/)**: modifiche che hanno un impatto importante e richiedono una spiegazione dettagliata e istruzioni speciali per garantire che i moduli di terze parti continuino a funzionare.
- **[Riferimento](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/)** a modifiche minori: documentazione di riferimento generata dalla codebase che descrive modifiche minori a classi, iscrizione API, database, inserimento di dipendenze, interfacce, layout, sistema e XSD.

## Estensioni di terze parti

I nuovi criteri di compatibilità di Adobe Commerce Marketplace garantiscono che _tutte_ le estensioni elencate siano compatibili con l&#39;ultima versione rilasciata entro 30 giorni dalla data GA. Per questo motivo, è importante ottenere le estensioni di terze parti, quando possibile, tramite il Marketplace.

## Moduli personalizzati

Tutti i moduli personalizzati devono essere confrontati con la versione destinazione a cui si desidera eseguire l&#39;aggiornamento. Questo è il processo che richiede più tempo e risorse di un aggiornamento. Quando si valutano i moduli personalizzati, è necessario cercare le modifiche incompatibili con le versioni precedenti ed essere consapevoli delle nuove pratiche, come la scomposizione del controller. Per ulteriori informazioni, consulta la [note sulla versione](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/overview). Inoltre, assicurati di seguire [le best practice](https://developer.adobe.com/commerce/php/best-practices/extensions/) per lo sviluppo dei moduli.

## [!DNL Upgrade Compatibility Tool]

È [!DNL Upgrade Compatibility Tool] un strumento da riga di comando che analizza il istanza alla ricerca di potenziali problemi di aggiornamento. Verifica la presenza di problemi tra la versione corrente installata e la versione a cui si sta tentando di eseguire l&#39;aggiornamento.

L&#39;utilizzo di questo strumento riduce lo sforzo richiesto al team per comprendere la ambito e l&#39;impatto di un aggiornamento. Consente di evitare problemi di codice comuni durante l&#39;aggiornamento e fornisce indicazioni chiare su come risolvere i problemi identificati. Aiuta anche a dare priorità ai problemi più critico necessari per garantire un aggiornamento di successo, risparmiando tempo e costi durante l&#39;aggiornamento.

Per iniziare a usare .[!DNL Upgrade Compatibility Tool] Consulta la [!DNL Upgrade Compatibility Tool] [guida](../upgrade-compatibility-tool/overview.md) per ulteriori dettagli tecnici e casi d&#39;uso avanzati.

### Scarica l&#39;strumento

Utilizza Composer per scaricare il strumento. Richiede PHP 7.3 o successivo, almeno 2 GB di RAM, Node.js (se si sta verificando la compatibilità GraphQL) e una licenza Adobe Systems Commerce.

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

### Eseguire l&#39;strumento

Per analizzare il istanza e verificare la presenza di errori, avvisi e problemi critico:

```bash
bin/uct upgrade:check <dir> -c <coming version> 
```

>[!NOTE]
>
> L&#39;argomento `<dir>` è la directory in cui è memorizzata la codebase. L&#39;opzione `-c` confronta la tua base di codice con la versione specificata.

Per identificare i problemi più critico che il tuo team affrontare:

```bash
bin/uct upgrade:check /path/to/magento/ --ignore-current-compatibility-issues –min-issue-level critical --vanilla-dir /path/to/vanilla/code/ /path/to/magento/app/code/Vendor/
```

Alcune altre opzioni da utilizzare con questo comando sono:

- `--ignore-current-version-compatibility-issues`- Elimina tutti i problemi critico noti, gli errori e gli avvisi relativi alla versione corrente. Fornisce solo errori rispetto alla versione che si sta tentando di aggiornare.

- `--min-issue-level`—Consente di impostare il livello di problema minimo per assegnare la priorità solo ai problemi più importanti con l&#39;aggiornamento. Le opzioni sono avvertenza, errore e critico in ordine crescente di gravità.

- `-m | [=MODULE-PATH]` - Se si desidera analizzare solo un determinato fornitore, modulo o directory, è possibile specificare il percorso come opzione.

- `--vanilla-dir` - Consente di controllare il codice di base per qualsiasi implementazione non standard di funzionalità o personalizzazioni. È importante che questi vengano puliti in anticipo. Una istanza vanilla della versione viene scaricata automaticamente come riferimento.

  >[!NOTE]
  >
  > Questo può essere fatto anche con il `core:code:changes` comando nella strumento).

### Analizzare i Output

Esporta [!DNL Upgrade Compatibility Tool] un file JSON che identifica il codice o i moduli interessati, la gravità e una descrizione del problema per ogni problema riscontrato. Produce anche un rapporto di riepilogo con un punteggio di complessità, che consente al team di capire approssimativamente cosa serve per eseguire l&#39;aggiornamento alla versione più recente. Più basso è il punteggio di complessità, più facile sarà eseguire l&#39;aggiornamento.

L&#39;output seguente mostra un esempio di rapporto di riepilogo:

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

Tutti i problemi identificati in strumento sono elencati nel report con codici di errore specifici. Utilizza il riferimento](../upgrade-compatibility-tool/error-messages.md) al [messaggio di errore per ottenere ulteriori dettagli su ciascun problema. Adobe Systems inoltre vengono forniti suggerimenti per risolvere ogni tipo di problema in modo da poter pianificare i passaggi correttivi.

Utilizzare il rapporto per stimare l&#39;impegno necessario per aggiornare il codice per l&#39;aggiornamento. In base alla tua esperienza, puoi stimare lo sforzo richiesto per l&#39;aggiornamento in base al numero totale di problemi identificati e alla gravità dei problemi. Poiché si tratta di un strumento da riga di comando, è possibile incorporarlo nelle suite di test e controllo del codice automatizzati e utilizzare l&#39;output JSON per generare i report.

È consigliabile salvare i risultati di ogni progetto di aggiornamento in modo da poter confrontare i risultati degli aggiornamenti futuri con quelli precedenti. Con l&#39;uso continuato, inizierai a sviluppare una buona idea del livello di impegno necessario per eseguire l&#39;aggiornamento alla versione successiva solo dal rapporto di riepilogo fornito dal strumento.

È inoltre consigliabile eseguire regolarmente lo strumento durante l’aggiornamento per avere visibilità sull’avanzamento. Il numero di problemi dovrebbe diminuire man mano che vengono risolti. Questo aiuta anche il tuo team a decidere l’approccio migliore per distribuire il lavoro.

[!DNL Upgrade Compatibility Tool] continua a essere migliorato e le versioni future includeranno funzioni quali correzioni automatiche per aiutarti a risolvere i problemi il più rapidamente possibile. Gli ultimi miglioramenti rilasciati a gennaio 2022 includono test di compatibilità PHP 8.1 e funzionalità di visualizzazione HTML che consentono di identificare rapidamente le aree che potrebbero richiedere più lavoro per l’aggiornamento.
