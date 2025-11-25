---
title: Procedure consigliate per la modifica delle tabelle di database
description: Scopri come e quando modificare le tabelle di database di Adobe Commerce e di terze parti.
role: Developer, Architect
feature: Best Practices
last-substantial-update: 2022-11-15T00:00:00Z
exl-id: 9e7adaaa-b165-4293-aa98-5dc4b8c23022
source-git-commit: d40de2f05147e6c58c15cd3cd59275cc91283162
workflow-type: tm+mt
source-wordcount: '1420'
ht-degree: 0%

---

# Procedure consigliate per la modifica delle tabelle di database

In questo articolo vengono fornite le procedure consigliate per la modifica delle tabelle di database create da [!DNL Adobe Commerce] o da moduli di terze parti. Scopri quando e come modificare efficacemente le tabelle per garantire la redditività a lungo termine e la stabilità della piattaforma commerce.

La migrazione da [!DNL Magento 1] e altre piattaforme di e-commerce o l&#39;utilizzo dei moduli del Marketplace [!DNL Adobe Commerce] può richiedere l&#39;aggiunta e il salvataggio di dati aggiuntivi. Il primo istinto potrebbe essere quello di aggiungere una colonna a una tabella di database o di modificarne una esistente. Tuttavia, è consigliabile modificare una tabella [!DNL Adobe Commerce] di base (o una tabella fornitore di terze parti) solo in situazioni limitate.

## Perché Adobe consiglia di evitare le modifiche

Il motivo principale per evitare di modificare le tabelle principali è che Adobe Commerce include una logica sottostante che contiene query SQL non elaborate. Le modifiche alla struttura della tabella possono causare effetti indesiderati imprevisti difficili da risolvere. La modifica può inoltre influire sulle operazioni DDL (Data Definition Language) causando impatti imprevisti e imprevedibili sulle prestazioni.

