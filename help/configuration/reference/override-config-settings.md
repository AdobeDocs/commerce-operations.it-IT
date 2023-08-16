---
title: Ignora impostazioni di configurazione
description: Scopri come utilizzare le variabili di ambiente per ignorare le impostazioni di configurazione.
exl-id: 788fd3cd-f8c1-4514-8141-547fed36e9ce
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1225'
ht-degree: 0%

---

# Ignora impostazioni di configurazione

Questo argomento illustra come derivare il nome di una variabile di ambiente conoscendo un percorso di configurazione. Puoi sovrascrivere le impostazioni di configurazione di Adobe Commerce utilizzando le variabili di ambiente. Ad esempio, puoi sovrascrivere il valore dell’URL live di un elaboratore di pagamenti sul sistema di produzione.

Puoi sovrascrivere il valore di _qualsiasi_ impostazioni di configurazione utilizzando variabili di ambiente; tuttavia, l’Adobe consiglia di mantenere impostazioni coerenti utilizzando il file di configurazione condiviso, `config.php`e il file di configurazione specifico del sistema, `env.php`, come discusso in [Panoramica generale sulla distribuzione](../deployment/overview.md).

>[!TIP]
>
>Consulta la sezione [Configurare gli ambienti](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html) argomento in _Guida di Commerce su infrastruttura cloud_.

## Variabili di ambiente

Un nome di variabile di ambiente è costituito dal relativo ambito seguito dal relativo percorso di configurazione in un particolare formato. Nelle sezioni seguenti viene illustrato come determinare un nome di variabile in modo più dettagliato.

È possibile utilizzare le variabili per uno dei seguenti elementi:

- [Valori sensibili](config-reference-sens.md) deve essere impostato utilizzando le variabili di ambiente o [`magento config:sensitive:set`](../cli/set-configuration-values.md) comando.
- I valori specifici del sistema devono essere impostati utilizzando:

   - Variabili di ambiente
   - Il [`magento config:set`](../cli/set-configuration-values.md) comando
   - L’amministratore seguito da [`magento app:config:dump` comando](../cli/export-configuration.md)

I percorsi di configurazione si trovano in:

- [Riferimento ai percorsi di configurazione sensibili e specifici del sistema](config-reference-sens.md)
- [Riferimento ai percorsi di configurazione dei pagamenti](config-reference-payment.md)
- [Riferimento ai percorsi di configurazione dell’estensione Commerce B2B](config-reference-b2b.md)
- [Altri percorsi di configurazione di riferimento](config-reference-general.md)

### Nomi variabili

Il formato generale dei nomi delle variabili delle impostazioni di sistema è il seguente:

`<SCOPE>__<SYSTEM__VARIABLE__NAME>`

`<SCOPE>` può essere:

- Ambito globale (ovvero l&#39;impostazione globale per _tutto_ ambiti)

  Le variabili di ambito globali hanno il seguente formato:

  `CONFIG__DEFAULT__<SYSTEM__VARIABLE__NAME>`

- Un ambito specifico (ovvero l&#39;impostazione influisce solo su una visualizzazione store o su un sito Web specifici)

  Le variabili dell’ambito della visualizzazione archivio, ad esempio, hanno il seguente formato:

  `CONFIG__STORES__ <STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>`

  Per ulteriori informazioni sugli ambiti, consulta:

   - [Passaggio 1: trovare il valore di ambito della visualizzazione del sito Web o dello store](#step-1-find-the-website-or-store-view-scope-value)
   - [Argomento della Guida utente di Commerce sull’ambito](https://docs.magento.com/user-guide/configuration/scope.html)
   - [Riferimento rapido ambito](https://docs.magento.com/user-guide/stores/store-scope-reference.html)

`<SYSTEM__VARIABLE__NAME>` è il percorso di configurazione con caratteri di sottolineatura doppia sostituiti da `/`. Per ulteriori informazioni, consulta [Passaggio 2: impostare le variabili di sistema](#step-2-set-global-website-or-store-view-variables).

### Formato variabile

`<SCOPE>` è separato da `<SYSTEM__VARIABLE__NAME>` da due caratteri di sottolineatura.

`<SYSTEM__VARIABLE__NAME>` deriva da un&#39;impostazione di configurazione _percorso di configurazione_, che è un `/` stringa delimitata che identifica in modo univoco una determinata impostazione. Sostituisci ogni `/` nel percorso di configurazione con due caratteri di sottolineatura per creare la variabile di sistema.

Se un percorso di configurazione contiene un carattere di sottolineatura, questo rimane nella variabile.

Un elenco completo dei percorsi di configurazione è disponibile in:

- [Riferimento ai percorsi di configurazione sensibili e specifici del sistema](config-reference-sens.md)
- [Riferimento ai percorsi di configurazione dei pagamenti](config-reference-payment.md)
- [Riferimento ai percorsi di configurazione dell’estensione Commerce Enterprise B2B](config-reference-b2b.md)
- [Altri percorsi di configurazione di riferimento](config-reference-general.md)

## Passaggio 1: trovare il valore di ambito della visualizzazione del sito Web o dello store

Questa sezione descrive come trovare e impostare i valori di configurazione di sistema per _ambito_ (visualizzazione store o sito Web). Per impostare le variabili di ambito globali, vedere [Passaggio 2: impostare le variabili di visualizzazione globale, del sito Web o dello store](#step-2-set-global-website-or-store-view-variables).

I valori di ambito provengono da `store`, `store_group`, e `store_website` tabelle.

- Il `store` tabella specifica i nomi e i codici della vista archivio
- Il `store_website` tabella specifica i nomi e i codici dei siti Web

Puoi anche trovare i valori del codice utilizzando l’Admin.

Come leggere la tabella:

- `Path in Admin` colonna

  I valori prima della virgola sono percorsi nella navigazione dell’amministratore. I valori dopo la virgola sono opzioni nel riquadro di destra.

- `Variable name` column è il nome della variabile di ambiente corrispondente.

  Se lo desideri, puoi specificare i valori di sistema per questi parametri di configurazione come variabili di ambiente.

   - L&#39;intero nome della variabile è sempre TUTTO MAIUSC
   - Inizia un nome di variabile con `CONFIG__` (nota due caratteri di sottolineatura)
   - È possibile trovare `<STORE_VIEW_CODE>` o `<WEBSITE_CODE>` parte del nome di una variabile nel database Admin o Commerce, come indicato nelle sezioni seguenti.
   - Puoi trovare `<SYSTEM__VARIABLE__NAME>` come discusso in [Passaggio 2: impostare le variabili di visualizzazione globale, del sito Web o dello store](#step-2-set-global-website-or-store-view-variables).

### Trovare un ambito di visualizzazione sito web o store nell’Amministratore

Nella tabella seguente viene riepilogato come trovare il valore della visualizzazione del sito Web o dello store nell&#39;amministratore.

| Descrizione | Percorso in Admin | Nome variabile |
|--------------|--------------|----------------------|
| Creare, modificare ed eliminare le visualizzazioni dello store | **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** | `CONFIG__STORES__<STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>` |
| Creazione, modifica ed eliminazione di siti Web | **[!UICONTROL Stores]** > **[!UICONTROL All Store]s** | `CONFIG__WEBSITES__<WEBSITE_CODE>__<SYSTEM__VARIABLE__NAME>` |

Ad esempio, per trovare un valore di ambito di visualizzazione sito web o store nell’Admin:

1. Accedi all’amministratore come utente autorizzato a visualizzare i siti web.
1. Clic **[!UICONTROL Stores]** > **[!UICONTROL All Store]s**.
1. Fai clic sul nome di una visualizzazione sito web o store.

   Il riquadro di destra viene visualizzato in modo simile al seguente.

   ![Trovare un codice sito Web](../../assets/configuration/website-code.png)

1. Il nome dell&#39;ambito viene visualizzato in **[!UICONTROL Code]** campo.
1. Continua con [Passaggio 2: impostare le variabili di visualizzazione globale, del sito Web o dello store](#step-2-set-global-website-or-store-view-variables).

### Trovare un ambito di visualizzazione sito Web o archivio nel database

Per ottenere questi valori dal database:

1. Accedi al sistema di sviluppo come proprietario del file system, se non lo hai già fatto.
1. Immetti il comando seguente:

   ```bash
   mysql -u <database-username> -p
   ```

1. Alla `mysql>` immettete i seguenti comandi nell&#39;ordine indicato:

   ```shell
   use <database-name>;
   ```

1. Utilizzare le query SQL seguenti per trovare i valori rilevanti:

   ```shell
   SELECT * FROM STORE;
   SELECT * FROM STORE_WEBSITE;
   ```

   Di seguito è riportato un esempio:

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

1. Utilizza il valore di `code` come nome dell&#39;ambito, non come `name` valore.

   Ad esempio, per impostare una variabile di configurazione per il sito Web di prova, utilizza il formato seguente:

   ```shell
   CONFIG__WEBSITES__TEST1__<SYSTEM__VARIABLE__NAME>
   ```

   dove `<SYSTEM__VARIABLE__NAME>` viene dalla sezione successiva.

## Passaggio 2: impostare le variabili di visualizzazione globale, del sito Web o dello store

Questa sezione illustra come impostare le variabili di sistema.

- Per impostare i valori per l&#39;ambito globale, ovvero tutti i siti Web, gli archivi e le visualizzazioni degli archivi, inizia il nome della variabile con `CONFIG__DEFAULT__`.

- Per impostare un valore per una particolare visualizzazione store o sito Web, inizia il nome della variabile come descritto in [Passaggio 1: trovare il valore dell&#39;ambito](#step-1-find-the-website-or-store-view-scope-value):

   - `CONFIG__WEBSITES`
   - `CONFIG__STORES`

- L’ultima parte del nome della variabile è il percorso di configurazione, univoco per ogni impostazione di configurazione.

[Vedi alcuni esempi](#examples).

La tabella seguente mostra alcune variabili di esempio.

| Descrizione | Percorso in Admin (omesso **Negozi** > **Impostazioni** > **Configurazione**) | Nome variabile |
|--------------|--------------|----------------------|
| Nome host del server Elasticsearch | Catalogo > **Catalogo**, **Nome host server di Elasticsearch** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME` |
| porta server Elasticsearch | Catalogo > **Catalogo**, **Porta server Elasticsearch** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_PORT` |
| Origine paese di spedizione | Vendite > **Impostazioni spedizione** | `<SCOPE>__SHIPPING__ORIGIN__COUNTRY_ID` |
| URL amministratore personalizzato | Avanzate > **Amministratore** | `<SCOPE>__ADMIN__URL__CUSTOM` |
| Percorso amministratore personalizzato | Avanzate > **Amministratore** | `<SCOPE>__ADMIN__URL__CUSTOM_PATH` |

## Esempi

Questa sezione mostra come trovare i valori di alcune variabili di esempio.

### Nome host del server Elasticsearch

Per trovare il nome della variabile per la minimizzazione globale di HTML:

1. Determinare l&#39;ambito.

   È l’ambito globale, quindi il nome della variabile inizia con `CONFIG__DEFAULT__`

1. Il resto del nome della variabile è `CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`.

   **Risultato**: il nome della variabile è `CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`

### Origine paese di spedizione

Per trovare il nome della variabile per l&#39;origine del paese di spedizione:

1. Determinare l&#39;ambito.

   Trovare l’ambito in [database](#find-a-website-or-store-view-scope-in-the-database) come descritto in Passaggio 1: Trovare il valore dell&#39;ambito della visualizzazione del sito Web o dello store. (Puoi anche trovare il valore in Admin, come mostrato nella [tabella nel passaggio 2: impostare le variabili di visualizzazione globale, del sito Web o dello store](#step-2-set-global-website-or-store-view-variables.

   Ad esempio, l’ambito potrebbe essere `CONFIG__WEBSITES__DEFAULT`.

1. Il resto del nome della variabile è `SHIPPING__ORIGIN__COUNTRY_ID`.

   **Risultato**: il nome della variabile è `CONFIG__WEBSITES__DEFAULT__SHIPPING__ORIGIN__COUNTRY_ID`

## Come utilizzare le variabili di ambiente

Imposta i valori di configurazione come variabili utilizzando PHP [`$_ENV`](https://php.net/manual/en/reserved.variables.environment.php) associa array. È possibile impostare i valori in qualsiasi script PHP eseguito durante l’esecuzione di Commerce.

>[!TIP]
>
>Impostazione dei valori delle variabili in `index.php` o `pub/index.php` non funziona sempre come previsto, in quanto è possibile utilizzare punti di ingresso dell’applicazione diversi a seconda della configurazione del server web. Inserendo `$_ENV` direttive in `app/bootstrap.php` indipendentemente dai diversi punti di ingresso dell&#39;applicazione, `$_ENV` le direttive vengono sempre eseguite dal `app/bootstrap.php` caricamenti di file come parte dell’architettura Commerce.

Esempio di impostazione di due `$_ENV` valori:

```php
$_ENV['CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME'] = 'http://search.example.com';
$_ENV['CONFIG__DEFAULT__GENERAL__STORE_INFORMATION__MERCHANT_VAT_NUMBER'] = '1234';
```

Un esempio dettagliato è mostrato in [Impostare i valori di configurazione utilizzando le variabili di ambiente](../deployment/example-environment-variables.md).

>[!WARNING]
>
>- Per utilizzare i valori impostati in `$_ENV` , è necessario impostare `variables_order = "EGPCS"`(Ambiente, Get, Post, Cookie e Server) nel tuo `php.ini` file. Per ulteriori informazioni, consulta [Documentazione PHP](https://www.php.net/manual/en/ini.core.php).
>
>- Per Adobe Commerce su infrastruttura cloud, se tenti di sovrascrivere le impostazioni di configurazione utilizzando [Interfaccia Web di Project](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-the-project), è necessario anteporre al nome della variabile `env:`. Ad esempio:
>
>![Esempio di variabile di ambiente](../../assets/configuration/cloud-console-envvariable.png)
