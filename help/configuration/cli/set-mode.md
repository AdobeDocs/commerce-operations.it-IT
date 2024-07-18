---
title: Impostare la modalità operativa
description: Informazioni sull’impostazione delle modalità operative di Adobe Commerce.
exl-id: 62d183fa-d4ff-441d-b8bd-64ef5ae10978
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# Impostare la modalità operativa

{{file-system-owner}}

Per migliorare la sicurezza e la facilità d&#39;uso, è stato aggiunto un comando che cambia [modalità applicazione](../bootstrap/application-modes.md) da sviluppatore a produzione e viceversa.

La modalità di produzione offre prestazioni migliori perché i file di visualizzazione statica vengono popolati nella directory `pub/static` e a causa della compilazione del codice.

>[!INFO]
>
>Nella versione 2.0.6 o successiva, Commerce non imposta esplicitamente le autorizzazioni per i file o le directory quando si passa dalla modalità predefinita a quella di sviluppo e produzione. A differenza di altre modalità, le modalità di sviluppo e produzione sono impostate nel file `env.php`. Adobe Commerce su infrastruttura cloud supporta solo le modalità di produzione e manutenzione.
>
>Consulta [Proprietà e autorizzazioni di Commerce in sviluppo e produzione](../deployment/file-system-permissions.md).

Quando passi alla modalità di sviluppo o produzione, vengono cancellati i contenuti delle seguenti directory:

```
var/cache
generated/metadata
generated/code
var/view_preprocessed
pub/static
```

Eccezioni:

- `.htaccess` file non rimossi
- `pub/static` contiene un file che specifica la versione del contenuto statico. Il file non viene rimosso

>[!INFO]
>
>Per impostazione predefinita, Commerce utilizza le directory `var` per memorizzare la cache, i registri e il codice compilato. È possibile personalizzare questa directory, ma in questa guida si presume che sia `var`.

## Visualizza la modalità corrente

Il modo più semplice per farlo è eseguire questo comando come [proprietario del file system](../../installation/prerequisites/file-system/overview.md). Se hai condiviso l’hosting, questo è l’utente che il tuo provider ti offre per accedere al server. Se si dispone di un server privato, in genere si tratta di un account utente locale sul server Commerce.

Utilizzo comando:

```bash
bin/magento deploy:mode:show
```

Viene visualizzato un messaggio simile al seguente:

```
Current application mode: {mode}. (Note: Environment variables may override this value.)
```

dove:

- **`{mode}`** può essere `default`, `developer` o `production`

## Cambia modalità

Utilizzo comando:

```bash
bin/magento deploy:mode:set {mode} [-s|--skip-compilation]
```

dove:

- **`{mode}`** è obbligatorio; può essere `developer` o `production`

- **`--skip-compilation`** è un parametro facoltativo che è possibile utilizzare per ignorare [la compilazione del codice](../cli/code-compiler.md) quando si passa alla modalità di produzione.

Seguono alcuni esempi.

### Passare alla modalità di produzione

```bash
bin/magento deploy:mode:set production
```

Messaggi simili alla seguente visualizzazione:

```
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
Successfully processed LESS and/or Sass files
CSS deployment complete
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

### Passa alla modalità sviluppatore

Quando si passa dalla modalità di produzione alla modalità sviluppatore, è necessario cancellare le classi generate e le entità Object Manager come i proxy per evitare errori imprevisti. Dopo aver eseguito questa operazione, è possibile modificare le modalità. Procedi come segue:

1. Se si sta passando dalla modalità di produzione alla modalità sviluppatore, eliminare il contenuto delle directory `generated/code` e `generated/metadata`:

   ```bash
   rm -rf <magento_root>/generated/metadata/* <magento_root>/generated/code/*
   ```

1. Impostare la modalità:

   ```bash
   bin/magento deploy:mode:set developer
   ```

   Viene visualizzato il seguente messaggio:

   ```
   Enabled developer mode.
   ```

### Passa alla modalità predefinita

```bash
bin/magento deploy:mode:set default
```

Viene visualizzato il seguente messaggio:

```
Enabled default mode.
```

### Esecuzione di comandi CLI da qualsiasi luogo

[Esegui comandi CLI da qualsiasi luogo](../cli/config-cli.md#config-install-cli-first).

Se non hai aggiunto `<Commerce-install-directory>/bin` al tuo sistema `PATH`, puoi aspettarti un errore durante l&#39;esecuzione del comando da solo.
