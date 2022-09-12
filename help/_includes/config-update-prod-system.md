---
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '85'
ht-degree: 0%

---
# Aggiorna il sistema di produzione

**Per aggiornare il sistema di produzione**:

1. Accedi al sistema di produzione come proprietario del file system.
1. Passa alla directory principale dell&#39;applicazione e attiva la modalità di manutenzione.

   ```bash
   cd <Magento root dir>
   ```

   ```bash
   bin/magento maintenance:enable
   ```

   Per ulteriori opzioni, ad esempio la possibilità di impostare una whitelist di indirizzi IP, consulta [`magento maintenance:enable`](../installation/tutorials/maintenance-mode.md).

1. Interrompere i processi di lavoro in coda in esecuzione impostando `cron_run` a `false` in `app/etc/env.php` come segue:

   ```php?start_inline=1
   'cron_consumers_runner' => [
           'cron_run' => false
       ]
   ```

1. Aggiorna la configurazione.

   ```bash
   bin/magento app:config:import
   ```

1. Infine, `kill` qualsiasi processo attivo dei consumatori.

   ```bash
   kill <PID>
   ```

   Dove `PID` è l’ID del processo da terminare, ad esempio:

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

1. Pulisci la cache.

   ```bash
   bin/magento cache:clean
   ```

1. Modalità di manutenzione finale.

   ```bash
   bin/magento maintenance:disable
   ```
