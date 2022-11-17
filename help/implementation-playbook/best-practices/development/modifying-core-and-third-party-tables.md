---
title: Procedure consigliate per la modifica delle tabelle di database
description: Scopri come e quando modificare le tabelle di database di Adobe Commerce e di terze parti.
role: Developer, Architect
feature: Best Practices
feature-set: Commerce
last-substantial-update: 2022-11-15T00:00:00Z
source-git-commit: 570fa4877f578f636736f0404169ed215fd06b24
workflow-type: tm+mt
source-wordcount: '1469'
ht-degree: 0%

---

# Procedure consigliate per la modifica delle tabelle di database

Questo articolo fornisce le best practice per modificare le tabelle di database create da [!DNL Adobe Commerce] o moduli di terze parti. La comprensione di quando e come modificare in modo efficace le tabelle consente di garantire la vitalità e la stabilità a lungo termine della piattaforma di e-commerce.

Migrazione da [!DNL Magento 1] e altre piattaforme di e-commerce, o lavorare con moduli dal [!DNL Adobe Commerce] Marketplace, può richiedere l’aggiunta e il salvataggio di dati aggiuntivi. Il primo istinto potrebbe essere quello di aggiungere una colonna a una tabella di database o di modificarne una esistente. Tuttavia, devi solo modificare un nucleo [!DNL Adobe Commerce] tabella (o tabella fornitore di terze parti) in situazioni limitate.

## Perché Adobe consiglia di evitare modifiche

Il motivo principale per evitare di modificare le tabelle di base è che Adobe Commerce include la logica sottostante che contiene query SQL non elaborate. Le modifiche alla struttura della tabella possono causare effetti collaterali imprevisti che sono difficili da risolvere. La modifica può anche influire sulle operazioni DDL (Data Definition Language), causando impatti imprevisti e imprevedibili sulle prestazioni.

