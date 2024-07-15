---
title: Ignora impostazioni di configurazione
description: Scopri come utilizzare le variabili di ambiente per ignorare le impostazioni di configurazione.
exl-id: 788fd3cd-f8c1-4514-8141-547fed36e9ce
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1202'
ht-degree: 0%

---

# Sostituisci impostazioni di configurazione

In questo argomento viene illustrato come derivare un nome di variabile d&#39;ambiente conoscendo un percorso di configurazione. Puoi ignorare le impostazioni di configurazione di Adobe Systems Commerce utilizzando le variabili di ambiente. Ad esempio, puoi sovrascrivere il valore dell’URL live di un elaboratore di pagamenti sul sistema di produzione.

È possibile sovrascrivere il valore dell&#39;impostazione di configurazione _any_ utilizzando variabili di ambiente; tuttavia, l&#39;Adobe consiglia di mantenere impostazioni coerenti utilizzando il file di configurazione condiviso, `config.php`, e il file di configurazione specifico del sistema, `env.php`, come descritto in [Panoramica generale sulla distribuzione](../deployment/overview.md).

>[!TIP]
>
>Consulta l&#39;argomento [Configurare gli ambienti](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-intro.html) nella _guida di Commerce sull&#39;infrastruttura cloud_.

## Variabili di ambiente

Un nome di variabile di ambiente è costituito dal relativo ambito seguito dal relativo percorso di configurazione in un particolare formato. Nelle sezioni seguenti viene illustrato come determinare un nome di variabile in modo più dettagliato.

È possibile utilizzare le variabili per uno dei seguenti elementi:

- [I valori sensibili](config-reference-sens.md) devono essere impostati utilizzando le variabili di ambiente o il comando [`magento config:sensitive:set`](../cli/set-configuration-values.md).
- I valori specifici del sistema devono essere impostati utilizzando:

   - Variabili di ambiente
   - Il comando [`magento config:set`](../cli/set-configuration-values.md)
   - L&#39;amministratore seguito dal comando [`magento app:config:dump`](../cli/export-configuration.md)

I percorsi di configurazione si trovano in:

- [Riferimenti sui percorsi di configurazione sensibili e specifici del sistema](config-reference-sens.md)
- [Riferimento sui percorsi di configurazione dei pagamenti](config-reference-payment.md)
- [Riferimento ai percorsi di configurazione dell’estensione Commerce B2B](config-reference-b2b.md)
- [Altri percorsi di configurazione di riferimento](config-reference-general.md)

### Variabile nomi

Di seguito è riportato il formato generale dei nomi delle variabili delle impostazioni di sistema:

`<SCOPE>__<SYSTEM__VARIABLE__NAME>`

`<SCOPE>` può essere:

