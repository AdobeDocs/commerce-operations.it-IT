---
title: Disinstallare i pacchetti di lingua
description: Per disinstallare un pacchetto Adobe Commerce o Magenti Open Source Language, effettua le seguenti operazioni.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---


# Disinstallare i pacchetti di lingua

Questa sezione illustra come disinstallare uno o più pacchetti linguistici, includendo facoltativamente il codice dei pacchetti linguistici dal file system. È possibile creare prima i backup in modo da ripristinare i dati in un secondo momento.

Disinstalla questo comando *only* pacchetti linguistici specificati in `composer.json`; in altre parole, i pacchetti linguistici forniti come [Compositore](https://glossary.magento.com/composer) pacchetti. Se [pacchetto linguistico](https://glossary.magento.com/language-package) non è un pacchetto Composer, è necessario disinstallarlo manualmente rimuovendo il codice del pacchetto di linguaggio dal file system.

È possibile ripristinare i backup in qualsiasi momento utilizzando [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) comando.

Utilizzo comando:

```bash
bin/magento i18n:uninstall [-b|--backup-code] {language package name} ... {language package name}
```

Il comando disinstalla pacchetto linguistico esegue le seguenti attività:

1. Controllo delle dipendenze; in tal caso, il comando termina.

   Per risolvere questo problema, è possibile disinstallare contemporaneamente tutti i pacchetti di lingua dipendenti oppure disinstallare prima i pacchetti di lingua dipendenti.

1. Se `--backup code` viene specificato, esegue il backup del file system (escluso `var` e `pub/static` directory) a `var/backups/<timestamp>_filesystem.tgz`
1. Rimuove i file dei pacchetti di linguaggio dal codebase utilizzando `composer remove`.
1. Pulisce il [cache](https://glossary.magento.com/cache).

Ad esempio, se si tenta di disinstallare un pacchetto per la lingua da cui dipende un altro pacchetto per la lingua, viene visualizzato il seguente messaggio:

```terminal
Cannot uninstall vendorname/language-en_us because the following package(s) depend on it:
      vendorname/language-en_gb
```

Un&#39;alternativa è quella di disinstallare entrambi i pacchetti linguistici dopo il backup del codebase:

```bash
bin/magento i18n:uninstall vendorname/language-en_us vendorname/language-en_gb --backup-code
```

Messaggi simili alla visualizzazione seguente:

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