Un altro motivo per evitare di modificare la struttura della tabella di database è che le modifiche possono causare problemi se il team di sviluppo di base o sviluppatori di terze parti modificano la struttura delle tabelle di database. Alcune tabelle di database di base, ad esempio, contengono una colonna denominata `additional_data`. È sempre stato un tipo di colonna `text`. Tuttavia, per motivi di prestazioni, il team di base potrebbe cambiare la colonna in `longtext`. Questo tipo di colonna è un alias per JSON. La conversione in questo tipo di colonna comporta un aumento delle prestazioni e una maggiore ricercabilità, che non esiste come tipo `text`. Per ulteriori informazioni su questo argomento, consulta il [tipo di dati JSON](https://mariadb.com/kb/en/json-data-type/){target="_blank"}.

## Sapere quando salvare o rimuovere i dati

Adobe consiglia di determinare innanzitutto se è necessario salvare questi dati. Se trasferisci dati da un sistema legacy, qualsiasi dato rimuovibile ti consente di risparmiare tempo e fatica durante la migrazione. Esistono diversi modi per archiviare i dati, se è necessario accedervi in un secondo momento. Per essere un buon amministratore dell’applicazione e delle prestazioni, è consentito contestare una richiesta di salvataggio di dati aggiuntivi. L’obiettivo è garantire che il salvataggio dei dati sia un requisito per soddisfare un’esigenza aziendale che non può essere soddisfatta in altro modo.

### Dati legacy

Se il progetto contiene dati legacy, ad esempio vecchi ordini o record cliente, è consigliabile utilizzare un metodo di ricerca alternativo. Ad esempio, se l&#39;azienda richiede l&#39;accesso ai dati solo per un riferimento occasionale, è consigliabile implementare una ricerca esterna del vecchio database ospitato al di fuori della piattaforma commerce anziché eseguire la migrazione dei vecchi dati a [!DNL Adobe Commerce].

Questa situazione richiederebbe la migrazione del database a un server, che offre un’interfaccia web per la lettura dei dati o forse una formazione sull’utilizzo di MySQL Workbench o strumenti simili. L’esclusione di questi dati dal nuovo database accelera la migrazione consentendo al team di sviluppo di concentrarsi sul nuovo sito anziché sulla risoluzione dei problemi di migrazione dei dati.

Un’altra opzione correlata per mantenere i dati esterni al commercio, ma consentendoti di utilizzarli in tempo reale, sarebbe quella di sfruttare altri strumenti, come GraphQL mesh. Questa opzione combina diverse origini di dati e le restituisce come una singola risposta.

È ad esempio possibile `stitch` raggruppare i vecchi ordini provenienti da un database esterno, ad esempio il vecchio sito Magento 1 disattivato. Quindi, utilizzando GraphQL mesh, mostrale come parte della cronologia degli ordini dei clienti. Questi vecchi ordini possono essere combinati con quelli dell&#39;ambiente [!DNL Adobe Commerce] corrente.

Per ulteriori informazioni sull&#39;utilizzo di API mesh con GraphQL, vedere [Informazioni su API Mesh](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/){target="_blank"}) e [GraphQL Mesh Gateway](https://developer.adobe.com/graphql-mesh-gateway/){target="_blank"}.

## Migrare i dati legacy con gli attributi dell’estensione

Se si stabilisce che i dati legacy devono essere migrati o che i nuovi dati devono essere salvati in [!DNL Adobe Commerce], Adobe consiglia di utilizzare [attributi di estensione](https://developer.adobe.com/commerce/php/development/components/add-attributes/){target="_blank"}. L’utilizzo degli attributi di estensione per salvare dati aggiuntivi offre i seguenti vantaggi:

- Puoi controllare i dati persistenti e la struttura del database, in modo da garantire che vengano salvati con il tipo di colonna e gli indici corretti.
- La maggior parte delle entità in [!DNL Adobe Commerce] supporta l&#39;utilizzo degli attributi di estensione.
- Gli attributi di estensione sono un meccanismo indipendente dall’archiviazione che offre la flessibilità di salvare i dati nella posizione ottimale per il progetto.

Due esempi di percorsi di archiviazione sono le tabelle di database e [!DNL Redis]. Quando si sceglie una posizione, è importante considerare se la posizione comporta una complessità aggiuntiva o influisce sulle prestazioni.

### Valuta altre alternative

In qualità di sviluppatore, è fondamentale prendere sempre in considerazione l&#39;utilizzo di strumenti al di fuori dell&#39;ambiente [!DNL Adobe Commerce], ad esempio GraphQL mesh e Adobe App Builder. Questi strumenti possono essere utili per mantenere l’accesso ai dati, ma non hanno alcun impatto sull’applicazione Commerce di base o sulle tabelle di database sottostanti. Con questo approccio, puoi esporre i dati tramite un’API. Quindi, aggiungi un’origine dati alla configurazione di App Builder. Utilizzando GraphQL Mesh, puoi combinare tali origini dati e produrre un&#39;unica risposta come indicato in [dati legacy](#legacy-data).

Per ulteriori dettagli sulla rete GraphQL, vedere [Gateway GraphQL Mesh](https://developer.adobe.com/graphql-mesh-gateway/){target="_blank"}. Per informazioni sull&#39;App Builder di Adobe, vedere [Introduzione ad App Builder](https://experienceleague.adobe.com/docs/adobe-developers-live-events/events/2021/oct2021/introduction-app-builder.html){target="_blank"}.

## Modifica di una tabella core o di terze parti

Se si decide di archiviare i dati modificando una tabella di database di moduli di base [!DNL Adobe Commerce] o di terze parti, utilizzare le linee guida seguenti per ridurre al minimo l&#39;impatto sulla stabilità e sulle prestazioni.

- Aggiungi solo nuove colonne.
- Non modificare mai il valore _type_ di una colonna esistente. Ad esempio, non modificare `integer` in `varchar` per soddisfare il tuo caso d&#39;uso univoco.
- Evitare di aggiungere colonne alle tabelle degli attributi EAV. Queste tabelle sono già sovraccariche di logica e responsabilità.
- Prima di regolare una tabella, determinarne le dimensioni. La modifica di tabelle di grandi dimensioni ha un impatto sulla distribuzione e può causare minuti o ore di ritardo nell’applicazione delle modifiche.

## Procedure consigliate per la modifica di una tabella di database esterna

Adobe consiglia di seguire questi passaggi quando si aggiunge una colonna a una tabella di database di base o a una tabella di terze parti:

1. Crea un modulo con un nome nello spazio dei nomi che rappresenti ciò che stai aggiornando.

   Esempio: `app/code/YourCompany/Customer`

1. Creare i file appropriati per abilitare il modulo (vedere [Creare un modulo](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html){target="_blank"}.

1. Creare un file denominato `db_schema.xml` nella cartella `etc` e apportare le modifiche appropriate.

   Se applicabile, generare un file `db_schema_whitelist.json`. Per ulteriori informazioni, vedere [Schema dichiarativo](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/){target="_blank"}.

### Impatti potenziali

L’aggiunta di una colonna a un database esterno può avere un impatto sul progetto Adobe Commerce nei seguenti modi:

- Gli aggiornamenti potrebbero essere più complicati.
- Le distribuzioni sono interessate se la tabella in fase di modifica è di grandi dimensioni.
- Le migrazioni a una nuova piattaforma potrebbero essere più complicate.

## Modi per evitare di modificare le tabelle principali

È possibile evitare di modificare le tabelle del database di Adobe Commerce utilizzando [attributi di estensione](#migrate-legacy-data-with-extension-attributes). Un&#39;altra alternativa consiste nell&#39;utilizzare una colonna speciale (`additional_data`) trovata in alcune tabelle principali per memorizzare i dati e salvarli in formato JSON.

### Salvare i dati in una colonna di dati con codifica JSON

Alcune tabelle core hanno una colonna `additional_data` che contiene dati con codifica JSON. Questa colonna offre un modo nativo di mappare dati aggiuntivi in un campo. L’utilizzo di questo metodo evita l’aggiunta di una tabella per elementi di dati semplici e di piccole dimensioni in cui sono memorizzate informazioni per il recupero dei dati senza dover essere cercati. La colonna `additional_data` è in genere disponibile solo a livello di elemento e non per l&#39;intero preventivo o ordine.

- Vantaggi dell&#39;utilizzo del campo `additional_data`

   - Non sono necessari campi aggiuntivi, il che mantiene minimo il numero di colonne. Questa funzione è utile nel flusso di vendita, in cui sono già presenti molte tabelle. È meglio non complicare ulteriormente questo processo già complesso. Questo metodo soddisfa molti casi d&#39;uso, ma non tutti.

- Svantaggi

   - Questo metodo è ideale solo per l&#39;archiviazione di dati di sola lettura. Questo problema si verifica perché il nostro codice dovrebbe essere non serializzato per modificare e generare l’oggetto per aggiungere dipendenze o relazioni di database.

   - È difficile utilizzare le operazioni del database per cercare questi campi. La ricerca con questo metodo è lenta.

   - È necessario prestare particolare attenzione durante l&#39;archiviazione dei dati nella colonna `additional_data` per evitare l&#39;attivazione di operazioni di serializzazione o annullamento della serializzazione che potrebbero interrompere il codice creando JSON non valido o causando errori di lettura durante il runtime.

   - Questi campi devono essere dichiarati chiaramente nel codice, in modo che uno sviluppatore possa trovarli facilmente.

   - Altri problemi che possono verificarsi e che possono essere molto difficili da diagnosticare. Ad esempio, con alcune funzioni PHP native se non si utilizzano i metodi wrapper [!DNL Adobe Commerce] forniti dall&#39;applicazione principale, il risultato finale dei dati trasformati può essere diverso dal formato previsto. Utilizza sempre le funzioni di wrapper per garantire coerenza e prevedibilità dei dati salvati o recuperati.

Di seguito sono riportati alcuni esempi di tabelle con colonna e struttura per la colonna `additional_data`.

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

Nelle versioni 2.4.3, 2.4.4 e 2.4.5 sono presenti dieci tabelle con colonna `additional_data`.

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
