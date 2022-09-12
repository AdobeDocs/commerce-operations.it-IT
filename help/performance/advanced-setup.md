---
title: Configurazione avanzata
description: Esamina le best practice e le raccomandazioni per i sistemi aziendali di grandi dimensioni progettati per elaborare grandi volumi di dati.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '1192'
ht-degree: 0%

---


# Configurazione avanzata

[!DNL Commerce] è un prodotto altamente flessibile e scalabile che contiene soluzioni per commercianti di tutte le dimensioni. Questa sezione descrive le best practice e i consigli per la configurazione [!DNL Commerce] per lavorare con grandi quantità di dati, carico estremo e altri casi aziendali.

## Calibrare le prestazioni dell&#39;indice

Quando si tratta di grandi quantità di dati, la reindicizzazione può diventare un problema. La [!DNL Commerce] il team ha selezionato gli indici più caricati e ha abilitato l’indicizzazione in batch, che consente di impostare una parte dei dati da elaborare su ogni iterazione. In questo modo, l&#39;utente può ottimizzare le dimensioni batch in base al tipo e alla dimensione dei dati nel database.

Per gestire questa impostazione, modifica la `batchRowsCount` nel `di.xml` file del modulo corrispondente. I seguenti indici supportano questa funzione:

* Indice dei prodotti della categoria (modulo catalogo)
* Indice dei prezzi (modulo catalogo)
* Indice EAV (modulo catalogo)
* Indice delle scorte (modulo CatalogoInventario)

È possibile ottimizzare le prestazioni dell&#39;indicizzatore regolando le variabili delle dimensioni della batch dell&#39;indice. Questo controlla quante entità vengono elaborate alla volta dall&#39;indicizzatore. In alcune situazioni, abbiamo visto una significativa diminuzione del tempo di indicizzazione.

Ad esempio, se esegui un profilo simile a B2B Medium, puoi sovrascrivere il valore di configurazione `batchRowsCount` in `app/code/Magento/catalog/etc/di.xml` e sovrascrivi il valore predefinito di `5000` a `1000`. Questo riduce il tempo di indicizzazione completo da 4 ore a 2 ore con un valore predefinito [!DNL MySQL] configurazione.

>[!NOTE]
>
>Non sono stati abilitati i batch per l&#39;indicizzatore delle regole del catalogo. I commercianti con un numero elevato di regole di catalogo devono regolare i loro [!DNL MySQL] per ottimizzare il tempo di indicizzazione. In questo caso, modifica il [!DNL MySQL] il file di configurazione e l&#39;allocazione di più memoria ai valori di configurazione TMP_TABLE_SIZE e MAX_HEAP_TABLE_SIZE (l&#39;impostazione predefinita è 16M per entrambi) miglioreranno le prestazioni per questo indicizzatore, ma si tradurrà in [!DNL MySQL] consumo di più RAM.

### Limitare i gruppi di clienti e i cataloghi condivisi per siti web

Un numero elevato di SKU di prodotto, siti web, gruppi di clienti o cataloghi condivisi influisce sul tempo di esecuzione degli indici del prezzo del prodotto e delle regole del catalogo. Questo perché, per impostazione predefinita, tutti i siti web vengono assegnati a tutti i gruppi di clienti (cataloghi condivisi).

