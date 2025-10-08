---
title: Comandi comuni
description: Scopri i comandi CLI comuni di Adobe Commerce e i relativi esempi di utilizzo. Scopri gli strumenti essenziali della riga di comando per lo sviluppo e l’amministrazione.
exl-id: d35a1dd9-10b3-4364-b6f4-b1e259a04e3d
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# Comandi comuni

Di seguito vengono riepilogati alcuni dei comandi disponibili.

**Per visualizzare un elenco completo dei comandi**:

```bash
bin/magento list
```

Esempio di comando help:

```bash
bin/magento help <command>
```

```bash
bin/magento help cache:enable
```

I comandi vengono visualizzati solo in forma di riepilogo. Per ulteriori informazioni su un comando, fare clic sul collegamento nella colonna Comando.

| Comando | Descrizione |
|--- |--- |
| [`magento cache:{enable/disable/clean/flush/status}`](../cli/manage-cache.md) | Gestisce la cache |
| [`magento indexer:{status/show-mode/set-mode/reindex/info/reset/show-dimensions-mode/set-dimensions-mode}`](../cli/manage-indexers.md) | Gestisce gli indici |
| [`magento cron:run`](../cli/configure-cron-jobs.md) | Esegue processi cron Commerce |
| [`magento setup:di:compile`](../cli/code-compiler.md) | Compila tutti i proxy e le factory inesistenti e precompila le definizioni delle classi, le informazioni sull&#39;ereditarietà e le definizioni dei plug-in per un unico store e sito Web. |
| [`magento info:dependencies:{show-modules/show-modules-circular/show-framework}`](../cli/dependency-reports.md) | Dipendenze dei moduli, dipendenze circolari e dipendenze del framework Commerce. |
| [`magento i18n:{collect-phrases/pack/uninstall}`](../cli/localization.md) | Crea un dizionario o un pacchetto di traduzione |
| [`magento setup:static-content:deploy`](../cli/static-view-file-deployment.md) | Distribuisce i file di visualizzazione statici |
| [`magento dev:source-theme:deploy`](../cli/create-symlinks.md) | Crea CSS da LESS |
| [`magento dev:tests:run`](../cli/unit-tests.md) | Esegue test automatizzati |
| [`magento dev:xml:convert`](../cli/convert-layout-files.md) | Aggiornare i file XML di layout in modo che corrispondano al nuovo foglio di stile XSLT (Extensible Stylesheet Language Transformation) |
| [`magento setup:perf:generate-fixtures`](../cli/generate-data.md) | Genera i dati da utilizzare per il test delle prestazioni. |
| [`magento sampledata:install`](../../installation/sample-data/overview.md) | Installa dati di esempio facoltativi dopo l&#39;installazione dell&#39;applicazione Commerce.<br><br>Per ulteriori dettagli sui dati di esempio, vedere [Dati di esempio facoltativi](../../installation/sample-data/overview.md). |
| [`magento config:{set/sensitive:set/show/}`](../cli/set-configuration-values.md) | Gestisce le configurazioni back-end |
| [`magento admin:user:{create/unlock}`](../../installation/tutorials/admin.md#create-edit-or-unloack-an-administrator-account) | Crea/modifica/sblocca gli utenti amministratori. |
| [`magento dev:template-hints:{enable/disable}`](https://developer.adobe.com/commerce/frontend-core/guide/themes/debug/) | Abilita/disabilita gli hint del modello sviluppatore. |

## Argomenti comuni

I seguenti argomenti sono comuni a [tutti i comandi](/help/tools/reference/commerce-on-premises.md). Questi comandi possono essere eseguiti prima o dopo l&#39;installazione del software Commerce:

| Versione lunga | Versione breve | Significato |
|--- |--- |--- |
| `--help` | `-h` | Visualizzare la Guida per qualsiasi comando. Ad esempio, `./magento help setup:install` o `./magento help setup:config:set`. |
| `--quiet` | `-q` | Modalità silenziosa; nessuna uscita. |
| `--no-interaction` | `-n` | Nessuna domanda interattiva. |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | Livello di dettaglio. `--verbose=3` o `-vvv`, ad esempio, visualizza il livello di dettaglio del debug, ovvero l&#39;output più dettagliato. Il valore predefinito è `--verbose=1` o `-v`. |
| `--version` | `-V` | Visualizza questa versione dell&#39;applicazione |
| `--ansi` | n/d | Forza uscita ANSI |
| `--no-ansi` | n/d | Disattiva output ANSI |
