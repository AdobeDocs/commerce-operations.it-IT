---
title: Procedure consigliate per la modifica delle tabelle di database
description: Scopri come e quando modificare le tabelle di database di Adobe Commerce e di terze parti.
role: Developer, Architect
feature: Best Practices
feature-set: Commerce
last-substantial-update: 2022-11-15T00:00:00Z
exl-id: 9e7adaaa-b165-4293-aa98-5dc4b8c23022
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1438'
ht-degree: 0%

---

# Procedure consigliate per la modifica delle tabelle di database

In questo articolo vengono fornite le procedure consigliate per la modifica delle tabelle di database create da [!DNL Adobe Commerce] o moduli di terze parti. Scopri quando e come modificare efficacemente le tabelle per garantire la redditività a lungo termine e la stabilità della piattaforma commerce.

Migrazione da [!DNL Magento 1] e altre piattaforme di e-commerce, o l&#39;utilizzo di moduli del [!DNL Adobe Commerce] Marketplace, può richiedere l’aggiunta e il salvataggio di dati aggiuntivi. Il primo istinto potrebbe essere quello di aggiungere una colonna a una tabella di database o di modificarne una esistente. Tuttavia, è necessario modificare solo un core [!DNL Adobe Commerce] tabella (o tabella dei fornitori di terze parti) in situazioni limitate.

## Perché l’Adobe consiglia di evitare le modifiche

Il motivo principale per evitare di modificare le tabelle principali è che Adobe Commerce include una logica sottostante che contiene query SQL non elaborate. Le modifiche alla struttura della tabella possono causare effetti indesiderati imprevisti difficili da risolvere. La modifica può inoltre influire sulle operazioni DDL (Data Definition Language) causando impatti imprevisti e imprevedibili sulle prestazioni.

