---
title: Configurazione del sistema di build
description: Scopri come distribuire Commerce in un sistema di build.
feature: Configuration, Build, Deploy
exl-id: f6daf5c6-6d12-46b0-b775-76791bacea53
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# Configurazione del sistema di build

Puoi avere un sistema di build che soddisfa i seguenti requisiti:

- Tutto il codice Commerce è soggetto al controllo del codice sorgente nello stesso archivio dei sistemi di sviluppo e produzione
- Assicurati che tutte le seguenti operazioni siano _incluso_ nel controllo del codice sorgente:

   - `app/etc/config.php`
   - `generated` directory (e sottodirectory)
   - `pub/media` directory
   - `pub/media/wysiwyg` directory (e sottodirectory)
   - `pub/static` directory (e sottodirectory)

- Deve essere installata una versione PHP compatibile
- Deve avere Compositore installato
- Ha la proprietà del file system e le autorizzazioni impostate come descritto in [Prerequisito per i sistemi di sviluppo, generazione e produzione](../deployment/technical-details.md).
- Per installare il sistema di build non è necessario Commerce, ma è necessario che il codice sia disponibile.

>[!WARNING]
>
>La connessione al database non è necessaria se è già contenuta in `config.php`; vedi [Esportare la configurazione](../cli/export-configuration.md). In caso contrario, è necessaria la connessione al database.

>[!INFO]
>
>Il computer di build può trovarsi su un proprio host o sullo stesso host di un sistema Commerce installato.

## Configurare il computer di compilazione

Nelle sezioni seguenti viene illustrato come configurare il computer di compilazione.

### Installa Compositore

Innanzitutto, verifica se Composer è già installato:

Al prompt dei comandi immettere uno dei comandi seguenti:

- `composer --help`
- `composer list --help`

Se viene visualizzata la Guida del comando, Composer è già installato.

Se viene visualizzato un errore, attieniti alla procedura seguente per installare Composer.

Per installare Composer:

1. Cambia in o crea una directory vuota sul server Commerce.

1. Immettete i seguenti comandi:

   ```bash
   curl -sS https://getcomposer.org/installer | php
   ```

   ```bash
   mv composer.phar /usr/local/bin/composer
   ```

Per ulteriori opzioni di installazione, vedere [Documentazione sull’installazione del compositore][composer].

### Installare PHP

Installare PHP su [CentOS] o [Ubuntu].

### Configurare il sistema di build

Per impostare il sistema di build:

1. Accedi al sistema di build come proprietario del file system o passa a tale proprietario.
1. Recupera il codice Commerce dal controllo del codice sorgente.

   Se utilizzi Git, utilizza il seguente comando:

   ```bash
   git clone [-b <branch name>] <repository URL>
   ```

1. Passa alla directory principale di Commerce e immetti:

   ```bash
   composer install
   ```

1. Attendere l&#39;aggiornamento delle dipendenze.
1. Imposta proprietà:

   ```bash
   chown -R <Commerce file system owner name>:<web server username> .
   ```

   Ad esempio:

   ```bash
   chown -R commerce-username:apache .
   ```

1. Se usa Git, apra `.gitignore` in un editor di testo.
1. Iniziare ciascuna delle righe seguenti con un `#` per aggiungerne un commento:

   ```conf
   # app/etc/config.php
   # pub/media/*
   # generated/*
   # pub/media/*.*
   # pub/media/wysiwyg/*
   # pub/static/*
   ```

1. Salva le modifiche apportate a `.gitignore` ed esci dall’editor di testo.
1. Se utilizzi Git, utilizza i seguenti comandi per confermare la modifica:

   ```bash
   git add .gitignore && git commit -m "Modify .gitignore for build and production"
   ```

   Consulta la [`.gitignore` riferimento](../reference/config-reference-gitignore.md) per ulteriori informazioni.

1. Il sistema di build deve utilizzare [modalità predefinita](../bootstrap/application-modes.md#default-mode) o [modalità sviluppatore](../bootstrap/application-modes.md#developer-mode):

   ```bash
   bin/magento deploy:mode:set <mode>
   ```

   `<mode>` è obbligatorio. Può essere `default` o `developer`.

<!-- Link Definitions -->

[CentOS]: https://wiki.centos.org/HowTos/php7
[composer]: https://getcomposer.org/download/
[Ubuntu]: https://help.ubuntu.com/lts/serverguide/php.html
