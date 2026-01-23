---
title: Configurazione del sistema di build
description: Scopri come distribuire Commerce in un sistema di build.
feature: Configuration, Build, Deploy
exl-id: f6daf5c6-6d12-46b0-b775-76791bacea53
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# Configurazione del sistema di build

Puoi avere un sistema di build che soddisfa i seguenti requisiti:

- Tutto il codice Commerce è controllato dal codice sorgente nello stesso archivio dei sistemi di sviluppo e produzione
- Assicurarsi che tutti i seguenti elementi siano _inclusi_ nel controllo del codice sorgente:

   - `app/etc/config.php`
   - Directory `generated` (e sottodirectory)
   - Directory `pub/media`
   - Directory `pub/media/wysiwyg` (e sottodirectory)
   - Directory `pub/static` (e sottodirectory)

- Deve essere installata una versione PHP compatibile
- Deve avere Compositore installato
- Ha la proprietà del file system e le autorizzazioni impostate come descritto in [Prerequisiti per i sistemi di sviluppo, compilazione e produzione](../deployment/technical-details.md).
- Il sistema di build non ha bisogno di Commerce per essere installato, ma il codice deve essere disponibile.

>[!WARNING]
>
>La connessione al database non è necessaria se è già contenuta in `config.php`. Vedere [Esportare la configurazione](../cli/export-configuration.md). In caso contrario, è necessaria la connessione al database.

>[!INFO]
>
>Il computer di compilazione può trovarsi sul proprio host o sullo stesso host di un sistema Commerce installato.

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

Per ulteriori opzioni di installazione, vedere la [documentazione sull&#39;installazione del Compositore](https://getcomposer.org/download/).

### Installare PHP

Installa PHP in [CentOS](https://wiki.centos.org/HowTos/php7) o [Ubuntu](https://help.ubuntu.com/lts/serverguide/php.html).

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

1. Se si utilizza Git, aprire `.gitignore` in un editor di testo.
1. Iniziare ciascuna delle righe seguenti con un carattere `#` per aggiungerle come commento:

   ```conf
   # app/etc/config.php
   # pub/media/*
   # generated/*
   # pub/media/*.*
   # pub/media/wysiwyg/*
   # pub/static/*
   ```

1. Salvare le modifiche apportate a `.gitignore` e uscire dall&#39;editor di testo.
1. Se utilizzi Git, utilizza i seguenti comandi per confermare la modifica:

   ```bash
   git add .gitignore && git commit -m "Modify .gitignore for build and production"
   ```

   Per ulteriori informazioni, vedere il riferimento [`.gitignore`](../reference/config-reference-gitignore.md).

1. Il sistema di compilazione deve utilizzare [modalità predefinita](../bootstrap/application-modes.md#default-mode) o [modalità sviluppatore](../bootstrap/application-modes.md#developer-mode):

   ```bash
   bin/magento deploy:mode:set <mode>
   ```

   `<mode>` è obbligatorio. Può essere `default` o `developer`.

