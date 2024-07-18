---
title: Esegui  [!DNL Upgrade Compatibility Tool]
description: Segui questi passaggi per eseguire  [!DNL Upgrade Compatibility Tool]  in un'interfaccia della riga di comando per il tuo progetto Adobe Commerce.
exl-id: ea467a74-18eb-476b-96e2-23f4fc257d73
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '1077'
ht-degree: 0%

---

# Scarica [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

Per iniziare a utilizzare [!DNL Upgrade Compatibility Tool] in un&#39;interfaccia della riga di comando, scaricarlo eseguendo il comando seguente:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

Potrebbe essere necessario assegnare allo strumento le autorizzazioni eseguibili con il comando `chmod`:

```bash
chmod +x ./uct/bin/uct
```

## [!DNL Upgrade Compatibility Tool] in un&#39;interfaccia della riga di comando

[!DNL Upgrade Compatibility Tool] è uno strumento che controlla un&#39;istanza personalizzata di Adobe Commerce rispetto a una versione specifica analizzando tutti i moduli in essa installati. Restituisce un elenco di problemi critici, errori e avvisi che devono essere risolti prima dell’aggiornamento alla versione più recente di Adobe Commerce.

Per ulteriori informazioni su [!DNL Upgrade Compatibility Tool], consulta questa [esercitazione video](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02).

Comandi disponibili per [!DNL Upgrade Compatibility Tool] in un&#39;interfaccia della riga di comando:

| **Comando** | **Descrizione** |
|----------------|-----------------|
| `upgrade:check` | Questo comando esegue [!DNL Upgrade Compatibility Tool] analizzando tutti i moduli installati in esso. |
| `dbschema:diff` | Con questo comando vengono visualizzate tutte le differenze dello schema del database tra due versioni di Adobe Commerce specificate. |
| `core:code:changes` | Questo comando confronta l’installazione Adobe Commerce corrente con un’installazione pura. |
| `refactor` | Questo comando risolve automaticamente un set ridotto di problemi. |
| `graphql:compare` | Questo comando fornisce l’opzione per analizzare due endpoint di GraphQL e confrontare i loro schemi. |
| `list` | Questo comando restituisce un elenco di tutti i [!DNL Upgrade Compatibility Tool] comandi disponibili. |
| `help` | Questo comando restituisce tutte le `help` opzioni disponibili per [!DNL Upgrade Compatibility Tool]. Questo comando può essere eseguito insieme a un&#39;opzione con i comandi precedenti. |

## Usa il comando `upgrade:check`

Il comando `upgrade:check` verifica la presenza di modifiche al codice di base per l&#39;istanza Adobe Commerce specifica e tutte le modifiche al codice personalizzato sono installate in tale istanza.

Il comando `upgrade:check` è il comando principale per l&#39;esecuzione dello strumento:

```bash
bin/uct upgrade:check <dir>
```

Dove il valore `<dir>` è la directory in cui si trova l&#39;istanza di Adobe Commerce.

Opzioni disponibili per il comando `upgrade:check`:

| **Comando** | **Opzioni disponibili** |
|----------------|-----------------|
| `upgrade:check` | <ul><li>—help: restituisce tutte le opzioni disponibili.</li><li>—current-version: versione corrente di Adobe Commerce. Questo parametro è obbligatorio e deve essere sempre utilizzato.</li><li>—min-issue-level: è possibile filtrare i problemi in base al livello di problema minimo (il valore predefinito è WARNING).</li><li>—ignore-current-version-compatibility-issues (o -i): se non si desidera includere nel rapporto problemi critici, errori e avvisi della versione corrente.</li><li>—coming-version (o -c): specifica una versione di Adobe Commerce. Se omesso, verrà utilizzato il più recente disponibile.</li></ul> |

[!DNL Upgrade Compatibility Tool] consente di eseguire il comando `upgrade:check` con un&#39;opzione `--ignore-current-version-compatibility-issues`. Utilizzare questa opzione quando si desidera ottenere solo i nuovi problemi introdotti con l&#39;aggiornamento dalla versione corrente alla versione di destinazione nel report [!DNL Upgrade Compatibility Tool]:

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
> Questo vale solo per le convalide API PHP.

### Aggiunta dell&#39;opzione `--coming-version`

È possibile confrontare l&#39;installazione corrente di Adobe Commerce con qualsiasi versione di Adobe Commerce `>=2.3` utilizzando l&#39;opzione `--coming-version`.

È necessario fornire la versione come parametro durante l&#39;esecuzione del comando `upgrade:check`:

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

Dove `-c, --coming-version[=COMING-VERSION]` fa riferimento alla versione di destinazione di Adobe Commerce.

Esistono alcune limitazioni durante l&#39;esecuzione di `--coming-version`:

- Questo parametro fa riferimento a qualsiasi tag che identifica una versione specifica di Adobe Commerce.
- È un requisito fornire questo in modo esplicito; fornire solo il valore di esso non funziona.
- Specificare la versione del tag senza virgolette (né singole né doppie): ~~&#39;2.4.1-development&#39;~~.
- NON devi fornire versioni precedenti a quella attualmente installata, né versioni precedenti alla 2.3, che è quella più vecchia supportata al momento.

## Usa il comando `dbschema:diff`

Puoi recuperare la differenza tra lo schema del database di due versioni di Adobe Commerce.

```bash
bin/uct dbschema:diff <current-version> <target-version>
```

Dove gli argomenti sono i seguenti:

- `<current-version>`: qualsiasi versione di Adobe Commerce per il confronto.
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

## Usa il comando `core:code:changes`

Puoi confrontare la tua attuale installazione di Adobe Commerce per verificare se il codice core di Adobe Commerce è stato modificato per implementare una personalizzazione. Questo comando mostra solo un elenco delle modifiche principali:

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

