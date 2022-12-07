---
title: Guida all’installazione
description: "Utilizzare questa guida per l'installazione [!DNL Site-Wide Analysis Tool] per il tuo sito web"
source-git-commit: 5603d0feee6ec9dd5e8b534a0e64df274d7ab84d
workflow-type: tm+mt
source-wordcount: '1092'
ht-degree: 0%

---

# Guida all’installazione

La [!DNL Site-Wide Analysis Tool] fornisce monitoraggio delle prestazioni in tempo reale, report e raccomandazioni 24 ore su 24, 7 giorni su 7, per garantire la sicurezza e l&#39;operabilità di Adobe Commerce sulle installazioni dell&#39;infrastruttura cloud. Fornisce inoltre informazioni dettagliate sulle patch disponibili e installate, sulle estensioni di terze parti e sull’installazione di Adobe Commerce.

>[!INFO]
>
>Scopri [come abilitare](../site-wide-analysis-tool/access.md) la [!DNL Site-Wide Analysis Tool] e genera rapporti.

Se disponi di un’installazione on-premise di Adobe Commerce, installa un agente sull’infrastruttura per utilizzare lo strumento. Non è necessario installare l’agente su Adobe Commerce nei progetti di infrastruttura cloud.

## Agente

La [!DNL Site-Wide Analysis Tool] L&#39;agente consente di utilizzare il [!DNL Site-Wide Analysis Tool] per installazioni on-premise di Adobe Commerce.

La [!DNL Site-Wide Analysis Tool] L’agente raccoglie i dati aziendali e delle applicazioni, li analizza e fornisce ulteriori informazioni sullo stato dell’installazione in modo da migliorare l’esperienza del cliente. Controlla l&#39;applicazione e ti aiuta a identificare le prestazioni, la sicurezza, la disponibilità e i problemi delle applicazioni.

L&#39;installazione dell&#39;agente richiede i seguenti passaggi:

1. Verifica i requisiti di sistema.

1. Configurare le chiavi API nella [!UICONTROL Commerce Services Connector] estensione.

1. Installa l&#39;agente.

1. Esegui l&#39;agente.

>[!INFO]
>
>L’agente supporta installazioni Adobe Commerce a più nodi. Installa e configura l&#39;agente su ciascun nodo.

## Requisiti di sistema

Prima di installare l’agente, l’infrastruttura locale deve soddisfare i seguenti requisiti:

- Sistemi operativi

   - [!DNL Linux x86-64] le distribuzioni, quali [!DNL Red Hat® Enterprise Linux (RHEL)], [!DNL CentOS], [!DNL Ubuntu], [!DNL Debian]e simili
   >[!IMPORTANT]
   >
   >Adobe Commerce non è supportato su [!DNL Microsoft Windows] o [!DNL macOS].

- Adobe Commerce 2.4.1 o successivo

- [!DNL Commerce Services Connector extension]

- CLI PHP

- Utility Bash/shell

   - `php`

   - `wget`

   - `awk`

   - `nice`

   - `grep`

   - `openssl`

## [!DNL Commerce Services Connector]

L&#39;agente richiede l&#39; [[!DNL Commerce Services Connector]](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) estensione da installare nel sistema e [configurato](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) con le chiavi API. Per verificare che l&#39;estensione sia installata, esegui il comando seguente:

```bash
bin/magento module:status Magento_ServicesConnector
```

Se hai installato l’estensione e l’hai configurata utilizzando una chiave API esistente per un servizio diverso, **DEVE generare la chiave API** e aggiornalo nell’amministratore di Adobe Commerce per l’agente.

1. Inserisci il tuo sito web in [modalità di manutenzione](../../installation/tutorials/maintenance-mode.md).

