---
title: Configurare un lavoro cron personalizzato e un gruppo cron (esercitazione)
description: Utilizza questa esercitazione dettagliata per creare un lavoro cron personalizzato.
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '822'
ht-degree: 0%

---


# Configurare un processo cron personalizzato

Questa esercitazione dettagliata mostra come creare un lavoro cron personalizzato ed eventualmente un gruppo cron in un modulo di esempio. Puoi utilizzare un modulo già in tuo possesso o puoi utilizzare un modulo di esempio dal nostro [`magento2-samples` archivio][samples].

L’esecuzione del processo cron comporta l’aggiunta di una riga al `cron_schedule` tabella con il nome del cron job, `custom_cron`.

Inoltre, viene illustrato come creare facoltativamente un gruppo cron, che è possibile utilizzare per eseguire lavori cron personalizzati con impostazioni diverse dalle impostazioni predefinite dell’applicazione Commerce.

In questa esercitazione si assume quanto segue:

- L’applicazione Commerce è installata in `/var/www/html/magento2`
- Il nome utente e la password del database Commerce sono entrambi `magento`
- Esegui tutte le azioni come [proprietario del file system](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html)

## Passaggio 1: Ottieni un modulo di esempio

Per impostare un processo cron personalizzato, è necessario un modulo di esempio. Suggeriamo la `magento-module-minimal` modulo .

Se disponi già di un modulo di esempio, puoi utilizzarlo; salta questo passaggio e il passaggio successivo e continua con il passaggio 3: Crea una classe da eseguire cron.

**Per ottenere un modulo di esempio**:

1. Accedi al tuo server Commerce come o passa a [proprietario del file system](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Passa a una directory che non si trova nella directory principale dell’applicazione Commerce (ad esempio, nella directory principale).
1. Clona il [`magento2-samples` archivio][samples].

   ```bash
   git clone git@github.com:magento/magento2-samples.git
   ```

   Se il comando non riesce con l&#39;errore `Permission denied (publickey).`, devi [aggiungi la tua chiave pubblica SSH a GitHub.com][git-ssh].

1. Crea una directory in cui copiare il codice di esempio:

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

   Dovresti vedere il seguente risultato:

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

1. Aggiorna il database e lo schema Commerce:

   ```bash
   bin/magento setup:upgrade
   ```

1. Pulisci la cache:

   ```bash
   bin/magento cache:clean
   ```

## Passaggio 2: Verifica il modulo di esempio

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
>Se l&#39;output indica che la `Module does not exist`, revisione [Passaggio 1](#step-1-get-a-sample-module) con attenzione. Assicurati che il codice sia nella directory corretta. Controllo ortografia e caso sono importanti; se qualcosa è diverso, il modulo non verrà caricato. Inoltre, non dimenticare di eseguire `magento setup:upgrade`.

## Passaggio 3: Crea una classe per eseguire cron

Questo passaggio mostra una classe semplice per creare un lavoro cron. La classe scrive solo una riga nel `cron_schedule` tabella che conferma la configurazione completata.

Per creare una classe:

1. Crea una directory per la classe e passa a tale directory:

   ```bash
   mkdir /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron && cd /var/www/html/magento2/app/code/Magento/SampleMinimal/Cron
   ```

1. Creazione di un file denominato `Test.php` in tale directory con il seguente contenuto:

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

## Passaggio 4: Crea `crontab.xml`

La `crontab.xml` file imposta una pianificazione per eseguire il codice cron personalizzato.

Crea `crontab.xml` come segue `/var/www/html/magento2/app/code/Magento/SampleMinimal/etc` directory:

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

Il `crontab.xml` esegue `Magento/SampleMinimal/Cron/Test.php` una volta al minuto, con conseguente aggiunta di una riga al `cron_schedule` tabella.

Per rendere la pianificazione cron configurabile dall&#39;amministratore, utilizza il percorso di configurazione del campo di configurazione del sistema.

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

Dove `system/config/path` è un percorso di configurazione del sistema definito in `etc/adminhtml/system.xml` di un modulo.

## Passaggio 5: Compili e pulizia della cache

Compila il codice con questo comando:

```bash
bin/magento setup:di:compile
```

E pulisci la cache con questo comando:

```bash
bin/magento cache:clean
```

## Passaggio 6: Verifica il lavoro cron

Questo passaggio mostra come verificare il processo cron personalizzato utilizzando correttamente una query SQL nella `cron_schedule` tabella del database.

Per verificare cron:

1. Esegui processi cron Commerce:

   ```bash
   bin/magento cron:run
   ```

1. Inserisci il `magento cron:run` comando due o tre volte.

   La prima volta che si immette il comando, mette in coda i lavori; successivamente, i lavori cron vengono eseguiti. Immettere il comando _almeno_ due volte.

1. Esegui la query SQL `SELECT * from cron_schedule WHERE job_code like '%custom%'` come segue:

   1. Invio `mysql -u magento -p`
   1. Alla `mysql>` prompt, immettere `use magento;`
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

   Dovresti visualizzare una o più voci come segue:

   ```terminal
   [2016-11-02 22:17:03] main.INFO: Cron Works [] []
   ```

   Questi messaggi provengono dal `execute` metodo in `Test.php`:

   ```php
   public function execute() {
        $this->logger->info('Cron Works');
   ```

Se il comando SQL e il registro di sistema non contengono voci, eseguire il `magento cron:run` comando ancora qualche volta e attendi. L&#39;aggiornamento del database può richiedere del tempo.

## Passaggio 7 (facoltativo): Imposta un gruppo cron personalizzato

Questo passaggio mostra come impostare facoltativamente un gruppo di cron personalizzato. È necessario impostare un gruppo cron personalizzato se si desidera che il processo cron personalizzato venga eseguito su una pianificazione diversa rispetto ad altri lavori cron (in genere, una volta al minuto) o se si desidera che diversi lavori cron personalizzati vengano eseguiti con impostazioni diverse.

Per impostare un gruppo cron personalizzato:

1. Apri `crontab.xml` in un editor di testo.
1. Modifica `<group id="default">` a `<group id="custom_crongroup">`
1. Esci dall’editor di testo.
1. Crea `/var/www/html/magento2/app/code/Magento/SampleMinimal/etc/cron_groups.xml` con i seguenti contenuti:

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

Per una descrizione del significato delle opzioni, vedi [Personalizzazione del riferimento cronologico](custom-cron-reference.md).

## Passaggio 8: Verifica il gruppo cron personalizzato

Questo _facoltativo_ questo passaggio mostra come verificare il gruppo cron personalizzato utilizzando l’amministratore.

Per verificare il gruppo cron personalizzato:

1. Esegui processi Commerce cron per il gruppo personalizzato:

   ```bash
   php /var/www/html/magento2/bin/magento cron:run --group="custom_crongroup"
   ```

   Esegui il comando almeno due volte.

1. Pulisci la cache:

   ```bash
   php /var/www/html/magento2/bin/magento cache:clean
   ```

1. Accedi all’amministratore come amministratore.
1. Fai clic su **Negozi** > **Impostazioni** > **Configurazione** > **Avanzate** > **Sistema**.
1. Nel riquadro a destra, espandi **Cron**.

   Il gruppo cron viene visualizzato come segue:

   ![Gruppo cron personalizzato](../../assets/configuration/cron-group.png)

<!-- link definitions -->

[git-ssh]: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account
[samples]: https://github.com/magento/magento2-samples
