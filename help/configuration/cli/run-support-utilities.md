---
title: Eseguire le utilità di supporto
description: Risolvi i problemi del progetto Commerce utilizzando l’utility di supporto incorporata.
exl-id: 021b795f-e00d-43b5-9cbb-5b57a4795be7
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---

# Eseguire le utilità di supporto

{{ee-only}}

{{file-system-owner}}

Le utility di supporto di Adobe Commerce, denominate anche [Agente di raccolta dati](https://docs.magento.com/user-guide/system/support-data-collector.html): consente agli utenti di raccogliere informazioni sulla risoluzione dei problemi del sistema che possono essere utilizzate dal team di supporto.

Adobe Commerce utilizza questi backup, denominati anche _immagini_, per analizzare i problemi che richiedono l’accesso al codice. Di seguito è riportato uno scenario tipico:

1. Stai avendo un problema con il tuo Negozio Commerce e contatta il Supporto Adobe Commerce.
1. Il supporto determina che devono visualizzare il codice o il database per riprodurre il problema.
1. Esegui il backup del codice in un `.tar.gz` file.

   Questo backup _esclude i file multimediali per velocizzare il processo e ottenere un file molto più piccolo.

1. Eseguire il backup del database in una `.tar.gz` file.

   Per impostazione predefinita, i dati sensibili vengono sottoposti a hashing durante l’esecuzione del backup.

1. I backup vengono caricati in un servizio di condivisione file.
1. Il supporto analizza i problemi senza influire sull’ambiente di sviluppo o produzione.

Il completamento delle utilità può richiedere alcuni minuti.

## Creare un backup del codice

Questo comando esegue il backup del codice e lo comprime `tar.gz` formato.

{{tip-backup-command}}

Opzioni comando:

```bash
bin/magento support:backup:code [--name=<file name>] [-o|--output=<path>] [-l|--logs]
```

Dove:

- **`--name`** specifica il nome del file di dump (facoltativo). Se si omette questo parametro, il file di dump sarà contrassegnato con data e ora.
- **`-o|--output=<path>`** è il percorso assoluto del file system in cui archiviare il backup (obbligatorio).
- **`-l|--logs`** include i file di registro (facoltativo).

Ad esempio, per creare un backup del codice denominato `/var/www/html/magento2/var/log/mycodebackup.tar.gz`:

```bash
bin/magento support:backup:code --name mycodebackup -o /var/www/html/magento2/var/log
```

Al termine del comando, fornisci il backup del codice al supporto Adobe Commerce.

## Creare un backup del database

Questo comando esegue il backup del database Commerce e lo comprime in `tar.gz` formato.

{{tip-backup-command}}

Opzioni comando:

```bash
bin/magento support:backup:db [--name=<name>] [-o|--output=<path>] [-l|--logs] [-i|--ignore-sanitize]
```

Dove:

- **`--name`** specifica il nome del file di dump (facoltativo). Se si omette questo parametro, il file di dump sarà contrassegnato con data e ora.
- **`-o|--output=<path>` è il percorso assoluto del file system in cui archiviare il backup (obbligatorio).
- **`-l|--logs`** include i file di registro (facoltativo).
- **`-i|--ignore-sanitize`** significa che i dati vengono conservati; ometti il flag per eseguire l’hashing dei dati sensibili memorizzati nel database durante la creazione del backup (facoltativo).

I dati riservati includono le informazioni sui clienti delle tabelle di database seguenti:

```terminal
'customer_entity',
'customer_entity_varchar',
'customer_address_entity',
'customer_address_entity_varchar',
'customer_grid_flat',
'quote',
'quote_address',
'sales_order',
'sales_order_address',
'sales_order_grid'
```

Al termine del comando, fornire il backup del database al supporto Adobe Commerce.

## Risoluzione dei problemi: utility di visualizzazione e percorsi

Forniamo comandi che visualizzano i percorsi delle utility richieste dall’agente di raccolta dati e dalla riga di comando. Puoi utilizzare questi comandi, ad esempio, se nella riga di comando o in Amministrazione vengono visualizzati errori come i seguenti:

```terminal
Utility lsof not found
```

Eseguire i seguenti comandi nell&#39;ordine indicato per visualizzare i percorsi delle applicazioni utilizzate dalle utility di supporto e dall&#39;agente di raccolta dati:

1. Passa alla directory di installazione di Commerce.

   Ad esempio: `cd /var/www/magento2`

   >[!INFO]
   >
   >I comandi vengono eseguiti correttamente _solo_ dalla directory di installazione.

1. `bin/magento support:utility:paths` crea `<magento_root>/var/support/Paths.php`, che elenca i percorsi di tutte le applicazioni utilizzate dall&#39;utility.
1. `bin/magento support:utility:check` visualizza i percorsi del file system.

Di seguito è riportato un esempio:

```terminal
   gzip => /bin/gzip
   lsof => /usr/sbin/lsof
   mysqldump => /usr/bin/mysqldump
   nice => /bin/nice
   php => /usr/bin/php
   tar => /bin/tar
   sed => /bin/sed
   bash => /bin/bash
   mysql => /usr/bin/mysql
```

Per risolvere i problemi relativi all&#39;esecuzione degli strumenti, assicurarsi che queste applicazioni siano installate e si trovino nel file dell&#39;utente del server Web `$PATH` variabile di ambiente.
