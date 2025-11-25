---
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '993'
ht-degree: 1%

---
# bin/uct

<!-- All the assigned and captured content is used in the included template -->



<!-- The template to render with above values -->
**Versione**: 3.0.25

Questo riferimento contiene 9 comandi disponibili tramite lo strumento della riga di comando `bin/uct`.
L&#39;elenco iniziale viene generato automaticamente utilizzando il comando `bin/uct list` in Adobe Commerce.

## Generale

Ulteriori informazioni sullo strumento in [Panoramica](/help/upgrade/upgrade-compatibility-tool/overview.md).

>[!NOTE]
>
>Il comando `composer update` non funziona per l&#39;aggiornamento di questo strumento. È necessario [scaricare e installare la versione più recente](/help/upgrade/upgrade-compatibility-tool/run.md).

Questa documentazione di riferimento viene generata dal codice sorgente dell’applicazione. Per modificare la documentazione, è necessario aprire una richiesta di pull per il comando corrispondente nell&#39;archivio [codebase](https://github.com/magento) pertinente. Per ulteriori informazioni, consulta [Contributi codice](https://developer.adobe.com/commerce/contributor/guides/code-contributions).

### Opzioni globali

#### `--help`, `-h`

Visualizza la Guida per il comando specificato. Se non viene assegnato alcun comando, visualizzare la Guida per il comando list

- Predefinito: `false`
- Non accetta un valore

#### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore

#### `--verbose`, `-v|-vv|-vvv`

Aumenta la gravità dei messaggi: 1 per l’output normale, 2 per l’output più dettagliato e 3 per il debug

- Predefinito: `false`
- Non accetta un valore

#### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

#### `--ansi`

Forza (o disattiva — senza ansi) output ANSI

- Non accetta un valore

#### `--no-ansi`

Ignora l&#39;opzione &quot;—ansi&quot;

- Predefinito: `false`
- Non accetta un valore

#### `--no-interaction`, `-n`

Non porre domande interattive

- Predefinito: `false`
- Non accetta un valore


## `_complete`

```bash
bin/uct _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-a|--api-version API-VERSION] [-S|--symfony SYMFONY]
```

Comando interno per fornire suggerimenti per il completamento della shell

### Opzioni

