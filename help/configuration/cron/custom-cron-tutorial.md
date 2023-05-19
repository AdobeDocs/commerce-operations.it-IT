---
title: Configurare un processo cron personalizzato e un gruppo cron (tutorial)
description: Utilizza questo tutorial per creare un processo cron personalizzato.
exl-id: d8efcafc-3ae1-4c2d-a8ad-4a806fb48932
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '808'
ht-degree: 0%

---

# Configurare un processo cron personalizzato

Questa esercitazione dettagliata mostra come creare un processo cron personalizzato e facoltativamente un gruppo cron in un modulo di esempio. Puoi utilizzare un modulo che già disponi oppure un modulo di esempio dal nostro [`magento2-samples` archivio][samples].

L’esecuzione del processo cron comporta l’aggiunta di una riga al `cron_schedule` tabella con il nome del processo cron, `custom_cron`.

Viene inoltre illustrato come creare facoltativamente un gruppo cron, che è possibile utilizzare per eseguire processi cron personalizzati con impostazioni diverse dai valori predefiniti dell’applicazione Commerce.

In questo tutorial, si presuppone quanto segue:

- L’applicazione Commerce viene installata in `/var/www/html/magento2`
- Il nome utente e la password del database Commerce sono entrambi `magento`
- Tutte le azioni vengono eseguite come [proprietario del file system](../../installation/prerequisites/file-system/overview.md)

## Passaggio 1: ottenere un modulo di esempio

Per impostare un processo cron personalizzato, è necessario un modulo di esempio. Suggeriamo `magento-module-minimal` modulo.

Se disponi già di un modulo di esempio, puoi utilizzarlo; salta questo passaggio e quello successivo e continua con il Passaggio 3: Creare una classe per eseguire cron.

**Per ottenere un modulo di esempio**:

1. Accedi al server Commerce come, o passa a, il [proprietario del file system](../../installation/prerequisites/file-system/overview.md).
1. Passa a una directory che non si trova nella directory principale dell’applicazione Commerce (ad esempio, la home directory).
1. Clona il [`magento2-samples` archivio][samples].

   ```bash
   git clone git@github.com:magento/magento2-samples.git
   ```

   Se il comando non riesce e viene visualizzato l&#39;errore `Permission denied (publickey).`, è necessario [aggiungi la chiave pubblica SSH a GitHub.com][git-ssh].

