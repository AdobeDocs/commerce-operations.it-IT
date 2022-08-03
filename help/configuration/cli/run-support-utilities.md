---
title: Esegui le utilità di supporto
description: Risolvere i problemi relativi al progetto Commerce utilizzando l’utility di supporto integrata.
source-git-commit: 2c12c6ea6e7b6ffeb07bbda17ded34e39de6656a
workflow-type: tm+mt
source-wordcount: '465'
ht-degree: 0%

---


# Esegui le utilità di supporto

{{ee-only}}

{{file-system-owner}}

Le utility di supporto Adobe Commerce, denominate anche [Raccoglitore dati](https://docs.magento.com/user-guide/system/support-data-collector.html)- consente agli utenti di raccogliere informazioni sulla risoluzione dei problemi relativi al sistema che possono essere utilizzate dal nostro team di assistenza.

Adobe Commerce utilizza questi backup, denominati anche _immagini_, per analizzare i problemi che richiedono l’accesso al codice. Segue uno scenario tipico:

1. Stai avendo un problema con il tuo negozio Commerce e contatta il supporto Adobe Commerce.
1. Il supporto determina la necessità di visualizzare il codice o il database per riprodurre il problema.
1. Esegui il backup del codice in un `.tar.gz` file.

   Questo backup _esclude i file multimediali per velocizzare il processo e ottenere un file molto più piccolo.

1. Eseguire il backup del database su un `.tar.gz` file.

   Per impostazione predefinita, i dati sensibili vengono crittografati durante il backup.

1. Puoi caricare i backup in un servizio di condivisione file.
1. Il supporto analizza i problemi senza influire sull&#39;ambiente di sviluppo o produzione.

Il completamento delle utility può richiedere alcuni minuti.

## Creare un backup del codice

Questo comando esegue il backup del codice e lo comprime in `tar.gz` formato.

{{tip-backup-command}}

Opzioni di comando:

```bash
bin/magento support:backup:code [--name=<file name>] [-o|--output=<path>] [-l|--logs]
```

Dove:

- **`--name`** specifica il nome del file di dump (facoltativo). Se ometti questo parametro, il file di immagine viene contrassegnato con data e ora.
- **`-o|--output=<path>`** è il percorso assoluto del file system in cui memorizzare il backup (obbligatorio).
- **`-l|--logs`** include i file di registro (facoltativo).

Ad esempio, per creare un backup del codice denominato `/var/www/html/magento2/var/log/mycodebackup.tar.gz`:

```bash
bin/magento support:backup:code --name mycodebackup -o /var/www/html/magento2/var/log
```

Al termine del comando, fornisci il backup del codice al supporto Adobe Commerce.

## Creare un backup del database

Questo comando esegue il backup del database Commerce e lo comprime in `tar.gz` formato.

{{tip-backup-command}}

Opzioni di comando:

```bash
bin/magento support:backup:db [--name=<name>] [-o|--output=<path>] [-l|--logs] [-i|--ignore-sanitize]
```

Dove:

- **`--name`** specifica il nome del file di dump (facoltativo). Se ometti questo parametro, il file di immagine viene contrassegnato con data e ora.
- **`-o|--output=<path>` è il percorso assoluto del file system in cui memorizzare il backup (obbligatorio).
- **`-l|--logs`** include i file di registro (facoltativo).
- **`-i|--ignore-sanitize`** significa che i dati sono conservati; omettere il flag ai dati sensibili all’hash memorizzati nel database durante la creazione del backup (facoltativo).

I dati sensibili includono le informazioni sui clienti provenienti dalle seguenti tabelle di database:

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

Al termine del comando, fornisci il backup del database al supporto Adobe Commerce.

## Risoluzione dei problemi: utilità di visualizzazione e percorsi

Forniamo comandi che visualizzano i percorsi alle utility richieste dal Data Collector e dalla riga di comando. È possibile utilizzare questi comandi, ad esempio, se si verificano errori come la seguente visualizzazione in Admin o nella riga di comando:

```terminal
Utility lsof not found
```

Esegui i seguenti comandi nell&#39;ordine mostrato per visualizzare i percorsi delle applicazioni utilizzate dalle utilità di supporto e dal Data Collector:

1. Passa alla directory di installazione Commerce.

   Ad esempio: `cd /var/www/magento2`

   >[!INFO]
   >
   >I comandi vengono eseguiti correttamente _only_ dalla directory di installazione.

1. `bin/magento support:utility:paths` crea `<magento_root>/var/support/Paths.php`, che elenca i percorsi di tutte le applicazioni utilizzate dall&#39;utilità.
1. `bin/magento support:utility:check` visualizza i percorsi del file system.

Segue un esempio:

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

Per risolvere i problemi relativi all&#39;esecuzione degli strumenti, assicurati che queste applicazioni siano installate e siano nel server Web dell&#39;utente `$PATH` variabile di ambiente.