Un altro motivo per evitare di modificare la struttura della tabella del database è che le modifiche possono causare problemi se il team di sviluppo principale o gli sviluppatori di terze parti modificano la struttura delle rispettive tabelle del database. Ad esempio, esistono alcune tabelle di database di base con una colonna denominata `additional_data`. Questo è sempre stato un `text` tipo di colonna. Tuttavia, per motivi di prestazioni, il team principale potrebbe modificare la colonna in `longtext`. Questo tipo di colonna è un alias per JSON. La conversione in questo tipo di colonna comporta miglioramenti delle prestazioni e della ricercabilità aggiunte a tale colonna, che non esiste come `text` digitare. Per ulteriori informazioni su questo argomento, consulta [Tipo di dati JSON](https://mariadb.com/kb/en/json-data-type/){target=&quot;_blank&quot;}.

## Sapere quando salvare o rimuovere i dati

Adobe consiglia innanzitutto di determinare se è necessario salvare i dati. Se stai spostando dati da un sistema legacy, qualsiasi dato che puoi rimuovere ti consente di risparmiare tempo e fatica durante la migrazione. (Esistono modi per archiviare i dati se è necessario accedervi in un secondo momento). Per essere un buon amministratore dell&#39;applicazione e delle prestazioni, è bene sfidare una richiesta per risparmiare dati aggiuntivi. Il tuo obiettivo è quello di garantire che il salvataggio dei dati sia un requisito per soddisfare una necessità aziendale che non può essere riempita in altro modo.

### Dati legacy

Se il progetto contiene dati legacy, ad esempio ordini precedenti o record cliente, considera un metodo di ricerca alternativo. Ad esempio, se l’azienda richiede l’accesso ai dati solo per riferimento occasionale, è consigliabile implementare una ricerca esterna del vecchio database ospitato al di fuori della piattaforma di e-commerce invece di eseguire la migrazione dei vecchi dati a [!DNL Adobe Commerce].

Questa situazione richiederebbe la migrazione del database a un server, che offra un&#39;interfaccia Web per leggere i dati, o magari una formazione sull&#39;uso di MySQL Workbench o strumenti simili. L’esclusione di questi dati dal nuovo database velocizza la migrazione consentendo al team di sviluppo di concentrarsi sul nuovo sito invece di risolvere i problemi di migrazione dei dati.

Un&#39;altra opzione correlata per mantenere i dati esterni al commercio ma consentendoti di utilizzarli in tempo reale sarebbe quella di sfruttare altri strumenti, come la mesh GraphQL. Questa opzione combina diverse origini dati e le restituisce come una singola risposta.

Ad esempio, puoi `stitch` insieme vecchi ordini provenienti da un database esterno, forse il vecchio sito del Magento 1 che viene ritirato. Quindi utilizzando la mesh GraphQL, mostrali come parte della cronologia degli ordini dei clienti. Questi vecchi ordini possono essere combinati con gli ordini del tuo attuale [!DNL Adobe Commerce] ambiente.

Per ulteriori informazioni sull&#39;utilizzo della mesh API con GraphQL, vedi [Cosa è la mesh API](https://developer.adobe.com/graphql-mesh-gateway/gateway/overview/){target=&quot;_blank&quot;}) e [Gateway mesh GraphQL](https://developer.adobe.com/graphql-mesh-gateway/){target=&quot;_blank&quot;}.

## Migrazione di dati legacy con attributi di estensione

Se determini che i dati legacy richiedono la migrazione o che i nuovi dati devono essere salvati in [!DNL Adobe Commerce], Adobe consiglia di utilizzare [attributi di estensione](https://developer.adobe.com/commerce/php/development/components/add-attributes/){target=&quot;_blank&quot;}. L’utilizzo degli attributi di estensione per salvare dati aggiuntivi offre i seguenti vantaggi:

- È possibile controllare i dati persistenti e la struttura del database, in modo che i dati vengano salvati con il tipo di colonna corretto e con gli indici appropriati.
- La maggior parte delle entità in [!DNL Adobe Commerce] e [!DNL Magento Open Source] supporta l’utilizzo di attributi di estensione.
- Gli attributi di estensione sono un meccanismo agnostico dell’archiviazione che offre la flessibilità di salvare i dati nella posizione ottimale per il progetto.

Due esempi di posizioni di archiviazione sono tabelle di database e [!DNL Redis]. Le cose chiave da considerare quando si sceglie una posizione sono se la posizione introduce una complessità aggiuntiva o influisce sulle prestazioni.

### Considerare altre alternative

In qualità di sviluppatore, è fondamentale considerare sempre l’utilizzo di strumenti al di fuori del tuo [!DNL Adobe Commerce] ambiente, come la mesh GraphQL e Adobe App Builder. Questi strumenti possono essere utili per mantenere l’accesso ai dati ma non hanno alcun impatto sull’applicazione commerce di base o sulle relative tabelle di database sottostanti. Con questo approccio, esponi i dati tramite un’API. Quindi, aggiungi un’origine dati alla configurazione di App Builder. Utilizzando GraphQL Mesh, puoi combinare queste origini dati e produrre una singola risposta come indicato in [dati legacy](#legacy-data).

Per ulteriori dettagli sulla mesh GraphQL, vedi [Gateway mesh GraphQL](https://developer.adobe.com/graphql-mesh-gateway/){target=&quot;_blank&quot;}. Per informazioni sull&#39;Adobe di App Builder, vedi [Introduzione a App Builder](https://experienceleague.adobe.com/docs/adobe-developers-live-events/events/2021/oct2021/introduction-app-builder.html?lang=en){target=&quot;_blank&quot;}.

## Modifica di una tabella di base o di una tabella di terze parti

Se decidi di archiviare i dati modificando un core [!DNL Adobe Commerce] per la tabella del database dei moduli di terze parti, utilizzare le seguenti linee guida per ridurre al minimo l’impatto sulla stabilità e sulle prestazioni.

- Aggiungi solo nuove colonne.
- Non modificare mai la _type_ di una colonna esistente. Ad esempio, non modificare un `integer` a `varchar` per soddisfare il tuo caso d&#39;uso unico.
- Evita di aggiungere colonne alle tabelle degli attributi EAV. Queste tabelle sono già sovraccariche di logica e responsabilità.
- Prima di regolare una tabella, determinarne le dimensioni. La modifica di tabelle di grandi dimensioni influisce sulla distribuzione, che può causare minuti o ore di ritardo quando vengono applicate modifiche.

## Procedure consigliate per la modifica di una tabella di database esterna

Adobe consiglia di seguire questi passaggi quando si aggiunge una colonna a una tabella di database di base o a una tabella di terze parti:

1. Crea un modulo con un nome nello spazio dei nomi che rappresenti l’aggiornamento in corso.

   Ad esempio: `app/code/YourCompany/Customer`

1. Crea i file appropriati per abilitare il modulo (vedi [Creare un modulo](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/backend-development/create-module.html){target=&quot;_blank&quot;}.

1. Crea un file denominato `db_schema.xml` in `etc` e apporta le modifiche appropriate.

   Se applicabile, genera un `db_schema_whitelist.json` file. Vedi [Schema dichiarativo](https://developer.adobe.com/commerce/php/development/components/declarative-schema/configuration/){target=&quot;_blank&quot;} per ulteriori informazioni.

### Effetti potenziali

L’aggiunta di una colonna a un database esterno può avere un impatto sul progetto Adobe Commerce nei seguenti modi:

- Gli aggiornamenti potrebbero essere più complicati.
- Le implementazioni sono interessate se la tabella che si sta modificando è di grandi dimensioni.
- Le migrazioni verso una nuova piattaforma potrebbero essere più complicate.

## Modi per evitare di modificare le tabelle principali

È possibile evitare di modificare le tabelle del database Adobe Commerce utilizzando [attributi di estensione](#migrate-legacy-data-with-extension-attributes). Un’altra alternativa è quella di utilizzare una colonna speciale (`additional_data`) trovata in alcune tabelle principali per memorizzare i dati e salvarli in formato codificato JSON.

### Salvare i dati in una colonna di dati con codifica JSON

Alcune tabelle principali hanno un `additional_data` che contiene dati codificati JSON. Questa colonna offre un modo nativo di mappare dati aggiuntivi in un campo. Questo metodo evita di aggiungere una tabella per elementi di dati semplici e di piccole dimensioni che memorizzano informazioni per il recupero dei dati senza un requisito di ricerca. La `additional_data` in genere è disponibile solo a livello di articolo, non per l&#39;intero preventivo o ordine.

- Vantaggi dell&#39;utilizzo del `additional_data` field

   - Non sono necessari campi aggiuntivi, il che riduce al minimo il numero di colonne. Questo è utile nel flusso di vendita, in cui sono già presenti molte tabelle. È meglio non aggiungere più complessità a questo processo già complicato. Questo metodo soddisfa molti casi di utilizzo, ma non tutti.

- Svantaggi

   - Questo metodo è ideale solo per la memorizzazione di dati di sola lettura. Questo problema si verifica perché il nostro codice dovrebbe essere non serializzato per modificare e creare l&#39;oggetto per aggiungere dipendenze o relazioni di database.

   - È difficile utilizzare le operazioni del database per cercare questi campi. La ricerca con questo metodo è lenta.

   - Occorre prestare particolare attenzione quando si memorizzano i dati nella `additional_data` per evitare di attivare operazioni di serializzazione o di annullamento della serializzazione che potrebbero interrompere il codice creando JSON non valido o causando errori di lettura durante il runtime.

   - Questi campi devono essere dichiarati chiaramente nel codice, in modo che uno sviluppatore possa trovarli facilmente.

   - Altri problemi che possono verificarsi che possono essere molto difficili da diagnosticare. Ad esempio, con alcune funzioni PHP native se non si utilizza [!DNL Adobe Commerce] metodi wrapper forniti dall&#39;applicazione principale il risultato finale dei dati trasformati può essere diverso dal formato previsto. Utilizza sempre le funzioni wrapper per garantire la coerenza e la prevedibilità dei dati salvati o recuperati.

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

Nelle versioni 2.4.3, 2.4.4 e 2.4.5 ci sono dieci tabelle con la colonna `additional_data`.

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
