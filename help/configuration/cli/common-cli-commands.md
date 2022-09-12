---
title: Comandi comuni
description: Visualizza un esempio di comandi e utilizzo comuni di Commerce CLI.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---


# Comandi comuni

Di seguito sono riepilogati alcuni dei comandi disponibili.

**Visualizzazione di un elenco completo dei comandi**:

```bash
bin/magento list
```

Esempio di comando della guida:

```bash
bin/magento help <command>
```

```bash
bin/magento help cache:enable
```

I comandi sono visualizzati solo in forma sintetica; per ulteriori informazioni su un comando, fare clic sul collegamento nella colonna Comando.

| Comando | Descrizione |
|--- |--- |
| [`magento cache:{enable/disable/clean/flush/status}`](../cli/manage-cache.md) | Gestisce la cache |
| [`magento indexer:{status/show-mode/set-mode/reindex/info/reset/show-dimensions-mode/set-dimensions-mode}`](../cli/manage-indexers.md) | Gestisce gli indicizzatori |
| [`magento cron:run`](../cli/configure-cron-jobs.md) | Esegue i processi Commerce cron |
| [`magento setup:di:compile`](../cli/code-compiler.md) | compila tutti i proxy e le fabbriche inesistenti; precompila le definizioni delle classi, le informazioni di ereditarietà e le definizioni dei plug-in per un singolo archivio e un sito web. |
| [`magento info:dependencies:{show-modules/show-modules-circular/show-framework}`](../cli/dependency-reports.md) | Dipendenze del modulo, dipendenze circolari e dipendenze del framework Commerce. |
| [`magento i18n:{collect-phrases/pack/uninstall}`](../cli/localization.md) | Crea un dizionario di traduzione o un pacchetto di traduzione |
| [`magento setup:static-content:deploy`](../cli/static-view-file-deployment.md) | Distribuisce file di visualizzazione statici |
| [`magento dev:source-theme:deploy`](../cli/create-symlinks.md) | Crea CSS da LESS |
| [`magento dev:tests:run`](../cli/unit-tests.md) | Esegue test automatici |
| [`magento dev:xml:convert`](../cli/convert-layout-files.md) | Aggiornare i file XML di layout in modo che corrispondano al nuovo foglio di stile XSLT (Extensible Stylesheet Language Transformations) |
| [`magento setup:perf:generate-fixtures`](../cli/generate-data.md) | Genera i dati da utilizzare per il test delle prestazioni. |
| [`magento sampledata:install`](../../installation/sample-data/overview.md) | Installa i dati di esempio facoltativi dopo l’installazione dell’applicazione Commerce.<br><br>Per ulteriori dettagli sui dati di esempio, consulta [Dati di esempio opzionali](../../installation/sample-data/overview.md). |
| [`magento config:{set/sensitive:set/show/}`](../cli/set-configuration-values.md) | Gestisce le configurazioni back-end |
| [`magento admin:user:{create/unlock}`](../../installation/tutorials/admin.md#create-edit-or-unloack-an-administrator-account) | Crea/modifica/sblocca gli utenti amministratori. |
| [`magento dev:template-hints:{enable/disable}`](https://developer.adobe.com/commerce/frontend-core/guide/themes/debug/) | Abilita/disabilita i suggerimenti per i modelli di sviluppatori. |

## Argomenti comuni

Gli argomenti seguenti sono comuni a tutti i comandi. Questi comandi possono essere eseguiti prima o dopo l&#39;installazione del software Commerce:

| Versione lunga | Versione breve | Significato |
|--- |--- |--- |
| `--help` | `-h` | Richiedi aiuto per qualsiasi comando. Ad esempio: `./magento help setup:install` o `./magento help setup:config:set`. |
| `--quiet` | `-q` | Modalità silenziosa; nessun output. |
| `--no-interaction` | `-n` | Nessuna domanda interattiva. |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | Livello di verbosità. Ad esempio: `--verbose=3` o `-vvv` visualizza la verbosità di debug, che è l&#39;output più dettagliato. Il valore predefinito è `--verbose=1` o `-v`. |
| `--version` | `-V` | Visualizza questa versione dell&#39;applicazione |
| `--ansi` | n/d | Forza uscita ANSI |
| `--no-ansi` | n/d | Disabilita output ANSI |
