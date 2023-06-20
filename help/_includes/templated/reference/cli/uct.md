---
source-git-commit: 64c453adabb092075854b2c20bf7da73c4a5146e
workflow-type: tm+mt
source-wordcount: '1529'
ht-degree: 0%

---
# bin/uct

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**Versione**: 3.0.3

Questo riferimento contiene 9 comandi disponibili tramite `bin/uct` strumento da riga di comando.
L’elenco iniziale viene generato automaticamente utilizzando `bin/uct list` in Adobe Commerce.

Ulteriori informazioni sullo strumento sono disponibili in [Panoramica](/help/upgrade/upgrade-compatibility-tool/overview.md).

>[!NOTE]
>
>Questo riferimento viene generato dalla base di codice dell&#39;applicazione. Per modificare il contenuto, puoi aggiornare il codice sorgente per l’implementazione del comando corrispondente in [codebase](https://github.com/magento) e inviare le modifiche per la revisione. Un altro modo consiste nel _Inviaci feedback_ (trovi il collegamento in alto a destra). Per le linee guida sui contributi, consulta [Contributi codice](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `_complete`

Comando interno per fornire suggerimenti per il completamento della shell

```bash
bin/uct _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-S|--symfony SYMFONY]
```

### `--shell`, `-s`

Tipo di shell (&quot;bash&quot;)

- Richiede un valore

### `--input`, `-i`

Array di token di input (ad esempio, COMP_WORDS o argv)

- Predefinito: `[]`
- Richiede un valore

### `--current`, `-c`

Indice dell&#39;array &quot;input&quot; in cui si trova il cursore (ad esempio, COMP_CWORD)

- Richiede un valore

### `--symfony`, `-S`

Versione dello script di completamento

- Richiede un valore

### `--help`, `-h`

Visualizza la Guida per il comando specificato. Se non viene fornito alcun comando, visualizzare la Guida per il comando \&lt;info>list\&lt;/info> comando

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumenta la gravità dei messaggi: 1 per l’output normale, 2 per l’output più dettagliato e 3 per il debug

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza (o disattiva — senza ansi) output ANSI

- Non accetta un valore

### `--no-ansi`

Ignora l&#39;opzione &quot;—ansi&quot;

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`, `-n`

Non porre domande interattive

- Predefinito: `false`
- Non accetta un valore


## `completion`

Scarica lo script di completamento della shell

```bash
bin/uct completion [--debug] [--] [<shell>]
```


### `shell`

Se non specificato, verrà utilizzato il tipo di shell (ad esempio &quot;bash&quot;) e il valore dell’env var &quot;$SHELL&quot;


### `--debug`

Suddividi il registro di debug di completamento

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza la Guida per il comando specificato. Se non viene fornito alcun comando, visualizzare la Guida per il comando \&lt;info>list\&lt;/info> comando

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumenta la gravità dei messaggi: 1 per l’output normale, 2 per l’output più dettagliato e 3 per il debug

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza (o disattiva — senza ansi) output ANSI

- Non accetta un valore

### `--no-ansi`

Ignora l&#39;opzione &quot;—ansi&quot;

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`, `-n`

Non porre domande interattive

- Predefinito: `false`
- Non accetta un valore


## `help`

Visualizza la Guida per un comando

```bash
bin/uct help [--format FORMAT] [--raw] [--] [<command_name>]
```


### `command_name`

Nome del comando

- Predefinito: `help`


### `--format`

Il formato di output (txt, xml, json o md)

- Predefinito: `txt`
- Richiede un valore

### `--raw`

Per visualizzare la guida dei comandi raw

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza la Guida per il comando specificato. Se non viene fornito alcun comando, visualizzare la Guida per il comando \&lt;info>list\&lt;/info> comando

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumenta la gravità dei messaggi: 1 per l’output normale, 2 per l’output più dettagliato e 3 per il debug

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza (o disattiva — senza ansi) output ANSI

- Non accetta un valore

### `--no-ansi`

Ignora l&#39;opzione &quot;—ansi&quot;

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`, `-n`

Non porre domande interattive

- Predefinito: `false`
- Non accetta un valore


## `list`

Comandi elenco

```bash
bin/uct list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
```


### `namespace`

Nome dello spazio dei nomi


### `--raw`

Per generare l&#39;elenco dei comandi raw

- Predefinito: `false`
- Non accetta un valore

### `--format`

Il formato di output (txt, xml, json o md)

- Predefinito: `txt`
- Richiede un valore

### `--short`

Per ignorare la descrizione degli argomenti dei comandi

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza la Guida per il comando specificato. Se non viene fornito alcun comando, visualizzare la Guida per il comando \&lt;info>list\&lt;/info> comando

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumenta la gravità dei messaggi: 1 per l’output normale, 2 per l’output più dettagliato e 3 per il debug

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza (o disattiva — senza ansi) output ANSI

- Non accetta un valore

### `--no-ansi`

Ignora l&#39;opzione &quot;—ansi&quot;

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`, `-n`

