---
title: Impostare la modalità operativa
description: Scopri come impostare le modalità operative di Adobe Commerce.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '383'
ht-degree: 0%

---


# Impostare la modalità operativa

{{file-system-owner}}

Per migliorare la sicurezza e la facilità d&#39;uso, è stato aggiunto un comando che attiva gli switch [modalità di applicazione](../bootstrap/application-modes.md) dallo sviluppatore alla produzione e viceversa.

La modalità di produzione offre prestazioni migliori perché i file di visualizzazione statici vengono compilati nel `pub/static` e per la compilazione del codice.

>[!INFO]
>
>Nella versione 2.0.6 e successive, Commerce non imposta esplicitamente le autorizzazioni di file o directory quando si passa dalle modalità di produzione, sviluppo e predefinita. A differenza di altre modalità, le modalità di sviluppo e produzione sono impostate nella `env.php` file. Adobe Commerce sull’infrastruttura cloud supporta solo le modalità di produzione e manutenzione.
>
>Vedi [Proprietà e autorizzazioni del commercio nello sviluppo e nella produzione](../deployment/file-system-permissions.md).

Quando passi alla modalità di sviluppo o produzione, cancelliamo il contenuto delle seguenti directory:

```terminal
var/cache
generated/metadata
generated/code
var/view_preprocessed
pub/static
```

Eccezioni:

- `.htaccess` i file non vengono rimossi
- `pub/static` contiene un file che specifica la versione del contenuto statico; file non rimosso

>[!INFO]
>
>Per impostazione predefinita, Commerce utilizza l’ `var` directory in cui memorizzare la cache, i registri e il codice compilato. Puoi personalizzare questa directory ma in questa guida si presume che sia `var`.

## Visualizza la modalità corrente

Il modo più semplice per farlo è eseguire questo comando come [proprietario del file system](../../installation/prerequisites/file-system/overview.md). Se hai condiviso l&#39;hosting, questo è l&#39;utente che il provider ti dà per accedere al server. Se disponi di un server privato, in genere si tratta di un account utente locale sul server Commerce.

Utilizzo comando:

```bash
bin/magento deploy:mode:show
```

Viene visualizzato un messaggio simile al seguente:

```terminal
Current application mode: {mode}. (Note: Environment variables may override this value.)
```

dove:

- **`{mode}`** può essere `default`, `developer`oppure `production`

## Cambia modalità

Utilizzo comando:

```bash
bin/magento deploy:mode:set {mode} [-s|--skip-compilation]
```

dove:

- **`{mode}`** è obbligatorio; può essere `developer` o `production`

- **`--skip-compilation`** è un parametro facoltativo che può essere ignorato [compilazione del codice](../cli/code-compiler.md) quando si passa alla modalità di produzione.

Gli esempi seguono.

### Passa alla modalità di produzione

```bash
bin/magento deploy:mode:set production
```

Messaggi simili alla visualizzazione seguente:

```terminal
Enabled maintenance mode
Requested languages: en_US
=== frontend -> Magento/luma -> en_US ===
... more ...
Successful: 1884 files; errors: 0
---

=== frontend -> Magento/blank -> en_US ===
... more ...
Successful: 1828 files; errors: 0
---

=== adminhtml -> Magento/backend -> en_US ===
... more ...
---

=== Minify templates ===
... more ...
Successful: 897 files modified
---

New version of deployed files: 1440461332
Static content deployment complete
Gathering css/styles-m.less sources.
Successfully processed LESS and/or [Sass](https://glossary.magento.com/sass) files
[CSS](https://glossary.magento.com/css) deployment complete
Generated classes:
      Magento\Sales\Api\Data\CreditmemoCommentInterfacePersistor
      Magento\Sales\Api\Data\CreditmemoCommentInterfaceFactory
      Magento\Sales\Api\Data\CreditmemoCommentSearchResultInterfaceFactory
      Magento\Sales\Api\Data\CreditmemoComment\Repository
      Magento\Sales\Api\Data\CreditmemoItemInterfacePersistor
      ... more ...
Compilation complete
Disabled maintenance mode
Enabled production mode.
```

### Modifica alla modalità sviluppatore

Quando si passa dalla produzione alla modalità sviluppatore, è necessario cancellare le classi generate e le entità Object Manager come proxy per evitare errori imprevisti. Una volta fatto questo, è possibile modificare le modalità. Segui i passaggi seguenti:

1. Se stai passando dalla modalità di produzione alla modalità sviluppatore, elimina i contenuti del `generated/code` e `generated/metadata` directory:

   ```bash
   rm -rf <magento_root>/generated/metadata/* <magento_root>/generated/code/*
   ```

1. Imposta la modalità:

   ```bash
   bin/magento deploy:mode:set developer
   ```

   Viene visualizzato il seguente messaggio:

   ```terminal
   Enabled developer mode.
   ```

### Passa alla modalità predefinita

```bash
bin/magento deploy:mode:set default
```

Viene visualizzato il seguente messaggio:

```terminal
Enabled default mode.
```

### Esegui i comandi CLI da qualsiasi punto

[Esegui i comandi CLI da qualsiasi punto](../cli/config-cli.md#config-install-cli-first).

Se non hai aggiunto `<Commerce-install-directory>/bin` al sistema `PATH`, quindi si può verificare un errore durante l&#39;esecuzione del comando da solo.