1. Accedi a [account.magento.com](https://account.magento.com/customer/account/login?_ga=2.164207871.117144580.1649172612-1623400270.1640858671).

   >[!NOTE]
   >
   > In caso di problemi nell&#39;accesso all&#39;account, consulta [Impossibile accedere al supporto Adobe Commerce o all&#39;account cloud](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html) per informazioni sulla risoluzione dei problemi.

1. Clic **[!UICONTROL API Portal]**.

1. Fai clic su **[!UICONTROL Delete]** accanto alla chiave API esistente.

1. [Configura](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) una nuova chiave API.

>[!IMPORTANT]
>
> Se generi nuove chiavi nel portale API, aggiorna immediatamente le chiavi API nel [!DNL Admin configuration]. Se generi nuove chiavi e non aggiorni le chiavi nella [!DNL Admin], le estensioni SaaS non funzioneranno più e perderai dati preziosi.

Se l&#39;estensione non è installata, segui le istruzioni seguenti per installarla:

1. Aggiungi l&#39;estensione al `composer.json` e installalo.

   ```bash
   composer require magento/services-connector:1.*
   ```

1. Abilita l&#39;estensione .

   ```bash
   bin/magento module:enable Magento_ServicesConnector
   ```

1. Aggiornare lo schema del database.

   ```bash
   bin/magento setup:upgrade
   ```

1. [Configurare le chiavi API](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) per collegare l&#39;estensione al sistema.

## Installare l’agente

Abbiamo creato un [script shell](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) per semplificare l&#39;installazione. Si consiglia di utilizzare lo script shell, ma è possibile seguire la [installazione manuale](#manual) se necessario.

>[!INFO]
>
>Una volta installato l’agente, questo si aggiornerà automaticamente quando sarà disponibile una nuova versione.

### Scripting

1. Scarica ed esegui lo script della shell.

   ```bash
   bash -c "$(wget -qO - https://raw.githubusercontent.com/magento-swat/install-agent-helpers/main/install.sh)"
   ```

   >[!TIP]
   >
   >È consigliabile installare l’agente all’esterno della directory principale del progetto Adobe Commerce.

1. Verifica l’installazione.

   ```bash
   ./scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. Dopo aver scaricato e installato l&#39;agente, [configurarlo per l&#39;esecuzione](#run-the-agent) utilizzando uno dei seguenti metodi:

   - [Servizio](#service) (opzione preferita se si dispone dell&#39;accesso radice)

   - [Cron](#cron)

### Manuale {#manual}

Se non desideri usare la nostra [script shell](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) per installare l&#39;agente, devi installarlo manualmente seguendo questi passaggi:

1. Crea una directory in cui desideri scaricare l&#39;agente.

   >[!TIP]
   >
   >È consigliabile installare l’agente all’esterno della directory principale del progetto Adobe Commerce.

1. Scarica il file binario e decomprimi il pacchetto.

   >[!INFO]
   >
   >Per utilizzare [!DNL Site-Wide Analysis Tool], devi prima leggere e accettare i Termini d&#39;uso che vengono presentati quando accedi al dashboard dall&#39;amministratore di Adobe Commerce.

   Per **AMD64** architettura:

   1. Scarica l&#39;archivio del lanciatore.

      ```bash
      curl -O https://updater.swat.magento.com/launcher/launcher.linux-amd64.tar.gz
      ```

   1. Decomprimi l&#39;archivio del lanciatore.

      ```bash
      tar -xf launcher.linux-amd64.tar.gz
      ```
   Per **ARM64** architettura:

   1. Scarica l&#39;archivio del lanciatore.

      ```bash
      curl -O https://updater.swat.magento.com/launcher/launcher.linux-arm64.tar.gz
      ```

   1. Decomprimi l&#39;archivio del lanciatore.

      ```bash
      tar -xf launcher.linux-arm64.tar.gz
      ```


1. *(Facoltativo)* Verificare la firma del file checksum.

   ```bash
   echo -n "LS0tLS1CRUdJTiBQVUJMSUMgS0VZLS0tLS0KTUlJQ0lqQU5CZ2txaGtpRzl3MEJBUUVGQUFPQ0FnOEFNSUlDQ2dLQ0FnRUE0M2FBTk1WRXR3eEZBdTd4TE91dQpacG5FTk9pV3Y2aXpLS29HendGRitMTzZXNEpOR3lRS1Jha0MxTXRsU283VnFPWnhUbHZSSFhQZWt6TG5vSHVHCmdmNEZKa3RPUEE2S3d6cjF4WFZ3RVg4MEFYU1JNYTFadzdyOThhenh0ZHdURVh3bU9GUXdDcjYramFOM3ErbUoKbkRlUWYzMThsclk0NVJxWHV1R294QzBhbWVoakRnTGxJUSs1d1kxR1NtRGRiaDFJOWZqMENVNkNzaFpsOXFtdgorelhjWGh4dlhmTUU4MUZsVUN1elRydHJFb1Bsc3dtVHN3ODNVY1lGNTFUak8zWWVlRno3RFRhRUhMUVVhUlBKClJtVzdxWE9kTGdRdGxIV0t3V2ppMFlrM0d0Ylc3NVBMQ2pGdEQzNytkVDFpTEtzYjFyR0VUYm42V3I0Nno4Z24KY1Q4cVFhS3pYRThoWjJPSDhSWjN1aFVpRHhZQUszdmdsYXJSdUFacmVYMVE2ZHdwYW9ZcERKa29XOXNjNXlkWApBTkJsYnBjVXhiYkpaWThLS0lRSURnTFdOckw3SVNxK2FnYlRXektFZEl0Ni9EZm1YUnJlUmlMbDlQMldvOFRyCnFxaHNHRlZoRHZlMFN6MjYyOU55amgwelloSmRUWXRpdldxbGl6VTdWbXBob1NrVnNqTGtwQXBiUUNtVm9vNkgKakJmdU1sY1JPeWI4TXJCMXZTNDJRU1MrNktkMytwR3JyVnh0akNWaWwyekhSSTRMRGwrVzUwR1B6LzFkeEw2TgprZktZWjVhNUdCZm00aUNlaWVNa3lBT2lKTkxNa1cvcTdwM200ejdUQjJnbWtldm1aU3Z5MnVMNGJLYlRoYXRlCm9sdlpFd253WWRxaktkcVkrOVM1UlNVQ0F3RUFBUT09Ci0tLS0tRU5EIFBVQkxJQyBLRVktLS0tLQ==" | base64 -d > release.pub
   ```

   ```bash
   openssl dgst -sha256 -verify release.pub -signature launcher.sha256 launcher.checksum
   ```

1. *(Facoltativo)* Verifica il checksum.

   ```bash
   shasum -a 512 -c launcher.checksum
   ```

1. Crea il `config.yaml` con il seguente contenuto.

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

1. Verifica l’installazione.

   ```bash
   scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. Dopo aver scaricato e installato l&#39;agente, devi [configurarlo per l&#39;esecuzione](#run-the-agent) utilizzando uno dei seguenti metodi:

   - [Servizio](#service) (opzione preferita se si dispone dell&#39;accesso radice)

   - [Cron](#cron)

## Esegui l&#39;agente {#run-the-agent}

È consigliabile configurare l’agente per l’esecuzione come servizio. Se si dispone di un accesso limitato all&#39;infrastruttura e non si dispone delle autorizzazioni root, è necessario utilizzare [cron](#cron) invece.

### Servizio {#service}

1. Creare un file di unità di sistema `(/etc/systemd/system/scheduler.service)` con la seguente configurazione (sostituisci `<filesystemowner>` con l&#39;utente UNIX® proprietario della directory in cui sono installati l&#39;agente e il software Adobe Commerce). Se hai scaricato l’agente come utente principale, modifica la directory e il proprietario dei file nidificati.

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

Se non disponi di autorizzazioni root o non disponi di autorizzazioni per configurare un servizio come root, puoi utilizzare cron.

Aggiorna la pianificazione cron:

```bash
( crontab -l ; echo "* * * * * flock -n /tmp/swat-agent.lockfile -c '/path/to/agent/scheduler' >> /path/to/agent/errors.log 2>&1" ) | sort - | uniq - | crontab -
```

## Disinstalla

Esegui i seguenti comandi per disinstallare il servizio dal sistema e rimuovere tutti i file generati:

1. Interrompi lo scheduler.

   ```bash
   systemctl stop scheduler
   ```

1. Disattiva la pianificazione.

   ```bash
   systemctl disable scheduler
   ```

1. Rimuovi il servizio di pianificazione `systemd` file di unità.

   ```bash
   rm /etc/systemd/system/scheduler.service
   ```

1. Ricarica il `systemd` configurazione di gestione.

   ```bash
   systemctl daemon-reload
   ```

1. Reimposta qualsiasi `systemd` unità da uno stato non riuscito.

   ```bash
   systemctl reset-failed
   ```

1. Rimuovi la directory del servizio di pianificazione.

   ```bash
   rm -rf <CHECK_REGISTRY_PATH> #see SWAT_AGENT_APPLICATION_CHECK_REGISTRY_PATH in /etc/systemd/system/scheduler.service
   ```

1. Rimuovi il file binario di pianificazione.

   ```bash
   rm /usr/local/bin/scheduler
   ```

Se invece hai configurato l&#39;agente per l&#39;esecuzione con cron, utilizza le seguenti istruzioni:

1. Rimuovi l&#39;agente dall&#39;elenco crontab.

   ```bash
   crontab -e
   ```

1. Interrompi il processo in esecuzione.

   ```bash
   ps aux | grep scheduler
   ```

1. Rimuovi la directory in cui hai installato l&#39;agente.

   ```bash
   rm -rf swat-agent
   ```

## Ignorare il file di configurazione

È possibile sostituire i valori specificati nel file di configurazione durante l&#39;installazione utilizzando le variabili di ambiente. In questo modo viene mantenuta la compatibilità con le versioni precedenti dell’agente. Per i valori consigliati, consultare la tabella seguente:

| PROPRIETÀ | DESCRIZIONE |
| --- | --- |
| `SWAT_AGENT_APP_NAME` | Nome dell&#39;azienda o del sito fornito al momento dell&#39;installazione dell&#39;agente |
| `SWAT_AGENT_APPLICATION_PHP_PATH` | Percorso dell’interprete CLI PHP (di solito `/usr/bin/php`) |
| `SWAT_AGENT_APPLICATION_MAGENTO_PATH` | Directory principale in cui è installata l’applicazione Adobe Commerce (in genere `/var/www/html`) |
| `SWAT_AGENT_APPLICATION_DB_USER` | Utente del database per l&#39;installazione di Adobe Commerce |
| `SWAT_AGENT_APPLICATION_DB_PASSWORD` | Password del database per l&#39;utente specificato per l&#39;installazione di Adobe Commerce |
| `SWAT_AGENT_APPLICATION_DB_HOST` | Host di database per l&#39;installazione di Adobe Commerce |
| `SWAT_AGENT_APPLICATION_DB_NAME` | Nome del database per l&#39;installazione di Adobe Commerce |
| `SWAT_AGENT_APPLICATION_DB_PORT` | Porta di database per l&#39;installazione di Adobe Commerce (in genere `3306`) |
| `SWAT_AGENT_APPLICATION_DB_TABLE_PREFIX` | Prefisso tabella per l’installazione di Adobe Commerce (valore predefinito: `empty`) |
| `SWAT_AGENT_APPLICATION_DB_REPLICATED` | Se l’installazione di Adobe Commerce dispone di un’istanza di database secondaria (in genere `false`) |
| `SWAT_AGENT_APPLICATION_CHECK_REGISTRY_PATH` | Directory temporanea per l&#39;agente (in genere `/usr/local/swat-agent/tmp`) |
| `SWAT_AGENT_RUN_CHECKS_ON_START` | Raccogliere dati sulla prima esecuzione (in genere `1`) |
| `SWAT_AGENT_LOG_LEVEL` | Determina gli eventi registrati in base alla gravità (in genere `error`) |
| `SWAT_AGENT_ENABLE_AUTO_UPGRADE` | Abilita l&#39;aggiornamento automatico (riavvio richiesto dopo un aggiornamento; l&#39;agente non controlla gli aggiornamenti se l&#39;opzione è disabilitata; `true` o `false`) |
| `SWAT_AGENT_IS_SANDBOX=false` | Abilitazione della modalità sandbox per utilizzare l’agente nell’ambiente di gestione temporanea |

>[!INFO]
>
>Vedi [Accesso [!DNL Site-Wide Analysis Tool] e genera rapporti](../site-wide-analysis-tool/access.md).
