---
title: Guida all’installazione
description: Utilizza questa guida per installare  [!DNL Site-Wide Analysis Tool]  per il tuo sito Web
exl-id: ba36dc74-806d-49c5-b4d1-ba53ed4076fb
feature: Configuration, Install
source-git-commit: 16feb8ec7ecc88a6ef03a769d45b1a3a2fe88d97
workflow-type: tm+mt
source-wordcount: '1136'
ht-degree: 0%

---

# Guida all’installazione

>[!IMPORTANT]
>
>A decorrere dal 23 aprile 2024, le autorizzazioni di [!DNL Site-Wide Analysis Tool] verranno rimosse per tutti i clienti Adobe Commerce on-premise.

[!DNL Site-Wide Analysis Tool] fornisce monitoraggio delle prestazioni in tempo reale, report e raccomandazioni 24 ore su 24, 7 giorni su 7 per garantire la sicurezza e l&#39;operabilità di Adobe Commerce nelle installazioni dell&#39;infrastruttura cloud. Fornisce inoltre informazioni dettagliate sulle patch disponibili e installate, sulle estensioni di terze parti e sull’installazione di Adobe Commerce.

>[!INFO]
>
>Scopri [come abilitare](../site-wide-analysis-tool/access.md) [!DNL Site-Wide Analysis Tool] e generare rapporti.

Se hai installato Adobe Commerce on-premise, installa un agente nell’infrastruttura per utilizzare lo strumento. Non è necessario installare l’agente su Adobe Commerce nei progetti di infrastruttura cloud.

## Agente

L&#39;agente [!DNL Site-Wide Analysis Tool] consente di utilizzare [!DNL Site-Wide Analysis Tool] per le installazioni locali di Adobe Commerce.

L&#39;agente [!DNL Site-Wide Analysis Tool] raccoglie dati applicativi e aziendali, li analizza e fornisce ulteriori informazioni sull&#39;integrità dell&#39;installazione per migliorare l&#39;esperienza del cliente. Monitora l&#39;applicazione e consente di identificare le prestazioni, la sicurezza, la disponibilità e i problemi dell&#39;applicazione.

La procedura per l&#39;installazione dell&#39;agente è la seguente:

1. Verificare i requisiti di sistema.

1. Configurare le chiavi API nell&#39;estensione [!UICONTROL Commerce Services Connector].

1. Installa l’agente.

1. Esegui l’agente.

>[!INFO]
>
>L&#39;agente supporta installazioni Adobe Commerce a più nodi. Installa e configura l’agente su ciascun nodo.

## Requisiti di sistema

Prima di installare l&#39;agente, l&#39;infrastruttura locale deve soddisfare i seguenti requisiti:

- Sistemi operativi

   - [!DNL Linux x86-64] distribuzioni, ad esempio [!DNL Red Hat® Enterprise Linux (RHEL)], [!DNL CentOS], [!DNL Ubuntu], [!DNL Debian] e simili

  >[!IMPORTANT]
  >
  >Adobe Commerce non è supportato in [!DNL Microsoft Windows] o [!DNL macOS].

- Adobe Commerce 2.4.5-p1 o versione successiva (a causa della dipendenza del connettore di servizio)

- [!DNL Commerce Services Connector extension]

- CLI PHP

- Utilità Bash/shell

   - `php`

   - `wget`

   - `awk`

   - `nice`

   - `grep`

   - `openssl`

## [!DNL Commerce Services Connector]

L&#39;agente richiede che l&#39;estensione [[!DNL Commerce Services Connector]](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html?lang=it) sia installata nel sistema e [configurata](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html?lang=it) con chiavi API. Per verificare che l’estensione sia installata, esegui il seguente comando:

```bash
bin/magento module:status Magento_ServicesId
```

Se hai installato l&#39;estensione e l&#39;hai configurata utilizzando una chiave API esistente per un servizio diverso, **DEVI rigenerare la chiave API** e aggiornarla nell&#39;amministratore Adobe Commerce per l&#39;agente.

1. Imposta il tuo sito Web in [modalità di manutenzione](../../installation/tutorials/maintenance-mode.md).