1. Creare una directory in cui copiare il codice di esempio:

   ```bash
   mkdir -p /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

1. Copia il codice del modulo di esempio:

   ```bash
   cp -r ~/magento2-samples/sample-module-minimal/* /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

1. Verifica i file copiati correttamente:

   ```bash
   ls -al /var/www/html/magento2/app/code/Magento/SampleMinimal
   ```

   Dovresti visualizzare il seguente risultato:

   ```terminal
   drwxrwsr-x.   4 magento_user apache  4096 Oct 30 13:19 .
   drwxrwsr-x. 121 magento_user apache  4096 Oct 30 13:19 ..
   -rw-rw-r--.   1 magento_user apache   372 Oct 30 13:19 composer.json
   drwxrwsr-x.   2 magento_user apache  4096 Oct 30 13:19 etc
   -rw-rw-r--.   1 magento_user apache 10376 Oct 30 13:19 LICENSE_AFL.txt
   -rw-rw-r--.   1 magento_user apache 10364 Oct 30 13:19 LICENSE.txt
   -rw-rw-r--.   1 magento_user apache  1157 Oct 30 13:19 README.md
   -rw-rw-r--.   1 magento_user apache   270 Oct 30 13:19 registration.php
   drwxrwsr-x.   3 magento_user apache  4096 Oct 30 13:19 Test
   ```

1. Aggiorna il database e lo schema di Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Pulisci la cache:

   ```bash
   bin/magento cache:clean
   ```

## Passaggio 2: verificare il modulo di esempio

Prima di continuare, verifica che il modulo di esempio sia registrato e abilitato.

1. Esegui il comando seguente:

   ```bash
   bin/magento module:status Magento_SampleMinimal
   ```

1. Assicurati che il modulo sia abilitato.

   ```terminal
   Module is enabled
   ```

>[!TIP]
>
>Se l&#39;output indica che `Module does not exist`, revisione [Passaggio 1](#step-1-get-a-sample-module) con attenzione. Verifica che il codice si trovi nella directory corretta. L’ortografia e la distinzione tra maiuscole e minuscole sono importanti; se qualcosa è diverso, il modulo non viene caricato. Inoltre, non dimenticare di eseguire `magento setup:upgrade`.

## Passaggio 3: creare una classe per eseguire cron

Questo passaggio mostra una classe semplice per creare un processo cron. La classe scrive solo una riga nel `cron_schedule` tabella che ne conferma la corretta configurazione.

Per creare una classe:

1. Creare una directory per la classe e passare a tale directory:

   ```bash
   mkdir /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron && cd /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron
   ```

1. È stato creato un file denominato `Test.php` in tale directory con i seguenti contenuti:

   ```php
   <?php
   namespace Magento\SampleMinimal\Cron;
   
   use Psr\Log\LoggerInterface;
   
   class Test {
       protected $logger;
   
       public function __construct(LoggerInterface $logger) {
           $this->logger = $logger;
       }
   
      /**
       * Write to system.log
       *
       * @return void
       */
       public function execute() {
           $this->logger->info('Cron Works');
       }
   }
   ```

## Passaggio 4: creare `crontab.xml`

Il `crontab.xml` file imposta una pianificazione per eseguire il codice cron personalizzato.

Crea `crontab.xml` come segue nella `/var/www/html/magento2/app/code/Magento/SampleMinimal/etc` directory:

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="default">
        <job name="custom_cronjob" instance="Magento\SampleMinimal\Cron\Test" method="execute">
            <schedule>* * * * *</schedule>
        </job>
    </group>
</config>
```

Il precedente `crontab.xml` esegue `Magento/SampleMinimal/Cron/Test.php` una volta al minuto, con conseguente aggiunta di una riga alla classe `cron_schedule` tabella.

Per poter configurare la pianificazione cron dall’amministratore, utilizza il percorso di configurazione del campo di configurazione del sistema.

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/crontab.xsd">
    <group id="default">
        <job name="custom_cronjob" instance="Magento\SampleMinimal\Cron\Test" method="execute">
            <config_path>system/config/path</config_path>
        </job>
    </group>
