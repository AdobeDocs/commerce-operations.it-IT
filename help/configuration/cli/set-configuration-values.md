---
title: Impostare i valori di configurazione
description: Scopri come impostare i valori di configurazione e modificare i valori bloccati nell’amministratore.
exl-id: 1dc2412d-50b3-41fb-ab22-3eccbb086302
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '982'
ht-degree: 0%

---

# Impostare i valori di configurazione

{{file-system-owner}}

In questo argomento vengono descritti i comandi di configurazione avanzati che è possibile utilizzare per:

- Imposta qualsiasi opzione di configurazione dalla riga di comando
- Facoltativamente, blocca qualsiasi opzione di configurazione in modo che il suo valore non possa essere modificato in Admin
- Modificare un’opzione di configurazione bloccata in Admin

Puoi utilizzare questi comandi per impostare la configurazione di Commerce manualmente o utilizzando gli script. È possibile impostare le opzioni di configurazione utilizzando una _percorso di configurazione_, che è un `/`Stringa delimitata da -che identifica in modo univoco tale opzione di configurazione. Puoi trovare i percorsi di configurazione nei seguenti riferimenti:

- [Riferimento ai percorsi di configurazione sensibili e specifici del sistema](../reference/config-reference-sens.md)
- [Riferimento ai percorsi di configurazione dei pagamenti](../reference/config-reference-payment.md)
- [Riferimento generale ai percorsi di configurazione](../reference/config-reference-general.md)
- [Riferimento ai percorsi di configurazione dell’estensione Commerce Enterprise B2B](../reference/config-reference-b2b.md)

È possibile impostare i valori nei seguenti momenti:

- Prima di installare Commerce, è possibile impostare i valori di configurazione solo per l’ambito predefinito, perché è l’unico ambito valido.

- Dopo aver installato Commerce, puoi impostare i valori di configurazione per qualsiasi ambito di visualizzazione del sito web o dell’archivio.

Utilizza i seguenti comandi:

- `bin/magento config:set` imposta qualsiasi valore di configurazione non sensibile in base al relativo percorso di configurazione
- `bin/magento config:sensitive:set` imposta qualsiasi valore di configurazione sensibile in base al relativo percorso di configurazione
- `bin/magento config:show` mostra i valori di configurazione salvati; i valori delle impostazioni crittografate vengono visualizzati come asterischi

## Prerequisiti

Per impostare un valore di configurazione, è necessario conoscere almeno uno dei seguenti elementi:

- Percorso di configurazione
- Per impostare un valore di configurazione per un determinato ambito, è necessario conoscere il codice dell&#39;ambito.

   Per impostare un valore di configurazione per l&#39;ambito predefinito, non è necessario eseguire alcuna operazione.

### Trova il percorso di configurazione

Consulta i seguenti riferimenti:

- [Riferimento ai percorsi di configurazione sensibili e specifici del sistema](../reference/config-reference-sens.md)
- [Riferimento ai percorsi di configurazione dei pagamenti](../reference/config-reference-payment.md)
- [Altri percorsi di configurazione di riferimento](../reference/config-reference-general.md)
- [Riferimento ai percorsi di configurazione dell’estensione Commerce Enterprise B2B](../reference/config-reference-b2b.md)

### Trovare il codice ambito

Puoi trovare il codice ambito nel database Commerce o nell’amministratore di Commerce.

**Per trovare il codice ambito nell’amministratore**:

1. Accedi all’amministratore come utente che può visualizzare siti web e archiviare visualizzazioni.
1. Clic **[!UICONTROL Stores]** > Impostazioni > **[!UICONTROL All Stores]**.
1. Nel riquadro di destra fare clic sul nome della visualizzazione del sito Web o della visualizzazione dello store per visualizzarne il codice.

   Nella figura seguente viene illustrato un esempio di codice di un sito Web.

   ![Ottieni un codice di visualizzazione del sito web o store dall’amministratore](../../assets/configuration/website-code.png)

