---
title: Configurazione del sistema di compilazione
description: Scopri come distribuire Commerce in un sistema di build.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---


# Configurazione del sistema di generazione

Puoi disporre di un sistema di compilazione che soddisfi i seguenti requisiti:

- Tutto il codice Commerce è sotto il controllo del codice sorgente nello stesso archivio dei sistemi di sviluppo e produzione
- Assicurati che tutti i seguenti elementi siano _incluso_ nel controllo della sorgente:

   - `app/etc/config.php`
   - `generated` directory (e sottodirectory)
   - `pub/media` directory
   - `pub/media/wysiwyg` directory (e sottodirectory)
   - `pub/static` directory (e sottodirectory)

- Deve essere installata una versione PHP compatibile
- Deve avere installato Composer
- Possiede la proprietà e le autorizzazioni del file system impostate come descritto in [Prerequisito per i sistemi di sviluppo, generazione e produzione](../deployment/technical-details.md).
- Per installare il sistema di compilazione non è necessario Commerce, ma il codice deve essere disponibile.

>[!WARNING]
>
>La connessione al database non è necessaria se è già contenuta in `config.php`; vedere [Esporta la configurazione](../cli/export-configuration.md). In caso contrario, la connessione al database è obbligatoria.

>[!INFO]
>
>Il computer di compilazione può trovarsi sul proprio host o sullo stesso host di un sistema Commerce installato.

## Configurare il computer di compilazione

Nelle sezioni seguenti viene illustrato come configurare il computer di compilazione.

### Installa Compositore

Per prima cosa, controlla se il Compositore è già installato:

Nel prompt dei comandi immettere uno dei comandi seguenti:

- `composer --help`
- `composer list --help`

Se viene visualizzata la guida del comando, Compositore è già installato.

Se viene visualizzato un errore, utilizza i seguenti passaggi per installare Composer.

Per installare Compositore:

1. Passa a o crea una directory vuota sul server Commerce.

1. Immetti i seguenti comandi:

   ```bash
   curl -sS https://getcomposer.org/installer | php
   ```

   ```bash
   mv composer.phar /usr/local/bin/composer
   ```

Per ulteriori opzioni di installazione, consulta la sezione [Documentazione sull&#39;installazione del compositore][composer].

### Installa PHP

Installa PHP su [CentOS] o [Ubuntu].

### Configurare il sistema di compilazione

Per configurare il sistema di compilazione:

1. Accedi al sistema di compilazione come proprietario del file system o passa a .
1. Recupera il codice Commerce dal controllo del codice sorgente.

   Se utilizzi Git, utilizza il comando seguente:

   ```bash
   git clone [-b <branch name>] <repository URL>
   ```

1. Passa alla directory principale Commerce e immetti:

   ```bash
   composer install
   ```

1. Attendi l&#39;aggiornamento delle dipendenze.
1. Imposta proprietà:

   ```bash
   chown -R <Commerce file system owner name>:<web server username> .
   ```

   Ad esempio:

   ```bash
   chown -R commerce-username:apache .
   ```

1. Se utilizzi Git, apri `.gitignore` in un editor di testo.
1. Avvia ciascuna delle seguenti righe con un `#` carattere per commentarli:

   ```conf
   # app/etc/config.php
   # pub/media/*
   # generated/*
   # pub/media/*.*
   # pub/media/wysiwyg/*
   # pub/static/*
   ```

1. Salva le modifiche in `.gitignore` e esci dall’editor di testo.
1. Se utilizzi Git, utilizza i seguenti comandi per eseguire il commit della modifica:

   ```bash
   git add .gitignore && git commit -m "Modify .gitignore for build and production"
   ```

   Consulta la sezione [`.gitignore` riferimento](../reference/config-reference-gitignore.md) per ulteriori informazioni.

1. Il sistema di compilazione deve utilizzare [modalità predefinita](../bootstrap/application-modes.md#default-mode) o [modalità sviluppatore](../bootstrap/application-modes.md#developer-mode):

   ```bash
   bin/magento deploy:mode:set <mode>
   ```

   `<mode>` è obbligatorio. Può essere `default` o `developer`.

<!-- Link Definitions -->

[CentOS]: https://wiki.centos.org/HowTos/php7
[composer]: https://getcomposer.org/download/
[Ubuntu]: https://help.ubuntu.com/lts/serverguide/php.html
