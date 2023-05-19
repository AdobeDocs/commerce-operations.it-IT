---
title: Abilita registrazione
description: Scopri come abilitare e disabilitare i tipi di registrazione.
exl-id: 78b0416a-5bad-42a9-a918-603600e98928
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '252'
ht-degree: 0%

---

# Abilita registrazione

{{file-system-owner}}

## Debug logging

Per impostazione predefinita, Commerce scrive nel registro di debug (`<install_directory>/var/log/debug.log`) quando è in modalità predefinita o di sviluppo, ma non quando è in modalità di produzione. Utilizza il `bin/magento setup:config:set --enable-debug-logging` per modificare il valore predefinito.

>[!INFO]
>
>A partire dalla versione 2.3.1 di Commerce, non è più possibile utilizzare `bin/magento config:set dev/debug/debug_logging` per abilitare o disabilitare la registrazione di debug per la modalità corrente.

### Per abilitare la registrazione di debug

1. Utilizza il `setup:config:set` per abilitare la registrazione di debug per la modalità corrente.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=true
   ```

1. Svuota la cache.

   ```bash
   bin/magento cache:flush
   ```

### Per disabilitare la registrazione di debug

1. Utilizza il `setup:config:set` comando per disabilitare la registrazione di debug per la modalità corrente.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=false
   ```

1. Svuota la cache.

   ```bash
   bin/magento cache:flush
   ```

## Registrazione del database

Per impostazione predefinita, Commerce scrive i registri delle attività del database in `<install-dir>/var/debug/db.log` file.

### Per abilitare la registrazione del database

1. Utilizza il `dev:query-log` per attivare o disattivare la registrazione del database.

   ```bash
   bin/magento dev:query-log:enable
   ```

   ```bash
   bin/magento dev:query-log:disable
   ```

1. Svuota la cache.

   ```bash
   bin/magento cache:flush
   ```

## Registrazione Cron

Con il rilascio della versione 2.3.1 di, Commerce ora crea un’istanza `cron` log. \
Commerce ha recentemente reso la registrazione cron più dettagliata, che ha fornito ulteriori informazioni ma ha allungato i `system.log` considerevolmente.
Spostamento `cron` le informazioni su un registro dedicato facilitano la lettura di entrambi i registri.

Per impostazione predefinita, Commerce scrive `cron` informazioni su `<install-directory>/var/log/cron.log` file.

## Registrazione Syslog

Per impostazione predefinita, Commerce scrive _syslog_ registra nel sistema operativo `syslog` file.
A partire dalla versione 2.3.1 di Commerce, devi utilizzare il `magento` per attivare o disattivare syslog.
L’impostazione in Admin (Amministrazione) è stata rimossa.

### Per abilitare la registrazione syslog

Accesso a `syslog` è disattivato per impostazione predefinita.

1. Utilizza il `setup:config:set` comando per modificare `dev/syslog/syslog_logging` valore del database in `true`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=true
   ```

1. Svuota la cache.

   ```bash
   bin/magento cache:flush
   ```

### Per disattivare la registrazione syslog

1. Utilizza il `setup:config:set` comando per modificare `dev/syslog/syslog_logging` valore del database in `false`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=false
   ```

1. Svuota la cache.

   ```bash
   bin/magento cache:flush
   ```
