---
title: Abilita registrazione
description: Scopri come abilitare e disabilitare diversi tipi di accesso in Adobe Commerce. Scopri le tecniche di configurazione e gestione della registrazione.
feature: Configuration, Logs
exl-id: 78b0416a-5bad-42a9-a918-603600e98928
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '268'
ht-degree: 0%

---

# Abilita registrazione

{{file-system-owner}}

## Debug logging

Per impostazione predefinita, Commerce scrive nel registro di debug (`<install_directory>/var/log/debug.log`) quando è in modalità predefinita o di sviluppo, ma non quando è in modalità di produzione. Utilizzare il comando `bin/magento setup:config:set --enable-debug-logging` per modificare il valore predefinito.

>[!INFO]
>
>A partire da Commerce 2.3.1, non è più possibile utilizzare il comando `bin/magento config:set dev/debug/debug_logging` per abilitare o disabilitare la registrazione di debug per la modalità corrente.

### Per abilitare la registrazione di debug

1. Utilizzare il comando `setup:config:set` per abilitare la registrazione di debug per la modalità corrente.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=true
   ```

1. Svuota la cache.

   ```bash
   bin/magento cache:flush
   ```

### Per disabilitare la registrazione di debug

1. Utilizzare il comando `setup:config:set` per disabilitare la registrazione di debug per la modalità corrente.

   ```bash
   bin/magento setup:config:set --enable-debug-logging=false
   ```

1. Svuota la cache.

   ```bash
   bin/magento cache:flush
   ```

## Registrazione del database

Per impostazione predefinita, Commerce scrive i log delle attività del database nel file `<install-dir>/var/debug/db.log`.

### Per abilitare la registrazione del database

1. Utilizzare il comando `dev:query-log` per abilitare o disabilitare la registrazione del database.

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

Con la versione 2.3.1 di, Commerce ora crea un registro `cron` separato. \
Commerce ha recentemente reso la registrazione cron più dettagliata, fornendo ulteriori informazioni ma allungando notevolmente `system.log`.
Spostando le informazioni di `cron` in un registro dedicato, è più facile leggere entrambi i registri.

Per impostazione predefinita, Commerce scrive `cron` informazioni nel file `<install-directory>/var/log/cron.log`.

## Registrazione Syslog

Per impostazione predefinita, Commerce scrive i registri _syslog_ nel file `syslog` del sistema operativo.
A partire da Commerce 2.3.1, è necessario utilizzare il comando `magento` per abilitare o disabilitare syslog.
L’impostazione in Admin (Amministrazione) è stata rimossa.

### Per abilitare la registrazione syslog

La registrazione a `syslog` è disabilitata per impostazione predefinita.

1. Utilizzare il comando `setup:config:set` per modificare il valore del database `dev/syslog/syslog_logging` in `true`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=true
   ```

1. Svuota la cache.

   ```bash
   bin/magento cache:flush
   ```

### Per disattivare la registrazione syslog

1. Utilizzare il comando `setup:config:set` per modificare il valore del database `dev/syslog/syslog_logging` in `false`.

   ```bash
   bin/magento setup:config:set --enable-syslog-logging=false
   ```

1. Svuota la cache.

   ```bash
   bin/magento cache:flush
   ```
