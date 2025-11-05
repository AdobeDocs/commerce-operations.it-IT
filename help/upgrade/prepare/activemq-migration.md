---
title: Migrazione da RabbitMQ ad ActiveMQ
description: Scopri come sostituire il broker della coda di messaggi utilizzato per le installazioni locali di Adobe Commerce.
feature: Services, Configuration
source-git-commit: 8f57a4fa7744f4647ab96d0fcfae08b8eb4927c6
workflow-type: tm+mt
source-wordcount: '648'
ht-degree: 0%

---

# Migrazione ad ActiveMQ

ActiveMQ (Apache ActiveMQ Artemis) è un broker di messaggi multiprotocollo ad alte prestazioni che fornisce un’alternativa a RabbitMQ per la gestione delle code di messaggi in Adobe Commerce.

A partire da 2.4.8-p3, 2.4.7-p8 e 2.4.6-p13, Adobe Commerce supporta ActiveMQ come broker della coda di messaggi. Questo offre maggiore flessibilità alle installazioni on-premise per scegliere tra RabbitMQ e ActiveMQ in base ai requisiti e alle competenze dell&#39;infrastruttura.

## Prima di iniziare

Prima di avviare la migrazione, verifica quanto segue:

1. Esaminare la configurazione corrente di RabbitMQ in `app/etc/env.php`.
1. Backup completo del database e della base di codice.
1. Verificare che l&#39;installazione soddisfi i requisiti di sistema per ActiveMQ.
1. Pianifica una finestra di manutenzione per completare la migrazione.

## Percorso di migrazione

La migrazione ad ActiveMQ è un processo semplice, ma è essenziale assicurarsi che tutti i messaggi in sospeso vengano elaborati prima di cambiare broker.

Queste istruzioni di migrazione presuppongono che Adobe Commerce sia l’unica applicazione che utilizza il broker della coda di messaggi.

### Passaggio 1: attivare la modalità di manutenzione per il sito

1. Posiziona il sito in [Modalità manutenzione](../../installation/tutorials/maintenance-mode.md):

   ```bash
   bin/magento maintenance:enable
   ```

1. Verifica che la modalità di manutenzione sia abilitata:

   ```bash
   bin/magento maintenance:status
   ```

### Passaggio 2: controllare il conteggio dei messaggi RabbitMQ

Prima di procedere, verificare che tutti i messaggi in RabbitMQ siano stati elaborati. Utilizza uno dei seguenti metodi:

#### Metodo A: utilizzo del dashboard di gestione di RabbitMQ

1. Accedere all&#39;interfaccia utente di gestione di RabbitMQ all&#39;indirizzo `http://<host>:15672`
1. Credenziali predefinite: `guest/guest`
1. Passa alla scheda **Code**
1. Verifica che tutte le code mostrino **0 messaggi**

   ![Dashboard di gestione RabbitMQ](../../assets/upgrade-guide/rabbitmq_mgmt_dashboard.png)

#### Metodo B: Utilizzo della riga di comando rabbitmqctl

1. Controlla tutte le code e il numero dei messaggi:

   ```bash
   rabbitmqctl list_queues name messages consumers
   ```

   <img src="../../assets/upgrade-guide/rabbitmqctl.png" alt="Output CLI RabbitMQ" width="500" />

1. Controllare le informazioni dettagliate sulla coda:

   ```bash
   rabbitmqctl list_queues name messages messages_ready messages_unacknowledged consumers
   ```

   <img src="../../assets/upgrade-guide/rabbitmqctl_detailed.png" alt="Output dettagliato CLI di RabbitMQ" width="500" />

### Passaggio 3: elaborare i messaggi in sospeso

Se i messaggi sono in sospeso in una coda, elaborarli prima di procedere.

1. Ottieni l’elenco dei consumatori disponibili:

   ```bash
   bin/magento queue:consumers:list
   ```

1. Elabora i consumer come gruppo o per singola coda di messaggi:

   - **Elabora consumatori come gruppo**

     ```bash
     bin/magento cron:run --group=consumers
     ```

     >[!NOTE]
     >
     >Se cron è già in esecuzione nel sistema, non è necessario eseguire `bin/magento cron:run --group=consumers` manualmente. Verifica invece che i messaggi vengano elaborati controllando il conteggio dei messaggi utilizzando i comandi del passaggio 2.

   - **Elabora una coda messaggi specifica**

     ```bash
     bin/magento queue:consumers:start <consumer_name> --max-messages=<number>
     ```

     Ad esempio, per elaborare le operazioni asincrone:

     ```bash
     bin/magento queue:consumers:start async.operations.all --max-messages=1000
     ```

     >[!NOTE]
     >
     >Il parametro `--max-messages` limita il numero di messaggi da elaborare prima dell&#39;arresto del consumer. Regola questo valore in base alla dimensione della coda.

   - **Monitorare l&#39;elaborazione dei messaggi**

     Controlla continuamente i conteggi dei messaggi fino a quando tutte le code non sono vuote:

     ```bash
     # Check every few seconds until 0 messages remain
     watch -n 5 "rabbitmqctl list_queues name messages | grep -v '^Listing' | grep -v '0$'"
     ```

