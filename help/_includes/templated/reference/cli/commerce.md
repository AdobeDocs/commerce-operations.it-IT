---
source-git-commit: 27e7a262fd1d8092045f5ebe2f88caaec37a6b0d
workflow-type: tm+mt
source-wordcount: '29783'
ht-degree: 0%

---
# magento-cloud (Adobe Commerce su infrastruttura cloud)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**Versione**: 1,42,0

Questo riferimento contiene 134 comandi disponibili tramite `magento-cloud` strumento da riga di comando.
L’elenco iniziale viene generato automaticamente utilizzando `magento-cloud list` nell&#39;edizione.

>[!NOTE]
>
>Questo riferimento viene generato dalla base di codice dell&#39;applicazione. Per modificare il contenuto, puoi aggiornare il codice sorgente per l’implementazione del comando corrispondente in [codebase](https://github.com/magento) e inviare le modifiche per la revisione. Un altro modo consiste nel _Inviaci feedback_ (trovi il collegamento in alto a destra). Per le linee guida sui contributi, consulta [Contributi codice](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `_completion`

gancio di completamento BASH.

```bash
_completion [-g|--generate-hook] [-p|--program PROGRAM] [-m|--multiple] [--shell-type [SHELL-TYPE]]
```

### `--generate-hook`, `-g`

Genera codice BASH che imposta il completamento per questa applicazione.

- Predefinito: `false`
- Non accetta un valore

### `--program`, `-p`

Nome del programma che deve attivare il completamento &lt;comment>: il valore predefinito è il percorso assoluto dell&#39;applicazione.&lt;/comment>.

- Richiede un valore

### `--multiple`, `-m`

L&#39;hook generato può essere utilizzato per più applicazioni.

- Predefinito: `false`
- Non accetta un valore

### `--shell-type`

Impostate il tipo di shell (zsh o bash). In caso contrario, viene determinato automaticamente.

- Accetta un valore


## `bot`

Magento Cloud Bot

```bash
magento-cloud bot [--party] [--parrot]
```

### `--party`



- Predefinito: `false`
- Non accetta un valore

### `--parrot`



- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `clear-cache`

Cancellare la cache CLI

```bash
magento-cloud clear-cache
```


```bash
clearcache
```


```bash
cc
```

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `decode`

Decodificare una stringa codificata come MAGENTO_CLOUD_VARIABLES

```bash
magento-cloud decode [-P|--property PROPERTY] [--] <value>
```


### `value`

Valore della variabile da decodificare

- Obbligatorio

### `--property`, `-P`

Proprietà da visualizzare all’interno della variabile

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `docs`

Apri la documentazione online

```bash
magento-cloud docs [--browser BROWSER] [--pipe] [--] [<search>]...
```


### `search`

Cerca termini

- Predefinito: `[]`

- Array

### `--browser`

Browser da utilizzare per aprire l’URL. Impostate 0 su none.

- Richiede un valore

### `--pipe`

Invia l’URL a stdout.

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `help`

Visualizza la Guida per un comando

```bash
magento-cloud help [--format FORMAT] [--raw] [--] [<command_name>]
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

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `legacy-migrate`

Migrare dalla struttura di file legacy

```bash
magento-cloud legacy-migrate [--no-backup]
```

### `--no-backup`

Non creare un backup del progetto.

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `list`

Elenca i comandi

```bash
magento-cloud list [--raw] [--format FORMAT] [--all] [--] [<namespace>]
```


### `command`

Comando da eseguire

- Obbligatorio

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

### `--all`

Mostra tutti i comandi, inclusi quelli nascosti

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `multi`

Eseguire un comando su più progetti

```bash
magento-cloud multi [-p|--projects PROJECTS] [--continue] [--sort SORT] [--reverse] [--] <cmd> (<cmd>)...
```


### `cmd`

Comando da eseguire

- Predefinito: `[]`

- Obbligatorio
- Array

### `--projects`, `-p`

Elenco di ID progetto, separati da virgole e/o spazi

- Richiede un valore

### `--continue`

Continua l&#39;esecuzione dei comandi anche in caso di eccezione

- Predefinito: `false`
- Non accetta un valore

### `--sort`

Proprietà in base alla quale ordinare l&#39;elenco delle opzioni di progetto

- Predefinito: `title`
- Richiede un valore

### `--reverse`

Inverti l&#39;ordine delle opzioni di progetto

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `web`

Aprire l’interfaccia web

```bash
magento-cloud web [--browser BROWSER] [--pipe] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```

### `--browser`

Browser da utilizzare per aprire l’URL. Impostate 0 su none.

- Richiede un valore

### `--pipe`

Invia l’URL a stdout.

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `welcome`

Benvenuti in Magento Cloud

```bash
magento-cloud welcome
```

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `winky`



```bash
magento-cloud winky
```

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `activity:cancel`

Annullare un’attività

```bash
magento-cloud activity:cancel [--type TYPE] [--exclude-type EXCLUDE-TYPE] [-a|--all] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<id>]
```


### `id`

L’ID attività. Viene impostata automaticamente sull&#39;attività annullabile più recente.


### `--type`

Filtra per tipo (quando selezioni un’attività predefinita). Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti. Il carattere % può essere utilizzato come carattere jolly per il tipo, ad esempio &#39;%var%&#39; per selezionare attività correlate alla variabile.

- Predefinito: `[]`
- Richiede un valore

### `--exclude-type`

Escludi per tipo (quando selezioni un’attività predefinita). Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti. Il carattere % può essere utilizzato come carattere jolly per escludere i tipi.

- Predefinito: `[]`
- Richiede un valore

### `--all`, `-a`

Controlla le attività recenti in tutti gli ambienti (quando selezioni un’attività predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `activity:get`

Visualizzare informazioni dettagliate su una singola attività

```bash
magento-cloud activity:get [-P|--property PROPERTY] [--type TYPE] [--exclude-type EXCLUDE-TYPE] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<id>]
```


### `id`

L’ID attività. Viene impostata automaticamente l&#39;attività più recente.


### `--property`, `-P`

Proprietà da visualizzare

- Richiede un valore

### `--type`

Filtra per tipo (quando selezioni un’attività predefinita). Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti. Il carattere % può essere utilizzato come carattere jolly per il tipo, ad esempio &#39;%var%&#39; per selezionare attività correlate alla variabile.

- Predefinito: `[]`
- Richiede un valore

### `--exclude-type`

Escludi per tipo (quando selezioni un’attività predefinita). Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti. Il carattere % può essere utilizzato come carattere jolly per escludere i tipi.

- Predefinito: `[]`
- Richiede un valore

### `--state`

Filtra per stato (quando si seleziona un’attività predefinita): in_progress, pending, complete, o annullato. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--result`

Filtra per risultato (quando si seleziona un’attività predefinita): operazione riuscita o non riuscita

- Richiede un valore

### `--incomplete`, `-i`

Includi solo le attività incomplete (quando si seleziona un’attività predefinita). Questa è una scorciatoia per &lt;info>—state=in_progress,in sospeso&lt;/info>

- Predefinito: `false`
- Non accetta un valore

### `--all`, `-a`

