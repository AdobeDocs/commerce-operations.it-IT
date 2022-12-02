---
title: Ignora impostazioni di configurazione
description: Scopri come utilizzare le variabili di ambiente per ignorare le impostazioni di configurazione.
source-git-commit: 8102c083bb0216bbdcad2882f39f7711b9cee52b
workflow-type: tm+mt
source-wordcount: '1228'
ht-degree: 0%

---


# Ignora impostazioni di configurazione

Questo argomento illustra come derivare un nome di variabile di ambiente conoscendo un percorso di configurazione. Puoi sovrascrivere le impostazioni di configurazione di Adobe Commerce utilizzando le variabili di ambiente. Ad esempio, puoi ignorare il valore dell&#39;URL live di un elaboratore di pagamenti sul tuo sistema di produzione.

È possibile ignorare il valore di _qualsiasi_ impostazione della configurazione mediante variabili di ambiente; tuttavia, Adobe consiglia di mantenere impostazioni coerenti utilizzando il file di configurazione condiviso, `config.php`e il file di configurazione specifico del sistema, `env.php`, come illustrato in [Panoramica generale sulla distribuzione](../deployment/overview.md).

>[!TIP]
>
>Consulta la sezione [Configurare gli ambienti](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html) nell&#39;argomento _Guida a Commerce on Cloud Infrastructure_.

## Variabili di ambiente

Un nome di variabile di ambiente è costituito dal relativo ambito seguito dal relativo percorso di configurazione in un formato specifico. Nelle sezioni seguenti viene illustrato come determinare un nome di variabile in modo più dettagliato.

Puoi utilizzare le variabili per uno dei seguenti elementi:

- [Valori sensibili](config-reference-sens.md) deve essere impostato utilizzando le variabili di ambiente o [`magento config:sensitive:set`](../cli/set-configuration-values.md) comando.
- I valori specifici del sistema devono essere impostati utilizzando:

   - Variabili di ambiente
   - La [`magento config:set`](../cli/set-configuration-values.md) command
   - L’amministratore seguito da [`magento app:config:dump` command](../cli/export-configuration.md)

I percorsi di configurazione si trovano in:

- [Riferimento per i percorsi di configurazione sensibili e specifici del sistema](config-reference-sens.md)
- [Riferimento per i percorsi di configurazione dei pagamenti](config-reference-payment.md)
- [Riferimento per i percorsi di configurazione dell’estensione Commerce B2B](config-reference-b2b.md)
- [Riferimento ad altri percorsi di configurazione](config-reference-general.md)

### Nomi di variabile

Il formato generale dei nomi delle variabili delle impostazioni di sistema è il seguente:

`<SCOPE>__<SYSTEM__VARIABLE__NAME>`

`<SCOPE>` può essere:

- Ambito globale (ovvero, impostazione globale per _tutto_ ambiti)

   Le variabili di ambito globale hanno il seguente formato:

   `CONFIG__DEFAULT__<SYSTEM__VARIABLE__NAME>`