Dove gli argomenti sono i seguenti:

- `<dir>`: directory di installazione di Adobe Commerce.
- `<vanilla dir>`: directory di installazione Adobe Commerce vanilla.

Opzioni disponibili per il comando `core:code:changes`:

| **Comando** | **Opzioni disponibili** |
|----------------|-----------------|
| `core:code:changes` | `--help`: restituisce tutte le `--help` opzioni disponibili. |

>[!NOTE]
>
> È consigliabile escludere il codice personalizzato dal codice principale. Per ulteriori best practice per l&#39;aggiornamento, consulta la [guida all&#39;aggiornamento](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) di Adobe Commerce 2.4.

### Installazione Vanilla

Un&#39;installazione di _vanilla_ è un&#39;installazione pulita di un tag di versione o di un ramo specificato per una versione specifica.

Il comando `bin/uct core:code:changes` verifica se nel sistema è presente un&#39;istanza Vanilla. Se questa è la prima volta che si utilizza un&#39;installazione di tipo vanilla, una domanda interattiva della riga di comando richiede di scaricare il progetto vanilla dall&#39;archivio di Adobe Commerce (`https://repo.magento.com/`).

È possibile eseguire un comando [!DNL Upgrade Compatibility Tool] con l&#39;opzione `--vanilla-dir` per specificare la directory di installazione di Adobe Commerce Vanilla.

Per ulteriori informazioni, vedere l&#39;argomento [Distribuisci istanza Vanilla](https://developer.adobe.com/commerce/contributor/guides/code-contributions/#deploy-vanilla-magento-open-source-instance).

## Usa il comando `refactor`

[!DNL Upgrade Compatibility Tool] ha la possibilità di risolvere automaticamente un set ridotto di problemi:

- Funzioni che potevano essere utilizzate senza passare un argomento, ma con tale utilizzo ora sono obsolete.
- Utilizzo di `$this` nei modelli di Magento.
- Utilizzo della parola chiave PHP `final` nei metodi privati.

A tale scopo, eseguire il comando `refactor`:

```bash
bin/uct refactor <dir>
```

Dove il valore `<dir>` è la directory in cui si trova l&#39;istanza di Adobe Commerce.

Opzioni disponibili per il comando `refactor`:

| **Comando** | **Opzioni disponibili** |
|----------------|-----------------|
| `refactor` | `--help`: restituisce tutte le `--help` opzioni disponibili. |

## Usa il comando `graphql:compare`

Questo comando fornisce a [!DNL Upgrade Compatibility Tool] l&#39;opzione per analizzare due endpoint di GraphQL e confrontare i relativi schemi alla ricerca di modifiche pericolose e non funzionanti tra loro:

```bash
bin/uct graphql:compare <schema1> <schema2>
```

Dove gli argomenti sono i seguenti:

- `<schema1>`: URL endpoint per l&#39;installazione esistente.
- `<schema2>`: URL endpoint per l&#39;installazione Vanilla.

Opzioni disponibili per il comando `graphql:compare`:

| **Comando** | **Opzioni disponibili** |
|----------------|-----------------|
| `graphql:compare` | `--help`: restituisce tutte le `--help` opzioni disponibili. |

## Usa il comando `list`

Per restituire un elenco dei comandi disponibili [!DNL Upgrade Compatibility Tool], eseguire:

```bash
bin/uct list
```

## Usa il comando `help`

Per visualizzare le opzioni generali e la Guida del comando [!DNL Upgrade Compatibility Tool], eseguire:

```bash
bin/uct --help
```

In questo modo viene restituito un elenco con tutte le opzioni `help` disponibili per [!DNL Upgrade Compatibility Tool] in un&#39;interfaccia della riga di comando:

```
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

È possibile eseguire `--help` come opzione durante l&#39;esecuzione di un comando specifico. Restituisce `--help` opzioni per il comando specificato.

Esempio del comando `upgrade:check` con opzione `--help`:

```bash
bin/uct upgrade:check --help
```

Vengono restituite opzioni specifiche che è possibile eseguire per il comando `upgrade:check`:

```
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
- Segui [gli standard di codifica](https://developer.adobe.com/commerce/php/coding-standards/) di Adobe Commerce.
- Best practice per l&#39;aggiornamento alla [Guida all&#39;aggiornamento](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) di Adobe Commerce 2.4.
- Esegui [!DNL Upgrade Compatibility Tool] da [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html) per [Adobe Commerce su infrastruttura cloud](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html){target=_blank} progetti.

## Ottimizzare i risultati

[!DNL Upgrade Compatibility Tool] fornisce un report contenente i risultati con tutti i problemi identificati nel progetto per impostazione predefinita. Puoi ottimizzare i risultati in modo da concentrarti sui problemi da risolvere per completare l’aggiornamento:

- Utilizzare l&#39;opzione `--ignore-current-version-compatibility-issues` quando si desidera ottenere solo i nuovi problemi introdotti con l&#39;aggiornamento dalla versione corrente alla versione di destinazione nel report [!DNL Upgrade Compatibility Tool].
- Aggiungendo l&#39;opzione `--min-issue-level`, questa impostazione consente di impostare il livello minimo di problema, per aiutare a dare priorità solo ai problemi più importanti con l&#39;aggiornamento.
- [!DNL Upgrade Compatibility Tool] richiede almeno 2 GB di RAM per l&#39;esecuzione. Questa impostazione è consigliata per evitare problemi dovuti a una limitazione della memoria. [!DNL Upgrade Compatibility Tool] visualizza una domanda se si esegue il comando `upgrade:check` con un&#39;impostazione `memory_limit` bassa.
