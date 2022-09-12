---
title: Disinstallare i temi
description: Per disinstallare un tema Adobe Commerce o Magenti Open Source, effettua le seguenti operazioni.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---


# Disinstallare i temi

Prima di utilizzare questo comando, è necessario conoscere il percorso relativo del tema. I temi si trovano in una sottodirectory di `<magento_root>/app/design/<area name>`. È necessario specificare il percorso del tema che inizia con l&#39;area, che è `frontend` (per temi di vetrina) o `adminhtml` (per [Amministratore](https://glossary.magento.com/magento-admin) temi).

Ad esempio, il percorso della Luma [tema](https://glossary.magento.com/theme) fornito con Adobe Commerce e Magento Open Source è `frontend/Magento/luma`.

Per ulteriori informazioni sui temi, vedi [struttura a tema](https://developer.adobe.com/commerce/frontend-core/guide/themes/structure/).

## Panoramica della disinstallazione dei temi

Questa sezione illustra come disinstallare uno o più temi, includendo facoltativamente il codice dei temi dal file system. È possibile creare prima i backup in modo da ripristinare i dati in un secondo momento.

Disinstalla questo comando *only* temi specificati in `composer.json`; in altre parole, i temi forniti come [Compositore](https://glossary.magento.com/composer) pacchetti. Se il tema non è un pacchetto Compositore, devi disinstallarlo manualmente tramite:

* Aggiornamento della `parent` informazioni nodo in `theme.xml` per rimuovere i riferimenti al tema.
* Rimozione del codice del tema dal file system in corso.

   [Ulteriori informazioni sull’ereditarietà di un tema](https://developer.adobe.com/commerce/frontend-core/guide/themes/inheritance/).

## Disinstallare i temi

Utilizzo comando:

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] {theme path} ... {theme path}
```

Dove

* `{theme path}` è il percorso relativo del tema, a partire dal nome dell’area. Ad esempio, il percorso del tema vuoto fornito con Adobe Commerce e Magenti Open Source è `frontend/Magento/blank`.
* `--backup-code` esegue il backup della base di codice, come illustrato nei paragrafi seguenti.
* `--clear-static-content` pulizie generate [file di visualizzazione statici](../../configuration/cli/static-view-file-deployment.md), necessaria per la corretta visualizzazione dei file di visualizzazione statica.

Il comando esegue le seguenti attività:

1. verifica l&#39;esistenza dei percorsi del tema specificati; in caso contrario, il comando termina.
1. verifica che il tema sia un pacchetto Compositore; in caso contrario, il comando termina.
1. Controlla le dipendenze e interrompe il comando in caso di dipendenze non soddisfatte.

   Per aggirare questo problema, è possibile disinstallare tutti i temi allo stesso tempo o è possibile disinstallare l&#39;a seconda del tema prima.

1. verifica che il tema non sia utilizzato; se viene utilizzato, il comando termina.
1. verifica che il tema non sia la base del tema virtuale; se è la base di un tema virtuale, il comando termina.
1. Posiziona il negozio in modalità manutenzione.
1. Se `--backup-code` viene specificato, esegui il backup della base di codice, escludendo `pub/static`, `pub/media`e `var` directory.

   Il nome del file di backup è `var/backups/<timestamp>_filesystem.tgz`

   È possibile ripristinare i backup in qualsiasi momento utilizzando [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) comando.

1. Rimuove i temi dal `theme` tabella del database.
1. Rimuovi i temi dalla base di codice utilizzando `composer remove`.
1. Pulisce il [cache](https://glossary.magento.com/cache).
1. Cancella le classi generate
1. Se `--clear-static-content` è specificato, pulisce [file di visualizzazione statica generati](../../configuration/cli/static-view-file-deployment.md).

Ad esempio, se tenti di disinstallare un tema da cui dipende un altro tema, viene visualizzato il seguente messaggio:

```terminal
Cannot uninstall frontend/ExampleCorp/SampleModuleTheme because the following package(s) depend on it:
        ExampleCorp/sample-module-theme-depend
```

Un&#39;alternativa è disinstallare entrambi i temi contemporaneamente al seguente backup del codebase:

```bash
bin/magento theme:uninstall frontend/ExampleCorp/SampleModuleTheme frontend/ExampleCorp/SampleModuleThemeDepend --backup-code
```

Messaggi simili alla visualizzazione seguente:

```terminal
Code backup is starting...
Code backup filename: 1435261098_filesystem_code.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_code.tgz
[SUCCESS]: Code backup completed successfully.Removing frontend/ExampleCorp/SampleModuleTheme, frontend/ExampleCorp/SampleModuleThemeDepend from database
Loading composer repositories with package information
Updating dependencies (including require-dev)
Removing frontend/ExampleCorp/SampleModuleTheme, frontend/ExampleCorp/SampleModuleThemeDepend from Magento codebase
  - Removing ExampleCorp/sample-module-theme-depend (dev-master)
Removing ExampleCorp/SampleThemeDepend
  - Removing ExampleCorp/sample-module-theme (dev-master)
Removing ExampleCorp/SampleTheme
Writing lock file
Generating autoload files
Cache cleared successfully.
Alert: Generated static view files were not cleared. You can clear them using the --clear-static-content option.
Failure to clear static view files might cause display issues in the Admin and storefront.
Disabling maintenance mode
```

>[!NOTE]
>
>Per disinstallare un [Amministratore](https://glossary.magento.com/admin) tema, devi anche rimuoverlo dal componente [iniezione di dipendenza](https://glossary.magento.com/dependency-injection) configurazione, `<component root directory>/etc/di.xml`.
