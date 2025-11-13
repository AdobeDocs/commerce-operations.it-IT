---
title: Impostare i valori di configurazione
description: Scopri come impostare i valori di configurazione e modificare i valori Admin bloccati in Adobe Commerce. Scopri i comandi e le tecniche di configurazione avanzata.
exl-id: 1dc2412d-50b3-41fb-ab22-3eccbb086302
source-git-commit: 2672c696d672ad72bef7537570ed630bc33c41b4
workflow-type: tm+mt
source-wordcount: '1101'
ht-degree: 0%

---

# Impostare i valori di configurazione

{{file-system-owner}}

In questo argomento vengono descritti i comandi di configurazione avanzati che è possibile utilizzare per:

- Imposta qualsiasi opzione di configurazione dalla riga di comando
- Facoltativamente, blocca qualsiasi opzione di configurazione in modo che il suo valore non possa essere modificato in Admin
- Modificare un’opzione di configurazione bloccata in Admin

È possibile utilizzare questi comandi per impostare la configurazione di Commerce manualmente o utilizzando gli script. Le opzioni di configurazione vengono impostate utilizzando un _percorso di configurazione_, ovvero una stringa delimitata da `/` che identifica in modo univoco tale opzione di configurazione. Puoi trovare i percorsi di configurazione nei seguenti riferimenti:

- [Riferimento ai percorsi di configurazione sensibili e specifici del sistema](../reference/config-reference-sens.md)
- [Riferimento ai percorsi di configurazione dei pagamenti](../reference/config-reference-payment.md)
- [Riferimento generale ai percorsi di configurazione](../reference/config-reference-general.md)
- [Riferimento ai percorsi di configurazione dell’estensione Commerce Enterprise B2B](../reference/config-reference-b2b.md)

È possibile impostare i valori nei seguenti momenti:

- Prima di installare Commerce, è possibile impostare i valori di configurazione solo per l&#39;ambito predefinito, in quanto è l&#39;unico ambito valido.

- Dopo aver installato Commerce, è possibile impostare i valori di configurazione per qualsiasi ambito di visualizzazione del sito Web o dell&#39;archivio.

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

Puoi trovare il codice ambito nel database di Commerce o nell’amministratore di Commerce.

**Per trovare il codice di ambito nell&#39;amministratore**:

1. Accedi all’amministratore come utente che può visualizzare siti web e archiviare visualizzazioni.
1. Fare clic su **[!UICONTROL Stores]** > Impostazioni > **[!UICONTROL All Stores]**.
1. Nel riquadro di destra fare clic sul nome della visualizzazione del sito Web o della visualizzazione dello store per visualizzarne il codice.

   Nella figura seguente viene illustrato un esempio di codice di un sito Web.

   ![Ottieni un codice di visualizzazione sito Web o store dall&#39;amministratore](../../assets/configuration/website-code.png)

1. Continua con [Imposta valori](#set-values).

**Per trovare il codice di ambito nel database**:

I codici di ambito per i siti Web e le visualizzazioni degli archivi vengono archiviati nel database di Commerce rispettivamente nelle tabelle `store_website` e `store`.

1. Connettersi al database di Commerce.

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

   ```
   [mysql]> SELECT * FROM store_website;
   +------------+-------+--------------+------------+------------------+------------+
   | website_id | code  | name         | sort_order | default_group_id | is_default |
   +------------+-------+--------------+------------+------------------+------------+
   |          0 | admin | Admin        |          0 |                0 |          0 |
   |          1 | base  | Main Website |          0 |                1 |          1 |
   |          2 | test1 | Test Website |          0 |                3 |          0 |
   +------------+-------+--------------+------------+------------------+------------+
   ```

   Utilizzare il valore nella colonna `code`.

1. Procedi alla sezione successiva.

## Imposta valori

**Per impostare i valori di configurazione specifici del sistema**:

```bash
bin/magento config:set [--scope="..."] [--scope-code="..."] [-le | --lock-env] [-lc | --lock-config] path value
```

**Per impostare i valori di configurazione sensibili**:

```bash
bin/magento config:sensitive:set [--scope="..."] [--scope-code="..."] path
```

Nella tabella seguente sono descritti i parametri del comando `set`:

| Parametro | Descrizione |
| --- |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `--scope` | Ambito della configurazione. I valori possibili sono `default`, `website` o `store`. Il valore predefinito è `default`. |
| `--scope-code` | Codice ambito della configurazione (codice sito Web o codice visualizzazione archivio) |
| `-e or --lock-env` | Blocca il valore in modo che non possa essere modificato nell’amministratore o modifica un’impostazione già bloccata nell’amministratore. Il comando scrive il valore nel file `<Commerce base dir>/app/etc/env.php`. |
| `-c or --lock-config` | Blocca il valore in modo che non possa essere modificato nell’amministratore o modifica un’impostazione già bloccata nell’amministratore. Il comando scrive il valore nel file `<Commerce base dir>/app/etc/config.php`. L&#39;opzione `--lock-config` sovrascrive `--lock-env` se si specificano entrambe le opzioni. |
| `path` | _Richiesto_. Percorso di configurazione |
| `value` | _Richiesto_. Il valore della configurazione. Sebbene possa essere passato come argomento separato in un comando CLI, Adobe consiglia di non specificarlo nel comando originale. Eseguire invece il comando senza il valore, quindi immettere il valore quando richiesto. Questo metodo impedisce la scrittura di valori di accesso sensibili in bash_history, che è il modo più sicuro per impostare la configurazione. |

>[!INFO]
>
>A partire da Commerce 2.2.4, le opzioni `--lock-env` e `--lock-config` sostituiscono l&#39;opzione `--lock`.
>
>Se si utilizza l&#39;opzione `--lock-env` o `--lock-config` per impostare o modificare un valore, è necessario utilizzare il comando [`bin/magento app:config:import`](../cli/import-configuration.md) per importare l&#39;impostazione prima di accedere all&#39;Admin o alla vetrina.

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

Impostare l&#39;URL di base per il sito Web `base`:

```bash
bin/magento config:set --scope=websites --scope-code=base web/unsecure/base_url http://example2.com/
```

Impostare l&#39;URL di base per la visualizzazione archivio `test`:

```bash
bin/magento config:set --scope=stores --scope-code=test web/unsecure/base_url http://example3.com/
```

### Imposta i valori di configurazione che non possono essere modificati in Admin

Se si utilizza l&#39;opzione `--lock-env` come indicato di seguito, il comando salva il valore di configurazione in `<Commerce base dir>/app/etc/env.php` e disabilita il campo per la modifica di questo valore in Admin.

```bash
bin/magento config:set --lock-env --scope=stores --scope-code=default web/unsecure/base_url http://example3.com
```

È possibile utilizzare l&#39;opzione `--lock-env` per impostare i valori di configurazione se Commerce non è installato. Tuttavia, è possibile impostare valori solo per l&#39;ambito predefinito.

>[!INFO]
>
>Il file `env.php` è specifico del sistema. Non è consigliabile trasferirla in un altro sistema. Puoi utilizzarlo per sovrascrivere i valori di configurazione dal database. È possibile, ad esempio, acquisire un dump del database da un altro sistema e sovrascrivere `base_url` e altri valori in modo da non dover modificare il database.

Se si utilizza l&#39;opzione `--lock-config` come segue, il valore di configurazione viene salvato in `<Commerce base dir>/app/etc/config.php`. Il campo per la modifica di questo valore in Amministrazione è disabilitato.

```bash
bin/magento config:set --lock-config --scope=stores --scope-code=default web/url/use_store 1
```

È possibile utilizzare `--lock-config` per impostare i valori di configurazione se Commerce non è installato. Tuttavia, è possibile impostare valori solo per l&#39;ambito predefinito.

>[!INFO]
>
>È possibile trasferire `config.php` a un altro sistema per utilizzare gli stessi valori di configurazione. Ad esempio, se si dispone di un sistema di test, l&#39;utilizzo dello stesso `config.php` significa che non è necessario impostare nuovamente gli stessi valori di configurazione.

## Visualizza il valore delle impostazioni di configurazione

Opzioni comando:

```bash
bin/magento config:show [--scope[="..."]] [--scope-code[="..."]] path
```

dove

- `--scope` è l&#39;ambito della configurazione (predefinito, sito Web, archivio). Il valore predefinito è `default`
- `--scope-code` è il codice ambito della configurazione (codice sito Web o codice visualizzazione archivio)
- `path` è il percorso di configurazione in formato first_part/second_part/third_part/etc (_required_)

>[!INFO]
>
>Il comando `bin/magento config:show` visualizza i valori di qualsiasi [valore crittografato](../reference/config-reference-sens.md) come una serie di asterischi: `**&#x200B;**&#x200B;**`.

### Esempi

**Per visualizzare tutte le configurazioni salvate**:

```bash
bin/magento config:show
```

Risultato:

```
web/unsecure/base_url - http://example.com/
general/region/display_all - 1
general/region/state_required - AT,BR,CA,CH,EE,ES,FI,LT,LV,RO,US
catalog/category/root_id - 2
analytics/subscription/enabled - 1
```

**Per visualizzare tutte le configurazioni salvate per il sito Web `base`**:

```bash
bin/magento config:show --scope=websites --scope-code=base
```

Risultato:

```
web/unsecure/base_url - http://example-for-website.com/
general/region/state_required - AT,BR,CA
```

**Per visualizzare l&#39;URL di base per l&#39;ambito predefinito**:

```bash
bin/magento config:show web/unsecure/base_url
```

Risultato:

```
web/unsecure/base_url - http://example.com/
```

**Per visualizzare l&#39;URL di base per il sito Web `base`**:

```bash
bin/magento config:show --scope=websites --scope-code=base web/unsecure/base_url
```

Risultato:

```
web/unsecure/base_url - http://example-for-website.com/
```

**Per visualizzare l&#39;URL di base per l&#39;archivio `default`**:

```bash
bin/magento config:show --scope=stores --scope-code=default web/unsecure/base_url
```

Risultato:

```
web/unsecure/base_url - http://example-for-store.com/
```

>[!INFO]
>
>Il codice ambito può includere solo lettere (a-z o A-Z), numeri (0-9) e caratteri di sottolineatura (_). Inoltre, il primo carattere deve essere una lettera. Se si utilizzano maiuscole o minuscole durante la creazione di una vista sito web o store, internamente la corrispondenza non distingue tra maiuscole e minuscole per consentire l’override delle impostazioni di configurazione tramite le variabili di ambiente. Vedere [Utilizzare le variabili di ambiente per sostituire le impostazioni di configurazione](../reference/override-config-settings.md#environment-variables).

