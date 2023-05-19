---
title: Esegui il [!DNL Upgrade Compatibility Tool]
description: Per eseguire il comando [!DNL Upgrade Compatibility Tool] in un’interfaccia della riga di comando per il progetto Adobe Commerce.
exl-id: ea467a74-18eb-476b-96e2-23f4fc257d73
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1116'
ht-degree: 0%

---

# Scarica il file [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

Per iniziare a utilizzare [!DNL Upgrade Compatibility Tool] in un&#39;interfaccia della riga di comando, scaricarla eseguendo il comando seguente:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

Potrebbe essere necessario assegnare allo strumento le autorizzazioni eseguibili con `chmod` comando:

```bash
chmod +x ./uct/bin/uct
```

## Il [!DNL Upgrade Compatibility Tool] in un&#39;interfaccia della riga di comando

Il [!DNL Upgrade Compatibility Tool] è uno strumento che confronta un’istanza personalizzata di Adobe Commerce con una versione specifica analizzando tutti i moduli installati al suo interno. Restituisce un elenco di problemi critici, errori e avvisi che devono essere risolti prima dell’aggiornamento alla versione più recente di Adobe Commerce.

Vedi questo [tutorial video](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02) per ulteriori informazioni sul [!DNL Upgrade Compatibility Tool].

Comandi disponibili per [!DNL Upgrade Compatibility Tool] in un’interfaccia della riga di comando:

| **Comando** | **Descrizione** |
|----------------|-----------------|
| `upgrade:check` | Questo comando esegue [!DNL Upgrade Compatibility Tool] analizzando tutti i moduli installati al suo interno. |
| `dbschema:diff` | Con questo comando vengono visualizzate tutte le differenze dello schema del database tra due versioni di Adobe Commerce specificate. |
| `core:code:changes` | Questo comando confronta l’installazione Adobe Commerce corrente con un’installazione pura. |
| `refactor` | Questo comando risolve automaticamente un set ridotto di problemi. |
| `graphql:compare` | Questo comando fornisce l’opzione per analizzare due endpoint di GraphQL e confrontare i loro schemi. |
| `list` | Questo comando restituisce un elenco di tutti i [!DNL Upgrade Compatibility Tool] comandi disponibili. |
| `help` | Questo comando restituisce tutti gli elementi disponibili `help`opzioni per [!DNL Upgrade Compatibility Tool]. Questo comando può essere eseguito insieme a un&#39;opzione con i comandi precedenti. |

## Utilizza il `upgrade:check` comando

Il `upgrade:check` Il comando verifica la presenza di modifiche al codice di base per l’istanza Adobe Commerce specifica e di tutte le modifiche al codice personalizzato installate al suo interno.

Il `upgrade:check` Il comando è il comando principale per eseguire lo strumento:

```bash
bin/uct upgrade:check <dir>
```

Dove `<dir>` value è la directory in cui si trova l’istanza di Adobe Commerce.

Opzioni disponibili per `upgrade:check` comando:

| **Comando** | **Opzioni disponibili** |
|----------------|-----------------|
| `upgrade:check` | <ul><li>—help: restituisce tutte le opzioni disponibili.</li><li>—current-version: versione corrente di Adobe Commerce. Questo parametro è obbligatorio e deve essere sempre utilizzato.</li><li>—min-issue-level: è possibile filtrare i problemi in base al livello di problema minimo (il valore predefinito è WARNING).</li><li>—ignore-current-version-compatibility-issues (o -i): se non si desidera includere nel rapporto problemi critici, errori e avvisi della versione corrente.</li><li>—coming-version (o -c): specifica una versione di Adobe Commerce. Se omesso, verrà utilizzato il più recente disponibile.</li></ul> |

Il [!DNL Upgrade Compatibility Tool] consente di eseguire `upgrade:check` comando con un `--ignore-current-version-compatibility-issues` opzione. Utilizza questa opzione quando desideri ricevere solo i nuovi problemi introdotti con l’aggiornamento dalla versione corrente alla versione di destinazione nel tuo [!DNL Upgrade Compatibility Tool] rapporto:

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
> Questo vale solo per le convalide API PHP.

### Aggiunta di `--coming-version` opzione

Puoi confrontare l’installazione corrente di Adobe Commerce con qualsiasi versione di Adobe Commerce `>=2.3` utilizzando `--coming-version` opzione.

È necessario fornire la versione come parametro durante l’esecuzione di `upgrade:check` comando:

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

Dove `-c, --coming-version[=COMING-VERSION]` fa riferimento alla versione di destinazione di Adobe Commerce.

Esistono alcune limitazioni nell’esecuzione di `--coming-version`:

- Questo parametro fa riferimento a qualsiasi tag che identifica una versione specifica di Adobe Commerce.
- È un requisito fornire questo in modo esplicito; fornire solo il valore di esso non funziona.
- Fornisci la versione del tag senza virgolette (né singole né doppie): ~~&quot;2.4.1-sviluppare&quot;~~.
- NON devi fornire versioni precedenti a quella attualmente installata, né versioni precedenti alla 2.3, che è quella più vecchia supportata al momento.

## Utilizza il `dbschema:diff` comando

Puoi recuperare la differenza tra lo schema del database di due versioni di Adobe Commerce.

```bash
bin/uct dbschema:diff <current-version> <target-version>
```

Dove gli argomenti sono i seguenti:

- `<current-version>`: qualsiasi versione di Adobe Commerce a scopo di confronto.
- `<target-version>`: anche qualsiasi versione di Adobe Commerce a scopo di confronto.

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