Controlla le attività recenti in tutti gli ambienti (quando selezioni un’attività predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--format`

Il formato di output: tabella, csv, tsv o normale

- Predefinito: `table`
- Richiede un valore

### `--columns`, `-c`

Colonne da visualizzare. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non generare l’intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--date-fmt`

Il formato data (come stringa di formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `activity:list`

Ottenere un elenco delle attività per un ambiente o un progetto

```bash
magento-cloud activity:list [-t|--type TYPE] [-x|--exclude-type EXCLUDE-TYPE] [--limit LIMIT] [--start START] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```


```bash
activities
```


```bash
act
```

### `--type`, `-t`

Filtra le attività per tipo Se un elenco viene fornito come un singolo valore (ad esempio &quot;a,b,c&quot;) verrà suddiviso da virgole e/o spazi vuoti. Il carattere % può essere utilizzato come carattere jolly per il tipo, ad esempio &#39;%var%&#39; per selezionare attività correlate alla variabile.

- Predefinito: `[]`
- Richiede un valore

### `--exclude-type`, `-x`

Escludi attività per tipo. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti. Il carattere % può essere utilizzato come carattere jolly per escludere i tipi.

- Predefinito: `[]`
- Richiede un valore

### `--limit`

Limita il numero di risultati visualizzati

- Predefinito: `10`
- Richiede un valore

### `--start`

Verranno elencate solo le attività create prima di questa data

- Richiede un valore

### `--state`

Filtra attività per stato: in_corso, in sospeso, completo o annullato. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--result`

Filtra attività per risultato: operazione riuscita o non riuscita

- Richiede un valore

### `--incomplete`, `-i`

Elencare solo le attività incomplete

- Predefinito: `false`
- Non accetta un valore

### `--all`, `-a`

Elencare attività in tutti gli ambienti

- Predefinito: `false`
- Non accetta un valore

### `--format`

Il formato di output: tabella, csv, tsv o normale

- Predefinito: `table`
- Richiede un valore

### `--columns`, `-c`

Colonne da visualizzare. Colonne disponibili: id*, creato*, descrizione*, avanzamento*, stato*, risultato*, completato, ambienti, tipo (* = colonne predefinite). Il carattere &quot;+&quot; può essere utilizzato come segnaposto per le colonne predefinite. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non generare l’intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--date-fmt`

Il formato data (come stringa di formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `activity:log`

Visualizzare il registro di un’attività

```bash
magento-cloud activity:log [--refresh REFRESH] [-t|--timestamps] [--type TYPE] [--exclude-type EXCLUDE-TYPE] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<id>]
```


### `id`

L’ID attività. Viene impostata automaticamente l&#39;attività più recente.


### `--refresh`

Intervallo di aggiornamento attività (secondi). Impostate questo valore su 0 per disattivare l&#39;aggiornamento.

- Predefinito: `3`
- Richiede un valore

### `--timestamps`, `-t`

Visualizza un timestamp accanto a ogni messaggio

- Predefinito: `false`
- Non accetta un valore

### `--type`

Filtra per tipo (quando selezioni un’attività predefinita). Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti. Il carattere % può essere utilizzato come carattere jolly per il tipo, ad esempio &#39;%var%&#39; per selezionare attività correlate alla variabile.

- Predefinito: `[]`
- Richiede un valore

### `--exclude-type`

Escludi per tipo (quando selezioni un’attività predefinita). Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti. Il carattere % può essere utilizzato come carattere jolly per escludere i tipi.

- Predefinito: `[]`
- Richiede un valore

### `--state`

Filtra per stato (quando si seleziona un’attività predefinita): in_progress, pending, complete, o annullato. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--result`

Filtra per risultato (quando si seleziona un’attività predefinita): operazione riuscita o non riuscita

- Richiede un valore

### `--incomplete`, `-i`

Includi solo le attività incomplete (quando si seleziona un’attività predefinita). Questa è una scorciatoia per &lt;info>—state=in_progress,in sospeso&lt;/info>

- Predefinito: `false`
- Non accetta un valore

### `--all`, `-a`

Controlla le attività recenti in tutti gli ambienti (quando selezioni un’attività predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--date-fmt`

Il formato data (come stringa di formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `api:curl`

Eseguire una richiesta cURL autenticata nell’API Magento Cloud

```bash
magento-cloud api:curl [-X|--request REQUEST] [-d|--data DATA] [--json JSON] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-f|--fail] [-H|--header HEADER] [--] [<path>]
```


### `path`

Percorso API


### `--request`, `-X`

Metodo di richiesta da utilizzare

- Richiede un valore

### `--data`, `-d`

Dati da inviare

- Richiede un valore

### `--json`

Dati JSON da inviare

- Richiede un valore

### `--include`, `-i`

Includi intestazioni nell&#39;output

- Predefinito: `false`
- Non accetta un valore

### `--head`, `-I`

Recupera solo intestazioni

- Predefinito: `false`
- Non accetta un valore

### `--disable-compression`

Non utilizzare il flag curl - compresso

- Predefinito: `false`
- Non accetta un valore

### `--enable-glob`

Abilita globbing curl (rimuovi il flag —globoff)

- Predefinito: `false`
- Non accetta un valore

### `--fail`, `-f`

Non riuscito senza output in una risposta di errore

- Predefinito: `false`
- Non accetta un valore

### `--header`, `-H`

Intestazioni aggiuntive

- Predefinito: `[]`
- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `app:config-get`

Visualizzare la configurazione di un’app

```bash
magento-cloud app:config-get [-P|--property PROPERTY] [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE]
```

### `--property`, `-P`

Proprietà di configurazione da visualizzare

- Richiede un valore

### `--refresh`

Se aggiornare la cache

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--identity-file`, `-i`

[Opzione obsoleta, non più utilizzata]

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `app:list`

Elencare le app nel progetto

```bash
magento-cloud apps [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```


```bash
apps
```

### `--refresh`

Se aggiornare la cache

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--format`

Il formato di output: tabella, csv, tsv o normale

- Predefinito: `table`
- Richiede un valore

### `--columns`, `-c`

Colonne da visualizzare. Colonne disponibili: nome*, tipo*, disco, percorso, dimensione (* = colonne predefinite). Il carattere &quot;+&quot; può essere utilizzato come segnaposto per le colonne predefinite. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non generare l’intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `auth:api-token-login`

Accedi a Magento Cloud utilizzando un token API

```bash
magento-cloud auth:api-token-login
```

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `auth:browser-login`

Accedi a Magento Cloud tramite un browser

```bash
magento-cloud login [-f|--force] [--browser BROWSER] [--pipe]
```


```bash
login
```

### `--force`, `-f`

Accedi di nuovo, anche se hai già effettuato l’accesso

- Predefinito: `false`
- Non accetta un valore

### `--browser`

Browser da utilizzare per aprire l’URL. Impostate 0 su none.

- Richiede un valore

### `--pipe`

Invia l’URL a stdout.

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `auth:info`

Visualizzare le informazioni sull&#39;account

```bash
magento-cloud auth:info [--no-auto-login] [-P|--property PROPERTY] [--refresh] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--] [<property>]
```


### `property`

Proprietà account da visualizzare


### `--no-auto-login`

Ignora l&#39;accesso automatico. Se non si è connessi, non verrà generato nulla e il codice di uscita sarà 0, supponendo che non vi siano altri errori.

- Predefinito: `false`
- Non accetta un valore

### `--property`, `-P`

Proprietà dell&#39;account da visualizzare (sintassi alternativa)

- Richiede un valore

### `--refresh`

Se aggiornare la cache

- Predefinito: `false`
- Non accetta un valore

### `--format`

Il formato di output: tabella, csv, tsv o normale

- Predefinito: `table`
- Richiede un valore

### `--columns`, `-c`

Colonne da visualizzare. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non generare l’intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `auth:logout`

Disconnetti da Magento Cloud

```bash
magento-cloud logout [-a|--all] [--other]
```


```bash
logout
```

### `--all`, `-a`

Disconnetti da tutte le sessioni locali

- Predefinito: `false`
- Non accetta un valore

### `--other`

Disconnetti da altre sessioni locali

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `auth:password-login`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLETO ]&lt;/> Accedere a Magento Cloud utilizzando un nome utente e una password

```bash
magento-cloud auth:password-login
```


```bash
auth:login
```

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `auth:token`

Ottenere un token di accesso OAuth 2 per le richieste alle API Magento Cloud

```bash
magento-cloud auth:token [-H|--header] [-W|--no-warn]
```

### `--header`, `-H`

Aggiungi al token il prefisso &quot;Authorization: Bearer&quot; per creare un’intestazione RFC 6750

- Predefinito: `false`
- Non accetta un valore

### `--no-warn`, `-W`

Eliminare l&#39;avviso stampato per impostazione predefinita in stderr. Questa opzione è da preferirsi al reindirizzamento dello stderr, in quanto nasconderebbe altri messaggi potenzialmente utili.

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `blackfire:setup`

Configurare l’integrazione Blackfire.io per il progetto

```bash
magento-cloud blackfire:setup [--server_id SERVER_ID] [--server_token SERVER_TOKEN] [-p|--project PROJECT] [-W|--no-wait] [--wait]
```

### `--server_id`

ID server

- Richiede un valore

### `--server_token`

Token del server

- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendere il completamento dell&#39;operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `blue-green:conclude`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ ALFA ]&lt;/> Concludere una distribuzione blu/verde

```bash
magento-cloud blue-green:conclude [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `blue-green:deploy`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ ALFA ]&lt;/> Eseguire una distribuzione blu/verde

```bash
magento-cloud blue-green:deploy [--routing-percentage ROUTING-PERCENTAGE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```

### `--routing-percentage`

Imposta la percentuale di distribuzione della versione più recente

- Predefinito: `100`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `blue-green:enable`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ ALFA ]&lt;/> Abilitare le distribuzioni blu/verde

```bash
magento-cloud blue-green:enable [-%|--routing-percentage ROUTING-PERCENTAGE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```

### `--routing-percentage`, `-%`

Imposta la percentuale di distribuzione della versione più recente

- Predefinito: `100`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `certificate:add`

Aggiungere un certificato SSL al progetto

```bash
magento-cloud certificate:add [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [-W|--no-wait] [--wait]
```

### `--cert`

Percorso del file di certificato

- Richiede un valore

### `--key`

Percorso del file della chiave privata del certificato

- Richiede un valore

### `--chain`

Percorso del file della catena di certificati

- Predefinito: `[]`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendere il completamento dell&#39;operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `certificate:delete`

Eliminare un certificato dal progetto

```bash
magento-cloud certificate:delete [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <id>
```


### `id`

ID del certificato (o il suo inizio)

- Obbligatorio

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendere il completamento dell&#39;operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `certificate:get`

Visualizzare un certificato

```bash
magento-cloud certificate:get [-P|--property PROPERTY] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--] <id>
```


### `id`

ID del certificato (o il suo inizio)

- Obbligatorio

### `--property`, `-P`

Proprietà del certificato da visualizzare

- Richiede un valore

### `--date-fmt`

Il formato data (come stringa di formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `certificate:list`

Elencare certificati di progetto

```bash
magento-cloud certificate:list [--domain DOMAIN] [--exclude-domain EXCLUDE-DOMAIN] [--issuer ISSUER] [--only-auto] [--no-auto] [--ignore-expiry] [--only-expired] [--no-expired] [--pipe-domains] [--date-fmt DATE-FMT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT]
```


```bash
certificates
```


```bash
certs
```

### `--domain`

Filtra per nome di dominio (ricerca senza distinzione tra maiuscole e minuscole)

- Richiede un valore

### `--exclude-domain`

Escludi certificati, corrispondenza per nome di dominio (ricerca senza distinzione maiuscole/minuscole)

- Richiede un valore

### `--issuer`

Filtra per emittente

- Richiede un valore

### `--only-auto`

Mostra solo certificati con provisioning automatico

- Predefinito: `false`
- Non accetta un valore

### `--no-auto`

Mostra solo i certificati aggiunti manualmente

- Predefinito: `false`
- Non accetta un valore

### `--ignore-expiry`

Mostra certificati scaduti e non scaduti

- Predefinito: `false`
- Non accetta un valore

### `--only-expired`

Mostra solo certificati scaduti

- Predefinito: `false`
- Non accetta un valore

### `--no-expired`

Mostra solo certificati non scaduti (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--pipe-domains`

Restituisce solo un elenco di nomi di dominio coperti dai certificati

- Predefinito: `false`
- Non accetta un valore

### `--date-fmt`

Il formato data (come stringa di formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--format`

Il formato di output: tabella, csv, tsv o normale

- Predefinito: `table`
- Richiede un valore

### `--columns`, `-c`

Colonne da visualizzare. Colonne disponibili: creato, domini, scadenza, ID, emittente. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non generare l’intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `commit:get`

Mostra dettagli commit

```bash
magento-cloud commit:get [-P|--property PROPERTY] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--date-fmt DATE-FMT] [--] [<commit>]
```


### `commit`

Il commit SHA. Questo può anche accettare suffissi &quot;HEAD&quot; e accento circonflesso (^) o tilde (~) per commit principali.

- Predefinito: `HEAD`


### `--property`, `-P`

Proprietà commit da visualizzare.

- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--date-fmt`

Il formato data (come stringa di formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--format`

OBSOLETO

- Richiede un valore

### `--columns`

OBSOLETO

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

OBSOLETO

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `commit:list`

Elenca commit

```bash
magento-cloud commits [--limit LIMIT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<commit>]
```


```bash
commits
```


### `commit`

Il commit Git iniziale SHA. Questo può anche accettare suffissi &quot;HEAD&quot; e accento circonflesso (^) o tilde (~) per commit principali.


### `--limit`

Numero di commit da visualizzare.

- Predefinito: `10`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--format`

Il formato di output: tabella, csv, tsv o normale

- Predefinito: `table`
- Richiede un valore

### `--columns`, `-c`

Colonne da visualizzare. Colonne disponibili: author, date, sha, summary. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non generare l’intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--date-fmt`

Il formato data (come stringa di formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `db:dump`

Creare un dump locale del database remoto

```bash
magento-cloud db:dump [--schema SCHEMA] [-f|--file FILE] [-d|--directory DIRECTORY] [-z|--gzip] [-t|--timestamp] [-o|--stdout] [--table TABLE] [--exclude-table EXCLUDE-TABLE] [--schema-only] [--charset CHARSET] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE]
```


```bash
sql-dump
```


```bash
environment:sql-dump
```

### `--schema`

Schema da scaricare. Ometti di utilizzare lo schema predefinito (in genere &quot;main&quot;).

- Richiede un valore

### `--file`, `-f`

Un nome file personalizzato per l’immagine

- Richiede un valore

### `--directory`, `-d`

Una directory personalizzata per il dump

- Richiede un valore

### `--gzip`, `-z`

Comprimi l’immagine utilizzando gzip

- Predefinito: `false`
- Non accetta un valore

### `--timestamp`, `-t`

Aggiungi una marca temporale al nome del file di dump

- Predefinito: `false`
- Non accetta un valore

### `--stdout`, `-o`

Output in STDOUT anziché in un file

- Predefinito: `false`
- Non accetta un valore

### `--table`

Tabelle da includere

- Predefinito: `[]`
- Richiede un valore

### `--exclude-table`

Tabelle da escludere

- Predefinito: `[]`
- Richiede un valore

### `--schema-only`

Esegui il dump solo degli schemi, nessun dato

- Predefinito: `false`
- Non accetta un valore

### `--charset`

Codifica del set di caratteri per l’immagine

- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--relationship`, `-r`

Relazione di servizio da utilizzare

- Richiede un valore

### `--identity-file`, `-i`

Un’identità SSH (chiave privata) da utilizzare

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `db:size`

Stimare l&#39;utilizzo del disco di un database

```bash
magento-cloud db:size [-B|--bytes] [-C|--cleanup] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-i|--identity-file IDENTITY-FILE]
```

### `--bytes`, `-B`

Mostra dimensioni in byte.

- Predefinito: `false`
- Non accetta un valore

### `--cleanup`, `-C`

Controlla se le tabelle possono essere pulite e mostra i consigli (solo InnoDb).

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--relationship`, `-r`

Relazione di servizio da utilizzare

- Richiede un valore

### `--format`

Il formato di output: tabella, csv, tsv o normale

- Predefinito: `table`
- Richiede un valore

### `--columns`, `-c`

Colonne da visualizzare. Colonne disponibili: max, percent_used, used. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non generare l’intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--identity-file`, `-i`

Un’identità SSH (chiave privata) da utilizzare

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `db:sql`

Esegui SQL sul database remoto

```bash
magento-cloud sql [--raw] [--schema SCHEMA] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [--] [<query>]
```


```bash
sql
```


```bash
environment:sql
```


### `query`

Istruzione SQL da eseguire


### `--raw`

Genera output non tabulare

- Predefinito: `false`
- Non accetta un valore

### `--schema`

Schema da utilizzare. Ometti di utilizzare lo schema predefinito (in genere &quot;main&quot;). Passa una stringa vuota per non utilizzare alcuno schema.

- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--relationship`, `-r`

Relazione di servizio da utilizzare

- Richiede un valore

### `--identity-file`, `-i`

Un’identità SSH (chiave privata) da utilizzare

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `domain:add`

Aggiungi un nuovo dominio al progetto

```bash
magento-cloud domain:add [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

Il nome di dominio

- Obbligatorio

### `--cert`

Percorso del file di certificato per questo dominio

- Richiede un valore

### `--key`

Percorso del file della chiave privata per il certificato fornito.

- Richiede un valore

### `--chain`

Percorso del file o dei file della catena di certificati per il certificato fornito

- Predefinito: `[]`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendere il completamento dell&#39;operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `domain:delete`

Eliminare un dominio dal progetto

```bash
magento-cloud domain:delete [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

Il nome di dominio

- Obbligatorio

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendere il completamento dell&#39;operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `domain:get`

Visualizzare informazioni dettagliate per un dominio

```bash
magento-cloud domain:get [-P|--property PROPERTY] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--] [<name>]
```


### `name`

Il nome di dominio


### `--property`, `-P`

Proprietà di dominio da visualizzare

- Richiede un valore

### `--format`

Il formato di output: tabella, csv, tsv o normale

- Predefinito: `table`
- Richiede un valore

### `--columns`, `-c`

Colonne da visualizzare. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non generare l’intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--date-fmt`

Il formato data (come stringa di formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `domain:list`

Ottieni un elenco di tutti i domini

```bash
magento-cloud domains [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT]
```


```bash
domains
```

### `--format`

Il formato di output: tabella, csv, tsv o normale

- Predefinito: `table`
- Richiede un valore

### `--columns`, `-c`

Colonne da visualizzare. Colonne disponibili: name*, ssl*, created_at*, updated_at (* = colonne predefinite). Il carattere &quot;+&quot; può essere utilizzato come segnaposto per le colonne predefinite. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non generare l’intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `domain:update`

Aggiornare un dominio

```bash
magento-cloud domain:update [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

Il nome di dominio

- Obbligatorio

### `--cert`

Percorso del file di certificato per questo dominio

- Richiede un valore

### `--key`

Percorso del file della chiave privata per il certificato fornito.

- Richiede un valore

### `--chain`

Percorso del file o dei file della catena di certificati per il certificato fornito

- Predefinito: `[]`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendere il completamento dell&#39;operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `environment:activate`

Attivare un ambiente

```bash
magento-cloud environment:activate [--parent PARENT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]...
```


### `environment`

Ambiente/i da attivare

- Predefinito: `[]`

- Array

### `--parent`

Imposta un nuovo ambiente principale prima dell’attivazione

- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendere il completamento dell&#39;operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `environment:branch`

Creazione di un ramo di un ambiente

```bash
magento-cloud branch [--title TITLE] [--type TYPE] [--force] [--no-clone-parent] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [-i|--identity-file IDENTITY-FILE] [--] [<id>] [<parent>]
```


```bash
branch
```


### `id`

ID (nome del ramo) del nuovo ambiente


### `parent`

Elemento padre del nuovo ambiente


### `--title`

Titolo del nuovo ambiente

- Richiede un valore

### `--type`

Tipo del nuovo ambiente

- Richiede un valore

### `--force`

Crea il nuovo ambiente anche se il ramo non può essere estratto localmente

- Predefinito: `false`
- Non accetta un valore

### `--no-clone-parent`

Non clonare i dati del ramo principale

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendere il completamento dell&#39;operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--identity-file`, `-i`

Un’identità SSH (chiave privata) da utilizzare

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `environment:checkout`

Estrarre un ambiente

```bash
magento-cloud checkout [-i|--identity-file IDENTITY-FILE] [--] [<id>]
```


```bash
checkout
```


### `id`

ID dell&#39;ambiente da estrarre. Ad esempio: &quot;sprint2&quot;


### `--identity-file`, `-i`

Un’identità SSH (chiave privata) da utilizzare

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `environment:curl`

Eseguire una richiesta cURL autenticata sull’API di un ambiente

```bash
magento-cloud environment:curl [-X|--request REQUEST] [-d|--data DATA] [--json JSON] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-f|--fail] [-H|--header HEADER] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<path>]
```


### `path`

Percorso API


### `--request`, `-X`

Metodo di richiesta da utilizzare

- Richiede un valore

### `--data`, `-d`

Dati da inviare

- Richiede un valore

### `--json`

Dati JSON da inviare

- Richiede un valore

### `--include`, `-i`

Includi intestazioni nell&#39;output

- Predefinito: `false`
- Non accetta un valore

### `--head`, `-I`

Recupera solo intestazioni

- Predefinito: `false`
- Non accetta un valore

### `--disable-compression`

Non utilizzare il flag curl - compresso

- Predefinito: `false`
- Non accetta un valore

### `--enable-glob`

Abilita globbing curl (rimuovi il flag —globoff)

- Predefinito: `false`
- Non accetta un valore

### `--fail`, `-f`

Non riuscito senza output in una risposta di errore

- Predefinito: `false`
- Non accetta un valore

### `--header`, `-H`

Intestazioni aggiuntive

- Predefinito: `[]`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `environment:delete`

Eliminare uno o più ambienti

```bash
magento-cloud environment:delete [--delete-branch] [--no-delete-branch] [--type TYPE] [-t|--only-type ONLY-TYPE] [--exclude EXCLUDE] [--exclude-type EXCLUDE-TYPE] [--inactive] [--merged] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]...
```


```bash
environment:deactivate
```


### `environment`

Ambienti da eliminare. Il carattere % può essere utilizzato come carattere jolly. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`

- Array

### `--delete-branch`

Elimina rami Git (ambienti inattivi)

- Predefinito: `false`
- Non accetta un valore

### `--no-delete-branch`

Non eliminare i rami Git (ambienti inattivi)

- Predefinito: `false`
- Non accetta un valore

### `--type`

Elimina tutti gli ambienti di un tipo (aggiungendo a tutti gli altri selezionati) Se un elenco viene fornito come un singolo valore (ad esempio &quot;a,b,c&quot;) verrà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--only-type`, `-t`

Elimina solo gli ambienti di un tipo specifico Se un elenco viene fornito come un singolo valore (ad esempio &quot;a,b,c&quot;) verrà suddiviso tra virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--exclude`

Ambienti da non eliminare. Il carattere % può essere utilizzato come carattere jolly. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--exclude-type`

Tipi di ambiente di cui non eliminare Se un elenco è fornito come un singolo valore (ad esempio &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--inactive`

Elimina tutti gli ambienti inattivi (aggiungendoli agli altri selezionati)

- Predefinito: `false`
- Non accetta un valore

### `--merged`

Elimina tutti gli ambienti uniti (aggiungendoli a quelli selezionati)

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendere il completamento dell&#39;operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `environment:http-access`

Aggiornare le impostazioni di accesso HTTP per un ambiente

```bash
magento-cloud httpaccess [--access ACCESS] [--auth AUTH] [--enabled ENABLED] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait]
```


```bash
httpaccess
```

### `--access`

Restrizione di accesso in formato &quot;permission:address&quot; (autorizzazione:indirizzo). Utilizza 0 per cancellare tutti gli indirizzi.

- Predefinito: `[]`
- Richiede un valore

### `--auth`

Credenziali di autenticazione HTTP Basic in formato &quot;username:password&quot;. Utilizzare 0 per cancellare tutte le credenziali.

- Predefinito: `[]`
- Richiede un valore

### `--enabled`

Specifica se il controllo degli accessi deve essere abilitato: 1 per abilitare, 0 per disabilitare

- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendere il completamento dell&#39;operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `environment:info`

Lettura o impostazione delle proprietà di un ambiente

```bash
magento-cloud environment:info [--refresh] [--date-fmt DATE-FMT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<property>] [<value>]
```


```bash
environment:metadata
```


### `property`

Nome della proprietà


### `value`

Imposta un nuovo valore per la proprietà


### `--refresh`

Se aggiornare la cache

- Predefinito: `false`
- Non accetta un valore

### `--date-fmt`

Il formato data (come stringa di formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--format`

Il formato di output: tabella, csv, tsv o normale

- Predefinito: `table`
- Richiede un valore

### `--columns`, `-c`

Colonne da visualizzare. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non generare l’intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendere il completamento dell&#39;operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `environment:init`

Inizializzare un ambiente da un archivio Git pubblico

```bash
magento-cloud environment:init [--profile PROFILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <url>
```


### `url`

URL di un archivio Git

- Obbligatorio

### `--profile`

Nome del profilo

- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendere il completamento dell&#39;operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `environment:list`

Ottieni un elenco di ambienti

```bash
magento-cloud environment:list [-I|--no-inactive] [--pipe] [--refresh REFRESH] [--sort SORT] [--reverse] [--type TYPE] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT]
```


```bash
environments
```


```bash
env
```

### `--no-inactive`, `-I`

Non mostrare ambienti inattivi

- Predefinito: `false`
- Non accetta un valore

### `--pipe`

Genera un semplice elenco di ID ambiente.

- Predefinito: `false`
- Non accetta un valore

### `--refresh`

Specifica se aggiornare l&#39;elenco.

- Predefinito: `1`
- Richiede un valore

### `--sort`

Proprietà in base alla quale eseguire l&#39;ordinamento

- Predefinito: `title`
- Richiede un valore

### `--reverse`

Ordinamento inverso (decrescente)

- Predefinito: `false`
- Non accetta un valore

### `--type`

Filtra l’elenco per tipo/i di ambiente. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--format`

Il formato di output: tabella, csv, tsv o normale

- Predefinito: `table`
- Richiede un valore

### `--columns`, `-c`

Colonne da visualizzare. Colonne disponibili: id*, title*, status*, type*, created, machine_name, updated (* = default columns). Il carattere &quot;+&quot; può essere utilizzato come segnaposto per le colonne predefinite. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non generare l’intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `environment:logs`

Leggere i registri di un ambiente

```bash
magento-cloud log [--lines LINES] [--tail] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [--] [<type>]
```


```bash
log
```


```bash
logs
```


### `type`

Tipo di registro, ad esempio &quot;accesso&quot; o &quot;errore&quot;


### `--lines`

Numero di righe da visualizzare

- Predefinito: `100`
- Richiede un valore

### `--tail`

Coda continua del registro

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--worker`

Un nome lavoratore

- Richiede un valore

### `--instance`, `-I`

Un ID istanza

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `environment:merge`

Unire un ambiente

```bash
magento-cloud merge [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]
```


```bash
merge
```


### `environment`

Ambiente da unire


### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendere il completamento dell&#39;operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `environment:push`

Invio del codice a un ambiente

```bash
magento-cloud push [--target TARGET] [-f|--force] [--force-with-lease] [-u|--set-upstream] [--activate] [--parent PARENT] [--type TYPE] [--no-clone-parent] [-W|--no-wait] [--wait] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-i|--identity-file IDENTITY-FILE] [--] [<source>]
```


```bash
push
```


### `source`

Riferimento sorgente: un nome di ramo o un hash di commit

- Predefinito: `HEAD`


### `--target`

Nome del ramo di destinazione

- Richiede un valore

### `--force`, `-f`

Consenti aggiornamenti di avanzamento non rapido

- Predefinito: `false`
- Non accetta un valore

### `--force-with-lease`

Consenti aggiornamenti di inoltro non rapido, se il ramo di tracciamento remoto è aggiornato

- Predefinito: `false`
- Non accetta un valore

### `--set-upstream`, `-u`

Imposta l’ambiente di destinazione come ambiente a monte per il ramo di origine

- Predefinito: `false`
- Non accetta un valore

### `--activate`

Attiva l’ambiente prima di inviare

- Predefinito: `false`
- Non accetta un valore

### `--branch`

OBSOLETO: alias di —activate

- Predefinito: `false`
- Non accetta un valore

### `--parent`

Imposta il nuovo ambiente principale (utilizzato solo con —activate)

- Richiede un valore

### `--type`

Imposta il tipo di ambiente (utilizzato solo con —activate )

- Richiede un valore

### `--no-clone-parent`

Non clonare i dati del ramo principale (utilizzato solo con —activate)

- Predefinito: `false`
- Non accetta un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendere il completamento dell&#39;operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--identity-file`, `-i`

Un’identità SSH (chiave privata) da utilizzare

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `environment:redeploy`

Ridistribuire un ambiente

```bash
magento-cloud redeploy [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait]
```


```bash
redeploy
```

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendere il completamento dell&#39;operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `environment:relationships`

Visualizzare le relazioni di un ambiente

```bash
magento-cloud relationships [-P|--property PROPERTY] [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE] [--] [<environment>]
```


```bash
relationships
```


### `environment`

L&#39;ambiente


### `--property`, `-P`

Proprietà di relazione da visualizzare

- Richiede un valore

### `--refresh`

Se aggiornare le relazioni

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--identity-file`, `-i`

Un’identità SSH (chiave privata) da utilizzare

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `environment:scp`

Copia di file da e verso l&#39;ambiente corrente tramite scp

```bash
magento-cloud scp [-r|--recursive] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [-i|--identity-file IDENTITY-FILE] [--] [<files>]...
```


```bash
scp
```


### `files`

File da copiare. Utilizza il prefisso remote: per definire le posizioni remote.

- Predefinito: `[]`

- Array

### `--recursive`, `-r`

Copia ricorsiva di intere directory

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--worker`

Un nome lavoratore

- Richiede un valore

### `--instance`, `-I`

Un ID istanza

- Richiede un valore

### `--identity-file`, `-i`

Un’identità SSH (chiave privata) da utilizzare

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `environment:set-remote`

Imposta l’ambiente remoto da mappare su un ramo

```bash
magento-cloud environment:set-remote <environment> [<branch>]
```


### `environment`

Nome del computer dell’ambiente. Impostate questo valore su 0 per rimuovere la mappatura per un ramo

- Obbligatorio

### `branch`

Il ramo Git da mappare (l’impostazione predefinita è il ramo corrente)


### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `environment:ssh`

SSH per l’ambiente corrente

```bash
magento-cloud ssh [--pipe] [--all] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [-i|--identity-file IDENTITY-FILE] [--] [<cmd>]...
```


```bash
ssh
```


### `cmd`

Comando da eseguire nell&#39;ambiente.

- Predefinito: `[]`

- Array

### `--pipe`

Genera solo l’URL SSH.

- Predefinito: `false`
- Non accetta un valore

### `--all`

Genera tutti gli URL SSH (per ogni app).

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--worker`

Un nome lavoratore

- Richiede un valore

### `--instance`, `-I`

Un ID istanza

- Richiede un valore

### `--identity-file`, `-i`

Un’identità SSH (chiave privata) da utilizzare

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `environment:synchronize`

Sincronizzare il codice e/o i dati di un ambiente dal relativo elemento padre

```bash
magento-cloud sync [--rebase] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<synchronize>]...
```


```bash
sync
```


### `synchronize`

Cosa sincronizzare: &quot;codice&quot;, &quot;dati&quot; o entrambi

- Predefinito: `[]`

- Array

### `--rebase`

Sincronizzare il codice ribasandolo anziché unendo

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendere il completamento dell&#39;operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `environment:url`

Ottenere gli URL pubblici di un ambiente

```bash
magento-cloud url [-1|--primary] [--browser BROWSER] [--pipe] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```


```bash
url
```

### `--primary`, `-1`

Restituisce solo l&#39;URL per la route principale

- Predefinito: `false`
- Non accetta un valore

### `--browser`

Browser da utilizzare per aprire l’URL. Impostate 0 su none.

- Richiede un valore

### `--pipe`

Invia l’URL a stdout.

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `environment:xdebug`

Apri un tunnel per Xdebug nell’ambiente

```bash
magento-cloud xdebug [--port PORT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [-i|--identity-file IDENTITY-FILE]
```


```bash
xdebug
```

### `--port`

La porta locale

- Predefinito: `9000`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--worker`

Un nome lavoratore

- Richiede un valore

### `--instance`, `-I`

Un ID istanza

- Richiede un valore

### `--identity-file`, `-i`

Un’identità SSH (chiave privata) da utilizzare

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `integration:activity:get`

Visualizzare informazioni dettagliate su una singola attività di integrazione

```bash
magento-cloud integration:activity:get [-P|--property PROPERTY] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<integration>] [<activity>]
```


### `integration`

Un ID integrazione. Lascia vuoto per scegliere da un elenco.


### `activity`

L’ID attività. Impostazione predefinita dell&#39;attività di integrazione più recente.


### `--property`, `-P`

Proprietà da visualizzare

- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

[Opzione obsoleta, non utilizzata]

- Richiede un valore

### `--format`

Il formato di output: tabella, csv, tsv o normale

- Predefinito: `table`
- Richiede un valore

### `--columns`, `-c`

Colonne da visualizzare. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non generare l’intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--date-fmt`

Il formato data (come stringa di formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `integration:activity:list`

Ottieni un elenco di attività per un’integrazione

```bash
magento-cloud i:act [--type TYPE] [-x|--exclude-type EXCLUDE-TYPE] [--limit LIMIT] [--start START] [--state STATE] [--result RESULT] [-i|--incomplete] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<id>]
```


```bash
i:act
```


```bash
integration:activities
```


### `id`

Un ID integrazione. Lascia vuoto per scegliere da un elenco.


### `--type`

Filtra le attività per tipo. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--exclude-type`, `-x`

Escludi attività per tipo. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti. Il carattere % può essere utilizzato come carattere jolly per escludere i tipi.

- Predefinito: `[]`
- Richiede un valore

### `--limit`

Limita il numero di risultati visualizzati

- Predefinito: `10`
- Richiede un valore

### `--start`

Verranno elencate solo le attività create prima di questa data

- Richiede un valore

### `--state`

Filtra le attività per stato. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--result`

Filtra attività per risultato

- Richiede un valore

### `--incomplete`, `-i`

Elencare solo le attività incomplete

- Predefinito: `false`
- Non accetta un valore

### `--format`

Il formato di output: tabella, csv, tsv o normale

- Predefinito: `table`
- Richiede un valore

### `--columns`, `-c`

Colonne da visualizzare. Colonne disponibili: id*, created*, description*, type*, state*, result*, completed (* = default columns). Il carattere &quot;+&quot; può essere utilizzato come segnaposto per le colonne predefinite. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non generare l’intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--date-fmt`

Il formato data (come stringa di formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

[Opzione obsoleta, non utilizzata]

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `integration:activity:log`

Visualizzare il registro per un’attività di integrazione

```bash
magento-cloud integration:activity:log [-t|--timestamps] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<integration>] [<activity>]
```


### `integration`

Un ID integrazione. Lascia vuoto per scegliere da un elenco.


### `activity`

L’ID attività. Impostazione predefinita dell&#39;attività di integrazione più recente.


### `--timestamps`, `-t`

Visualizza un timestamp accanto a ogni messaggio

- Predefinito: `false`
- Non accetta un valore

### `--date-fmt`

Il formato data (come stringa di formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

[Opzione obsoleta, non utilizzata]

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `integration:add`

Aggiungere un’integrazione al progetto

```bash
magento-cloud integration:add [--type TYPE] [--base-url BASE-URL] [--username USERNAME] [--token TOKEN] [--key KEY] [--secret SECRET] [--license-key LICENSE-KEY] [--server-project SERVER-PROJECT] [--repository REPOSITORY] [--build-merge-requests BUILD-MERGE-REQUESTS] [--build-pull-requests BUILD-PULL-REQUESTS] [--build-draft-pull-requests BUILD-DRAFT-PULL-REQUESTS] [--build-pull-requests-post-merge BUILD-PULL-REQUESTS-POST-MERGE] [--build-wip-merge-requests BUILD-WIP-MERGE-REQUESTS] [--merge-requests-clone-parent-data MERGE-REQUESTS-CLONE-PARENT-DATA] [--pull-requests-clone-parent-data PULL-REQUESTS-CLONE-PARENT-DATA] [--resync-pull-requests RESYNC-PULL-REQUESTS] [--fetch-branches FETCH-BRANCHES] [--prune-branches PRUNE-BRANCHES] [--url URL] [--shared-key SHARED-KEY] [--file FILE] [--events EVENTS] [--states STATES] [--environments ENVIRONMENTS] [--excluded-environments EXCLUDED-ENVIRONMENTS] [--from-address FROM-ADDRESS] [--recipients RECIPIENTS] [--channel CHANNEL] [--routing-key ROUTING-KEY] [--category CATEGORY] [--index INDEX] [--sourcetype SOURCETYPE] [--protocol PROTOCOL] [--syslog-host SYSLOG-HOST] [--syslog-port SYSLOG-PORT] [--facility FACILITY] [--message-format MESSAGE-FORMAT] [--auth-mode AUTH-MODE] [--auth-token AUTH-TOKEN] [--verify-tls VERIFY-TLS] [-p|--project PROJECT] [-W|--no-wait] [--wait]
```

### `--type`

Il tipo di integrazione (&quot;bitbucket&quot;, &quot;bitbucket_server&quot;, &quot;github&quot;, &quot;gitlab&quot;, &quot;webhook&quot;, &quot;health.email&quot;, &quot;health.pagerduty&quot;, &quot;health.slack&quot;, &quot;health.webhook&quot;, &quot;script&quot;, &quot;newrelic&quot;, &quot;splunk&quot;, &quot;sumologic&quot;, &quot;syslog&quot;)

- Richiede un valore

### `--base-url`

URL di base dell&#39;installazione del server

- Richiede un valore

### `--username`

Nome utente del server Bitbucket

- Richiede un valore

### `--token`

Un token di autenticazione o di accesso per l’integrazione

- Richiede un valore

### `--key`

Una chiave consumer OAuth Bitbucket

- Richiede un valore

### `--secret`

Un segreto consumer di Bitbucket OAuth

- Richiede un valore

### `--license-key`

Chiave di licenza per i registri di New Relic

- Richiede un valore

### `--server-project`

Il progetto (ad esempio, &quot;namespace/repo&quot;)

- Richiede un valore

### `--repository`

L’archivio di cui tenere traccia (ad esempio, &quot;proprietario/archivio&quot;)

- Richiede un valore

### `--build-merge-requests`

GitLab: creare richieste di unione come ambienti

- Predefinito: `true`
- Richiede un valore

### `--build-pull-requests`

Creare ogni richiesta di pull come ambiente

- Predefinito: `true`
- Richiede un valore

### `--build-draft-pull-requests`

Creare bozze di richieste pull

- Predefinito: `true`
- Richiede un valore

### `--build-pull-requests-post-merge`

Creare richieste di pull in base al loro stato post-unione

- Predefinito: `false`
- Richiede un valore

### `--build-wip-merge-requests`

GitLab: generare richieste di unione WIP

- Predefinito: `true`
- Richiede un valore

### `--merge-requests-clone-parent-data`

GitLab: dati clone per richieste di unione

- Predefinito: `true`
- Richiede un valore

### `--pull-requests-clone-parent-data`

Clonare i dati dell’ambiente principale per le richieste pull

- Predefinito: `true`
- Richiede un valore

### `--resync-pull-requests`

Risincronizzare i dati dell’ambiente di richiesta pull su ogni build

- Predefinito: `false`
- Richiede un valore

### `--fetch-branches`

Recupera tutti i rami dal remoto (come ambienti inattivi)

- Predefinito: `true`
- Richiede un valore

### `--prune-branches`

Elimina rami inesistenti nel remoto

- Predefinito: `true`
- Richiede un valore

### `--url`

L’URL o l’endpoint API per l’integrazione

- Richiede un valore

### `--shared-key`

Webhook: chiave segreta condivisa JWS

- Richiede un valore

### `--file`

Nome di un file locale che contiene lo script da caricare

- Richiede un valore

### `--events`

Elenco di eventi su cui agire, ad esempio environment.push

- Predefinito: `*`
- Richiede un valore

### `--states`

Elenco di stati su cui intervenire, ad esempio in sospeso, in corso, completo

- Predefinito: `complete`
- Richiede un valore

### `--environments`

ID ambiente da includere

- Predefinito: `*`
- Richiede un valore

### `--excluded-environments`

ID ambiente da escludere

- Predefinito: `[]`
- Richiede un valore

### `--from-address`

[Facoltativo] Indirizzo mittente personalizzato per le e-mail di avviso

- Richiede un valore

### `--recipients`

Gli indirizzi e-mail dei destinatari

- Predefinito: `[]`
- Richiede un valore

### `--channel`

Canale di Slack

- Richiede un valore

### `--routing-key`

Chiave di routing PagerDuty

- Richiede un valore

### `--category`

La categoria Logica di riepilogo, utilizzata per il filtro

- Richiede un valore

### `--index`

Indice Splunk

- Richiede un valore

### `--sourcetype`

Tipo di origine dell&#39;evento Splunk

- Richiede un valore

### `--protocol`

Protocollo di trasporto Syslog (&#39;tcp&#39;, &#39;udp&#39;, &#39;tls&#39;)

- Predefinito: `tls`
- Richiede un valore

### `--syslog-host`

Host agente di inoltro/agente di raccolta Syslog

- Richiede un valore

### `--syslog-port`

Porta di inoltro/raccolta Syslog

- Richiede un valore

### `--facility`

Funzionalità Syslog

- Predefinito: `1`
- Richiede un valore

### `--message-format`

Formato del messaggio Syslog (&#39;rfc3164&#39; o &#39;rfc5424&#39;)

- Predefinito: `rfc5424`
- Richiede un valore

### `--auth-mode`

Modalità di autenticazione (&#39;prefix&#39; o &#39;structured_data&#39;)

- Predefinito: `prefix`
- Richiede un valore

### `--auth-token`

Token di autenticazione

- Richiede un valore

### `--verify-tls`

Indica se la verifica del certificato HTTPS deve essere abilitata (scelta consigliata)

- Predefinito: `true`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendere il completamento dell&#39;operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `integration:delete`

Eliminare un’integrazione da un progetto

```bash
magento-cloud integration:delete [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] [<id>]
```


### `id`

L’ID integrazione. Lascia vuoto per scegliere da un elenco.


### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendere il completamento dell&#39;operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `integration:get`

Visualizzare i dettagli di un’integrazione

```bash
magento-cloud integration:get [-P|--property [PROPERTY]] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--] [<id>]
```


### `id`

Un ID integrazione. Lascia vuoto per scegliere da un elenco.


### `--property`, `-P`

Proprietà di integrazione da visualizzare

- Accetta un valore

### `--format`

Il formato di output: tabella, csv, tsv o normale

- Predefinito: `table`
- Richiede un valore

### `--columns`, `-c`

Colonne da visualizzare. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non generare l’intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `integration:list`

Visualizza un elenco di integrazioni di progetto

```bash
magento-cloud integrations [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT]
```


```bash
integrations
```

### `--format`

Il formato di output: tabella, csv, tsv o normale

- Predefinito: `table`
- Richiede un valore

### `--columns`, `-c`

Colonne da visualizzare. Colonne disponibili: id, riepilogo, tipo. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non generare l’intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `integration:update`

Aggiornare un’integrazione

```bash
magento-cloud integration:update [--type TYPE] [--base-url BASE-URL] [--username USERNAME] [--token TOKEN] [--key KEY] [--secret SECRET] [--license-key LICENSE-KEY] [--server-project SERVER-PROJECT] [--repository REPOSITORY] [--build-merge-requests BUILD-MERGE-REQUESTS] [--build-pull-requests BUILD-PULL-REQUESTS] [--build-draft-pull-requests BUILD-DRAFT-PULL-REQUESTS] [--build-pull-requests-post-merge BUILD-PULL-REQUESTS-POST-MERGE] [--build-wip-merge-requests BUILD-WIP-MERGE-REQUESTS] [--merge-requests-clone-parent-data MERGE-REQUESTS-CLONE-PARENT-DATA] [--pull-requests-clone-parent-data PULL-REQUESTS-CLONE-PARENT-DATA] [--resync-pull-requests RESYNC-PULL-REQUESTS] [--fetch-branches FETCH-BRANCHES] [--prune-branches PRUNE-BRANCHES] [--url URL] [--shared-key SHARED-KEY] [--file FILE] [--events EVENTS] [--states STATES] [--environments ENVIRONMENTS] [--excluded-environments EXCLUDED-ENVIRONMENTS] [--from-address FROM-ADDRESS] [--recipients RECIPIENTS] [--channel CHANNEL] [--routing-key ROUTING-KEY] [--category CATEGORY] [--index INDEX] [--sourcetype SOURCETYPE] [--protocol PROTOCOL] [--syslog-host SYSLOG-HOST] [--syslog-port SYSLOG-PORT] [--facility FACILITY] [--message-format MESSAGE-FORMAT] [--auth-mode AUTH-MODE] [--auth-token AUTH-TOKEN] [--verify-tls VERIFY-TLS] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] [<id>]
```


### `id`

ID dell’integrazione da aggiornare


### `--type`

Il tipo di integrazione (&quot;bitbucket&quot;, &quot;bitbucket_server&quot;, &quot;github&quot;, &quot;gitlab&quot;, &quot;webhook&quot;, &quot;health.email&quot;, &quot;health.pagerduty&quot;, &quot;health.slack&quot;, &quot;health.webhook&quot;, &quot;script&quot;, &quot;newrelic&quot;, &quot;splunk&quot;, &quot;sumologic&quot;, &quot;syslog&quot;)

- Richiede un valore

### `--base-url`

URL di base dell&#39;installazione del server

- Richiede un valore

### `--username`

Nome utente del server Bitbucket

- Richiede un valore

### `--token`

Un token di autenticazione o di accesso per l’integrazione

- Richiede un valore

### `--key`

Una chiave consumer OAuth Bitbucket

- Richiede un valore

### `--secret`

Un segreto consumer di Bitbucket OAuth

- Richiede un valore

### `--license-key`

Chiave di licenza per i registri di New Relic

- Richiede un valore

### `--server-project`

Il progetto (ad esempio, &quot;namespace/repo&quot;)

- Richiede un valore

### `--repository`

L’archivio di cui tenere traccia (ad esempio, &quot;proprietario/archivio&quot;)

- Richiede un valore

### `--build-merge-requests`

GitLab: creare richieste di unione come ambienti

- Predefinito: `true`
- Richiede un valore

### `--build-pull-requests`

Creare ogni richiesta di pull come ambiente

- Predefinito: `true`
- Richiede un valore

### `--build-draft-pull-requests`

Creare bozze di richieste pull

- Predefinito: `true`
- Richiede un valore

### `--build-pull-requests-post-merge`

Creare richieste di pull in base al loro stato post-unione

- Predefinito: `false`
- Richiede un valore

### `--build-wip-merge-requests`

GitLab: generare richieste di unione WIP

- Predefinito: `true`
- Richiede un valore

### `--merge-requests-clone-parent-data`

GitLab: dati clone per richieste di unione

- Predefinito: `true`
- Richiede un valore

### `--pull-requests-clone-parent-data`

Clonare i dati dell’ambiente principale per le richieste pull

- Predefinito: `true`
- Richiede un valore

### `--resync-pull-requests`

Risincronizzare i dati dell’ambiente di richiesta pull su ogni build

- Predefinito: `false`
- Richiede un valore

### `--fetch-branches`

Recupera tutti i rami dal remoto (come ambienti inattivi)

- Predefinito: `true`
- Richiede un valore

### `--prune-branches`

Elimina rami inesistenti nel remoto

- Predefinito: `true`
- Richiede un valore

### `--url`

L’URL o l’endpoint API per l’integrazione

- Richiede un valore

### `--shared-key`

Webhook: chiave segreta condivisa JWS

- Richiede un valore

### `--file`

Nome di un file locale che contiene lo script da caricare

- Richiede un valore

### `--events`

Elenco di eventi su cui agire, ad esempio environment.push

- Predefinito: `*`
- Richiede un valore

### `--states`

Elenco di stati su cui intervenire, ad esempio in sospeso, in corso, completo

- Predefinito: `complete`
- Richiede un valore

### `--environments`

ID ambiente da includere

- Predefinito: `*`
- Richiede un valore

### `--excluded-environments`

ID ambiente da escludere

- Predefinito: `[]`
- Richiede un valore

### `--from-address`

[Facoltativo] Indirizzo mittente personalizzato per le e-mail di avviso

- Richiede un valore

### `--recipients`

Gli indirizzi e-mail dei destinatari

- Predefinito: `[]`
- Richiede un valore

### `--channel`

Canale di Slack

- Richiede un valore

### `--routing-key`

Chiave di routing PagerDuty

- Richiede un valore

### `--category`

La categoria Logica di riepilogo, utilizzata per il filtro

- Richiede un valore

### `--index`

Indice Splunk

- Richiede un valore

### `--sourcetype`

Tipo di origine dell&#39;evento Splunk

- Richiede un valore

### `--protocol`

Protocollo di trasporto Syslog (&#39;tcp&#39;, &#39;udp&#39;, &#39;tls&#39;)

- Predefinito: `tls`
- Richiede un valore

### `--syslog-host`

Host agente di inoltro/agente di raccolta Syslog

- Richiede un valore

### `--syslog-port`

Porta di inoltro/raccolta Syslog

- Richiede un valore

### `--facility`

Funzionalità Syslog

- Predefinito: `1`
- Richiede un valore

### `--message-format`

Formato del messaggio Syslog (&#39;rfc3164&#39; o &#39;rfc5424&#39;)

- Predefinito: `rfc5424`
- Richiede un valore

### `--auth-mode`

Modalità di autenticazione (&#39;prefix&#39; o &#39;structured_data&#39;)

- Predefinito: `prefix`
- Richiede un valore

### `--auth-token`

Token di autenticazione

- Richiede un valore

### `--verify-tls`

Indica se la verifica del certificato HTTPS deve essere abilitata (scelta consigliata)

- Predefinito: `true`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendere il completamento dell&#39;operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `integration:validate`

Convalidare un’integrazione esistente

```bash
magento-cloud integration:validate [-p|--project PROJECT] [--] [<id>]
```


### `id`

Un ID integrazione. Lascia vuoto per scegliere da un elenco.


### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `local:build`

Crea il progetto corrente localmente

```bash
magento-cloud build [-a|--abslinks] [-s|--source SOURCE] [-d|--destination DESTINATION] [-c|--copy] [--clone] [--run-deploy-hooks] [--no-clean] [--no-archive] [--no-backup] [--no-cache] [--no-build-hooks] [--no-deps] [--working-copy] [--concurrency CONCURRENCY] [--lock] [--] [<app>]...
```


```bash
build
```


### `app`

Specifica le applicazioni da generare

- Predefinito: `[]`

- Array

### `--abslinks`, `-a`

Utilizzare i collegamenti assoluti

- Predefinito: `false`
- Non accetta un valore

### `--source`, `-s`

La directory di origine. Impostazione predefinita: directory principale del progetto corrente.

- Richiede un valore

### `--destination`, `-d`

La destinazione, alla quale sarà collegata la directory principale del web di ogni app. Predefinito: _www

- Richiede un valore

### `--copy`, `-c`

Copia in una directory di build, invece di eseguire il collegamento simbolico dal sorgente

- Predefinito: `false`
- Non accetta un valore

### `--clone`

Utilizza Git per clonare il HEAD corrente nella directory di build

- Predefinito: `false`
- Non accetta un valore

### `--run-deploy-hooks`

Eseguire gli hook di distribuzione e/o post_distribuzione

- Predefinito: `false`
- Non accetta un valore

### `--no-clean`

Non rimuovere le build precedenti

- Predefinito: `false`
- Non accetta un valore

### `--no-archive`

Non creare o utilizzare un archivio di build

- Predefinito: `false`
- Non accetta un valore

### `--no-backup`

Non eseguire il backup della build precedente

- Predefinito: `false`
- Non accetta un valore

### `--no-cache`

Disattiva caching

- Predefinito: `false`
- Non accetta un valore

### `--no-build-hooks`

Non eseguire hook di post-generazione

- Predefinito: `false`
- Non accetta un valore

### `--no-deps`

Non installare localmente le dipendenze della build

- Predefinito: `false`
- Non accetta un valore

### `--working-copy`

Elimina: utilizza Git per clonare un archivio di ciascun modulo Drupal anziché semplicemente scaricare una versione

- Predefinito: `false`
- Non accetta un valore

### `--concurrency`

Elimina: imposta il numero di progetti simultanei che verranno elaborati contemporaneamente

- Predefinito: `4`
- Richiede un valore

### `--lock`

Drush: crea o aggiorna un file di blocco (disponibile solo con Drush versione 7+)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `local:clean`

Rimuovi le build dei progetti precedenti

```bash
magento-cloud clean [--keep KEEP] [--max-age MAX-AGE] [--include-active]
```


```bash
clean
```

### `--keep`

Numero massimo di build da mantenere

- Predefinito: `5`
- Richiede un valore

### `--max-age`

Durata massima delle build, in secondi. Ignorato se non impostato.

- Richiede un valore

### `--include-active`

Elimina anche le build attive

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `local:dir`

Trova la directory principale del progetto locale

```bash
magento-cloud dir [<subdir>]
```


```bash
dir
```


### `subdir`

La sottodirectory da trovare (&#39;local&#39;, &#39;web&#39; o &#39;shared&#39;)


### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `metrics:disk-usage`

Mostra utilizzo disco in un servizio

```bash
magento-cloud disk [-s|--service SERVICE] [--type TYPE] [-r|--range RANGE] [-i|--interval INTERVAL] [--to TO] [-B|--bytes] [-1|--latest] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT]
```


```bash
disk
```

### `--service`, `-s`

Il nome del servizio

- Richiede un valore

### `--type`

Il tipo di servizio (se il nome del servizio non viene fornito), ad esempio mysql, pgsql, mongodb e così via. La versione del tipo non è richiesta.

- Richiede un valore

### `--range`, `-r`

L’intervallo di tempo. Le metriche vengono caricate per questa durata fino all’ora di fine (—to). È possibile specificare le unità di misura: ore (h), minuti (m) o secondi (s). Minimo &lt;comment>5 m&lt;/comment>, massimo &lt;comment>8 ore&lt;/comment> o più (a seconda del progetto), impostazione predefinita &lt;comment>10 m&lt;/comment>.

- Richiede un valore

### `--interval`, `-i`

Intervallo di tempo. Impostazione predefinita: una divisione dell&#39;intervallo. È possibile specificare le unità di misura: ore (h), minuti (m) o secondi (s). Minimo &lt;comment>1 m&lt;/comment>, massimo &lt;comment>1 ora&lt;/comment>.

- Richiede un valore

### `--to`

Ora di fine. Impostazione predefinita.

- Richiede un valore

### `--bytes`, `-B`

Mostra dimensioni in byte

- Predefinito: `false`
- Non accetta un valore

### `--latest`, `-1`

Mostra solo l&#39;ultimo punto dati singolo

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--format`

Il formato di output: tabella, csv, tsv o normale

- Predefinito: `table`
- Richiede un valore

### `--columns`, `-c`

Colonne da visualizzare. Colonne disponibili: timestamp*, used*, limit*, percent*, ipercent*, limit, interval, iused (* = default columns). Il carattere &quot;+&quot; può essere utilizzato come segnaposto per le colonne predefinite. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non generare l’intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--date-fmt`

Il formato data (come stringa di formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `mount:download`

Scaricare i file da un mount utilizzando rsync

```bash
magento-cloud mount:download [-a|--all] [-m|--mount MOUNT] [--target TARGET] [--source-path] [--delete] [--exclude EXCLUDE] [--include INCLUDE] [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [-i|--identity-file IDENTITY-FILE]
```

### `--all`, `-a`

Scarica da tutti i supporti

- Predefinito: `false`
- Non accetta un valore

### `--mount`, `-m`

Il mount (come percorso relativo all’app)

- Richiede un valore

### `--target`

La directory in cui verranno scaricati i file. Se si utilizza —all, al percorso di montaggio verrà aggiunto

- Richiede un valore

### `--source-path`

Utilizza il percorso di origine del mount (anziché il percorso di mount) come sottodirectory della destinazione, quando si utilizza —all

- Predefinito: `false`
- Non accetta un valore

### `--delete`

Se eliminare i file estranei nella directory di destinazione

- Predefinito: `false`
- Non accetta un valore

### `--exclude`

File da escludere dal download (modello)

- Predefinito: `[]`
- Richiede un valore

### `--include`

File da includere nel download (modello)

- Predefinito: `[]`
- Richiede un valore

### `--refresh`

Se aggiornare la cache

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--worker`

Un nome lavoratore

- Richiede un valore

### `--instance`, `-I`

Un ID istanza

- Richiede un valore

### `--identity-file`, `-i`

Un’identità SSH (chiave privata) da utilizzare

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `mount:list`

Ottieni un elenco di montaggi

```bash
magento-cloud mounts [--paths] [--refresh] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE]
```


```bash
mounts
```

### `--paths`

Output solo dei percorsi di montaggio (uno per riga)

- Predefinito: `false`
- Non accetta un valore

### `--refresh`

Se aggiornare la cache

- Predefinito: `false`
- Non accetta un valore

### `--format`

Il formato di output: tabella, csv, tsv o normale

- Predefinito: `table`
- Richiede un valore

### `--columns`, `-c`

Colonne da visualizzare. Colonne disponibili: definizione, percorso. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non generare l’intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--worker`

Un nome lavoratore

- Richiede un valore

### `--instance`, `-I`

Un ID istanza

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `mount:size`

Verificare l&#39;utilizzo del disco dei supporti

```bash
magento-cloud mount:size [-B|--bytes] [--refresh] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE]
```

### `--bytes`, `-B`

Mostra dimensioni in byte

- Predefinito: `false`
- Non accetta un valore

### `--refresh`

Aggiorna la cache

- Predefinito: `false`
- Non accetta un valore

### `--format`

Il formato di output: tabella, csv, tsv o normale

- Predefinito: `table`
- Richiede un valore

### `--columns`, `-c`

Colonne da visualizzare. Colonne disponibili: disponibile, max, mount, percentuale_utilizzata, dimensioni, utilizzata. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non generare l’intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--identity-file`, `-i`

Un’identità SSH (chiave privata) da utilizzare

- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--worker`

Un nome lavoratore

- Richiede un valore

### `--instance`, `-I`

Un ID istanza

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `mount:upload`

Caricare i file su un mount, utilizzando rsync

```bash
magento-cloud mount:upload [--source SOURCE] [-m|--mount MOUNT] [--delete] [--exclude EXCLUDE] [--include INCLUDE] [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-I|--instance INSTANCE] [-i|--identity-file IDENTITY-FILE]
```

### `--source`

Una directory contenente i file da caricare

- Richiede un valore

### `--mount`, `-m`

Il mount (come percorso relativo all’app)

- Richiede un valore

### `--delete`

Indica se eliminare i file estranei nel mount

- Predefinito: `false`
- Non accetta un valore

### `--exclude`

File da escludere dal caricamento (pattern)

- Predefinito: `[]`
- Richiede un valore

### `--include`

File da includere nel caricamento (modello)

- Predefinito: `[]`
- Richiede un valore

### `--refresh`

Se aggiornare la cache

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--worker`

Un nome lavoratore

- Richiede un valore

### `--instance`, `-I`

Un ID istanza

- Richiede un valore

### `--identity-file`, `-i`

Un’identità SSH (chiave privata) da utilizzare

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `project:clear-build-cache`

Cancellare la cache di build di un progetto

```bash
magento-cloud project:clear-build-cache [-p|--project PROJECT]
```

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `project:curl`

Eseguire una richiesta cURL autenticata sull’API di un progetto

```bash
magento-cloud project:curl [-X|--request REQUEST] [-d|--data DATA] [--json JSON] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-f|--fail] [-H|--header HEADER] [-p|--project PROJECT] [--] [<path>]
```


### `path`

Percorso API


### `--request`, `-X`

Metodo di richiesta da utilizzare

- Richiede un valore

### `--data`, `-d`

Dati da inviare

- Richiede un valore

### `--json`

Dati JSON da inviare

- Richiede un valore

### `--include`, `-i`

Includi intestazioni nell&#39;output

- Predefinito: `false`
- Non accetta un valore

### `--head`, `-I`

Recupera solo intestazioni

- Predefinito: `false`
- Non accetta un valore

### `--disable-compression`

Non utilizzare il flag curl - compresso

- Predefinito: `false`
- Non accetta un valore

### `--enable-glob`

Abilita globbing curl (rimuovi il flag —globoff)

- Predefinito: `false`
- Non accetta un valore

### `--fail`, `-f`

Non riuscito senza output in una risposta di errore

- Predefinito: `false`
- Non accetta un valore

### `--header`, `-H`

Intestazioni aggiuntive

- Predefinito: `[]`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `project:get`

Clonare un progetto localmente

```bash
magento-cloud get [-e|--environment ENVIRONMENT] [--depth DEPTH] [--build] [-p|--project PROJECT] [-i|--identity-file IDENTITY-FILE] [--] [<project>] [<directory>]
```


```bash
get
```


### `project`

ID progetto


### `directory`

La directory in cui clonare. Impostazione predefinita del titolo del progetto


### `--environment`, `-e`

ID ambiente da clonare. Impostazione predefinita del progetto o del primo ambiente disponibile

- Richiede un valore

### `--depth`

Creare un clone superficiale: limita il numero di commit nella cronologia

- Richiede un valore

### `--build`

Genera il progetto dopo la clonazione

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--identity-file`, `-i`

Un’identità SSH (chiave privata) da utilizzare

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `project:info`

Lettura o impostazione delle proprietà di un progetto

```bash
magento-cloud project:info [--refresh] [--date-fmt DATE-FMT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] [<property>] [<value>]
```


```bash
project:metadata
```


### `property`

Nome della proprietà


### `value`

Imposta un nuovo valore per la proprietà


### `--refresh`

Se aggiornare la cache

- Predefinito: `false`
- Non accetta un valore

### `--date-fmt`

Il formato data (come stringa di formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--format`

Il formato di output: tabella, csv, tsv o normale

- Predefinito: `table`
- Richiede un valore

### `--columns`, `-c`

Colonne da visualizzare. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non generare l’intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendere il completamento dell&#39;operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `project:list`

Ottieni un elenco di tutti i progetti attivi

```bash
magento-cloud project:list [--pipe] [--host HOST] [--title TITLE] [--my] [--refresh REFRESH] [--sort SORT] [--reverse] [--page PAGE] [-c|--count COUNT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT]
```


```bash
projects
```


```bash
pro
```

### `--pipe`

Genera un semplice elenco di ID progetto. Disattiva la paginazione.

- Predefinito: `false`
- Non accetta un valore

### `--host`

Filtra per nome host dell’area geografica (corrispondenza esatta)

- Richiede un valore

### `--title`

Filtra per titolo (ricerca senza distinzione maiuscole/minuscole)

- Richiede un valore

### `--my`

Visualizza solo i progetti di tua proprietà

- Predefinito: `false`
- Non accetta un valore

### `--refresh`

Se aggiornare l’elenco

- Predefinito: `1`
- Richiede un valore

### `--sort`

Proprietà in base alla quale eseguire l&#39;ordinamento

- Predefinito: `title`
- Richiede un valore

### `--reverse`

Ordinamento inverso (decrescente)

- Predefinito: `false`
- Non accetta un valore

### `--page`

Numero di pagina. Questo consente l’impaginazione, nonostante la configurazione o il conteggio. Ignorato se è specificato —pipe.

- Richiede un valore

### `--count`, `-c`

Il numero di progetti da visualizzare per pagina. Utilizza 0 per disabilitare l’impaginazione. Ignorato se si specifica —page.

- Richiede un valore

### `--format`

Il formato di output: tabella, csv, tsv o normale

- Predefinito: `table`
- Richiede un valore

### `--columns`

Colonne da visualizzare. Colonne disponibili: id*, title*, region*, created_at, endpoint, organization_id, organization_label, organization_name, region_label, status, ui_url (* = colonne predefinite). Il carattere &quot;+&quot; può essere utilizzato come segnaposto per le colonne predefinite. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non generare l’intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--date-fmt`

Il formato data (come stringa di formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `project:set-remote`

Imposta il progetto remoto per l’archivio Git corrente

```bash
magento-cloud project:set-remote [<project>]
```


### `project`

ID progetto


### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `project:variable:delete`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLETO ]&lt;/> Eliminare una variabile da un progetto

```bash
magento-cloud project:variable:delete [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

Nome della variabile

- Obbligatorio

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendere il completamento dell&#39;operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `project:variable:get`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLETO ]&lt;/> Visualizza variabili per un progetto

```bash
magento-cloud project:variable:get [--pipe] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--] [<name>]
```


```bash
project-variables
```


```bash
pvget
```


```bash
project:variable:list
```


### `name`

Nome della variabile


### `--pipe`

Genera solo il valore della variabile completa (è necessario specificare un &quot;nome&quot;)

- Predefinito: `false`
- Non accetta un valore

### `--format`

Il formato di output: tabella, csv, tsv o normale

- Predefinito: `table`
- Richiede un valore

### `--columns`, `-c`

Colonne da visualizzare. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non generare l’intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `project:variable:set`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLETO ]&lt;/> Imposta una variabile per un progetto

```bash
magento-cloud pvset [--json] [--no-visible-build] [--no-visible-runtime] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <name> <value>
```


```bash
pvset
```


### `name`

Nome della variabile

- Obbligatorio

### `value`

Il valore della variabile

- Obbligatorio

### `--json`

Contrassegna il valore come JSON

- Predefinito: `false`
- Non accetta un valore

### `--no-visible-build`

Non esporre questa variabile al momento della compilazione

- Predefinito: `false`
- Non accetta un valore

### `--no-visible-runtime`

Non esporre questa variabile in fase di runtime

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendere il completamento dell&#39;operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `repo:cat`

Lettura di un file nel repository del progetto

```bash
magento-cloud repo:cat [-c|--commit COMMIT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] <path>
```


### `path`

Percorso del file

- Obbligatorio

### `--commit`, `-c`

Il commit SHA. Questo può anche accettare suffissi &quot;HEAD&quot; e accento circonflesso (^) o tilde (~) per commit principali.

- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `repo:ls`

Elencare i file nell’archivio del progetto

```bash
magento-cloud repo:ls [-d|--directories] [-f|--files] [--git-style] [-c|--commit COMMIT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<path>]
```


### `path`

Percorso di una sottodirectory


### `--directories`, `-d`

Mostra solo directory

- Predefinito: `false`
- Non accetta un valore

### `--files`, `-f`

Mostra solo file

- Predefinito: `false`
- Non accetta un valore

### `--git-style`

Output di stile simile a &quot;Git ls-tree&quot;

- Predefinito: `false`
- Non accetta un valore

### `--commit`, `-c`

Il commit SHA. Questo può anche accettare suffissi &quot;HEAD&quot; e accento circonflesso (^) o tilde (~) per commit principali.

- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `repo:read`

Lettura di una directory o di un file nel repository del progetto

```bash
magento-cloud read [-c|--commit COMMIT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<path>]
```


```bash
read
```


### `path`

Percorso della directory o del file


### `--commit`, `-c`

Il commit SHA. Questo può anche accettare suffissi &quot;HEAD&quot; e accento circonflesso (^) o tilde (~) per commit principali.

- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `route:get`

Visualizzare informazioni dettagliate su un ciclo di lavorazione

```bash
magento-cloud route:get [--id ID] [-1|--primary] [-P|--property PROPERTY] [--refresh] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE] [--] [<route>]
```


### `route`

URL originale del percorso


### `--id`

Un ID di route da selezionare

- Richiede un valore

### `--primary`, `-1`

Seleziona il percorso principale

- Predefinito: `false`
- Non accetta un valore

### `--property`, `-P`

Proprietà da visualizzare

- Richiede un valore

### `--refresh`

Ignora la cache delle route

- Predefinito: `false`
- Non accetta un valore

### `--date-fmt`

Il formato data (come stringa di formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--app`, `-A`

[Opzione obsoleta, non più utilizzata]

- Richiede un valore

### `--identity-file`, `-i`

[Opzione obsoleta, non più utilizzata]

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `route:list`

Elencare tutte le route per un ambiente

```bash
magento-cloud routes [--refresh] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--] [<environment>]
```


```bash
routes
```


```bash
environment:routes
```


### `environment`

ID dell’ambiente


### `--refresh`

Ignora la cache delle route

- Predefinito: `false`
- Non accetta un valore

### `--format`

Il formato di output: tabella, csv, tsv o normale

- Predefinito: `table`
- Richiede un valore

### `--columns`, `-c`

Colonne da visualizzare. Colonne disponibili: route*, type*, to*, url (* = colonne predefinite). Il carattere &quot;+&quot; può essere utilizzato come segnaposto per le colonne predefinite. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non generare l’intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `self:install`

Installare o aggiornare i file di configurazione CLI

```bash
magento-cloud self:install [--shell-type SHELL-TYPE]
```


```bash
local:install
```

### `--shell-type`

Tipo di shell per il completamento automatico (bash o zsh)

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `self:stats`

Visualizzare le statistiche sui download dei pacchetti GitHub

```bash
magento-cloud self:stats [-p|--page PAGE] [-c|--count COUNT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT]
```

### `--page`, `-p`

Numero di pagina

- Predefinito: `1`
- Richiede un valore

### `--count`, `-c`

Risultati per pagina (massimo: 100)

- Predefinito: `20`
- Richiede un valore

### `--format`

Il formato di output: tabella, csv, tsv o normale

- Predefinito: `table`
- Richiede un valore

### `--columns`

Colonne da visualizzare. Colonne disponibili: risorsa, data, download, versione. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non generare l’intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--date-fmt`

Il formato data (come stringa di formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `self:update`

Aggiornare CLI alla versione più recente

```bash
magento-cloud self-update [--no-major] [--unstable] [--manifest MANIFEST] [--current-version CURRENT-VERSION] [--timeout TIMEOUT]
```


```bash
self-update
```


```bash
update
```

### `--no-major`

Aggiorna solo tra versioni secondarie o patch

- Predefinito: `false`
- Non accetta un valore

### `--unstable`

Aggiornamento a una nuova versione instabile, se disponibile

- Predefinito: `false`
- Non accetta un valore

### `--manifest`

Ignora il percorso del file manifesto

- Richiede un valore

### `--current-version`

Sostituisci la versione corrente

- Richiede un valore

### `--timeout`

Timeout per il controllo della versione

- Predefinito: `30`
- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `service:list`

Elencare servizi nel progetto

```bash
magento-cloud services [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```


```bash
services
```

### `--refresh`

Se aggiornare la cache

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--format`

Il formato di output: tabella, csv, tsv o normale

- Predefinito: `table`
- Richiede un valore

### `--columns`, `-c`

Colonne da visualizzare. Colonne disponibili: disco, nome, dimensione, tipo. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non generare l’intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `service:mongo:dump`

Creare un dump di archivio binario di dati da MongoDB

```bash
magento-cloud mongodump [-c|--collection COLLECTION] [-z|--gzip] [-o|--stdout] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP]
```


```bash
mongodump
```

### `--collection`, `-c`

Raccolta da scaricare

- Richiede un valore

### `--gzip`, `-z`

Comprimi l’immagine utilizzando gzip

- Predefinito: `false`
- Non accetta un valore

### `--stdout`, `-o`

Output in STDOUT anziché in un file

- Predefinito: `false`
- Non accetta un valore

### `--relationship`, `-r`

Relazione di servizio da utilizzare

- Richiede un valore

### `--identity-file`, `-i`

Un’identità SSH (chiave privata) da utilizzare

- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `service:mongo:export`

Esporta dati da MongoDB

```bash
magento-cloud mongoexport [-c|--collection COLLECTION] [--jsonArray] [--type TYPE] [-f|--fields FIELDS] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP]
```


```bash
mongoexport
```

### `--collection`, `-c`

Raccolta da esportare

- Richiede un valore

### `--jsonArray`

Esportare i dati come un singolo array JSON

- Predefinito: `false`
- Non accetta un valore

### `--type`

Tipo di esportazione, ad esempio &quot;csv&quot;

- Richiede un valore

### `--fields`, `-f`

Campi da esportare

- Predefinito: `[]`
- Richiede un valore

### `--relationship`, `-r`

Relazione di servizio da utilizzare

- Richiede un valore

### `--identity-file`, `-i`

Un’identità SSH (chiave privata) da utilizzare

- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `service:mongo:restore`

Ripristinare un’immagine di archivio binaria dei dati in MongoDB

```bash
magento-cloud mongorestore [-c|--collection COLLECTION] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP]
```


```bash
mongorestore
```

### `--collection`, `-c`

Raccolta da ripristinare

- Richiede un valore

### `--relationship`, `-r`

Relazione di servizio da utilizzare

- Richiede un valore

### `--identity-file`, `-i`

Un’identità SSH (chiave privata) da utilizzare

- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `service:mongo:shell`

Utilizzare la shell MongoDB

```bash
magento-cloud mongo [--eval EVAL] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP]
```


```bash
mongo
```

### `--eval`

Trasmettere un frammento JavaScript alla shell

- Richiede un valore

### `--relationship`, `-r`

Relazione di servizio da utilizzare

- Richiede un valore

### `--identity-file`, `-i`

Un’identità SSH (chiave privata) da utilizzare

- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `service:redis-cli`

Accedere a Redis CLI

```bash
magento-cloud redis [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--] [<args>]
```


```bash
redis
```


### `args`

Argomenti da aggiungere al comando Redis


### `--relationship`, `-r`

Relazione di servizio da utilizzare

- Richiede un valore

### `--identity-file`, `-i`

Un’identità SSH (chiave privata) da utilizzare

- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `session:switch`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ BETA ]&lt;/> Passare da una sessione all’altra

```bash
magento-cloud session:switch [<id>]
```


### `id`

Il nuovo ID sessione


### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `snapshot:create`

Creare un’istantanea di un ambiente

```bash
magento-cloud backup [--live] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]
```


```bash
backup
```


```bash
backup:create
```


```bash
environment:backup
```


### `environment`

L&#39;ambiente


### `--live`

Live backup: non arrestare l’ambiente. Se questa opzione è impostata, l’ambiente rimane in esecuzione e si apre alle connessioni durante il backup. Ciò riduce i tempi di inattività, con il rischio di eseguire il backup dei dati in uno stato incoerente.

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendere il completamento dell&#39;operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--unsafe`

Opzione obsoleta: usa —live invece

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `snapshot:list`

Elencare le istantanee disponibili di un ambiente

```bash
magento-cloud snapshots [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```


```bash
snapshots
```


```bash
backups
```


```bash
backup:list
```

### `--limit`

[Obsoleto] - questa opzione non è utilizzata

- Richiede un valore

### `--start`

[Obsoleto] - questa opzione non è utilizzata

- Richiede un valore

### `--format`

Il formato di output: tabella, csv, tsv o normale

- Predefinito: `table`
- Richiede un valore

### `--columns`, `-c`

Colonne da visualizzare. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non generare l’intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--date-fmt`

Il formato data (come stringa di formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `snapshot:restore`

Ripristinare uno snapshot dell’ambiente

```bash
magento-cloud snapshot:restore [--target TARGET] [--branch-from BRANCH-FROM] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<snapshot>]
```


```bash
environment:restore
```


```bash
backup:restore
```


### `snapshot`

Nome dello snapshot. Impostazione predefinita più recente


### `--target`

L’ambiente in cui eseguire il ripristino. Impostazione predefinita dell&#39;ambiente corrente dello snapshot

- Richiede un valore

### `--branch-from`

Se —target non esiste ancora, specifica l&#39;elemento padre del nuovo ambiente

- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendere il completamento dell&#39;operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `source-operation:run`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ BETA ]&lt;/> Eseguire un&#39;operazione di origine

```bash
magento-cloud source-operation:run [--variable VARIABLE] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <operation>
```


### `operation`

Nome dell’operazione

- Obbligatorio

### `--variable`

Variabile da impostare durante l&#39;operazione, nel formato &lt;info>type:name=value&lt;/info>

- Predefinito: `[]`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendere il completamento dell&#39;operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `ssh-cert:info`

Visualizza informazioni sul certificato SSH corrente

```bash
magento-cloud ssh-cert:info [--no-refresh] [-P|--property PROPERTY] [--date-fmt DATE-FMT]
```

### `--no-refresh`

Non aggiornare il certificato se non è valido

- Predefinito: `false`
- Non accetta un valore

### `--property`, `-P`

Proprietà del certificato da visualizzare

- Richiede un valore

### `--date-fmt`

Il formato data (come stringa di formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `ssh-cert:load`

Generare un certificato SSH

```bash
magento-cloud ssh-cert:load [--refresh-only] [--new] [--new-key]
```

### `--refresh-only`

Aggiorna il certificato solo se necessario (non scrivere la configurazione SSH)

- Predefinito: `false`
- Non accetta un valore

### `--new`

Forza l’aggiornamento del certificato

- Predefinito: `false`
- Non accetta un valore

### `--new-key`

[Obsoleto] Usa - Nuovo

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `ssh-key:add`

Aggiungi una nuova chiave SSH

```bash
magento-cloud ssh-key:add [--name NAME] [--] [<path>]
```


### `path`

Percorso di una chiave pubblica SSH esistente


### `--name`

Nome per identificare la chiave

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `ssh-key:delete`

Eliminare una chiave SSH

```bash
magento-cloud ssh-key:delete [<id>]
```


### `id`

ID della chiave SSH da eliminare


### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `ssh-key:list`

Ottieni un elenco di chiavi SSH nel tuo account

```bash
magento-cloud ssh-keys [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```


```bash
ssh-keys
```

### `--format`

Il formato di output: tabella, csv, tsv o normale

- Predefinito: `table`
- Richiede un valore

### `--columns`, `-c`

Colonne da visualizzare. Colonne disponibili: id*, title*, path*, fingerprint (* = colonne predefinite). Il carattere &quot;+&quot; può essere utilizzato come segnaposto per le colonne predefinite. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non generare l’intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `subscription:info`

Lettura o modifica delle proprietà di sottoscrizione

```bash
magento-cloud subscription:info [-s|--id ID] [--date-fmt DATE-FMT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--] [<property>] [<value>]
```


### `property`

Nome della proprietà


### `value`

Imposta un nuovo valore per la proprietà


### `--id`, `-s`

ID sottoscrizione

- Richiede un valore

### `--date-fmt`

Il formato data (come stringa di formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--format`

Il formato di output: tabella, csv, tsv o normale

- Predefinito: `table`
- Richiede un valore

### `--columns`, `-c`

Colonne da visualizzare. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non generare l’intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `tunnel:close`

Chiudi tunnel SSH

```bash
magento-cloud tunnel:close [-a|--all] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

### `--all`, `-a`

Chiudi tutti i tunnel

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `tunnel:info`

Visualizza informazioni sulle relazioni per i tunnel SSH

```bash
magento-cloud tunnel:info [-P|--property PROPERTY] [-c|--encode] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

### `--property`, `-P`

Proprietà di relazione da visualizzare

- Richiede un valore

### `--encode`, `-c`

Output come JSON con codifica base64

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--format`

Il formato di output: tabella, csv, tsv o normale

- Predefinito: `table`
- Richiede un valore

### `--columns`

Colonne da visualizzare. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non generare l’intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `tunnel:list`

Elenca tunnel SSH

```bash
magento-cloud tunnels [-a|--all] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```


```bash
tunnels
```

### `--all`, `-a`

Visualizza tutti i tunnel

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--format`

Il formato di output: tabella, csv, tsv o normale

- Predefinito: `table`
- Richiede un valore

### `--columns`, `-c`

Colonne da visualizzare. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non generare l’intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `tunnel:open`

Aprire i tunnel SSH alle relazioni di un’app

```bash
magento-cloud tunnel:open [-g|--gateway-ports] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE]
```

### `--gateway-ports`, `-g`

Consenti agli host remoti di connettersi alle porte inoltrate locali

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--identity-file`, `-i`

Un’identità SSH (chiave privata) da utilizzare

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `tunnel:single`

Aprire un singolo tunnel SSH a una relazione app

```bash
magento-cloud tunnel:single [--port PORT] [-g|--gateway-ports] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE]
```

### `--port`

La porta locale

- Richiede un valore

### `--gateway-ports`, `-g`

Consenti agli host remoti di connettersi alle porte inoltrate locali

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--relationship`, `-r`

Relazione di servizio da utilizzare

- Richiede un valore

### `--identity-file`, `-i`

Un’identità SSH (chiave privata) da utilizzare

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `user:add`

Aggiungere un utente al progetto

```bash
magento-cloud user:add [-r|--role ROLE] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] [<email>]
```


### `email`

Indirizzo e-mail dell’utente


### `--role`, `-r`

Ruolo del progetto dell’utente (&quot;admin&quot; o &quot;visualizzatore&quot;) o ruolo del tipo di ambiente (ad esempio &quot;staging:collaboratore&quot; o &quot;produzione:visualizzatore&quot;). Per rimuovere un utente da un tipo di ambiente, imposta il ruolo come &quot;none&quot; (nessuno). Il carattere % può essere utilizzato come carattere jolly per il tipo di ambiente. Esempio: &#39;%:visualizzatore&#39; per assegnare all&#39;utente il ruolo &#39;visualizzatore&#39; per tutti i tipi. Il ruolo può essere abbreviato, ad esempio &quot;production:v&quot;.

- Predefinito: `[]`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendere il completamento dell&#39;operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `user:delete`

Eliminare un utente dal progetto

```bash
magento-cloud user:delete [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] <email>
```


### `email`

Indirizzo e-mail dell’utente

- Obbligatorio

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendere il completamento dell&#39;operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `user:get`

Visualizzare i ruoli di un utente

```bash
magento-cloud user:get [-l|--level LEVEL] [--pipe] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [-r|--role ROLE] [--] [<email>]
```


```bash
user:role
```


### `email`

Indirizzo e-mail dell’utente


### `--level`, `-l`

Livello di ruolo (&quot;progetto&quot; o &quot;ambiente&quot;)

- Richiede un valore

### `--pipe`

Trasmette il ruolo allo stdout (dopo aver apportato eventuali modifiche)

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendere il completamento dell&#39;operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--role`, `-r`

[Obsoleto: usa utente:aggiornamento per modificare i ruoli di un utente]

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `user:list`

Elenca utenti progetto

```bash
magento-cloud users [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT]
```


```bash
users
```

### `--format`

Il formato di output: tabella, csv, tsv o normale

- Predefinito: `table`
- Richiede un valore

### `--columns`, `-c`

Colonne da visualizzare. Colonne disponibili: e-mail, ID, nome, ruolo. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non generare l’intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `user:update`

Aggiornare i ruoli utente in un progetto

```bash
magento-cloud user:update [-r|--role ROLE] [-p|--project PROJECT] [-W|--no-wait] [--wait] [--] [<email>]
```


### `email`

Indirizzo e-mail dell’utente


### `--role`, `-r`

Ruolo del progetto dell’utente (&quot;admin&quot; o &quot;visualizzatore&quot;) o ruolo del tipo di ambiente (ad esempio &quot;staging:collaboratore&quot; o &quot;produzione:visualizzatore&quot;). Per rimuovere un utente da un tipo di ambiente, imposta il ruolo come &quot;none&quot; (nessuno). Il carattere % può essere utilizzato come carattere jolly per il tipo di ambiente. Esempio: &#39;%:visualizzatore&#39; per assegnare all&#39;utente il ruolo &#39;visualizzatore&#39; per tutti i tipi. Il ruolo può essere abbreviato, ad esempio &quot;production:v&quot;.

- Predefinito: `[]`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendere il completamento dell&#39;operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `variable:create`

Creare una variabile

```bash
magento-cloud variable:create [-l|--level LEVEL] [--name NAME] [--value VALUE] [--json JSON] [--sensitive SENSITIVE] [--prefix PREFIX] [--enabled ENABLED] [--inheritable INHERITABLE] [--visible-build VISIBLE-BUILD] [--visible-runtime VISIBLE-RUNTIME] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<name>]
```


### `name`

Nome della variabile


### `--level`, `-l`

Livello al quale impostare la variabile (&quot;progetto&quot; o &quot;ambiente&quot;)

- Richiede un valore

### `--name`

Nome della variabile

- Richiede un valore

### `--value`

Valore della variabile

- Richiede un valore

### `--json`

Se la variabile è in formato JSON

- Predefinito: `false`
- Richiede un valore

### `--sensitive`

Se la variabile è sensibile

- Predefinito: `false`
- Richiede un valore

### `--prefix`

Prefisso del nome della variabile (ad esempio &quot;none&quot; o &quot;env:&quot;)

- Predefinito: `none`
- Richiede un valore

### `--enabled`

Se la variabile deve essere abilitata

- Predefinito: `true`
- Richiede un valore

### `--inheritable`

Se la variabile è ereditabile dagli ambienti figlio

- Predefinito: `true`
- Richiede un valore

### `--visible-build`

Indica se la variabile deve essere visibile al momento della compilazione

- Richiede un valore

### `--visible-runtime`

Indica se la variabile deve essere visibile in fase di runtime

- Predefinito: `true`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendere il completamento dell&#39;operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `variable:delete`

Eliminare una variabile

```bash
magento-cloud variable:delete [-l|--level LEVEL] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

Nome della variabile

- Obbligatorio

### `--level`, `-l`

Livello della variabile (&quot;project&quot;, &quot;environment&quot;, &quot;p&quot; o &quot;e&quot;)

- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendere il completamento dell&#39;operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `variable:disable`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLETO ]&lt;/> Disattivazione di una variabile a livello di ambiente abilitata

```bash
magento-cloud variable:disable [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

Nome della variabile

- Obbligatorio

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendere il completamento dell&#39;operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `variable:enable`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLETO ]&lt;/> Abilitare una variabile disabilitata a livello di ambiente

```bash
magento-cloud variable:enable [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

Nome della variabile

- Obbligatorio

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendere il completamento dell&#39;operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `variable:get`

Visualizzare una variabile

```bash
magento-cloud vget [-P|--property PROPERTY] [-l|--level LEVEL] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--pipe] [--] [<name>]
```


```bash
vget
```


### `name`

Nome della variabile


### `--property`, `-P`

Visualizzare una singola proprietà variabile

- Richiede un valore

### `--level`, `-l`

Livello della variabile (&quot;project&quot;, &quot;environment&quot;, &quot;p&quot; o &quot;e&quot;)

- Richiede un valore

### `--format`

Il formato di output: tabella, csv, tsv o normale

- Predefinito: `table`
- Richiede un valore

### `--columns`, `-c`

Colonne da visualizzare. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non generare l’intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--pipe`

[Opzione obsoleta] Restituisce solo il valore della variabile

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `variable:list`

Variabili elenco

```bash
magento-cloud variable:list [-l|--level LEVEL] [--format FORMAT] [-c|--columns COLUMNS] [--no-header] [-p|--project PROJECT] [-e|--environment ENVIRONMENT]
```


```bash
variables
```


```bash
var
```

### `--level`, `-l`

Livello della variabile (&quot;project&quot;, &quot;environment&quot;, &quot;p&quot; o &quot;e&quot;)

- Richiede un valore

### `--format`

Il formato di output: tabella, csv, tsv o normale

- Predefinito: `table`
- Richiede un valore

### `--columns`, `-c`

Colonne da visualizzare. Colonne disponibili: is_enabled, level, name, value. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non generare l’intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `variable:set`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLETO ]&lt;/> Impostare una variabile per un ambiente

```bash
magento-cloud vset [--json] [--disabled] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name> <value>
```


```bash
vset
```


### `name`

Nome della variabile

- Obbligatorio

### `value`

Il valore della variabile

- Obbligatorio

### `--json`

Contrassegna il valore come JSON

- Predefinito: `false`
- Non accetta un valore

### `--disabled`

Contrassegna la variabile come disabilitata

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendere il completamento dell&#39;operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `variable:update`

Aggiornare una variabile

```bash
magento-cloud variable:update [-l|--level LEVEL] [--value VALUE] [--json JSON] [--sensitive SENSITIVE] [--enabled ENABLED] [--inheritable INHERITABLE] [--visible-build VISIBLE-BUILD] [--visible-runtime VISIBLE-RUNTIME] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

Nome della variabile

- Obbligatorio

### `--level`, `-l`

Livello della variabile (&quot;project&quot;, &quot;environment&quot;, &quot;p&quot; o &quot;e&quot;)

- Richiede un valore

### `--value`

Valore della variabile

- Richiede un valore

### `--json`

Se la variabile è in formato JSON

- Predefinito: `false`
- Richiede un valore

### `--sensitive`

Se la variabile è sensibile

- Predefinito: `false`
- Richiede un valore

### `--enabled`

Se la variabile deve essere abilitata

- Predefinito: `true`
- Richiede un valore

### `--inheritable`

Se la variabile è ereditabile dagli ambienti figlio

- Predefinito: `true`
- Richiede un valore

### `--visible-build`

Indica se la variabile deve essere visibile al momento della compilazione

- Richiede un valore

### `--visible-runtime`

Indica se la variabile deve essere visibile in fase di runtime

- Predefinito: `true`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendere il completamento dell&#39;operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `version:list`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ ALFA ]&lt;/> Elenco delle versioni dell’ambiente

```bash
magento-cloud versions [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```


```bash
versions
```

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--format`

Il formato di output: tabella, csv, tsv o normale

- Predefinito: `table`
- Richiede un valore

### `--columns`, `-c`

Colonne da visualizzare. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non generare l’intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore


## `worker:list`

Ottieni un elenco di tutti i processi di lavoro distribuiti

```bash
magento-cloud workers [--refresh] [-p|--project PROJECT] [-e|--environment ENVIRONMENT] [--format FORMAT] [-c|--columns COLUMNS] [--no-header]
```


```bash
workers
```

### `--refresh`

Se aggiornare la cache

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Opzione obsoleta, non più utilizzata

- Richiede un valore

### `--environment`, `-e`

ID dell’ambiente

- Richiede un valore

### `--format`

Il formato di output: tabella, csv, tsv o normale

- Predefinito: `table`
- Richiede un valore

### `--columns`, `-c`

Colonne da visualizzare. Colonne disponibili: comandi, nome, tipo. Se un elenco è dato come un singolo valore (ad es. &quot;a,b,c&quot;) sarà diviso da virgole e/o spazi vuoti.

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non generare l’intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza questo messaggio della Guida

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la gravità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondi &quot;sì&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--no-interaction`

Non fare domande interattive; accetta valori predefiniti. Equivalente a utilizzare la variabile di ambiente: &lt;comment>MAGENTO_CLOUD_CLI_NO_INTERACTION=1&lt;/comment>

- Predefinito: `false`
- Non accetta un valore

### `--ansi`

Forza uscita ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no-ansi`

Disattiva output ANSI

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondi &quot;no&quot; alle domande di conferma; accetta il valore predefinito per altre domande; disattiva l’interazione

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non inviare messaggi

- Predefinito: `false`
- Non accetta un valore
