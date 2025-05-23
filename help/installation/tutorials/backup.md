---
title: Backup e rollback del file system, dell'media e del database
description: Segui questi passaggi per eseguire il backup e il ripristino di Adobe Systems Commerce applicazione.
exl-id: b9925198-37b4-4456-aa82-7c55d060c9eb
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 0%

---

# Backup e rollback del file system, dell&#39;media e del database

Questo comando consente di eseguire il backup:

* Il file system (escluse `var` le e `pub/static` directory)
* La `pub/media` directory
* Il database

I backup sono archiviati nella directory `var/backups` e possono essere ripristinati in qualsiasi momento utilizzando il comando [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files).

Dopo il backup, puoi [eseguire il rollback](#rollback) in un secondo momento.

>[!TIP]
>
>Per i progetti Adobe Commerce su infrastrutture cloud, consulta [Snapshot e gestione backup](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/storage/snapshots) nella _Guida cloud_.

## Abilita backup

La funzione di backup è disabilitata per impostazione predefinita. Per attivare questa opzione, immettere il seguente comando CLI:

```bash
bin/magento config:set system/backup/functionality_enabled 1
```

>[!WARNING]
>
>**Avviso di rimozione:**
>La funzionalità di backup è obsoleta dal 2.1.16, 2.2.7 e 2.3.0. Si consiglia di esaminare ulteriori tecnologie di backup e strumenti di backup binari (come Percona XtraBackup).

## Imposta il limite di file aperti

Il rollback a un backup precedente può non riuscire in modo invisibile all&#39;utente, causando la scrittura di dati incompleti nel file system o nel database tramite il comando [`magento setup:rollback`](uninstall-modules.md#roll-back-the-file-system-database-or-media-files).

A volte, una lunga stringa di query causa la mancanza di memoria dell’utente a causa di troppe chiamate ricorsive.

## Impostare i file aperti `ulimit`

È consigliabile impostare i file [`ulimit`](https://ss64.com/bash/ulimit.html) aperti per il file system utente su un valore pari `65536` o superiore.

Puoi farlo sia sulla riga di comando o puoi renderlo un&#39;impostazione permanente per il utente modificando il loro script di shell.

Prima di continuare, se non l&#39;avete già fatto, passate al [file system proprietario](../prerequisites/file-system/overview.md).

Comando:

```bash
ulimit -s 65536
```

Se necessario, è possibile modificarlo con un valore maggiore.

>[!NOTE]
>
>La sintassi per i file `ulimit` aperti dipende dalla shell UNIX utilizzata. L&#39;impostazione precedente dovrebbe funzionare con CentOS e Ubuntu con la shell Bash. Tuttavia, per macOS, l&#39;impostazione corretta è `ulimit -S 65532`. Per ulteriori informazioni, consultare una pagina man o un riferimento al sistema operativo.

Per impostare facoltativamente il valore nella shell Bash del utente:

1. Se non l&#39;avete già fatto, passate al [file system proprietario](../prerequisites/file-system/overview.md).
1. Apri `/home/<username>/.bashrc` in un editor di testo.
1. Aggiungi la seguente riga:

   ```bash
   ulimit -s 65536
   ```

1. Salvare le modifiche apportate a `.bashrc` e uscire dall&#39;editor di testo.

>[!WARNING]
>
>È consigliabile evitare di impostare un valore per [`pcre.recursion_limit`](https://www.php.net/manual/en/pcre.configuration.php) nel file `php.ini`, in quanto potrebbe causare rollback incompleti senza alcun avviso di errore.

## Backup

Utilizzo comando:

```bash
bin/magento setup:backup [--code] [--media] [--db]
```

Il comando esegue le seguenti operazioni:

1. Mette l&#39;archivio in modalità di manutenzione.
1. Esegue una delle seguenti opzioni di comando.

   | Opzione | Significato | Nome e percorso del file di backup |
   |--- |--- |--- |
   | `--code` | Esegue il backup del file system (escluse le directory var e pub/static). | `var/backups/<timestamp>/_filesystem.tgz` |
   | `--media` | Indietro la directory pub/media. | `var/backups/<timestamp>/_filesystem_media.tgz` |
   | `--db` | Indietro il database. | `var/backups/<timestamp>/_db.sql` |

1. Toglie il store dalla modalità di manutenzione.

Ad esempio, per eseguire il backup del file system e del database,

```bash
bin/magento setup:backup --code --db
```

Vengono visualizzati messaggi simili al seguente:

```
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

## Rollback

Questa sezione illustra come ripristinare un backup precedente. È necessario conoscere il nome del file di backup da ripristinare.

Per trovare il nome dei backup, immettere:

```bash
bin/magento info:backups:list
```

La prima stringa nel nome del file di backup è la marca temporale.

Per eseguire il rollback a un backup precedente, immettere:

```bash
bin/magento setup:rollback [-c|--code-file="<name>"] [-m|--media-file="<name>"] [-d|--db-file="<name>"]
```

Ad esempio, per ripristinare un backup multimediale denominato `1440611839_filesystem_media.tgz`, immettere:

```bash
bin/magento setup:rollback -m 1440611839_filesystem_media.tgz
```

Messaggi simili alla seguente visualizzazione:

```
[SUCCESS]: Media rollback completed successfully.
Please set file permission of bin/magento to executable
Disabling maintenance mode
```
