---
title: "Esegui il [!DNL Upgrade Compatibility Tool]"
description: Segui questi passaggi per eseguire il [!DNL Upgrade Compatibility Tool] in un’interfaccia a riga di comando per il progetto Adobe Commerce.
source-git-commit: e704748a7ceaa58a5a8d7004c81ac766dec4e7f1
workflow-type: tm+mt
source-wordcount: '1090'
ht-degree: 0%

---


# Scarica la [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

Per iniziare a utilizzare [!DNL Upgrade Compatibility Tool] in un&#39;interfaccia a riga di comando, scaricala eseguendo il seguente comando:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

Potrebbe essere necessario assegnare allo strumento le autorizzazioni eseguibili con `chmod` comando:

```bash
chmod +x ./uct/bin/uct
```

## La [!DNL Upgrade Compatibility Tool] in un&#39;interfaccia a riga di comando

La [!DNL Upgrade Compatibility Tool] è uno strumento che controlla un’istanza personalizzata di Adobe Commerce rispetto a una versione specifica analizzando tutti i moduli installati in essa. Restituisce un elenco di problemi critici, errori e avvisi che devono essere risolti prima di eseguire l’aggiornamento alla versione più recente di Adobe Commerce.

Vedi questo [tutorial video](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02) per saperne di più sul [!DNL Upgrade Compatibility Tool].

Comandi disponibili per [!DNL Upgrade Compatibility Tool] in un&#39;interfaccia a riga di comando:

| **Comando** | **Descrizione** |
|----------------|-----------------|
| `upgrade:check` | Questo comando esegue il comando [!DNL Upgrade Compatibility Tool] analizzando tutti i moduli installati al suo interno. |
| `dbschema:diff` | Questo comando visualizza tutte le differenze dello schema del database tra due versioni Adobe Commerce specificate. |
| `core:code:changes` | Questo comando confronta l&#39;installazione corrente di Adobe Commerce con un&#39;installazione pulita di vaniglia. |
| `refactor` | Questo comando corregge automaticamente un set ridotto di problemi. |
| `graphql:compare` | Questo comando fornisce l’opzione per introdurre due endpoint GraphQL e confrontare i relativi schemi. |
| `list` | Questo comando restituisce un elenco di tutti i [!DNL Upgrade Compatibility Tool] comandi disponibili. |
| `help` | Questo comando restituisce tutti gli elementi disponibili `help`opzioni per [!DNL Upgrade Compatibility Tool]. Questo comando può essere eseguito e un&#39;opzione con i comandi precedenti. |

## Utilizza la `upgrade:check` command

La `upgrade:check` controlla le modifiche del codice di base per la specifica istanza di Adobe Commerce e tutte le modifiche del codice personalizzato installate al suo interno.

La `upgrade:check` è il comando principale per eseguire lo strumento:

```bash
bin/uct upgrade:check <dir>
```

Dove `<dir>` value è la directory in cui si trova l’istanza Adobe Commerce.

Opzioni disponibili per `upgrade:check` comando:

| **Comando** | **Opzioni disponibili** |
|----------------|-----------------|
| `upgrade:check` | <ul><li>—aiuto: Restituisce tutte le opzioni disponibili.</li><li>—versione corrente: Versione corrente di Adobe Commerce. Questo parametro è obbligatorio e deve essere sempre utilizzato.</li><li>—livello di emissione minima: Puoi filtrare i problemi in base al livello di problema minimo (il valore predefinito è WARNING).</li><li>—ignore-current-version-compatible-issues (o -i): Se non desideri includere nel rapporto problemi critici, errori e avvisi della versione corrente.</li><li>—nella versione in arrivo (o -c): Esegui il targeting di una versione specifica di Adobe Commerce. Se omesso, verrà utilizzato l&#39;ultimo valore disponibile.</li></ul> |

La [!DNL Upgrade Compatibility Tool] consente di eseguire il `upgrade:check` con un comando `--ignore-current-version-compatibility-issues` opzione . Utilizza questa opzione solo per ottenere i nuovi problemi introdotti con l’aggiornamento dalla versione corrente alla versione di destinazione nel tuo [!DNL Upgrade Compatibility Tool] rapporto:

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
> Questo vale solo per le convalide API PHP.

### Aggiunta di `--coming-version` opzione

Puoi confrontare l’installazione di Adobe Commerce corrente con qualsiasi versione di Adobe Commerce `>=2.3` utilizzando `--coming-version` opzione .

È necessario fornire la versione come parametro quando si esegue il `upgrade:check` comando:

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

Dove `-c, --coming-version[=COMING-VERSION]` fa riferimento alla versione di destinazione di Adobe Commerce.

Sono presenti alcune limitazioni durante l&#39;esecuzione del `--coming-version`:

- Questo parametro fa riferimento a qualsiasi tag che identifica una versione specifica di Adobe Commerce.
- È un obbligo di prevedere esplicitamente tale obbligo; fornire solo il suo valore non funziona.
- Fornisci la versione del tag senza virgolette (né singole né doppie): ~~&quot;2.4.1-sviluppo&quot;~~.
- NON devi fornire versioni precedenti a quella attualmente installata, né versioni precedenti alla 2.3, che è la versione più vecchia attualmente supportata.

## Utilizza la `dbschema:diff` command

È possibile recuperare la differenza tra lo schema del database di due versioni di Adobe Commerce.

```bash
bin/uct dbschema:diff <current-version> <target-version>
```

Se gli argomenti sono i seguenti:

- `<current-version>`: qualsiasi versione di Adobe Commerce da confrontare.
- `<target-version>`: anche qualsiasi versione di Adobe Commerce per il confronto.

Esempio di esecuzione:

```bash
bin/uct dbschema:diff 2.4.3 2.4.3-p3

DB schema differences between versions 2.4.3 and 2.4.3-p3:

Table klarna_payments_quote constraint QUOTE_ID_KLARNA_PAYMENTS_QUOTE_QUOTE_ID_QUOTE_ENTITY_ID is present only in version 2.4.3-p3
Table klarna_payments_quote index KLARNA_PAYMENTS_QUOTE_SESSION_ID is present only in version 2.4.3-p3
Table customer_entity column session_cutoff is present only in version 2.4.3-p3
Table customer_visitor column session_id length value is different. 2.4.3: "64", 2.4.3-p3: "1"
Table customer_visitor column session_id comment value is different. 2.4.3: "Session ID", 2.4.3-p3: "Deprecated: Session ID value no longer used"
Table customer_visitor column created_at is present only in version 2.4.3-p3
Table oauth_consumer column secret length value is different. 2.4.3: "32", 2.4.3-p3: "128"
Table oauth_token column secret length value is different. 2.4.3: "32", 2.4.3-p3: "128"
Table admin_user_session column session_id nullable value is different. 2.4.3: "false", 2.4.3-p3: "true"
Table admin_user_session column session_id length value is different. 2.4.3: "128", 2.4.3-p3: "1"
Table admin_user_session column session_id comment value is different. 2.4.3: "Session ID value", 2.4.3-p3: "Deprecated: Session ID value no longer used"

Total detected differences between version 2.4.3 and 2.4.3-p3: 11
```

## Utilizza la `core:code:changes` command

Puoi confrontare l’installazione corrente di Adobe Commerce per verificare se il codice core di Adobe Commerce è stato modificato per implementare una personalizzazione. Questo comando mostra solo un elenco delle modifiche principali:

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

Se gli argomenti sono i seguenti:

- `<dir>`: Directory di installazione di Adobe Commerce.
- `<vanilla dir>`: Directory di installazione della vaniglia Adobe Commerce.

Opzioni disponibili per `core:code:changes` comando:

| **Comando** | **Opzioni disponibili** |
|----------------|-----------------|
| `core:code:changes` | `--help`: Restituisce tutti gli elementi disponibili `--help` opzioni. |

