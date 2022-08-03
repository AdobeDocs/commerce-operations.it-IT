---
title: Impostare i valori di configurazione
description: Scopri come impostare i valori di configurazione e modificare i valori bloccati nell’amministratore.
source-git-commit: ee2e446edf79efcd7cbbd67248f8e7ece06bfefd
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 0%

---


# Impostare i valori di configurazione

{{file-system-owner}}

Questo argomento illustra i comandi di configurazione avanzati che è possibile utilizzare per:

- Imposta qualsiasi opzione di configurazione dalla riga di comando
- Facoltativamente, blocca qualsiasi opzione di configurazione in modo che il suo valore non possa essere modificato nell’amministratore
- Modificare un&#39;opzione di configurazione bloccata nell&#39;amministratore

Puoi utilizzare questi comandi per impostare manualmente la configurazione Commerce o utilizzando script. Puoi impostare le opzioni di configurazione utilizzando un _percorso di configurazione_, che è un `/`Stringa delimitata da -che identifica in modo univoco tale opzione di configurazione. Puoi trovare i percorsi di configurazione nei seguenti riferimenti:

- [Riferimento per i percorsi di configurazione sensibili e specifici del sistema](../reference/config-reference-sens.md)
- [Riferimento per i percorsi di configurazione dei pagamenti](../reference/config-reference-payment.md)
- [Riferimento a percorsi di configurazione generali](../reference/config-reference-general.md)
- [Riferimento per i percorsi di configurazione dell’estensione Commerce Enterprise B2B](../reference/config-reference-b2b.md)

Puoi impostare i valori nei seguenti momenti:

- Prima di installare Commerce, è possibile impostare i valori di configurazione solo per l’ambito predefinito, perché è l’unico ambito valido.