Non porre domande interattive

- Predefinito: `false`
- Non accetta un valore


## `refactor`

Risolve i problemi che possono essere risolti automaticamente. Il codice nel percorso fornito verrà aggiornato.

```bash
bin/uct refactor <path>
```


### `path`

Percorso per risolvere i problemi in.

- Obbligatorio

### `--help`, `-h`

Visualizza la Guida per il comando specificato. Se non viene fornito alcun comando, visualizzare la Guida per il comando \&lt;info>list\&lt;/info> comando

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumenta la gravità dei messaggi: 1 per l’output normale, 2 per l’output più dettagliato e 3 per il debug

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza (o disattiva — senza ansi) output ANSI

- Non accetta un valore

### `--no-ansi`

Ignora l&#39;opzione &quot;—ansi&quot;

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`, `-n`

Non porre domande interattive

- Predefinito: `false`
- Non accetta un valore


## `core:code:changes`

Lo strumento di compatibilità per l’aggiornamento è uno strumento da riga di comando che controlla un’istanza di Adobe Commerce rispetto a una versione specifica analizzando tutti i moduli non Adobe Commerce installati all’interno. Restituisce un elenco di errori e avvisi ai quali è necessario rispondere prima di eseguire l&#39;aggiornamento a una nuova versione del codice Adobe Commerce.

```bash
bin/uct core:code:changes [-o|--output [OUTPUT]] [--] <dir> [<vanilla-dir>]
```


### `dir`

Directory di installazione di Adobe Commerce.

- Obbligatorio

### `vanilla-dir`

directory di installazione di Adobe Commerce vanilla.


### `--output`, `-o`

Percorso del file in cui verrà esportato l’output (Formato Json)

- Accetta un valore

### `--help`, `-h`

Visualizza la Guida per il comando specificato. Se non viene fornito alcun comando, visualizzare la Guida per il comando \&lt;info>list\&lt;/info> comando

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumenta la gravità dei messaggi: 1 per l’output normale, 2 per l’output più dettagliato e 3 per il debug

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza (o disattiva — senza ansi) output ANSI

- Non accetta un valore

### `--no-ansi`

Ignora l&#39;opzione &quot;—ansi&quot;

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`, `-n`

Non porre domande interattive

- Predefinito: `false`
- Non accetta un valore


## `dbschema:diff`

Consenti di elencare le differenze dello schema di Adobe Commerce DB tra due versioni selezionate.
Versioni disponibili: 2.3.0 | 2.3.1 | 2.3.2 | 2.3.2-p2 | 2.3.3 | 2.3.3-p1 | 2.3.4 | 2.3.4-p1 | 2.3.4-p2 | 2.3.5 | 2,3,5-p1 | 2,3,5-p2 | 2.3.6 | 2.3.6-p1 | 2.3.7 | 2.3.7-p1 | 2.3.7-p2 | 2,3,7-p3 | 2,3,7-p4 | 2.4.0 | 2,4,0-p1 | 2.4.1 | 2.4.1-p1 | 2.4.2 | 2.4.2-p1 | 2.4.2-p2 | 2.4.3 | 2.4.3-p1 | 2.4.3-p2 | 2.4.3-p3 | 2.4.4 | 2.4.4-p1 | 2.4.5 | 2.4.4-p2 | 2,4,5-p1 | 2.4.4-p3 | 2,4,5-p2 | 2.4.6

```bash
bin/uct dbschema:diff <current-version> <target-version>
```


### `current-version`

versione corrente (ad esempio 2.3.2).

- Obbligatorio

### `target-version`

versione di destinazione (ad esempio 2.4.5).

- Obbligatorio

### `--help`, `-h`

Visualizza la Guida per il comando specificato. Se non viene fornito alcun comando, visualizzare la Guida per il comando \&lt;info>list\&lt;/info> comando

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumenta la gravità dei messaggi: 1 per l’output normale, 2 per l’output più dettagliato e 3 per il debug

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza (o disattiva — senza ansi) output ANSI

- Non accetta un valore

### `--no-ansi`