Per le opzioni globali, vedi [Opzioni globali](#global-options).

#### `--shell`, `-s`

Tipo di conchiglia (&quot;bash&quot;, &quot;fish&quot;, &quot;zsh&quot;)

- Richiede un valore

#### `--input`, `-i`

Array di token di input (ad esempio, COMP_WORDS o argv)

- Predefinito: `[]`
- Richiede un valore

#### `--current`, `-c`

Indice dell&#39;array &quot;input&quot; in cui si trova il cursore (ad esempio, COMP_CWORD)

- Richiede un valore

#### `--api-version`, `-a`

Versione API dello script di completamento

- Richiede un valore

#### `--symfony`, `-S`

obsoleto

- Richiede un valore


## `completion`

```bash
bin/uct completion [--debug] [--] [<shell>]
```

Scarica lo script di completamento della shell

```
The completion command dumps the shell completion script required
to use shell autocompletion (currently, bash, fish, zsh completion are supported).

Static installation
-------------------

Dump the script to a global completion file and restart your shell:

    uct/bin/uct completion  | sudo tee /etc/bash_completion.d/uct

Or dump the script to a local file and source it:

    uct/bin/uct completion  > completion.sh

    # source the file whenever you use the project
    source completion.sh

    # or add this line at the end of your "~/.bashrc" file:
    source /path/to/completion.sh

Dynamic installation
--------------------

Add this to the end of your shell configuration file (e.g. "~/.bashrc"):

    eval "$(/var/jenkins/workspace/gendocs-uct-cli/uct/bin/uct completion )"
```

### Argomenti

#### `shell`

Se non specificato, verrà utilizzato il tipo di shell (ad esempio &quot;bash&quot;) e il valore dell’env var &quot;$SHELL&quot;

### Opzioni

Per le opzioni globali, vedi [Opzioni globali](#global-options).

#### `--debug`

Suddividi il registro di debug di completamento

- Predefinito: `false`
- Non accetta un valore


## `help`

```bash
bin/uct help [--format FORMAT] [--raw] [--] [<command_name>]
```

Visualizza la Guida per un comando

```
The help command displays help for a given command:

  uct/bin/uct help list

You can also output the help in other formats by using the --format option:

  uct/bin/uct help --format=xml list

To display the list of available commands, please use the list command.
```

### Argomenti

#### `command_name`

Nome del comando

- Predefinito: `help`

### Opzioni

Per le opzioni globali, vedi [Opzioni globali](#global-options).

#### `--format`

Il formato di output (txt, xml, json o md)

- Predefinito: `txt`
- Richiede un valore

#### `--raw`

Per visualizzare la guida dei comandi raw

- Predefinito: `false`
- Non accetta un valore


## `list`

```bash
bin/uct list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
```

Comandi elenco

```
The list command lists all commands:

  uct/bin/uct list

You can also display the commands for a specific namespace:

  uct/bin/uct list test

You can also output the information in other formats by using the --format option:

  uct/bin/uct list --format=xml

It's also possible to get raw list of commands (useful for embedding command runner):

  uct/bin/uct list --raw
```

### Argomenti

#### `namespace`

Nome dello spazio dei nomi

### Opzioni

Per le opzioni globali, vedi [Opzioni globali](#global-options).

#### `--raw`

Per generare l&#39;elenco dei comandi raw

- Predefinito: `false`
- Non accetta un valore

#### `--format`

Il formato di output (txt, xml, json o md)

- Predefinito: `txt`
- Richiede un valore

#### `--short`

Per ignorare la descrizione degli argomenti dei comandi

- Predefinito: `false`
- Non accetta un valore


## `refactor`

```bash
bin/uct refactor <path>
```

Risolve i problemi che possono essere risolti automaticamente. Il codice nel percorso fornito verrà aggiornato.

### Argomenti

#### `path`

Percorso per risolvere i problemi in.

- Obbligatorio

### Opzioni

Per le opzioni globali, vedi [Opzioni globali](#global-options).


## `core:code:changes`

```bash
bin/uct core:code:changes [-o|--output [OUTPUT]] [--] <dir> [<vanilla-dir>]
```

Lo strumento di compatibilità per l’aggiornamento è uno strumento da riga di comando che controlla un’istanza di Adobe Commerce rispetto a una versione specifica analizzando tutti i moduli non Adobe Commerce installati all’interno. Restituisce un elenco di errori e avvisi ai quali è necessario rispondere prima di eseguire l&#39;aggiornamento a una nuova versione del codice Adobe Commerce.

### Argomenti

#### `dir`

Directory di installazione di Adobe Commerce.

- Obbligatorio


#### `vanilla-dir`

directory di installazione di Adobe Commerce vanilla.

### Opzioni

Per le opzioni globali, vedi [Opzioni globali](#global-options).

#### `--output`, `-o`

Percorso del file in cui verrà esportato l’output (Formato Json)

- Accetta un valore


## `dbschema:diff`

```bash
bin/uct dbschema:diff <current-version> <target-version>
```

Consenti di elencare le differenze dello schema di Adobe Commerce DB tra due versioni selezionate. Versioni disponibili: 2.3.0 | 2.3.1. | 2.3.2. | 2.3.2-p2 | 2.3.3. | 2.3.3-p1 | 2.3.4. | 2.3.4-p1 | 2.3.4-p2 | 2.3.5. | 2.3.5-p1 | 2.3.5-p2 | 2.3.6. | 2.3.6-p1 | 2.3.7. | 2.3.7-p1 | 2.3.7-p2 | 2.3.7-p3 | 2.3.7-p4 | 2.4.0 | 2,4,0-p1 | 2.4.1. | 2.4.1-p1 | 2.4.2. | 2.4.2-p1 | 2.4.2-p2 | 2.4.3. | 2.4.3-p1 | 2.4.3-p2 | 2.4.3-p3 | 2.4.4. | 2.4.4-p1 | 2.4.5. | 2.4.4-p2 | 2,4,5-p1 | 2.4.4-p3 | 2.4.4-p4 | 2.4.4-p5 | 2.4.5-p2 | 2.4.5-p3 | 2,4,5-p4 | 2.4.6. | 2.4.6-p1 | 2.4.6-p2 | 2.4.7-beta1 | 2.4.4-p6 | 2,4,5-p5 | 2.4.6-p3 | 2.4.7-beta2 | 2.4.4-p7 | 2,4,5-p6 | 2,4,6-p4 | 2.4.7-beta3 | 2.4.7. | 2,4,6-p5 | 2,4,5-p7 | 2.4.4-p8 | 2.4.4-p9 | 2.4.5-p8 | 2,4,6-p6 | 2.4.7-p1 | 2.4.4-p10 | 2,4,5-p9 | 2,4,6-p7 | 2.4.7-p2 | 2.4.4-p11 | 2.4.5-p10 | 2.4.6-p8 | 2.4.7-p3 | 2.4.8-beta1 | 2.4.4-p12 | 2.4.5-p11 | 2.4.6-p9 | 2,4,7-p4 | 2.4.8-beta2 | 2.4.4-p13 | 2.4.5-p12 | 2.4.6-p10 | 2,4,7-p5 | 2.4.8. | 2,4,9-alfa2 | 2.4.8-p2 | 2,4,7-p7 | 2.4.6-p12 | 2.4.5-p14 | 2.4.4-p15 | 2,4,9-alfa1 | 2,4,8-p1 | 2,4,7-p6 | 2.4.6-p11 | 2.4.5-p13 | 2.4.4-p14 | 2,4,9-alfa3 | 2.4.8-p3 | 2.4.7-p8 | 2.4.6-p13 | 2.4.5-p15 | 2.4.4-p16

### Argomenti

#### `current-version`

versione corrente (ad esempio 2.3.2).

- Obbligatorio


#### `target-version`

versione di destinazione (ad esempio 2.4.5).

- Obbligatorio

### Opzioni

Per le opzioni globali, vedi [Opzioni globali](#global-options).


## `graphql:compare`

```bash
bin/uct graphql:compare [-o|--output [OUTPUT]] [--] <schema1> <schema2>
```

Verifica compatibilità schema GraphQL

### Argomenti

#### `schema1`

URL dell’endpoint che punta al primo schema di GraphQL.

- Obbligatorio


#### `schema2`

URL dell’endpoint che punta al secondo schema di GraphQL.

- Obbligatorio

### Opzioni

Per le opzioni globali, vedi [Opzioni globali](#global-options).

#### `--output`, `-o`

Percorso del file in cui verrà esportato l’output (Formato JSON)

- Accetta un valore


## `upgrade:check`

```bash
bin/uct upgrade:check [-a|--current-version [CURRENT-VERSION]] [-c|--coming-version [COMING-VERSION]] [--json-output-path [JSON-OUTPUT-PATH]] [--html-output-path [HTML-OUTPUT-PATH]] [--min-issue-level [MIN-ISSUE-LEVEL]] [-i|--ignore-current-version-compatibility-issues] [--context CONTEXT] [--] <dir>
```

Upgrade Compatibility Tool è uno strumento da riga di comando che controlla un’istanza personalizzata di Adobe Commerce rispetto a una versione specifica analizzando tutti i moduli installati al suo interno. Restituisce un elenco di errori e avvisi che devono essere corretti prima dell’aggiornamento alla versione più recente di Adobe Commerce.

### Argomenti

#### `dir`

Directory di installazione di Adobe Commerce.

- Obbligatorio

### Opzioni

Per le opzioni globali, vedi [Opzioni globali](#global-options).

#### `--current-version`, `-a`

Se omesso, verrà utilizzata la versione corrente di Adobe Commerce, ovvero la versione dell’installazione di Adobe Commerce.

- Accetta un valore

#### `--coming-version`, `-c`

Versione Adobe Commerce di destinazione. Se omessa, verrà utilizzata la versione stabile più recente di Adobe Commerce. Versioni disponibili di Adobe Commerce: 2.3.0 \| 2.3.1 \| 2.3.2 \| 2.3.2-p2 \| 2.3.3 \| 2.3.3-p1 \| 2.3.4 \| 2.3.4-p1 \| 2.3.4-p2 \| 2.3.5 \| 2.3.5-p1 \| 2.3.5-p2 \| 2.3.6 \| 2.3.6-p1 \| 2.3.7 \| 2.3.7-p1 \| 2.3.7-p2 \| 2.3.7-p3 \| 2.3.7-p4 \| 2.4.0 \| 2.4.0-p1 \| 2.4.1 \| 2.4.1-p1 \| 2.4.2 \| 2.4.2-p1 \| 2.4.2-p2 \| 2.4.3 \| 2.4.3-p1 \| 2.4.3-p2 \| 2.4.3-p3 \| 2.4.4 \| 2.4.4-p1 \| 2.4.4-p2 \| 2.4.4-p3 \| 2.4.4-p4 \| 2.4.4-p5 \| 2.4.4-p6 \| 2.4.4-p7 \| 2.4.4-p8 \| 2.4.4-p9 \| 2.4.4-p10 \| 2.4.4-p11 \| 2.4.4-p12 \| 2.4.4-p13 \| 2.4.4-p14 \| 2.4.4-p15 \| 2.4.4-p16 \| 2.4.5 \| 2.4.5-p1 \| 2.4.5-p2 \| 2.4.5-p3 \| 2.4.5-p4 \| 2.4.5-p5 \| 2.4.5-p6 \| 2.4.5-p7 \| 2.4.5-p8 \| 2.4.5-p9 \| 2.4.5-p10 \| 2.4.5-p11 \| 2.4.5-p12 \| 2.4.5-p13 \| 2.4.5-p14 \| 2.4.5-p15 \| 2.4.6 \| 2.4.6-p1 \| 2.4.6-p2 \| 2.4.6-p3 \| 2.4.6-p4 \| 2.4.6-p5 \| 2.4.6-p6 \| 2.4.6-p7 \| 2.4.6-p8 \| 2.4.6-p9 \| 2.4.6-p10 \| 2.4.6-p11 \| 2.4.6-p12 \| 2.4.6-p13 \| 2.4.7-beta1 \| 2.4.7-beta2 \| 2.4.7-beta3 \| 2.4.7 \| 2.4.7-p1 \| 2.4.7-p2 \| 2.4.7-p3 \| 2.4.7-p4 \| 2.4.7-p5 \| 2.4.7-p6 \| 2.4.7-p7 \| 2.4.7-p8 \| 2.4.8-beta1 \| 2.4.8-beta2 \| 2.4.8 \| 2.4.8-p1 \| 2.4.8-p2 \| 2.4.8-p3 \| 2.4.9-alfa1 \| 2.4.9-alfa2 \| 2,4,9-alfa3

- Accetta un valore

#### `--json-output-path`

Percorso del file in cui verrà esportato l’output in formato JSON

- Accetta un valore

#### `--html-output-path`

Percorso del file in cui verrà esportato l’output in formato HTML

- Accetta un valore

#### `--min-issue-level`

Livello di problema minimo da visualizzare nel rapporto (avviso, errore o critico).

- Predefinito: `warning`
- Accetta un valore

#### `--ignore-current-version-compatibility-issues`, `-i`

Ignora problemi comuni per la versione corrente e quella in arrivo

- Predefinito: `false`
- Non accetta un valore

#### `--context`

Contesto di esecuzione. Questa opzione è a scopo di integrazione e non influisce sul risultato dell’esecuzione.

- Richiede un valore