Per ridurre il tempo di indicizzazione, puoi [escludere alcuni siti web dai gruppi di clienti (cataloghi condivisi)](https://developer.adobe.com/commerce/php/development/components/indexing/optimization/#customer-group-limitations-by-websites).

## Imposta Redis

A volte un’istanza Redis non è sufficiente per soddisfare le richieste in arrivo. Ci sono diverse soluzioni che possiamo consigliare di affrontare questa situazione.

Primo, [!DNL Commerce] consente di configurare una memorizzazione cache separata per ogni tipo di cache. Questo ti consente di installare altrettante istanze Redis separate del numero di tipi di cache registrati nel Magento. In modo realistico, è possibile che si desideri utilizzare le istanze Redis per le cache utilizzate più attivamente, ad esempio configurazione, layout e blocchi.

Un&#39;altra soluzione può essere quella di posizionare la cache di configurazione sul file system e spostare le altre cache sul server Redis. Con questa soluzione, è necessario uno strumento separato per l’annullamento centralizzato della validità della cache di configurazione su tutti i nodi web.

È inoltre possibile utilizzare un cluster Redis che esegue operazioni parallele di lettura/scrittura con un numero crescente automatico di nodi. [!DNL Commerce] non fornisce la configurazione per questo caso, ma può essere avviata con personalizzazioni minori.

## Configurazione [!DNL RabbitMQ]

Magento Open Source e Adobe [!DNL Commerce] code di messaggi di supporto implementate tramite [!DNL RabbitMQ]. [!DNL Commerce] utilizza questo servizio per l’esecuzione di numerose operazioni asincrone, comprese le operazioni di catalogo B2B e gli aggiornamenti di stock asincroni. Tutte le interfacce per l’aggiunta di più processi al server dei processi sono distribuite con il prodotto e sono disponibili per l’implementazione logica asincrona personalizzata nell’ambito di estensioni di terze parti. Come per qualsiasi altra integrazione, [!DNL Commerce] fornisce un esempio di file di configurazione per [!DNL RabbitMQ] che contiene tutte le impostazioni consigliate ed è completamente pronto per l’utilizzo in produzione.

## Dividere il database

>[!WARNING]
>
>La funzionalità del database diviso era [obsoleto](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) nella versione 2.4.2 di Adobe Commerce. Vedi [Ripristino da un database diviso a un singolo database](../configuration/storage/revert-split-database.md).

Adobe Commerce consente di configurare lo storage di database scalabile per soddisfare le esigenze di un&#39;azienda in crescita. Puoi impostare tre database master separati che distribuiscono domini specifici:

* Database principale (catalogo)
* Database di estrazione
* Database del sistema di gestione degli ordini (OMS)

Per configurare database aggiuntivi, è necessario creare un database vuoto ed eseguire uno dei seguenti comandi:

Per il database principale di pagamento

```bash
bin/magento setup:db-schema:split-quote
```

Per il database master OMS

```bash
bin/magento setup:db-schema:split-sales
```

Questi comandi migrano tabelle di dominio specifiche dal database principale a un database di dominio. Cambiano anche le [!DNL Commerce] per consentire l’elaborazione dei vincoli e della connettività corrispondenti.

Disponendo di database separati per il pagamento e la gestione degli ordini, è possibile distribuire il carico tra i server di database. Puoi eseguire più pagamenti ed elaborare più ordini al secondo senza influire sulla disponibilità del catalogo e di altre operazioni. Consigliamo di suddividere i database per i periodi di vendite flash o attive, o di utilizzarli in modo permanente per progetti ad alto carico naturale. La migrazione dei dati presenti tra i database deve essere eseguita sotto la supervisione dell&#39;amministratore di sistema.  Non dividere i database in modalità Produzione.

Oltre ai database master, [!DNL Commerce] consente di configurare un numero di database slave (uno per ogni risorsa dati dichiarata nel sistema). Un database slave funge da replica completa del database principale o di uno dei database master di dominio. Viene rilasciato per le operazioni di lettura su una risorsa specifica.

È possibile aggiungere un database slave eseguendo il seguente comando:

```bash
bin/magento setup:db-schema:add-slave
```

Questo comando esegue le modifiche di configurazione ma non configura la replica stessa. Questo dovrebbe essere fatto manualmente.

Dopo aver suddiviso il database principale e aver impostato i database slave, [!DNL Commerce] regola automaticamente le connessioni a un database specifico, prendendo decisioni in base al tipo di richiesta (POST, PUT, GET, ecc.) e alla risorsa dati. Se [!DNL Commerce] Per le sue estensioni esegue operazioni di scrittura su una richiesta GET, il sistema passa automaticamente la connessione dal database slave al database master. Funziona allo stesso modo con i database master: non appena si lavora con una tabella relativa al checkout, tutte le query vengono reindirizzate a un database specifico. Nel frattempo, tutte le query relative al catalogo andranno al database principale.

Per ulteriori dettagli sulla configurazione e sui vantaggi di più configurazioni master/slave, vedi
[Soluzione per le prestazioni del database diviso](../configuration/storage/multi-master.md).

## Distribuire contenuti multimediali

Il Magento non fornisce alcuna integrazione specifica per distribuire e distribuire contenuti multimediali. Tutti gli approcci comuni possono essere utilizzati insieme nel Magento.

Il modo più semplice per trasmettere i contenuti multimediali è distribuirli e memorizzarli nella cache su un [!DNL Varnish] server. Questo approccio presuppone un file system condiviso per la memorizzazione dei contenuti multimediali o un server dedicato che punta a [!DNL Varnish].

Per ambienti a carico medio e elevato, si consiglia di utilizzare i servizi CDN (Content Delivery Network) come Flast, Akamai e altri. Quando si lavora con questi servizi, [!DNL Commerce] utilizza l’approccio di pull classico per gli aggiornamenti dei contenuti. Devi configurare [!DNL Commerce] URL da utilizzare con il servizio CDN corrispondente. Spostando i contenuti multimediali su una rete CDN, si riduce notevolmente il carico sulle istanze.

## Configurare l’archiviazione dei registri

L&#39;archiviazione dei log e la loro influenza su altre operazioni su disco influiscono sulla disponibilità dei nodi web, soprattutto in situazioni di carico elevato. Se non ti serve, consigliamo di ridurre al minimo la registrazione. È inoltre possibile configurare la registrazione in modo che esegua la scrittura su un sistema di storage separato con elevate velocità di accesso. Tieni presente che qualsiasi collo di bottiglia sull’accesso all’archiviazione dei log può influenzare direttamente l’elaborazione delle richieste in arrivo che registrano le operazioni di scrittura o lettura come parte del loro flusso.
