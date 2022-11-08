---
source-git-commit: 23d55385046de18b238c90f6a99be692f1ce7561
workflow-type: tm+mt
source-wordcount: '19853'
ht-degree: 0%

---
# magento-cloud (Adobe Commerce su infrastruttura cloud)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**Versione**: 1 40,0

Questo riferimento contiene 129 comandi disponibili tramite il `magento-cloud` strumento a riga di comando.
L’elenco iniziale viene generato automaticamente utilizzando `magento-cloud list` all&#39;edizione.

>[!NOTE]
>
>Questo riferimento viene generato dal codebase dell&#39;applicazione. Per modificare il contenuto, è possibile aggiornare il codice sorgente per l’implementazione del comando corrispondente nel [codebase](https://github.com/magento) e invia le modifiche per la revisione. Un altro modo è quello di _Invia feedback_ (trova il link in alto a destra). Per gli orientamenti sui contributi, consultare [Contributi codice](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `_completion`

Gancio di completamento BASH.

```bash
_completion [-g|--generate-hook] [-p|--program PROGRAM] [-m|--multiple] [--shell-type [SHELL-TYPE]]
```

### `--generate-hook`, `-g`

Genera codice BASH che imposta il completamento per questa applicazione.

- Predefinito: `false`
- Non accetta un valore

### `--program`, `-p`

