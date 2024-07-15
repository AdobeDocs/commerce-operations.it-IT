---
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 0%

---
# Aggiorna sistema di produzione

**Per aggiornare il sistema di produzione**:

1. Accedi al sistema di produzione come proprietario del file system.
1. Passa alla directory principale dell’applicazione e abilita la modalità di manutenzione.

   ```bash
   cd <Magento root dir>
   ```

   ```bash
   bin/magento maintenance:enable
   ```

   Per ulteriori opzioni, ad esempio la possibilità di impostare un indirizzo IP nella whitelist, vedere [`magento maintenance:enable`](../installation/tutorials/maintenance-mode.md).

1. Arrestare i processi di lavoro in esecuzione impostando `cron_run` su `false` in `app/etc/env.php` nel modo seguente:

   ```php?start_inline=1
   'cron_consumers_runner' => [
           'cron_run' => false
       ]
   ```

1. Aggiorna la configurazione.

   ```bash
   bin/magento app:config:import
   ```

1. Infine, `kill` qualsiasi processo consumer attivo.

   ```bash
   kill <PID>
   ```

   Dove `PID` è l&#39;ID processo da terminare, ad esempio:

   ```bash
   kill 1234
   ```

1. Estrarre il codice dal controllo del codice sorgente.

   ```bash
   git pull mconfig m2.2_deploy
   ```

1. Aggiorna la configurazione.

   ```bash
   bin/magento app:config:import
   ```

1. Pulire la cache.

   ```bash
   bin/magento cache:clean
   ```

1. Termina modalità di manutenzione.

   ```bash
   bin/magento maintenance:disable
   ```
