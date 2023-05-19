---
title: Disinstalla moduli
description: Per disinstallare un modulo Adobe Commerce o Magenti Open Source, segui la procedura riportata di seguito.
exl-id: 66879ef5-47c7-4b61-8c7e-78b60441980a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '741'
ht-degree: 0%

---

# Disinstalla moduli

Questa sezione illustra come disinstallare uno o più moduli. Durante la disinstallazione, è possibile rimuovere facoltativamente il codice dei moduli, lo schema del database e i dati del database. È possibile creare prima i backup in modo da poter recuperare i dati in un secondo momento.

È consigliabile disinstallare un modulo solo se si è certi di non utilizzarlo. Invece di disinstallare un modulo, puoi disattivarlo come descritto in [Abilitare o disabilitare i moduli](manage-modules.md).

>[!NOTE]
>
>Questo comando verifica che solo le dipendenze dichiarate nel `composer.json` file. Se disinstalli un modulo che è _non_ definito nel `composer.json` file, questo comando disinstalla il modulo senza verificare le dipendenze. Questo comando esegue _non_ Tuttavia, rimuovi il codice del modulo dal file system. Per rimuovere il codice del modulo è necessario utilizzare gli strumenti del file system (ad esempio, `rm -rf <path to module>`). In alternativa, puoi: [disable](manage-modules.md) moduli non di composizione.

Utilizzo comando:

```bash
bin/magento module:uninstall [--backup-code] [--backup-media] [--backup-db] [-r|--remove-data] [-c|--clear-static-content] \
  {ModuleName} ... {ModuleName}
```

Dove `{ModuleName}` specifica il nome del modulo in `<VendorName>_<ModuleName>` formato. Ad esempio, il nome del modulo Cliente è `Magento_Customer`. Per ottenere un elenco dei nomi dei moduli, immetti `magento module:status`

Il comando di disinstallazione del modulo esegue le operazioni seguenti:

1. Verifica che i moduli specificati siano presenti nella base di codice e siano pacchetti installati da Composer.

   Questo comando funziona _solo_ con moduli definiti come pacchetti Compositore.

1. Controlla le dipendenze con altri moduli e termina il comando se sono presenti dipendenze non soddisfatte.

   Per ovviare a questo problema, è possibile disinstallare tutti i moduli contemporaneamente oppure disinstallare prima i moduli dipendenti.

1. Richiede conferma per continuare.
1. Mette l&#39;archivio in modalità di manutenzione.
1. Elabora le seguenti opzioni di comando.

   | Opzione | Significato | Nome e percorso del file di backup |
   | ---------------- | -------------------------------------------------------------------------------- | -------------------------------------------- |
   | `--backup-code` | Backup del file system (escluso `var` e `pub/static` directory). | `var/backups/<timestamp>_filesystem.tgz` |
   | `--backup-media` | Esegue il backup della directory pub/media. | `var/backups/<timestamp>_filesystem_media.tgz` |
   | `--backup-db` | Backup del database. | `var/backups/<timestamp>_db.gz` |

1. Se `--remove-data` , rimuovi lo schema del database e i dati definiti nel file `Uninstall` classi.

   Per ogni modulo specificato da disinstallare, richiama `uninstall` metodo nel suo `Uninstall` classe. Questa classe deve ereditare da [Magento\Framework\Setup\UninstallInterface](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Setup/UninstallInterface.php).

1. Rimuove i moduli specificati dal `setup_module` tabella di database.
1. Rimuove i moduli specificati dall&#39;elenco dei moduli nel [configurazione della distribuzione](../../configuration/reference/deployment-files.md).
1. Rimuove il codice dal codebase utilizzando `composer remove`.

   >[!NOTE]
   >
   >Disinstallazione di un modulo _sempre_ esecuzioni `composer remove`. Il `--remove-data` rimuove i dati del database e lo schema definiti dal modulo `Uninstall` classe.

1. Pulisce la cache.
1. Aggiorna le classi generate.
1. Se `--clear-static-content` è specificato, pulisce [file di visualizzazione statica generati](../../configuration/cli/static-view-file-deployment.md).
1. Porta il negozio fuori dalla modalità di manutenzione.

Ad esempio, se tenti di disinstallare un modulo da cui dipende un altro modulo, viene visualizzato il seguente messaggio:

```terminal
magento module:uninstall Magento_SampleMinimal
    Cannot uninstall module 'Magento_SampleMinimal' because the following module(s) depend on it:
        Magento_SampleModifyContent
```

Un&#39;alternativa consiste nel disinstallare entrambi i moduli dopo aver eseguito il backup del file system dei moduli, `pub/media` file e tabelle di database, ma _non_ rimozione dello schema di database o dei dati del modulo:

```bash
bin/magento module:uninstall Magento_SampleMinimal Magento_SampleModifyContent --backup-code --backup-media --backup-db
```

Messaggi simili alla seguente visualizzazione:

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
>Se si tenta di disinstallare un modulo con una dipendenza da un altro modulo, vengono visualizzati degli errori. In tal caso, non è possibile disinstallare un modulo, ma è necessario disinstallare entrambi.

## Eseguire il rollback dei file system, database o file multimediali

Per ripristinare la base di codice nello stato in cui è stato eseguito il backup, utilizzare il comando seguente:

```bash
bin/magento setup:rollback [-c|--code-file="<filename>"] [-m|--media-file="<filename>"] [-d|--db-file="<filename>"]
```

Dove `<filename>` è il nome del file di backup in `<app_root>/var/backups` directory. Per visualizzare un elenco di file di backup, immettere: `magento info:backups:list`

>[!WARNING]
>
>Questo comando elimina i file specificati o il database prima di ripristinarli. Ad esempio, il `--media-file` elimina le risorse multimediali in `pub/media` prima del ripristino dal file di rollback specificato. Prima di utilizzare questo comando, assicurarsi di non aver modificato il file system o il database che si desidera mantenere.

>[!NOTE]
>
>Per visualizzare un elenco dei file di backup disponibili, immettere: `magento info:backups:list`

Questo comando esegue le seguenti attività:

1. Mette l&#39;archivio in modalità di manutenzione.
1. Verifica il nome del file di backup.
1. Se si specifica un file di rollback del codice:

   a. Verifica che le posizioni di destinazione del rollback siano scrivibili (si noti che `pub/static` e `var` cartelle ignorate).

   b. Elimina tutti i file e le directory nella directory di installazione dell&#39;applicazione.

   c. Estrae il file di archivio nei percorsi di destinazione.

1. Se si specifica un file di rollback del database:

   a. Elimina l’intero database.

   b. Ripristina il database utilizzando il backup del database.

1. Se si specifica un file di rollback multimediale:

   a. Verifica che le posizioni di destinazione del rollback siano scrivibili.

   b. Elimina tutti i file e le directory in `pub/media`

   c. Estrae il file di archivio nei percorsi di destinazione.

1. Porta il negozio fuori dalla modalità di manutenzione.

Ad esempio, per ripristinare un backup del codice (ovvero del file system), immettere i seguenti comandi nell&#39;ordine indicato:

* Visualizza un elenco di backup:

   ```bash
   magento info:backups:list
   ```

* Ripristinare un backup di file denominato `1433876616_filesystem.tgz`:

   ```bash
   magento setup:rollback --code-file="1433876616_filesystem.tgz"
   ```

   Messaggi simili alla seguente visualizzazione:

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
>Per eseguire `magento` senza modificare le directory, potrebbe essere necessario immettere `cd pwd`.