- Dopo aver installato Commerce, puoi impostare i valori di configurazione per qualsiasi sito Web o [vista store](https://glossary.magento.com/store-view) ambito di applicazione.

Utilizza i seguenti comandi:

- `bin/magento config:set` imposta qualsiasi valore di configurazione non sensibile in base al relativo percorso di configurazione
- `bin/magento config:sensitive:set` imposta qualsiasi valore di configurazione sensibile in base al relativo percorso di configurazione
- `bin/magento config:show` mostra i valori di configurazione salvati; i valori delle impostazioni crittografate vengono visualizzati come asterischi

## Prerequisiti

Per impostare un valore di configurazione, è necessario conoscere almeno uno dei seguenti elementi:

- Percorso di configurazione
- Per impostare un valore di configurazione per un determinato ambito, devi conoscere il codice di ambito.

   Per impostare un valore di configurazione per l&#39;ambito predefinito, non è necessario eseguire alcuna operazione.

### Trova il percorso di configurazione

Vedi i seguenti riferimenti:

- [Riferimento per i percorsi di configurazione sensibili e specifici del sistema](../reference/config-reference-sens.md)
- [Riferimento per i percorsi di configurazione dei pagamenti](../reference/config-reference-payment.md)
- [Riferimento ad altri percorsi di configurazione](../reference/config-reference-general.md)
- [Riferimento per i percorsi di configurazione dell’estensione Commerce Enterprise B2B](../reference/config-reference-b2b.md)

### Trova il codice ambito

Puoi trovare il codice ambito nel database Commerce o nell’amministratore Commerce.

**Per trovare il codice ambito nell’amministratore**:

1. Accedi all’amministratore come utente che può visualizzare i siti web e archiviare le visualizzazioni.
1. Fai clic su **[!UICONTROL Stores]** > Impostazioni > **[!UICONTROL All Stores]**.
1. Nel riquadro a destra, fai clic sul nome del sito web o della visualizzazione archivio per visualizzarne il codice.

   La figura seguente mostra un esempio di codice del sito web.

   ![Ottenere un codice di visualizzazione del sito web o del negozio dall’amministratore](../../assets/configuration/website-code.png)

1. Continua con [Imposta valori](#set-values).

**Per trovare il codice ambito nel database**:

I codici di ambito per i siti web e le viste Store sono memorizzati nel database Commerce in `store_website` e `store` tabelle, rispettivamente.

1. Connettersi al database Commerce.

   ```bash
   mysql -u <Commerce database username> -p
   ```

1. Immetti i seguenti comandi:

   ```shell
   use <Commerce database name>;
   ```

   ```shell
   SELECT * FROM store;
   ```

   ```shell
   SELECT * FROM store_website;
   ```

   Segue un esempio di risultato:

   ```terminal
   [mysql]> SELECT * FROM store_website;
   +------------+-------+--------------+------------+------------------+------------+
   | website_id | code  | name         | sort_order | default_group_id | is_default |
   +------------+-------+--------------+------------+------------------+------------+
   |          0 | admin | Admin        |          0 |                0 |          0 |
   |          1 | base  | Main Website |          0 |                1 |          1 |
   |          2 | test1 | Test Website |          0 |                3 |          0 |
   +------------+-------+--------------+------------+------------------+------------+
   ```

   Utilizza il valore in `code` colonna.

1. Procedi alla sezione successiva.

## Imposta valori

**Per impostare valori di configurazione specifici del sistema**:

```bash
bin/magento config:set [--scope="..."] [--scope-code="..."] [-le | --lock-env] [-lc | --lock-config] path value
```

**Per impostare valori di configurazione sensibili**:

```bash
bin/magento config:sensitive:set [--scope="..."] [--scope-code="..."] path value
```

Nella tabella seguente viene descritta la `set` parametri di comando:

| Parametro | Descrizione |
| --- | --- |
| `--scope` | Ambito della configurazione. I valori possibili sono `default`, `website`oppure `store`. Il valore predefinito è `default`. |
| `--scope-code` | Il codice di ambito di configurazione (codice del sito web o codice della visualizzazione del negozio) |
| `-le or --lock-env` | Blocca il valore in modo che non possa essere modificato nell&#39;amministratore o modifica un&#39;impostazione già bloccata nell&#39;amministratore. Il comando scrive il valore nel `<Commerce base dir>/app/etc/env.php` file. |
| `-lc or --lock-config` | Blocca il valore in modo che non possa essere modificato nell&#39;amministratore o modifica un&#39;impostazione già bloccata nell&#39;amministratore. Il comando scrive il valore nel `<Commerce base dir>/app/etc/config.php` file. La `--lock-config` sovrascrittura delle opzioni `--lock-env` se si specificano entrambe le opzioni. |
| `path` | _Obbligatorio_. Percorso di configurazione |
| `value` | _Obbligatorio_. Valore della configurazione |

>[!INFO]
>
>A partire da Commerce 2.2.4, il `--lock-env` e `--lock-config` le opzioni sostituiscono `--lock` opzione .
>
>Se utilizzi `--lock-env` o `--lock-config` per impostare o modificare un valore, è necessario utilizzare l&#39; [`bin/magento app:config:import` command](../cli/import-configuration.md) per importare l’impostazione prima di accedere ad Admin o a storefront.

Se immetti un percorso di configurazione non corretto, questo comando restituisce un errore

```text
The "wrong/config/path" does not exist
```

Per ulteriori informazioni, consulta una delle sezioni seguenti:

- [Imposta i valori di configurazione che possono essere modificati nell&#39;Admin](#set-configuration-values-that-can-be-edited-in-the-admin)
- [Imposta valori di configurazione che non possono essere modificati nell&#39;Admin](#set-configuration-values-that-cannot-be-edited-in-the-admin)

### Imposta i valori di configurazione che possono essere modificati nell&#39;Admin

Utilizzo `bin/magento config:set` _senza_ `--lock-env` o `--lock-config` per scrivere il valore nel database. I valori impostati in questo modo possono essere modificati in Admin.

Di seguito sono riportati alcuni esempi per l&#39;impostazione di un URL di base dello store:

Imposta l&#39;URL di base per l&#39;ambito predefinito:

```bash
bin/magento config:set web/unsecure/base_url http://example.com/
```

Imposta l&#39;URL di base per `base` sito web:

```bash
bin/magento config:set --scope=websites --scope-code=base web/unsecure/base_url http://example2.com/
```

Imposta l&#39;URL di base per `test` visualizzazione archivio:

```bash
bin/magento config:set --scope=stores --scope-code=test web/unsecure/base_url http://example3.com/
```

### Imposta valori di configurazione che non possono essere modificati nell&#39;Admin

Se utilizzi `--lock-env`  come segue, il comando salva il valore di configurazione in `<Commerce base dir>/app/etc/env.php` e disabilita il campo per la modifica di questo valore in Admin.

```bash
bin/magento config:set --lock-env --scope=stores --scope-code=default web/unsecure/base_url http://example3.com
```

È possibile utilizzare `--lock-env` per impostare i valori di configurazione se Commerce non è installato. Tuttavia, è possibile impostare valori solo per l&#39;ambito predefinito.

>[!INFO]
>
>La `env.php` il file è specifico del sistema. Non devi trasferirlo in un altro sistema. Puoi utilizzarlo per sovrascrivere i valori di configurazione dal database. Ad esempio, puoi prelevare un dump di database da un altro sistema e sovrascrivere il `base_url` e altri valori in modo da non dover modificare il database.

Se utilizzi `--lock-config` come segue, il valore di configurazione viene salvato in `<Commerce base dir>/app/etc/config.php`. Il campo per la modifica di questo valore in Admin è disabilitato.

```bash
bin/magento config:set --lock-config --scope=stores --scope-code=default web/url/use_store 1
```

È possibile utilizzare `--lock-config` per impostare i valori di configurazione se Commerce non è installato. Tuttavia, è possibile impostare valori solo per l&#39;ambito predefinito.

>[!INFO]
>
>È possibile trasferire `config.php` a un altro sistema per utilizzare gli stessi valori di configurazione. Ad esempio, se disponi di un sistema di test che utilizza lo stesso `config.php` significa che non è necessario impostare nuovamente gli stessi valori di configurazione.

## Visualizza il valore delle impostazioni di configurazione

Opzioni di comando:

```bash
bin/magento config:show [--scope[="..."]] [--scope-code[="..."]] path
```

dove

- `--scope` è l’ambito di configurazione (predefinito, sito web, archivio). Il valore predefinito è `default`
- `--scope-code` è il codice di ambito della configurazione (codice del sito web o codice della visualizzazione del negozio)
- `path` è il percorso di configurazione in formato first_part/seconde_part/third_part/etc (_obbligatorio_)

>[!INFO]
>
>La `bin/magento config:show` visualizza i valori di qualsiasi [valori crittografati](../reference/config-reference-sens.md) come serie di asterischi: `******`.

### Esempi

**Per visualizzare tutte le configurazioni salvate**:

```bash
bin/magento config:show
```

Risultato:

```terminal
web/unsecure/base_url - http://example.com/
general/region/display_all - 1
general/region/state_required - AT,BR,CA,CH,EE,ES,FI,LT,LV,RO,US
catalog/category/root_id - 2
analytics/subscription/enabled - 1
```

**Per visualizzare tutte le configurazioni salvate per `base` sito web**:

```bash
bin/magento config:show --scope=websites --scope-code=base
```

Risultato:

```terminal
web/unsecure/base_url - http://example-for-website.com/
general/region/state_required - AT,BR,CA
```

**Visualizzazione dell&#39;URL di base per l&#39;ambito predefinito**:

```bash
bin/magento config:show web/unsecure/base_url
```

Risultato:

```terminal
web/unsecure/base_url - http://example.com/
```

**Per visualizzare l&#39;URL di base per `base` sito web**:

```bash
bin/magento config:show --scope=websites --scope-code=base web/unsecure/base_url
```

Risultato:

```terminal
web/unsecure/base_url - http://example-for-website.com/
```

**Per visualizzare l&#39;URL di base per `default` archiviare**:

```bash
bin/magento config:show --scope=stores --scope-code=default web/unsecure/base_url
```

Risultato:

```terminal
web/unsecure/base_url - http://example-for-store.com/
```
