---
title: Installazione rapida on-premise
description: Per installare Adobe Commerce nell’infrastruttura di tua proprietà, segui la procedura riportata di seguito.
exl-id: a93476e8-2b30-461a-91df-e73eb1a14d3c
source-git-commit: 60db3da9154e76032c88d687b6b6e22d7b81f9ae
workflow-type: tm+mt
source-wordcount: '957'
ht-degree: 0%

---

# Installazione rapida on-premise

Le istruzioni presenti in questa pagina descrivono come installare Adobe Commerce su un’infrastruttura con hosting autonomo. Per informazioni sull&#39;aggiornamento di un&#39;installazione esistente, vedere la [_Guida all&#39;aggiornamento_](../upgrade/overview.md).

Adobe utilizza [Compositore](https://getcomposer.org/) per gestire i componenti Adobe Commerce e le relative dipendenze. L’utilizzo di Composer per ottenere il metapackage di Adobe Commerce offre i seguenti vantaggi:

- Riutilizzare le librerie di terze parti senza unirle al codice sorgente
- Ridurre i conflitti di estensione e i problemi di compatibilità utilizzando un’architettura basata su componenti con una solida gestione delle dipendenze
- Rispetta gli standard [PHP-Framework Interoperability Group (FIG)](https://www.php-fig.org/)
- Riconfezionamento di Magento Open Source con altri componenti
- Utilizzare il software Adobe Commerce in un ambiente di produzione

>[!NOTE]
>
>Gli sviluppatori che contribuiscono a Magento Open Source devono utilizzare il metodo di installazione [basato su Git](https://developer.adobe.com/commerce/contributor/guides/install/).

## Prerequisiti

Prima di continuare, è necessario effettuare le seguenti operazioni:

- Completa tutte le [attività preliminari](system-requirements.md).
- [Installa Compositore](https://getcomposer.org/download/).
- Ottieni [chiavi di autenticazione](prerequisites/authentication-keys.md) nell&#39;archivio del Compositore Adobe Commerce.

## Accedi come proprietario del file system

Per informazioni su proprietà, autorizzazioni e proprietario del file system, vedere l&#39;argomento [Panoramica sulla proprietà e sulle autorizzazioni](prerequisites/file-system/overview.md).

Per passare al proprietario del file system:

1. Accedere al server applicazioni come utente con autorizzazioni di scrittura nel file system o passare a tale utente.

   Se si utilizza la shell bash, è possibile utilizzare la sintassi seguente per passare al proprietario del file system e immettere contemporaneamente il comando:

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   Se il proprietario del file system non consente l&#39;accesso, è possibile effettuare le seguenti operazioni:

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. Per eseguire i comandi CLI da qualsiasi directory, aggiungere `<app_root>/bin` al sistema `PATH`.

   Poiché le shell hanno sintassi diverse, consultare un riferimento come [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   Shell di base di esempio per CentOS:

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   Facoltativamente, è possibile eseguire i comandi nei modi seguenti:

   - `cd <app_root>/bin` ed eseguirli come `./magento <command name>`
   - `app_root>/bin/magento <command name>`
   - `<app_root>` è una sottodirectory della directory dei documenti del server Web

## Ottieni il metapacchetto

Per ottenere il metapacchetto Adobe Commerce:

1. Accedi al server applicazioni come [proprietario del file system](prerequisites/file-system/overview.md) o passa a tale proprietario.
1. Passare alla directory principale dei documenti del server Web o a una directory configurata come directory principale dei documenti host virtuale.
1. Creare un progetto Compositore utilizzando un metapacchetto Commerce.

   **Magento Open Source**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Quando richiesto, immettere le chiavi di autenticazione. Le chiavi pubbliche e private vengono create e configurate da [Commerce Marketplace - Chiavi di accesso](https://commercemarketplace.adobe.com/customer/account/login/). Per `[!UICONTROL username]`, copia e incolla il valore della chiave pubblica. Per `[!UICONTROL password]`, copia e incolla il valore della chiave privata.

   >[!NOTE]
   >
   > Se si utilizza un file Composer `[auth.json](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/authentication-keys)` o una variabile di ambiente configurata con le chiavi di autenticazione di Commerce, non viene richiesto di immettere le chiavi di autenticazione.

   Se si verificano errori, ad esempio `Could not find package...` o `...no matching package found`, verificare che il comando non contenga errori di battitura. Se riscontri ancora errori, potresti non essere autorizzato a scaricare Adobe Commerce. Contatta il [Supporto Adobe Commerce](https://support.magento.com/hc/en-us) per assistenza.

   Per ulteriori informazioni sugli errori, vedere [Risoluzione dei problemi](https://support.magento.com/hc/en-us/articles/360033818091).

### Esempio: versione secondaria

Le versioni secondarie contengono nuove funzioni, correzioni di qualità e correzioni di sicurezza. Utilizza Composer per specificare una versione secondaria. Ad esempio, per specificare il metapackage di Adobe Commerce 2.4.6:

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6 <install-directory-name>
```

### Esempio: patch di qualità

Le patch di qualità contengono principalmente _e_ correzioni di sicurezza funzionali. Tuttavia, a volte possono anche contenere nuove funzioni compatibili con le versioni precedenti. Utilizza Composer per scaricare una patch di qualità. Ad esempio, per specificare il metapackage di Adobe Commerce 2.4.6:

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6 <install-directory-name>
```

### Esempio: patch di sicurezza

Le patch di sicurezza contengono solo correzioni di sicurezza. Sono progettati per rendere il processo di aggiornamento più rapido e semplice.

Le patch di sicurezza utilizzano la convenzione di denominazione del Compositore `2.4.6-px`. Utilizzate Composer per specificare una patch. Ad esempio, per scaricare il metapacchetto Adobe Commerce 2.4.6-p1:

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6-p1 <install-directory-name>
```

## Imposta autorizzazioni file

Prima di installare Adobe Commerce, è necessario impostare le autorizzazioni di lettura e scrittura per il gruppo di server Web. Ciò è necessario affinché la riga di comando possa scrivere file nel file system.

```bash
cd /var/www/html/<magento install directory>
find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
chown -R :www-data . # Ubuntu
chmod u+x bin/magento
```

## Installare l’applicazione

Per installare Adobe Commerce è necessario utilizzare la riga di comando.

In questo esempio si presuppone che la directory di installazione sia denominata `magento2ee`, che `db-host` si trovi nello stesso computer (`localhost`) e che `db-name`, `db-user` e `db-password` siano tutti `magento`:

```bash
bin/magento setup:install \
--base-url=http://localhost/magento2ee \
--db-host=localhost \
--db-name=magento \
--db-user=magento \
--db-password=magento \
--admin-firstname=admin \
--admin-lastname=admin \
--admin-email=admin@admin.com \
--admin-user=admin \
--admin-password=admin123 \
--language=en_US \
--currency=USD \
--timezone=America/Chicago \
--use-rewrites=1 \
--search-engine=opensearch \
--opensearch-host=os-host.example.com \
--opensearch-port=9200 \
--opensearch-index-prefix=magento2 \
--opensearch-timeout=15
```

>[!TIP]
>
>È possibile personalizzare l&#39;URI amministratore con l&#39;opzione `--backend-frontname`. Tuttavia, Adobe consiglia di omettere questa opzione e consentire al comando di installazione di generare automaticamente un URI casuale. Un URI casuale è più difficile da sfruttare per gli hacker o per il software dannoso. Al termine dell’installazione, l’URI viene visualizzato nella console.

>[!TIP]
>
>Per una descrizione completa delle opzioni di installazione CLI, vedere [Installare l&#39;applicazione dalla riga di comando](advanced.md).

## Riepilogo comandi

Per visualizzare un elenco completo dei comandi, immettere:

```bash
bin/magento list
```

Per ottenere informazioni su un comando specifico, immettere:

```bash
bin/magento help <command>
```

Ad esempio:

```bash
bin/magento help setup:install
```

```bash
bin/magento help cache:enable
```

Nella tabella seguente vengono riepilogati i comandi disponibili. I comandi vengono visualizzati solo in forma di riepilogo. Per ulteriori informazioni su un comando, fare clic sul collegamento nella colonna Comando.

| Comando | Descrizione | Prerequisiti |
|--- |--- |--- |
| `magento setup:install` | Installa l&#39;applicazione | Nessuno |
| `magento setup:uninstall` | Rimuove l&#39;applicazione. | Applicazione installata |
| `magento setup:upgrade` | Aggiorna l&#39;applicazione. | Configurazione della distribuzione |
| `magento maintenance:{enable/disable}` | Attiva o disattiva la modalità di manutenzione (in modalità di manutenzione, solo gli indirizzi IP esenti possono accedere all’Admin o alla vetrina). | Applicazione installata |
| `magento setup:config:set` | Crea o aggiorna la configurazione di distribuzione. | Nessuno |
| `magento module:{enable/disable}` | Attiva o disattiva i moduli. | Nessuno |
| `magento setup:store-config:set` | Imposta le opzioni relative alla vetrina, ad esempio URL di base, lingua, fuso orario. | Configurazione della distribuzione |
| `magento setup:db-schema:upgrade` | Aggiorna lo schema del database. | Configurazione della distribuzione |
| `magento setup:db-data:upgrade` | Aggiorna i dati del database. | Configurazione della distribuzione |
| `magento setup:db:status` | Controlla se il database è aggiornato con il codice. | Configurazione della distribuzione |
| `magento admin:user:create` | Crea un utente amministratore. | Puoi creare utenti per:<br><br>Configurazione della distribuzione<br><br>Abilitare almeno i moduli `Magento_User` e `Magento_Authorization`<br><br>Database (il modo più semplice è utilizzare `bin/magento setup:upgrade`) |
| `magento list` | Elenca tutti i comandi disponibili. | Nessuno |
| `magento help` | Visualizza la Guida per il comando specificato. | Nessuno |

### Argomenti comuni

I seguenti argomenti sono comuni a tutti i comandi. Questi comandi possono essere eseguiti prima o dopo l&#39;installazione dell&#39;applicazione:

| Versione lunga | Versione breve | Significato |
|--- |--- |--- |
| `--help` | `-h` | Visualizzare la Guida per qualsiasi comando. Ad esempio, `./magento help setup:install` o `./magento help setup:config:set`. |
| `--quiet` | `-q` | Modalità silenziosa; nessuna uscita. |
| `--no-interaction` | `-n` | Nessuna domanda interattiva. |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | Livello di dettaglio. `--verbose=3` o `-vvv`, ad esempio, visualizza il livello di dettaglio del debug, ovvero l&#39;output più dettagliato. Il valore predefinito è `--verbose=1` o `-v`. |
| `--version` | `-V` | Visualizza questa versione dell&#39;applicazione |
| `--ansi` | n/d | Forza uscita ANSI |
| `--no-ansi` | n/d | Disattiva output ANSI |

>[!NOTE]
>
>Congratulazioni! L&#39;installazione rapida è stata completata. Hai bisogno di assistenza più avanzata? Consulta la [Guida all&#39;installazione avanzata](advanced.md).