- ambito globale (ovvero l&#39;impostazione globale per _tutti_ gli ambiti)

  Le variabili di ambito globali hanno il formato seguente:

  `CONFIG__DEFAULT__<SYSTEM__VARIABLE__NAME>`

- Un ambito specifico (ovvero, l&#39;impostazione interessa solo una visualizzazione store o un sito Web specifici)

  Le variabili dell’ambito della visualizzazione archivio, ad esempio, hanno il seguente formato:

  `CONFIG__STORES__ <STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>`

  Per ulteriori informazioni sugli ambiti, consulta:

   - [Passaggio 1: trovare il valore di ambito della visualizzazione del sito Web o dello store](#step-1-find-the-website-or-store-view-scope-value)
   - [Argomento della Guida utente di Commerce sull&#39;ambito](https://docs.magento.com/user-guide/configuration/scope.html)
   - [Riferimento rapido ambito](https://docs.magento.com/user-guide/stores/store-scope-reference.html)

`<SYSTEM__VARIABLE__NAME>` è il percorso di configurazione con due caratteri di sottolineatura al posto di `/`. Per ulteriori informazioni, vedere [Passaggio 2: impostazione delle variabili di sistema](#step-2-set-global-website-or-store-view-variables).

### Formato variabile

`<SCOPE>` è separato da `<SYSTEM__VARIABLE__NAME>` da due caratteri di sottolineatura.

`<SYSTEM__VARIABLE__NAME>` è derivato dal _percorso di configurazione_ di un&#39;impostazione di configurazione, che è una stringa delimitata da `/` che identifica in modo univoco un&#39;impostazione specifica. Sostituire ogni carattere `/` nel percorso di configurazione con due caratteri di sottolineatura per creare la variabile di sistema.

Se un percorso di configurazione contiene un carattere di sottolineatura, questo rimane nella variabile.

Un elenco completo dei percorsi di configurazione è disponibile in:

- [Riferimenti sui percorsi di configurazione sensibili e specifici del sistema](config-reference-sens.md)
- [Riferimento sui percorsi di configurazione dei pagamenti](config-reference-payment.md)
- [Riferimento ai percorsi di configurazione dell’estensione Commerce Enterprise B2B](config-reference-b2b.md)
- [Altri percorsi di configurazione di riferimento](config-reference-general.md)

## Passaggio 1: trovare il valore di ambito della visualizzazione del sito Web o dello store

In questa sezione viene illustrato come trovare e impostare i valori di configurazione di sistema per _ambito_ (visualizzazione archivio o sito Web). Per impostare le variabili di ambito globali, vedere [Passaggio 2: Impostazione delle variabili di visualizzazione globali, del sito Web o dell&#39;archivio](#step-2-set-global-website-or-store-view-variables).

I valori di ambito provengono dalle tabelle `store`, `store_group` e `store_website`.

- La tabella `store` specifica i nomi e i codici della visualizzazione archivio
- La tabella `store_website` specifica i nomi e i codici del sito Web

Puoi anche trovare i valori del codice utilizzando l’Admin.

Come leggere la tabella:

- Colonna `Path in Admin`

  I valori prima della virgola sono percorsi nella navigazione dell’amministratore. I valori dopo la virgola sono opzioni nel riquadro di destra.

- La colonna `Variable name` è il nome della variabile di ambiente corrispondente.

  È possibile specificare i valori di sistema per questi parametri di configurazione come variabili di ambiente, se lo si desidera.

   - L&#39;intero nome della variabile è sempre TUTTO MAIUSCOLO
   - Inizia un nome variabile con `CONFIG__` (notare due caratteri di sottolineatura)
   - È possibile trovare il nome o `<STORE_VIEW_CODE>` `<WEBSITE_CODE>` parte di un nome di variabile nel database Admin o Commerce, come indicato nelle sezioni seguenti.
   - `<SYSTEM__VARIABLE__NAME>` Come illustrato nel [Passaggio 2: impostare variabili](#step-2-set-global-website-or-store-view-variables) di visualizzazione globale, sito Web o store.

### Trovare un ambito di visualizzazione sito web o store nell’Amministratore

Nella tabella seguente viene riepilogato come trovare il valore della visualizzazione del sito Web o dello store nell&#39;amministratore.

| Descrizione | Percorso in Admin | Variabile nome |
|--------------|--------------|----------------------|
| Crea, modifica, elimina store visualizzazioni | **[!UICONTROL Stores]** > **[!UICONTROL All Stores]** | `CONFIG__STORES__<STORE_VIEW_CODE>__<SYSTEM__VARIABLE__NAME>` |
| Creazione, modifica ed eliminazione di siti Web | **[!UICONTROL Stores]** > **[!UICONTROL All Store]s** | `CONFIG__WEBSITES__<WEBSITE_CODE>__<SYSTEM__VARIABLE__NAME>` |

Ad esempio, per trovare un valore di ambito di visualizzazione sito web o store nell’Admin:

1. Accedi all’amministratore come utente autorizzato a visualizzare i siti web.
1. Fare clic su **[!UICONTROL Stores]** > **[!UICONTROL All Store]s**.
1. Fai clic sul nome di una visualizzazione sito web o store.

   Il riquadro di destra viene visualizzato in modo simile al seguente.

   ![Trovare un codice sito Web](../../assets/configuration/website-code.png)

1. Il nome dell&#39;ambito viene visualizzato nel campo **[!UICONTROL Code]**.
1. Continua con [Passaggio 2: imposta le variabili globali, di visualizzazione sito Web o di visualizzazione archivio](#step-2-set-global-website-or-store-view-variables).

### Trovare un sito Web o visualizzare store ambito nel database

Per ottenere questi valori dal database:

1. Accedi al tuo sistema di sviluppo come file system proprietario se non lo hai già fatto.
1. Immetti il comando seguente:

   ```bash
   mysql -u <database-username> -p
   ```

1. Al prompt `mysql>`, immettere i comandi seguenti nell&#39;ordine indicato:

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

1. Utilizza il valore della `code` colonna come nome del ambito, non come `name` valore.

   Ad esempio, per impostare una variabile di configurazione per il sito Web di prova, utilizzare il formato seguente:

   ```shell
   CONFIG__WEBSITES__TEST1__<SYSTEM__VARIABLE__NAME>
   ```

   dove `<SYSTEM__VARIABLE__NAME>` viene dalla sezione successiva.

## Passaggio 2: Imposta le variabili di visualizzazione globale, sito Web o store

Questa sezione illustra come impostare le variabili di sistema.

- Per impostare i valori per l&#39;ambito globale, ovvero tutti i siti Web, gli archivi e le visualizzazioni degli archivi, iniziare il nome della variabile con `CONFIG__DEFAULT__`.

- Per impostare un valore per una particolare visualizzazione archivio o sito Web, avviare il nome della variabile come descritto in [Passaggio 1: Trovare il valore dell&#39;ambito](#step-1-find-the-website-or-store-view-scope-value):

   - `CONFIG__WEBSITES`
   - `CONFIG__STORES`

- L’ultima parte del nome della variabile è il percorso di configurazione, univoco per ogni impostazione di configurazione.

[Vedi alcuni esempi](#examples).

La tabella seguente mostra alcune variabili di esempio.

| Descrizione | Percorso in Amministrazione (omettendo **Archivi** > **Impostazioni >** **Configurazione**) | Variabile nome |
|--------------|--------------|----------------------|
| Elasticsearch nome host del server | Catalogo > **Catalogo**, **Nome host server Elasticsearch** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME` |
| porta server Elasticsearch | Catalogo > **Catalogo**, **Elasticsearch porta server** | `<SCOPE>__CATALOG__SEARCH__ELASTICSEARCH_SERVER_PORT` |
| Paese di spedizione di provenienza | Vendita > **spedizione Impostazioni** | `<SCOPE>__SHIPPING__ORIGIN__COUNTRY_ID` |
| Custom Admin URL | **Amministratore Avanzate >** | `<SCOPE>__ADMIN__URL__CUSTOM` |
| Percorso amministratore personalizzato | Avanzate > **Amministratore** | `<SCOPE>__ADMIN__URL__CUSTOM_PATH` |

## Esempi

Questa sezione mostra come trovare i valori di alcune variabili di esempio.

### Nome host del server Elasticsearch

Per trovare il nome della variabile per la minimizzazione globale di HTML:

1. Determinare l&#39;ambito.

   È l&#39;ambito globale, quindi il nome della variabile inizia con `CONFIG__DEFAULT__`

1. Il resto del nome della variabile è `CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`.

   **Risultato**: nome variabile: `CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME`

### Origine paese di spedizione

Per trovare il nome della variabile per il paese di spedizione di origine:

1. Determinare il ambito.

   Individuare il ambito nel [database](#find-a-website-or-store-view-scope-in-the-database) come illustrato nel Passaggio 1: trovare il sito Web o visualizzare store ambito valore. (È inoltre possibile trovare il valore nell&#39;amministratore, come mostrato nella [tabella in Passaggio 2: Imposta variabili] di visualizzazione globale, sito Web o store (#step-2-set-global-website-or-store-view-variables.

   Ad esempio, il ambito potrebbe essere `CONFIG__WEBSITES__DEFAULT`.

1. Il resto del nome della variabile è `SHIPPING__ORIGIN__COUNTRY_ID`.

   **Risultato**: nome variabile: `CONFIG__WEBSITES__DEFAULT__SHIPPING__ORIGIN__COUNTRY_ID`

## Come usare le variabili d&#39;ambiente

Imposta i valori di configurazione come variabili utilizzando l&#39;array associato di [`$_ENV`](https://php.net/manual/en/reserved.variables.environment.php) PHP. È possibile impostare i valori in qualsiasi script PHP eseguito durante l&#39;esecuzione di Commerce.

>[!TIP]
>
>L&#39;impostazione dei valori delle variabili in `index.php` o `pub/index.php` non funziona sempre come previsto poiché è possibile utilizzare diversi punti di ingresso applicazione a seconda della configurazione del server Web. Inserendo `$_ENV` le direttive nel `app/bootstrap.php` file, indipendentemente dai diversi punti di ingresso applicazione, le `$_ENV` direttive vengono sempre eseguite poiché il `app/bootstrap.php` file viene caricato come parte dell&#39;architettura Commerce.

Di seguito è riportato un esempio di impostazione di due valori `$_ENV`:

```php
$_ENV['CONFIG__DEFAULT__CATALOG__SEARCH__ELASTICSEARCH_SERVER_HOSTNAME'] = 'http://search.example.com';
$_ENV['CONFIG__DEFAULT__GENERAL__STORE_INFORMATION__MERCHANT_VAT_NUMBER'] = '1234';
```

Un esempio dettagliato viene visualizzato in [Impostare i valori di configurazione utilizzando le variabili di ambiente](../deployment/example-environment-variables.md).

>[!WARNING]
>
>- Per utilizzare i valori impostati nell&#39;array `$_ENV`, è necessario impostare `variables_order = "EGPCS"`(Ambiente, Get, Post, Cookie e Server) nel file `php.ini`. Per informazioni dettagliate, vedere la [documentazione PHP](https://www.php.net/manual/en/ini.core.php).
>
>- Per Adobe Commerce su infrastruttura cloud, se si tenta di ignorare le impostazioni di configurazione utilizzando [Project Web Interface](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html#configure-the-project), è necessario anteporre al nome della variabile `env:`. Ad esempio:
>
>![Esempio di variabile di ambiente](../../assets/configuration/cloud-console-envvariable.png)
