---
title: Installazione rapida in locale
description: Segui questi passaggi per installare Adobe Commerce o Magento Open Source sull’infrastruttura di tua proprietà.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '996'
ht-degree: 0%

---


# Installazione rapida in locale

Usiamo [Compositore](https://getcomposer.org/) per gestire i componenti Adobe Commerce e Magenti Open Source e le loro dipendenze. Utilizzo del Compositore per ottenere Adobe Commerce e il Magento Open Source [metapackage](https://glossary.magento.com/metapackage) offre i seguenti vantaggi:

- Riutilizzare le librerie di terze parti senza raggrupparle con il codice sorgente
- Riduci i conflitti di estensione e i problemi di compatibilità utilizzando un&#39;architettura basata su componenti con una gestione affidabile delle dipendenze
- Aggiungi a [Gruppo di interoperabilità PHP-Framework (FIG)](https://www.php-fig.org/) standard
- Ricompila il Magento Open Source con altri componenti
- Utilizzare il software Adobe Commerce o Magenti Open Source in un ambiente di produzione

>[!NOTE]
>
>Gli sviluppatori che contribuiscono al Magento Open Source devono utilizzare [basato su Git](https://developer.adobe.com/commerce/contributor/guides/install/) metodo di installazione.

## Prerequisiti

Prima di continuare, è necessario effettuare le seguenti operazioni:

- Completa tutte [attività preliminari](system-requirements.md).
- [Installa Compositore](https://getcomposer.org/download/).
- Get [chiavi di autenticazione](prerequisites/authentication-keys.md) all’archivio Adobe Commerce e Magenti Open Source Composer.

## Accedi come proprietario del file system

Scopri la proprietà, le autorizzazioni e il proprietario del file system nel nostro [Panoramica dell’argomento relativo alla proprietà e alle autorizzazioni](prerequisites/file-system/overview.md).

Per passare al proprietario del file system:

1. Accedi al server applicazioni come utente autorizzato a scrivere nel file system o passa a un utente con autorizzazioni di scrittura.

   Se si utilizza la shell bash, è possibile utilizzare la sintassi seguente per passare al proprietario del file system e immettere il comando contemporaneamente:

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   Se il proprietario del file system non consente l&#39;accesso, è possibile effettuare le seguenti operazioni:

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. Per eseguire i comandi CLI da qualsiasi directory, aggiungi `<app_root>/bin` al sistema `PATH`.

   Poiché le conchiglie hanno sintassi diversa, consulta un riferimento come [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   shell di base di esempio per CentOS:

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   Facoltativamente, è possibile eseguire i comandi nei seguenti modi:

   - `cd <app_root>/bin` e eseguili come `./magento <command name>`
   - `app_root>/bin/magento <command name>`
   - `<app_root>` è una sottodirectory del docroot del server web

## Ottieni il metapackage

Per ottenere il metapackage Adobe Commerce o Magento Open Source:

1. Accedi al server delle applicazioni come o passa a [proprietario del file system](prerequisites/file-system/overview.md).
1. Passare alla directory docroot del server Web o a una directory configurata come docroot host virtuale.
1. Crea un progetto Composer utilizzando il metapackage Adobe Commerce o Magento Open Source.

   **Magento Open Source**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Quando richiesto, immetti le chiavi di autenticazione. Le chiavi pubbliche e private vengono create e configurate nel tuo [Commerce Marketplace](https://marketplace.magento.com/customer/account/login/).

   In caso di errori, ad esempio `Could not find package...` o `...no matching package found`, assicurati che il comando non contenga errori di battitura. Se si verificano ancora degli errori, potresti non essere autorizzato a scaricare Adobe Commerce. Contatto [Supporto Adobe Commerce](https://support.magento.com/hc/en-us) per aiuto.

   Vedi [Risoluzione dei problemi](https://support.magento.com/hc/en-us/articles/360033818091) per ulteriori errori.

   >[!NOTE]
   >
   >I clienti Adobe Commerce possono accedere alle patch 2.4.x e 2.3.x due settimane prima della data di disponibilità generale (GA, General Availability). I pacchetti pre-release sono disponibili solo tramite Composer. Non è possibile accedere alle versioni precedenti su Developer Portal o GitHub fino a quando non viene rilasciata una versione GA. Se non riesci a trovare questi pacchetti in Compositore, contatta il supporto Adobe Commerce.

### Esempio - Versione secondaria

Le versioni secondarie contengono nuove funzioni, correzioni di qualità e correzioni di sicurezza. Utilizza Compositore per specificare una versione secondaria. Ad esempio, per specificare il metapackage Adobe Commerce 2.4.3:

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.3 <install-directory-name>
```

### Esempio - Patch di qualità

Le patch di qualità contengono principalmente elementi funzionali _e_ correzioni di sicurezza. Tuttavia, a volte possono anche contenere nuove funzioni compatibili con le versioni precedenti. Utilizza Compositore per scaricare una patch di qualità. Ad esempio, per specificare il metapackage Adobe Commerce 2.4.3:

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.3 <install-directory-name>
```

### Esempio: patch di sicurezza

Le patch di sicurezza contengono solo correzioni di sicurezza. Sono progettati per rendere il processo di aggiornamento più rapido e semplice.

Le patch di sicurezza utilizzano la convenzione di denominazione del Compositore `2.4.3-px`. Utilizza Compositore per specificare una patch. Ad esempio, per scaricare il metapackage Adobe Commerce 2.4.3-p1:

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.3-p1 <install-directory-name>
```

## Impostare le autorizzazioni dei file

È necessario impostare le autorizzazioni di lettura e scrittura per il gruppo di server web prima di installare Adobe Commerce o il Magento Open Source. Questo è necessario in modo che la riga di comando possa scrivere file nel file system.

```terminal
cd /var/www/html/<magento install directory>
find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
chown -R :www-data . # Ubuntu
chmod u+x bin/magento
```

## Installare l’applicazione

È necessario utilizzare la riga di comando per installare Adobe Commerce o Magenti Open Source.

Questo esempio presuppone che la directory di installazione sia denominata `magento2ee`, `db-host` si trova sulla stessa macchina (`localhost`) e che la `db-name`, `db-user`e `db-password` sono tutti `magento`:

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
--search-engine=elasticsearch7 \
--elasticsearch-host=es-host.example.com \
--elasticsearch-port=9200 \
--elasticsearch-index-prefix=magento2 \
--elasticsearch-timeout=15
```

>[!TIP]
>
>Puoi personalizzare l’URI amministratore con la `--backend-frontname` opzione . Tuttavia, si consiglia di omettere questa opzione e di consentire al comando di installazione di generare automaticamente un URI casuale. Un URI casuale è più difficile da sfruttare per gli hacker o software dannoso. L’URI viene visualizzato nella console al termine dell’installazione.

>[!TIP]
>
>Per una descrizione completa delle opzioni di installazione di CLI, vedi [Installa l&#39;applicazione dalla riga di comando](advanced.md).

## Riepilogo dei comandi

Per visualizzare un elenco completo dei comandi, immetti:

```bash
bin/magento list
```

Per ottenere assistenza per un comando specifico, immetti:

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

Nella tabella seguente sono riepilogati i comandi disponibili. I comandi vengono visualizzati solo in forma sintetica. Per ulteriori informazioni su un comando, fare clic sul collegamento nella colonna Comando.

| Comando | Descrizione | Prerequisiti |
|--- |--- |--- |
| `magento setup:install` | Installa l&#39;applicazione | Nessuno |
| `magento setup:uninstall` | Rimuove l’applicazione. | Applicazione installata |
| `magento setup:upgrade` | Aggiorna l&#39;applicazione. | Configurazione della distribuzione |
| `magento maintenance:{enable/disable}` | Abilita o disabilita la modalità di manutenzione (in modalità manutenzione, solo gli indirizzi IP esenti possono accedere all’amministratore o alla vetrina). | Applicazione installata |
| `magento setup:config:set` | Crea o aggiorna la configurazione di distribuzione. | Nessuno |
| `magento module:{enable/disable}` | Abilitare o disabilitare i moduli. | Nessuno |
| `magento setup:store-config:set` | Imposta le opzioni relative alla vetrina, ad esempio URL di base, lingua, fuso orario. | Configurazione della distribuzione |
| `magento setup:db-schema:upgrade` | Aggiorna lo schema del database. | Configurazione della distribuzione |
| `magento setup:db-data:upgrade` | Aggiorna i dati del database. | Configurazione della distribuzione |
| `magento setup:db:status` | Controlla se il database è aggiornato con il codice. | Configurazione della distribuzione |
| `magento admin:user:create` | Crea un utente amministratore. | Puoi creare utenti per i seguenti elementi:<br><br>Configurazione della distribuzione<br><br>Abilita almeno `Magento_User` e `Magento_Authorization` moduli<br><br>Database (il modo più semplice è quello di utilizzare `bin/magento setup:upgrade`) |
| `magento list` | Elenca tutti i comandi disponibili. | Nessuno |
| `magento help` | Fornisce la Guida per il comando specificato. | Nessuno |

### Argomenti comuni

Gli argomenti seguenti sono comuni a tutti i comandi. Questi comandi possono essere eseguiti prima o dopo l&#39;installazione dell&#39;applicazione:

| Versione lunga | Versione breve | Significato |
|--- |--- |--- |
| `--help` | `-h` | Richiedi aiuto per qualsiasi comando. Ad esempio: `./magento help setup:install` o `./magento help setup:config:set`. |
| `--quiet` | `-q` | Modalità silenziosa; nessun output. |
| `--no-interaction` | `-n` | Nessuna domanda interattiva. |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | Livello di verbosità. Ad esempio: `--verbose=3` o `-vvv` visualizza la verbosità di debug, che è l&#39;output più dettagliato. Il valore predefinito è `--verbose=1` o `-v`. |
| `--version` | `-V` | Visualizza questa versione dell&#39;applicazione |
| `--ansi` | n/d | Forza uscita ANSI |
| `--no-ansi` | n/d | Disabilita output ANSI |

>[!NOTE]
>
>Congratulazioni! Installazione rapida completata. Hai bisogno di aiuto più avanzato? Consulta il nostro [Installazione avanzata](advanced.md) guida.
