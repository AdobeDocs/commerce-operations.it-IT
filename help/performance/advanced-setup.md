---
title: Configurazione Avanzate
description: Esaminare le best practice e le raccomandazioni per i sistemi aziendali di grandi dimensioni progettati per elaborare grandi volumi di dati.
exl-id: eb9ca9fa-b099-4e77-ab33-16cd0f382ffe
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '1173'
ht-degree: 0%

---

# Avanzate configurazione

[!DNL Commerce] è un prodotto altamente flessibile e scalabile che contiene soluzioni per commercianti di tutte le dimensioni. In questa sezione vengono illustrate le best practice e le raccomandazioni per la configurazione di [!DNL Commerce] per l&#39;utilizzo con grandi quantità di dati, carichi estremi e altri casi aziendali.

## Calibra prestazioni indice

Quando si gestiscono grandi quantità di dati, la reindicizzazione può diventare un problema. Il team [!DNL Commerce] ha selezionato gli indici più caricati e ha abilitato l&#39;indicizzazione batch, che consente di impostare una parte di dati da elaborare su ogni iterazione. In questo modo, l’utente può regolare le dimensioni del batch in base al tipo e alle dimensioni dei dati nel database.

Per gestire questa impostazione, modificare il parametro `batchRowsCount` nel file `di.xml` del modulo corrispondente. I seguenti indici supportano questa funzione:

* Indice dei prodotti per categorie (modulo catalogo)
* Indice di prezzo (modulo catalogo)
* Indice EAV (Modulo catalogo)
* Indice scorte (modulo CatalogInventory)

È possibile regolare le prestazioni dell&#39;indicizzatore regolando le variabili di dimensione batch dell&#39;indice. Controlla quante entità vengono elaborate contemporaneamente dall&#39;indicizzatore. In alcune situazioni, abbiamo assistito a riduzioni significative del tempo di indicizzazione.

Se ad esempio si esegue un profilo simile a B2B Medium, è possibile sostituire il valore di configurazione `batchRowsCount` in `app/code/Magento/catalog/etc/di.xml` e sostituire il valore predefinito `5000` con `1000`. Questo riduce il tempo di indicizzazione completo da 4 ore a 2 ore con una configurazione predefinita di [!DNL MySQL].

>[!NOTE]
>
>Non è stata abilitata la gestione in batch per l&#39;indicizzatore delle regole di catalogo. I commercianti con un numero elevato di regole di catalogo devono modificare la configurazione [!DNL MySQL] per ottimizzare il tempo di indicizzazione. In questo caso, la modifica del file di configurazione [!DNL MySQL] e l&#39;allocazione di più memoria ai valori di configurazione TMP_TABLE_SIZE e MAX_HEAP_TABLE_SIZE (il valore predefinito è 16M per entrambi) miglioreranno le prestazioni di questo indicizzatore, ma [!DNL MySQL] utilizzerà più RAM.

### Limitare i gruppi di clienti e i cataloghi condivisi per siti Web

Un numero elevato di SKU di prodotto, siti web, gruppi di clienti o cataloghi condivisi influirà sul tempo di esecuzione degli indicizzatori Prezzo prodotto e Regola catalogo. Questo perché, per impostazione predefinita, tutti i siti web vengono assegnati a tutti i gruppi di clienti (cataloghi condivisi).

