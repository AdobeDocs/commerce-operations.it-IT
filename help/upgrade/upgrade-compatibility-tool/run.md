---
title: Esegui il [!DNL Upgrade Compatibility Tool]
description: Segui questi passaggi per eseguire il [!DNL Upgrade Compatibility Tool] sul progetto Adobe Commerce.
source-git-commit: bcb8fced43c5d9972291f15a5039dbbc2a692a59
workflow-type: tm+mt
source-wordcount: '1864'
ht-degree: 0%

---


# Esegui il [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

La [!DNL Upgrade Compatibility Tool] è uno strumento a riga di comando che controlla un’istanza personalizzata di Adobe Commerce rispetto a una versione specifica analizzando tutti i moduli installati al suo interno. Restituisce un elenco di problemi critici, errori e avvisi che devono essere risolti prima di eseguire l’aggiornamento alla versione più recente di Adobe Commerce.

La [!DNL Upgrade Compatibility Tool] identifica potenziali problemi che devono essere risolti nel codice prima di tentare di eseguire l&#39;aggiornamento a una versione più recente di Adobe Commerce.

## Utilizza la `upgrade:check` command

La `upgrade:check` è il comando principale per eseguire lo strumento:

```bash
bin/uct upgrade:check <dir>
```

>[!TIP]
>
>La `<dir>` value è la directory in cui si trova l’istanza Adobe Commerce.

La `upgrade:check` esegue il comando [!DNL Upgrade Compatibility Tool] e controlla un&#39;istanza personalizzata di Adobe Commerce rispetto a una versione specifica analizzando tutti i moduli installati al suo interno. Restituisce un elenco di problemi critici, errori e avvisi che devono essere risolti prima di eseguire l’aggiornamento alla versione più recente del tuo Adobe Commerce.

>[!WARNING]
>
>Esegui solo quando viene fornita la directory principale del progetto (o principale).

Questo comando controlla le modifiche del codice di base per la specifica istanza di Adobe Commerce e tutte le modifiche del codice personalizzato installate al suo interno.

