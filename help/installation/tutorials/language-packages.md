---
title: Disinstalla pacchetti per lingua
description: Per disinstallare un pacchetto lingua di Adobe Commerce, segui la procedura riportata di seguito.
exl-id: 9901aa0b-af1a-4ae9-968f-ac8421060f57
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# Disinstalla pacchetti per lingua

Questa sezione illustra come disinstallare uno o più pacchetti di lingua, includendo facoltativamente il codice dei pacchetti di lingua dal file system. È possibile creare prima i backup in modo da poter ripristinare i dati in un secondo momento.

Con questo comando vengono disinstallati *solo* pacchetti di linguaggio specificati in `composer.json`; in altre parole, pacchetti di linguaggio forniti come pacchetti Composer. Se il pacchetto lingua non è un pacchetto Compositore, è necessario disinstallarlo manualmente rimuovendo il codice del pacchetto lingua dal file system.

È possibile ripristinare i backup in qualsiasi momento utilizzando il comando [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files).

Utilizzo comando:

```bash
bin/magento i18n:uninstall [-b|--backup-code] {language package name} ... {language package name}
```

Il comando di disinstallazione del pacchetto della lingua esegue le operazioni seguenti:

1. Controlla le dipendenze; in tal caso, il comando termina.

   Per ovviare a questo problema, è possibile disinstallare contemporaneamente tutti i pacchetti delle lingue dipendenti oppure disinstallare prima i pacchetti delle lingue dipendenti.

1. Se si specifica `--backup code`, eseguire il backup del file system (escluse `var` e `pub/static` directory) in `var/backups/<timestamp>_filesystem.tgz`
1. Rimuove i file dei pacchetti della lingua dalla base di codice utilizzando `composer remove`.
1. Pulisce la cache.

Ad esempio, se tenti di disinstallare un pacchetto lingua da cui dipende un altro pacchetto lingua, viene visualizzato il seguente messaggio:

```terminal
Cannot uninstall vendorname/language-en_us because the following package(s) depend on it:
      vendorname/language-en_gb
```

Un&#39;alternativa consiste nel disinstallare entrambi i pacchetti di linguaggio dopo il backup della base di codice:

```bash
bin/magento i18n:uninstall vendorname/language-en_us vendorname/language-en_gb --backup-code
```

Messaggi simili alla seguente visualizzazione:

```terminal
Code backup is starting...
Code backup filename: 1435261098_filesystem_code.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1435261098_filesystem_code.tgz
[SUCCESS]: Code backup completed successfully.
Loading composer repositories with package information
Updating dependencies (including require-dev)
  - Removing vendorname/language-en_us (dev-master)
Removing Magento/LanguageEn_us
  - Removing vendorname/language-en_br (dev-master)
  - Removing vendorname/language-en_br (dev-master)
Writing lock file
Generating autoload files
```
