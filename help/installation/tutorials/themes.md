---
title: Disinstalla temi
description: Segui questi passaggi per disinstallare un tema Adobe Commerce.
feature: Install, Themes
exl-id: 73150e8c-2d83-4479-b96b-75f41fd9c842
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# Disinstalla temi

Prima di utilizzare questo comando, è necessario conoscere il percorso relativo del tema. I temi si trovano in una sottodirectory di `<magento_root>/app/design/<area name>`. È necessario specificare il percorso del tema che inizia con l&#39;area, che è `frontend` (per i temi storefront) o `adminhtml` (per i temi Admin).

Il percorso del tema Luma fornito con Adobe Commerce, ad esempio, è `frontend/Magento/luma`.

Per ulteriori informazioni sui temi, vedere [struttura tema](https://developer.adobe.com/commerce/frontend-core/guide/themes/structure/).

## Panoramica sulla disinstallazione dei temi

Questa sezione illustra come disinstallare uno o più temi, includendo facoltativamente il codice dei temi dal file system. È possibile creare prima i backup in modo da poter ripristinare i dati in un secondo momento.

Questo comando disinstalla *solo* temi specificati in `composer.json`; in altre parole, temi forniti come pacchetti Composer. Se il tema non è un pacchetto Compositore, è necessario disinstallarlo manualmente:

* Aggiornamento delle informazioni sul nodo `parent` in `theme.xml` per rimuovere i riferimenti al tema.
* Rimozione del codice del tema dal file system.

  [Ulteriori informazioni sull&#39;ereditarietà del tema](https://developer.adobe.com/commerce/frontend-core/guide/themes/inheritance/).

## Disinstalla temi

Utilizzo comando:

```bash
bin/magento theme:uninstall [--backup-code] [-c|--clear-static-content] {theme path} ... {theme path}
```

Dove

* `{theme path}` è il percorso relativo del tema, a partire dal nome dell&#39;area. Il percorso del tema vuoto fornito con Adobe Commerce, ad esempio, è `frontend/Magento/blank`.
* `--backup-code` esegue il backup della base di codice come descritto nei paragrafi seguenti.
* `--clear-static-content` pulisce i [file di visualizzazione statica](../../configuration/cli/static-view-file-deployment.md) generati, necessari per la corretta visualizzazione dei file di visualizzazione statica.

Il comando esegue le seguenti operazioni:

1. Verifica l&#39;esistenza dei percorsi del tema specificati; in caso contrario, il comando termina.
1. Verifica che il tema sia un pacchetto Compositore; in caso contrario, il comando termina.
1. Controlla le dipendenze e termina il comando se sono presenti dipendenze non soddisfatte.

   Per ovviare a questo problema, puoi disinstallare tutti i temi contemporaneamente oppure puoi disinstallare prima i a seconda del tema.

1. Verifica che il tema non sia utilizzato; se è utilizzato, il comando termina.
1. Verifica che il tema non sia la base del tema virtuale; se è la base di un tema virtuale, il comando termina.
1. Mette l&#39;archivio in modalità di manutenzione.
1. Se si specifica `--backup-code`, eseguire il backup della codebase, escludendo le directory `pub/static`, `pub/media` e `var`.

   Il nome del file di backup è `var/backups/<timestamp>_filesystem.tgz`

   È possibile ripristinare i backup in qualsiasi momento utilizzando il comando [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files).

1. Rimuove i temi dalla tabella del database `theme`.
1. Rimuovere i temi dalla base di codice utilizzando `composer remove`.
1. Pulisce la cache.
1. Pulisce le classi generate
1. Se si specifica `--clear-static-content`, pulisce [file di visualizzazione statica generati](../../configuration/cli/static-view-file-deployment.md).

Ad esempio, se tenti di disinstallare un tema da cui dipende un altro tema, viene visualizzato il seguente messaggio:

```
Cannot uninstall frontend/ExampleCorp/SampleModuleTheme because the following package(s) depend on it:
        ExampleCorp/sample-module-theme-depend
```

Un&#39;alternativa è quella di disinstallare entrambi i temi contemporaneamente come segue backup della base di codice:

```bash
bin/magento theme:uninstall frontend/ExampleCorp/SampleModuleTheme frontend/ExampleCorp/SampleModuleThemeDepend --backup-code
```

Messaggi simili alla seguente visualizzazione:

```
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
>Per disinstallare un tema amministratore, è necessario rimuoverlo anche dalla configurazione dell&#39;iniezione di dipendenza del componente, `<component root directory>/etc/di.xml`.