Puoi eseguire il `core:code:changes` per analizzare solo le modifiche del codice di base per quella specifica istanza di Adobe Commerce. Vedi [Modifiche al codice core](../upgrade-compatibility-tool/run.md#use-the-core:code:changes-command) sezione .

Quando è possibile utilizzare `graphql:compare` confrontare due schemi GraphQL per verificare la presenza di eventuali modifiche tra di essi. Vedi [Verifica della compatibilità dello schema GraphQL](../upgrade-compatibility-tool/run.md#graphql-schema-compatibility-verification) sezione .

### Recommendations per utilizzare `upgrade:check` command

- La [!DNL Upgrade Compatibility Tool] richiede almeno 2 GB di RAM per l&#39;esecuzione. Questa impostazione è consigliata per evitare problemi dovuti a una limitazione della memoria insufficiente. La [!DNL Upgrade Compatibility Tool] visualizza una domanda se esegui `upgrade:check` comando con basso `memory_limit` impostazione.
- Specifica la `-m` opzione per eseguire lo strumento rispetto a un modulo specifico:

   ```bash
   bin/uct upgrade:check <dir> -m[=MODULE-PATH]
   ```

Se gli argomenti sono i seguenti:

- `<dir>`: Directory di installazione di Adobe Commerce.
- `[=MODULE-PATH]`: Directory del percorso del modulo specifico.

### Utilizza la `--help` opzione

Per visualizzare il [!DNL Upgrade Compatibility Tool] opzioni generali di comando e aiuto, eseguire:

```bash
bin/uct --help
```

Tuttavia, è possibile eseguire `--help` come opzione quando si esegue un comando specifico, come `bin/uct upgrade:check`. Questo restituisce un valore specifico `--help` opzioni per quel comando:

```bash
bin/uct upgrade:check --help
```

Disponibile `--help` opzioni per `upgrade:check` comando:

- `-m, --module-path[=MODULE-PATH]`: Percorso dei moduli da analizzare
- `-a, --current-version[=CURRENT-VERSION]`: La versione corrente di Adobe Commerce, la versione dell’installazione di Adobe Commerce, verrà utilizzata se omessa.
- `-c, --coming-version[=COMING-VERSION]`: La versione Adobe Commerce di destinazione, la versione dell’installazione di Adobe Commerce, verrà utilizzata se omessa.
- `--json-output-path[=JSON-OUTPUT-PATH]`: Percorso del file in cui verrà esportato l&#39;output in formato json.
- `--html-output-path[=HTML-OUTPUT-PATH]`: Percorso del file in cui verrà esportato l’output in formato HTML.
- `--min-issue-level`: Livello minimo di problema da visualizzare nel rapporto. Il valore predefinito è [AVVISO].
- `--ignore-current-version-compatibility-issues`: Utilizza questa opzione quando non desideri includere problemi critici noti, errori e avvisi nel tuo [!DNL Upgrade Compatibility Tool] rapporto.
- `--context=CONTEXT`: Contesto di esecuzione. Questa opzione è a scopo di integrazione e non influisce sul risultato dell’esecuzione.
- `-h, --help`: Visualizza la Guida per quel comando specifico. Se non viene fornito alcun comando, `list` è il risultato predefinito.
- `-q, --quiet`: Non inviare messaggi durante l&#39;esecuzione del comando.
- `-v, --version`: Visualizza la versione dell&#39;applicazione.
- `--ansi, --no-ansi`: Abilita uscita ANSI.
- `-n, --no-interaction`: Non fare domande interattive durante l&#39;esecuzione del comando.
- `-v, --vv, --vvv, --verbose`: Aumentare la verbosità delle comunicazioni in uscita. 1 per uscita normale, 2 per uscita dettagliata e 3 per uscita DEBUG.

### Uscita

A seguito dell&#39;analisi effettuata, il [!DNL Upgrade Compatibility Tool] esporta un rapporto che contiene un elenco di problemi per ogni file, specificando gravità, codice di errore e descrizione dell’errore.

Vedi l&#39;esempio seguente:

```terminal
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 23: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.2'
 * [ERROR][1429] Line 103: Call method 'Magento\Framework\Api\SearchCriteriaBuilder::addFilters' that is non API on version '2.4.2'
 * [CRITICAL][1110] Line 60: Instantiating class/interface 'Magento\Catalog\Model\ProductRepository' that does not exist on version '2.4.2'
```

Controlla la [Riferimento al messaggio di errore](error-messages.md) per ulteriori informazioni.

Il rapporto include anche un riepilogo dettagliato che mostra:

- *Versione corrente*: versione attualmente installata.
- *Versione di destinazione*: la versione a cui desideri eseguire l’aggiornamento.
- *Tempo di esecuzione*: il tempo impiegato dall&#39;analisi per costruire il rapporto (mm:ss).
- *Moduli che richiedono aggiornamento*: la percentuale di moduli che contengono problemi di compatibilità e richiedono l’aggiornamento.
- *File che richiedono l’aggiornamento*: la percentuale di file che contengono problemi di compatibilità e richiedono l’aggiornamento.
- *Errori critici totali*: numero di errori critici rilevati.
- *Errori totali*: numero di errori rilevati.
- *Avvisi totali*: numero di avvisi rilevati.

Vedi l&#39;esempio seguente:

```terminal
 ----------------------------- ------------------
  Current version               2.4.2
  Target version                2.4.3
  Execution time                1m:10s
  Modules that require update   78.33% (47/60)
  Files that require update     21.62% (115/532)
  Total critical issues         35
  Total errors                  201
  Total warnings                103
 ----------------------------- ------------------
```

>[!NOTE]
>
>Per impostazione predefinita, la [!DNL Upgrade Compatibility Tool] esporta il rapporto in 2 formati diversi: `json` e `html`.

#### JSON

Il file JSON contiene esattamente le stesse informazioni mostrate nell’output:

- Elenco dei problemi individuati.
- Sintesi dell&#39;analisi.

Per ogni problema riscontrato, il rapporto fornisce informazioni dettagliate, ad esempio la gravità e la descrizione del problema.

>[!NOTE]
>
>Il percorso predefinito per la cartella di output è `var/output/[TIME]-results.json`.

Per esportare il rapporto in una cartella di output diversa, esegui:

```bash
bin/uct upgrade:check <dir> --json-output-path[=JSON-OUTPUT-PATH]
```

Se gli argomenti sono i seguenti:

- `<dir>`: Directory di installazione di Adobe Commerce.
- `[=JSON-OUTPUT-PATH]`: Directory del percorso per esportare `.json` file di output.

>[!NOTE]
>
>Il percorso predefinito per la cartella di output è `var/output/[TIME]-results.json`.

#### HTML

Il file HTML contiene anche l’elenco dei problemi identificati e il riepilogo dell’analisi. Include inoltre quattro diversi grafici:

- **Moduli per gravità del problema**: Mostra la distribuzione della gravità per moduli.
- **File per gravità del problema**: Mostra la distribuzione della gravità per file.
- **Moduli ordinati per numero totale di problemi**: Mostra i 10 moduli più compromessi tenendo conto di avvisi, errori ed errori critici.
- **Moduli con dimensioni e problemi relativi**: Più file contiene un modulo, più grande è il suo cerchio. Più problemi ha un modulo, più rosso appare il suo cerchio.

Questi grafici ti consentono di identificare, a colpo d&#39;occhio, le parti più compromesse e quelle che richiedono più lavoro per eseguire un aggiornamento.

![Rapporto HTML - Riepilogo](../../assets/upgrade-guide/uct-html-summary.png)

![Rapporto HTML - Dettagli](../../assets/upgrade-guide/uct-html-details.png)

Per esportare il rapporto in una cartella di output diversa, esegui:

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

Se gli argomenti sono i seguenti:

- `<dir>`: Directory di installazione di {{site.data.var.ee}}.
- `[=HTML-OUTPUT-PATH]`: Directory del percorso per esportare `.html` file di output.

>[!NOTE]
>
>Il percorso predefinito per la cartella di output è `var/output/[TIME]-results.html`.

### Utilizza la `--ignore-current-version-compatibility-issues` opzione

La [!DNL Upgrade Compatibility Tool] consente di eseguire il `upgrade:check` con un comando `--ignore-current-version-compatibility-issues` quindi mostra solo problemi critici nuovi o sconosciuti, errori e avvisi. Utilizza questa opzione quando non desideri includere problemi critici noti, errori e avvisi nel tuo [!DNL Upgrade Compatibility Tool] rapporto.

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
>Questo vale solo per le convalide API PHP.

### Installazione di vaniglia

A _vaniglia_ installazione è un’installazione pulita di un tag di versione o di un ramo specifico per una versione specifica di rilascio.

La `bin/uct core:code:changes` controlla se nel sistema è presente un&#39;istanza di vaniglia. Se questa è la prima volta che si utilizza un&#39;installazione di vaniglia, una domanda interattiva della riga di comando richiede di scaricare il progetto di vaniglia dal [Archivio Adobe Commerce](https://repo.magento.com/).

Puoi eseguire un [!DNL Upgrade Compatibility Tool] con il comando `--vanilla-dir` per specificare la directory di installazione di vaniglia di Adobe Commerce.

Consulta la sezione [Distribuzione di un&#39;istanza di vaniglia](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) per ulteriori informazioni.

## Utilizza la `list` command

Per restituire un elenco di [!DNL Upgrade Compatibility Tool] comandi disponibili, esegui:

```bash
bin/uct list
```

La `list` restituisce quanto segue:

- `-h, --help`: Visualizza la Guida per quel comando specifico. Se non viene fornito alcun comando, `list` è il risultato predefinito.
- `-q, --quiet`: Non inviare messaggi durante l&#39;esecuzione del comando.
- `-v, --version`: Visualizza la versione dell&#39;app.
- `--ansi, --no-ansi`: Abilita uscita ANSI.
- `-n, --no-interaction`: Non fare domande interattive durante l&#39;esecuzione del comando.
- `-v, --vv, --vvv, --verbose`: Aumentare la verbosità delle comunicazioni in uscita. 1 per uscita normale, 2 per uscita dettagliata e 3 per uscita DEBUG.

## Utilizza la `core:code:changes` command

Puoi confrontare l’installazione di Adobe Commerce corrente con un’installazione di vaniglia pulita per verificare se il codice core ha apportato modifiche per implementare una nuova funzione o personalizzazione. Questa convalida consente di stimare lo sforzo necessario per l’aggiornamento in base a tali modifiche.

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

Se gli argomenti sono i seguenti:

- `<dir>`: Directory di installazione di Adobe Commerce.
- `<vanilla dir>`: Directory di installazione della vaniglia Adobe Commerce.

Ci sono alcune limitazioni durante l&#39;esecuzione di questo comando:

- Esegui solo quando viene fornita la directory principale del progetto (o principale).
- Mostra solo un elenco di modifiche principali.

### Utilizza la `core:code:changes` con il comando `--help` opzione

Disponibile `--help` opzioni per `core:code:changes` comando:

- `-h, --help`: Visualizza la Guida per quel comando specifico. Se non viene fornito alcun comando, `list` è il risultato predefinito.
- `-q, --quiet`: Non inviare messaggi durante l&#39;esecuzione del comando.
- `-v, --version`: Visualizza la versione dell&#39;app.
- `--ansi, --no-ansi`: Abilita uscita ANSI.
- `-n, --no-interaction`: Non fare domande interattive durante l&#39;esecuzione del comando.
- `-v, --vv, --vvv, --verbose`: Aumentare la verbosità delle comunicazioni in uscita. 1 per uscita normale, 2 per uscita dettagliata e 3 per uscita DEBUG.

## Versione

Puoi confrontare l’installazione corrente di Adobe Commerce con le versioni di Adobe Commerce `>=2.3`.

È necessario fornire la versione come parametro quando si esegue il comando:

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

Dove:

- `-c, --coming-version[=COMING-VERSION]`: La versione di destinazione di Adobe Commerce.

Sono presenti alcune limitazioni durante l&#39;esecuzione del comando precedente:

- Questo parametro fa riferimento a qualsiasi tag che identifica una versione specifica di Adobe Commerce.
- È un obbligo di prevedere esplicitamente tale obbligo; fornire solo il suo valore non funziona.
- Fornisci la versione del tag senza virgolette (né singole né doppie): ~~&quot;2.4.1-sviluppo&quot;~~.
- NON devi fornire versioni precedenti a quella attualmente installata, né versioni precedenti alla 2.3, che è la versione più vecchia attualmente supportata.

### Utilizza la `refactor` command

La [!DNL Upgrade Compatibility Tool] è in grado di risolvere automaticamente un set ridotto di problemi:

- Funzioni consentite per l’utilizzo senza passare un argomento, ma con tale utilizzo ora è obsoleta.
- Utilizzo di `$this` nei modelli di Magento.
- Utilizzo della parola chiave PHP `final` in metodi privati.

Esegui:

```bash
bin/uct refactor <dir>
```

## Verifica della compatibilità dello schema GraphQL

La [!DNL Upgrade Compatibility Tool] fornisce inoltre l’opzione per introdurre due endpoint GraphQL e confrontare i rispettivi schemi in cerca di modifiche interrotte e pericolose tra di essi:

```bash
bin/uct graphql:compare <schema1> <schema2>
```

Se gli argomenti sono i seguenti:

- `<schema1>`: URL dell&#39;endpoint per l&#39;installazione esistente.
- `<schema2>`: URL dell&#39;endpoint per l&#39;installazione di vaniglia.

Deve essere in esecuzione `instance before` e `instance after` l&#39;aggiornamento.

### GraficoQL, comando di confronto `--help` options

Disponibile `--help` opzioni per `graphql:compare` comando:

- `-h, --help`: Visualizza la Guida per quel comando specifico. Se non viene fornito alcun comando, `list` è il risultato predefinito.
- `-q, --quiet`: Non inviare messaggi durante l&#39;esecuzione del comando.
- `-v, --version`: Visualizza la versione dell&#39;app.
- `--ansi, --no-ansi`: Abilita uscita ANSI.
- `-n, --no-interaction`: Non fare domande interattive durante l&#39;esecuzione del comando.
- `-v, --vv, --vvv, --verbose`: Aumentare la verbosità delle comunicazioni in uscita. 1 per uscita normale, 2 per uscita dettagliata e 3 per uscita DEBUG.

### Esempio con un elenco di problemi critici, errori e avvisi per GraphQL

```terminal
 *   [WARNING] FIELD_CHANGED_KIND: ConfigurableProduct.gender changed type from Int to String.
 *   [WARNING] OPTIONAL_INPUT_FIELD_ADDED: An optional field sku on input type ProductAttributeSortInput was added.
```

Vedi [Informazioni per gli sviluppatori](../upgrade-compatibility-tool/developer.md) per ulteriori informazioni.

Puoi eseguire il [!DNL Upgrade Compatibility Tool] con una configurazione di esecuzione tramite il plugin PhpStorm. Consulta la sezione [[!DNL Upgrade Compatibility Tool] Esegui configurazione](https://devdocs.magento.com/guides/v2.3/ext-best-practices/phpstorm/uct-run-configuration.html) per ulteriori informazioni.

## Azioni consigliate

### Ottimizzare i risultati

La [!DNL Upgrade Compatibility Tool] fornisce un rapporto contenente i risultati per impostazione predefinita con tutti i problemi identificati nel progetto. Puoi ottimizzare i risultati per concentrarti sui problemi da risolvere per completare l&#39;aggiornamento:

- Utilizza l’opzione `--ignore-current-version-compatibility-issues`, che sopprime tutti i problemi critici noti, gli errori e gli avvisi relativi alla versione corrente di Adobe Commerce. Fornisce solo errori rispetto alla versione a cui si sta tentando di eseguire l&#39;aggiornamento.
- Aggiungi il `--min-issue-level` questa impostazione consente di impostare il livello minimo di problema, in modo da assegnare priorità solo ai problemi più importanti con l&#39;aggiornamento. Se si desidera analizzare solo un determinato fornitore, modulo o persino directory, è possibile specificare anche il percorso come opzione.
- Esegui il `bin` con l&#39;opzione aggiunta `-m`. Ciò consente di [!DNL Upgrade Compatibility Tool] per analizzare un modulo specifico in modo indipendente e aiuta con i problemi di memoria che possono verificarsi durante l&#39;esecuzione [!DNL Upgrade Compatibility Tool].

### Segui le best practice di Adobe Commerce

- Evitare di avere due moduli con lo stesso nome.
- Segui Adobe Commerce [norme di codifica](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html).

## Risoluzione dei problemi

### Errore di segmentazione

Quando due moduli hanno lo stesso nome, la [!DNL Upgrade Compatibility Tool] mostra un errore di segmentazione.

Per evitare questo errore, si consiglia di eseguire il `bin` con l&#39;opzione aggiunta `-m`:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/<module-name>
```

>[!NOTE]
>
>La `<dir>` value è la directory in cui si trova l’istanza Adobe Commerce.

La `-m` consente di [!DNL Upgrade Compatibility Tool] per analizzare ogni modulo specifico in modo indipendente, in modo da evitare di incontrare due moduli con lo stesso nome nell’istanza Adobe Commerce.

Questa opzione di comando consente inoltre di [!DNL Upgrade Compatibility Tool] per analizzare una cartella contenente diversi moduli:

```bash
bin/uct upgrade:check /<dir>/<instance-name> --coming-version=2.4.1 -m /vendor/<vendor-name>/
```

Questa raccomandazione aiuta anche con i problemi di memoria che possono verificarsi durante l&#39;esecuzione di [!DNL Upgrade Compatibility Tool].

### Uscita vuota

>[!NOTE]
>
>La `M2_VERSION` è la versione Adobe Commerce di destinazione che desideri confrontare con la tua istanza Adobe Commerce.

Se dopo aver eseguito questo comando:

```bash
bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
```

L&#39;unico output è `Upgrade compatibility tool`:

```terminal
bin/uct upgrade:check /var/www/project/magento/ -c 2.4.1
Upgrade compatibility tool
```

La causa probabile è una limitazione della memoria PHP.
Ignorare la limitazione della memoria impostando `memory_limit` a `-1`:

```bash
php -d memory_limit=-1 /bin/uct upgrade:check INSTALLATION_DIR -c M2_VERSION
```