Per ridurre il tempo di indicizzazione, è possibile [escludere determinati siti web dai gruppi di clienti (cataloghi condivisi).](https://developer.adobe.com/commerce/php/development/components/indexing/optimization/#customer-group-limitations-by-websites)

## Configurare Redis

A volte un istanza Redis non è sufficiente per soddisfare le richieste in arrivo. Ci sono diverse soluzioni che possiamo consigliare per affrontare questa situazione.

In primo luogo, [!DNL Commerce] consente di configurare l&#39;archiviazione cache separata per ogni tipo di cache. Questo consente di installare tante istanze Redis separate quanti sono i tipi di cache registrati nel Magento. Realisticamente, potresti desiderare istanze Redis per le cache più attivamente utilizzate, come configurazione, layout e blocchi.

Un&#39;altra soluzione consiste nel posizionare la cache di configurazione sul file system e spostare le altre cache sul server Redis. Con questa soluzione, è necessario uno strumento separato per l’invalidazione centralizzata della cache di configurazione su tutti i nodi web.

È inoltre possibile utilizzare un cluster Redis che esegue operazioni parallele di lettura/scrittura con un numero di nodi in aumento automatico. [!DNL Commerce] non fornisce la configurazione per questo caso, ma può essere avviato con personalizzazioni minori.

## Configura [!DNL RabbitMQ]

Adobe Commerce supporta le code di messaggi implementate tramite [!DNL RabbitMQ]. [!DNL Commerce] utilizza questo servizio per eseguire numerose operazioni asincrone, incluse le operazioni del catalogo B2B e gli aggiornamenti asincroni delle scorte. Tutte le interfacce per l’aggiunta di più processi al server dei processi sono distribuite con il prodotto e sono disponibili per l’implementazione asincrona personalizzata della logica nell’ambito di estensioni di terze parti. Come qualsiasi altra integrazione, [!DNL Commerce] fornisce un file di configurazione di esempio per [!DNL RabbitMQ] che contiene tutte le impostazioni consigliate ed è completamente pronto per l&#39;utilizzo in produzione.

## Dividere il database

>[!WARNING]
>
>La funzionalità del database diviso era [obsoleta](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) nella versione 2.4.2 di Adobe Commerce. Vedere [Ripristino da un database diviso a un singolo database](../configuration/storage/revert-split-database.md).

Adobe Systems Commerce consente di configurare l&#39;archiviazione di database scalabile per soddisfare le esigenze di un&#39;azienda in crescita. È possibile configurare tre database master distinti che servono domini specifici:

* Database principale (catalogo)
* Database di estrazione
* Database di Order Management System (OMS)

Per configurare database aggiuntivi, è necessario creare un database vuoto ed eseguire uno dei comandi seguenti:

Per database master di estrazione

```bash
bin/magento setup:db-schema:split-quote
```

Per OMS Master DB

```bash
bin/magento setup:db-schema:split-sales
```

Questi comandi consentono di eseguire la migrazione di tabelle di dominio specifiche dal database principale a un database di dominio. Modificano anche la configurazione per consentire la [!DNL Commerce] connettività corrispondente e l&#39;elaborazione dei vincoli.

Disponendo di database separati per il checkout e la gestione degli ordini, è possibile distribuire il carico tra i server di database. Puoi effettuare più casse ed elaborare più ordini al secondo senza influire sulla disponibilità del catalogo e su altre operazioni. È consigliabile suddividere i database per periodi di vendite flash o attive o utilizzarli in modo permanente per progetti naturalmente ad alto carico. La migrazione dei dati presenti tra database deve essere eseguita sotto la supervisione dell&#39;amministratore di sistema.  Non dividere i database in modalità di produzione.

Oltre ai database master, [!DNL Commerce] consente di configurare diversi database slave (uno per ogni risorsa dati dichiarata nel sistema). Un database slave funge da replica completa del database principale o di uno dei database master del dominio. Viene emesso per le operazioni di lettura su una risorsa specifica.

È possibile aggiungere un database slave eseguendo il comando seguente:

```bash
bin/magento setup:db-schema:add-slave
```

Questo comando esegue le modifiche di configurazione ma non configura la replica stessa. Questo dovrebbe essere fatto manualmente.

Dopo aver suddiviso il database master e impostato i database slave, [!DNL Commerce] regola automaticamente le connessioni a un database specifico, prendendo decisioni in base al tipo di richiesta (POST, PUT, GET, ecc.) e alla risorsa dati. Se [!DNL Commerce] o le sue estensioni eseguono operazioni di scrittura su un richiesta GET, il sistema commuta automaticamente la connessione dal database slave a quello master. Funziona allo stesso modo con i database master: non appena si utilizza una tabella relativa all&#39;estrazione, il sistema reindirizza tutte le query a un database specifico. Nel frattempo, tutte le query relative al catalogo verranno inviate al database principale.

Per ulteriori dettagli sulla configurazione e sui vantaggi di una configurazione con più elementi principali e slave, vedere
[Soluzione per le prestazioni del database diviso](../configuration/storage/multi-master.md).

## Distribuire contenuti multimediali

Il Magento non fornisce alcuna integrazione specifica per la distribuzione e la distribuzione dei contenuti multimediali. Tutti gli approcci comuni possono essere utilizzati insieme nel Magento.

Il modo più semplice per distribuire i contenuti multimediali consiste nel distribuirli e memorizzarli nella cache su un server [!DNL Varnish]. Questo approccio presuppone un file system condiviso per l&#39;archiviazione dei contenuti multimediali o un server dedicato che punta a [!DNL Varnish].

Per gli ambienti con carichi medi e elevati, consigliamo di utilizzare i servizi CDN (Content Delivery Network) like Fastly, Akamai e altri. Quando si utilizzano questi servizi, [!DNL Commerce] utilizza l&#39;approccio richiamare classico per gli aggiornamenti contenuto. È necessario configurare [!DNL Commerce] gli URL affinché funzionino con il servizio CDN corrispondente. Spostando media contenuto su una rete CDN, ridurrai significativamente il carico sulle tue istanze.

## Configurare l&#39;archiviazione dei log

L&#39;archiviazione dei registri e la loro influenza su altre operazioni su disco influiscono sulla disponibilità dei nodi web, soprattutto in situazioni di carico elevato. È consigliabile ridurre a icona la registrazione se non è necessaria. È inoltre possibile configurare la registrazione in modo che esegua la scrittura su un sistema di storage separato con velocità di accesso elevate. Eventuali colli di bottiglia nell’accesso all’archiviazione dei registri possono influire direttamente sull’elaborazione delle richieste in entrata che registrano le operazioni di scrittura o lettura come parte del loro flusso.