### Passaggio 4: verifica che tutti i messaggi siano elaborati

Prima di procedere al passaggio successivo, verificare che **tutte le code visualizzino 0 messaggi**. Esegui nuovamente i comandi di verifica dal passaggio 2.

>[!WARNING]
>
>Non procedere al passaggio successivo se alcuni messaggi rimangono non elaborati. Se cambi operatore mentre i messaggi sono ancora in sospeso, potrebbe verificarsi una perdita di dati.

### Passaggio 5: arrestare i processi relativi a consumatori e cron

1. Arresta tutti i consumer della coda di messaggi in esecuzione:

   ```bash
   # If using supervisor
   supervisorctl stop all
   
   # Or manually kill consumer processes
   pkill -f "queue:consumers:start"
   ```

1. Disabilita processi cron:

   ```bash
   bin/magento cron:remove
   ```

1. Verificare che i processi cron siano rimossi:

   ```bash
   crontab -l
   ```

### Passaggio 6: eseguire il backup della configurazione corrente

Crea un backup della configurazione corrente:

```bash
cp app/etc/env.php app/etc/env.php.backup.rabbitmq
```

### Passaggio 7: disinstallare facoltativamente RabbitMQ

Se non è più necessario, è possibile disinstallare RabbitMQ.

### Passaggio 8: installare e configurare ActiveMQ in Adobe Commerce

Per completare le attività di installazione e configurazione di ActiveMQ, ad esempio la configurazione del protocollo STOMP e la verifica della connessione, vedere la [Guida all&#39;installazione e alla configurazione](../../installation/prerequisites/activemq.md).

### Passaggio 9: reinstallare i processi cron

1. Al termine del test, reinstallare i processi cron:

   ```bash
   bin/magento cron:install
   ```

1. Verifica che i processi cron siano pianificati:

   ```bash
   crontab -l
   ```

### Passaggio 10: disabilitare la modalità di manutenzione

1. Dopo aver verificato che tutto funzioni correttamente, disattiva la modalità di manutenzione:

   ```bash
   bin/magento maintenance:disable
   ```

1. Verifica che la modalità di manutenzione sia disabilitata:

   ```bash
   bin/magento maintenance:status
   ```

### Passaggio 11: Monitorare il sistema

Monitora il sistema per 24-48 ore dopo la migrazione per verificare che tutte le operazioni in coda funzionino correttamente:

- Controllare regolarmente la velocità effettiva dei messaggi nella console Web ActiveMQ
- Monitorare i registri dell’applicazione per individuare eventuali errori relativi alla coda
- Verifica che le operazioni asincrone (salvataggio configurazione, esportazioni e così via) funzionino
- Controlla i registri cron per assicurarti che i consumatori siano in esecuzione

```bash
# Monitor system logs for queue activity
tail -f var/log/system.log | grep -i queue

# Monitor cron logs
tail -f var/log/cron.log

# Check running consumer processes
ps aux | grep "queue:consumers:start"
```

## Rollback

Se si verificano problemi durante o dopo la migrazione, puoi eseguire il rollback a RabbitMQ:

1. Abilita modalità di manutenzione:

   ```bash
   bin/magento maintenance:enable
   ```

1. Interrompi tutti i consumer e disattiva cron:

   ```bash
   pkill -f "queue:consumers:start"
   bin/magento cron:remove
   ```

1. Ripristina la configurazione precedente:

   ```bash
   cp app/etc/env.php.backup.rabbitmq app/etc/env.php
   ```

1. Avviare RabbitMQ (se interrotto):

   ```bash
   sudo systemctl start rabbitmq-server
   ```

1. Cancella cache:

   ```bash
   bin/magento cache:flush
   ```

1. Reinstalla cron:

   ```bash
   bin/magento cron:install
   ```

1. Disattiva modalità di manutenzione:

   ```bash
   bin/magento maintenance:disable
   ```

Al termine della migrazione non sono necessarie ulteriori modifiche al valore di configurazione.

