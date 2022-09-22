---
source-git-commit: a5777f437430bc48b87aaea65c0e101d4ecd6574
workflow-type: tm+mt
source-wordcount: '14684'
ht-degree: 0%

---
# bin/magento (Magento Open Source)

<!-- All the assigned and captured content is used in the included template -->

<!-- The template to render with above values -->
**Versione**: 2.4.5 <!-- app.version -->

Questo riferimento contiene 111 comandi disponibili tramite il `bin/magento` strumento a riga di comando.
L’elenco iniziale viene generato automaticamente utilizzando `bin/magento list` all&#39;edizione.
Utilizza la [&quot;Aggiungi comandi CLI&quot;](https://developer.adobe.com/commerce/php/development/cli-commands/) guida per aggiungere un comando CLI personalizzato.

>[!NOTE]
>
>Puoi chiamare `bin/magento` Comandi CLI che utilizzano le scelte rapide invece del nome completo del comando. Ad esempio, puoi chiamare `bin/magento setup:upgrade` utilizzo `bin/magento s:up`, `bin/magento s:upg`. Vedi [sintassi di collegamento](https://symfony.com/doc/current/components/console/usage.html#shortcut-syntax) per comprendere come utilizzare le scelte rapide con qualsiasi comando CLI.

>[!NOTE]
>
>Questo riferimento viene generato dal codebase dell&#39;applicazione. Per modificare il contenuto, è possibile aggiornare il codice sorgente per l’implementazione del comando corrispondente nel [codebase](https://github.com/magento) e invia le modifiche per la revisione. Un altro modo è quello di _Invia feedback_ (trova il link in alto a destra). Per gli orientamenti sui contributi, consultare [Contributi codice](https://developer.adobe.com/commerce/contributor/guides/code-contributions/).

## `help`

Visualizza la Guida per un comando

```bash
bin/magento help [--format FORMAT] [--raw] [--] [<command_name>]
```

<!-- app.name --> <!-- command.usage -->

### `command_name`

Nome del comando
- Predefinito: `help`

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `list`

Elenca comandi

```bash
bin/magento list [--raw] [--format FORMAT] [--] [<namespace>]
```

<!-- app.name --> <!-- command.usage -->

### `namespace`

Nome dello spazio dei nomi
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--raw`

Per visualizzare l&#39;elenco dei comandi non elaborati
- Predefinito: `false`
- Non accetta un valore


### `--format`

Il formato di output (txt, xml, json o md)
- Predefinito: `txt`
- Richiede un valore <!-- options --> <!-- options.size -->

## `admin:adobe-ims:disable`

Disattiva il modulo Adobe IMS

```bash
bin/magento admin:adobe-ims:disable
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `admin:adobe-ims:enable`

Attiva il modulo Adobe IMS.

```bash
bin/magento admin:adobe-ims:enable [-o|--organization-id [ORGANIZATION-ID]] [-c|--client-id [CLIENT-ID]] [-s|--client-secret [CLIENT-SECRET]] [-t|--2fa [2FA]]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--organization-id`, `-o`



Imposta l’ID organizzazione per la configurazione di Adobe IMS. Obbligatorio quando si abilita il modulo
- Accetta un valore



### `--client-id`, `-c`



Imposta l’ID client per la configurazione di Adobe IMS. Obbligatorio quando si abilita il modulo
- Accetta un valore



### `--client-secret`, `-s`



Imposta il segreto client per la configurazione di Adobe IMS. Obbligatorio quando si abilita il modulo
- Accetta un valore



### `--2fa`, `-t`



Controlla se 2FA è abilitato per l&#39;organizzazione in Adobe Admin Console. Obbligatorio quando si abilita il modulo
- Accetta un valore



### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `admin:adobe-ims:info`

Informazioni sulla configurazione del modulo Adobe IMS

```bash
bin/magento admin:adobe-ims:info
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `admin:adobe-ims:status`

Stato del modulo Adobe IMS

```bash
bin/magento admin:adobe-ims:status
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `admin:user:create`

Crea un amministratore

```bash
bin/magento admin:user:create [--admin-user ADMIN-USER] [--admin-password ADMIN-PASSWORD] [--admin-email ADMIN-EMAIL] [--admin-firstname ADMIN-FIRSTNAME] [--admin-lastname ADMIN-LASTNAME] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--admin-user`

(Obbligatorio) Utente amministratore
- Richiede un valore


### `--admin-password`

(Obbligatorio) Password amministratore
- Richiede un valore


### `--admin-email`

(Obbligatorio) E-mail dell’amministratore
- Richiede un valore


### `--admin-firstname`

(Obbligatorio) Nome amministratore
- Richiede un valore


### `--admin-lastname`

(Obbligatorio) Cognome amministratore
- Richiede un valore


### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `admin:user:unlock`

Sblocca account amministratore

```bash
bin/magento admin:user:unlock <username>
```

<!-- app.name --> <!-- command.usage -->

### `username`

Nome utente amministratore da sbloccare
- Obbligatorio

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `app:config:dump`

Crea dump dell&#39;applicazione

```bash
bin/magento app:config:dump [<config-types>...]
```

<!-- app.name --> <!-- command.usage -->

### `config-types`

Elenco dei tipi di configurazione separati da uno spazio o ometti per scaricare tutti [ambiti, temi, sistema, i18n]

- Predefinito: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `app:config:import`

Importare dati da file di configurazione condivisi nell&#39;archiviazione dati appropriata

```bash
bin/magento app:config:import
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `app:config:status`

Controlla se la propagazione della configurazione richiede un aggiornamento

```bash
bin/magento app:config:status
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `braintree:migrate`

Migrazione delle schede archiviate da un database di Magento 1

```bash
bin/magento braintree:migrate [--host HOST] [--dbname DBNAME] [--username USERNAME] [--password PASSWORD]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



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



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `cache:clean`

Cancella i tipi di cache

```bash
bin/magento cache:clean [--bootstrap BOOTSTRAP] [--] [<types>...]
```

<!-- app.name --> <!-- command.usage -->

### `types`

Elenco dei tipi di cache separati da spazio o omettete di applicare a tutti i tipi di cache.

- Predefinito: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--bootstrap`

aggiungi o sovrascrivi parametri del bootstrap
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `cache:disable`

Disattiva i tipi di cache

```bash
bin/magento cache:disable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

<!-- app.name --> <!-- command.usage -->

### `types`

Elenco dei tipi di cache separati da spazio o omettete di applicare a tutti i tipi di cache.

- Predefinito: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--bootstrap`

aggiungi o sovrascrivi parametri del bootstrap
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `cache:enable`

Abilita i tipi di cache

```bash
bin/magento cache:enable [--bootstrap BOOTSTRAP] [--] [<types>...]
```

<!-- app.name --> <!-- command.usage -->

### `types`

Elenco dei tipi di cache separati da spazio o omettete di applicare a tutti i tipi di cache.

- Predefinito: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--bootstrap`

aggiungi o sovrascrivi parametri del bootstrap
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `cache:flush`

Archiviazione cache scaricata utilizzata dai tipi di cache

```bash
bin/magento cache:flush [--bootstrap BOOTSTRAP] [--] [<types>...]
```

<!-- app.name --> <!-- command.usage -->

### `types`

Elenco dei tipi di cache separati da spazio o omettete di applicare a tutti i tipi di cache.

- Predefinito: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--bootstrap`

aggiungi o sovrascrivi parametri del bootstrap
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `cache:status`

Verifica lo stato della cache

```bash
bin/magento cache:status [--bootstrap BOOTSTRAP]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--bootstrap`

aggiungi o sovrascrivi parametri del bootstrap
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `catalog:images:resize`

Crea immagini di prodotto ridimensionate

```bash
bin/magento catalog:images:resize [-a|--async] [--skip_hidden_images]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--async`, `-a`



Ridimensiona l’immagine in modalità asincrona
- Predefinito: `false`
- Non accetta un valore


### `--skip_hidden_images`

Non elaborare le immagini contrassegnate come nascoste dalla pagina del prodotto
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `catalog:product:attributes:cleanup`

Rimuove gli attributi di prodotto non utilizzati.

```bash
bin/magento catalog:product:attributes:cleanup
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `cms:wysiwyg:restrict`

Stabilire se applicare la convalida del contenuto di HTML per l’utente o mostrare un avviso

```bash
bin/magento cms:wysiwyg:restrict <restrict>
```

<!-- app.name --> <!-- command.usage -->

### `restrict`

y\n
- Obbligatorio

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `config:sensitive:set`

Impostare valori di configurazione sensibili

```bash
bin/magento config:sensitive:set [-i|--interactive] [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path> [<value>]]
```

<!-- app.name --> <!-- command.usage -->

### `path`

Percorso di configurazione per esempio nome_campo/sezione
<!-- argument -->

### `value`

Valore di configurazione
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--interactive`, `-i`



Attiva la modalità interattiva per impostare tutte le variabili sensibili
- Predefinito: `false`
- Non accetta un valore


### `--scope`

Ambito della configurazione, se non impostato, usa &#39;default&#39;
- Predefinito: `default`
- Accetta un valore


### `--scope-code`

Codice di ambito per la configurazione, stringa vuota per impostazione predefinita
- Predefinito: &quot;
- Accetta un valore



### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `config:set`

Modificare la configurazione del sistema

```bash
bin/magento config:set [--scope SCOPE] [--scope-code SCOPE-CODE] [-e|--lock-env] [-c|--lock-config] [-l|--lock] [--] <path> <value>
```

<!-- app.name --> <!-- command.usage -->

### `path`

Percorso di configurazione in formato sezione/gruppo/nome_campo
- Obbligatorio

   <!-- argument -->

### `value`

Valore di configurazione
- Obbligatorio

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--scope`

Ambito di configurazione (predefinito, sito web o archivio)
- Predefinito: `default`
- Richiede un valore


### `--scope-code`

Codice ambito (obbligatorio solo se l’ambito non è &quot;predefinito&quot;)
- Richiede un valore



### `--lock-env`, `-e`



Valore di blocco che impedisce la modifica nell’amministratore (verrà salvato in app/etc/env.php)
- Predefinito: `false`
- Non accetta un valore



### `--lock-config`, `-c`



Blocca e condividi il valore con altre installazioni, evita modifiche nell’amministratore (sarà salvato in app/etc/config.php)
- Predefinito: `false`
- Non accetta un valore



### `--lock`, `-l`



Obsoleto, utilizza invece l’opzione —lock-env .
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `config:show`

Mostra il valore di configurazione per il percorso specificato. Se il percorso non è specificato, verranno visualizzati tutti i valori salvati

```bash
bin/magento config:show [--scope [SCOPE]] [--scope-code [SCOPE-CODE]] [--] [<path>]
```

<!-- app.name --> <!-- command.usage -->

### `path`

Percorso di configurazione, ad esempio section_id/group_id/field_id
<!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--scope`

Ambito della configurazione, se non specificato, verrà utilizzato l&#39;ambito &quot;predefinito&quot;
- Predefinito: `default`
- Accetta un valore


### `--scope-code`

Codice di ambito (obbligatorio solo se l&#39;ambito non è `default`)
- Predefinito: &quot;
- Accetta un valore



### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `cron:install`

Genera e installa crontab per l&#39;utente corrente

```bash
bin/magento cron:install [-f|--force] [-d|--non-optional]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--force`, `-f`



Forza attività di installazione
- Predefinito: `false`
- Non accetta un valore



### `--non-optional`, `-d`



Installa solo le attività non facoltative (predefinite)
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `cron:remove`

Rimuove le attività dalla scheda cronologica

```bash
bin/magento cron:remove
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `cron:run`

Esegue i processi in base alla pianificazione

```bash
bin/magento cron:run [--group GROUP] [--bootstrap BOOTSTRAP]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--group`

Esegui i processi solo dal gruppo specificato
- Richiede un valore


### `--bootstrap`

Aggiungi o sovrascrivi parametri del bootstrap
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `customer:hash:upgrade`

Aggiorna l’hash del cliente in base all’algoritmo più recente

```bash
bin/magento customer:hash:upgrade
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `deploy:mode:set`

Imposta la modalità applicazione.

```bash
bin/magento deploy:mode:set [-s|--skip-compilation] [--] <mode>
```

<!-- app.name --> <!-- command.usage -->

### `mode`

Modalità dell&#39;applicazione da impostare. Le opzioni disponibili sono &quot;sviluppatore&quot; o &quot;produzione&quot;
- Obbligatorio

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--skip-compilation`, `-s`



Ignora la cancellazione e la rigenerazione del contenuto statico (codice generato, CSS preelaborati e risorse in pub/static/)
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `deploy:mode:show`

Visualizza la modalità applicazione corrente.

```bash
bin/magento deploy:mode:show
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `dev:di:info`

Fornisce informazioni sulla configurazione dell&#39;iniezione di dipendenza per il comando.

```bash
bin/magento dev:di:info <class>
```

<!-- app.name --> <!-- command.usage -->

### `class`

Nome classe
- Obbligatorio

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `dev:email:newsletter-compatibility-check`

Scansiona i modelli di newsletter per potenziali problemi di compatibilità dell’utilizzo delle variabili

```bash
bin/magento dev:email:newsletter-compatibility-check
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `dev:email:override-compatibility-check`

Esegue l&#39;analisi delle sostituzioni dei modelli e-mail per potenziali problemi di compatibilità dell&#39;utilizzo delle variabili

```bash
bin/magento dev:email:override-compatibility-check
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `dev:profiler:disable`

Disattiva il profiler.

```bash
bin/magento dev:profiler:disable
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `dev:profiler:enable`

Attiva il profiler.

```bash
bin/magento dev:profiler:enable [<type>]
```

<!-- app.name --> <!-- command.usage -->

### `type`

Tipo di profiler
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `dev:query-log:disable`

Disabilita registrazione query DB

```bash
bin/magento dev:query-log:disable
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `dev:query-log:enable`

Abilita registrazione query DB

```bash
bin/magento dev:query-log:enable [--include-all-queries [INCLUDE-ALL-QUERIES]] [--query-time-threshold [QUERY-TIME-THRESHOLD]] [--include-call-stack [INCLUDE-CALL-STACK]]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--include-all-queries`

Registra tutte le query. [true\|false]
- Predefinito: `true`
- Accetta un valore


### `--query-time-threshold`

Soglie di tempo della query.
- Predefinito: `0.001`
- Accetta un valore


### `--include-call-stack`

Includi lo stack di chiamate. [true\|false]
- Predefinito: `true`
- Accetta un valore



### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `dev:source-theme:deploy`

Raccoglie e pubblica i file di origine per theme.

```bash
bin/magento dev:source-theme:deploy [--type TYPE] [--locale LOCALE] [--area AREA] [--theme THEME] [--] [<file>...]
```

<!-- app.name --> <!-- command.usage -->

### `file`

File da pre-elaborare (il file deve essere specificato senza estensione)
- Predefinito: `css/styles-mcss/styles-l`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--type`

Tipo di file di origine: [less]
- Predefinito: `less`
- Richiede un valore


### `--locale`

Impostazioni internazionali: [en_US]
- Predefinito: `en_US`
- Richiede un valore


### `--area`

Area: [frontend\|adminhtml]
- Predefinito: `frontend`
- Richiede un valore


### `--theme`

Tema: [Fornitore/tema]
- Predefinito: `Magento/luma`
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `dev:template-hints:disable`

Disattiva i suggerimenti modello frontend. Potrebbe essere necessario uno scaricamento della cache.

```bash
bin/magento dev:template-hints:disable
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `dev:template-hints:enable`

Abilita i suggerimenti modello frontend. Potrebbe essere necessario uno scaricamento della cache.

```bash
bin/magento dev:template-hints:enable
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `dev:template-hints:status`

Mostra lo stato dei suggerimenti modello frontend.

```bash
bin/magento dev:template-hints:status
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `dev:tests:run`

Esegue i test

```bash
bin/magento dev:tests:run [-c|--arguments ARGUMENTS] [--] [<type>]
```

<!-- app.name --> <!-- command.usage -->

### `type`

Tipo di test da eseguire. Tipi disponibili: all, unit, integration, integration-all, static, static, static, all, integrità, legacy, default
- Predefinito: `default`

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--arguments`, `-c`



Argomenti aggiuntivi per PHPUnit. Esempio: &quot;-c&#39;—filter=MyTest&#39;&quot; (senza spazi)
- Predefinito: &quot;
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `dev:urn-catalog:generate`

Genera il catalogo degli URL in *.xsd mappature per l&#39;IDE per evidenziare xml.

```bash
bin/magento dev:urn-catalog:generate [--ide IDE] [--] <path>
```

<!-- app.name --> <!-- command.usage -->

### `path`

Percorso del file per l&#39;output del catalogo. Per PhpStorm utilizzare .idea/misc.xml
- Obbligatorio

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--ide`

Formato in cui verrà generato il catalogo. Supportato: [tempesta, vscode]
- Predefinito: `phpstorm`
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `dev:xml:convert`

Converte i file XML utilizzando i fogli di stile XSL

```bash
bin/magento dev:xml:convert [-o|--overwrite] [--] <xml-file> <processor>
```

<!-- app.name --> <!-- command.usage -->

### `xml-file`

Percorso del file XML che verrà trasformato
- Obbligatorio

   <!-- argument -->

### `processor`

Percorso del foglio di stile XSL da applicare al file XML
- Obbligatorio

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--overwrite`, `-o`



Sovrascrivi file XML
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `downloadable:domains:add`

Aggiungi i domini alla whitelist dei domini scaricabili

```bash
bin/magento downloadable:domains:add [<domains>...]
```

<!-- app.name --> <!-- command.usage -->

### `domains`

Nome del dominio

- Predefinito: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `downloadable:domains:remove`

Rimuovere i domini dalla whitelist dei domini scaricabili

```bash
bin/magento downloadable:domains:remove [<domains>...]
```

<!-- app.name --> <!-- command.usage -->

### `domains`

Nomi di dominio

- Predefinito: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `downloadable:domains:show`

Visualizza la whitelist dei domini scaricabili

```bash
bin/magento downloadable:domains:show
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `encryption:payment-data:update`

Cifra nuovamente i dati della carta di credito crittografati con la crittografia più recente.

```bash
bin/magento encryption:payment-data:update
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `i18n:collect-phrases`

Trova frasi nella codebase

```bash
bin/magento i18n:collect-phrases [-o|--output OUTPUT] [-m|--magento] [--] [<directory>]
```

<!-- app.name --> <!-- command.usage -->

### `directory`

Percorso directory da analizzare. Non necessario se è impostato il flag —magento
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--output`, `-o`



Percorso (compreso il nome del file) di un file di output. Se non viene specificato alcun file, viene impostato automaticamente su stdout.
- Richiede un valore



### `--magento`, `-m`



Usa il parametro —magento per analizzare la base di codice del Magento corrente. Ometti il parametro se è specificata una directory.
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `i18n:pack`

Salva il pacchetto linguistico

```bash
bin/magento i18n:pack [-m|--mode MODE] [-d|--allow-duplicates] [--] <source> <locale>
```

<!-- app.name --> <!-- command.usage -->

### `source`

Percorso del file del dizionario di origine con le traduzioni
- Obbligatorio

   <!-- argument -->

### `locale`

Impostazioni internazionali di destinazione per il dizionario, ad esempio &quot;de_DE&quot;
- Obbligatorio

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--mode`, `-m`



Modalità di salvataggio per dizionario - &quot;replace&quot; - sostituire il Language Pack con un nuovo - &quot;merge&quot; - unire i pacchetti linguistici, per impostazione predefinita &quot;replace&quot;
- Predefinito: `replace`
- Richiede un valore



### `--allow-duplicates`, `-d`



Utilizza il parametro —allow-duplicate per consentire il salvataggio di duplicati di translate. In caso contrario, ometti il parametro .
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `i18n:uninstall`

Disinstalla i pacchetti di lingua

```bash
bin/magento i18n:uninstall [-b|--backup-code] [--] <package>...
```

<!-- app.name --> <!-- command.usage -->

### `package`

Nome del pacchetto linguistico

- Predefinito: `[]`
- Obbligatorio

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--backup-code`, `-b`



Esegui il backup dei file di codice e di configurazione (esclusi i file temporanei)
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `indexer:info`

Mostra gli indicizzatori consentiti

```bash
bin/magento indexer:info
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `indexer:reindex`

Dati reindicizzati

```bash
bin/magento indexer:reindex [<index>...]
```

<!-- app.name --> <!-- command.usage -->

### `index`

Elenco separato da spazi dei tipi di indice o ometto da applicare a tutti gli indici.

- Predefinito: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `indexer:reset`

Ripristina lo stato dell&#39;indicizzatore su non valido

```bash
bin/magento indexer:reset [<index>...]
```

<!-- app.name --> <!-- command.usage -->

### `index`

Elenco separato da spazi dei tipi di indice o ometto da applicare a tutti gli indici.

- Predefinito: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `indexer:set-dimensions-mode`

Imposta modalità Dimension indicizzatore

```bash
bin/magento indexer:set-dimensions-mode [<indexer> [<mode>]]
```

<!-- app.name --> <!-- command.usage -->

### `indexer`

Nome indicizzatore [catalog_product_price]
<!-- argument -->

### `mode`

Le modalità della dimensione indicizzatore catalog_product_price none,sito web,gruppo_cliente,sito_web_and_gruppo_cliente
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `indexer:set-mode`

Imposta il tipo di modalità indice

```bash
bin/magento indexer:set-mode [<mode> [<index>...]]
```

<!-- app.name --> <!-- command.usage -->

### `mode`

Tipo di modalità indicizzatore [in tempo reale|pianificazione]
<!-- argument -->

### `index`

Elenco separato da spazi dei tipi di indice o ometto da applicare a tutti gli indici.

- Predefinito: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `indexer:show-dimensions-mode`

Mostra la modalità Dimension indicizzatore

```bash
bin/magento indexer:show-dimensions-mode [<indexer>...]
```

<!-- app.name --> <!-- command.usage -->

### `indexer`

Elenco separato da spazi dei tipi di indice o omettere di applicare a tutti gli indici (catalog_product_price)

- Predefinito: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `indexer:show-mode`

Mostra modalità indice

```bash
bin/magento indexer:show-mode [<index>...]
```

<!-- app.name --> <!-- command.usage -->

### `index`

Elenco separato da spazi dei tipi di indice o ometto da applicare a tutti gli indici.

- Predefinito: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `indexer:status`

Mostra lo stato dell&#39;indicizzatore

```bash
bin/magento indexer:status [<index>...]
```

<!-- app.name --> <!-- command.usage -->

### `index`

Elenco separato da spazi dei tipi di indice o ometto da applicare a tutti gli indici.

- Predefinito: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `info:adminuri`

Visualizza l&#39;URI amministratore di Magento

```bash
bin/magento info:adminuri
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `info:backups:list`

Stampa l&#39;elenco dei file di backup disponibili

```bash
bin/magento info:backups:list
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `info:currency:list`

Visualizza l&#39;elenco delle valute disponibili

```bash
bin/magento info:currency:list
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `info:dependencies:show-framework`

Mostra il numero di dipendenze dal framework di Magento

```bash
bin/magento info:dependencies:show-framework [-o|--output OUTPUT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--output`, `-o`



Nome del file del rapporto
- Predefinito: `framework-dependencies.csv`
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `info:dependencies:show-modules`

Mostra il numero di dipendenze tra i moduli

```bash
bin/magento info:dependencies:show-modules [-o|--output OUTPUT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--output`, `-o`



Nome del file del rapporto
- Predefinito: `modules-dependencies.csv`
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `info:dependencies:show-modules-circular`

Mostra il numero di dipendenze circolari tra i moduli

```bash
bin/magento info:dependencies:show-modules-circular [-o|--output OUTPUT]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--output`, `-o`



Nome del file del rapporto
- Predefinito: `modules-circular-dependencies.csv`
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `info:language:list`

Visualizza l’elenco delle impostazioni internazionali di lingua disponibili

```bash
bin/magento info:language:list
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `info:timezone:list`

Visualizza l&#39;elenco dei blocchi temporali disponibili

```bash
bin/magento info:timezone:list
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `inventory:reservation:create-compensations`

Crea prenotazioni tramite gli argomenti di retribuzione forniti

```bash
bin/magento inventory:reservation:create-compensations [-r|--raw] [--] [<compensations>...]
```

<!-- app.name --> <!-- command.usage -->

### `compensations`

Elenco degli argomenti di compensazione nel formato &quot;&lt;order_increment_id>:&lt;sku>:&lt;quantity>:&lt;stock-id>&quot;

- Predefinito: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--raw`, `-r`



Uscita non elaborata
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `inventory:reservation:list-inconsistencies`

Mostra tutti gli ordini e i prodotti con incongruenze di quantità salabili

```bash
bin/magento inventory:reservation:list-inconsistencies [-c|--complete-orders] [-i|--incomplete-orders] [-b|--bunch-size [BUNCH-SIZE]] [-r|--raw]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




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



Uscita non elaborata
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `inventory-geonames:import`

Scaricare e importare i nomi geografici per l’algoritmo di selezione della sorgente

```bash
bin/magento inventory-geonames:import <countries>...
```

<!-- app.name --> <!-- command.usage -->

### `countries`

Elenco dei codici paese da importare

- Predefinito: `[]`
- Obbligatorio

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `maintenance:allow-ips`

Imposta gli IP esenti dalla modalità di manutenzione

```bash
bin/magento maintenance:allow-ips [--none] [--add] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<ip>...]
```

<!-- app.name --> <!-- command.usage -->

### `ip`

Indirizzi IP consentiti

- Predefinito: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--none`

Cancella indirizzi IP consentiti
- Predefinito: `false`
- Non accetta un valore


### `--add`

Aggiungi l’indirizzo IP all’elenco esistente
- Predefinito: `false`
- Non accetta un valore


### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `maintenance:disable`

Disattiva la modalità di manutenzione

```bash
bin/magento maintenance:disable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--ip`

Indirizzi IP consentiti (usa &#39;nessuno&#39; per cancellare l&#39;elenco IP consentito)
- Predefinito: `[]`
- Richiede un valore


### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `maintenance:enable`

Abilita la modalità di manutenzione

```bash
bin/magento maintenance:enable [--ip IP] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--ip`

Indirizzi IP consentiti (usa &#39;nessuno&#39; per cancellare l&#39;elenco IP consentito)
- Predefinito: `[]`
- Richiede un valore


### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `maintenance:status`

Visualizza lo stato della modalità di manutenzione

```bash
bin/magento maintenance:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `media-content:sync`

Sincronizzazione del contenuto con le risorse

```bash
bin/magento media-content:sync
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `media-gallery:sync`

Sincronizzazione dell&#39;archiviazione e delle risorse multimediali nel database

```bash
bin/magento media-gallery:sync
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `module:config:status`

Controlla la configurazione dei moduli nel file app/etc/config.php e segnala se sono aggiornati o meno

```bash
bin/magento module:config:status
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `module:disable`

Disabilita i moduli specificati

```bash
bin/magento module:disable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

<!-- app.name --> <!-- command.usage -->

### `module`

Nome del modulo

- Predefinito: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--force`, `-f`



Ignora controllo dipendenze
- Predefinito: `false`
- Non accetta un valore


### `--all`

Disattiva tutti i moduli
- Predefinito: `false`
- Non accetta un valore



### `--clear-static-content`, `-c`



Cancella i file di visualizzazione statica generati. Necessario, se i moduli dispongono di file di visualizzazione statici
- Predefinito: `false`
- Non accetta un valore


### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `module:enable`

Abilita i moduli specificati

```bash
bin/magento module:enable [-f|--force] [--all] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module>...]
```

<!-- app.name --> <!-- command.usage -->

### `module`

Nome del modulo

- Predefinito: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--force`, `-f`



Ignora controllo dipendenze
- Predefinito: `false`
- Non accetta un valore


### `--all`

Abilita tutti i moduli
- Predefinito: `false`
- Non accetta un valore



### `--clear-static-content`, `-c`



Cancella i file di visualizzazione statica generati. Necessario, se i moduli dispongono di file di visualizzazione statici
- Predefinito: `false`
- Non accetta un valore


### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `module:status`

Visualizza lo stato dei moduli

```bash
bin/magento module:status [--enabled] [--disabled] [--magento-init-params MAGENTO-INIT-PARAMS] [--] [<module-names>...]
```

<!-- app.name --> <!-- command.usage -->

### `module-names`

Nome modulo opzionale

- Predefinito: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--enabled`

Solo moduli abilitati per la stampa
- Predefinito: `false`
- Non accetta un valore


### `--disabled`

Solo stampa moduli disattivati
- Predefinito: `false`
- Non accetta un valore


### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `module:uninstall`

Disinstalla i moduli installati dal compositore

```bash
bin/magento module:uninstall [-r|--remove-data] [--backup-code] [--backup-media] [--backup-db] [--non-composer] [-c|--clear-static-content] [--magento-init-params MAGENTO-INIT-PARAMS] [--] <module>...
```

<!-- app.name --> <!-- command.usage -->

### `module`

Nome del modulo

- Predefinito: `[]`
- Obbligatorio

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--remove-data`, `-r`



Rimuovere i dati installati dai moduli
- Predefinito: `false`
- Non accetta un valore


### `--backup-code`

Esegui il backup dei file di codice e di configurazione (esclusi i file temporanei)
- Predefinito: `false`
- Non accetta un valore


### `--backup-media`

Backup su supporti
- Predefinito: `false`
- Non accetta un valore


### `--backup-db`

Esegui backup completo del database
- Predefinito: `false`
- Non accetta un valore


### `--non-composer`

Tutti i moduli, che saranno passati qui saranno non basati su compositore
- Predefinito: `false`
- Non accetta un valore



### `--clear-static-content`, `-c`



Cancella i file di visualizzazione statica generati. Necessario, se i moduli dispongono di file di visualizzazione statici
- Predefinito: `false`
- Non accetta un valore


### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `newrelic:create:deploy-marker`

Controlla la coda di distribuzione per le voci e crea un marcatore di distribuzione appropriato.

```bash
bin/magento newrelic:create:deploy-marker <message> <change_log> [<user> [<revision>]]
```

<!-- app.name --> <!-- command.usage -->

### `message`

Distribuisci messaggio?
- Obbligatorio

   <!-- argument -->

### `change_log`

Cambia registro?
- Obbligatorio

   <!-- argument -->

### `user`

Utente distribuzione
<!-- argument -->

### `revision`

Revisione
<!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `queue:consumers:list`

Elenco dei consumatori di MessageQueue

```bash
bin/magento queue:consumers:list
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `queue:consumers:start`

Avvia consumer MessageQueue

```bash
bin/magento queue:consumers:start [--max-messages MAX-MESSAGES] [--batch-size BATCH-SIZE] [--area-code AREA-CODE] [--single-thread] [--multi-process [MULTI-PROCESS]] [--pid-file-path PID-FILE-PATH] [--] <consumer>
```

<!-- app.name --> <!-- command.usage -->

### `consumer`

Nome del consumatore da avviare.
- Obbligatorio

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--max-messages`

Il numero di messaggi che il consumatore deve elaborare prima della chiusura del processo. Se non viene specificato - termina dopo l’elaborazione di tutti i messaggi in coda.
- Richiede un valore


### `--batch-size`

Numero di messaggi per batch. Applicabile solo al consumatore batch.
- Richiede un valore


### `--area-code`

L’impostazione predefinita dell’area preferita (globale, adminhtml, ecc..) è globale.
- Richiede un valore


### `--single-thread`

Questa opzione impedisce l’esecuzione simultanea di più copie di un consumatore.
- Predefinito: `false`
- Non accetta un valore


### `--multi-process`

Numero di processi per consumatore.
- Accetta un valore


### `--pid-file-path`

Percorso file per il salvataggio del PID (questa opzione è obsoleta, usa invece —single-thread)
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `remote-storage:sync`

Sincronizzare i file multimediali con l&#39;archiviazione remota.

```bash
bin/magento remote-storage:sync
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `sampledata:deploy`

Distribuire moduli di dati di esempio per le installazioni di Magenti basati su compositore

```bash
bin/magento sampledata:deploy [--no-update]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-update`

Aggiorna composer.json senza eseguire l&#39;aggiornamento del compositore
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `sampledata:remove`

Rimuovi tutti i pacchetti di dati di esempio da compositore.json

```bash
bin/magento sampledata:remove [--no-update]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--no-update`

Aggiorna composer.json senza eseguire l&#39;aggiornamento del compositore
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `sampledata:reset`

Reimpostare tutti i moduli di dati di esempio per la reinstallazione

```bash
bin/magento sampledata:reset
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `security:recaptcha:disable-for-user-forgot-password`

Disattiva reCAPTCHA per modulo password dimenticata dall&#39;utente amministratore

```bash
bin/magento security:recaptcha:disable-for-user-forgot-password
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `security:recaptcha:disable-for-user-login`

Disattiva reCAPTCHA per il modulo di accesso utente amministratore

```bash
bin/magento security:recaptcha:disable-for-user-login
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `security:tfa:google:set-secret`

Imposta il segreto utilizzato per la generazione OTP di Google.

```bash
bin/magento security:tfa:google:set-secret <user> <secret>
```

<!-- app.name --> <!-- command.usage -->

### `user`

Nome utente
- Obbligatorio

   <!-- argument -->

### `secret`

Segreto
- Obbligatorio

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `security:tfa:providers`

Elenca tutti i provider disponibili

```bash
bin/magento security:tfa:providers
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `security:tfa:reset`

Ripristino della configurazione per un utente

```bash
bin/magento security:tfa:reset <user> <provider>
```

<!-- app.name --> <!-- command.usage -->

### `user`

Nome utente
- Obbligatorio

   <!-- argument -->

### `provider`

Codice fornitore
- Obbligatorio

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `setup:backup`

Esegue il backup della base di codice dell&#39;applicazione di Magento, del supporto e del database

```bash
bin/magento setup:backup [--code] [--media] [--db] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--code`

Esegui il backup dei file di codice e di configurazione (esclusi i file temporanei)
- Predefinito: `false`
- Non accetta un valore


### `--media`

Backup su supporti
- Predefinito: `false`
- Non accetta un valore


### `--db`

Esegui backup completo del database
- Predefinito: `false`
- Non accetta un valore


### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `setup:config:set`

Crea o modifica la configurazione della distribuzione

```bash
bin/magento setup:config:set [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--backend-frontname`

Nome frontespizio backend (se mancante verrà generato automaticamente)
- Richiede un valore


### `--enable-debug-logging`

Abilita registrazione debug
- Richiede un valore


### `--enable-syslog-logging`

Abilita log syslog
- Richiede un valore


### `--remote-storage-driver`

Driver di archiviazione remoto
- Richiede un valore


### `--remote-storage-prefix`

Prefisso archiviazione remota
- Predefinito: &quot;
- Richiede un valore


### `--remote-storage-endpoint`

Endpoint di archiviazione remoto
- Richiede un valore


### `--remote-storage-bucket`

bucket di archiviazione remota
- Richiede un valore


### `--remote-storage-region`

Area di archiviazione remota
- Richiede un valore


### `--remote-storage-key`

Chiave di accesso all&#39;archiviazione remota
- Predefinito: &quot;
- Richiede un valore


### `--remote-storage-secret`

Chiave segreta archiviazione remota
- Predefinito: &quot;
- Richiede un valore


### `--remote-storage-path-style`

Stile del percorso di archiviazione remota
- Predefinito: `0`
- Richiede un valore


### `--amqp-host`

Host server Amqp
- Predefinito: &quot;
- Richiede un valore


### `--amqp-port`

Porta server Amqp
- Predefinito: `5672`
- Richiede un valore


### `--amqp-user`

Nome utente del server Amqp
- Predefinito: &quot;
- Richiede un valore


### `--amqp-password`

Password del server Amqp
- Predefinito: &quot;
- Richiede un valore


### `--amqp-virtualhost`

virtualhost Amqp
- Predefinito: `/`
- Richiede un valore


### `--amqp-ssl`

SSL Amqp
- Predefinito: &quot;
- Richiede un valore


### `--amqp-ssl-options`

Opzioni SSL Amqp (JSON)
- Predefinito: &quot;
- Richiede un valore


### `--consumers-wait-for-messages`

I consumatori devono attendere un messaggio dalla coda? 1 - Sì, 0 - No
- Richiede un valore


### `--queue-default-connection`

Connessione predefinita in coda messaggi. Può essere &#39;db&#39;, &#39;amqp&#39; o un sistema di coda personalizzato. Il sistema di coda deve essere installato e configurato, altrimenti i messaggi non verranno elaborati correttamente.
- Richiede un valore


### `--key`

Chiave di crittografia
- Richiede un valore


### `--db-host`

Host server database
- Richiede un valore


### `--db-name`

Nome database
- Richiede un valore


### `--db-user`

Nome utente del server di database
- Richiede un valore


### `--db-engine`

Motore server database
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



Se specificato, la convalida della connessione del database verrà ignorata
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

Percorso completo del file del certificato client per stabilire la connessione del db tramite SSL
- Predefinito: &quot;
- Richiede un valore


### `--db-ssl-ca`

Percorso completo del file di certificato del server per stabilire la connessione del database tramite SSL
- Predefinito: &quot;
- Richiede un valore


### `--db-ssl-verify`

Verifica della certificazione del server
- Predefinito: `false`
- Non accetta un valore


### `--session-save`

Gestore di salvataggio della sessione
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

Timeout connessione, in secondi
- Richiede un valore


### `--session-save-redis-persistent-id`

Stringa univoca per abilitare le connessioni permanenti
- Richiede un valore


### `--session-save-redis-db`

Numero del database Redis
- Richiede un valore


### `--session-save-redis-compression-threshold`

Soglia di compressione Redis
- Richiede un valore


### `--session-save-redis-compression-lib`

Libreria di compressione Redis. Valori: gzip (predefinito), lzf, lz4, snappy
- Richiede un valore


### `--session-save-redis-log-level`

Ridisfa il livello di log. Valori: Da 0 (minimo) a 7 (più dettagliato)
- Richiede un valore


### `--session-save-redis-max-concurrency`

Numero massimo di processi che possono attendere un blocco in una sessione
- Richiede un valore


### `--session-save-redis-break-after-frontend`

Numero di secondi da attendere prima di tentare di interrompere un blocco per una sessione frontale
- Richiede un valore


### `--session-save-redis-break-after-adminhtml`

Numero di secondi di attesa prima di tentare di interrompere un blocco per la sessione di amministrazione
- Richiede un valore


### `--session-save-redis-first-lifetime`

Ciclo di vita, in secondi, della sessione per i non-robot nella prima scrittura (usare 0 per disabilitare)
- Richiede un valore


### `--session-save-redis-bot-first-lifetime`

Durata, in secondi, della sessione per i bot nella prima scrittura (usare 0 per disabilitare)
- Richiede un valore


### `--session-save-redis-bot-lifetime`

Ciclo di vita della sessione per i bot nelle scritture successive (usare 0 per disabilitare)
- Richiede un valore


### `--session-save-redis-disable-locking`

Disabilita nuovamente il blocco. Valori: false (predefinito), true
- Richiede un valore


### `--session-save-redis-min-lifetime`

Ridis durata minima della sessione, in secondi
- Richiede un valore


### `--session-save-redis-max-lifetime`

Durata massima della sessione di Redis, in secondi
- Richiede un valore


### `--session-save-redis-sentinel-master`

Master Redis Sentinel
- Richiede un valore


### `--session-save-redis-sentinel-servers`

Server Sentinel Redis, separati da virgole
- Richiede un valore


### `--session-save-redis-sentinel-verify-master`

Redis Sentinel verifica master. Valori: false (predefinito), true
- Richiede un valore


### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel nuovi tentativi di connessione.
- Richiede un valore


### `--cache-backend`

Gestore di cache predefinito
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

Imposta su 0 per disabilitare la compressione (il valore predefinito è 1, abilitato)
- Richiede un valore


### `--cache-backend-redis-compression-lib`

Compressione lib da utilizzare [snappy,lzf,l4z,zstd,gzip] (lasciare vuoto per determinare automaticamente)
- Richiede un valore


### `--cache-id-prefix`

Prefisso ID per le chiavi di cache
- Richiede un valore


### `--allow-parallel-generation`

Consenti generazione cache in modo non bloccato
- Predefinito: `false`
- Non accetta un valore


### `--page-cache`

Gestore di cache predefinito
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

Imposta su 1 per comprimere la cache della pagina intera (usa 0 per disabilitare)
- Richiede un valore


### `--page-cache-redis-compression-lib`

Libreria di compressione da utilizzare [snappy,lzf,l4z,zstd,gzip] (lasciare vuoto per determinare automaticamente)
- Richiede un valore


### `--page-cache-id-prefix`

Prefisso ID per le chiavi di cache
- Richiede un valore


### `--lock-provider`

Blocca nome provider
- Richiede un valore


### `--lock-db-prefix`

Prefisso di blocco specifico per l&#39;installazione per evitare conflitti di blocco
- Richiede un valore


### `--lock-zookeeper-host`

Host e porta per connettersi al cluster Zookeeper. Ad esempio: 127.0.0.1:2181
- Richiede un valore


### `--lock-zookeeper-path`

Percorso in cui Zookeeper salverà le serrature. Il percorso predefinito è: /magento/locks
- Richiede un valore


### `--lock-file-path`

Percorso in cui verranno salvati i blocchi di file.
- Richiede un valore


### `--document-root-is-pub`

Flag da mostrare se il Pub è nella radice, può essere solo vero o falso
- Richiede un valore


### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `setup:db-data:upgrade`

Installa e aggiorna i dati nel database

```bash
bin/magento setup:db-data:upgrade [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `setup:db-declaration:generate-patch`

Genera patch e inseriscila in una cartella specifica.

```bash
bin/magento setup:db-declaration:generate-patch [--revertable [REVERTABLE]] [--type [TYPE]] [--] <module> <patch>
```

<!-- app.name --> <!-- command.usage -->

### `module`

Nome modulo
- Obbligatorio

   <!-- argument -->

### `patch`

Nome patch
- Obbligatorio

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--revertable`

Controllare se la patch è reversibile o meno.
- Predefinito: `false`
- Accetta un valore


### `--type`

Scopri il tipo di patch da generare. Valori disponibili: `data`, `schema`.
- Predefinito: `data`
- Accetta un valore



### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `setup:db-declaration:generate-whitelist`

Genera una whitelist di tabelle e colonne che possono essere modificate dal programma di installazione delle dichiarazioni

```bash
bin/magento setup:db-declaration:generate-whitelist [--module-name [MODULE-NAME]]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--module-name`

Nome del modulo in cui verrà generata la whitelist
- Predefinito: `all`
- Accetta un valore



### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `setup:db-schema:upgrade`

Installa e aggiorna lo schema DB

```bash
bin/magento setup:db-schema:upgrade [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--convert-old-scripts`

Consente di convertire i vecchi script (InstallSchema, UpgradeSchema) in formato db_schema.xml
- Predefinito: `false`
- Accetta un valore


### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `setup:db:status`

Controlla se lo schema o i dati del database richiedono un aggiornamento

```bash
bin/magento setup:db:status [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `setup:di:compile`

Genera la configurazione DI e tutte le classi mancanti che possono essere generate automaticamente

```bash
bin/magento setup:di:compile
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `setup:install`

Installa l&#39;applicazione di Magento

```bash
bin/magento setup:install [--backend-frontname BACKEND-FRONTNAME] [--enable-debug-logging ENABLE-DEBUG-LOGGING] [--enable-syslog-logging ENABLE-SYSLOG-LOGGING] [--remote-storage-driver REMOTE-STORAGE-DRIVER] [--remote-storage-prefix REMOTE-STORAGE-PREFIX] [--remote-storage-endpoint REMOTE-STORAGE-ENDPOINT] [--remote-storage-bucket REMOTE-STORAGE-BUCKET] [--remote-storage-region REMOTE-STORAGE-REGION] [--remote-storage-key REMOTE-STORAGE-KEY] [--remote-storage-secret REMOTE-STORAGE-SECRET] [--remote-storage-path-style REMOTE-STORAGE-PATH-STYLE] [--amqp-host AMQP-HOST] [--amqp-port AMQP-PORT] [--amqp-user AMQP-USER] [--amqp-password AMQP-PASSWORD] [--amqp-virtualhost AMQP-VIRTUALHOST] [--amqp-ssl AMQP-SSL] [--amqp-ssl-options AMQP-SSL-OPTIONS] [--consumers-wait-for-messages CONSUMERS-WAIT-FOR-MESSAGES] [--queue-default-connection QUEUE-DEFAULT-CONNECTION] [--key KEY] [--db-host DB-HOST] [--db-name DB-NAME] [--db-user DB-USER] [--db-engine DB-ENGINE] [--db-password DB-PASSWORD] [--db-prefix DB-PREFIX] [--db-model DB-MODEL] [--db-init-statements DB-INIT-STATEMENTS] [-s|--skip-db-validation] [--http-cache-hosts HTTP-CACHE-HOSTS] [--db-ssl-key DB-SSL-KEY] [--db-ssl-cert DB-SSL-CERT] [--db-ssl-ca DB-SSL-CA] [--db-ssl-verify] [--session-save SESSION-SAVE] [--session-save-redis-host SESSION-SAVE-REDIS-HOST] [--session-save-redis-port SESSION-SAVE-REDIS-PORT] [--session-save-redis-password SESSION-SAVE-REDIS-PASSWORD] [--session-save-redis-timeout SESSION-SAVE-REDIS-TIMEOUT] [--session-save-redis-persistent-id SESSION-SAVE-REDIS-PERSISTENT-ID] [--session-save-redis-db SESSION-SAVE-REDIS-DB] [--session-save-redis-compression-threshold SESSION-SAVE-REDIS-COMPRESSION-THRESHOLD] [--session-save-redis-compression-lib SESSION-SAVE-REDIS-COMPRESSION-LIB] [--session-save-redis-log-level SESSION-SAVE-REDIS-LOG-LEVEL] [--session-save-redis-max-concurrency SESSION-SAVE-REDIS-MAX-CONCURRENCY] [--session-save-redis-break-after-frontend SESSION-SAVE-REDIS-BREAK-AFTER-FRONTEND] [--session-save-redis-break-after-adminhtml SESSION-SAVE-REDIS-BREAK-AFTER-ADMINHTML] [--session-save-redis-first-lifetime SESSION-SAVE-REDIS-FIRST-LIFETIME] [--session-save-redis-bot-first-lifetime SESSION-SAVE-REDIS-BOT-FIRST-LIFETIME] [--session-save-redis-bot-lifetime SESSION-SAVE-REDIS-BOT-LIFETIME] [--session-save-redis-disable-locking SESSION-SAVE-REDIS-DISABLE-LOCKING] [--session-save-redis-min-lifetime SESSION-SAVE-REDIS-MIN-LIFETIME] [--session-save-redis-max-lifetime SESSION-SAVE-REDIS-MAX-LIFETIME] [--session-save-redis-sentinel-master SESSION-SAVE-REDIS-SENTINEL-MASTER] [--session-save-redis-sentinel-servers SESSION-SAVE-REDIS-SENTINEL-SERVERS] [--session-save-redis-sentinel-verify-master SESSION-SAVE-REDIS-SENTINEL-VERIFY-MASTER] [--session-save-redis-sentinel-connect-retries SESSION-SAVE-REDIS-SENTINEL-CONNECT-RETRIES] [--cache-backend CACHE-BACKEND] [--cache-backend-redis-server CACHE-BACKEND-REDIS-SERVER] [--cache-backend-redis-db CACHE-BACKEND-REDIS-DB] [--cache-backend-redis-port CACHE-BACKEND-REDIS-PORT] [--cache-backend-redis-password CACHE-BACKEND-REDIS-PASSWORD] [--cache-backend-redis-compress-data CACHE-BACKEND-REDIS-COMPRESS-DATA] [--cache-backend-redis-compression-lib CACHE-BACKEND-REDIS-COMPRESSION-LIB] [--cache-id-prefix CACHE-ID-PREFIX] [--allow-parallel-generation] [--page-cache PAGE-CACHE] [--page-cache-redis-server PAGE-CACHE-REDIS-SERVER] [--page-cache-redis-db PAGE-CACHE-REDIS-DB] [--page-cache-redis-port PAGE-CACHE-REDIS-PORT] [--page-cache-redis-password PAGE-CACHE-REDIS-PASSWORD] [--page-cache-redis-compress-data PAGE-CACHE-REDIS-COMPRESS-DATA] [--page-cache-redis-compression-lib PAGE-CACHE-REDIS-COMPRESSION-LIB] [--page-cache-id-prefix PAGE-CACHE-ID-PREFIX] [--lock-provider LOCK-PROVIDER] [--lock-db-prefix LOCK-DB-PREFIX] [--lock-zookeeper-host LOCK-ZOOKEEPER-HOST] [--lock-zookeeper-path LOCK-ZOOKEEPER-PATH] [--lock-file-path LOCK-FILE-PATH] [--document-root-is-pub DOCUMENT-ROOT-IS-PUB] [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--admin-user [ADMIN-USER]] [--admin-password [ADMIN-PASSWORD]] [--admin-email [ADMIN-EMAIL]] [--admin-firstname [ADMIN-FIRSTNAME]] [--admin-lastname [ADMIN-LASTNAME]] [--search-engine SEARCH-ENGINE] [--elasticsearch-host ELASTICSEARCH-HOST] [--elasticsearch-port ELASTICSEARCH-PORT] [--elasticsearch-enable-auth ELASTICSEARCH-ENABLE-AUTH] [--elasticsearch-username ELASTICSEARCH-USERNAME] [--elasticsearch-password ELASTICSEARCH-PASSWORD] [--elasticsearch-index-prefix ELASTICSEARCH-INDEX-PREFIX] [--elasticsearch-timeout ELASTICSEARCH-TIMEOUT] [--cleanup-database] [--sales-order-increment-prefix SALES-ORDER-INCREMENT-PREFIX] [--use-sample-data] [--enable-modules [ENABLE-MODULES]] [--disable-modules [DISABLE-MODULES]] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [-i|--interactive] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--backend-frontname`

Nome frontespizio backend (se mancante verrà generato automaticamente)
- Richiede un valore


### `--enable-debug-logging`

Abilita registrazione debug
- Richiede un valore


### `--enable-syslog-logging`

Abilita log syslog
- Richiede un valore


### `--remote-storage-driver`

Driver di archiviazione remoto
- Richiede un valore


### `--remote-storage-prefix`

Prefisso archiviazione remota
- Predefinito: &quot;
- Richiede un valore


### `--remote-storage-endpoint`

Endpoint di archiviazione remoto
- Richiede un valore


### `--remote-storage-bucket`

bucket di archiviazione remota
- Richiede un valore


### `--remote-storage-region`

Area di archiviazione remota
- Richiede un valore


### `--remote-storage-key`

Chiave di accesso all&#39;archiviazione remota
- Predefinito: &quot;
- Richiede un valore


### `--remote-storage-secret`

Chiave segreta archiviazione remota
- Predefinito: &quot;
- Richiede un valore


### `--remote-storage-path-style`

Stile del percorso di archiviazione remota
- Predefinito: `0`
- Richiede un valore


### `--amqp-host`

Host server Amqp
- Predefinito: &quot;
- Richiede un valore


### `--amqp-port`

Porta server Amqp
- Predefinito: `5672`
- Richiede un valore


### `--amqp-user`

Nome utente del server Amqp
- Predefinito: &quot;
- Richiede un valore


### `--amqp-password`

Password del server Amqp
- Predefinito: &quot;
- Richiede un valore


### `--amqp-virtualhost`

virtualhost Amqp
- Predefinito: `/`
- Richiede un valore


### `--amqp-ssl`

SSL Amqp
- Predefinito: &quot;
- Richiede un valore


### `--amqp-ssl-options`

Opzioni SSL Amqp (JSON)
- Predefinito: &quot;
- Richiede un valore


### `--consumers-wait-for-messages`

I consumatori devono attendere un messaggio dalla coda? 1 - Sì, 0 - No
- Richiede un valore


### `--queue-default-connection`

Connessione predefinita in coda messaggi. Può essere &#39;db&#39;, &#39;amqp&#39; o un sistema di coda personalizzato. Il sistema di coda deve essere installato e configurato, altrimenti i messaggi non verranno elaborati correttamente.
- Richiede un valore


### `--key`

Chiave di crittografia
- Richiede un valore


### `--db-host`

Host server database
- Richiede un valore


### `--db-name`

Nome database
- Richiede un valore


### `--db-user`

Nome utente del server di database
- Richiede un valore


### `--db-engine`

Motore server database
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



Se specificato, la convalida della connessione del database verrà ignorata
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

Percorso completo del file del certificato client per stabilire la connessione del db tramite SSL
- Predefinito: &quot;
- Richiede un valore


### `--db-ssl-ca`

Percorso completo del file di certificato del server per stabilire la connessione del database tramite SSL
- Predefinito: &quot;
- Richiede un valore


### `--db-ssl-verify`

Verifica della certificazione del server
- Predefinito: `false`
- Non accetta un valore


### `--session-save`

Gestore di salvataggio della sessione
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

Timeout connessione, in secondi
- Richiede un valore


### `--session-save-redis-persistent-id`

Stringa univoca per abilitare le connessioni permanenti
- Richiede un valore


### `--session-save-redis-db`

Numero del database Redis
- Richiede un valore


### `--session-save-redis-compression-threshold`

Soglia di compressione Redis
- Richiede un valore


### `--session-save-redis-compression-lib`

Libreria di compressione Redis. Valori: gzip (predefinito), lzf, lz4, snappy
- Richiede un valore


### `--session-save-redis-log-level`

Ridisfa il livello di log. Valori: Da 0 (minimo) a 7 (più dettagliato)
- Richiede un valore


### `--session-save-redis-max-concurrency`

Numero massimo di processi che possono attendere un blocco in una sessione
- Richiede un valore


### `--session-save-redis-break-after-frontend`

Numero di secondi da attendere prima di tentare di interrompere un blocco per una sessione frontale
- Richiede un valore


### `--session-save-redis-break-after-adminhtml`

Numero di secondi di attesa prima di tentare di interrompere un blocco per la sessione di amministrazione
- Richiede un valore


### `--session-save-redis-first-lifetime`

Ciclo di vita, in secondi, della sessione per i non-robot nella prima scrittura (usare 0 per disabilitare)
- Richiede un valore


### `--session-save-redis-bot-first-lifetime`

Durata, in secondi, della sessione per i bot nella prima scrittura (usare 0 per disabilitare)
- Richiede un valore


### `--session-save-redis-bot-lifetime`

Ciclo di vita della sessione per i bot nelle scritture successive (usare 0 per disabilitare)
- Richiede un valore


### `--session-save-redis-disable-locking`

Disabilita nuovamente il blocco. Valori: false (predefinito), true
- Richiede un valore


### `--session-save-redis-min-lifetime`

Ridis durata minima della sessione, in secondi
- Richiede un valore


### `--session-save-redis-max-lifetime`

Durata massima della sessione di Redis, in secondi
- Richiede un valore


### `--session-save-redis-sentinel-master`

Master Redis Sentinel
- Richiede un valore


### `--session-save-redis-sentinel-servers`

Server Sentinel Redis, separati da virgole
- Richiede un valore


### `--session-save-redis-sentinel-verify-master`

Redis Sentinel verifica master. Valori: false (predefinito), true
- Richiede un valore


### `--session-save-redis-sentinel-connect-retries`

Redis Sentinel nuovi tentativi di connessione.
- Richiede un valore


### `--cache-backend`

Gestore di cache predefinito
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

Imposta su 0 per disabilitare la compressione (il valore predefinito è 1, abilitato)
- Richiede un valore


### `--cache-backend-redis-compression-lib`

Compressione lib da utilizzare [snappy,lzf,l4z,zstd,gzip] (lasciare vuoto per determinare automaticamente)
- Richiede un valore


### `--cache-id-prefix`

Prefisso ID per le chiavi di cache
- Richiede un valore


### `--allow-parallel-generation`

Consenti generazione cache in modo non bloccato
- Predefinito: `false`
- Non accetta un valore


### `--page-cache`

Gestore di cache predefinito
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

Imposta su 1 per comprimere la cache della pagina intera (usa 0 per disabilitare)
- Richiede un valore


### `--page-cache-redis-compression-lib`

Libreria di compressione da utilizzare [snappy,lzf,l4z,zstd,gzip] (lasciare vuoto per determinare automaticamente)
- Richiede un valore


### `--page-cache-id-prefix`

Prefisso ID per le chiavi di cache
- Richiede un valore


### `--lock-provider`

Blocca nome provider
- Richiede un valore


### `--lock-db-prefix`

Prefisso di blocco specifico per l&#39;installazione per evitare conflitti di blocco
- Richiede un valore


### `--lock-zookeeper-host`

Host e porta per connettersi al cluster Zookeeper. Ad esempio: 127.0.0.1:2181
- Richiede un valore


### `--lock-zookeeper-path`

Percorso in cui Zookeeper salverà le serrature. Il percorso predefinito è: /magento/locks
- Richiede un valore


### `--lock-file-path`

Percorso in cui verranno salvati i blocchi di file.
- Richiede un valore


### `--document-root-is-pub`

Flag da mostrare se il Pub è nella radice, può essere solo vero o falso
- Richiede un valore


### `--base-url`

URL in cui lo store deve essere disponibile. Obsoleto, usa config:set con percorso web/unsecure/base_url
- Richiede un valore


### `--language`

Codice lingua predefinito. Obsoleto, usa config:set con percorso generale/locale/codice
- Richiede un valore


### `--timezone`

Codice del fuso orario predefinito. Obsoleto, usa config:set con percorso generale/locale/fuso orario
- Richiede un valore


### `--currency`

Codice valuta predefinito. Obsoleto, usa config:set con percorso currency/options/base, currency/options/default e currency/options/allow
- Richiede un valore


### `--use-rewrites`

Utilizza le riscritture. Obsoleto, usa config:set con il percorso web/seo/use_rewrites
- Richiede un valore


### `--use-secure`

Utilizzare URL sicuri. Abilita questa opzione solo se SSL è disponibile. Obsoleto, usa config:set con il percorso web/secure/use_in_frontend
- Richiede un valore


### `--base-url-secure`

URL di base per la connessione SSL. Obsoleto, usa config:set con percorso web/secure/base_url
- Richiede un valore


### `--use-secure-admin`

Esegui l&#39;interfaccia di amministrazione con SSL. Obsoleto, usa config:set con il percorso web/secure/use_in_adminhtml
- Richiede un valore


### `--admin-use-security-key`

Se utilizzare una funzione &quot;chiave di sicurezza&quot; negli URL e nei moduli dell’amministratore di Magento. Obsoleto, usa config:set con percorso admin/security/use_form_key
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

Motore di ricerca. Valori: elasticsearch5, elasticsearch6, elasticsearch7
- Richiede un valore


### `--elasticsearch-host`

Host del server di Elasticsearch.
- Richiede un valore


### `--elasticsearch-port`

Porta server di Elasticsearch.
- Richiede un valore


### `--elasticsearch-enable-auth`

Imposta su 1 per abilitare l’autenticazione. (Il valore predefinito è 0, disabilitato)
- Richiede un valore


### `--elasticsearch-username`

Elasticsearch nome utente. Applicabile solo se l’autenticazione HTTP è abilitata
- Richiede un valore


### `--elasticsearch-password`

Elasticsearch di password. Applicabile solo se l’autenticazione HTTP è abilitata
- Richiede un valore


### `--elasticsearch-index-prefix`

Elasticsearch di prefisso dell&#39;indice.
- Richiede un valore


### `--elasticsearch-timeout`

Elasticsearch di timeout del server.
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

Elenco dei nomi dei moduli separati da virgole. Questo deve essere incluso durante l&#39;installazione. Param magico disponibile &quot;all&quot;.
- Accetta un valore


### `--disable-modules`

Elenco dei nomi dei moduli separati da virgole. Questo deve essere evitato durante l&#39;installazione. Param magico disponibile &quot;all&quot;.
- Accetta un valore


### `--convert-old-scripts`

Consente di convertire i vecchi script (InstallSchema, UpgradeSchema) in formato db_schema.xml
- Predefinito: `false`
- Accetta un valore



### `--interactive`, `-i`



Installazione di Magenti interattivi
- Predefinito: `false`
- Non accetta un valore


### `--safe-mode`

Installazione sicura del Magento con immagini in operazioni distruttive, come la rimozione delle colonne
- Accetta un valore


### `--data-restore`

Ripristinare i dati rimossi dalle immagini
- Accetta un valore


### `--dry-run`

L&#39;installazione del Magento verrà eseguita in modalità a secco
- Predefinito: `false`
- Accetta un valore


### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `setup:performance:generate-fixtures`

Genera gli staffaggi

```bash
bin/magento setup:performance:generate-fixtures [-s|--skip-reindex] [--] <profile>
```

<!-- app.name --> <!-- command.usage -->

### `profile`

Percorso del file di configurazione del profilo
- Obbligatorio

   <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--skip-reindex`, `-s`



Ignora reindicizzazione
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `setup:rollback`

Rollback del database, supporto e base di codice dell&#39;applicazione del Magento

```bash
bin/magento setup:rollback [-c|--code-file CODE-FILE] [-m|--media-file MEDIA-FILE] [-d|--db-file DB-FILE] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--code-file`, `-c`



Nome del file di backup del codice in var/backup
- Richiede un valore



### `--media-file`, `-m`



Nome base del file di backup multimediale in var/backup
- Richiede un valore



### `--db-file`, `-d`



Nome base del file di backup del db in var/backup
- Richiede un valore


### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `setup:static-content:deploy`

Distribuisce file di visualizzazione statici

```bash
bin/magento setup:static-content:deploy [-f|--force] [-s|--strategy [STRATEGY]] [-a|--area [AREA]] [--exclude-area [EXCLUDE-AREA]] [-t|--theme [THEME]] [--exclude-theme [EXCLUDE-THEME]] [-l|--language [LANGUAGE]] [--exclude-language [EXCLUDE-LANGUAGE]] [-j|--jobs [JOBS]] [--max-execution-time [MAX-EXECUTION-TIME]] [--symlink-locale] [--content-version CONTENT-VERSION] [--refresh-content-version-only] [--no-javascript] [--no-js-bundle] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [--] [<languages>...]
```

<!-- app.name --> <!-- command.usage -->

### `languages`

Elenco separato da spazio dei codici di lingua ISO-639 per i quali si desidera generare file di visualizzazione statici.

- Predefinito: `[]`

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->




### `--force`, `-f`



Distribuisci i file in qualsiasi modalità.
- Predefinito: `false`
- Non accetta un valore



### `--strategy`, `-s`



Distribuisci i file utilizzando la strategia specificata.
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



Genera file di visualizzazione statici solo per i temi specificati.
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

Crea collegamenti simbolici per i file di tali impostazioni internazionali, che vengono passati per la distribuzione ma non dispongono di personalizzazioni.
- Predefinito: `false`
- Non accetta un valore


### `--content-version`

La versione personalizzata del contenuto statico può essere utilizzata se si esegue la distribuzione su più nodi per garantire che la versione del contenuto statico sia identica e che il caching funzioni correttamente.
- Richiede un valore


### `--refresh-content-version-only`

L’aggiornamento della versione solo del contenuto statico può essere utilizzato per aggiornare il contenuto statico nella cache del browser e nella cache CDN.
- Predefinito: `false`
- Non accetta un valore


### `--no-javascript`

Non distribuire file JavaScript.
- Predefinito: `false`
- Non accetta un valore


### `--no-js-bundle`

Non distribuire file di bundle JavaScript.
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

Non distribuire i file di font.
- Predefinito: `false`
- Non accetta un valore


### `--no-html`

Non distribuire file HTML.
- Predefinito: `false`
- Non accetta un valore


### `--no-misc`

Non distribuire file di altri tipi (.md, .jbf, .csv, ecc.).
- Predefinito: `false`
- Non accetta un valore


### `--no-html-minify`

Non minimizzare i file HTML.
- Predefinito: `false`
- Non accetta un valore


### `--no-parent`

Non compilare i temi principali. Supportato solo nelle strategie rapide e standard.
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `setup:store-config:set`

Installa la configurazione dell&#39;archivio. Obsoleto a partire dalla versione 2.2.0. Utilizza invece config:set

```bash
bin/magento setup:store-config:set [--base-url BASE-URL] [--language LANGUAGE] [--timezone TIMEZONE] [--currency CURRENCY] [--use-rewrites USE-REWRITES] [--use-secure USE-SECURE] [--base-url-secure BASE-URL-SECURE] [--use-secure-admin USE-SECURE-ADMIN] [--admin-use-security-key ADMIN-USE-SECURITY-KEY] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--base-url`

URL in cui lo store deve essere disponibile. Obsoleto, usa config:set con percorso web/unsecure/base_url
- Richiede un valore


### `--language`

Codice lingua predefinito. Obsoleto, usa config:set con percorso generale/locale/codice
- Richiede un valore


### `--timezone`

Codice del fuso orario predefinito. Obsoleto, usa config:set con percorso generale/locale/fuso orario
- Richiede un valore


### `--currency`

Codice valuta predefinito. Obsoleto, usa config:set con percorso currency/options/base, currency/options/default e currency/options/allow
- Richiede un valore


### `--use-rewrites`

Utilizza le riscritture. Obsoleto, usa config:set con il percorso web/seo/use_rewrites
- Richiede un valore


### `--use-secure`

Utilizzare URL sicuri. Abilita questa opzione solo se SSL è disponibile. Obsoleto, usa config:set con il percorso web/secure/use_in_frontend
- Richiede un valore


### `--base-url-secure`

URL di base per la connessione SSL. Obsoleto, usa config:set con percorso web/secure/base_url
- Richiede un valore


### `--use-secure-admin`

Esegui l&#39;interfaccia di amministrazione con SSL. Obsoleto, usa config:set con il percorso web/secure/use_in_adminhtml
- Richiede un valore


### `--admin-use-security-key`

Se utilizzare una funzione &quot;chiave di sicurezza&quot; negli URL e nei moduli dell’amministratore di Magento. Obsoleto, usa config:set con percorso admin/security/use_form_key
- Richiede un valore


### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `setup:uninstall`

Disinstalla l&#39;applicazione di Magento

```bash
bin/magento setup:uninstall [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `setup:upgrade`

Aggiorna l&#39;applicazione di Magento, i dati del database e lo schema

```bash
bin/magento setup:upgrade [--keep-generated] [--convert-old-scripts [CONVERT-OLD-SCRIPTS]] [--safe-mode [SAFE-MODE]] [--data-restore [DATA-RESTORE]] [--dry-run [DRY-RUN]] [--magento-init-params MAGENTO-INIT-PARAMS]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--keep-generated`

Impedisce l’eliminazione dei file generati. Scoraggiamo l’utilizzo di questa opzione tranne durante l’implementazione in produzione. Per ulteriori informazioni, consulta l’integratore di sistema o l’amministratore.
- Predefinito: `false`
- Non accetta un valore


### `--convert-old-scripts`

Consente di convertire i vecchi script (InstallSchema, UpgradeSchema) in formato db_schema.xml
- Predefinito: `false`
- Accetta un valore


### `--safe-mode`

Installazione sicura del Magento con immagini in operazioni distruttive, come la rimozione delle colonne
- Accetta un valore


### `--data-restore`

Ripristinare i dati rimossi dalle immagini
- Accetta un valore


### `--dry-run`

L&#39;installazione del Magento verrà eseguita in modalità a secco
- Predefinito: `false`
- Accetta un valore


### `--magento-init-params`

Aggiungi a qualsiasi comando per personalizzare i parametri di inizializzazione del Magento Ad esempio: &quot;MAGE_MODE=developer&amp;MAGE_DIRS[base][path]=/var/www/example.com&amp;MAGE_DIRS[cache][path]=/var/tmp/cache&quot;
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `store:list`

Visualizza l&#39;elenco degli archivi

```bash
bin/magento store:list
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `store:website:list`

Visualizza l’elenco dei siti web

```bash
bin/magento store:website:list
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->




### `--help`, `-h`



Visualizza il messaggio della guida
- Predefinito: `false`
- Non accetta un valore



### `--quiet`, `-q`



Non trasmettere messaggi
- Predefinito: `false`
- Non accetta un valore



### `--verbose`, `-v|-vv|-vvv`



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `theme:uninstall`

Disinstalla il tema

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] [--] <theme>...
```

<!-- app.name --> <!-- command.usage -->

### `theme`

Percorso del tema. Il percorso del tema deve essere specificato come percorso completo che è area/fornitore/nome. Ad esempio, frontend/Magento/blank

- Predefinito: `[]`
- Obbligatorio

- Array <!-- argument --> <!-- arguments --> <!-- arguments.size -->



### `--backup-code`

Esegui backup del codice (esclusi i file temporanei)
- Predefinito: `false`
- Non accetta un valore



### `--clear-static-content`, `-c`



Cancella i file di visualizzazione statica generati.
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size -->

## `varnish:vcl:generate`

Genera VCL vernico ed echeggia alla riga di comando

```bash
bin/magento varnish:vcl:generate [--access-list ACCESS-LIST] [--backend-host BACKEND-HOST] [--backend-port BACKEND-PORT] [--export-version EXPORT-VERSION] [--grace-period GRACE-PERIOD] [--output-file OUTPUT-FILE]
```

<!-- app.name --> <!-- command.usage --> <!-- arguments.size -->



### `--access-list`

Elenco di accesso IP in grado di eliminare Varnish
- Predefinito: `localhost`
- Richiede un valore


### `--backend-host`

Host del backend web
- Predefinito: `localhost`
- Richiede un valore


### `--backend-port`

Porta del backend web
- Predefinito: `8080`
- Richiede un valore


### `--export-version`

La versione del file Varnish
- Predefinito: `4`
- Richiede un valore


### `--grace-period`

Periodo di tolleranza in secondi
- Predefinito: `300`
- Richiede un valore


### `--output-file`

Percorso del file per scrivere vcl
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



Aumenta la verbosità dei messaggi: 1 per l&#39;output normale, 2 per l&#39;output più dettagliato e 3 per il debug
- Predefinito: `false`
- Non accetta un valore



### `--version`, `-V`



Visualizza questa versione dell&#39;applicazione
- Predefinito: `false`
- Non accetta un valore


### `--ansi`

Forza uscita ANSI
- Predefinito: `false`
- Non accetta un valore


### `--no-ansi`

Disabilita output ANSI
- Predefinito: `false`
- Non accetta un valore



### `--no-interaction`, `-n`



Non fare domande interattive
- Predefinito: `false`
- Non accetta un valore <!-- options --> <!-- options.size --> <!-- commands --> <!-- file -->