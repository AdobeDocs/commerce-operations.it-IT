---
title: Configurazione avanzata
description: Esamina le best practice e i consigli per i sistemi aziendali di grandi dimensioni progettati per elaborare grandi volumi di dati.
exl-id: eb9ca9fa-b099-4e77-ab33-16cd0f382ffe
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '1173'
ht-degree: 0%

---

# Configurazione avanzata

[!DNL Commerce] è un prodotto altamente flessibile e scalabile che contiene soluzioni per commercianti di tutte le dimensioni. Questa sezione descrive le best practice e i consigli per la configurazione di [!DNL Commerce] utilizzare grandi quantità di dati, carichi estremi e altri casi aziendali.

## Calibra prestazioni indice

Quando si gestiscono grandi quantità di dati, la reindicizzazione può diventare un problema. Il [!DNL Commerce] il team ha selezionato gli indici più caricati e ha abilitato l’indicizzazione batch, che consente di impostare una parte di dati da elaborare su ogni iterazione. In questo modo, l’utente può regolare le dimensioni del batch in base al tipo e alle dimensioni dei dati nel database.

Per gestire questa impostazione, modifica il `batchRowsCount` parametro in `di.xml` del modulo corrispondente. I seguenti indici supportano questa funzione:

* Indice dei prodotti per categorie (modulo catalogo)
* Indice di prezzo (modulo catalogo)
* Indice EAV (Modulo catalogo)
* Indice scorte (modulo CatalogInventory)

È possibile regolare le prestazioni dell&#39;indicizzatore regolando le variabili di dimensione batch dell&#39;indice. Questo controlla quante entità vengono elaborate contemporaneamente dall’indicizzatore. In alcune situazioni, abbiamo visto riduzioni significative del tempo di indicizzazione.

Ad esempio, se esegui un profilo simile al medio B2B, puoi sovrascrivere il valore di configurazione `batchRowsCount` in `app/code/Magento/catalog/etc/di.xml` e sovrascrivi il valore predefinito di `5000` a `1000`. Questo riduce il tempo di indicizzazione completo da 4 ore a 2 ore con un valore predefinito [!DNL MySQL] configurazione.

>[!NOTE]
>
>Non è stata abilitata la gestione in batch per l&#39;indicizzatore delle regole di catalogo. I commercianti con un numero elevato di regole di catalogo devono adeguare il proprio [!DNL MySQL] per ottimizzare il tempo di indicizzazione. In questo caso, modifica [!DNL MySQL] file di configurazione e l&#39;allocazione di più memoria ai valori di configurazione TMP_TABLE_SIZE e MAX_HEAP_TABLE_SIZE (il valore predefinito è 16M per entrambi) migliorerà le prestazioni di questo indicizzatore, ma si otterrà [!DNL MySQL] utilizzo di più RAM.

### Limitare i gruppi di clienti e i cataloghi condivisi per siti Web

Un numero elevato di SKU di prodotto, siti web, gruppi di clienti o cataloghi condivisi influirà sul tempo di esecuzione degli indicizzatori Prezzo prodotto e Regola catalogo. Questo perché, per impostazione predefinita, tutti i siti web vengono assegnati a tutti i gruppi di clienti (cataloghi condivisi).