Un altro motivo per evitare di modificare la struttura della tabella di database è che le modifiche possono causare problemi se il team di sviluppo di base o sviluppatori di terze parti modificano la struttura delle tabelle di database. Ad esempio, alcune tabelle di database di base hanno una colonna denominata `additional_data`. Questo è sempre stato un `text` tipo di colonna. Tuttavia, per motivi di prestazioni, il team di base potrebbe modificare la colonna in `longtext`. Questo tipo di colonna è un alias per JSON. La conversione in questo tipo di colonna comporta un aumento delle prestazioni e una maggiore ricercabilità, che non esiste come `text` tipo. Per ulteriori informazioni su questo argomento, consulta [Tipo di dati JSON](https://mariadb.com/kb/en/json-data-type/){target="_blank"}.

## Sapere quando salvare o rimuovere i dati

L’Adobe consiglia di determinare innanzitutto se è necessario salvare questi dati. Se trasferisci dati da un sistema legacy, qualsiasi dato rimuovibile ti consente di risparmiare tempo e fatica durante la migrazione. Esistono diversi modi per archiviare i dati, se è necessario accedervi in un secondo momento. Per essere un buon amministratore dell’applicazione e delle prestazioni, è consentito contestare una richiesta di salvataggio di dati aggiuntivi. L’obiettivo è garantire che il salvataggio dei dati sia un requisito per soddisfare un’esigenza aziendale che non può essere soddisfatta in altro modo.

### Dati legacy

Se il progetto contiene dati legacy, ad esempio vecchi ordini o record cliente, è consigliabile utilizzare un metodo di ricerca alternativo. Ad esempio, se l’azienda richiede l’accesso ai dati solo per riferimento occasionale, puoi implementare una ricerca esterna del vecchio database ospitato al di fuori della piattaforma commerce invece di migrare i vecchi dati a [!DNL Adobe Commerce].

Questa situazione richiederebbe la migrazione del database a un server, che offre un’interfaccia web per la lettura dei dati o forse una formazione sull’utilizzo di MySQL Workbench o strumenti simili. L’esclusione di questi dati dal nuovo database accelera la migrazione consentendo al team di sviluppo di concentrarsi sul nuovo sito anziché sulla risoluzione dei problemi di migrazione dei dati.

Un’altra opzione correlata per mantenere i dati esterni al commercio, ma consentendoti di utilizzarli in tempo reale, sarebbe quella di sfruttare altri strumenti, come GraphQL mesh. Questa opzione combina diverse origini di dati e le restituisce come una singola risposta.

Ad esempio, puoi `stitch` insieme vecchi ordini da un database esterno, forse il vecchio Magento 1 sito che è disattivato. Quindi, utilizzando GraphQL mesh, mostrale come parte della cronologia degli ordini dei clienti. Questi vecchi ordini possono essere combinati con gli ordini del tuo attuale [!DNL Adobe Commerce] ambiente.

Per ulteriori informazioni sull’utilizzo di API mesh con GraphQL, consulta [Cos’è API Mesh](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/){target="_blank"}) and [GraphQL Mesh Gateway](https://developer.adobe.com/graphql-mesh-gateway/){target="_blank"}.

## Migrare i dati legacy con gli attributi dell’estensione

Se stabilisci che i dati legacy devono essere migrati o che i nuovi dati devono essere salvati in [!DNL Adobe Commerce], Adobe consiglia di utilizzare [attributi di estensione](https://developer.adobe.com/commerce/php/development/components/add-attributes/){target="_blank"}. L’utilizzo degli attributi di estensione per salvare dati aggiuntivi offre i seguenti vantaggi:

- Puoi controllare i dati persistenti e la struttura del database, in modo da garantire che vengano salvati con il tipo di colonna e gli indici corretti.
- La maggior parte delle entità in [!DNL Adobe Commerce] e [!DNL Magento Open Source] supporta l’utilizzo degli attributi di estensione.
- Gli attributi di estensione sono un meccanismo indipendente dall’archiviazione che offre la flessibilità di salvare i dati nella posizione ottimale per il progetto.

Due esempi di percorsi di archiviazione sono le tabelle di database e [!DNL Redis]. Quando si sceglie una posizione, è importante considerare se la posizione comporta una complessità aggiuntiva o influisce sulle prestazioni.

### Valuta altre alternative

In qualità di sviluppatore, è fondamentale considerare sempre l’utilizzo di strumenti al di fuori del [!DNL Adobe Commerce] ad esempio GraphQL mesh e Adobe App Builder. Questi strumenti possono essere utili per mantenere l’accesso ai dati, ma non hanno alcun impatto sull’applicazione Commerce di base o sulle tabelle di database sottostanti. Con questo approccio, puoi esporre i dati tramite un’API. Quindi, aggiungi un’origine dati alla configurazione di App Builder. Utilizzando GraphQL Mesh, puoi combinare tali origini dati e produrre un’unica risposta come indicato in [dati legacy](#legacy-data).

Per ulteriori dettagli sulla rete GraphQL, vedi [Gateway GraphQL Mesh](https://developer.adobe.com/graphql-mesh-gateway/){target="_blank"}. For information about the Adobe App Builder,  see [Introducing App Builder](https://experienceleague.adobe.com/docs/adobe-developers-live-events/events/2021/oct2021/introduction-app-builder.html?lang=en){target="_blank"}.

## Modifica di una tabella core o di terze parti

Se decidi di memorizzare i dati modificando un core [!DNL Adobe Commerce] Per la tabella del database dei moduli di terze parti, attenersi alle linee guida riportate di seguito per ridurre al minimo l&#39;impatto sulla stabilità e sulle prestazioni.

- Aggiungi solo nuove colonne.
- Non modificare mai _tipo_ valore di una colonna esistente. Ad esempio, non modificare un’ `integer` a un `varchar` al fine di soddisfare il tuo caso d’uso univoco.
- Evitare di aggiungere colonne alle tabelle degli attributi EAV. Queste tabelle sono già sovraccariche di logica e responsabilità.
- Prima di regolare una tabella, determinarne le dimensioni. La modifica di tabelle di grandi dimensioni ha un impatto sulla distribuzione e può causare minuti o ore di ritardo nell’applicazione delle modifiche.

## Procedure consigliate per la modifica di una tabella di database esterna

L&#39;Adobe consiglia di eseguire la procedura seguente quando si aggiunge una colonna a una tabella di database di base o a una tabella di terze parti:

1. Crea un modulo con un nome nello spazio dei nomi che rappresenti ciò che stai aggiornando.

   Ad esempio: `app/code/YourCompany/Customer`

1. Creare i file appropriati per abilitare il modulo (vedere [Creare un modulo](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html){target="_blank"}.

1. Crea un file denominato `db_schema.xml` nel `etc` e apportare le modifiche appropriate.

   Se applicabile, genera un `db_schema_whitelist.json` file. Consulta [Schema dichiarativo](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/){target="_blank"} per ulteriori informazioni.

### Impatti potenziali

L’aggiunta di una colonna a un database esterno può avere un impatto sul progetto Adobe Commerce nei seguenti modi:

- Gli aggiornamenti potrebbero essere più complicati.
- Le distribuzioni sono interessate se la tabella in fase di modifica è di grandi dimensioni.
- Le migrazioni a una nuova piattaforma potrebbero essere più complicate.

## Modi per evitare di modificare le tabelle principali

È possibile evitare di modificare le tabelle del database di Adobe Commerce utilizzando [attributi di estensione](#migrate-legacy-data-with-extension-attributes). Un&#39;altra alternativa consiste nell&#39;utilizzare una colonna speciale (`additional_data`) trovato in alcune tabelle principali per memorizzare i dati e salvarli in formato codificato JSON.

### Salvare i dati in una colonna di dati con codifica JSON

Alcune tabelle core presentano `additional_data` che contiene dati con codifica JSON. Questa colonna offre un modo nativo di mappare dati aggiuntivi in un campo. L’utilizzo di questo metodo evita l’aggiunta di una tabella per elementi di dati semplici e di piccole dimensioni in cui sono memorizzate informazioni per il recupero dei dati senza dover essere cercati. Il `additional_data` La colonna è in genere disponibile solo a livello di articolo, non per l&#39;intero preventivo o ordine.

- Vantaggi dell&#39;utilizzo di `additional_data` campo

   - Non sono necessari campi aggiuntivi, il che mantiene minimo il numero di colonne. Questa funzione è utile nel flusso di vendita, in cui sono già presenti molte tabelle. È meglio non complicare ulteriormente questo processo già complesso. Questo metodo soddisfa molti casi d&#39;uso, ma non tutti.

- Svantaggi

   - Questo metodo è ideale solo per l&#39;archiviazione di dati di sola lettura. Questo problema si verifica perché il nostro codice dovrebbe essere non serializzato per modificare e generare l’oggetto per aggiungere dipendenze o relazioni di database.

   - È difficile utilizzare le operazioni del database per cercare questi campi. La ricerca con questo metodo è lenta.

   - Prestare particolare attenzione quando si memorizzano i dati nella `additional_data` colonna per evitare l’attivazione di operazioni di serializzazione o annullamento della serializzazione che potrebbero interrompere il codice creando JSON non valido o causando errori di lettura durante il runtime.

   - Questi campi devono essere dichiarati chiaramente nel codice, in modo che uno sviluppatore possa trovarli facilmente.

   - Altri problemi che possono verificarsi e che possono essere molto difficili da diagnosticare. Ad esempio, con alcune funzioni PHP native se non si utilizza [!DNL Adobe Commerce] metodi di wrapper forniti dall&#39;applicazione di base il risultato finale dei dati trasformati può essere diverso dal formato previsto. Utilizza sempre le funzioni di wrapper per garantire coerenza e prevedibilità dei dati salvati o recuperati.

Di seguito sono riportati alcuni esempi di tabelle con colonna e struttura per `additional_data` colonna.

```mysql
MariaDB [main]> DESCRIBE quote_item additional_data;
+-----------------+------+------+-----+---------+-------+
| Field           | Type | Null | Key | Default | Extra |
+-----------------+------+------+-----+---------+-------+
| additional_data | text | YES  |     | NULL    |       |
+-----------------+------+------+-----+---------+-------+
1 row in set (0.001 sec)


MariaDB [main]> DESCRIBE sales_order_item additional_data;
+-----------------+------+------+-----+---------+-------+
| Field           | Type | Null | Key | Default | Extra |
+-----------------+------+------+-----+---------+-------+
| additional_data | text | YES  |     | NULL    |       |
+-----------------+------+------+-----+---------+-------+
1 row in set (0.001 sec)
```

Nelle versioni 2.4.3, 2.4.4 e 2.4.5 sono presenti dieci tabelle con la colonna `additional_data`.

```mysql
MariaDB [magento]> SELECT DISTINCT TABLE_NAME FROM INFORMATION_SCHEMA.COLUMNS WHERE COLUMN_NAME IN ('additional_data') AND TABLE_SCHEMA='main';
+------------------------+
| TABLE_NAME             |
+------------------------+
| sales_shipment_item    |
| sales_creditmemo_item  |
| sales_invoice_item     |
| catalog_eav_attribute  |
| sales_order_payment    |
| quote_address_item     |
| quote_payment          |
| quote_item             |
| magento_reward_history |
| sales_order_item       |
+------------------------+
10 rows in set (0.020 sec)
```