1. Accedi a [account.magento.com](https://account.magento.com/customer/account/login?_ga=2.164207871.117144580.1649172612-1623400270.1640858671).

   >[!NOTE]
   >
   > In caso di problemi durante l&#39;accesso all&#39;account, vedere [Impossibile accedere al supporto Adobe Commerce o all&#39;account cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html?lang=it) per assistenza nella risoluzione dei problemi.

1. Fare clic su **[!UICONTROL API Portal]**.

1. Fai clic su **[!UICONTROL Delete]** accanto alla chiave API esistente.

1. [Configura](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html?lang=it) una nuova chiave API.

>[!IMPORTANT]
>
> Se si generano nuove chiavi nel portale API, aggiornare immediatamente le chiavi API in [!DNL Admin configuration]. Se si generano nuove chiavi e non si aggiornano le chiavi in [!DNL Admin], le estensioni SaaS non funzioneranno più e si perderanno dati importanti.

Se l&#39;estensione non è installata, attenersi alle istruzioni seguenti per installarla:

1. Aggiungi l&#39;estensione al file `composer.json` e installala.

   ```bash
   composer require magento/services-id
   ```

1. Abilita l&#39;estensione.

   ```bash
   bin/magento module:enable Magento_ServicesId
   ```

1. Aggiornare lo schema del database.

   ```bash
   bin/magento setup:upgrade
   ```

1. Cancella la cache.

   ```bash
   bin/magento cache:clean
   ```

1. [Configura le chiavi API](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html?lang=it) per connettere l&#39;estensione al sistema.

## Installare l’agente

È stato creato uno script [shell](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) per semplificare l&#39;installazione. È consigliabile utilizzare lo script della shell, ma se necessario è possibile seguire il metodo [installazione manuale](#manual).

>[!INFO]
>
>Dopo l’installazione, l’agente si aggiornerà automaticamente quando sarà disponibile una nuova versione.

### Con script

1. Scarica ed esegui lo script della shell.

   ```bash
   bash -c "$(wget -qO - https://raw.githubusercontent.com/magento-swat/install-agent-helpers/main/install.sh)"
   ```

   >[!TIP]
   >
   >È consigliabile installare l’agente all’esterno della directory principale del progetto Adobe Commerce.

1. Verificare l&#39;installazione.

   ```bash
   ./scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. Dopo aver scaricato e installato l&#39;agente, [configurarlo per l&#39;esecuzione](#run-the-agent) utilizzando uno dei metodi seguenti:

   - [Servizio](#service) (preferito se si dispone dell&#39;accesso root)

   - [Cron](#cron)

### Manuale {#manual}

Se non desideri utilizzare il nostro [script shell](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) per installare l&#39;agente, devi installarlo manualmente seguendo questi passaggi:

1. Creare una directory in cui scaricare l&#39;agente.

   >[!TIP]
   >
   >È consigliabile installare l’agente all’esterno della directory principale del progetto Adobe Commerce.

1. Scarica il file binario e decomprimi.

   >[!INFO]
   >
   >Per utilizzare [!DNL Site-Wide Analysis Tool], devi prima leggere e accettare le Condizioni d&#39;uso che vengono presentate quando accedi al dashboard da Adobe Commerce Admin.

   Per l&#39;architettura **AMD64**:

   1. Scarica l’archivio del modulo di avvio.

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-amd64.tar.gz
      ```

   1. Decomprimi l&#39;archivio del modulo di avvio.

      ```bash
      tar -xf launcher.linux-amd64.tar.gz
      ```

   Per l&#39;architettura **ARM64**:

   1. Scarica l’archivio del modulo di avvio.

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-arm64.tar.gz
      ```

   1. Decomprimi l&#39;archivio del modulo di avvio.

      ```bash
      tar -xf launcher.linux-arm64.tar.gz
      ```

1. *(Facoltativo)* Verificare la firma per il file di checksum.

   ```bash
   echo -n "LS0tLS1CRUdJTiBQVUJMSUMgS0VZLS0tLS0KTUlJQ0lqQU5CZ2txaGtpRzl3MEJBUUVGQUFPQ0FnOEFNSUlDQ2dLQ0FnRUE0M2FBTk1WRXR3eEZBdTd4TE91dQpacG5FTk9pV3Y2aXpLS29HendGRitMTzZXNEpOR3lRS1Jha0MxTXRsU283VnFPWnhUbHZSSFhQZWt6TG5vSHVHCmdmNEZKa3RPUEE2S3d6cjF4WFZ3RVg4MEFYU1JNYTFadzdyOThhenh0ZHdURVh3bU9GUXdDcjYramFOM3ErbUoKbkRlUWYzMThsclk0NVJxWHV1R294QzBhbWVoakRnTGxJUSs1d1kxR1NtRGRiaDFJOWZqMENVNkNzaFpsOXFtdgorelhjWGh4dlhmTUU4MUZsVUN1elRydHJFb1Bsc3dtVHN3ODNVY1lGNTFUak8zWWVlRno3RFRhRUhMUVVhUlBKClJtVzdxWE9kTGdRdGxIV0t3V2ppMFlrM0d0Ylc3NVBMQ2pGdEQzNytkVDFpTEtzYjFyR0VUYm42V3I0Nno4Z24KY1Q4cVFhS3pYRThoWjJPSDhSWjN1aFVpRHhZQUszdmdsYXJSdUFacmVYMVE2ZHdwYW9ZcERKa29XOXNjNXlkWApBTkJsYnBjVXhiYkpaWThLS0lRSURnTFdOckw3SVNxK2FnYlRXektFZEl0Ni9EZm1YUnJlUmlMbDlQMldvOFRyCnFxaHNHRlZoRHZlMFN6MjYyOU55amgwelloSmRUWXRpdldxbGl6VTdWbXBob1NrVnNqTGtwQXBiUUNtVm9vNkgKakJmdU1sY1JPeWI4TXJCMXZTNDJRU1MrNktkMytwR3JyVnh0akNWaWwyekhSSTRMRGwrVzUwR1B6LzFkeEw2TgprZktZWjVhNUdCZm00aUNlaWVNa3lBT2lKTkxNa1cvcTdwM200ejdUQjJnbWtldm1aU3Z5MnVMNGJLYlRoYXRlCm9sdlpFd253WWRxaktkcVkrOVM1UlNVQ0F3RUFBUT09Ci0tLS0tRU5EIFBVQkxJQyBLRVktLS0tLQ==" | base64 -d > release.pub
   ```

   ```bash
   openssl dgst -sha256 -verify release.pub -signature launcher.sha256 launcher.checksum
   ```

1. *(facoltativo)* Verificare il checksum.

   ```bash
   shasum -a 512 -c launcher.checksum
   ```

1. Creare il file `config.yaml` con il seguente contenuto.

   ```yaml
   project:
     appname: "Acme Inc" # Company or site name that you provided when installing the agent
   application:
     phppath: php # Path to your PHP CLI interpreter (usually /usr/bin/php)
     magentopath: /var/www/html/example.com # Root directory where your Adobe Commerce application is installed (usually /var/www/html)
     checkregistrypath: /path/to/swat-agent/tmp # Temporary directory for the agent (usually /usr/local/swat-agent/tmp)
     issandbox: false # Enabling sandbox mode to use the agent on staging environment (true or false)
     database:
       user: your-adobe-commerce-db-username # Database user for your Adobe Commerce installation
       password: your-password # Database password for the specified user for your Adobe Commerce installation
       host: 127.0.0.1 # Database host for your Adobe Commerce installation
       dbname: your-adobe-commerce-db-name # Database name for your Adobe Commerce installation
       port: 3306 # Database port for your Adobe Commerce installation (usually 3306)
       tableprefix: # Table Prefix for your Adobe Commerce installation (default value: empty)
    enableautoupgrade: true # Enables automatic upgrade (restart required after an upgrade; agent does not check for upgrades if the option is disabled; true or false)
    runchecksonstart: true # Collect data on the first run (Usually 1)
    loglevel: error # Determines what events are logged based on severity (usually error)
   ```

1. Verificare l&#39;installazione.

   ```bash
   scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. Dopo aver scaricato e installato l&#39;agente, è necessario [configurarlo per l&#39;esecuzione](#run-the-agent) utilizzando uno dei metodi seguenti:

   - [Servizio](#service) (preferito se si dispone dell&#39;accesso root)

   - [Cron](#cron)

## Eseguire l’agente {#run-the-agent}

È consigliabile configurare l’agente in modo che venga eseguito come servizio. Se disponi di un accesso limitato all&#39;infrastruttura e non disponi delle autorizzazioni root, devi invece utilizzare [cron](#cron).

### Servizio {#service}

1. Creare un file di unità di sistema `(/etc/systemd/system/scheduler.service)` con la seguente configurazione (sostituire `<filesystemowner>` con l&#39;utente UNIX® proprietario della directory in cui sono installati l&#39;agente e il software Adobe Commerce). Se l&#39;agente è stato scaricato come utente root, modificare la directory e il proprietario dei file nidificati.

   ```config
   [Unit]
   Wants=network.target
   After=network.target
   
   [Service]
   Type=simple
   User=<filesystemowner>
   ExecStart=/path/to/agent/scheduler
   Restart=always
   RestartSec=3
   
   [Install]
   WantedBy=multi-user.target
   ```

1. Avvia il servizio.

   ```bash
   systemctl daemon-reload
   ```

   ```bash
   systemctl start scheduler
   ```

   ```bash
   systemctl enable scheduler
   ```

1. Verifica che il servizio sia in esecuzione.

   ```bash
   journalctl -u scheduler | grep "Application is going to update" | tail -1 && echo "Agent is successfully installed"
   ```

### Cron {#cron}

Se non si dispone delle autorizzazioni radice o non si dispone delle autorizzazioni necessarie per configurare un servizio come radice, è possibile utilizzare cron.

Aggiorna la pianificazione cron:

```bash
( crontab -l ; echo "* * * * * flock -n /tmp/swat-agent.lockfile -c '/path/to/agent/scheduler' >> /path/to/agent/errors.log 2>&1" ) | sort - | uniq - | crontab -
```

## Disinstalla

Esegui i seguenti comandi per disinstallare il servizio dal sistema e rimuovere tutti i file generati:

1. Arresta il modulo di pianificazione.

   ```bash
   systemctl stop scheduler
   ```

1. Disattiva la pianificazione.

   ```bash
   systemctl disable scheduler
   ```

1. Rimuovere il file di unità `systemd` del servizio di pianificazione.

   ```bash
   rm /etc/systemd/system/scheduler.service
   ```

1. Ricarica la configurazione del gestore `systemd`.

   ```bash
   systemctl daemon-reload
   ```

1. Reimpostare `systemd` unità da uno stato non riuscito.

   ```bash
   systemctl reset-failed
   ```

1. Rimuovere la directory del servizio di pianificazione.

   ```bash
   rm -rf <CHECK_REGISTRY_PATH> #see SWAT_AGENT_APPLICATION_CHECK_REGISTRY_PATH in /etc/systemd/system/scheduler.service
   ```

1. Rimuovi il file binario dell&#39;utilità di pianificazione.

   ```bash
   rm /usr/local/bin/scheduler
   ```

Se invece hai configurato l’agente per l’esecuzione con cron, utilizza le seguenti istruzioni:

1. Rimuovi l’agente dall’elenco crontab.

   ```bash
   crontab -e
   ```

1. Arresta il processo in esecuzione.

   ```bash
   ps aux | grep scheduler
   ```

1. Rimuovere la directory in cui è stato installato l&#39;agente.

   ```bash
   rm -rf swat-agent
   ```

## Risoluzione dei problemi

### Chiavi di accesso non analizzate correttamente

Se le chiavi di accesso non vengono analizzate correttamente, è possibile che venga visualizzato il seguente errore:

```
ERRO[2022-10-10 00:01:41] Error while refreshing token: error while getting jwt from magento: invalid character 'M' looking for beginning of value
FATA[2022-12-10 20:38:44] bad http status from https://updater.supportinsights.adobe.com/linux-amd64.json: 403 Forbidden
```

Per risolvere l&#39;errore, effettuare le seguenti operazioni:

1. Eseguire un&#39;installazione [con script](#scripted), salvare l&#39;output ed esaminarlo per individuare eventuali errori.
1. Rivedi il file `config.yaml` generato e verifica che il percorso dell&#39;istanza Commerce e del PHP sia corretto.
1. Verificare che l&#39;utente che esegue il modulo di pianificazione si trovi nel gruppo Unix [proprietario del file system](../../installation/prerequisites/file-system/overview.md) o che sia lo stesso utente del proprietario del file system.
1. Verificare che le chiavi [Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html?lang=it) siano installate correttamente e provare ad aggiornarle per connettere l&#39;estensione al sistema.
1. [Disinstalla](#uninstall) l&#39;agente dopo l&#39;aggiornamento delle chiavi e la reinstallazione tramite lo [script di installazione](#scripted).
1. Eseguire il modulo di pianificazione e verificare se si riceve ancora lo stesso errore.
1. Se si riceve lo stesso errore, aumentare il livello di registro in `config.yaml` per eseguire il debug e aprire un ticket di supporto.

### *ERRORE.SIGFAULT*

Se durante l&#39;esecuzione del file binario viene visualizzato un errore *SIGFAULT*, è probabile che non venga eseguito come proprietario dei file di Adobe Commerce e dell&#39;agente.
Per risolvere il problema, verifica se tutti i file all’interno della directory dell’agente che hanno lo stesso utente del proprietario del file che hanno i file di Adobe Commerce e il file binario devono essere eseguiti anche sotto tale utente.
È possibile utilizzare il comando `chown` per cambiare il proprietario dei file e passare all&#39;utente appropriato.
Assicurati che il meccanismo di daemonizzazione (Cron o System.d) esegua il processo sotto l’utente appropriato.

>[!INFO]
>
>Consulta [Come accedere [!DNL Site-Wide Analysis Tool] e generare rapporti](../site-wide-analysis-tool/access.md).