Per ridurre il tempo di indicizzazione, puoi [escludere alcuni siti Web dai gruppi di clienti (cataloghi condivisi)](https://developer.adobe.com/commerce/php/development/components/indexing/optimization/#customer-group-limitations-by-websites).

## Configurazione Redis

A volte un’istanza Redis non è sufficiente per soddisfare le richieste in ingresso. Per risolvere questa situazione possiamo consigliare diverse soluzioni.

In primo luogo, [!DNL Commerce] consente di configurare una memoria cache separata per ogni tipo di cache. Questo consente di installare tante istanze Redis separate quanti sono i tipi di cache registrati nel Magento. Realisticamente, potresti desiderare istanze Redis per le cache più attivamente utilizzate, come configurazione, layout e blocchi.

Un&#39;altra soluzione consiste nel posizionare la cache di configurazione sul file system e spostare le altre cache sul server Redis. Con questa soluzione, è necessario uno strumento separato per l’invalidazione centralizzata della cache di configurazione su tutti i nodi web.

È inoltre possibile utilizzare un cluster Redis che esegue operazioni parallele di lettura/scrittura con un numero di nodi in aumento automatico. [!DNL Commerce] non fornisce la configurazione per questo caso, ma può essere avviato con personalizzazioni minori.

## Configurazione [!DNL RabbitMQ]

Adobe Commerce supporta le code di messaggi implementate tramite [!DNL RabbitMQ]. [!DNL Commerce] utilizza questo servizio per eseguire numerose operazioni asincrone, incluse le operazioni del catalogo B2B e gli aggiornamenti asincroni delle scorte. Tutte le interfacce per l’aggiunta di più processi al server dei processi sono distribuite con il prodotto e sono disponibili per l’implementazione asincrona personalizzata della logica nell’ambito di estensioni di terze parti. Come con qualsiasi altra integrazione, [!DNL Commerce] fornisce un esempio di file di configurazione per [!DNL RabbitMQ] che contiene tutte le impostazioni consigliate ed è completamente pronto per l’utilizzo in produzione.

## Dividere il database

>[!WARNING]
>
>La funzionalità di suddivisione del database era [obsoleto](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187) nella versione 2.4.2 di Adobe Commerce. Consulta [Ripristino da un database diviso a un singolo database](../configuration/storage/revert-split-database.md).

Adobe Commerce consente di configurare lo storage scalabile del database per soddisfare le esigenze di un&#39;azienda in crescita. È possibile impostare tre database master distinti che servono domini specifici:

* Database principale (catalogo)
* Database di estrazione
* Database di Order Management System (OMS)

Per configurare database aggiuntivi, è necessario creare un database vuoto ed eseguire uno dei comandi seguenti:

Per database master di estrazione

```bash
bin/magento setup:db-schema:split-quote
```

Per database master OMS

```bash
bin/magento setup:db-schema:split-sales
```

Con questi comandi vengono migrate tabelle di dominio specifiche dal database principale a un database di dominio. Cambiano anche la [!DNL Commerce] per consentire la connettività e l’elaborazione dei vincoli corrispondenti.

Disponendo di database separati per l&#39;estrazione e Order Management, è possibile distribuire il carico tra i server di database. Puoi distribuire più checkout ed elaborare più ordini al secondo senza influire sulla disponibilità del catalogo e di altre operazioni. Si consiglia di suddividere i database per periodi di vendite flash o attive o di utilizzarli in modo permanente per progetti con carichi naturalmente elevati. La migrazione dei dati attuali tra database deve essere eseguita sotto la supervisione dell&#39;amministratore di sistema.  Non dividere i database in modalità di produzione.

Oltre ai database master, [!DNL Commerce] consente di configurare diversi database slave (uno per ogni risorsa dati dichiarata nel sistema). Un database slave funge da replica completa del database principale o di uno dei database master del dominio. Viene emesso per le operazioni di lettura su una risorsa specifica.

È possibile aggiungere un database slave eseguendo il comando seguente:

```bash
bin/magento setup:db-schema:add-slave
```

Questo comando esegue le modifiche di configurazione ma non configura la replica stessa. Questo dovrebbe essere fatto manualmente.

Dopo aver diviso il database master e aver impostato i database slave, [!DNL Commerce] regola automaticamente le connessioni a un database specifico, prendendo decisioni in base al tipo di richiesta (POST, PUT, GET, ecc.) e alla risorsa dati. Se [!DNL Commerce] o le relative estensioni eseguono operazioni di scrittura su una richiesta di GET, il sistema passa automaticamente la connessione da slave a database master. Funziona allo stesso modo con i database master: non appena si utilizza una tabella relativa all&#39;estrazione, il sistema reindirizza tutte le query a un database specifico. Nel frattempo, tutte le query relative al catalogo verranno inviate al database principale.

Per ulteriori dettagli sulla configurazione e sui vantaggi di una configurazione con più elementi principali e slave, vedere
[Soluzione per la suddivisione delle prestazioni del database](../configuration/storage/multi-master.md).

## Distribuire contenuti multimediali

Il Magento non fornisce alcuna integrazione specifica per la distribuzione e la distribuzione dei contenuti multimediali. Tutti gli approcci comuni possono essere utilizzati insieme nel Magento.

Il modo più semplice per distribuire i contenuti multimediali è distribuirli e memorizzarli nella cache [!DNL Varnish] server. Questo approccio presuppone un file system condiviso per l&#39;archiviazione dei contenuti multimediali o un server dedicato che punti a [!DNL Varnish].

Per ambienti con carichi medi e alti, consigliamo di utilizzare servizi CDN (Content Delivery Network) come Fastly, Akamai e altri. Quando si lavora con questi servizi, [!DNL Commerce] utilizza il classico approccio pull per gli aggiornamenti dei contenuti. Devi configurare [!DNL Commerce] URL da utilizzare con il servizio CDN corrispondente. Spostando i contenuti multimediali su una rete CDN, diminuirai in modo significativo il carico sulle istanze.

## Configurare l’archiviazione del registro

L&#39;archiviazione dei registri e la loro influenza su altre operazioni su disco influiscono sulla disponibilità dei nodi web, soprattutto in situazioni di carico elevato. È consigliabile ridurre a icona la registrazione se non è necessaria. È inoltre possibile configurare la registrazione in modo che esegua la scrittura su un sistema di storage separato con velocità di accesso elevate. Eventuali colli di bottiglia nell’accesso all’archiviazione dei registri possono influire direttamente sull’elaborazione delle richieste in entrata che registrano le operazioni di scrittura o lettura come parte del loro flusso.