1. Continua con [Imposta valori](#set-values).

**Per trovare il codice di ambito nel database**:

I codici di ambito per i siti web e le visualizzazioni degli archivi vengono memorizzati nel database di Commerce nel `store_website` e `store` tabelle.

1. Connettersi al database Commerce.

   ```bash
   mysql -u <Commerce database username> -p
   ```

1. Immettete i seguenti comandi:

   ```shell
   use <Commerce database name>;
   ```

   ```shell
   SELECT * FROM store;
   ```

   ```shell
   SELECT * FROM store_website;
   ```

   Di seguito è riportato un esempio di risultato:

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

**Per impostare i valori di configurazione specifici del sistema**:

```bash
bin/magento config:set [--scope="..."] [--scope-code="..."] [-le | --lock-env] [-lc | --lock-config] path value
```

**Per impostare i valori di configurazione sensibili**:

```bash
bin/magento config:sensitive:set [--scope="..."] [--scope-code="..."] path value
```

La tabella seguente descrive `set` parametri comando:

| Parametro | Descrizione |
| --- | --- |
| `--scope` | Ambito della configurazione. I valori possibili sono `default`, `website`, o `store`. Il valore predefinito è `default`. |
| `--scope-code` | Codice ambito della configurazione (codice sito Web o codice visualizzazione archivio) |
| `-e or --lock-env` | Blocca il valore in modo che non possa essere modificato nell’amministratore o modifica un’impostazione già bloccata nell’amministratore. Il comando scrive il valore in `<Commerce base dir>/app/etc/env.php` file. |
| `-c or --lock-config` | Blocca il valore in modo che non possa essere modificato nell’amministratore o modifica un’impostazione già bloccata nell’amministratore. Il comando scrive il valore in `<Commerce base dir>/app/etc/config.php` file. Il `--lock-config` l&#39;opzione sovrascrive `--lock-env` se si specificano entrambe le opzioni. |
| `path` | _Obbligatorio_. Percorso di configurazione |
| `value` | _Obbligatorio_. Valore della configurazione |

>[!INFO]
>
>A partire dalla versione Commerce 2.2.4, la `--lock-env` e `--lock-config` opzioni sostituiscono `--lock` opzione.
>
>Se si utilizza `--lock-env` o `--lock-config` per impostare o modificare un valore, è necessario utilizzare l&#39; [`bin/magento app:config:import` comando](../cli/import-configuration.md) per importare l’impostazione prima di accedere all’Admin o alla vetrina.

Se si immette un percorso di configurazione errato, questo comando restituirà un errore

```text
The "wrong/config/path" does not exist
```

Per ulteriori informazioni, consulta una delle sezioni seguenti:

- [Imposta i valori di configurazione che possono essere modificati in Admin](#set-configuration-values-that-can-be-edited-in-the-admin)
- [Imposta i valori di configurazione che non possono essere modificati in Admin](#set-configuration-values-that-cannot-be-edited-in-the-admin)

### Imposta i valori di configurazione che possono essere modificati in Admin

Utilizzare `bin/magento config:set` _senza_ `--lock-env` o `--lock-config` per scrivere il valore nel database. I valori impostati in questo modo possono essere modificati in Admin.

Di seguito sono riportati alcuni esempi per l’impostazione di un URL di base dello store:

Impostare l&#39;URL di base per l&#39;ambito predefinito:

```bash
bin/magento config:set web/unsecure/base_url http://example.com/
```

Imposta l’URL di base per `base` sito Web:

```bash
bin/magento config:set --scope=websites --scope-code=base web/unsecure/base_url http://example2.com/
```

Imposta l’URL di base per `test` visualizzazione store:

```bash
bin/magento config:set --scope=stores --scope-code=test web/unsecure/base_url http://example3.com/
```

### Imposta i valori di configurazione che non possono essere modificati in Admin

Se si utilizza `--lock-env`  come segue, il comando salva il valore di configurazione in `<Commerce base dir>/app/etc/env.php` e disabilita il campo per la modifica di questo valore in Admin.

```bash
bin/magento config:set --lock-env --scope=stores --scope-code=default web/unsecure/base_url http://example3.com
```

È possibile utilizzare `--lock-env` opzione per impostare i valori di configurazione se Commerce non è installato. Tuttavia, è possibile impostare valori solo per l&#39;ambito predefinito.

>[!INFO]
>
>Il `env.php` file specifico del sistema. Non è consigliabile trasferirla in un altro sistema. Puoi utilizzarlo per sovrascrivere i valori di configurazione dal database. Ad esempio, è possibile estrarre un dump del database da un altro sistema e sovrascrivere il `base_url` e altri valori in modo da non dover modificare il database.

Se si utilizza `--lock-config` come segue, il valore di configurazione viene salvato in `<Commerce base dir>/app/etc/config.php`. Il campo per la modifica di questo valore in Amministrazione è disabilitato.

```bash
bin/magento config:set --lock-config --scope=stores --scope-code=default web/url/use_store 1
```

È possibile utilizzare `--lock-config` per impostare i valori di configurazione se Commerce non è installato. Tuttavia, è possibile impostare valori solo per l&#39;ambito predefinito.

>[!INFO]
>
>È possibile trasferire `config.php` a un altro sistema per utilizzare gli stessi valori di configurazione. Ad esempio, se disponi di un sistema di test, utilizzando lo stesso `config.php` significa che non è necessario impostare nuovamente gli stessi valori di configurazione.

## Visualizza il valore delle impostazioni di configurazione

Opzioni comando:

```bash
bin/magento config:show [--scope[="..."]] [--scope-code[="..."]] path
```

dove

- `--scope` è l’ambito della configurazione (impostazione predefinita, sito web, archivio). Il valore predefinito è `default`
- `--scope-code` è il codice ambito della configurazione (codice sito web o codice visualizzazione archivio)
- `path` è il percorso di configurazione in formato prima_parte/seconda_parte/terza_parte/ecc. (_obbligatorio_)

>[!INFO]
>
>Il `bin/magento config:show` visualizza i valori di qualsiasi [valori crittografati](../reference/config-reference-sens.md) come serie di asterischi: `******`.

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

**Per visualizzare l&#39;URL di base per l&#39;ambito predefinito**:

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
