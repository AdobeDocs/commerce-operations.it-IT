---
title: Abilita registrazione
description: Scopri come abilitare e disabilitare i tipi di registrazione.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---


# Abilita registrazione

{{file-system-owner}}

## Debug logging

Per impostazione predefinita, Commerce scrive nel registro di debug (`<install_directory>/var/log/debug.log`) quando è in modalità predefinita o di sviluppo, ma non in modalità di produzione. Utilizza la `bin/magento setup:config:set --enable-debug-logging` per modificare il valore predefinito.

>[!INFO]
>
>A partire da Commerce 2.3.1, non è più possibile utilizzare la funzione `bin/magento config:set dev/debug/debug_logging` per abilitare o disabilitare la registrazione di debug per la modalità corrente.

### Per abilitare la registrazione di debug

1. Utilizza la `setup:config:set` per abilitare la registrazione di debug per la modalità corrente.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=true
   ```

1. Svuotare la cache.

   ```bash
   bin/magento cache:flush
   ```

### Per disabilitare la registrazione di debug

1. Utilizza la `setup:config:set` per disabilitare la registrazione di debug per la modalità corrente.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=false
   ```

1. Svuotare la cache.

   ```bash
   bin/magento cache:flush
   ```

## Registrazione database

Per impostazione predefinita, Commerce scrive i registri delle attività del database in `<install-dir>/var/debug/db.log` file.

### Per abilitare la registrazione del database

1. Utilizza la `dev:query-log` per abilitare o disabilitare la registrazione del database.

   ```bash
   bin/magento dev:query-log:enable
   ```

   ```bash
   bin/magento dev:query-log:disable
   ```

1. Svuotare la cache.

   ```bash
   bin/magento cache:flush
   ```

## Registrazione con cloro

Con il rilascio della versione 2.3.1, Commerce ora crea un `cron` registro. \
Recentemente il commercio ha reso la registrazione dei cron più dettagliata, che ha fornito più informazioni ma allungato il `system.log` considerevolmente.
Spostamento `cron` informazioni su un registro dedicato facilita la lettura di entrambi i registri.

Per impostazione predefinita, Commerce scrive `cron` informazioni `<install-directory>/var/log/cron.log` file.

## Registrazione del registro di sistema

Per impostazione predefinita, Commerce scrive _syslog_ accede al sistema operativo `syslog` file.
A partire da Commerce 2.3.1, è necessario utilizzare il `magento` per attivare o disattivare il registro di sistema.
L’impostazione in Amministratore è stata rimossa.

### Per abilitare la registrazione del registro di sistema

Accesso a `syslog` è disabilitata per impostazione predefinita.

1. Utilizza la `setup:config:set` per modificare il comando `dev/syslog/syslog_logging` valore di database in `true`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=true
   ```

1. Svuotare la cache.

   ```bash
   bin/magento cache:flush
   ```

### Per disabilitare la registrazione del registro di sistema

1. Utilizza la `setup:config:set` per modificare il comando `dev/syslog/syslog_logging` valore di database in `false`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=false
   ```

1. Svuotare la cache.

   ```bash
   bin/magento cache:flush
   ```
