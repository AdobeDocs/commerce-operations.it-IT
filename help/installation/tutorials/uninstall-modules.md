---
title: Disinstallare i moduli
description: Per disinstallare un modulo Adobe Commerce o Magenti Open Source, effettua le seguenti operazioni.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '741'
ht-degree: 0%

---


# Disinstallare i moduli

Questa sezione illustra come disinstallare uno o più moduli. Durante la disinstallazione, è possibile rimuovere facoltativamente il codice, lo schema del database e i dati del database dei moduli. È possibile creare prima i backup in modo da poter recuperare i dati in un secondo momento.

È necessario disinstallare un modulo solo se si è certi di non utilizzarlo. Invece di disinstallare un modulo, puoi disattivarlo come descritto in [Attivare o disattivare i moduli](manage-modules.md).

>[!NOTE]
>
>Questo comando controlla che solo le dipendenze dichiarate nel `composer.json` file. Se disinstalla un modulo _not_ definito in `composer.json` file, questo comando disinstalla il modulo senza controllare le dipendenze. Questo comando _not_, tuttavia, rimuovi il codice del modulo dal file system. È necessario utilizzare gli strumenti del file system per rimuovere il codice del modulo (ad esempio, `rm -rf <path to module>`). In alternativa, puoi [disable](manage-modules.md) moduli non compositori.

Utilizzo comando:

```bash
bin/magento module:uninstall [--backup-code] [--backup-media] [--backup-db] [-r|--remove-data] [-c|--clear-static-content] \
  {ModuleName} ... {ModuleName}
```

Dove `{ModuleName}` specifica il nome del modulo in `<VendorName>_<ModuleName>` formato. Ad esempio, il nome del modulo Cliente è `Magento_Customer`. Per ottenere un elenco dei nomi dei moduli, immettere `magento module:status`

Il comando di disinstallazione del modulo esegue le seguenti attività:

1. Verifica che i moduli specificati siano presenti nella base di codice e siano pacchetti installati da Composer.

   Questo comando funziona _only_ con moduli definiti come pacchetti Composer.

1. Controlla le dipendenze con altri moduli e termina il comando se sono presenti dipendenze non soddisfatte.

   Per risolvere questo problema, è possibile disinstallare tutti i moduli contemporaneamente oppure disinstallare prima i moduli dipendenti.

1. Richiede conferma per procedere.
1. Posiziona il negozio in modalità manutenzione.
1. Elabora le seguenti opzioni di comando.

   | Opzione | Significato | Nome e posizione del file di backup |
   | ---------------- | -------------------------------------------------------------------------------- | -------------------------------------------- |
   | `--backup-code` | Backup del file system (escluso `var` e `pub/static` directory). | `var/backups/<timestamp>_filesystem.tgz` |
   | `--backup-media` | Esegue il backup della directory pub/media. | `var/backups/<timestamp>_filesystem_media.tgz` |
   | `--backup-db` | Esegue il backup del database. | `var/backups/<timestamp>_db.gz` |

1. Se `--remove-data` viene specificato, rimuovi lo schema di database e i dati definiti nel modulo `Uninstall` classi.

   Per ogni modulo specificato da disinstallare, richiama il `uninstall` metodo `Uninstall` classe. Questa classe deve ereditare da [Magento\Framework\Setup\UninstallInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/UninstallInterface.php).

1. Rimuove i moduli specificati dalla `setup_module` tabella del database.
1. Rimuove i moduli specificati dall’elenco dei moduli nel [configurazione della distribuzione](../../configuration/reference/deployment-files.md).
1. Rimuove il codice dalla codebase utilizzando `composer remove`.

   >[!NOTE]
   >
   >Disinstallazione di un modulo _sempre_ run `composer remove`. La `--remove-data` rimuove i dati del database e lo schema definiti dal modulo `Uninstall` classe.

1. Elimina la cache.
1. Aggiornamenti delle classi generate.
1. Se `--clear-static-content` è specificato, pulisce [file di visualizzazione statica generati](../../configuration/cli/static-view-file-deployment.md).
1. Elimina il negozio dalla modalità di manutenzione.

Ad esempio, se si tenta di disinstallare un modulo da cui dipende un altro modulo, viene visualizzato il seguente messaggio:

```terminal
magento module:uninstall Magento_SampleMinimal
    Cannot uninstall module 'Magento_SampleMinimal' because the following module(s) depend on it:
        Magento_SampleModifyContent
```

Un&#39;alternativa è disinstallare entrambi i moduli dopo il backup del file system del modulo, `pub/media` file e tabelle di database, ma _not_ rimozione dello schema o dei dati del database del modulo:

```bash
bin/magento module:uninstall Magento_SampleMinimal Magento_SampleModifyContent --backup-code --backup-media --backup-db
```

Messaggi simili alla visualizzazione seguente:

```terminal
You are about to remove code and/or database tables. Are you sure?[y/N]y
Enabling maintenance mode
Code backup is starting...
Code backup filename: 1435261098_filesystem_code.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_code.tgz
[SUCCESS]: Code backup completed successfully.
Media backup is starting...
Media backup filename: 1435261098_filesystem_media.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Media backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_media.tgz
[SUCCESS]: Media backup completed successfully.
DB backup is starting...
DB backup filename: 1435261098_db.gz (The archive can be uncompressed with 7-Zip on Windows systems)
DB backup path: /var/www/html/magento2/var/backups/1435261098_db.gz
[SUCCESS]: DB backup completed successfully.
You are about to remove a module(s) that might have database data. Remove the database data manually after uninstalling, if desired.
Removing Magento_SampleMinimal, Magento_SampleModifyContent from module registry in database
Removing Magento_SampleMinimal, Magento_SampleModifyContent from module list in deployment configuration
Removing code from Magento codebase:
Loading composer repositories with package information
Updating dependencies (including require-dev)
  - Removing magento/sample-module-modifycontent (1.0.0)
Removing Magento/SampleModifycontent
  - Removing magento/sample-module-minimal (1.0.0)
Removing Magento/SampleMinimal
Writing lock file
Generating autoload files
Cache cleared successfully.
Generated classes cleared successfully.
Alert: Generated static view files were not cleared. You can clear them using the --clear-static-content option. Failure to clear static view files might cause display issues in the Admin and storefront.
Disabling maintenance mode
```

>[!NOTE]
>
>Gli errori vengono visualizzati se si tenta di disinstallare un modulo con una dipendenza da un altro modulo. In tal caso, non è possibile disinstallare un modulo; devi disinstallare entrambi.

## Ripristino del file system, del database o dei file multimediali

Per ripristinare il codebase allo stato in cui è stato eseguito il backup, utilizzare il comando seguente:

```bash
bin/magento setup:rollback [-c|--code-file="<filename>"] [-m|--media-file="<filename>"] [-d|--db-file="<filename>"]
```

Dove `<filename>` è il nome del file di backup nel `<app_root>/var/backups` directory. Per visualizzare un elenco dei file di backup, immettere `magento info:backups:list`

>[!WARNING]
>
>Questo comando elimina i file specificati o il database prima di ripristinarli. Ad esempio, il `--media-file` elimina le risorse multimediali nella `pub/media` prima del ripristino dal file di rollback specificato. Assicurarsi di non aver modificato il file system o il database che si desidera mantenere prima di utilizzare questo comando.

>[!NOTE]
>
>Per visualizzare un elenco dei file di backup disponibili, immettere `magento info:backups:list`

Questo comando esegue le seguenti attività:

1. Posiziona il negozio in modalità manutenzione.
1. Verifica il nome del file di backup.
1. Se si specifica un file di rollback del codice:

   a) Verifica che le posizioni di destinazione di rollback siano scrivibili (nota che il `pub/static` e `var` le cartelle vengono ignorate).

   b) Elimina tutti i file e le directory nella directory di installazione dell&#39;applicazione.

   c. Estrae il file di archivio nelle posizioni di destinazione.

1. Se si specifica un file di rollback del database:

   a) Rilascia l’intero database.

   b) Ripristina il database utilizzando il backup del database.

1. Se si specifica un file di rollback dei file multimediali:

   a) Verifica che le posizioni di destinazione di rollback siano scrivibili.

   b) Elimina tutti i file e le directory in `pub/media`

   c. Estrae il file di archivio nelle posizioni di destinazione.

1. Elimina il negozio dalla modalità di manutenzione.

Ad esempio, per ripristinare un backup del codice (ovvero del file system), immettere i seguenti comandi nell&#39;ordine mostrato:

* Visualizza un elenco di backup:

   ```bash
   magento info:backups:list
   ```

* Ripristinare un backup di file denominato `1433876616_filesystem.tgz`:

   ```bash
   magento setup:rollback --code-file="1433876616_filesystem.tgz"
   ```

   Messaggi simili alla visualizzazione seguente:

   ```terminal
   Enabling maintenance mode
   Code rollback is starting ...
   Code rollback filename: 1433876616_filesystem.tgz
   Code rollback file path: /var/www/html/magento2/var/backups/1433876616_filesystem.tgz
   [SUCCESS]: Code rollback has completed successfully.
   Disabling maintenance mode
   ```

>[!NOTE]
>
>Per eseguire la `magento` di nuovo comando senza modificare le directory, potrebbe essere necessario immettere `cd pwd`.
