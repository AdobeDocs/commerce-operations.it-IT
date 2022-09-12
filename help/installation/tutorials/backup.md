---
title: Backup e ripristino del file system, dei supporti e del database
description: Segui questi passaggi per eseguire il backup e ripristinare l’applicazione Adobe Commerce o Magenti Open Source.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 0%

---


# Backup e ripristino del file system, dei supporti e del database

Questo comando consente di eseguire il backup:

* File system (escluso `var` e `pub/static` directory)
* La `pub/media` directory
* Il database

I backup vengono memorizzati nel `var/backups` e può essere ripristinato in qualsiasi momento utilizzando [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) comando.

Dopo il backup, è possibile [rollback](#rollback) più tardi.

>[!TIP]
>
>Per Adobe Commerce sui progetti di infrastruttura cloud, consulta [Snapshot e gestione del backup](https://devdocs.magento.com/cloud/project/project-webint-snap.html) in _Guida a Cloud_.

## Abilita backup

La funzione di backup è disabilitata per impostazione predefinita. Per abilitare, immetti il seguente comando CLI:

```bash
bin/magento config:set system/backup/functionality_enabled 1
```

>[!WARNING]
>
>**Avviso obsoleto:**
>La funzionalità di backup è obsoleta a partire dalla versione 2.1.16, 2.2.7 e 2.3.0. Si consiglia di indagare su tecnologie di backup aggiuntive e strumenti di backup binari (come Percona XtraBackup).

## Imposta il limite dei file aperti

Il ripristino di un backup precedente può avere esito negativo in modo silenzioso, causando la scrittura di dati incompleti nel file system o nel database utilizzando [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files) comando.

A volte, una stringa di query lunga causa l&#39;esaurimento dello spazio di memoria assegnato dall&#39;utente a causa di troppe chiamate ricorsive.

## Come impostare i file aperti `ulimit`

È consigliabile impostare i file aperti [`ulimit`](https://ss64.com/bash/ulimit.html) per l&#39;utente del file system a un valore di `65536` o più.

È possibile eseguire questa operazione sulla riga di comando oppure impostarla come impostazione permanente per l&#39;utente modificando il relativo script shell.

Prima di continuare, se non lo hai già fatto, passa alla [proprietario del file system](../prerequisites/file-system/overview.md).

Comando:

```bash
ulimit -s 65536
```

Se necessario, puoi impostarlo su un valore maggiore.

>[!NOTE]
>
>Sintassi dei file aperti `ulimit` dipende dalla shell UNIX utilizzata. L’impostazione precedente deve funzionare con CentOS e Ubuntu con la shell Bash. Tuttavia, per macOS, l’impostazione corretta è `ulimit -S 65532`. Per ulteriori informazioni, consultare una pagina man o un riferimento al sistema operativo.

Per impostare facoltativamente il valore nella shell Bash dell’utente:

1. Se non lo hai già fatto, passa alla [proprietario del file system](../prerequisites/file-system/overview.md).
1. Apri `/home/<username>/.bashrc` in un editor di testo.
1. Aggiungi la riga seguente:

   ```bash
   ulimit -s 65536
   ```

1. Salva le modifiche in `.bashrc` e esci dall’editor di testo.

>[!WARNING]
>
>È consigliabile evitare di impostare un valore per [`pcre.recursion_limit`](https://www.php.net/manual/en/pcre.configuration.php) in `php.ini` file perché può causare ripristini incompleti senza preavviso di errore.

## Backup

Utilizzo comando:

```bash
bin/magento setup:backup [--code] [--media] [--db]
```

Il comando esegue le seguenti attività:

1. Posiziona il negozio in modalità manutenzione.
1. Esegue una delle seguenti opzioni di comando.

   | Opzione | Significato | Nome e posizione del file di backup |
   |--- |--- |--- |
   | `--code` | Esegue il backup del file system (escluse le directory var e pub/static). | `var/backups/<timestamp>/_filesystem.tgz` |
   | `--media` | Eseguire il backup della directory pub/media. | `var/backups/<timestamp>/_filesystem_media.tgz` |
   | `--db` | Esegui il backup del database. | `var/backups/<timestamp>/_db.sql` |

1. Elimina il negozio dalla modalità di manutenzione.

Ad esempio, per eseguire il backup del file system e del database,

```bash
bin/magento setup:backup --code --db
```

Messaggi simili alla visualizzazione seguente:

```terminal
Enabling maintenance mode
Code backup is starting...
Code backup filename: 1434133011_filesystem.tgz (The archive can be uncompressed with 7-Zip on Windows systems)
Code backup path: /var/www/html/magento2/var/backups/1434133011_filesystem.tgz
[SUCCESS]: Code backup completed successfully.
DB backup is starting...
DB backup filename: 1434133011_db.sql
DB backup path: /var/www/html/magento2/var/backups/1434133011_db.sql
[SUCCESS]: DB backup completed successfully.
Disabling maintenance mode
```

## Ripristino

Questa sezione illustra come eseguire il rollback a un backup eseguito in precedenza. È necessario conoscere il nome file del file di backup da ripristinare.

Per trovare il nome dei backup, immettere:

```bash
bin/magento info:backups:list
```

La prima stringa nel nome del file di backup è la marca temporale.

Per ripristinare un backup precedente, immetti:

```bash
bin/magento setup:rollback [-c|--code-file="<name>"] [-m|--media-file="<name>"] [-d|--db-file="<name>"]
```

Ad esempio, per ripristinare un backup multimediale denominato `1440611839_filesystem_media.tgz`, inserisci

```bash
bin/magento setup:rollback -m 1440611839_filesystem_media.tgz
```

Messaggi simili alla visualizzazione seguente:

```terminal
[SUCCESS]: Media rollback completed successfully.
Please set file permission of bin/magento to executable
Disabling maintenance mode
```