</config>
```

Dove: `system/config/path` è un percorso di configurazione del sistema definito in `etc/adminhtml/system.xml` di un modulo.

## Passaggio 5: compilazione e pulizia della cache

Compila il codice con questo comando:

```bash
bin/magento setup:di:compile
```

E pulisci la cache con questo comando:

```bash
bin/magento cache:clean
```

## Passaggio 6: verificare il processo cron

Questo passaggio mostra come verificare il processo cron personalizzato correttamente utilizzando una query SQL sul `cron_schedule` tabella di database.

Per verificare cron:

1. Esegui processi di Commerce cron:

   ```bash
   bin/magento cron:run
   ```

1. Inserisci il `magento cron:run` comando due o tre volte.

   La prima volta che si immette il comando, vengono messi in coda i processi, quindi vengono eseguiti i processi cron. Immetti il comando _almeno_ due volte.

1. Eseguire la query SQL `SELECT * from cron_schedule WHERE job_code like '%custom%'` come segue:

   1. Invio `mysql -u magento -p`
   1. Alla `mysql>` prompt, immetti `use magento;`
   1. Invio `SELECT * from cron_schedule WHERE job_code like '%custom%';`

      Il risultato deve essere simile al seguente:

      ```terminal
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      | schedule_id | job_code       | status  | messages | created_at        | scheduled_at        | executed_at         | finished_at     |
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      |        3670 | custom_cronjob | success | NULL     | 2016-11-02 09:38:03 | 2016-11-02 09:38:00 | 2016-11-02 09:39:03 | 2016-11-02 09:39:03 |
      |        3715 | custom_cronjob | success | NULL     | 2016-11-02 09:53:03 | 2016-11-02 09:53:00 | 2016-11-02 09:54:04 | 2016-11-02 09:54:04 |
      |        3758 | custom_cronjob | success | NULL     | 2016-11-02 10:09:03 | 2016-11-02 10:09:00 | 2016-11-02 10:10:03 | 2016-11-02 10:10:03 |
      |        3797 | custom_cronjob | success | NULL     | 2016-11-02 10:24:03 | 2016-11-02 10:24:00 | 2016-11-02 10:25:03 | 2016-11-02 10:25:03 |
      +-------------+----------------+---------+----------+---------------------+---------------------+---------------------+---------------------+
      ```

1. (Facoltativo) Verifica che i messaggi siano scritti nel registro di sistema di Commerce:

   ```bash
   cat /var/www/html/magento2/var/log/system.log
   ```

   Dovresti visualizzare una o più voci come le seguenti:

   ```terminal
   [2016-11-02 22:17:03] main.INFO: Cron Works [] []
   ```

   Questi messaggi provengono da `execute` metodo in `Test.php`:

   ```php
   public function execute() {
        $this->logger->info('Cron Works');
   ```

Se il comando SQL e il log di sistema non contengono voci, eseguire il comando `magento cron:run` comando ancora qualche volta e attendi. L&#39;aggiornamento del database può richiedere del tempo.

## Passaggio 7 (facoltativo): configurare un gruppo cron personalizzato

Questo passaggio mostra come impostare facoltativamente un gruppo cron personalizzato. È necessario impostare un gruppo cron personalizzato se si desidera che il processo cron personalizzato venga eseguito con una pianificazione diversa rispetto agli altri processi cron (in genere, una volta al minuto) o se si desidera che vengano eseguiti più processi cron personalizzati con impostazioni diverse.

Per impostare un gruppo cron personalizzato:

1. Apri `crontab.xml` in un editor di testo.
1. Cambia `<group id="default">` a `<group id="custom_crongroup">`
1. Esci dall’editor di testo.
1. Crea `/var/www/html/magento2/app/code/Magento/SampleMinimal/etc/cron_groups.xml` con il seguente contenuto:

   ```xml
   <?xml version="1.0"?>
   <config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:module:Magento_Cron:etc/cron_groups.xsd">
       <group id="custom_crongroup">
           <schedule_generate_every>1</schedule_generate_every>
           <schedule_ahead_for>4</schedule_ahead_for>
           <schedule_lifetime>2</schedule_lifetime>
           <history_cleanup_every>10</history_cleanup_every>
           <history_success_lifetime>60</history_success_lifetime>
           <history_failure_lifetime>600</history_failure_lifetime>
           <use_separate_process>1</use_separate_process>
       </group>
   </config>
   ```

Per una descrizione del significato delle opzioni, vedi [Personalizzazione del riferimento crons](custom-cron-reference.md).

## Passaggio 8: verificare il gruppo cron personalizzato

Questo _facoltativo_ Questo passaggio mostra come verificare il gruppo cron personalizzato utilizzando l’amministratore.

Per verificare il gruppo cron personalizzato:

1. Esegui processi di Commerce cron per il gruppo personalizzato:

   ```bash
   php /var/www/html/magento2/bin/magento cron:run --group="custom_crongroup"
   ```

   Esegui il comando almeno due volte.

1. Pulisci la cache:

   ```bash
   php /var/www/html/magento2/bin/magento cache:clean
   ```

1. Accedi all’amministratore come amministratore.
1. Clic **Negozi** > **Impostazioni** > **Configurazione** > **Avanzate** > **Sistema**.
1. Nel riquadro di destra, espandere **Cron**.

   Il gruppo cron viene visualizzato come segue:

   ![Gruppo cron personalizzato](../../assets/configuration/cron-group.png)

<!-- link definitions -->

[git-ssh]: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account
[samples]: https://github.com/magento/magento2-samples
