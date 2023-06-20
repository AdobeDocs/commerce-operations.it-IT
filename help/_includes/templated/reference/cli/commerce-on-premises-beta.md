---
source-git-commit: 64c453adabb092075854b2c20bf7da73c4a5146e
workflow-type: tm+mt
source-wordcount: '19899'
ht-degree: 0%

---
# bin/magento (Adobe Commerce on-premise)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->

**Versione**: 2.4.7-beta1

Questo riferimento contiene 132 comandi disponibili tramite `bin/magento` strumento da riga di comando.
L’elenco iniziale viene generato automaticamente utilizzando `bin/magento list` in Adobe Commerce.
Utilizza il [&quot;Aggiungi comandi CLI&quot;](https://developer.adobe.com/commerce/php/development/cli-commands/) per aggiungere un comando CLI personalizzato.

>[!NOTE]
>
>Puoi chiamare `bin/magento` Comandi CLI che utilizzano i tasti di scelta rapida anziché il nome completo del comando. Ad esempio, puoi chiamare `bin/magento setup:upgrade` utilizzo `bin/magento s:up`, `bin/magento s:upg`. Consulta [sintassi di scelta rapida](https://symfony.com/doc/current/components/console/usage.html#shortcut-syntax) per informazioni su come utilizzare le scelte rapide con qualsiasi comando CLI.

>[!NOTE]
>
>Questo riferimento viene generato dalla base di codice dell&#39;applicazione. Per modificare il contenuto, puoi aggiornare il codice sorgente per l’implementazione del comando corrispondente in [codebase](https://github.com/magento) e inviare le modifiche per la revisione. Un altro modo consiste nel _Inviaci feedback_ (trovi il collegamento in alto a destra). Per le linee guida sui contributi, consulta [Contributi codice](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `_complete`

Comando interno per fornire suggerimenti per il completamento della shell

```bash
bin/magento _complete [-s|--shell SHELL] [-i|--input INPUT] [-c|--current CURRENT] [-S|--symfony SYMFONY]
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
bin/magento completion [--debug] [--] [<shell>]
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
bin/magento help [--format FORMAT] [--raw] [--] [<command_name>]
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
bin/magento list [--raw] [--format FORMAT] [--short] [--] [<namespace>]
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


## `admin:adobe-ims:disable`

Disattiva modulo Adobe IMS

```bash
bin/magento admin:adobe-ims:disable
```

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


## `admin:adobe-ims:enable`

Abilita il modulo Adobe IMS.

```bash
bin/magento admin:adobe-ims:enable [-o|--organization-id [ORGANIZATION-ID]] [-c|--client-id [CLIENT-ID]] [-s|--client-secret [CLIENT-SECRET]] [-t|--2fa [2FA]]
```

### `--organization-id`, `-o`

Imposta l’ID organizzazione per la configurazione Adobe IMS. Obbligatorio quando si abilita il modulo

- Accetta un valore

### `--client-id`, `-c`

Imposta l’ID client per la configurazione Adobe IMS. Obbligatorio quando si abilita il modulo

- Accetta un valore

### `--client-secret`, `-s`

Imposta il segreto client per la configurazione Adobe IMS. Obbligatorio quando si abilita il modulo

- Accetta un valore

### `--2fa`, `-t`

Verificare se 2FA è abilitato per l&#39;organizzazione in Adobe Admin Console. Obbligatorio quando si abilita il modulo

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


## `admin:adobe-ims:info`

Informazioni sulla configurazione del modulo Adobe IMS

```bash
bin/magento admin:adobe-ims:info
```

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


## `admin:adobe-ims:status`

Stato del modulo Adobe IMS

```bash
bin/magento admin:adobe-ims:status
```

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


## `admin:user:create`

Crea un amministratore

```bash
bin/magento admin:user:create [--admin-user ADMIN-USER] [--admin-password ADMIN-PASSWORD] [--admin-email ADMIN-EMAIL] [--admin-firstname ADMIN-FIRSTNAME] [--admin-lastname ADMIN-LASTNAME] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--admin-user`

(Obbligatorio) Utente amministratore

- Richiede un valore

### `--admin-password`

(Obbligatorio) Password amministratore

- Richiede un valore

### `--admin-email`

(Obbligatorio) E-mail amministratore

- Richiede un valore

### `--admin-firstname`

(Obbligatorio) Nome amministratore

- Richiede un valore

### `--admin-lastname`

(Obbligatorio) Cognome amministratore

- Richiede un valore

### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;DIR_IMMAGINE[cache][path]=/var/tmp/cache&quot;

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


## `admin:user:unlock`

Sblocca account amministratore

```bash
bin/magento admin:user:unlock <username>
```


### `username`

Nome utente amministratore da sbloccare

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


## `app:config:dump`

Crea dump dell’applicazione

```bash
bin/magento app:config:dump [<config-types>...]
```


### `config-types`

Elenco separato da spazi dei tipi di configurazione o ometti di scaricare tutto [ambiti, sistema, temi, i18n]

- Predefinito: `[]`

- Array

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


## `app:config:import`

Importare dati da file di configurazione condivisi nell&#39;archivio dati appropriato

```bash
bin/magento app:config:import
```

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


## `app:config:status`

Controlla se la propagazione della configurazione richiede un aggiornamento

```bash
bin/magento app:config:status
```

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


## `braintree:migrate`

Migrazione di schede memorizzate da un database del Magento 1

```bash
bin/magento braintree:migrate [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password PASSWORD]
```

### `--host`

Nome host/IP. Porta opzionale

- Richiede un valore

### `--dbname`

Nome database

- Richiede un valore

### `--username`

Nome utente del database. Deve avere accesso in lettura

- Richiede un valore

### `--password`

Password

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


## `cache:clean`

Pulisce i tipi di cache

```bash
bin/magento cache:clean [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

Elenco separato da spazi dei tipi di cache o omesso da applicare a tutti i tipi di cache.

- Predefinito: `[]`

- Array

### `--bootstrap`

aggiungere o sostituire i parametri del bootstrap

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


## `cache:disable`

Disabilita i tipi di cache

```bash
bin/magento cache:disable [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

Elenco separato da spazi dei tipi di cache o omesso da applicare a tutti i tipi di cache.

- Predefinito: `[]`

- Array

### `--bootstrap`

aggiungere o sostituire i parametri del bootstrap

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


## `cache:enable`

Abilita i tipi di cache

```bash
bin/magento cache:enable [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

Elenco separato da spazi dei tipi di cache o omesso da applicare a tutti i tipi di cache.

- Predefinito: `[]`

- Array

### `--bootstrap`

aggiungere o sostituire i parametri del bootstrap

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


## `cache:flush`

Svuota la memoria cache utilizzata dai tipi di cache

```bash
bin/magento cache:flush [--bootstrap BOOTSTRAP] [--] [<types>...]
```


### `types`

Elenco separato da spazi dei tipi di cache o omesso da applicare a tutti i tipi di cache.

- Predefinito: `[]`

- Array

### `--bootstrap`

aggiungere o sostituire i parametri del bootstrap

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


## `cache:status`

Verifica lo stato della cache

```bash
bin/magento cache:status [--bootstrap BOOTSTRAP]
```

### `--bootstrap`

aggiungere o sostituire i parametri del bootstrap

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


## `catalog:images:resize`

Crea immagini prodotto ridimensionate

```bash
bin/magento catalog:images:resize [-a|--async] [--skip_hidden_images]
```

### `--async`, `-a`

Ridimensiona immagine in modalità asincrona

- Predefinito: `false`
- Non accetta un valore

### `--skip_hidden_images`

Non elaborare le immagini contrassegnate come nascoste dalla pagina prodotto

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


## `catalog:product:attributes:cleanup`

Rimuove gli attributi di prodotto inutilizzati.

```bash
bin/magento catalog:product:attributes:cleanup
```

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


## `cms:wysiwyg:restrict`

Imposta se applicare la convalida del contenuto di User HTML o mostrare un avviso

```bash
bin/magento cms:wysiwyg:restrict <restrict>
```


### `restrict`

y\n

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


## `config:sensitive:set`

Imposta valori di configurazione sensibili

```bash
bin/magento config:sensitive:set [-i|--interactive] [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path> [<value>]]
```


### `path`

Percorso di configurazione, ad esempio gruppo/sezione/nome_campo


### `value`

Valore di configurazione


### `--interactive`, `-i`

Abilita la modalità interattiva per impostare tutte le variabili sensibili

- Predefinito: `false`
- Non accetta un valore

### `--scope`

Ambito della configurazione, se non impostato, utilizzare &#39;default&#39;

- Predefinito: `default`
- Accetta un valore

### `--scope-code`

Codice ambito per la configurazione, stringa vuota per impostazione predefinita

- Predefinito: &quot;
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


## `config:set`

Modificare la configurazione del sistema

```bash
bin/magento config:set [--scope SCOPE] [--scope-code SCOPE-CODE] [-e|--lock-env] [-c|--lock-config] [-l|--lock] [--] <path> <value>
```


### `path`

Percorso di configurazione nel formato sezione/gruppo/nome_campo

- Obbligatorio

### `value`

Valore di configurazione

- Obbligatorio

### `--scope`

Ambito di configurazione (predefinito, sito Web o archivio)

- Predefinito: `default`
- Richiede un valore

### `--scope-code`

Codice ambito (obbligatorio solo se l’ambito non è &quot;predefinito&quot;)

- Richiede un valore

### `--lock-env`, `-e`

Valore di blocco che impedisce la modifica in Admin (verrà salvato in app/etc/env.php)

- Predefinito: `false`
- Non accetta un valore

### `--lock-config`, `-c`

Blocca e condividi il valore con altre installazioni, impedisce le modifiche in Admin (verrà salvato in app/etc/config.php)

- Predefinito: `false`
- Non accetta un valore

### `--lock`, `-l`

Obsoleto, utilizza invece l’opzione —lock-env.

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


## `config:show`

Mostra il valore di configurazione per il percorso specificato. Se non si specifica il percorso, verranno visualizzati tutti i valori salvati

```bash
bin/magento config:show [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path>]
```


### `path`

Percorso di configurazione, ad esempio section_id/group_id/field_id


### `--scope`

Ambito per la configurazione, se non specificato, verrà utilizzato l’ambito &quot;predefinito&quot;

- Predefinito: `default`
- Accetta un valore

### `--scope-code`

Codice ambito (obbligatorio solo se l’ambito non è `default`)

- Predefinito: &quot;
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


## `cron:install`

Genera e installa crontab per l&#39;utente corrente

```bash
bin/magento cron:install [-f|--force] [-d|--non-optional]
```

### `--force`, `-f`

Forza attività di installazione

- Predefinito: `false`
- Non accetta un valore

### `--non-optional`, `-d`

Installa solo le attività non facoltative (predefinite)

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


## `cron:remove`

Rimuove le attività da crontab

```bash
bin/magento cron:remove
```

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


## `cron:run`

Esegue i processi per pianificazione

```bash
bin/magento cron:run [--group GROUP] [--exclude-group [EXCLUDE-GROUP]] [--bootstrap BOOTSTRAP]
```

### `--group`

Esegui processi solo dal gruppo specificato

- Richiede un valore

### `--exclude-group`

Escludi processi dal gruppo specificato

- Predefinito: `[]`
- Accetta più valori

### `--bootstrap`

Aggiungere o sostituire i parametri del bootstrap

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


## `customer:hash:upgrade`

Aggiorna l’hash del cliente in base all’algoritmo più recente

```bash
bin/magento customer:hash:upgrade
```

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


## `deploy:mode:set`

Impostare la modalità applicazione.

```bash
bin/magento deploy:mode:set [-s|--skip-compilation] [--] <mode>
```


### `mode`

Modalità di applicazione da impostare. Le opzioni disponibili sono &quot;sviluppatore&quot; o &quot;produzione&quot;

- Obbligatorio

### `--skip-compilation`, `-s`

Ignora la cancellazione e la rigenerazione del contenuto statico (codice generato, CSS preelaborato e risorse in pub/static/)

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


## `deploy:mode:show`

Visualizza la modalità di applicazione corrente.

```bash
bin/magento deploy:mode:show
```

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


## `dev:di:info`

Fornisce informazioni sulla configurazione di Iniezione dipendenze per il comando.

```bash
bin/magento dev:di:info <class>
```


### `class`

Nome classe

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


## `dev:email:newsletter-compatibility-check`

Analizza i modelli di newsletter per potenziali problemi di compatibilità dell’utilizzo delle variabili

```bash
bin/magento dev:email:newsletter-compatibility-check
```

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


## `dev:email:override-compatibility-check`

Analizza le sostituzioni del modello e-mail per potenziali problemi di compatibilità dell’utilizzo delle variabili

```bash
bin/magento dev:email:override-compatibility-check
```

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


## `dev:profiler:disable`

Disattiva il profiler.

```bash
bin/magento dev:profiler:disable
```

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


## `dev:profiler:enable`

Abilita il profiler.

```bash
bin/magento dev:profiler:enable [<type>]
```


### `type`

Tipo di profiler


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


## `dev:query-log:disable`

Disabilita registrazione query DB

```bash
bin/magento dev:query-log:disable
```

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


## `dev:query-log:enable`

Abilita registrazione query DB

```bash
bin/magento dev:query-log:enable [--include-all-queries [INCLUDE-ALL-QUERIES]] [--query-time-threshold [QUERY-TIME-THRESHOLD]] [--include-call-stack [INCLUDE-CALL-STACK]]
```

### `--include-all-queries`

Registra tutte le query. [true\|false]

- Predefinito: `true`
- Accetta un valore

### `--query-time-threshold`

Soglie di tempo per le query.

- Predefinito: `0.001`
- Accetta un valore

### `--include-call-stack`

Include lo stack di chiamate. [true\|false]

- Predefinito: `true`
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


## `dev:source-theme:deploy`

Raccoglie e pubblica i file di origine per il tema.

```bash
bin/magento dev:source-theme:deploy [--type TYPE] [--locale LOCALE] [--area AREA] [--theme THEME] [--] [<file>...]
```


### `file`

File da pre-elaborare (il file deve essere specificato senza estensione)

- Predefinito: `css/styles-mcss/styles-l`

- Array

### `--type`

Tipo di file di origine: [meno]

- Predefinito: `less`
- Richiede un valore

### `--locale`

Lingua: [en_US]

- Predefinito: `en_US`
- Richiede un valore

### `--area`

Superficie: [frontend\|adminhtml]

- Predefinito: `frontend`
- Richiede un valore

### `--theme`

Tema: [Fornitore/tema]

- Predefinito: `Magento/luma`
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


## `dev:template-hints:disable`

Disattiva gli hint modello front-end. Potrebbe essere necessario svuotare la cache.

```bash
bin/magento dev:template-hints:disable
```

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


## `dev:template-hints:enable`

Abilitare gli hint modello front-end. Potrebbe essere necessario svuotare la cache.

```bash
bin/magento dev:template-hints:enable
```

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


## `dev:template-hints:status`

Mostra lo stato degli hint di modello front-end.

```bash
bin/magento dev:template-hints:status
```

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


## `dev:tests:run`

Esegue i test

```bash
bin/magento dev:tests:run [-c|--arguments ARGUMENTS] [--] [<type>]
```


### `type`

Tipo di test da eseguire. Tipi disponibili: all, unit, integration, integration-all, static, static-all, integrity, legacy, default

- Predefinito: `default`


### `--arguments`, `-c`

Argomenti aggiuntivi per PHPUnit. Esempio: &quot;-c&#39;—filter=MyTest&#39;&quot; (senza spazi)

- Predefinito: &quot;
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


## `dev:urn-catalog:generate`

Genera il catalogo di URN in mappature *.xsd per l’IDE per evidenziare xml.

```bash
bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>
```


### `path`

Percorso del file di output del catalogo. Per PhpStorm utilizzare .idea/misc.xml

- Obbligatorio

### `--ide`

Formato di generazione del catalogo. Supportato: [phpstorm, vscode]

- Predefinito: `phpstorm`
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


## `dev:xml:convert`

Converte i file XML utilizzando i fogli di stile XSL

```bash
bin/magento dev:xml:convert [-o|--overwrite] [--] <xml-file> <processor>
```


### `xml-file`

Percorso del file XML da trasformare

- Obbligatorio

### `processor`

Percorso del foglio di stile XSL da applicare al file XML

- Obbligatorio

### `--overwrite`, `-o`

Sovrascrivi file XML

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


## `downloadable:domains:add`

Aggiungere domini alla whitelist dei domini scaricabili

```bash
bin/magento downloadable:domains:add [<domains>...]
```


### `domains`

Nome domini

- Predefinito: `[]`

- Array

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


## `downloadable:domains:remove`

Rimuovere i domini dalla whitelist dei domini scaricabili

```bash
bin/magento downloadable:domains:remove [<domains>...]
```


### `domains`

Nomi di dominio

- Predefinito: `[]`

- Array

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


## `downloadable:domains:show`

Visualizza whitelist domini scaricabili

```bash
bin/magento downloadable:domains:show
```

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


## `encryption:payment-data:update`

Crittografa nuovamente i dati crittografati della carta di credito con la crittografia più recente.

```bash
bin/magento encryption:payment-data:update
```

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


## `events:create-event-provider`

Creare un provider di eventi personalizzato in Adobe I/O Events per questa istanza. Se non si specificano le opzioni di etichetta e descrizione, è necessario definirle nel file di sistema app/etc/event-types.json.

```bash
bin/magento events:create-event-provider [--label [LABEL]] [--description [DESCRIPTION]]
```


```bash
bin/magento events:provider:create 
```

### `--label`

Un’etichetta per definire il provider personalizzato.

- Accetta un valore

### `--description`

Descrizione del provider.

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


## `events:generate:module`

Genera modulo basato sull’elenco dei plug-in

```bash
bin/magento events:generate:module
```

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


## `events:info`

Restituisce il payload dell’evento specificato.

```bash
bin/magento events:info [--depth [DEPTH]] [--] <event-code>
```


### `event-code`

Codice evento

- Obbligatorio

### `--depth`

Il numero di livelli nel payload dell’evento da restituire

- Predefinito: `2`
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


## `events:list`

Mostra l’elenco degli eventi a cui sei iscritto

```bash
bin/magento events:list
```

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


## `events:list:all`

Restituisce un elenco di eventi sottoscrittori definiti nel modulo specificato

```bash
bin/magento events:list:all <module_name>
```


### `module_name`

Nome modulo

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


## `events:metadata:populate`

Crea metadati in Adobe I/O dall&#39;elenco di configurazione (configurazioni XML e di applicazioni)

```bash
bin/magento events:metadata:populate
```

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


## `events:subscribe`

Si iscrive all’evento

```bash
bin/magento events:subscribe [-f|--force] [--fields FIELDS] [--parent PARENT] [--rules RULES] [-p|--priority] [--] <event-code>
```


### `event-code`

Codice evento

- Obbligatorio

### `--force`, `-f`

Forza la sottoscrizione dell&#39;evento specificato, anche se non è stato definito localmente.

- Predefinito: `false`
- Non accetta un valore

### `--fields`

L’elenco dei campi nel payload dei dati dell’evento.

- Predefinito: `[]`
- Richiede un valore

### `--parent`

Il codice evento padre di una sottoscrizione evento con regole.

- Richiede un valore

### `--rules`

L’elenco delle regole per la sottoscrizione dell’evento, in cui ogni regola è formattata come &quot;campo\|operatore\|valore&quot;.

- Predefinito: `[]`
- Richiede un valore

### `--priority`, `-p`

Accelera la trasmissione di questo evento. Specifica questa opzione per gli eventi che devono essere consegnati immediatamente. Per impostazione predefinita, gli eventi vengono inviati da cron una volta al minuto.

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


## `events:sync-events-metadata`

Sincronizza metadati evento per questa istanza

```bash
bin/magento events:sync-events-metadata [-d|--delete]
```

### `--delete`, `-d`

I metadati dell’eliminazione degli eventi non sono più necessari

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


## `events:unsubscribe`

Rimuove l’abbonamento all’evento fornito

```bash
bin/magento events:unsubscribe <event-code>
```


### `event-code`

Codice evento a cui annullare l’abbonamento

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


## `i18n:collect-phrases`

Rileva le frasi nella base di codice

```bash
bin/magento i18n:collect-phrases [-o|--output OUTPUT] [-m|--magento] [--] [<directory>]
```


### `directory`

Percorso della directory da analizzare. Non necessario se è impostato il flag Magento


### `--output`, `-o`

Percorso (compreso il nome del file) di un file di output. Se non viene specificato alcun file, l&#39;impostazione predefinita è stdout.

- Richiede un valore

### `--magento`, `-m`

Utilizzate il parametro —magento per analizzare la base di codice del Magento corrente. Ometti il parametro se è specificata una directory.

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


## `i18n:pack`

Salva il pacchetto lingua

```bash
bin/magento i18n:pack [-m|--mode MODE] [-d|--allow-duplicates] [--] <source> <locale>
```


### `source`

Percorso del file del dizionario di origine con le traduzioni

- Obbligatorio

### `locale`

Impostazioni locali di destinazione per il dizionario, ad esempio &quot;de_DE&quot;

- Obbligatorio

### `--mode`, `-m`

Modalità di salvataggio per il dizionario - &quot;replace&quot; - sostituisci Language Pack con un nuovo - &quot;merge&quot; - unisci pacchetti di lingue, per impostazione predefinita &quot;replace&quot;

- Predefinito: `replace`
- Richiede un valore

### `--allow-duplicates`, `-d`

Utilizza il parametro —allow-duplicates per consentire il salvataggio di duplicati di traduzione. In caso contrario, ometti il parametro.

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


## `i18n:uninstall`

Disinstalla i pacchetti della lingua

```bash
bin/magento i18n:uninstall [-b|--backup-code] [--] <package>...
```


### `package`

Nome pacchetto lingua

- Predefinito: `[]`

- Obbligatorio
- Array

### `--backup-code`, `-b`

Backup del codice e dei file di configurazione (esclusi i file temporanei)

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


## `indexer:info`

Mostra gli indicizzatori consentiti

```bash
bin/magento indexer:info
```

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


## `indexer:reindex`

Reindicizza dati

```bash
bin/magento indexer:reindex [<index>...]
```


### `index`

Elenco separato da spazi dei tipi di indice o omesso da applicare a tutti gli indici.

- Predefinito: `[]`

- Array

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


## `indexer:reset`

Reimposta lo stato dell&#39;indicizzatore su non valido

```bash
bin/magento indexer:reset [<index>...]
```


### `index`

Elenco separato da spazi dei tipi di indice o omesso da applicare a tutti gli indici.

- Predefinito: `[]`

- Array

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


## `indexer:set-dimensions-mode`

Imposta modalità Dimension indicizzatore

```bash
bin/magento indexer:set-dimensions-mode [<indexer> [<mode>]]
```


### `indexer`

Nome indicizzatore [catalog_product_price|catalogpermissions_category]


### `mode`

Indicizzatore modalità dimensione catalog_product_price none,website,customer_group,website_and_customer_group catalogpermissions_category none,customer_group


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


## `indexer:set-mode`

Imposta il tipo di modalità indice

```bash
bin/magento indexer:set-mode [<mode> [<index>...]]
```


### `mode`

Tipo di modalità indicizzatore [realtime|pianificazione]


### `index`

Elenco separato da spazi dei tipi di indice o omesso da applicare a tutti gli indici.

- Predefinito: `[]`

- Array

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


## `indexer:show-dimensions-mode`

Mostra modalità Dimension indicizzatore

```bash
bin/magento indexer:show-dimensions-mode [<indexer>...]
```


### `indexer`

Elenco separato da spazi dei tipi di indice o omesso da applicare a tutti gli indici (catalog_product_price,catalogpermissions_category)

- Predefinito: `[]`

- Array

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


## `indexer:show-mode`

Mostra la modalità indice

```bash
bin/magento indexer:show-mode [<index>...]
```


### `index`

Elenco separato da spazi dei tipi di indice o omesso da applicare a tutti gli indici.

- Predefinito: `[]`

- Array

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


## `indexer:status`

Mostra lo stato dell&#39;indicizzatore

```bash
bin/magento indexer:status [<index>...]
```


### `index`

Elenco separato da spazi dei tipi di indice o omesso da applicare a tutti gli indici.

- Predefinito: `[]`

- Array

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


## `info:adminuri`

Visualizza l&#39;URI di amministrazione del Magento

```bash
bin/magento info:adminuri
```

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


## `info:backups:list`

Stampa elenco dei file di backup disponibili

```bash
bin/magento info:backups:list
```

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


## `info:currency:list`

Visualizza l&#39;elenco delle valute disponibili

```bash
bin/magento info:currency:list
```

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


## `info:dependencies:show-framework`

Mostra il numero di dipendenze nel framework del Magento

```bash
bin/magento info:dependencies:show-framework [-o|--output OUTPUT]
```

### `--output`, `-o`

Nome file del rapporto

- Predefinito: `framework-dependencies.csv`
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


## `info:dependencies:show-modules`

Mostra il numero di dipendenze tra i moduli

```bash
bin/magento info:dependencies:show-modules [-o|--output OUTPUT]
```

### `--output`, `-o`

Nome file del rapporto

- Predefinito: `modules-dependencies.csv`
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


## `info:dependencies:show-modules-circular`

Mostra il numero di dipendenze circolari tra i moduli

```bash
bin/magento info:dependencies:show-modules-circular [-o|--output OUTPUT]
```

### `--output`, `-o`

Nome file del rapporto

- Predefinito: `modules-circular-dependencies.csv`
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


## `info:language:list`

Visualizza l&#39;elenco delle lingue disponibili

```bash
bin/magento info:language:list
```

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


## `info:timezone:list`

Visualizza l&#39;elenco dei fusi orari disponibili

```bash
bin/magento info:timezone:list
```

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


## `inventory:reservation:create-compensations`

Crea prenotazioni per argomenti di retribuzione forniti

```bash
bin/magento inventory:reservation:create-compensations [-r|--raw] [--] [<compensations>...]
```


### `compensations`

Elenco degli argomenti retribuzione in formato &quot;\&lt;order_increment_id>:\&lt;sku>:\&lt;quantity>:\&lt;stock-id>&quot;

- Predefinito: `[]`

- Array

### `--raw`, `-r`

Uscita raw

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


## `inventory:reservation:list-inconsistencies`

Mostra tutti gli ordini e i prodotti con incongruenze di quantità vendibili

```bash
bin/magento inventory:reservation:list-inconsistencies [-c|--complete-orders] [-i|--incomplete-orders] [-b|--bunch-size [BUNCH-SIZE]] [-r|--raw]
```

### `--complete-orders`, `-c`

Mostra solo incongruenze per ordini completi

- Predefinito: `false`
- Non accetta un valore

### `--incomplete-orders`, `-i`

Mostra solo incongruenze per ordini incompleti

- Predefinito: `false`
- Non accetta un valore

### `--bunch-size`, `-b`

Definisce quanti ordini verranno caricati contemporaneamente

- Predefinito: `50`
- Accetta un valore

### `--raw`, `-r`

Uscita raw

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


## `inventory-geonames:import`

Scarica e importa i nomi geografici per l’algoritmo di selezione sorgente

```bash
bin/magento inventory-geonames:import <countries>...
```


### `countries`

Elenco dei codici paese da importare

- Predefinito: `[]`

- Obbligatorio
- Array

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


## `maintenance:allow-ips`

Imposta gli IP esenti dalla modalità di manutenzione

```bash
bin/magento maintenance:allow-ips [--none] [--add] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<ip>...]
```


### `ip`

Indirizzi IP consentiti

- Predefinito: `[]`

- Array

### `--none`

Cancella indirizzi IP consentiti

- Predefinito: `false`
- Non accetta un valore

### `--add`

Aggiungi l&#39;indirizzo IP all&#39;elenco esistente

- Predefinito: `false`
- Non accetta un valore

### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;DIR_IMMAGINE[cache][path]=/var/tmp/cache&quot;

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


## `maintenance:disable`

Disattiva la modalità di manutenzione

```bash
bin/magento maintenance:disable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--ip`

Indirizzi IP consentiti (utilizza &quot;nessuno&quot; per cancellare l’elenco IP consentiti)

- Predefinito: `[]`
- Richiede un valore

### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;DIR_IMMAGINE[cache][path]=/var/tmp/cache&quot;

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


## `maintenance:enable`

Abilita la modalità di manutenzione

```bash
bin/magento maintenance:enable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--ip`

Indirizzi IP consentiti (utilizza &quot;nessuno&quot; per cancellare l’elenco IP consentiti)

- Predefinito: `[]`
- Richiede un valore

### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;DIR_IMMAGINE[cache][path]=/var/tmp/cache&quot;

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


## `maintenance:status`

Visualizza lo stato della modalità di manutenzione

```bash
bin/magento maintenance:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;DIR_IMMAGINE[cache][path]=/var/tmp/cache&quot;

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


## `media-content:sync`

Sincronizzare i contenuti con le risorse

```bash
bin/magento media-content:sync
```

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


## `media-gallery:sync`

Sincronizzare le risorse di archiviazione e i supporti nel database

```bash
bin/magento media-gallery:sync
```

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


## `module:config:status`

Controlla la configurazione dei moduli nel file &quot;app/etc/config.php&quot; e segnala se sono aggiornati o meno

```bash
bin/magento module:config:status
```

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


## `module:disable`

Disabilita i moduli specificati

```bash
bin/magento module:disable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```


### `module`

Nome del modulo

- Predefinito: `[]`

- Array

### `--force`, `-f`

Ignora controllo dipendenze

- Predefinito: `false`
- Non accetta un valore

### `--all`

Disattiva tutti i moduli

- Predefinito: `false`
- Non accetta un valore

### `--clear-static-content`, `-c`

Cancellare i file di visualizzazione statica generati. Necessario, se i moduli dispongono di file di visualizzazione statica

- Predefinito: `false`
- Non accetta un valore

### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;DIR_IMMAGINE[cache][path]=/var/tmp/cache&quot;

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


## `module:enable`

Abilita i moduli specificati

```bash
bin/magento module:enable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```


### `module`

Nome del modulo

- Predefinito: `[]`

- Array

### `--force`, `-f`

Ignora controllo dipendenze

- Predefinito: `false`
- Non accetta un valore

### `--all`

Abilita tutti i moduli

- Predefinito: `false`
- Non accetta un valore

### `--clear-static-content`, `-c`

Cancellare i file di visualizzazione statica generati. Necessario, se i moduli dispongono di file di visualizzazione statica

- Predefinito: `false`
- Non accetta un valore

### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;DIR_IMMAGINE[cache][path]=/var/tmp/cache&quot;

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


## `module:status`

Visualizza lo stato dei moduli

```bash
bin/magento module:status [--enabled] [--disabled] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module-names>...]
```


### `module-names`

Nome modulo opzionale

- Predefinito: `[]`

- Array

### `--enabled`

Stampa solo moduli abilitati

- Predefinito: `false`
- Non accetta un valore

### `--disabled`

Stampa solo moduli disattivati

- Predefinito: `false`
- Non accetta un valore

### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;DIR_IMMAGINE[cache][path]=/var/tmp/cache&quot;

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


## `module:uninstall`

Disinstalla i moduli installati dal compositore

```bash
bin/magento module:uninstall [-r|--remove-data] [--backup-code] [--backup-media] [--backup-db] [--non-composer] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] <module>...
```


### `module`

Nome del modulo

- Predefinito: `[]`

- Obbligatorio
- Array

### `--remove-data`, `-r`

Rimuovi i dati installati dai moduli

- Predefinito: `false`
- Non accetta un valore

### `--backup-code`

Backup del codice e dei file di configurazione (esclusi i file temporanei)

- Predefinito: `false`
- Non accetta un valore

### `--backup-media`

Backup dei supporti

- Predefinito: `false`
- Non accetta un valore

### `--backup-db`

Esegui backup completo del database

- Predefinito: `false`
- Non accetta un valore

### `--non-composer`

Tutti i moduli che verranno superati saranno non basati su compositore

- Predefinito: `false`
- Non accetta un valore

### `--clear-static-content`, `-c`

Cancellare i file di visualizzazione statica generati. Necessario, se i moduli dispongono di file di visualizzazione statica

- Predefinito: `false`
- Non accetta un valore

### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;DIR_IMMAGINE[cache][path]=/var/tmp/cache&quot;

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


## `newrelic:create:deploy-marker`

Controlla le voci nella coda di distribuzione e crea un marcatore di distribuzione appropriato.

```bash
bin/magento newrelic:create:deploy-marker <message> <change_log> [<user> [<revision>]]
```


### `message`

Distribuire il messaggio?

- Obbligatorio

### `change_log`

Registro modifiche?

- Obbligatorio

### `user`

Utente distribuzione


### `revision`

Revisione


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


## `queue:consumers:list`

Elenco dei consumer di MessageQueue

```bash
bin/magento queue:consumers:list
```

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


## `queue:consumers:restart`

Riavvia consumer MessageQueue

```bash
bin/magento queue:consumers:restart
```

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


## `queue:consumers:start`

Avvia consumer MessageQueue

```bash
bin/magento queue:consumers:start [--max-messages MAX-MESSAGES] [--batch-size BATCH-SIZE] [--area-code AREA-CODE] [--single-thread] [--multi-process [MULTI-PROCESS]] [--pid-file-path PID-FILE-PATH] [--] <consumer>
```


### `consumer`

Nome del consumer da avviare.

- Obbligatorio

### `--max-messages`

Il numero di messaggi che il consumatore deve elaborare prima della fine del processo. Se non specificato, termina dopo l’elaborazione di tutti i messaggi in coda.

- Richiede un valore

### `--batch-size`

Il numero di messaggi per batch. Applicabile solo al consumatore batch.

- Richiede un valore

### `--area-code`

L’area preferita (globale, adminhtml, ecc.) predefinita è globale.

- Richiede un valore

### `--single-thread`

Questa opzione impedisce l’esecuzione simultanea di più copie di un consumer.

- Predefinito: `false`
- Non accetta un valore

### `--multi-process`

Il numero di processi per consumatore.

- Accetta un valore

### `--pid-file-path`

Percorso del file per il salvataggio del PID (questa opzione è obsoleta, usa invece —thread singolo)

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


## `remote-storage:sync`

Sincronizzare i file multimediali con l&#39;archiviazione remota.

```bash
bin/magento remote-storage:sync
```

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


## `saas:resync`

Risincronizza i dati del feed con il servizio SaaS.

```bash
bin/magento saas:resync [--no-reindex] [--feed FEED] [--cleanup-feed]
```

### `--no-reindex`

Esegui nuovamente l’invio dei dati del feed solo al servizio SaaS. Non reindicizza.

- Predefinito: `false`
- Non accetta un valore

### `--feed`

Nome del feed per la risincronizzazione completa con il servizio SaaS. Feed disponibili:

- Richiede un valore

### `--cleanup-feed`

Forza la pulizia della tabella dell&#39;indicizzatore del feed prima della sincronizzazione.

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


## `sampledata:deploy`

Distribuire moduli dati di esempio per installazioni di Magento basate su compositore

```bash
bin/magento sampledata:deploy [--no-update]
```

### `--no-update`

Aggiornare compositore.json senza eseguire l’aggiornamento del compositore

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


## `sampledata:remove`

Rimuovi tutti i pacchetti di dati di esempio da compositore.json

```bash
bin/magento sampledata:remove [--no-update]
```

### `--no-update`

Aggiornare compositore.json senza eseguire l’aggiornamento del compositore

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


## `sampledata:reset`

Reimposta tutti i moduli dati di esempio per la reinstallazione

```bash
bin/magento sampledata:reset
```

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


## `security:recaptcha:disable-for-user-forgot-password`

Disattiva reCAPTCHA per modulo password dimenticata dall’utente amministratore

```bash
bin/magento security:recaptcha:disable-for-user-forgot-password
```

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


## `security:recaptcha:disable-for-user-login`

Disabilita reCAPTCHA per il modulo di accesso utente amministratore

```bash
bin/magento security:recaptcha:disable-for-user-login
```

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


## `security:tfa:google:set-secret`

Imposta il segreto utilizzato per la generazione OTP di Google.

```bash
bin/magento security:tfa:google:set-secret <user> <secret>
```


### `user`

Nome utente

- Obbligatorio

### `secret`

Segreto

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


## `security:tfa:providers`

Elenca tutti i provider disponibili

```bash
bin/magento security:tfa:providers
```

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


## `security:tfa:reset`

Ripristina configurazione per un utente

```bash
bin/magento security:tfa:reset <user> <provider>
```


### `user`

Nome utente

- Obbligatorio

### `provider`

Codice provider

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


## `server:run`

Eseguire il server applicazioni

```bash
bin/magento server:run [-p|--port [PORT]] [-b|--background [BACKGROUND]] [-a|--area [AREA]] [-mip|--magento-init-params [MAGENTO-INIT-PARAMS]]
```

### `--port`, `-p`

porta su server

- Predefinito: `9501`
- Accetta un valore

### `--background`, `-b`

flag modalità di sfondo

- Predefinito: `0`
- Accetta un valore

### `--area`, `-a`

area server applicazioni

- Predefinito: `graphql`
- Accetta un valore

### `--magento-init-params`, `-mip`

parametri init bootstrap magento

- Predefinito: &quot;
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


## `setup:backup`

Esegue il backup della base di codice dell&#39;applicazione di Magento, del supporto e del database

```bash
bin/magento setup:backup [--code] [--media] [--db] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--code`

Backup del codice e dei file di configurazione (esclusi i file temporanei)

- Predefinito: `false`
- Non accetta un valore

### `--media`

Backup dei supporti

- Predefinito: `false`
- Non accetta un valore

### `--db`

Esegui backup completo del database

- Predefinito: `false`
- Non accetta un valore

### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;DIR_IMMAGINE[cache][path]=/var/tmp/cache&quot;

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


## `setup:config:set`

Crea o modifica la configurazione di distribuzione

```bash
bin/magento setup:config:set [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--id_salt ID_SALT] [--checkout-async CHECKOUT-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--config-async CONFIG-ASYNC] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--backend-frontname`

Nome front-end (verrà generato automaticamente se mancante)

- Richiede un valore

### `--enable-debug-logging`

Abilita registrazione debug

- Richiede un valore

### `--enable-syslog-logging`

Abilita registrazione syslog

- Richiede un valore

### `--remote-storage-driver`

Driver di archiviazione remota

- Richiede un valore

### `--remote-storage-prefix`

Prefisso archiviazione remota

- Predefinito: &quot;
- Richiede un valore

### `--remote-storage-endpoint`

Endpoint di archiviazione remota

- Richiede un valore

### `--remote-storage-bucket`

Bucket di archiviazione remota

- Richiede un valore

### `--remote-storage-region`

Area di archiviazione remota

- Richiede un valore

### `--remote-storage-key`

Chiave di accesso all&#39;archiviazione remota

- Predefinito: &quot;
- Richiede un valore

### `--remote-storage-secret`

Chiave segreta di archiviazione remota

- Predefinito: &quot;
- Richiede un valore

### `--remote-storage-path-style`

Stile percorso archiviazione remota

- Predefinito: `0`
- Richiede un valore

### `--id_salt`

GraphQl Salt

- Richiede un valore

### `--checkout-async`

Abilitare l’elaborazione asincrona degli ordini? 1 - Sì, 0 - No

- Richiede un valore

### `--amqp-host`

Host del server Amqp

- Predefinito: &quot;
- Richiede un valore

### `--amqp-port`

Porta server Amqp

- Predefinito: `5672`
- Richiede un valore

### `--amqp-user`

Nome utente server Amqp

- Predefinito: &quot;
- Richiede un valore

### `--amqp-password`

Password del server Amqp

- Predefinito: &quot;
- Richiede un valore

### `--amqp-virtualhost`

Amqp virtualhost

- Predefinito: `/`
- Richiede un valore

### `--amqp-ssl`

Amqp SSL

- Predefinito: &quot;
- Richiede un valore

### `--amqp-ssl-options`

Opzioni SSL Amqp (JSON)

- Predefinito: &quot;
- Richiede un valore

### `--config-async`

Abilitare il salvataggio asincrono della configurazione amministratore? 1 - Sì, 0 - No

- Richiede un valore

### `--consumers-wait-for-messages`

I consumatori devono attendere un messaggio dalla coda? 1 - Sì, 0 - No

- Richiede un valore

### `--queue-default-connection`

Connessione predefinita delle code di messaggi. Può essere &#39;db&#39;, &#39;amqp&#39; o un sistema di code personalizzato. Il sistema di code deve essere installato e configurato, altrimenti i messaggi non verranno elaborati correttamente.

- Richiede un valore

### `--deferred-total-calculating`

Abilitare il calcolo del totale differito? 1 - Sì, 0 - No

- Richiede un valore

### `--key`

Chiave di crittografia

- Richiede un valore

### `--db-host`

Host del server di database

- Richiede un valore

### `--db-name`

Nome database

- Richiede un valore

### `--db-user`

Nome utente server database

- Richiede un valore

### `--db-engine`

Motore server di database

- Richiede un valore

### `--db-password`

Password del server di database

- Richiede un valore

### `--db-prefix`

Prefisso tabella database

- Richiede un valore

### `--db-model`

Tipo di database

- Richiede un valore

### `--db-init-statements`

Set iniziale di comandi del database

- Richiede un valore

### `--skip-db-validation`, `-s`

Se specificato, la convalida della connessione database verrà ignorata

- Predefinito: `false`
- Non accetta un valore

### `--http-cache-hosts`

Host cache http

- Richiede un valore

### `--db-ssl-key`

Percorso completo del file della chiave client per stabilire la connessione db tramite SSL

- Predefinito: &quot;
- Richiede un valore

### `--db-ssl-cert`

Percorso completo del file del certificato client per stabilire la connessione del database tramite SSL

- Predefinito: &quot;
- Richiede un valore

### `--db-ssl-ca`

Percorso completo del file del certificato del server per stabilire la connessione del database tramite SSL

- Predefinito: &quot;
- Richiede un valore

### `--db-ssl-verify`

Verifica certificazione server

- Predefinito: `false`
- Non accetta un valore

### `--session-save`

Gestore salvataggio sessione

- Richiede un valore

### `--session-save-redis-host`

Nome host completo, indirizzo IP o percorso assoluto se si utilizzano socket UNIX

- Richiede un valore

### `--session-save-redis-port`

Porta di ascolto del server Redis

- Richiede un valore

### `--session-save-redis-password`

Password del server Redis

- Richiede un valore

### `--session-save-redis-timeout`

Timeout della connessione, in secondi

- Richiede un valore

### `--session-save-redis-persistent-id`

Stringa univoca per abilitare le connessioni permanenti

- Richiede un valore

### `--session-save-redis-db`

Numero database Redis

- Richiede un valore

### `--session-save-redis-compression-threshold`

Soglia di compressione Redis

- Richiede un valore

### `--session-save-redis-compression-lib`

Libreria di compressione Redis. Valori: gzip (predefinito), lzf, lz4, snappy

- Richiede un valore

### `--session-save-redis-log-level`

Livello di registro Redis. Valori: da 0 (meno dettagliato) a 7 (più dettagliato)

- Richiede un valore

### `--session-save-redis-max-concurrency`

Numero massimo di processi che possono attendere un blocco in una sessione

- Richiede un valore

### `--session-save-redis-break-after-frontend`

Numero di secondi di attesa prima di interrompere un blocco per la sessione front-end

- Richiede un valore

### `--session-save-redis-break-after-adminhtml`

Numero di secondi di attesa prima di interrompere un blocco per la sessione di amministrazione

- Richiede un valore

### `--session-save-redis-first-lifetime`

Durata in secondi della sessione per i non bot alla prima scrittura (usa 0 per disabilitare)

- Richiede un valore

### `--session-save-redis-bot-first-lifetime`

Durata in secondi della sessione per i bot alla prima scrittura (usa 0 per disabilitare)

- Richiede un valore

### `--session-save-redis-bot-lifetime`

Durata della sessione per i bot nelle scritture successive (usa 0 per disabilitare)

- Richiede un valore

### `--session-save-redis-disable-locking`

Disattiva il blocco. Valori: false (predefinito), true

- Richiede un valore

### `--session-save-redis-min-lifetime`

Durata minima sessione Redis, in secondi

- Richiede un valore

### `--session-save-redis-max-lifetime`

Durata massima sessione Redis, in secondi

- Richiede un valore

### `--session-save-redis-sentinel-master`

Redis Sentinel master

- Richiede un valore

### `--session-save-redis-sentinel-servers`

Server Redis Sentinel, separati da virgola

- Richiede un valore

### `--session-save-redis-sentinel-verify-master`

Redis Sentinel verifica master. Valori: false (predefinito), true

- Richiede un valore

### `--session-save-redis-sentinel-connect-retries`

Nuovi tentativi di connessione di Redis Sentinel.

- Richiede un valore

### `--cache-backend`

Gestore cache predefinito

- Richiede un valore

### `--cache-backend-redis-server`

Server Redis

- Richiede un valore

### `--cache-backend-redis-db`

Numero di database per la cache

- Richiede un valore

### `--cache-backend-redis-port`

Porta di ascolto del server Redis

- Richiede un valore

### `--cache-backend-redis-password`

Password del server Redis

- Richiede un valore

### `--cache-backend-redis-compress-data`

Impostate questo valore su 0 per disattivare la compressione (il valore predefinito è 1, abilitato)

- Richiede un valore

### `--cache-backend-redis-compression-lib`

Libreria di compressione da utilizzare [snappy,lzf,l4z,zstd,gzip] (lasciare vuoto per determinare automaticamente)

- Richiede un valore

### `--cache-id-prefix`

Prefisso ID per le chiavi della cache

- Richiede un valore

### `--allow-parallel-generation`

Consenti la generazione della cache in modo non bloccante

- Predefinito: `false`
- Non accetta un valore

### `--page-cache`

Gestore cache predefinito

- Richiede un valore

### `--page-cache-redis-server`

Server Redis

- Richiede un valore

### `--page-cache-redis-db`

Numero di database per la cache

- Richiede un valore

### `--page-cache-redis-port`

Porta di ascolto del server Redis

- Richiede un valore

### `--page-cache-redis-password`

Password del server Redis

- Richiede un valore

### `--page-cache-redis-compress-data`

Impostate questo valore su 1 per comprimere la cache dell&#39;intera pagina (usate 0 per disattivare)

- Richiede un valore

### `--page-cache-redis-compression-lib`

Libreria di compressione da utilizzare [snappy,lzf,l4z,zstd,gzip] (lasciare vuoto per determinare automaticamente)

- Richiede un valore

### `--page-cache-id-prefix`

Prefisso ID per le chiavi della cache

- Richiede un valore

### `--lock-provider`

Blocca nome provider

- Richiede un valore

### `--lock-db-prefix`

Prefisso di blocco specifico per l&#39;installazione per evitare conflitti di blocco

- Richiede un valore

### `--lock-zookeeper-host`

Host e porta per la connessione al cluster Zookeeper. Ad esempio: 127.0.0.1:2181

- Richiede un valore

### `--lock-zookeeper-path`

Percorso in cui Zookeeper salverà i blocchi. Il percorso predefinito è: /magento/locks

- Richiede un valore

### `--lock-file-path`

Percorso in cui verranno salvati i blocchi di file.

- Richiede un valore

### `--document-root-is-pub`

Flag da mostrare: il pub è nella directory principale; può essere true o false solo

- Richiede un valore

### `--backpressure-logger`

Gestore logger di backpression

- Richiede un valore

### `--backpressure-logger-redis-server`

Server Redis

- Richiede un valore

### `--backpressure-logger-redis-port`

Porta di ascolto del server Redis

- Richiede un valore

### `--backpressure-logger-redis-timeout`

Timeout del server Redis

- Richiede un valore

### `--backpressure-logger-redis-persistent`

Redis persistente

- Richiede un valore

### `--backpressure-logger-redis-db`

Numero Redis db

- Richiede un valore

### `--backpressure-logger-redis-password`

Password del server Redis

- Richiede un valore

### `--backpressure-logger-redis-user`

Utente server Redis

- Richiede un valore

### `--backpressure-logger-id-prefix`

Prefisso ID per le chiavi

- Richiede un valore

### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;DIR_IMMAGINE[cache][path]=/var/tmp/cache&quot;

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


## `setup:db-data:upgrade`

Installa e aggiorna i dati nel database

```bash
bin/magento setup:db-data:upgrade [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;DIR_IMMAGINE[cache][path]=/var/tmp/cache&quot;

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


## `setup:db-declaration:generate-patch`

Generare la patch e inserirla in una cartella specifica.

```bash
bin/magento setup:db-declaration:generate-patch [--revertable [REVERTABLE]] [--type [TYPE]] [--] <module> <patch>
```


### `module`

Nome modulo

- Obbligatorio

### `patch`

Nome patch

- Obbligatorio

### `--revertable`

Verificare se la patch è ripristinabile o meno.

- Predefinito: `false`
- Accetta un valore

### `--type`

Scopri il tipo di patch da generare. Valori disponibili: `data`, `schema`.

- Predefinito: `data`
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


## `setup:db-declaration:generate-whitelist`

Genera una whitelist di tabelle e colonne che possono essere modificate dal programma di installazione della dichiarazione

```bash
bin/magento setup:db-declaration:generate-whitelist [--module-name [MODULE-NAME]]
```

### `--module-name`

Nome del modulo in cui verrà generata la whitelist

- Predefinito: `all`
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


## `setup:db-schema:add-slave`

Spostare le tabelle correlate alle virgolette di estrazione in un server di database separato

```bash
bin/magento setup:db-schema:add-slave [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--maxAllowedLag [MAXALLOWEDLAG]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--host`

Host del server di database slave

- Predefinito: `localhost`
- Richiede un valore

### `--dbname`

Nome database secondario

- Richiede un valore

### `--username`

Nome utente database secondario

- Predefinito: `root`
- Richiede un valore

### `--password`

Password utente di Slave DB

- Accetta un valore

### `--connection`

Nome connessione secondaria

- Predefinito: `default`
- Accetta un valore

### `--resource`

Nome risorsa secondaria

- Predefinito: `default`
- Accetta un valore

### `--maxAllowedLag`

Connessione slave lag max consentita (in secondi)

- Predefinito: &quot;
- Accetta un valore

### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;DIR_IMMAGINE[cache][path]=/var/tmp/cache&quot;

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


## `setup:db-schema:split-quote`

Spostare le tabelle correlate alle virgolette di estrazione in un server di database separato. Obsoleto dalla versione 2.4.2 e verrà rimosso

```bash
bin/magento setup:db-schema:split-quote [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--host`

Archivia host server database

- Richiede un valore

### `--dbname`

Nome database di estrazione

- Richiede un valore

### `--username`

Nome utente database di estrazione

- Richiede un valore

### `--password`

Estrai password utente DB

- Accetta un valore

### `--connection`

Estrai nome connessione

- Predefinito: `checkout`
- Accetta un valore

### `--resource`

Nome risorsa di estrazione

- Predefinito: `checkout`
- Accetta un valore

### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;DIR_IMMAGINE[cache][path]=/var/tmp/cache&quot;

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


## `setup:db-schema:split-sales`

Spostare le tabelle correlate alle vendite in un server DB separato. Obsoleto dalla versione 2.4.2 e verrà rimosso

```bash
bin/magento setup:db-schema:split-sales [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password [PASSWORD]] [--connection [CONNECTION]] [--resource [RESOURCE]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--host`

Host server database vendite

- Richiede un valore

### `--dbname`

Nome database vendite

- Richiede un valore

### `--username`

Nome utente database vendite

- Richiede un valore

### `--password`

Password utente database vendite

- Accetta un valore

### `--connection`

Nome connessione vendite

- Predefinito: `sales`
- Accetta un valore

### `--resource`

Nome risorsa di vendita

- Predefinito: `sales`
- Accetta un valore

### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;DIR_IMMAGINE[cache][path]=/var/tmp/cache&quot;

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


## `setup:db-schema:upgrade`

Installa e aggiorna lo schema del database

```bash
bin/magento setup:db-schema:upgrade [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--convert-old-scripts`

Consente di convertire gli script precedenti (InstallSchema, UpgradeSchema) nel formato db_schema.xml

- Predefinito: `false`
- Accetta un valore

### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;DIR_IMMAGINE[cache][path]=/var/tmp/cache&quot;

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


## `setup:db:status`

Controlla se lo schema o i dati del database devono essere aggiornati

```bash
bin/magento setup:db:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;DIR_IMMAGINE[cache][path]=/var/tmp/cache&quot;

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


## `setup:di:compile`

Genera la configurazione DI e tutte le classi mancanti che possono essere generate automaticamente

```bash
bin/magento setup:di:compile
```

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


## `setup:install`

Installa l&#39;applicazione di Magento

```bash
bin/magento setup:install [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--id_salt ID_SALT] [--checkout-async CHECKOUT-ASYNC] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--config-async CONFIG-ASYNC] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--deferred-total-calculating DEFERRED-TOTAL-CALCULATING] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--backpressure-logger BACKPRESSURE-LOGGER] [--backpressure-logger-redis-server BACKPRESSURE-LOGGER-REDIS-SERVER] [--backpressure-logger-redis-port BACKPRESSURE-LOGGER-REDIS-PORT] [--backpressure-logger-redis-timeout BACKPRESSURE-LOGGER-REDIS-TIMEOUT] [--backpressure-logger-redis-persistent BACKPRESSURE-LOGGER-REDIS-PERSISTENT] [--backpressure-logger-redis-db BACKPRESSURE-LOGGER-REDIS-DB] [--backpressure-logger-redis-password BACKPRESSURE-LOGGER-REDIS-PASSWORD] [--backpressure-logger-redis-user BACKPRESSURE-LOGGER-REDIS-USER] [--backpressure-logger-id-prefix BACKPRESSURE-LOGGER-ID-PREFIX] [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--admin-user [ADMIN-USER]] [--admin-password [ADMIN-PASSWORD]] [--admin-email [ADMIN-EMAIL]] [--admin-firstname [ADMIN-FIRSTNAME]] [--admin-lastname [ADMIN-LASTNAME]] [--search-engine SEARCH-ENGINE] [--elasticsearch-host ELASTICSEARCH-HOST] [--elasticsearch-port ELASTICSEARCH-PORT] [--elasticsearch-enable-auth ELASTICSEARCH-ENABLE-AUTH] [--elasticsearch-username ELASTICSEARCH-USERNAME] [--elasticsearch-password ELASTICSEARCH-PASSWORD] [--elasticsearch-index-prefix ELASTICSEARCH-INDEX-PREFIX] [--elasticsearch-timeout ELASTICSEARCH-TIMEOUT] [--opensearch-host OPENSEARCH-HOST] [--opensearch-port OPENSEARCH-PORT] [--opensearch-enable-auth OPENSEARCH-ENABLE-AUTH] [--opensearch-username OPENSEARCH-USERNAME] [--opensearch-password OPENSEARCH-PASSWORD] [--opensearch-index-prefix OPENSEARCH-INDEX-PREFIX] [--opensearch-timeout OPENSEARCH-TIMEOUT] [--cleanup-database] [--sales-order-increment-prefix SALES-ORDER-INCREMENT-PREFIX] [--use-sample-data] [--enable-modules [ENABLE-MODULES]] [--disable-modules [DISABLE-MODULES]] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [-i|--interactive] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--backend-frontname`

Nome front-end (verrà generato automaticamente se mancante)

- Richiede un valore

### `--enable-debug-logging`

Abilita registrazione debug

- Richiede un valore

### `--enable-syslog-logging`

Abilita registrazione syslog

- Richiede un valore

### `--remote-storage-driver`

Driver di archiviazione remota

- Richiede un valore

### `--remote-storage-prefix`

Prefisso archiviazione remota

- Predefinito: &quot;
- Richiede un valore

### `--remote-storage-endpoint`

Endpoint di archiviazione remota

- Richiede un valore

### `--remote-storage-bucket`

Bucket di archiviazione remota

- Richiede un valore

### `--remote-storage-region`

Area di archiviazione remota

- Richiede un valore

### `--remote-storage-key`

Chiave di accesso all&#39;archiviazione remota

- Predefinito: &quot;
- Richiede un valore

### `--remote-storage-secret`

Chiave segreta di archiviazione remota

- Predefinito: &quot;
- Richiede un valore

### `--remote-storage-path-style`

Stile percorso archiviazione remota

- Predefinito: `0`
- Richiede un valore

### `--id_salt`

GraphQl Salt

- Richiede un valore

### `--checkout-async`

Abilitare l’elaborazione asincrona degli ordini? 1 - Sì, 0 - No

- Richiede un valore

### `--amqp-host`

Host del server Amqp

- Predefinito: &quot;
- Richiede un valore

### `--amqp-port`

Porta server Amqp

- Predefinito: `5672`
- Richiede un valore

### `--amqp-user`

Nome utente server Amqp

- Predefinito: &quot;
- Richiede un valore

### `--amqp-password`

Password del server Amqp

- Predefinito: &quot;
- Richiede un valore

### `--amqp-virtualhost`

Amqp virtualhost

- Predefinito: `/`
- Richiede un valore

### `--amqp-ssl`

Amqp SSL

- Predefinito: &quot;
- Richiede un valore

### `--amqp-ssl-options`

Opzioni SSL Amqp (JSON)

- Predefinito: &quot;
- Richiede un valore

### `--config-async`

Abilitare il salvataggio asincrono della configurazione amministratore? 1 - Sì, 0 - No

- Richiede un valore

### `--consumers-wait-for-messages`

I consumatori devono attendere un messaggio dalla coda? 1 - Sì, 0 - No

- Richiede un valore

### `--queue-default-connection`

Connessione predefinita delle code di messaggi. Può essere &#39;db&#39;, &#39;amqp&#39; o un sistema di code personalizzato. Il sistema di code deve essere installato e configurato, altrimenti i messaggi non verranno elaborati correttamente.

- Richiede un valore

### `--deferred-total-calculating`

Abilitare il calcolo del totale differito? 1 - Sì, 0 - No

- Richiede un valore

### `--key`

Chiave di crittografia

- Richiede un valore

### `--db-host`

Host del server di database

- Richiede un valore

### `--db-name`

Nome database

- Richiede un valore

### `--db-user`

Nome utente server database

- Richiede un valore

### `--db-engine`

Motore server di database

- Richiede un valore

### `--db-password`

Password del server di database

- Richiede un valore

### `--db-prefix`

Prefisso tabella database

- Richiede un valore

### `--db-model`

Tipo di database

- Richiede un valore

### `--db-init-statements`

Set iniziale di comandi del database

- Richiede un valore

### `--skip-db-validation`, `-s`

Se specificato, la convalida della connessione database verrà ignorata

- Predefinito: `false`
- Non accetta un valore

### `--http-cache-hosts`

Host cache http

- Richiede un valore

### `--db-ssl-key`

Percorso completo del file della chiave client per stabilire la connessione db tramite SSL

- Predefinito: &quot;
- Richiede un valore

### `--db-ssl-cert`

Percorso completo del file del certificato client per stabilire la connessione del database tramite SSL

- Predefinito: &quot;
- Richiede un valore

### `--db-ssl-ca`

Percorso completo del file del certificato del server per stabilire la connessione del database tramite SSL

- Predefinito: &quot;
- Richiede un valore

### `--db-ssl-verify`

Verifica certificazione server

- Predefinito: `false`
- Non accetta un valore

### `--session-save`

Gestore salvataggio sessione

- Richiede un valore

### `--session-save-redis-host`

Nome host completo, indirizzo IP o percorso assoluto se si utilizzano socket UNIX

- Richiede un valore

### `--session-save-redis-port`

Porta di ascolto del server Redis

- Richiede un valore

### `--session-save-redis-password`

Password del server Redis

- Richiede un valore

### `--session-save-redis-timeout`

Timeout della connessione, in secondi

- Richiede un valore

### `--session-save-redis-persistent-id`

Stringa univoca per abilitare le connessioni permanenti

- Richiede un valore

### `--session-save-redis-db`

Numero database Redis

- Richiede un valore

### `--session-save-redis-compression-threshold`

Soglia di compressione Redis

- Richiede un valore

### `--session-save-redis-compression-lib`

Libreria di compressione Redis. Valori: gzip (predefinito), lzf, lz4, snappy

- Richiede un valore

### `--session-save-redis-log-level`

Livello di registro Redis. Valori: da 0 (meno dettagliato) a 7 (più dettagliato)

- Richiede un valore

### `--session-save-redis-max-concurrency`

Numero massimo di processi che possono attendere un blocco in una sessione

- Richiede un valore

### `--session-save-redis-break-after-frontend`

Numero di secondi di attesa prima di interrompere un blocco per la sessione front-end

- Richiede un valore

### `--session-save-redis-break-after-adminhtml`

Numero di secondi di attesa prima di interrompere un blocco per la sessione di amministrazione

- Richiede un valore

### `--session-save-redis-first-lifetime`

Durata in secondi della sessione per i non bot alla prima scrittura (usa 0 per disabilitare)

- Richiede un valore

### `--session-save-redis-bot-first-lifetime`

Durata in secondi della sessione per i bot alla prima scrittura (usa 0 per disabilitare)

- Richiede un valore

### `--session-save-redis-bot-lifetime`

Durata della sessione per i bot nelle scritture successive (usa 0 per disabilitare)

- Richiede un valore

### `--session-save-redis-disable-locking`

Disattiva il blocco. Valori: false (predefinito), true

- Richiede un valore

### `--session-save-redis-min-lifetime`

Durata minima sessione Redis, in secondi

- Richiede un valore

### `--session-save-redis-max-lifetime`

Durata massima sessione Redis, in secondi

- Richiede un valore

### `--session-save-redis-sentinel-master`

Redis Sentinel master

- Richiede un valore

### `--session-save-redis-sentinel-servers`

Server Redis Sentinel, separati da virgola

- Richiede un valore

### `--session-save-redis-sentinel-verify-master`

Redis Sentinel verifica master. Valori: false (predefinito), true

- Richiede un valore

### `--session-save-redis-sentinel-connect-retries`

Nuovi tentativi di connessione di Redis Sentinel.

- Richiede un valore

### `--cache-backend`

Gestore cache predefinito

- Richiede un valore

### `--cache-backend-redis-server`

Server Redis

- Richiede un valore

### `--cache-backend-redis-db`

Numero di database per la cache

- Richiede un valore

### `--cache-backend-redis-port`

Porta di ascolto del server Redis

- Richiede un valore

### `--cache-backend-redis-password`

Password del server Redis

- Richiede un valore

### `--cache-backend-redis-compress-data`

Impostate questo valore su 0 per disattivare la compressione (il valore predefinito è 1, abilitato)

- Richiede un valore

### `--cache-backend-redis-compression-lib`

Libreria di compressione da utilizzare [snappy,lzf,l4z,zstd,gzip] (lasciare vuoto per determinare automaticamente)

- Richiede un valore

### `--cache-id-prefix`

Prefisso ID per le chiavi della cache

- Richiede un valore

### `--allow-parallel-generation`

Consenti la generazione della cache in modo non bloccante

- Predefinito: `false`
- Non accetta un valore

### `--page-cache`

Gestore cache predefinito

- Richiede un valore

### `--page-cache-redis-server`

Server Redis

- Richiede un valore

### `--page-cache-redis-db`

Numero di database per la cache

- Richiede un valore

### `--page-cache-redis-port`

Porta di ascolto del server Redis

- Richiede un valore

### `--page-cache-redis-password`

Password del server Redis

- Richiede un valore

### `--page-cache-redis-compress-data`

Impostate questo valore su 1 per comprimere la cache dell&#39;intera pagina (usate 0 per disattivare)

- Richiede un valore

### `--page-cache-redis-compression-lib`

Libreria di compressione da utilizzare [snappy,lzf,l4z,zstd,gzip] (lasciare vuoto per determinare automaticamente)

- Richiede un valore

### `--page-cache-id-prefix`

Prefisso ID per le chiavi della cache

- Richiede un valore

### `--lock-provider`

Blocca nome provider

- Richiede un valore

### `--lock-db-prefix`

Prefisso di blocco specifico per l&#39;installazione per evitare conflitti di blocco

- Richiede un valore

### `--lock-zookeeper-host`

Host e porta per la connessione al cluster Zookeeper. Ad esempio: 127.0.0.1:2181

- Richiede un valore

### `--lock-zookeeper-path`

Percorso in cui Zookeeper salverà i blocchi. Il percorso predefinito è: /magento/locks

- Richiede un valore

### `--lock-file-path`

Percorso in cui verranno salvati i blocchi di file.

- Richiede un valore

### `--document-root-is-pub`

Flag da mostrare: il pub è nella directory principale; può essere true o false solo

- Richiede un valore

### `--backpressure-logger`

Gestore logger di backpression

- Richiede un valore

### `--backpressure-logger-redis-server`

Server Redis

- Richiede un valore

### `--backpressure-logger-redis-port`

Porta di ascolto del server Redis

- Richiede un valore

### `--backpressure-logger-redis-timeout`

Timeout del server Redis

- Richiede un valore

### `--backpressure-logger-redis-persistent`

Redis persistente

- Richiede un valore

### `--backpressure-logger-redis-db`

Numero Redis db

- Richiede un valore

### `--backpressure-logger-redis-password`

Password del server Redis

- Richiede un valore

### `--backpressure-logger-redis-user`

Utente server Redis

- Richiede un valore

### `--backpressure-logger-id-prefix`

Prefisso ID per le chiavi

- Richiede un valore

### `--base-url`

URL in cui lo store deve essere disponibile. Obsoleto, usa config:set con percorso web/unsecure/base_url

- Richiede un valore

### `--language`

Codice lingua predefinito. Obsoleto, usa config:set con percorso generale/lingua/codice

- Richiede un valore

### `--timezone`

Codice fuso orario predefinito. Obsoleto, usa config:set con percorso generale/lingua/fuso orario

- Richiede un valore

### `--currency`

Codice valuta predefinito. Obsoleto, usa config:set con percorso valuta/opzioni/base, valuta/opzioni/predefinito e valuta/opzioni/consenti

- Richiede un valore

### `--use-rewrites`

Utilizza le riscritture. Obsoleto, usa config:set con percorso web/seo/use_rewrites

- Richiede un valore

### `--use-secure`

Utilizza URL sicuri. Abilita questa opzione solo se SSL è disponibile. Obsoleto, usa config:set con percorso web/secure/use_in_frontend

- Richiede un valore

### `--base-url-secure`

URL di base per la connessione SSL. Obsoleto, usa config:set con percorso web/secure/base_url

- Richiede un valore

### `--use-secure-admin`

Esegui l’interfaccia di amministrazione con SSL. Obsoleto, usa config:set con percorso web/secure/use_in_adminhtml

- Richiede un valore

### `--admin-use-security-key`

Specifica se utilizzare una funzione di &quot;chiave di sicurezza&quot; negli URL e nei moduli dell’amministratore di Magento. Obsoleto, usa config:set con path admin/security/use_form_key

- Richiede un valore

### `--admin-user`

Utente amministratore

- Accetta un valore

### `--admin-password`

Password amministratore

- Accetta un valore

### `--admin-email`

E-mail amministratore

- Accetta un valore

### `--admin-firstname`

Nome amministratore

- Accetta un valore

### `--admin-lastname`

Cognome amministratore

- Accetta un valore

### `--search-engine`

Motore di ricerca. Valori: elasticsearch5, elasticsearch7, elasticsearch8, opensearch

- Richiede un valore

### `--elasticsearch-host`

Host del server di Elasticsearch.

- Richiede un valore

### `--elasticsearch-port`

Porta server di Elasticsearch.

- Richiede un valore

### `--elasticsearch-enable-auth`

Imposta su 1 per abilitare l’autenticazione. Il valore predefinito è 0, disabilitato

- Richiede un valore

### `--elasticsearch-username`

Nome utente di Elasticsearch. Applicabile solo se l’autenticazione HTTP è abilitata

- Richiede un valore

### `--elasticsearch-password`

Password di Elasticsearch. Applicabile solo se l’autenticazione HTTP è abilitata

- Richiede un valore

### `--elasticsearch-index-prefix`

Prefisso indice Elasticsearch.

- Richiede un valore

### `--elasticsearch-timeout`

Timeout del server di Elasticsearch.

- Richiede un valore

### `--opensearch-host`

Host del server OpenSearch.

- Richiede un valore

### `--opensearch-port`

Porta del server OpenSearch.

- Richiede un valore

### `--opensearch-enable-auth`

Imposta su 1 per abilitare l’autenticazione. Il valore predefinito è 0, disabilitato

- Richiede un valore

### `--opensearch-username`

Nome utente OpenSearch. Applicabile solo se l’autenticazione HTTP è abilitata

- Richiede un valore

### `--opensearch-password`

Password OpenSearch. Applicabile solo se l’autenticazione HTTP è abilitata

- Richiede un valore

### `--opensearch-index-prefix`

Prefisso indice OpenSearch.

- Richiede un valore

### `--opensearch-timeout`

Timeout del server OpenSearch.

- Richiede un valore

### `--cleanup-database`

Pulizia del database prima dell&#39;installazione

- Predefinito: `false`
- Non accetta un valore

### `--sales-order-increment-prefix`

Prefisso numero ordine cliente

- Richiede un valore

### `--use-sample-data`

Utilizzare dati di esempio

- Predefinito: `false`
- Non accetta un valore

### `--enable-modules`

Elenco di nomi di moduli separati da virgole. Questo deve essere incluso durante l&#39;installazione. Disponibile param magico &quot;all&quot;.

- Accetta un valore

### `--disable-modules`

Elenco di nomi di moduli separati da virgole. Ciò deve essere evitato durante l&#39;installazione. Disponibile param magico &quot;all&quot;.

- Accetta un valore

### `--convert-old-scripts`

Consente di convertire gli script precedenti (InstallSchema, UpgradeSchema) nel formato db_schema.xml

- Predefinito: `false`
- Accetta un valore

### `--interactive`, `-i`

Installazione interattiva del Magento

- Predefinito: `false`
- Non accetta un valore

### `--safe-mode`

Installazione sicura del Magento con immagini su operazioni distruttive, come la rimozione delle colonne

- Accetta un valore

### `--data-restore`

Ripristinare i dati rimossi dalle immagini

- Accetta un valore

### `--dry-run`

L&#39;installazione del Magento viene eseguita in modalità di funzionamento a secco

- Predefinito: `false`
- Accetta un valore

### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;DIR_IMMAGINE[cache][path]=/var/tmp/cache&quot;

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


## `setup:performance:generate-fixtures`

Genera gli staffaggi

```bash
bin/magento setup:performance:generate-fixtures [-s|--skip-reindex] [--] <profile>
```


### `profile`

Percorso del file di configurazione del profilo

- Obbligatorio

### `--skip-reindex`, `-s`

Salta reindicizzazione

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


## `setup:rollback`

Ripristina il database, il supporto e la base di codice dell&#39;applicazione di Magento

```bash
bin/magento setup:rollback [-c|--code-file CODE-FILE] [-m|--media-file MEDIA-FILE] [-d|--db-file DB-FILE] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--code-file`, `-c`

Nome base del file di backup del codice in var/backups

- Richiede un valore

### `--media-file`, `-m`

Nome base del file di backup multimediale in var/backups

- Richiede un valore

### `--db-file`, `-d`

Nome base del file di backup del database in var/backups

- Richiede un valore

### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;DIR_IMMAGINE[cache][path]=/var/tmp/cache&quot;

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


## `setup:static-content:deploy`

Distribuisce i file di visualizzazione statici

```bash
bin/magento setup:static-content:deploy [-f|--force] [-s|--strategy [STRATEGY]] [-a|--area [AREA]] [--exclude-area [EXCLUDE-AREA]] [-t|--theme [THEME]] [--exclude-theme [EXCLUDE-THEME]] [-l|--language [LANGUAGE]] [--exclude-language [EXCLUDE-LANGUAGE]] [-j|--jobs [JOBS]] [--max-execution-time [MAX-EXECUTION-TIME]] [--symlink-locale] [--content-version CONTENT-VERSION] [--refresh-content-version-only] [--no-javascript] [--no-js-bundle] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [--] [<languages>...]
```


### `languages`

Elenco separato da spazi dei codici di lingua ISO-639 per i quali generare file di visualizzazione statica.

- Predefinito: `[]`

- Array

### `--force`, `-f`

Distribuisci i file in qualsiasi modalità.

- Predefinito: `false`
- Non accetta un valore

### `--strategy`, `-s`

Distribuire i file utilizzando la strategia specificata.

- Predefinito: `quick`
- Accetta un valore

### `--area`, `-a`

Genera file solo per le aree specificate.

- Predefinito: `all`
- Accetta più valori

### `--exclude-area`

Non generare file per le aree specificate.

- Predefinito: `none`
- Accetta più valori

### `--theme`, `-t`

Genera file di visualizzazione statica solo per i temi specificati.

- Predefinito: `all`
- Accetta più valori

### `--exclude-theme`

Non generare file per i temi specificati.

- Predefinito: `none`
- Accetta più valori

### `--language`, `-l`

Genera file solo per le lingue specificate.

- Predefinito: `all`
- Accetta più valori

### `--exclude-language`

Non generare file per le lingue specificate.

- Predefinito: `none`
- Accetta più valori

### `--jobs`, `-j`

Abilita l&#39;elaborazione parallela utilizzando il numero specificato di processi.

- Predefinito: `0`
- Accetta un valore

### `--max-execution-time`

Tempo massimo di esecuzione previsto del processo statico di distribuzione (in secondi).

- Predefinito: `900`
- Accetta un valore

### `--symlink-locale`

Creare collegamenti simbolici per i file di tali impostazioni internazionali, che vengono passati per la distribuzione, ma che non presentano personalizzazioni.

- Predefinito: `false`
- Non accetta un valore

### `--content-version`

È possibile utilizzare una versione personalizzata del contenuto statico se si esegue la distribuzione su più nodi per garantire che la versione del contenuto statico sia identica e che il caching funzioni correttamente.

- Richiede un valore

### `--refresh-content-version-only`

L’aggiornamento della sola versione del contenuto statico può essere utilizzato per aggiornare il contenuto statico nella cache del browser e nella cache CDN.

- Predefinito: `false`
- Non accetta un valore

### `--no-javascript`

Non distribuire file JavaScript.

- Predefinito: `false`
- Non accetta un valore

### `--no-js-bundle`

Non distribuire file bundle JavaScript.

- Predefinito: `false`
- Non accetta un valore

### `--no-css`

Non distribuire file CSS.

- Predefinito: `false`
- Non accetta un valore

### `--no-less`

Non distribuire file LESS.

- Predefinito: `false`
- Non accetta un valore

### `--no-images`

Non distribuire immagini.

- Predefinito: `false`
- Non accetta un valore

### `--no-fonts`

Non distribuire file di font.

- Predefinito: `false`
- Non accetta un valore

### `--no-html`

Non distribuire file HTML.

- Predefinito: `false`
- Non accetta un valore

### `--no-misc`

Non distribuire file di altro tipo (.md, .jbf, .csv, ecc.).

- Predefinito: `false`
- Non accetta un valore

### `--no-html-minify`

Non minimizzare i file HTML.

- Predefinito: `false`
- Non accetta un valore

### `--no-parent`

Non compilare i temi principali. Supportato solo in strategie veloci e standard.

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


## `setup:store-config:set`

Installa la configurazione dell&#39;archivio. Obsoleto dalla versione 2.2.0. Usa config:set

```bash
bin/magento setup:store-config:set [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--base-url`

URL in cui lo store deve essere disponibile. Obsoleto, usa config:set con percorso web/unsecure/base_url

- Richiede un valore

### `--language`

Codice lingua predefinito. Obsoleto, usa config:set con percorso generale/lingua/codice

- Richiede un valore

### `--timezone`

Codice fuso orario predefinito. Obsoleto, usa config:set con percorso generale/lingua/fuso orario

- Richiede un valore

### `--currency`

Codice valuta predefinito. Obsoleto, usa config:set con percorso valuta/opzioni/base, valuta/opzioni/predefinito e valuta/opzioni/consenti

- Richiede un valore

### `--use-rewrites`

Utilizza le riscritture. Obsoleto, usa config:set con percorso web/seo/use_rewrites

- Richiede un valore

### `--use-secure`

Utilizza URL sicuri. Abilita questa opzione solo se SSL è disponibile. Obsoleto, usa config:set con percorso web/secure/use_in_frontend

- Richiede un valore

### `--base-url-secure`

URL di base per la connessione SSL. Obsoleto, usa config:set con percorso web/secure/base_url

- Richiede un valore

### `--use-secure-admin`

Esegui l’interfaccia di amministrazione con SSL. Obsoleto, usa config:set con percorso web/secure/use_in_adminhtml

- Richiede un valore

### `--admin-use-security-key`

Specifica se utilizzare una funzione di &quot;chiave di sicurezza&quot; negli URL e nei moduli dell’amministratore di Magento. Obsoleto, usa config:set con path admin/security/use_form_key

- Richiede un valore

### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;DIR_IMMAGINE[cache][path]=/var/tmp/cache&quot;

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


## `setup:uninstall`

Disinstalla l&#39;applicazione di Magento

```bash
bin/magento setup:uninstall [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;DIR_IMMAGINE[cache][path]=/var/tmp/cache&quot;

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


## `setup:upgrade`

Aggiorna l&#39;applicazione di Magento, i dati del database e lo schema

```bash
bin/magento setup:upgrade [--keep-generated] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

### `--keep-generated`

Impedisce l&#39;eliminazione dei file generati. L’utilizzo di questa opzione è sconsigliato, tranne quando si distribuisce in produzione. Per ulteriori informazioni, rivolgersi all&#39;integratore o all&#39;amministratore di sistema.

- Predefinito: `false`
- Non accetta un valore

### `--convert-old-scripts`

Consente di convertire gli script precedenti (InstallSchema, UpgradeSchema) nel formato db_schema.xml

- Predefinito: `false`
- Accetta un valore

### `--safe-mode`

Installazione sicura del Magento con immagini su operazioni distruttive, come la rimozione delle colonne

- Accetta un valore

### `--data-restore`

Ripristinare i dati rimossi dalle immagini

- Accetta un valore

### `--dry-run`

L&#39;installazione del Magento viene eseguita in modalità di funzionamento a secco

- Predefinito: `false`
- Accetta un valore

### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;DIR_IMMAGINE[cache][path]=/var/tmp/cache&quot;

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


## `store:list`

Visualizza l&#39;elenco dei negozi

```bash
bin/magento store:list
```

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


## `store:website:list`

Visualizza l&#39;elenco dei siti Web

```bash
bin/magento store:website:list
```

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


## `support:backup:code`

Crea backup del codice

```bash
bin/magento support:backup:code [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs]
```

### `--name`

Nome dump

- Accetta un valore

### `--output`, `-o`

Percorso di output

- Accetta un valore

### `--logs`, `-l`

Includi registri

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


## `support:backup:db`

Crea backup del database

```bash
bin/magento support:backup:db [--name [NAME]] [-o|--output [OUTPUT]] [-l|--logs] [-i|--ignore-sanitize]
```

### `--name`

Nome dump

- Accetta un valore

### `--output`, `-o`

Percorso di output

- Accetta un valore

### `--logs`, `-l`

Includi registri

- Predefinito: `false`
- Non accetta un valore

### `--ignore-sanitize`, `-i`

Ignora bonifica

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


## `support:utility:check`

Controlla le utilità di backup richieste

```bash
bin/magento support:utility:check [--hide-paths]
```

### `--hide-paths`

Controlla solo le utility della console richieste

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


## `support:utility:paths`

Crea elenco percorsi utilità

```bash
bin/magento support:utility:paths [-f|--force]
```

### `--force`, `-f`

Forza

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


## `theme:uninstall`

Disinstalla il tema

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] [--] <theme>...
```


### `theme`

Percorso del tema. Il percorso del tema deve essere specificato come percorso completo, ovvero area/fornitore/nome. Ad esempio, frontend/Magento/blank

- Predefinito: `[]`

- Obbligatorio
- Array

### `--backup-code`

Esegui backup del codice (esclusi i file temporanei)

- Predefinito: `false`
- Non accetta un valore

### `--clear-static-content`, `-c`

Cancellare i file di visualizzazione statica generati.

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


## `varnish:vcl:generate`

Genera vernice VCL e la trasforma nella riga di comando

```bash
bin/magento varnish:vcl:generate [--access-list ACCESS-LIST] [--backend-host BACKEND-HOST] [--backend-port BACKEND-PORT] [--export-version EXPORT-VERSION] [--grace-period GRACE-PERIOD] [--output-file OUTPUT-FILE]
```

### `--access-list`

Elenco di accesso IP in grado di eliminare la vernice

- Predefinito: `localhost`
- Richiede un valore

### `--backend-host`

Host del back-end web

- Predefinito: `localhost`
- Richiede un valore

### `--backend-port`

Porta del back-end web

- Predefinito: `8080`
- Richiede un valore

### `--export-version`

Versione del file di vernice

- Predefinito: `4`
- Richiede un valore

### `--grace-period`

Periodo di tolleranza in secondi

- Predefinito: `300`
- Richiede un valore

### `--output-file`

Percorso del file da scrivere in vcl

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