- Un ambito specifico (ovvero, l&#39;impostazione interessa solo una visualizzazione store o un sito Web specifici)

   Le variabili dell&#39;ambito della visualizzazione archivio, ad esempio, hanno il formato seguente:

   `CONFIG__STORES__ <STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>`

   Per ulteriori informazioni sugli ambiti, vedi:

   - [Passaggio 1: Trova il valore dell&#39;ambito della visualizzazione del sito web o del negozio](#step-1-find-the-website-or-store-view-scope-value)
   - [Argomento della Guida utente di Commerce sull’ambito](https://docs.magento.com/user-guide/configuration/scope.html)
   - [Riferimento rapido ambito](https://docs.magento.com/user-guide/stores/store-scope-reference.html)

`<SYSTEM__VARIABLE__NAME>` è il percorso di configurazione con caratteri di sottolineatura doppi sostituiti da `/`. Per ulteriori informazioni, consulta [Passaggio 2: Imposta variabili di sistema](#step-2-set-global-website-or-store-view-variables).

### Formato variabile

`<SCOPE>` è separato da `<SYSTEM__VARIABLE__NAME>` per due caratteri di sottolineatura.

`<SYSTEM__VARIABLE__NAME>` deriva da un&#39;impostazione di configurazione _percorso di configurazione_, che è un `/` stringa delimitata che identifica in modo univoco una particolare impostazione. Sostituisci ciascuno `/` nel percorso di configurazione con due caratteri di sottolineatura per creare la variabile di sistema.

Se un percorso di configurazione contiene un carattere di sottolineatura, il carattere di sottolineatura rimane nella variabile .

Un elenco completo dei percorsi di configurazione si trova in:

- [Riferimento per i percorsi di configurazione sensibili e specifici del sistema](config-reference-sens.md)
- [Riferimento per i percorsi di configurazione dei pagamenti](config-reference-payment.md)
- [Riferimento per i percorsi di configurazione dell’estensione Commerce Enterprise B2B](config-reference-b2b.md)
- [Riferimento ad altri percorsi di configurazione](config-reference-general.md)

## Passaggio 1: Trova il valore dell&#39;ambito della visualizzazione del sito web o del negozio

Questa sezione illustra come trovare e impostare i valori di configurazione del sistema per _scope_ (visualizzazione store o sito web). Per impostare le variabili di ambito globale, vedi [Passaggio 2: Impostare variabili globali, di siti web o di visualizzazione store](#step-2-set-global-website-or-store-view-variables).

I valori di ambito provengono dal `store`, `store_group`e `store_website` tabelle.

- La `store` la tabella specifica i nomi e i codici della vista archivio
- La `store_website` tabella specifica nomi e codici del sito web

Puoi anche trovare i valori del codice utilizzando l’amministratore.

Come leggere la tabella:

- `Path in Admin` column

   I valori prima della virgola sono percorsi nella navigazione Admin. I valori dopo la virgola sono opzioni nel riquadro a destra.

- `Variable name` column è il nome della variabile di ambiente corrispondente.

   Puoi specificare i valori di sistema per questi parametri di configurazione come variabili di ambiente, se lo desideri.

   - L&#39;intero nome della variabile è sempre ALL CAPS
   - Avvia un nome di variabile con `CONFIG__` (nota due caratteri di sottolineatura)
   - È possibile trovare le `<STORE_VIEW_CODE>` o `<WEBSITE_CODE>` parte del nome di una variabile nel database Admin o Commerce, come indicato nelle sezioni seguenti.
   - È possibile trovare `<SYSTEM__VARIABLE__NAME>` discussi in [Passaggio 2: Impostare variabili globali, di siti web o di visualizzazione store](#step-2-set-global-website-or-store-view-variables).

### Trova un sito web o un ambito di visualizzazione store nell’Admin

Nella tabella seguente viene riepilogato come trovare il valore della visualizzazione del sito Web o dell’archivio nell’amministratore.

| Descrizione | Percorso in Admin | Nome della variabile |
|--------------|--------------|----------------------|
| Creare, modificare, eliminare le viste store | **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** | `CONFIG__STORES__<STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>` |
| Creare, modificare, eliminare siti web | **[!UICONTROL Stores]** > **[!UICONTROL All Store]s** | `CONFIG__WEBSITES__<WEBSITE_CODE>__<SYSTEM__VARIABLE__NAME>` |

Ad esempio, per trovare un valore dell’ambito di visualizzazione del sito web o dell’archivio nell’amministratore:

1. Accedi all’amministratore come utente autorizzato a visualizzare i siti web.
1. Fai clic su **[!UICONTROL Stores]** > **[!UICONTROL All Store]s**.
1. Fare clic sul nome di una visualizzazione sito Web o store.

   Il riquadro a destra viene visualizzato in modo simile al seguente.

   ![Trovare un codice del sito web](../../assets/configuration/website-code.png)

1. Il nome dell&#39;ambito viene visualizzato nel **[!UICONTROL Code]** campo .
1. Continua con [Passaggio 2: Impostare variabili globali, di siti web o di visualizzazione store](#step-2-set-global-website-or-store-view-variables).

### Trovare un sito Web o un ambito di visualizzazione del negozio nel database

Per ottenere questi valori dal database:

1. Accedi al tuo sistema di sviluppo come [proprietario del file system](https://glossary.magento.com/magento-file-system-owner) se non lo hai già fatto.
1. Immetti il seguente comando:

   ```bash
   mysql -u <database-username> -p
   ```

1. Alla `mysql>` immettere i seguenti comandi nell&#39;ordine mostrato:

   ```shell
   use <database-name>;
   ```

1. Utilizzare le seguenti query SQL per trovare i valori pertinenti:

   ```shell
   SELECT * FROM STORE;
   SELECT * FROM STORE_WEBSITE;
   ```

   Segue un esempio:

   ```shell
   mysql> SELECT * FROM STORE_WEBSITE;
   +------------+-------+--------------+------------+------------------+------------+
   | website_id | code  | name         | sort_order | default_group_id | is_default |
   +------------+-------+--------------+------------+------------------+------------+
   |          0 | admin | Admin        |          0 |                0 |          0 |
   |          1 | base  | Main Website |          0 |                1 |          1 |
   |          2 | test1 | Test Website |          0 |                3 |          0 |
   +------------+-------+--------------+------------+------------------+------------+
   ```

1. Utilizza il valore del `code` come nome dell’ambito, non come colonna `name` valore.

   Ad esempio, per impostare una variabile di configurazione per Test Website, utilizza il formato seguente:

   ```shell
   CONFIG__WEBSITES__TEST1__<SYSTEM__VARIABLE__NAME>
   ```

   dove `<SYSTEM__VARIABLE__NAME>` viene dalla sezione successiva.

## Passaggio 2: Impostare variabili globali, di siti web o di visualizzazione store

Questa sezione illustra come impostare le variabili di sistema.

- Per impostare i valori per l’ambito globale (ovvero, tutti i siti web, gli archivi e le viste Store), inizia il nome della variabile con `CONFIG__DEFAULT__`.

- Per impostare un valore per una particolare visualizzazione store o sito Web, avvia il nome della variabile come descritto in [Passaggio 1: Trova il valore dell&#39;ambito](#step-1-find-the-website-or-store-view-scope-value):

   - `CONFIG__WEBSITES`
   - `CONFIG__STORES`

- L&#39;ultima parte del nome della variabile è il percorso di configurazione, univoco per ogni impostazione di configurazione.

[Alcuni esempi](#examples).

La tabella seguente mostra alcune variabili di esempio.

| Descrizione | Percorso in Admin (omettendo) **Negozi** > **Impostazioni** > **Configurazione**) | Nome della variabile |
|--------------|--------------|----------------------|
| Nome host del server di Elasticsearch | Catalogo > **Catalogo**, **Nome host del server Elasticsearch** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME` |
| Porta server di Elasticsearch | Catalogo > **Catalogo**, **Porta server Elasticsearch** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_PORT` |
| Origine del paese di spedizione | Vendite > **Impostazioni di spedizione** | `<SCOPE>__SHIPPING__ORIGIN__COUNTRY_ID` |
| URL amministratore personalizzato | Avanzate > **Amministratore** | `<SCOPE>__ADMIN__URL__CUSTOM` |
| Percorso amministratore personalizzato | Avanzate > **Amministratore** | `<SCOPE>__ADMIN__URL__CUSTOM_PATH` |

## Esempi

Questa sezione mostra come trovare i valori di alcune variabili di esempio.

### Nome host del server di Elasticsearch

Per trovare il nome della variabile per la minimizzazione globale di HTML:

1. Determina l&#39;ambito.

   Si tratta dell’ambito globale con cui inizia il nome della variabile `CONFIG__DEFAULT__`

1. Il resto del nome della variabile è `CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`.

   **Risultato**: Il nome della variabile è `CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`

### Origine del paese di spedizione

Per trovare il nome della variabile per l&#39;origine del paese di spedizione:

1. Determina l&#39;ambito.

   Trova l&#39;ambito nel [database](#find-a-website-or-store-view-scope-in-the-database) come descritto nel passaggio 1: Trova il valore dell&#39;ambito della visualizzazione del sito web o del negozio. (Puoi anche trovare il valore nell’amministratore come mostrato nella [tabella al passaggio 2: Impostare variabili globali, di siti web o di visualizzazione store](#step-2-set-global-website-or-store-view-variables.

   Ad esempio, l&#39;ambito potrebbe essere `CONFIG__WEBSITES__DEFAULT`.

1. Il resto del nome della variabile è `SHIPPING__ORIGIN__COUNTRY_ID`.

   **Risultato**: Il nome della variabile è `CONFIG__WEBSITES__DEFAULT__SHIPPING__ORIGIN__COUNTRY_ID`

## Come utilizzare le variabili di ambiente

Imposta i valori di configurazione come variabili utilizzando PHP [`$_ENV`](https://php.net/manual/en/reserved.variables.environment.php) associa array. Puoi impostare i valori in qualsiasi script PHP in esecuzione quando Commerce viene eseguito.

>[!TIP]
>
>Impostazione dei valori variabili in `index.php` o `pub/index.php` non funziona sempre come previsto, in quanto è possibile utilizzare diversi punti di ingresso dell&#39;applicazione a seconda della configurazione del server web. Posizionamento `$_ENV` le direttive `app/bootstrap.php` , indipendentemente dai diversi punti di ingresso dell&#39;applicazione, il `$_ENV` le direttive vengono sempre eseguite dal `app/bootstrap.php` i file vengono caricati come parte dell’architettura Commerce.

Esempio di impostazione di due `$_ENV` i valori seguenti:

```php
$_ENV['CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME'] = 'http://search.example.com';
$_ENV['CONFIG__DEFAULT__GENERAL__STORE_INFORMATION__MERCHANT_VAT_NUMBER'] = '1234';
```

Un esempio dettagliato è mostrato in [Impostare i valori di configurazione utilizzando le variabili di ambiente](../deployment/example-environment-variables.md).

>[!WARNING]
>
>- Per utilizzare i valori impostati in `$_ENV` array, è necessario impostare `variables_order = "EGPCS"`(Ambiente, Get, Post, Cookie e Server) nel `php.ini` file. Per maggiori dettagli, vedi [Documentazione PHP](https://www.php.net/manual/en/ini.core.php).
>
>- Per Adobe Commerce sull&#39;infrastruttura cloud, se tenti di ignorare le impostazioni di configurazione utilizzando [Interfaccia Web progetto](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-the-project), devi anteporre il nome della variabile a `env:`. Ad esempio:
>
>![Esempio di variabile di ambiente](../../assets/configuration/cloud-console-envvariable.png)