>[!NOTE]
>
> È consigliabile mantenere il codice personalizzato fuori dal codice core. Vedi Adobe Commerce 2.4 [guida all&#39;aggiornamento](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) per ulteriori best practice di aggiornamento.

### Installazione di vaniglia

A _vaniglia_ installazione è un’installazione pulita di un tag di versione o di un ramo specifico per una versione specifica di rilascio.

La `bin/uct core:code:changes` controlla se nel sistema è presente un&#39;istanza di vaniglia. Se questa è la prima volta che si utilizza un&#39;installazione di vaniglia, una domanda interattiva della riga di comando richiede di scaricare il progetto di vaniglia dall&#39;archivio Adobe Commerce (`https://repo.magento.com/`).

Puoi eseguire un [!DNL Upgrade Compatibility Tool] con il comando `--vanilla-dir` per specificare la directory di installazione di vaniglia di Adobe Commerce.

Consulta la sezione [Distribuzione di un&#39;istanza di vaniglia](https://developer.adobe.com/commerce/contributor/guides/code-contributions/#deploy-vanilla-magento-open-source-instance) per ulteriori informazioni.

## Utilizza la `refactor` command

La [!DNL Upgrade Compatibility Tool] è in grado di risolvere automaticamente un set ridotto di problemi:

- Funzioni consentite per l’utilizzo senza passare un argomento, ma con tale utilizzo ora è obsoleta.
- Utilizzo di `$this` nei modelli di Magento.
- Utilizzo della parola chiave PHP `final` in metodi privati.

A tale scopo, esegui la `refactor` comando:

```bash
bin/uct refactor <dir>
```

Dove `<dir>` value è la directory in cui si trova l’istanza Adobe Commerce.

Opzioni disponibili per `refactor` comando:

| **Comando** | **Opzioni disponibili** |
|----------------|-----------------|
| `refactor` | `--help`: Restituisce tutti gli elementi disponibili `--help` opzioni. |

## Utilizza la `graphql:compare` command

Questo comando fornisce l&#39;opzione per [!DNL Upgrade Compatibility Tool] per introdurre due endpoint GraphQL e confrontare i loro schemi cercando modifiche interrotte e pericolose tra di essi:

```bash
bin/uct graphql:compare <schema1> <schema2>
```

Se gli argomenti sono i seguenti:

- `<schema1>`: URL dell&#39;endpoint per l&#39;installazione esistente.
- `<schema2>`: URL dell&#39;endpoint per l&#39;installazione di vaniglia.

Opzioni disponibili per `graphql:compare` comando:

| **Comando** | **Opzioni disponibili** |
|----------------|-----------------|
| `graphql:compare` | `--help`: Restituisce tutti gli elementi disponibili `--help` opzioni. |

## Utilizza la `list` command

Per restituire un elenco di [!DNL Upgrade Compatibility Tool] comandi disponibili, esegui:

```bash
bin/uct list
```

## Utilizza la `--help` command

Per visualizzare il [!DNL Upgrade Compatibility Tool] opzioni generali di comando e aiuto, eseguire:

```bash
bin/uct --help
```

che restituisce un elenco con tutti i dati disponibili `help` opzioni per [!DNL Upgrade Compatibility Tool] in un&#39;interfaccia a riga di comando:

```terminal
- --raw             To output raw command list
- --format=FORMAT   The output format (txt, xml, json, or md) [default: "txt"]
- --short           To skip describing commands' arguments
- -h, --help            Display help for the given command. When no command is given display help for the list command
- -q, --quiet           Do not output any message
- -V, --version         Display this application version
- --ansi|--no-ansi  Force (or disable --no-ansi) ANSI output
- -n, --no-interaction  Do not ask any interactive question
- -v|vv|vvv, --verbose  Increase the verbosity of messages: 1 for normal output, 2 for more verbose output and 3 for debug
```

È possibile eseguire `--help` come opzione quando si esegue un comando specifico. Restituisce `--help` opzioni per il comando specificato.

Esempio di `upgrade:check` comando con `--help` opzione:

```bash
bin/uct upgrade:check --help
```

Questo restituisce opzioni specifiche che possono essere eseguite per `upgrade:check` comando:

```terminal
- -a, --current-version[=CURRENT-VERSION]: Current Adobe Commerce version, version of the Adobe Commerce installation will be used if omitted.
- -c, --coming-version[=COMING-VERSION]: Target Adobe Commerce version, latest released version of Adobe Commerce will be used if omitted. Provides a list of all available Adobe Commerce versions.
- --json-output-path[=JSON-OUTPUT-PATH]: Path of the file where the output will be exported in json format.
- --html-output-path[=HTML-OUTPUT-PATH]: Path of the file where the output will be exported in HTML format.
- --min-issue-level[=MIN-ISSUE-LEVEL]            Minimal issue level you want to see in the report (warning, error or critical). [default: "warning"]
- -i, --ignore-current-version-compatibility-issues  Ignore common issues for current and coming version
- --context=CONTEXT: Execution context. This option is for integration purposes and does not affect the execution result.
- -h, --help: Display help for that specific command. If no command is provided, `list` command is the default result.
- -q, --quiet: Do not output any messages while executing the command.
- -v, --version: Display application version.
- --ansi, --no-ansi: Enable ANSI output.
- -n, --no-interaction: Do not ask any interactive question while executing the command.
- -v, --vv, --vvv, --verbose: Increase verbosity of output communications. 1 for normal output, 2 for verbose output, and 3 for DEBUG output.
```

## Segui le best practice di Adobe Commerce

- Evitare di avere due moduli con lo stesso nome.
- Segui Adobe Commerce [norme di codifica](https://developer.adobe.com/commerce/php/coding-standards/).
- Adobe Commerce 2.4 [Guida all’aggiornamento](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) best practice.

## Ottimizzare i risultati

La [!DNL Upgrade Compatibility Tool] fornisce un rapporto contenente i risultati per impostazione predefinita con tutti i problemi identificati nel progetto. Puoi ottimizzare i risultati per concentrarti sui problemi da risolvere per completare l&#39;aggiornamento:

- Utilizza l’opzione `--ignore-current-version-compatibility-issues` quando desideri ottenere solo i nuovi problemi introdotti con l’aggiornamento dalla versione corrente alla versione di destinazione nel tuo [!DNL Upgrade Compatibility Tool] rapporto.
- Aggiunta di `--min-issue-level` questa impostazione consente di impostare il livello minimo di problema, in modo da assegnare priorità solo ai problemi più importanti con l&#39;aggiornamento.
- La [!DNL Upgrade Compatibility Tool] richiede almeno 2 GB di RAM per l&#39;esecuzione. Questa impostazione è consigliata per evitare problemi dovuti a una limitazione della memoria insufficiente. La [!DNL Upgrade Compatibility Tool] visualizza una domanda se esegui `upgrade:check` comando con basso `memory_limit` impostazione.