Ignora l&#39;opzione &quot;—ansi&quot;

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`, `-n`

Non porre domande interattive

- Predefinito: `false`
- Non accetta un valore


## `graphql:compare`

Verifica compatibilità schema GraphQL

```bash
bin/uct graphql:compare [-o|--output [OUTPUT]] [--] <schema1> <schema2>
```


### `schema1`

URL dell’endpoint che punta al primo schema di GraphQL.

- Obbligatorio

### `schema2`

URL dell’endpoint che punta al secondo schema di GraphQL.

- Obbligatorio

### `--output`, `-o`

Percorso del file in cui verrà esportato l’output (Formato JSON)

- Accetta un valore

### `--help`, `-h`

Visualizza la Guida per il comando specificato. Se non viene fornito alcun comando, visualizzare la Guida per il comando \&lt;info>list\&lt;/info> comando

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumenta la gravità dei messaggi: 1 per l’output normale, 2 per l’output più dettagliato e 3 per il debug

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza (o disattiva — senza ansi) output ANSI

- Non accetta un valore

### `--no-ansi`

Ignora l&#39;opzione &quot;—ansi&quot;

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`, `-n`

Non porre domande interattive

- Predefinito: `false`
- Non accetta un valore


## `upgrade:check`

Upgrade Compatibility Tool è uno strumento da riga di comando che controlla un’istanza personalizzata di Adobe Commerce rispetto a una versione specifica analizzando tutti i moduli installati al suo interno. Restituisce un elenco di errori e avvisi che devono essere corretti prima dell’aggiornamento alla versione più recente di Adobe Commerce.

```bash
bin/uct upgrade:check [-a|--current-version [CURRENT-VERSION]] [-c|--coming-version [COMING-VERSION]] [--json-output-path [JSON-OUTPUT-PATH]] [--html-output-path [HTML-OUTPUT-PATH]] [--min-issue-level [MIN-ISSUE-LEVEL]] [-i|--ignore-current-version-compatibility-issues] [--context CONTEXT] [--] <dir>
```


### `dir`

Directory di installazione di Adobe Commerce.

- Obbligatorio

### `--current-version`, `-a`

Se omesso, verrà utilizzata la versione corrente di Adobe Commerce, ovvero la versione dell’installazione di Adobe Commerce.

- Accetta un valore

### `--coming-version`, `-c`

Versione Adobe Commerce di destinazione; se omessa, verrà utilizzata l’ultima versione rilasciata di Adobe Commerce. Versioni disponibili di Adobe Commerce: 2.3.0 \| 2.3.1 \| 2.3.2 \| 2.3.2-p2 \| 2.3.3 \| 2.3.3-p1 \| 2.3.4 \| 2.3.4-p1 \| 2.3.4-p2 \| 2.3.5 \| 2.3.5-p1 \| 2.3.5-p2 \| 2.3.6 \| 2.3.6-p1 \| 2.3.7 \| 2.3.7-p1 \| 2.3.7-p2 | 2.3.7-p3 \| 2.3.7-p4 \| 2.4.0 \| 2.4.0-p1 \| 2.4.1 \| 2.4.1-p1 \| 2.4.2 \|| 2.4.2-p1 \| 2.4.2-p2 \| 2.4.3 \| 2.4.3-p1 \| 2.4.3-p2 \| 2.4.3-p3 \| 2.4.4 \| 2.4.4-p1 \| 2.4.5 \| 2.4.4 2 \| 2,4,5-p1 \| 2,4,4-p3 \| 2,4,5-p2 \| 2,4,6

- Accetta un valore

### `--json-output-path`

Percorso del file in cui verrà esportato l’output in formato JSON

- Accetta un valore

### `--html-output-path`

Percorso del file in cui verrà esportato l’output in formato HTML

- Accetta un valore

### `--min-issue-level`

Livello di problema minimo da visualizzare nel rapporto (avviso, errore o critico).

- Predefinito: `warning`
- Accetta un valore

### `--ignore-current-version-compatibility-issues`, `-i`

Ignora problemi comuni per la versione corrente e quella in arrivo

- Predefinito: `false`
- Non accetta un valore

### `--context`

Contesto di esecuzione. Questa opzione è a scopo di integrazione e non influisce sul risultato dell’esecuzione.

- Richiede un valore

### `--help`, `-h`

Visualizza la Guida per il comando specificato. Se non viene fornito alcun comando, visualizzare la Guida per il comando \&lt;info>list\&lt;/info> comando

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumenta la gravità dei messaggi: 1 per l’output normale, 2 per l’output più dettagliato e 3 per il debug

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza (o disattiva — senza ansi) output ANSI

- Non accetta un valore

### `--no-ansi`

Ignora l&#39;opzione &quot;—ansi&quot;

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`, `-n`

Non porre domande interattive

- Predefinito: `false`
- Non accetta un valore