## Utilizza il `core:code:changes` comando

Puoi confrontare la tua attuale installazione di Adobe Commerce per verificare se il codice core di Adobe Commerce è stato modificato per implementare una personalizzazione. Questo comando mostra solo un elenco delle modifiche principali:

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

Dove gli argomenti sono i seguenti:

- `<dir>`: directory di installazione di Adobe Commerce.
- `<vanilla dir>`: directory di installazione di Adobe Commerce vanilla.

Opzioni disponibili per `core:code:changes` comando:

| **Comando** | **Opzioni disponibili** |
|----------------|-----------------|
| `core:code:changes` | `--help`: restituisce tutti gli elementi disponibili `--help` opzioni. |

>[!NOTE]
>
> È consigliabile escludere il codice personalizzato dal codice principale. Consulta Adobe Commerce 2.4 [guida all’aggiornamento](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) per ulteriori best practice per l’aggiornamento.

### Installazione Vanilla

A _vaniglia_ l’installazione è un’installazione pulita di un tag di versione o di un ramo specifico per una versione specifica.

Il `bin/uct core:code:changes` Il comando controlla se nel sistema è presente un’istanza vanilla. Se questa è la prima volta che utilizzi un’installazione vanilla, una domanda interattiva da riga di comando richiede di scaricare il progetto vanilla dall’archivio Adobe Commerce (`https://repo.magento.com/`).

È possibile eseguire una [!DNL Upgrade Compatibility Tool] comando con `--vanilla-dir` per specificare la directory di installazione di Adobe Commerce vanilla.

Consulta la [Distribuisci istanza vanilla](https://developer.adobe.com/commerce/contributor/guides/code-contributions/#deploy-vanilla-magento-open-source-instance) per ulteriori informazioni.

## Utilizza il `refactor` comando

Il [!DNL Upgrade Compatibility Tool] ha la possibilità di risolvere automaticamente un set ridotto di problemi:

- Funzioni che potevano essere utilizzate senza passare un argomento, ma con tale utilizzo ora sono obsolete.
- Utilizzo di `$this` nei modelli di Magento.
- Utilizzo della parola chiave PHP `final` in metodi privati.

Per questo, esegui il `refactor` comando:

```bash
bin/uct refactor <dir>
```

Dove `<dir>` value è la directory in cui si trova l’istanza di Adobe Commerce.

Opzioni disponibili per `refactor` comando:

| **Comando** | **Opzioni disponibili** |
|----------------|-----------------|
| `refactor` | `--help`: restituisce tutti gli elementi disponibili `--help` opzioni. |

## Utilizza il `graphql:compare` comando

Questo comando fornisce l&#39;opzione al [!DNL Upgrade Compatibility Tool] per analizzare due endpoint GraphQL e confrontare i loro schemi alla ricerca di modifiche pericolose e interrotte tra di essi:

```bash
bin/uct graphql:compare <schema1> <schema2>
```

Dove gli argomenti sono i seguenti:

- `<schema1>`: URL dell’endpoint per l’installazione esistente.
- `<schema2>`: URL dell’endpoint per l’installazione Vanilla.

Opzioni disponibili per `graphql:compare` comando:

| **Comando** | **Opzioni disponibili** |
|----------------|-----------------|
| `graphql:compare` | `--help`: restituisce tutti gli elementi disponibili `--help` opzioni. |

## Utilizza il `list` comando

Per restituire un elenco di [!DNL Upgrade Compatibility Tool] comandi disponibili, esegui:

```bash
bin/uct list
```

## Utilizza il `help` comando

Per visualizzare [!DNL Upgrade Compatibility Tool] comando opzioni generali e guida, eseguire:

```bash
bin/uct --help
```

che restituisce un elenco con tutti gli elementi disponibili `help` opzioni per [!DNL Upgrade Compatibility Tool] in un’interfaccia della riga di comando:

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

È possibile eseguire `--help` come opzione durante l’esecuzione di un comando specifico. Restituisce `--help` opzioni per il comando specificato.

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

- Evita di avere due moduli con lo stesso nome.
- Segui Adobe Commerce [standard di codifica](https://developer.adobe.com/commerce/php/coding-standards/).
- Adobe Commerce 2.4 [Guida all’aggiornamento](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) best practice.
- Esegui il [!DNL Upgrade Compatibility Tool] dal [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html) per [Adobe Commerce sull’infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html){target=_blank} progetti.

## Ottimizzare i risultati

Il [!DNL Upgrade Compatibility Tool] fornisce un rapporto contenente i risultati con tutti i problemi identificati nel progetto per impostazione predefinita. Puoi ottimizzare i risultati in modo da concentrarti sui problemi da risolvere per completare l’aggiornamento:

- Utilizza l’opzione `--ignore-current-version-compatibility-issues` quando desideri ricevere solo i nuovi problemi introdotti con l&#39;aggiornamento dalla versione corrente alla versione di destinazione nel tuo [!DNL Upgrade Compatibility Tool] rapporto.
- Aggiunta di `--min-issue-level` , questa impostazione consente di impostare il livello di problema minimo, per assegnare la priorità solo ai problemi più importanti con l’aggiornamento.
- Il [!DNL Upgrade Compatibility Tool] richiede almeno 2 GB di RAM per l&#39;esecuzione. Questa impostazione è consigliata per evitare problemi dovuti a una limitazione della memoria. Il [!DNL Upgrade Compatibility Tool] visualizza una domanda se si esegue `upgrade:check` comando con basso `memory_limit` impostazione.