Nome del programma che deve attivare il completamento &lt;comment>(impostazione predefinita del percorso assoluto dell&#39;applicazione)&lt;/comment>.

- Richiede un valore

### `--multiple`, `-m`

Gancio generato può essere utilizzato per più applicazioni.

- Predefinito: `false`
- Non accetta un valore

### `--shell-type`

Impostare il tipo di shell (zsh o bash). In caso contrario, questo viene determinato automaticamente.

- Accetta un valore


## `bot`

Bot Magento Cloud

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

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `clear-cache`

Elimina la cache CLI

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

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `decode`

Decodificare una stringa codificata come MAGENTO_CLOUD_VARIABLES

```bash
magento-cloud decode [-P|--property PROPERTY] [--] <value>
```


### `value`

Il valore della variabile da decodificare

- Obbligatorio

### `--property`, `-P`

Proprietà da visualizzare all’interno della variabile

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `docs`

Apri la documentazione online

```bash
magento-cloud docs [--browser BROWSER] [--pipe] [--] [<search>]...
```


### `search`

Termini di ricerca

- Predefinito: `[]`

- Array

### `--browser`

Il browser da utilizzare per aprire l’URL. Imposta 0 su Nessuno.

- Richiede un valore

### `--pipe`

Invia l’URL a stdout.

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `help`

Visualizza la Guida per un comando

```bash
help [--format FORMAT] [--raw] [--] [<command_name>]
```


### `command_name`

Nome del comando

- Predefinito: `help`


### `--format`

Il formato di output (txt, xml, json o md)

- Predefinito: `txt`
- Richiede un valore

### `--raw`

Per visualizzare la guida dei comandi non elaborati

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `legacy-migrate`

Migrazione dalla struttura file legacy

```bash
magento-cloud legacy-migrate [--no-backup]
```

### `--no-backup`

Non creare un backup del progetto.

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `list`

Elenca comandi

```bash
list [--raw] [--format FORMAT] [--all] [--] [<namespace>]
```


### `namespace`

Nome dello spazio dei nomi


### `--raw`

Per visualizzare l&#39;elenco dei comandi non elaborati

- Predefinito: `false`
- Non accetta un valore

### `--format`

Il formato di output (txt, xml, json o md)

- Predefinito: `txt`
- Richiede un valore


## `multi`

Esegui un comando su più progetti

```bash
magento-cloud multi [-p|--projects PROJECTS] [--continue] [--sort SORT] [--reverse] [--] <cmd>
```


### `cmd`

Il comando da eseguire

- Obbligatorio

### `--projects`, `-p`

Elenco degli ID del progetto, separati da virgole e/o spazi bianchi

- Richiede un valore

### `--continue`

Continua a eseguire i comandi anche se viene rilevata un&#39;eccezione

- Predefinito: `false`
- Non accetta un valore

### `--sort`

Proprietà in base alla quale ordinare l’elenco delle opzioni del progetto

- Predefinito: `title`
- Richiede un valore

### `--reverse`

Annulla l’ordine delle opzioni del progetto

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `web`

Apri l’interfaccia utente Web

```bash
magento-cloud web [--browser BROWSER] [--pipe] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```

### `--browser`

Il browser da utilizzare per aprire l’URL. Imposta 0 su Nessuno.

- Richiede un valore

### `--pipe`

Invia l’URL a stdout.

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `welcome`

Benvenuto in Magento Cloud

```bash
magento-cloud welcome
```

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `winky`



```bash
magento-cloud winky
```

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `activity:cancel`

Annullare un’attività

```bash
magento-cloud activity:cancel [--type TYPE] [--exclude-type EXCLUDE-TYPE] [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<id>]
```


### `id`

L&#39;ID attività. Impostazione predefinita dell&#39;attività di eliminazione più recente.


### `--type`

Filtra per tipo (quando selezioni un’attività predefinita). Se viene specificato un singolo valore, questo viene suddiviso per virgole o spazi bianchi.

- Predefinito: `[]`
- Richiede un valore

### `--exclude-type`

Escludi per tipo (quando selezioni un’attività predefinita). Se viene specificato un singolo valore, questo viene suddiviso per virgole o spazi bianchi.

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

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `activity:get`

Visualizzare informazioni dettagliate su una singola attività

```bash
magento-cloud activity:get [-P|--property PROPERTY] [--type TYPE] [--exclude-type EXCLUDE-TYPE] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<id>]
```


### `id`

L&#39;ID attività. Impostazione predefinita dell’attività più recente.


### `--property`, `-P`

Proprietà da visualizzare

- Richiede un valore

### `--type`

Filtra per tipo (quando selezioni un’attività predefinita). Se viene specificato un singolo valore, questo viene suddiviso per virgole o spazi bianchi.

- Predefinito: `[]`
- Richiede un valore

### `--exclude-type`

Escludi per tipo (quando selezioni un’attività predefinita). Se viene specificato un singolo valore, questo viene suddiviso per virgole o spazi bianchi.

- Predefinito: `[]`
- Richiede un valore

### `--state`

Filtra per stato (quando selezioni un’attività predefinita): in_progress, in sospeso, completato o annullato. Se viene specificato un singolo valore, questo viene suddiviso per virgole o spazi bianchi.

- Predefinito: `[]`
- Richiede un valore

### `--result`

Filtra per risultato (quando selezioni un’attività predefinita): successo o fallimento

- Richiede un valore

### `--incomplete`, `-i`

Includi solo le attività incomplete (quando selezioni un’attività predefinita). Questa è una stenografia per &lt;info>—state=in_progress,in sospeso&lt;/info>

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

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--format`

Il formato di output (&quot;tabella&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;normale&quot;)

- Predefinito: `table`
- Richiede un valore

### `--columns`

Colonne da visualizzare (elenco separato da virgole o valori multipli)

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non trasmettere l&#39;intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--date-fmt`

Formato data (come stringa formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `activity:list`

Ottenere un elenco delle attività per un ambiente o un progetto

```bash
magento-cloud activity:list [-t|--type TYPE] [-x|--exclude-type EXCLUDE-TYPE] [--limit LIMIT] [--start START] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```


```bash
activities
```


```bash
act
```

### `--type`, `-t`

Filtrare le attività per tipo Se viene specificato un singolo valore, questo verrà suddiviso per virgole o spazi bianchi.

- Predefinito: `[]`
- Richiede un valore

### `--exclude-type`, `-x`

Escludi le attività per tipo. Se viene specificato un singolo valore, questo viene suddiviso per virgole o spazi bianchi.

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

Filtrare le attività per stato: in_progress, in sospeso, completato o annullato. Se viene specificato un singolo valore, questo viene suddiviso per virgole o spazi bianchi.

- Predefinito: `[]`
- Richiede un valore

### `--result`

Filtrare le attività per risultato: successo o fallimento

- Richiede un valore

### `--incomplete`, `-i`

Elenca solo attività incomplete

- Predefinito: `false`
- Non accetta un valore

### `--all`, `-a`

Elencare attività in tutti gli ambienti

- Predefinito: `false`
- Non accetta un valore

### `--format`

Il formato di output (&quot;tabella&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;normale&quot;)

- Predefinito: `table`
- Richiede un valore

### `--columns`

Colonne da visualizzare (elenco separato da virgole o valori multipli)

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non trasmettere l&#39;intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--date-fmt`

Formato data (come stringa formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `activity:log`

Visualizza il registro per un’attività

```bash
magento-cloud activity:log [--refresh REFRESH] [-t|--timestamps] [--type TYPE] [--exclude-type EXCLUDE-TYPE] [--state STATE] [--result RESULT] [-i|--incomplete] [-a|--all] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<id>]
```


### `id`

L&#39;ID attività. Impostazione predefinita dell’attività più recente.


### `--refresh`

Intervallo di aggiornamento dell’attività (secondi). Impostare su 0 per disabilitare l&#39;aggiornamento.

- Predefinito: `3`
- Richiede un valore

### `--timestamps`, `-t`

Visualizza una marca temporale accanto a ciascun messaggio

- Predefinito: `false`
- Non accetta un valore

### `--type`

Filtra per tipo (quando selezioni un’attività predefinita). Se viene specificato un singolo valore, questo viene suddiviso per virgole o spazi bianchi.

- Predefinito: `[]`
- Richiede un valore

### `--exclude-type`

Escludi per tipo (quando selezioni un’attività predefinita). Se viene specificato un singolo valore, questo viene suddiviso per virgole o spazi bianchi.

- Predefinito: `[]`
- Richiede un valore

### `--state`

Filtra per stato (quando selezioni un’attività predefinita): in_progress, in sospeso, completato o annullato. Se viene specificato un singolo valore, questo viene suddiviso per virgole o spazi bianchi.

- Predefinito: `[]`
- Richiede un valore

### `--result`

Filtra per risultato (quando selezioni un’attività predefinita): successo o fallimento

- Richiede un valore

### `--incomplete`, `-i`

Includi solo le attività incomplete (quando selezioni un’attività predefinita). Questa è una stenografia per &lt;info>—state=in_progress,in sospeso&lt;/info>

- Predefinito: `false`
- Non accetta un valore

### `--all`, `-a`

Controlla le attività recenti in tutti gli ambienti (quando selezioni un’attività predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--date-fmt`

Formato data (come stringa formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `api:curl`

Esegui una richiesta cURL autenticata sull’API Magento Cloud

```bash
magento-cloud api:curl [-X|--request REQUEST] [-d|--data DATA] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-f|--fail] [-H|--header HEADER] [--] [<path>]
```


### `path`

Percorso API


### `--request`, `-X`

Il metodo di richiesta da utilizzare

- Richiede un valore

### `--data`, `-d`

Dati da inviare

- Richiede un valore

### `--include`, `-i`

Includi intestazioni nell&#39;output

- Predefinito: `false`
- Non accetta un valore

### `--head`, `-I`

Solo intestazioni di recupero

- Predefinito: `false`
- Non accetta un valore

### `--disable-compression`

Non utilizzare il flag curl —compressed

- Predefinito: `false`
- Non accetta un valore

### `--enable-glob`

Abilita la globbing curl (rimuovi la bandiera —globoff)

- Predefinito: `false`
- Non accetta un valore

### `--fail`, `-f`

Errore senza output in una risposta di errore

- Predefinito: `false`
- Non accetta un valore

### `--header`, `-H`

Intestazioni supplementari

- Predefinito: `[]`
- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `app:config-get`

Visualizzare la configurazione di un’app

```bash
magento-cloud app:config-get [-P|--property PROPERTY] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE]
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

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--identity-file`, `-i`

[Opzione obsoleta, non più utilizzata]

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `app:list`

Elencare app nel progetto

```bash
magento-cloud apps [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header]
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

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--format`

Il formato di output (&quot;tabella&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;normale&quot;)

- Predefinito: `table`
- Richiede un valore

### `--columns`

Colonne da visualizzare (elenco separato da virgole o valori multipli)

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non trasmettere l&#39;intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `auth:api-token-login`

Accedere a Magento Cloud utilizzando un token API

```bash
magento-cloud auth:api-token-login
```

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `auth:browser-login`

Accedere a Magento Cloud tramite un browser

```bash
magento-cloud login [-f|--force] [--browser BROWSER] [--pipe]
```


```bash
login
```

### `--force`, `-f`

Accedi di nuovo, anche se hai già effettuato l&#39;accesso

- Predefinito: `false`
- Non accetta un valore

### `--browser`

Il browser da utilizzare per aprire l’URL. Imposta 0 su Nessuno.

- Richiede un valore

### `--pipe`

Invia l’URL a stdout.

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `auth:info`

Visualizza le informazioni sul tuo account

```bash
magento-cloud auth:info [--no-auto-login] [-P|--property PROPERTY] [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [--] [<property>]
```


### `property`

Proprietà dell&#39;account da visualizzare


### `--no-auto-login`

Ignora l&#39;accesso automatico. Se non è stato effettuato l’accesso, non verrà emesso nulla e il codice di uscita sarà 0, purché non si verifichino altri errori.

- Predefinito: `false`
- Non accetta un valore

### `--property`, `-P`

Proprietà account da visualizzare (sintassi alternativa)

- Richiede un valore

### `--refresh`

Se aggiornare la cache

- Predefinito: `false`
- Non accetta un valore

### `--format`

Il formato di output (&quot;tabella&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;normale&quot;)

- Predefinito: `table`
- Richiede un valore

### `--columns`

Colonne da visualizzare (elenco separato da virgole o valori multipli)

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non trasmettere l&#39;intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `auth:logout`

Esci da Magento Cloud

```bash
magento-cloud logout [-a|--all] [--other]
```


```bash
logout
```

### `--all`, `-a`

Esci da tutte le sessioni locali

- Predefinito: `false`
- Non accetta un valore

### `--other`

Disconnessione da altre sessioni locali

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `auth:password-login`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLETO ]&lt;/> Accedi a Magento Cloud utilizzando un nome utente e una password

```bash
magento-cloud auth:password-login
```


```bash
auth:login
```

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `auth:token`

Ottieni un token di accesso OAuth 2 per le richieste alle API di Magento Cloud

```bash
magento-cloud auth:token
```

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `blackfire:setup`

Configurazione dell’integrazione Blackfire.io per il progetto

```bash
magento-cloud blackfire:setup [--server_id SERVER_ID] [--server_token SERVER_TOKEN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait]
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

Nome host API del progetto

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendi il completamento dell’operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `certificate:add`

Aggiungere un certificato SSL al progetto

```bash
magento-cloud certificate:add [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait]
```

### `--cert`

Percorso del file del certificato

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

Nome host API del progetto

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendi il completamento dell’operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `certificate:delete`

Eliminare un certificato dal progetto

```bash
magento-cloud certificate:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <id>
```


### `id`

ID certificato (o l’inizio di esso)

- Obbligatorio

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendi il completamento dell’operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `certificate:get`

Visualizzare un certificato

```bash
magento-cloud certificate:get [-P|--property PROPERTY] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [--] <id>
```


### `id`

ID certificato (o l’inizio di esso)

- Obbligatorio

### `--property`, `-P`

Proprietà del certificato da visualizzare

- Richiede un valore

### `--date-fmt`

Formato data (come stringa formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `certificate:list`

Elencare certificati di progetto

```bash
magento-cloud certificate:list [--domain DOMAIN] [--exclude-domain EXCLUDE-DOMAIN] [--issuer ISSUER] [--only-auto] [--no-auto] [--ignore-expiry] [--only-expired] [--no-expired] [--pipe-domains] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
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

Escludi certificati, corrispondenti per nome di dominio (ricerca senza distinzione tra maiuscole e minuscole)

- Richiede un valore

### `--issuer`

Filtra per emittente

- Richiede un valore

### `--only-auto`

Mostra solo certificati con provisioning automatico

- Predefinito: `false`
- Non accetta un valore

### `--no-auto`

Mostra solo certificati aggiunti manualmente

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

Formato data (come stringa formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--format`

Il formato di output (&quot;tabella&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;normale&quot;)

- Predefinito: `table`
- Richiede un valore

### `--columns`

Colonne da visualizzare (elenco separato da virgole o valori multipli)

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non trasmettere l&#39;intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `commit:get`

Mostra dettagli commit

```bash
magento-cloud commit:get [-P|--property PROPERTY] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--] [<commit>]
```


### `commit`

Il commettere SHA. Questo può anche accettare i suffissi &quot;HEAD&quot; e &quot;caret&quot; (^) o &quot;tilde&quot; (~) per i commit dei genitori.

- Predefinito: `HEAD`


### `--property`, `-P`

La proprietà commit da visualizzare.

- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--date-fmt`

Formato data (come stringa formato data PHP)

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

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `commit:list`

Impegni elenco

```bash
magento-cloud commits [--limit LIMIT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<commit>]
```


```bash
commits
```


### `commit`

Il Git iniziale commit SHA. Questo può anche accettare i suffissi &quot;HEAD&quot; e &quot;caret&quot; (^) o &quot;tilde&quot; (~) per i commit dei genitori.


### `--limit`

Numero di commit da visualizzare.

- Predefinito: `10`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--format`

Il formato di output (&quot;tabella&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;normale&quot;)

- Predefinito: `table`
- Richiede un valore

### `--columns`

Colonne da visualizzare (elenco separato da virgole o valori multipli)

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non trasmettere l&#39;intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--date-fmt`

Formato data (come stringa formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `db:dump`

Crea un dump locale del database remoto

```bash
magento-cloud db:dump [--schema SCHEMA] [-f|--file FILE] [-d|--directory DIRECTORY] [-z|--gzip] [-t|--timestamp] [-o|--stdout] [--table TABLE] [--exclude-table EXCLUDE-TABLE] [--schema-only] [--charset CHARSET] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE]
```


```bash
sql-dump
```


```bash
environment:sql-dump
```

### `--schema`

Lo schema da scaricare. Ometti di utilizzare lo schema predefinito (in genere &quot;principale&quot;).

- Richiede un valore

### `--file`, `-f`

Un nome file personalizzato per il dump

- Richiede un valore

### `--directory`, `-d`

Una directory personalizzata per il dump

- Richiede un valore

### `--gzip`, `-z`

Comprimi il dump utilizzando gzip

- Predefinito: `false`
- Non accetta un valore

### `--timestamp`, `-t`

Aggiungi una marca temporale al nome del file immagine

- Predefinito: `false`
- Non accetta un valore

### `--stdout`, `-o`

Output in STDOUT invece di un file

- Predefinito: `false`
- Non accetta un valore

### `--table`

Tabella da includere

- Predefinito: `[]`
- Richiede un valore

### `--exclude-table`

Tabella da escludere

- Predefinito: `[]`
- Richiede un valore

### `--schema-only`

Eseguire il dump solo degli schemi, nessun dato

- Predefinito: `false`
- Non accetta un valore

### `--charset`

Codifica set di caratteri per il dump

- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

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

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `db:size`

Stimare l&#39;utilizzo del disco di un database

```bash
magento-cloud db:size [-B|--bytes] [-C|--cleanup] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [--format FORMAT] [--columns COLUMNS] [--no-header] [-i|--identity-file IDENTITY-FILE]
```

### `--bytes`, `-B`

Mostra dimensioni in byte.

- Predefinito: `false`
- Non accetta un valore

### `--cleanup`, `-C`

Controlla se le tabelle possono essere pulite e mostrami i consigli (solo InnoDb).

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--relationship`, `-r`

Relazione di servizio da utilizzare

- Richiede un valore

### `--format`

Il formato di output (&quot;tabella&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;normale&quot;)

- Predefinito: `table`
- Richiede un valore

### `--columns`

Colonne da visualizzare (elenco separato da virgole o valori multipli)

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non trasmettere l&#39;intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--identity-file`, `-i`

Un’identità SSH (chiave privata) da utilizzare

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `db:sql`

Eseguire SQL nel database remoto

```bash
magento-cloud sql [--raw] [--schema SCHEMA] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [--] [<query>]
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

Produrre output grezzo, non tabulare

- Predefinito: `false`
- Non accetta un valore

### `--schema`

Schema da utilizzare. Ometti di utilizzare lo schema predefinito (in genere &quot;principale&quot;). Passa una stringa vuota per non utilizzare alcuno schema.

- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

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

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `domain:add`

Aggiungi un nuovo dominio al progetto

```bash
magento-cloud domain:add [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

Nome di dominio

- Obbligatorio

### `--cert`

Percorso del file di certificato per questo dominio

- Richiede un valore

### `--key`

Percorso del file della chiave privata per il certificato fornito.

- Richiede un valore

### `--chain`

Percorso del file della catena di certificati o dei file per il certificato fornito

- Predefinito: `[]`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendi il completamento dell’operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `domain:delete`

Eliminare un dominio dal progetto

```bash
magento-cloud domain:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

Nome di dominio

- Obbligatorio

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendi il completamento dell’operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `domain:get`

Mostra informazioni dettagliate per un dominio

```bash
magento-cloud domain:get [-P|--property PROPERTY] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [--] [<name>]
```


### `name`

Nome di dominio


### `--property`, `-P`

Proprietà di dominio da visualizzare

- Richiede un valore

### `--format`

Il formato di output (&quot;tabella&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;normale&quot;)

- Predefinito: `table`
- Richiede un valore

### `--columns`

Colonne da visualizzare (elenco separato da virgole o valori multipli)

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non trasmettere l&#39;intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--date-fmt`

Formato data (come stringa formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `domain:list`

Ottieni un elenco di tutti i domini

```bash
magento-cloud domains [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```


```bash
domains
```

### `--format`

Il formato di output (&quot;tabella&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;normale&quot;)

- Predefinito: `table`
- Richiede un valore

### `--columns`

Colonne da visualizzare (elenco separato da virgole o valori multipli)

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non trasmettere l&#39;intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `domain:update`

Aggiornare un dominio

```bash
magento-cloud domain:update [--cert CERT] [--key KEY] [--chain CHAIN] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

Nome di dominio

- Obbligatorio

### `--cert`

Percorso del file di certificato per questo dominio

- Richiede un valore

### `--key`

Percorso del file della chiave privata per il certificato fornito.

- Richiede un valore

### `--chain`

Percorso del file della catena di certificati o dei file per il certificato fornito

- Predefinito: `[]`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendi il completamento dell’operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `environment:activate`

Attivare un ambiente

```bash
magento-cloud environment:activate [--parent PARENT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]...
```


### `environment`

Ambiente da attivare

- Predefinito: `[]`

- Array

### `--parent`

Impostare un nuovo elemento padre dell&#39;ambiente prima di attivare

- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendi il completamento dell’operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `environment:branch`

Ramo di un ambiente

```bash
magento-cloud branch [--title TITLE] [--type TYPE] [--force] [--no-clone-parent] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [-i|--identity-file IDENTITY-FILE] [--] [<id>] [<parent>]
```


```bash
branch
```


### `id`

ID (nome ramo) del nuovo ambiente


### `parent`

Elemento padre del nuovo ambiente


### `--title`

Il titolo del nuovo ambiente

- Richiede un valore

### `--type`

Tipo del nuovo ambiente

- Richiede un valore

### `--force`

Crea il nuovo ambiente anche se il ramo non può essere estratto localmente

- Predefinito: `false`
- Non accetta un valore

### `--no-clone-parent`

Non duplicare i dati del ramo principale

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendi il completamento dell’operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--identity-file`, `-i`

Un’identità SSH (chiave privata) da utilizzare

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `environment:checkout`

Controllare un ambiente

```bash
magento-cloud checkout [-i|--identity-file IDENTITY-FILE] [--] [<id>]
```


```bash
checkout
```


### `id`

ID dell’ambiente da estrarre. Ad esempio: &quot;sprint2&quot;


### `--identity-file`, `-i`

Un’identità SSH (chiave privata) da utilizzare

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `environment:curl`

Esegui una richiesta cURL autenticata sull’API di un ambiente

```bash
magento-cloud environment:curl [-X|--request REQUEST] [-d|--data DATA] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-f|--fail] [-H|--header HEADER] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<path>]
```


### `path`

Percorso API


### `--request`, `-X`

Il metodo di richiesta da utilizzare

- Richiede un valore

### `--data`, `-d`

Dati da inviare

- Richiede un valore

### `--include`, `-i`

Includi intestazioni nell&#39;output

- Predefinito: `false`
- Non accetta un valore

### `--head`, `-I`

Solo intestazioni di recupero

- Predefinito: `false`
- Non accetta un valore

### `--disable-compression`

Non utilizzare il flag curl —compressed

- Predefinito: `false`
- Non accetta un valore

### `--enable-glob`

Abilita la globbing curl (rimuovi la bandiera —globoff)

- Predefinito: `false`
- Non accetta un valore

### `--fail`, `-f`

Errore senza output in una risposta di errore

- Predefinito: `false`
- Non accetta un valore

### `--header`, `-H`

Intestazioni supplementari

- Predefinito: `[]`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `environment:delete`

Eliminare un ambiente

```bash
magento-cloud environment:delete [--delete-branch] [--no-delete-branch] [--inactive] [--merged] [--type TYPE] [--exclude EXCLUDE] [--exclude-type EXCLUDE-TYPE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]...
```


```bash
environment:deactivate
```


### `environment`

Ambiente da eliminare. Il carattere % può essere utilizzato come carattere jolly. Se viene specificato un singolo valore, questo viene suddiviso per virgole o spazi bianchi.

- Predefinito: `[]`

- Array

### `--delete-branch`

Elimina i rami Git remoti

- Predefinito: `false`
- Non accetta un valore

### `--no-delete-branch`

Non eliminare i rami Git remoti

- Predefinito: `false`
- Non accetta un valore

### `--inactive`

Elimina tutti gli ambienti inattivi

- Predefinito: `false`
- Non accetta un valore

### `--merged`

Elimina tutti gli ambienti uniti

- Predefinito: `false`
- Non accetta un valore

### `--type`

Tipi di ambiente di cui eliminare Se viene specificato un singolo valore, questo verrà suddiviso per virgole o spazi bianchi.

- Predefinito: `[]`
- Richiede un valore

### `--exclude`

Ambiente da non eliminare. Il carattere % può essere utilizzato come carattere jolly. Se viene specificato un singolo valore, questo viene suddiviso per virgole o spazi bianchi.

- Predefinito: `[]`
- Richiede un valore

### `--exclude-type`

Tipi di ambiente di cui non eliminare Se viene specificato un singolo valore, questo verrà suddiviso per virgole o spazi bianchi.

- Predefinito: `[]`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendi il completamento dell’operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `environment:http-access`

Aggiornare le impostazioni di accesso HTTP per un ambiente

```bash
magento-cloud httpaccess [--access ACCESS] [--auth AUTH] [--enabled ENABLED] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait]
```


```bash
httpaccess
```

### `--access`

Restrizione di accesso nel formato &quot;permission:address&quot;. Utilizza 0 per cancellare tutti gli indirizzi.

- Predefinito: `[]`
- Richiede un valore

### `--auth`

Credenziali di autenticazione HTTP Basic nel formato &quot;username:password&quot;. Utilizzare 0 per cancellare tutte le credenziali.

- Predefinito: `[]`
- Richiede un valore

### `--enabled`

Specifica se il controllo di accesso deve essere abilitato: 1 per abilitare, 0 per disabilitare

- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendi il completamento dell’operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `environment:info`

Proprietà di lettura o impostazione per un ambiente

```bash
magento-cloud environment:info [--refresh] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<property>] [<value>]
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

Formato data (come stringa formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--format`

Il formato di output (&quot;tabella&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;normale&quot;)

- Predefinito: `table`
- Richiede un valore

### `--columns`

Colonne da visualizzare (elenco separato da virgole o valori multipli)

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non trasmettere l&#39;intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendi il completamento dell’operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `environment:init`

Inizializzare un ambiente da un archivio Git pubblico

```bash
magento-cloud environment:init [--profile PROFILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <url>
```


### `url`

Un URL per un archivio Git

- Obbligatorio

### `--profile`

Nome del profilo

- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendi il completamento dell’operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `environment:list`

Ottieni un elenco di ambienti

```bash
magento-cloud environment:list [-I|--no-inactive] [--pipe] [--refresh REFRESH] [--sort SORT] [--reverse] [--type TYPE] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
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

Invia un semplice elenco di ID ambiente.

- Predefinito: `false`
- Non accetta un valore

### `--refresh`

Se aggiornare l’elenco.

- Predefinito: `1`
- Richiede un valore

### `--sort`

Una proprietà per l&#39;ordinamento

- Predefinito: `title`
- Richiede un valore

### `--reverse`

Ordina in ordine inverso (decrescente)

- Predefinito: `false`
- Non accetta un valore

### `--type`

Filtrare l’elenco per tipo di ambiente. Se viene specificato un singolo valore, questo viene suddiviso per virgole o spazi bianchi.

- Predefinito: `[]`
- Richiede un valore

### `--format`

Il formato di output (&quot;tabella&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;normale&quot;)

- Predefinito: `table`
- Richiede un valore

### `--columns`

Colonne da visualizzare (elenco separato da virgole o valori multipli)

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non trasmettere l&#39;intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `environment:logs`

Leggi i registri di un ambiente

```bash
magento-cloud log [--lines LINES] [--tail] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [--] [<type>]
```


```bash
log
```


```bash
logs
```


### `type`

Il tipo di log, ad esempio &quot;access&quot; o &quot;error&quot;


### `--lines`

Numero di righe da visualizzare

- Predefinito: `100`
- Richiede un valore

### `--tail`

Segna continuamente il registro

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--worker`

Nome di un lavoratore

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `environment:merge`

Unire un ambiente

```bash
magento-cloud merge [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]
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

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendi il completamento dell’operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `environment:push`

Implementare il codice in un ambiente

```bash
magento-cloud push [--target TARGET] [-f|--force] [--force-with-lease] [-u|--set-upstream] [--activate] [--branch] [--parent PARENT] [--type TYPE] [--no-clone-parent] [-W|--no-wait] [--wait] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-i|--identity-file IDENTITY-FILE] [--] [<source>]
```


```bash
push
```


### `source`

Riferimento di origine: un nome di ramo o un hash di commit

- Predefinito: `HEAD`


### `--target`

Nome del ramo di destinazione

- Richiede un valore

### `--force`, `-f`

Consenti aggiornamenti non rapidi

- Predefinito: `false`
- Non accetta un valore

### `--force-with-lease`

Consenti aggiornamenti non rapidi se il ramo di tracciamento remoto è aggiornato

- Predefinito: `false`
- Non accetta un valore

### `--set-upstream`, `-u`

Imposta l’ambiente di destinazione come a monte per il ramo di origine

- Predefinito: `false`
- Non accetta un valore

### `--activate`

Attivare l&#39;ambiente prima di premere

- Predefinito: `false`
- Non accetta un valore

### `--branch`

OBSOLETO: alias di —activate

- Predefinito: `false`
- Non accetta un valore

### `--parent`

Imposta il nuovo elemento padre dell&#39;ambiente (utilizzato solo con —activate)

- Richiede un valore

### `--type`

Imposta il tipo di ambiente (utilizzato solo con —activate )

- Richiede un valore

### `--no-clone-parent`

Non clonare i dati del ramo principale (utilizzati solo con —activate)

- Predefinito: `false`
- Non accetta un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendi il completamento dell’operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--identity-file`, `-i`

Un’identità SSH (chiave privata) da utilizzare

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `environment:redeploy`

Ridistribuzione di un ambiente

```bash
magento-cloud redeploy [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait]
```


```bash
redeploy
```

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendi il completamento dell’operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `environment:relationships`

Mostra le relazioni di un ambiente

```bash
magento-cloud relationships [-P|--property PROPERTY] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE] [--] [<environment>]
```


```bash
relationships
```


### `environment`

L&#39;ambiente


### `--property`, `-P`

Proprietà della relazione da visualizzare

- Richiede un valore

### `--refresh`

Se aggiornare le relazioni

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--identity-file`, `-i`

Un’identità SSH (chiave privata) da utilizzare

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `environment:scp`

Copia i file in e dall’ambiente corrente utilizzando scp

```bash
magento-cloud scp [-r|--recursive] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE] [--] [<files>]...
```


```bash
scp
```


### `files`

File da copiare. Utilizzare il telecomando: Prefisso per definire le posizioni remote.

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

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--worker`

Nome di un lavoratore

- Richiede un valore

### `--identity-file`, `-i`

Un’identità SSH (chiave privata) da utilizzare

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `environment:set-remote`

Impostare l&#39;ambiente remoto da mappare su un ramo

```bash
magento-cloud environment:set-remote <environment> [<branch>]
```


### `environment`

Nome del computer dell&#39;ambiente. Imposta su 0 per rimuovere la mappatura di un ramo

- Obbligatorio

### `branch`

Il ramo Git da mappare (impostazione predefinita del ramo corrente)


### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `environment:ssh`

SSH all’ambiente corrente

```bash
magento-cloud ssh [--pipe] [--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE] [--] [<cmd>]...
```


```bash
ssh
```


### `cmd`

Comando da eseguire nell&#39;ambiente.

- Predefinito: `[]`

- Array

### `--pipe`

Trasmetti solo l’URL SSH.

- Predefinito: `false`
- Non accetta un valore

### `--all`

Trasmetti tutti gli URL SSH (per ogni app).

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--worker`

Nome di un lavoratore

- Richiede un valore

### `--identity-file`, `-i`

Un’identità SSH (chiave privata) da utilizzare

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `environment:synchronize`

Sincronizzazione del codice e/o dei dati di un ambiente dal relativo elemento padre

```bash
magento-cloud sync [--rebase] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<synchronize>]...
```


```bash
sync
```


### `synchronize`

Cosa sincronizzare: &quot;code&quot;, &quot;data&quot; o entrambi

- Predefinito: `[]`

- Array

### `--rebase`

Sincronizza il codice tramite rebasing invece dell&#39;unione

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendi il completamento dell’operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `environment:url`

Ottenere gli URL pubblici di un ambiente

```bash
magento-cloud url [-1|--primary] [--browser BROWSER] [--pipe] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```


```bash
url
```

### `--primary`, `-1`

Restituisci solo l’URL della route principale

- Predefinito: `false`
- Non accetta un valore

### `--browser`

Il browser da utilizzare per aprire l’URL. Imposta 0 su Nessuno.

- Richiede un valore

### `--pipe`

Invia l’URL a stdout.

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `environment:xdebug`

Apri un tunnel a Xdebug nell&#39;ambiente

```bash
magento-cloud xdebug [--port PORT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE]
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

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--worker`

Nome di un lavoratore

- Richiede un valore

### `--identity-file`, `-i`

Un’identità SSH (chiave privata) da utilizzare

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `integration:activity:get`

Visualizzare informazioni dettagliate su una singola attività di integrazione

```bash
magento-cloud integration:activity:get [-P|--property PROPERTY] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [--] [<integration>] [<activity>]
```


### `integration`

Un ID integrazione. Lascia vuoto per scegliere da un elenco.


### `activity`

L&#39;ID attività. Impostazione predefinita dell’attività di integrazione più recente.


### `--property`, `-P`

Proprietà da visualizzare

- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

[Opzione obsoleta, non utilizzata]

- Richiede un valore

### `--format`

Il formato di output (&quot;tabella&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;normale&quot;)

- Predefinito: `table`
- Richiede un valore

### `--columns`

Colonne da visualizzare (elenco separato da virgole o valori multipli)

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non trasmettere l&#39;intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--date-fmt`

Formato data (come stringa formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `integration:activity:list`

Ottenere un elenco di attività per un’integrazione

```bash
magento-cloud i:act [--type TYPE] [-x|--exclude-type EXCLUDE-TYPE] [--limit LIMIT] [--start START] [--state STATE] [--result RESULT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<id>]
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

Filtrare le attività per tipo. Se viene specificato un singolo valore, questo viene suddiviso per virgole o spazi bianchi.

- Predefinito: `[]`
- Richiede un valore

### `--exclude-type`, `-x`

Escludi le attività per tipo. Se viene specificato un singolo valore, questo viene suddiviso per virgole o spazi bianchi.

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

Filtrare le attività per stato. Se viene specificato un singolo valore, questo viene suddiviso per virgole o spazi bianchi.

- Predefinito: `[]`
- Richiede un valore

### `--result`

Filtrare le attività in base ai risultati

- Richiede un valore

### `--format`

Il formato di output (&quot;tabella&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;normale&quot;)

- Predefinito: `table`
- Richiede un valore

### `--columns`

Colonne da visualizzare (elenco separato da virgole o valori multipli)

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non trasmettere l&#39;intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--date-fmt`

Formato data (come stringa formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

[Opzione obsoleta, non utilizzata]

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `integration:activity:log`

Visualizza il registro per un’attività di integrazione

```bash
magento-cloud integration:activity:log [-t|--timestamps] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<integration>] [<activity>]
```


### `integration`

Un ID integrazione. Lascia vuoto per scegliere da un elenco.


### `activity`

L&#39;ID attività. Impostazione predefinita dell’attività di integrazione più recente.


### `--timestamps`, `-t`

Visualizza una marca temporale accanto a ciascun messaggio

- Predefinito: `false`
- Non accetta un valore

### `--date-fmt`

Formato data (come stringa formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

[Opzione obsoleta, non utilizzata]

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `integration:add`

Aggiungi un’integrazione al progetto

```bash
magento-cloud integration:add [--type TYPE] [--base-url BASE-URL] [--username USERNAME] [--token TOKEN] [--key KEY] [--secret SECRET] [--server-project SERVER-PROJECT] [--repository REPOSITORY] [--build-merge-requests BUILD-MERGE-REQUESTS] [--build-pull-requests BUILD-PULL-REQUESTS] [--build-draft-pull-requests BUILD-DRAFT-PULL-REQUESTS] [--build-pull-requests-post-merge BUILD-PULL-REQUESTS-POST-MERGE] [--build-wip-merge-requests BUILD-WIP-MERGE-REQUESTS] [--merge-requests-clone-parent-data MERGE-REQUESTS-CLONE-PARENT-DATA] [--pull-requests-clone-parent-data PULL-REQUESTS-CLONE-PARENT-DATA] [--resync-pull-requests RESYNC-PULL-REQUESTS] [--fetch-branches FETCH-BRANCHES] [--prune-branches PRUNE-BRANCHES] [--url URL] [--shared-key SHARED-KEY] [--file FILE] [--events EVENTS] [--states STATES] [--environments ENVIRONMENTS] [--excluded-environments EXCLUDED-ENVIRONMENTS] [--from-address FROM-ADDRESS] [--recipients RECIPIENTS] [--channel CHANNEL] [--routing-key ROUTING-KEY] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait]
```

### `--type`

Tipo di integrazione (&#39;bitbucket&#39;, &#39;bitbucket_server&#39;, &#39;github&#39;, &#39;gitlab&#39;, &#39;webhook&#39;, &#39;health.email&#39;, &#39;health.pagerduty&#39;, &#39;health.slack&#39;, &#39;health.webhook&#39;, &#39;script&#39;)

- Richiede un valore

### `--base-url`

URL di base dell&#39;installazione del server

- Richiede un valore

### `--username`

Nome utente del server Bitbucket

- Richiede un valore

### `--token`

Token di accesso per l’integrazione

- Richiede un valore

### `--key`

Una chiave di consumo OAuth Bitbucket

- Richiede un valore

### `--secret`

Segreto consumer OAuth di Bitbucket

- Richiede un valore

### `--server-project`

Il progetto (ad es. &quot;namespace/repo&quot;)

- Richiede un valore

### `--repository`

Archivio da tracciare (ad es. &#39;proprietario/repository&#39;)

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

Creare richieste di pull di bozza

- Predefinito: `true`
- Richiede un valore

### `--build-pull-requests-post-merge`

Creare richieste di pull in base al loro stato post-unione

- Predefinito: `false`
- Richiede un valore

### `--build-wip-merge-requests`

GitLab: creare richieste di unione WIP

- Predefinito: `true`
- Richiede un valore

### `--merge-requests-clone-parent-data`

GitLab: clonare dati per le richieste di unione

- Predefinito: `true`
- Richiede un valore

### `--pull-requests-clone-parent-data`

Clonare i dati dell’ambiente padre per le richieste di pull

- Predefinito: `true`
- Richiede un valore

### `--resync-pull-requests`

Sincronizza nuovamente i dati dell&#39;ambiente della richiesta di pull su ogni build

- Predefinito: `false`
- Richiede un valore

### `--fetch-branches`

Recupera tutti i rami dal remoto (come ambienti inattivi)

- Predefinito: `true`
- Richiede un valore

### `--prune-branches`

Elimina rami non esistenti nel telecomando

- Predefinito: `true`
- Richiede un valore

### `--url`

Webhook: un URL per ricevere i dati JSON

- Richiede un valore

### `--shared-key`

Webhook: la chiave segreta condivisa di JWS

- Richiede un valore

### `--file`

Nome di un file locale contenente lo script da caricare

- Richiede un valore

### `--events`

Un elenco di eventi su cui intervenire, ad esempio environment.push

- Predefinito: `*`
- Richiede un valore

### `--states`

Elenco di stati su cui intervenire, ad esempio in sospeso, in_progress, complete

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

[Facoltativo] Indirizzo personalizzato da per e-mail di avviso

- Richiede un valore

### `--recipients`

Gli indirizzi e-mail del destinatario

- Predefinito: `[]`
- Richiede un valore

### `--channel`

Canale di Slack

- Richiede un valore

### `--routing-key`

Chiave di routing PagerDuty

- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendi il completamento dell’operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `integration:delete`

Eliminare un’integrazione da un progetto

```bash
magento-cloud integration:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<id>]
```


### `id`

ID integrazione. Lascia vuoto per scegliere da un elenco.


### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendi il completamento dell’operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `integration:get`

Visualizzare i dettagli di un’integrazione

```bash
magento-cloud integration:get [-P|--property [PROPERTY]] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [--] [<id>]
```


### `id`

Un ID integrazione. Lascia vuoto per scegliere da un elenco.


### `--property`, `-P`

Proprietà di integrazione da visualizzare

- Accetta un valore

### `--format`

Il formato di output (&quot;tabella&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;normale&quot;)

- Predefinito: `table`
- Richiede un valore

### `--columns`

Colonne da visualizzare (elenco separato da virgole o valori multipli)

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non trasmettere l&#39;intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `integration:list`

Visualizza un elenco delle integrazioni di progetto

```bash
magento-cloud integrations [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```


```bash
integrations
```

### `--format`

Il formato di output (&quot;tabella&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;normale&quot;)

- Predefinito: `table`
- Richiede un valore

### `--columns`

Colonne da visualizzare (elenco separato da virgole o valori multipli)

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non trasmettere l&#39;intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `integration:update`

Aggiornare un’integrazione

```bash
magento-cloud integration:update [--type TYPE] [--base-url BASE-URL] [--username USERNAME] [--token TOKEN] [--key KEY] [--secret SECRET] [--server-project SERVER-PROJECT] [--repository REPOSITORY] [--build-merge-requests BUILD-MERGE-REQUESTS] [--build-pull-requests BUILD-PULL-REQUESTS] [--build-draft-pull-requests BUILD-DRAFT-PULL-REQUESTS] [--build-pull-requests-post-merge BUILD-PULL-REQUESTS-POST-MERGE] [--build-wip-merge-requests BUILD-WIP-MERGE-REQUESTS] [--merge-requests-clone-parent-data MERGE-REQUESTS-CLONE-PARENT-DATA] [--pull-requests-clone-parent-data PULL-REQUESTS-CLONE-PARENT-DATA] [--resync-pull-requests RESYNC-PULL-REQUESTS] [--fetch-branches FETCH-BRANCHES] [--prune-branches PRUNE-BRANCHES] [--url URL] [--shared-key SHARED-KEY] [--file FILE] [--events EVENTS] [--states STATES] [--environments ENVIRONMENTS] [--excluded-environments EXCLUDED-ENVIRONMENTS] [--from-address FROM-ADDRESS] [--recipients RECIPIENTS] [--channel CHANNEL] [--routing-key ROUTING-KEY] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<id>]
```


### `id`

ID dell’integrazione da aggiornare


### `--type`

Tipo di integrazione (&#39;bitbucket&#39;, &#39;bitbucket_server&#39;, &#39;github&#39;, &#39;gitlab&#39;, &#39;webhook&#39;, &#39;health.email&#39;, &#39;health.pagerduty&#39;, &#39;health.slack&#39;, &#39;health.webhook&#39;, &#39;script&#39;)

- Richiede un valore

### `--base-url`

URL di base dell&#39;installazione del server

- Richiede un valore

### `--username`

Nome utente del server Bitbucket

- Richiede un valore

### `--token`

Token di accesso per l’integrazione

- Richiede un valore

### `--key`

Una chiave di consumo OAuth Bitbucket

- Richiede un valore

### `--secret`

Segreto consumer OAuth di Bitbucket

- Richiede un valore

### `--server-project`

Il progetto (ad es. &quot;namespace/repo&quot;)

- Richiede un valore

### `--repository`

Archivio da tracciare (ad es. &#39;proprietario/repository&#39;)

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

Creare richieste di pull di bozza

- Predefinito: `true`
- Richiede un valore

### `--build-pull-requests-post-merge`

Creare richieste di pull in base al loro stato post-unione

- Predefinito: `false`
- Richiede un valore

### `--build-wip-merge-requests`

GitLab: creare richieste di unione WIP

- Predefinito: `true`
- Richiede un valore

### `--merge-requests-clone-parent-data`

GitLab: clonare dati per le richieste di unione

- Predefinito: `true`
- Richiede un valore

### `--pull-requests-clone-parent-data`

Clonare i dati dell’ambiente padre per le richieste di pull

- Predefinito: `true`
- Richiede un valore

### `--resync-pull-requests`

Sincronizza nuovamente i dati dell&#39;ambiente della richiesta di pull su ogni build

- Predefinito: `false`
- Richiede un valore

### `--fetch-branches`

Recupera tutti i rami dal remoto (come ambienti inattivi)

- Predefinito: `true`
- Richiede un valore

### `--prune-branches`

Elimina rami non esistenti nel telecomando

- Predefinito: `true`
- Richiede un valore

### `--url`

Webhook: un URL per ricevere i dati JSON

- Richiede un valore

### `--shared-key`

Webhook: la chiave segreta condivisa di JWS

- Richiede un valore

### `--file`

Nome di un file locale contenente lo script da caricare

- Richiede un valore

### `--events`

Un elenco di eventi su cui intervenire, ad esempio environment.push

- Predefinito: `*`
- Richiede un valore

### `--states`

Elenco di stati su cui intervenire, ad esempio in sospeso, in_progress, complete

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

[Facoltativo] Indirizzo personalizzato da per e-mail di avviso

- Richiede un valore

### `--recipients`

Gli indirizzi e-mail del destinatario

- Predefinito: `[]`
- Richiede un valore

### `--channel`

Canale di Slack

- Richiede un valore

### `--routing-key`

Chiave di routing PagerDuty

- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendi il completamento dell’operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `integration:validate`

Convalidare un’integrazione esistente

```bash
magento-cloud integration:validate [-p|--project PROJECT] [--host HOST] [--] [<id>]
```


### `id`

Un ID integrazione. Lascia vuoto per scegliere da un elenco.


### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

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

Specificare le applicazioni da generare

- Predefinito: `[]`

- Array

### `--abslinks`, `-a`

Usa collegamenti assoluti

- Predefinito: `false`
- Non accetta un valore

### `--source`, `-s`

La directory di origine. Impostazione predefinita della directory principale del progetto corrente.

- Richiede un valore

### `--destination`, `-d`

La destinazione, a cui verrà collegata la directory principale web di ogni app. Predefinito: _www

- Richiede un valore

### `--copy`, `-c`

Copia in una directory di build, invece del collegamento simbolico dalla sorgente

- Predefinito: `false`
- Non accetta un valore

### `--clone`

Usa Git per clonare il HEAD corrente nella directory di compilazione

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

Non creare o utilizzare un archivio build

- Predefinito: `false`
- Non accetta un valore

### `--no-backup`

Non eseguire il backup della build precedente

- Predefinito: `false`
- Non accetta un valore

### `--no-cache`

Disattiva la memorizzazione in cache

- Predefinito: `false`
- Non accetta un valore

### `--no-build-hooks`

Non eseguire gli hook post-build

- Predefinito: `false`
- Non accetta un valore

### `--no-deps`

Non installare localmente le dipendenze della build

- Predefinito: `false`
- Non accetta un valore

### `--working-copy`

Drush: usa git per clonare un archivio di ciascun modulo Drupal anziché semplicemente scaricare una versione

- Predefinito: `false`
- Non accetta un valore

### `--concurrency`

Drush: imposta il numero di progetti simultanei che verranno elaborati contemporaneamente

- Predefinito: `4`
- Richiede un valore

### `--lock`

Drush: creare o aggiornare un file di blocco (disponibile solo con Drush versione 7+)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `local:clean`

Rimuovere le build di progetto precedenti

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

L&#39;età massima delle build, in secondi. Ignorato se non impostato.

- Richiede un valore

### `--include-active`

Elimina anche le build attive

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

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

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `mount:download`

Scaricare file da un montaggio, utilizzando rsync

```bash
magento-cloud mount:download [-a|--all] [-m|--mount MOUNT] [--target TARGET] [--source-path] [--delete] [--exclude EXCLUDE] [--include INCLUDE] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE]
```

### `--all`, `-a`

Scarica da tutti i montaggi

- Predefinito: `false`
- Non accetta un valore

### `--mount`, `-m`

Il montaggio (come percorso relativo all’app)

- Richiede un valore

### `--target`

La directory in cui verranno scaricati i file. Se si utilizza —all, il percorso di montaggio viene aggiunto

- Richiede un valore

### `--source-path`

Utilizza il percorso sorgente del montaggio (anziché il percorso di montaggio) come sottodirectory del target, quando viene utilizzato —all

- Predefinito: `false`
- Non accetta un valore

### `--delete`

Se eliminare file estranei nella directory di destinazione

- Predefinito: `false`
- Non accetta un valore

### `--exclude`

File da escludere dal download (pattern)

- Predefinito: `[]`
- Richiede un valore

### `--include`

File da includere nel download (pattern)

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

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--worker`

Nome di un lavoratore

- Richiede un valore

### `--identity-file`, `-i`

Un’identità SSH (chiave privata) da utilizzare

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `mount:list`

Ottieni un elenco di montaggi

```bash
magento-cloud mounts [--paths] [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER]
```


```bash
mounts
```

### `--paths`

Trasmettere solo i percorsi di montaggio (uno per riga)

- Predefinito: `false`
- Non accetta un valore

### `--refresh`

Se aggiornare la cache

- Predefinito: `false`
- Non accetta un valore

### `--format`

Il formato di output (&quot;tabella&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;normale&quot;)

- Predefinito: `table`
- Richiede un valore

### `--columns`

Colonne da visualizzare (elenco separato da virgole o valori multipli)

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non trasmettere l&#39;intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--worker`

Nome di un lavoratore

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `mount:size`

Controllare l&#39;utilizzo del disco dei montaggi

```bash
magento-cloud mount:size [-B|--bytes] [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER]
```

### `--bytes`, `-B`

Mostra dimensioni in byte

- Predefinito: `false`
- Non accetta un valore

### `--refresh`

Aggiornare la cache

- Predefinito: `false`
- Non accetta un valore

### `--format`

Il formato di output (&quot;tabella&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;normale&quot;)

- Predefinito: `table`
- Richiede un valore

### `--columns`

Colonne da visualizzare (elenco separato da virgole o valori multipli)

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non trasmettere l&#39;intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--identity-file`, `-i`

Un’identità SSH (chiave privata) da utilizzare

- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--worker`

Nome di un lavoratore

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `mount:upload`

Caricare i file su un montaggio, utilizzando rsync

```bash
magento-cloud mount:upload [--source SOURCE] [-m|--mount MOUNT] [--delete] [--exclude EXCLUDE] [--include INCLUDE] [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--worker WORKER] [-i|--identity-file IDENTITY-FILE]
```

### `--source`

Una directory contenente i file da caricare

- Richiede un valore

### `--mount`, `-m`

Il montaggio (come percorso relativo all’app)

- Richiede un valore

### `--delete`

Se eliminare file estranei nel montaggio

- Predefinito: `false`
- Non accetta un valore

### `--exclude`

File da escludere dal caricamento (pattern)

- Predefinito: `[]`
- Richiede un valore

### `--include`

File da includere nel caricamento (pattern)

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

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--worker`

Nome di un lavoratore

- Richiede un valore

### `--identity-file`, `-i`

Un’identità SSH (chiave privata) da utilizzare

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `project:clear-build-cache`

Cancellare la cache di compilazione di un progetto

```bash
magento-cloud project:clear-build-cache [-p|--project PROJECT] [--host HOST]
```

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `project:curl`

Esegui una richiesta cURL autenticata sull’API di un progetto

```bash
magento-cloud project:curl [-X|--request REQUEST] [-d|--data DATA] [-i|--include] [-I|--head] [--disable-compression] [--enable-glob] [-f|--fail] [-H|--header HEADER] [-p|--project PROJECT] [--host HOST] [--] [<path>]
```


### `path`

Percorso API


### `--request`, `-X`

Il metodo di richiesta da utilizzare

- Richiede un valore

### `--data`, `-d`

Dati da inviare

- Richiede un valore

### `--include`, `-i`

Includi intestazioni nell&#39;output

- Predefinito: `false`
- Non accetta un valore

### `--head`, `-I`

Solo intestazioni di recupero

- Predefinito: `false`
- Non accetta un valore

### `--disable-compression`

Non utilizzare il flag curl —compressed

- Predefinito: `false`
- Non accetta un valore

### `--enable-glob`

Abilita la globbing curl (rimuovi la bandiera —globoff)

- Predefinito: `false`
- Non accetta un valore

### `--fail`, `-f`

Errore senza output in una risposta di errore

- Predefinito: `false`
- Non accetta un valore

### `--header`, `-H`

Intestazioni supplementari

- Predefinito: `[]`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `project:get`

Clonazione locale di un progetto

```bash
magento-cloud get [-e|--environment ENVIRONMENT] [--depth DEPTH] [--build] [-p|--project PROJECT] [--host HOST] [-i|--identity-file IDENTITY-FILE] [--] [<project>] [<directory>]
```


```bash
get
```


### `project`

ID progetto


### `directory`

La directory in cui clonare. Impostazione predefinita del titolo del progetto


### `--environment`, `-e`

ID ambiente da clonare. Impostazioni predefinite per il progetto o per il primo ambiente disponibile

- Richiede un valore

### `--depth`

Crea un clone superficiale: limitare il numero di commit nella cronologia

- Richiede un valore

### `--build`

Crea il progetto dopo la clonazione

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--identity-file`, `-i`

Un’identità SSH (chiave privata) da utilizzare

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `project:info`

Leggere o impostare le proprietà di un progetto

```bash
magento-cloud project:info [--refresh] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<property>] [<value>]
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

Formato data (come stringa formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--format`

Il formato di output (&quot;tabella&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;normale&quot;)

- Predefinito: `table`
- Richiede un valore

### `--columns`

Colonne da visualizzare (elenco separato da virgole o valori multipli)

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non trasmettere l&#39;intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendi il completamento dell’operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `project:list`

Ottieni un elenco di tutti i progetti attivi

```bash
magento-cloud project:list [--pipe] [--host HOST] [--title TITLE] [--my] [--refresh REFRESH] [--sort SORT] [--reverse] [--page PAGE] [--count COUNT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT]
```


```bash
projects
```


```bash
pro
```

### `--pipe`

Invia un semplice elenco di ID di progetto. Questo disabilita l’impaginazione.

- Predefinito: `false`
- Non accetta un valore

### `--host`

Filtra per nome host regione (corrispondenza esatta)

- Richiede un valore

### `--title`

Filtra per titolo (ricerca senza distinzione tra maiuscole e minuscole)

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

Una proprietà per l&#39;ordinamento

- Predefinito: `title`
- Richiede un valore

### `--reverse`

Ordina in ordine inverso (decrescente)

- Predefinito: `false`
- Non accetta un valore

### `--page`

Numero pagina (a partire da 1)

- Predefinito: `1`
- Richiede un valore

### `--count`

Il numero di progetti da visualizzare per pagina. L&#39;impostazione predefinita si basa sull&#39;altezza del terminale. Utilizzare 0 per disabilitare l’impaginazione.

- Richiede un valore

### `--format`

Il formato di output (&quot;tabella&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;normale&quot;)

- Predefinito: `table`
- Richiede un valore

### `--columns`

Colonne da visualizzare (elenco separato da virgole o valori multipli)

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non trasmettere l&#39;intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--date-fmt`

Formato data (come stringa formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

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

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `project:variable:delete`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLETO ]&lt;/> Eliminare una variabile da un progetto

```bash
magento-cloud project:variable:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

Nome della variabile

- Obbligatorio

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendi il completamento dell’operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `project:variable:get`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLETO ]&lt;/> Visualizza variabili per un progetto

```bash
magento-cloud project:variable:get [--pipe] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [--] [<name>]
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

Trasmettere solo il valore della variabile completa (è necessario specificare un &quot;nome&quot;)

- Predefinito: `false`
- Non accetta un valore

### `--format`

Il formato di output (&quot;tabella&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;normale&quot;)

- Predefinito: `table`
- Richiede un valore

### `--columns`

Colonne da visualizzare (elenco separato da virgole o valori multipli)

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non trasmettere l&#39;intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `project:variable:set`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLETO ]&lt;/> Imposta una variabile per un progetto

```bash
magento-cloud pvset [--json] [--no-visible-build] [--no-visible-runtime] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <name> <value>
```


```bash
pvset
```


### `name`

Nome della variabile

- Obbligatorio

### `value`

Valore variabile

- Obbligatorio

### `--json`

Contrassegna il valore come JSON

- Predefinito: `false`
- Non accetta un valore

### `--no-visible-build`

Non esporre questa variabile in fase di compilazione

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

Nome host API del progetto

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendi il completamento dell’operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `repo:cat`

Leggi un file nell’archivio del progetto

```bash
magento-cloud repo:cat [-c|--commit COMMIT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] <path>
```


### `path`

Percorso del file

- Obbligatorio

### `--commit`, `-c`

Il commettere SHA. Questo può anche accettare i suffissi &quot;HEAD&quot; e &quot;caret&quot; (^) o &quot;tilde&quot; (~) per i commit dei genitori.

- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `repo:ls`

Elencare file nell’archivio del progetto

```bash
magento-cloud repo:ls [-d|--directories] [-f|--files] [--git-style] [-c|--commit COMMIT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<path>]
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

Output di stile simile a &quot;git ls-tree&quot;

- Predefinito: `false`
- Non accetta un valore

### `--commit`, `-c`

Il commettere SHA. Questo può anche accettare i suffissi &quot;HEAD&quot; e &quot;caret&quot; (^) o &quot;tilde&quot; (~) per i commit dei genitori.

- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `repo:read`

Leggi una directory o un file nell’archivio del progetto

```bash
magento-cloud read [-c|--commit COMMIT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<path>]
```


```bash
read
```


### `path`

Percorso della directory o del file


### `--commit`, `-c`

Il commettere SHA. Questo può anche accettare i suffissi &quot;HEAD&quot; e &quot;caret&quot; (^) o &quot;tilde&quot; (~) per i commit dei genitori.

- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `route:get`

Visualizza informazioni dettagliate su un percorso

```bash
magento-cloud route:get [--id ID] [-1|--primary] [-P|--property PROPERTY] [--refresh] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE] [--] [<route>]
```


### `route`

URL originale della route


### `--id`

Un ID di route da selezionare

- Richiede un valore

### `--primary`, `-1`

Selezionare il percorso principale

- Predefinito: `false`
- Non accetta un valore

### `--property`, `-P`

Proprietà da visualizzare

- Richiede un valore

### `--refresh`

Ignora la cache dei percorsi

- Predefinito: `false`
- Non accetta un valore

### `--date-fmt`

Formato data (come stringa formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--app`, `-A`

[Opzione obsoleta, non più utilizzata]

- Richiede un valore

### `--identity-file`, `-i`

[Opzione obsoleta, non più utilizzata]

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `route:list`

Elencare tutti i percorsi per un ambiente

```bash
magento-cloud routes [--refresh] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--] [<environment>]
```


```bash
routes
```


```bash
environment:routes
```


### `environment`

ID ambiente


### `--refresh`

Ignora la cache dei percorsi

- Predefinito: `false`
- Non accetta un valore

### `--format`

Il formato di output (&quot;tabella&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;normale&quot;)

- Predefinito: `table`
- Richiede un valore

### `--columns`

Colonne da visualizzare (elenco separato da virgole o valori multipli)

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non trasmettere l&#39;intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `self:install`

Installa o aggiorna i file di configurazione CLI

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

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `self:stats`

Visualizzare gli stati sui download dei pacchetti GitHub

```bash
magento-cloud self:stats [-p|--page PAGE] [-c|--count COUNT] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT]
```

### `--page`, `-p`

Numero di pagina

- Predefinito: `1`
- Richiede un valore

### `--count`, `-c`

Risultati per pagina (max: 100)

- Predefinito: `20`
- Richiede un valore

### `--format`

Il formato di output (&quot;tabella&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;normale&quot;)

- Predefinito: `table`
- Richiede un valore

### `--columns`

Colonne da visualizzare (elenco separato da virgole o valori multipli)

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non trasmettere l&#39;intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--date-fmt`

Formato data (come stringa formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `self:update`

Aggiorna CLI alla versione più recente

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

Solo aggiornamento tra versioni secondarie o patch

- Predefinito: `false`
- Non accetta un valore

### `--unstable`

Aggiornamento a una nuova versione instabile, se disponibile

- Predefinito: `false`
- Non accetta un valore

### `--manifest`

Escludere la posizione del file manifesto

- Richiede un valore

### `--current-version`

Ignora la versione corrente

- Richiede un valore

### `--timeout`

Timeout per il controllo della versione

- Predefinito: `30`
- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `service:list`

Elencare servizi nel progetto

```bash
magento-cloud services [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header]
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

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--format`

Il formato di output (&quot;tabella&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;normale&quot;)

- Predefinito: `table`
- Richiede un valore

### `--columns`

Colonne da visualizzare (elenco separato da virgole o valori multipli)

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non trasmettere l&#39;intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `service:mongo:dump`

Crea un dump di dati di archivio binario da MongoDB

```bash
magento-cloud mongodump [-c|--collection COLLECTION] [-z|--gzip] [-o|--stdout] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```


```bash
mongodump
```

### `--collection`, `-c`

La raccolta da scaricare

- Richiede un valore

### `--gzip`, `-z`

Comprimi il dump utilizzando gzip

- Predefinito: `false`
- Non accetta un valore

### `--stdout`, `-o`

Output in STDOUT invece di un file

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

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `service:mongo:export`

Esportare dati da MongoDB

```bash
magento-cloud mongoexport [-c|--collection COLLECTION] [--jsonArray] [--type TYPE] [-f|--fields FIELDS] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```


```bash
mongoexport
```

### `--collection`, `-c`

La raccolta da esportare

- Richiede un valore

### `--jsonArray`

Esportare i dati come un singolo array JSON

- Predefinito: `false`
- Non accetta un valore

### `--type`

Il tipo di esportazione, ad esempio &quot;csv&quot;

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

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `service:mongo:restore`

Ripristinare un dump di dati di archivio binario in MongoDB

```bash
magento-cloud mongorestore [-c|--collection COLLECTION] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```


```bash
mongorestore
```

### `--collection`, `-c`

La raccolta da ripristinare

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

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `service:mongo:shell`

Utilizzare la shell MongoDB

```bash
magento-cloud mongo [--eval EVAL] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```


```bash
mongo
```

### `--eval`

Passa un frammento JavaScript alla shell

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

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `service:redis-cli`

Accedere alla CLI di Redis

```bash
magento-cloud redis [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--] [<args>]
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

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `session:switch`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ BETA ]&lt;/> Passa da una sessione all&#39;altra

```bash
magento-cloud session:switch [<id>]
```


### `id`

Il nuovo ID sessione


### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `snapshot:create`

Creare un’istantanea di un ambiente

```bash
magento-cloud backup [--live] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<environment>]
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

Backup live: non interrompere l&#39;ambiente. Se impostato, questo consente l&#39;esecuzione dell&#39;ambiente e l&#39;apertura alle connessioni durante il backup. Questo consente di ridurre i tempi di inattività, a rischio di backup dei dati in uno stato incoerente.

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendi il completamento dell’operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `snapshot:list`

Elencare le istantanee disponibili di un ambiente

```bash
magento-cloud snapshots [--limit LIMIT] [--start START] [--format FORMAT] [--columns COLUMNS] [--no-header] [--date-fmt DATE-FMT] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
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

Limita il numero di istantanee da elencare

- Richiede un valore

### `--start`

[Obsoleto] - questa opzione non è utilizzata

- Richiede un valore

### `--format`

Il formato di output (&quot;tabella&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;normale&quot;)

- Predefinito: `table`
- Richiede un valore

### `--columns`

Colonne da visualizzare (elenco separato da virgole o valori multipli)

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non trasmettere l&#39;intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--date-fmt`

Formato data (come stringa formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `snapshot:restore`

Ripristinare un&#39;istantanea dell&#39;ambiente

```bash
magento-cloud snapshot:restore [--target TARGET] [--branch-from BRANCH-FROM] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<snapshot>]
```


```bash
environment:restore
```


```bash
backup:restore
```


### `snapshot`

Nome dell&#39;istantanea. Impostazioni predefinite per la versione più recente


### `--target`

L’ambiente in cui eseguire il ripristino. Impostazioni predefinite nell&#39;ambiente corrente dello snapshot

- Richiede un valore

### `--branch-from`

Se l&#39;oggetto —target non esiste ancora, specifica l&#39;elemento padre del nuovo ambiente

- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendi il completamento dell’operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `source-operation:run`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ BETA ]&lt;/> Eseguire un&#39;operazione sorgente

```bash
magento-cloud source-operation:run [--variable VARIABLE] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <operation>
```


### `operation`

Nome dell&#39;operazione

- Obbligatorio

### `--variable`

Variabile da impostare durante l&#39;operazione, nel formato &lt;info>type:name=value&lt;/info>

- Predefinito: `[]`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendi il completamento dell’operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

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

Formato data (come stringa formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

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

[Obsoleto] Usa —new invece

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

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

Un nome per identificare la chiave

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

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

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `ssh-key:list`

Ottieni un elenco di chiavi SSH nel tuo account

```bash
magento-cloud ssh-keys [--format FORMAT] [--columns COLUMNS] [--no-header]
```


```bash
ssh-keys
```

### `--format`

Il formato di output (&quot;tabella&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;normale&quot;)

- Predefinito: `table`
- Richiede un valore

### `--columns`

Colonne da visualizzare (elenco separato da virgole o valori multipli)

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non trasmettere l&#39;intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `subscription:info`

Leggere o modificare le proprietà della sottoscrizione

```bash
magento-cloud subscription:info [-s|--id ID] [--date-fmt DATE-FMT] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [--] [<property>] [<value>]
```


### `property`

Nome della proprietà


### `value`

Imposta un nuovo valore per la proprietà


### `--id`, `-s`

ID sottoscrizione

- Richiede un valore

### `--date-fmt`

Formato data (come stringa formato data PHP)

- Predefinito: `c`
- Richiede un valore

### `--format`

Il formato di output (&quot;tabella&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;normale&quot;)

- Predefinito: `table`
- Richiede un valore

### `--columns`

Colonne da visualizzare (elenco separato da virgole o valori multipli)

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non trasmettere l&#39;intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `tunnel:close`

Chiudi tunnel SSH

```bash
magento-cloud tunnel:close [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP]
```

### `--all`, `-a`

Chiudi tutti i tunnel

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `tunnel:info`

Visualizza informazioni sulle relazioni per i tunnel SSH

```bash
magento-cloud tunnel:info [-P|--property PROPERTY] [-c|--encode] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--format FORMAT] [--columns COLUMNS] [--no-header]
```

### `--property`, `-P`

Proprietà della relazione da visualizzare

- Richiede un valore

### `--encode`, `-c`

Output come JSON codificato base64

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--format`

Il formato di output (&quot;tabella&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;normale&quot;)

- Predefinito: `table`
- Richiede un valore

### `--columns`

Colonne da visualizzare (elenco separato da virgole o valori multipli)

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non trasmettere l&#39;intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `tunnel:list`

Elencare tunnel SSH

```bash
magento-cloud tunnels [-a|--all] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [--format FORMAT] [--columns COLUMNS] [--no-header]
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

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--format`

Il formato di output (&quot;tabella&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;normale&quot;)

- Predefinito: `table`
- Richiede un valore

### `--columns`

Colonne da visualizzare (elenco separato da virgole o valori multipli)

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non trasmettere l&#39;intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `tunnel:open`

Aprire i tunnel SSH alle relazioni di un&#39;app

```bash
magento-cloud tunnel:open [-g|--gateway-ports] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-i|--identity-file IDENTITY-FILE]
```

### `--gateway-ports`, `-g`

Consenti agli host remoti di connettersi alle porte inoltrate locali

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--app`, `-A`

Nome dell&#39;applicazione remota

- Richiede un valore

### `--identity-file`, `-i`

Un’identità SSH (chiave privata) da utilizzare

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `tunnel:single`

Apri un singolo tunnel SSH per una relazione di app

```bash
magento-cloud tunnel:single [--port PORT] [-g|--gateway-ports] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-A|--app APP] [-r|--relationship RELATIONSHIP] [-i|--identity-file IDENTITY-FILE]
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

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

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

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `user:add`

Aggiungi un utente al progetto

```bash
magento-cloud user:add [-r|--role ROLE] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<email>]
```


### `email`

Indirizzo e-mail dell’utente


### `--role`, `-r`

Ruolo di progetto dell’utente (&quot;admin&quot; o &quot;viewer&quot;) o ruolo di tipo di ambiente (ad esempio &#39;staging:contributor&#39; o &#39;production:viewer&#39;). Per rimuovere un utente da un tipo di ambiente, imposta il ruolo come &#39;none&#39;. Il carattere % può essere utilizzato come carattere jolly per il tipo di ambiente, ad esempio &#39;%:viewer&#39; per assegnare all&#39;utente il ruolo di &#39;viewer&#39; su tutti i tipi. Il ruolo può essere abbreviato, ad esempio &#39;produzione:v&#39;.

- Predefinito: `[]`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendi il completamento dell’operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `user:delete`

Eliminare un utente dal progetto

```bash
magento-cloud user:delete [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] <email>
```


### `email`

Indirizzo e-mail dell’utente

- Obbligatorio

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendi il completamento dell’operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `user:get`

Visualizzare i ruoli di un utente

```bash
magento-cloud user:get [-l|--level LEVEL] [--pipe] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [-r|--role ROLE] [--] [<email>]
```


```bash
user:role
```


### `email`

Indirizzo e-mail dell’utente


### `--level`, `-l`

Livello del ruolo (&quot;progetto&quot; o &quot;ambiente&quot;)

- Richiede un valore

### `--pipe`

Trasmettere il ruolo a stdout (dopo aver apportato eventuali modifiche)

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendi il completamento dell’operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--role`, `-r`

[Obsoleto: utilizzare user:update per modificare i ruoli di un utente]

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `user:list`

Elencare utenti del progetto

```bash
magento-cloud users [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST]
```


```bash
users
```

### `--format`

Il formato di output (&quot;tabella&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;normale&quot;)

- Predefinito: `table`
- Richiede un valore

### `--columns`

Colonne da visualizzare (elenco separato da virgole o valori multipli)

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non trasmettere l&#39;intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `user:update`

Aggiornare i ruoli utente di un progetto

```bash
magento-cloud user:update [-r|--role ROLE] [-p|--project PROJECT] [--host HOST] [-W|--no-wait] [--wait] [--] [<email>]
```


### `email`

Indirizzo e-mail dell’utente


### `--role`, `-r`

Ruolo di progetto dell’utente (&quot;admin&quot; o &quot;viewer&quot;) o ruolo di tipo di ambiente (ad esempio &#39;staging:contributor&#39; o &#39;production:viewer&#39;). Per rimuovere un utente da un tipo di ambiente, imposta il ruolo come &#39;none&#39;. Il carattere % può essere utilizzato come carattere jolly per il tipo di ambiente, ad esempio &#39;%:viewer&#39; per assegnare all&#39;utente il ruolo di &#39;viewer&#39; su tutti i tipi. Il ruolo può essere abbreviato, ad esempio &#39;produzione:v&#39;.

- Predefinito: `[]`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendi il completamento dell’operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `variable:create`

Creare una variabile

```bash
magento-cloud variable:create [-l|--level LEVEL] [--name NAME] [--value VALUE] [--json JSON] [--sensitive SENSITIVE] [--prefix PREFIX] [--enabled ENABLED] [--inheritable INHERITABLE] [--visible-build VISIBLE-BUILD] [--visible-runtime VISIBLE-RUNTIME] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] [<name>]
```


### `name`

Nome della variabile


### `--level`, `-l`

Livello a cui impostare la variabile (&quot;project&quot; o &quot;environment&quot;)

- Richiede un valore

### `--name`

Nome della variabile

- Richiede un valore

### `--value`

Valore della variabile

- Richiede un valore

### `--json`

Se la variabile è formattata con JSON

- Predefinito: `false`
- Richiede un valore

### `--sensitive`

Se la variabile è sensibile

- Predefinito: `false`
- Richiede un valore

### `--prefix`

Prefisso del nome della variabile (ad es. &#39;none&#39; o &#39;env:&#39;)

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

Se la variabile deve essere visibile in fase di creazione

- Richiede un valore

### `--visible-runtime`

Se la variabile deve essere visibile in fase di runtime

- Predefinito: `true`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendi il completamento dell’operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `variable:delete`

Eliminare una variabile

```bash
magento-cloud variable:delete [-l|--level LEVEL] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

Nome della variabile

- Obbligatorio

### `--level`, `-l`

Livello variabile (&quot;progetto&quot;, &quot;ambiente&quot;, &quot;p&quot; o &quot;e&quot;)

- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendi il completamento dell’operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `variable:disable`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLETO ]&lt;/> Disattivare una variabile abilitata a livello di ambiente

```bash
magento-cloud variable:disable [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

Nome della variabile

- Obbligatorio

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendi il completamento dell’operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `variable:enable`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLETO ]&lt;/> Attivare una variabile disattivata a livello di ambiente

```bash
magento-cloud variable:enable [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

Nome della variabile

- Obbligatorio

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendi il completamento dell’operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `variable:get`

Visualizzare una variabile

```bash
magento-cloud vget [-P|--property PROPERTY] [-l|--level LEVEL] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--pipe] [--] [<name>]
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

Livello variabile (&quot;progetto&quot;, &quot;ambiente&quot;, &quot;p&quot; o &quot;e&quot;)

- Richiede un valore

### `--format`

Il formato di output (&quot;tabella&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;normale&quot;)

- Predefinito: `table`
- Richiede un valore

### `--columns`

Colonne da visualizzare (elenco separato da virgole o valori multipli)

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non trasmettere l&#39;intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--pipe`

[Opzione obsoleta] Trasmettere solo il valore della variabile

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `variable:list`

Variabili elenco

```bash
magento-cloud variable:list [-l|--level LEVEL] [--format FORMAT] [--columns COLUMNS] [--no-header] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT]
```


```bash
variables
```


```bash
var
```

### `--level`, `-l`

Livello variabile (&quot;progetto&quot;, &quot;ambiente&quot;, &quot;p&quot; o &quot;e&quot;)

- Richiede un valore

### `--format`

Il formato di output (&quot;tabella&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;normale&quot;)

- Predefinito: `table`
- Richiede un valore

### `--columns`

Colonne da visualizzare (elenco separato da virgole o valori multipli)

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non trasmettere l&#39;intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `variable:set`

&lt;fg white=&quot;&quot; bg=&quot;red&quot;>[ OBSOLETO ]&lt;/> Imposta una variabile per un ambiente

```bash
magento-cloud vset [--json] [--disabled] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name> <value>
```


```bash
vset
```


### `name`

Nome della variabile

- Obbligatorio

### `value`

Valore variabile

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

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendi il completamento dell’operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `variable:update`

Aggiornare una variabile

```bash
magento-cloud variable:update [-l|--level LEVEL] [--value VALUE] [--json JSON] [--sensitive SENSITIVE] [--enabled ENABLED] [--inheritable INHERITABLE] [--visible-build VISIBLE-BUILD] [--visible-runtime VISIBLE-RUNTIME] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [-W|--no-wait] [--wait] [--] <name>
```


### `name`

Nome della variabile

- Obbligatorio

### `--level`, `-l`

Livello variabile (&quot;progetto&quot;, &quot;ambiente&quot;, &quot;p&quot; o &quot;e&quot;)

- Richiede un valore

### `--value`

Valore della variabile

- Richiede un valore

### `--json`

Se la variabile è formattata con JSON

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

Se la variabile deve essere visibile in fase di creazione

- Richiede un valore

### `--visible-runtime`

Se la variabile deve essere visibile in fase di runtime

- Predefinito: `true`
- Richiede un valore

### `--project`, `-p`

ID o URL del progetto

- Richiede un valore

### `--host`

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--no-wait`, `-W`

Non attendere il completamento dell&#39;operazione

- Predefinito: `false`
- Non accetta un valore

### `--wait`

Attendi il completamento dell’operazione (impostazione predefinita)

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore


## `worker:list`

Ottenere un elenco di tutti i lavoratori distribuiti

```bash
magento-cloud workers [--refresh] [-p|--project PROJECT] [--host HOST] [-e|--environment ENVIRONMENT] [--format FORMAT] [--columns COLUMNS] [--no-header]
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

Nome host API del progetto

- Richiede un valore

### `--environment`, `-e`

ID ambiente

- Richiede un valore

### `--format`

Il formato di output (&quot;tabella&quot;, &quot;csv&quot;, &quot;tsv&quot; o &quot;normale&quot;)

- Predefinito: `table`
- Richiede un valore

### `--columns`

Colonne da visualizzare (elenco separato da virgole o valori multipli)

- Predefinito: `[]`
- Richiede un valore

### `--no-header`

Non trasmettere l&#39;intestazione della tabella

- Predefinito: `false`
- Non accetta un valore

### `--help`, `-h`

Visualizza il messaggio della guida

- Predefinito: `false`
- Non accetta un valore

### `--quiet`, `-q`

Non trasmettere messaggi

- Predefinito: `false`
- Non accetta un valore

### `--verbose`, `-v|-vv|-vvv`

Aumentare la verbosità dei messaggi

- Predefinito: `false`
- Non accetta un valore

### `--version`, `-V`

Visualizza questa versione dell&#39;applicazione

- Predefinito: `false`
- Non accetta un valore

### `--yes`, `-y`

Rispondere &quot;sì&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore

### `--no`, `-n`

Rispondere &quot;no&quot; a qualsiasi domanda sì/no; disattiva interazione

- Predefinito: `false`
- Non accetta un valore
