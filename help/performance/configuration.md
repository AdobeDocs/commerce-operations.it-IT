---
title: Best practice per la configurazione
description: Ottimizza i tempi di risposta dell’implementazione di Adobe Commerce utilizzando queste best practice.
feature: Best Practices, Configuration
exl-id: 4cb0f5e7-49d5-4343-a8c7-b8e351170f91
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '1417'
ht-degree: 0%

---

# Best practice di configurazione

Commerce fornisce molte impostazioni e strumenti che puoi utilizzare per migliorare il tempo di risposta sulle pagine e fornire una velocità effettiva più elevata.

## Processi Cron

Tutte le operazioni asincrone in [!DNL Commerce] vengono eseguite utilizzando il comando Linux `cron`. Vedi [Configura ed esegui cron](../configuration/cli/configure-cron-jobs.md) per configurarlo correttamente.

## Indicizzatori

Un indicizzatore può essere eseguito in modalità **[!UICONTROL Update on Save]** o **[!UICONTROL Update on Schedule]**. La modalità **[!UICONTROL Update on Save]** indicizza immediatamente ogni volta che il catalogo o altri dati cambiano. Questa modalità presuppone un&#39;intensità ridotta di operazioni di aggiornamento e navigazione nel negozio. Può causare notevoli ritardi e la mancata disponibilità dei dati in caso di carichi elevati. È consigliabile utilizzare **Aggiorna in base alla pianificazione** per le prestazioni, in quanto memorizza informazioni sugli aggiornamenti dei dati ed esegue l&#39;indicizzazione per porzioni in background tramite un processo cron specifico. È possibile modificare la modalità di ogni indicizzatore [!DNL Commerce] separatamente nella pagina di configurazione **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Index Management]**. L&#39;indice [!UICONTROL Customer Grid] deve essere sempre impostato sulla modalità **[!UICONTROL Update on Save]**.

>[!TIP]
>
>La reindicizzazione su MariaDB 10.4 e 10.6 richiede più tempo rispetto ad altre versioni di MariaDB o [!DNL MySQL]. Si consiglia di modificare l&#39;impostazione di configurazione predefinita di MariaDB, descritta nei [prerequisiti per l&#39;installazione](../installation/prerequisites/database/mysql.md).

## Cache

Quando avvii lo store in produzione, attiva tutte le cache dalla pagina **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Cache Management]**. Si consiglia vivamente di utilizzare [!DNL Varnish], in quanto è una soluzione efficiente per la cache delle pagine di produzione.

## Notifiche e-mail asincrone

L’abilitazione dell’impostazione &quot;Notifiche e-mail asincrone&quot; sposta in background i processi che gestiscono le notifiche e-mail di pagamento e di elaborazione dell’ordine. Per abilitare questa funzione, vai a **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Sales] > [!UICONTROL Sales Emails] > [!UICONTROL General Settings] >[!UICONTROL Asynchronous Sending]**. Per ulteriori informazioni, vedere [E-mail vendite](https://experienceleague.adobe.com/en/docs/commerce-admin/config/sales/sales-emails) nella _Guida utente amministratore_.

## Elaborazione dati ordine asincrono

In alcuni casi le vendite intensive in una vetrina si verificano contemporaneamente all&#39;elaborazione intensiva degli ordini da parte di [!DNL Commerce]. È possibile configurare [!DNL Commerce] per distinguere questi due pattern di traffico a livello di database per evitare conflitti tra le operazioni di lettura e scrittura nelle tabelle corrispondenti. Puoi archiviare e indicizzare i dati dell’ordine in modo asincrono. Gli ordini vengono inseriti in un archivio temporaneo e spostati in blocco nella griglia di Order Management senza alcuna collisione. È possibile attivare questa opzione da **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Developer] > [!UICONTROL Grid Settings] >[!UICONTROL Asynchronous indexing]**. Per ulteriori informazioni, vedere [Aggiornamenti pianificati alla griglia](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/order-management/orders/order-scheduled-operations#enable-scheduled-grid-updates-and-reindexing) nella _Guida utente amministratore_.

>[!WARNING]
>
>La scheda e le opzioni **[!UICONTROL Developer]** sono disponibili solo in [modalità sviluppatore](../configuration/cli/set-mode.md). [Adobe Commerce sull&#39;infrastruttura cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/overview#cloud-req-test) non supporta la modalità `Developer`.

## Salvataggio configurazione asincrona

Per i progetti con un numero elevato di configurazioni a livello di archivio, il salvataggio di una configurazione di archivio può richiedere un tempo eccessivo o causare un timeout. Il modulo _Configurazione asincrona_ consente il salvataggio asincrono della configurazione eseguendo un processo cron che utilizza un consumer per elaborare il salvataggio in una coda di messaggi. AsyncConfig è **disabilitato** per impostazione predefinita.

Puoi abilitare AsyncConfig utilizzando l’interfaccia della riga di comando:

```bash
bin/magento setup:config:set --config-async 1
```

Il comando `set` scrive quanto segue nel file `app/etc/env.php`:

```conf
...
   'config' => [
       'async' => 1
   ]
```

Avvia il seguente consumer per iniziare a elaborare i messaggi nella coda in base al principio &quot;primo in primo out&quot;:

```bash
bin/magento queue:consumers:start saveConfigProcessor --max-messages=1
```

## Aggiornamento scorte differite

In periodi di vendite intensive, [!DNL Commerce] può rimandare gli aggiornamenti delle scorte relativi agli ordini. In questo modo si riduce al minimo il numero di operazioni e si accelera il processo di posizionamento dell&#39;ordine. Tuttavia, questa opzione è rischiosa e può essere utilizzata solo quando gli ordini inevasi vengono attivati nel punto vendita, perché può portare a quantità di scorte negative. Questa opzione consente di migliorare notevolmente le prestazioni dei flussi di cassa per i negozi che possono facilmente ricaricare le scorte su richiesta. Per attivare gli aggiornamenti delle azioni differite sul sito, vai a **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Catalog] > [!UICONTROL Inventory] > [!UICONTROL Product Stock Options] >[!UICONTROL Use Deferred Stock Update]**. Per ulteriori informazioni, vedere [Gestione dell&#39;inventario](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-cloud) nella _Guida utente di Adobe Commerce_.

>[!INFO]
>
>Questa opzione è disponibile solo se **[!UICONTROL Backorder with any mode]** è attivato.

>[!INFO]
>
>Questa opzione funziona anche con [Inserimento ordine asincrono](high-throughput-order-processing.md#asynchronous-order-placement) in combinazione con [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/guide-overview.html).

## Impostazioni di ottimizzazione lato client

Per migliorare la reattività della vetrina dell&#39;istanza [!DNL Commerce], passare all&#39;amministratore in modalità predefinita o sviluppatore e modificare le impostazioni seguenti:

**[!UICONTROL Stores]-> [!UICONTROL Configuration] -> [!UICONTROL Advanced] -> [!UICONTROL Developer]:**

| Gruppo impostazioni | Impostazione | Valore |
| ------------------- | -------------------------- | ------ |
| Impostazioni griglia | Indicizzazione asincrona | Abilita |
| Impostazioni CSS | Minimizza file CSS | Sì |
| Impostazioni [!DNL JavaScript] | Minimizza [!DNL JavaScript] file | Sì |
| Impostazioni [!DNL JavaScript] | Abilita bundle [!DNL JavaScript] | Sì |
| Impostazioni modello | Minify HTML | Sì |

>[!INFO]
>
>La scheda e le opzioni **[!UICONTROL Developer]** sono disponibili solo in [modalità sviluppatore](../configuration/cli/set-mode.md). [Adobe [!DNL Commerce] sull&#39;infrastruttura cloud](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/overview#cloud-req-test) non supporta la modalità `Developer`.

Quando attivi l&#39;opzione **[!UICONTROL Enable [!DNL JavaScript] Bundling]**, consenti a Commerce di unire tutte le risorse JS in uno o più bundle caricati nelle pagine della vetrina. Il bundling di JS comporta un numero inferiore di richieste al server, migliorando le prestazioni della pagina. Aiuta anche il browser a memorizzare in cache le risorse JS alla prima chiamata e a riutilizzarle per tutte le ulteriori ricerche. Questa opzione consente anche la valutazione lenta, in quanto tutto JS viene caricato come testo. Avvia l&#39;analisi e la valutazione del codice solo dopo che sono state attivate azioni specifiche sulla pagina. Tuttavia, questa impostazione non è consigliata per i negozi in cui il tempo di caricamento della prima pagina è estremamente critico, perché tutto il contenuto JS verrà caricato alla prima chiamata.

>[!INFO]
>
>Per ulteriori informazioni sull&#39;ottimizzazione di CSS e JavaScript, vedere [Ottimizzazione di file CSS e JavaScript in Adobe Commerce sull&#39;infrastruttura cloud e Adobe Commerce](https://support.magento.com/hc/en-us/articles/360044482152) nel Centro assistenza Adobe Commerce_.

### Suggerimenti per il bundling

* È consigliabile utilizzare strumenti di terze parti per la minimizzazione e il bundling (come [r.js](https://requirejs.org/)). [!DNL Commerce] meccanismi incorporati non sono ottimali e vengono forniti come alternative di fallback.
* L’attivazione del protocollo HTTP/2 può essere una buona alternativa all’utilizzo del bundling JS. Il protocollo offre molti degli stessi vantaggi. È abilitato per impostazione predefinita in Adobe Commerce sui progetti di infrastruttura cloud.
* È consigliabile non utilizzare impostazioni obsolete, come l’unione di file JS e CSS, in quanto sono state progettate solo per il file JS caricato in modo sincrono nella sezione HEAD della pagina. L’utilizzo di questa tecnica può causare il malfunzionamento del bundling e della logica requireJS.

## Convalida dei segmenti cliente

I commercianti che hanno un numero elevato di [segmenti di clienti](https://experienceleague.adobe.com/en/docs/commerce-admin/customers/segments/customer-segments) possono riscontrare un significativo deterioramento delle prestazioni con le azioni dei clienti, ad esempio l&#39;accesso dei clienti e l&#39;aggiunta di prodotti al carrello.

Le azioni dei clienti attivano un processo di convalida per i segmenti dei clienti, che è ciò che può causare il deterioramento delle prestazioni. Per impostazione predefinita, Adobe Commerce convalida ogni segmento in tempo reale per definire quali segmenti dei clienti corrispondono e quali no.

Per evitare un peggioramento delle prestazioni, è possibile impostare l&#39;opzione di configurazione del sistema **[!UICONTROL Real-time Check if Customer is Matched by Segment]** su **No** per convalidare i segmenti dei clienti tramite una singola query SQL con condizione combinata.

Per abilitare questa ottimizzazione, vai a **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Customers] > [!UICONTROL Customer Configuration] > [!UICONTROL Customer Segments] >[!UICONTROL Real-time Check if Customer is Matched by Segment]**.

Questa impostazione migliora le prestazioni della convalida del segmento del cliente se nel sistema sono presenti molti segmenti di clienti. Tuttavia, non funziona con [implementazioni di database suddiviso](../configuration/storage/multi-master.md) o quando non vi sono clienti registrati.

## Pianificazione della manutenzione del database {#database}

È consigliabile eseguire backup periodici del database per le istanze di staging e produzione. A causa dell&#39;intensa attività di I/O delle operazioni di backup, è possibile che si verifichino backup più lenti e potenziali problemi. L&#39;esecuzione simultanea di processi di database per più ambienti potrebbe risultare più lenta a causa di conflitti per le risorse disponibili.

Per migliorare le prestazioni, pianificare l&#39;esecuzione dei backup in successione, uno alla volta, nei momenti di minore utilizzo. Questo metodo evita i conflitti di I/O e riduce i tempi di completamento, in particolare per le istanze più piccole, i database più grandi e così via.

Ad esempio, consigliamo di pianificare un backup del database di produzione seguito dal database di staging quando gli store riscontrano visite minori.

## Limita il numero di prodotti nella griglia

Per migliorare le prestazioni della griglia prodotti per i cataloghi di grandi dimensioni, si consiglia di limitare il numero di prodotti nella griglia con l&#39;impostazione di configurazione di sistema **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Admin] > [!UICONTROL Admin Grids] >[!UICONTROL Limit Number of Products in Grid]**.

Questa impostazione di configurazione del sistema è disabilitata per impostazione predefinita. Attivandola, puoi limitare il numero di prodotti nella griglia a un valore specifico. **[!UICONTROL Records Limit]** è un&#39;impostazione personalizzabile con un valore minimo predefinito di `20000`.
Quando l&#39;impostazione **[!UICONTROL Limit Number of Products in Grid]** è abilitata e il numero di prodotti nella griglia è maggiore del limite di record, viene restituita la raccolta limitata di record. Al raggiungimento del limite, i record totali trovati, il numero di record selezionati e gli elementi di impaginazione sono nascosti dall&#39;intestazione della griglia.

Quando il numero totale di prodotti nella griglia è limitato, non influisce sulle azioni di massa della griglia del prodotto. Influisce solo sul livello di presentazione della griglia del prodotto. Ad esempio, nella griglia è presente un numero limitato di prodotti `20000`, l&#39;utente fa clic su **[!UICONTROL Select All]**, seleziona l&#39;azione di massa **[!UICONTROL Update attributes]** e aggiorna alcuni attributi. Di conseguenza, vengono aggiornati tutti i prodotti, non la raccolta limitata di `20000` record.

La limitazione relativa alla griglia di prodotti influisce solo sulle raccolte di prodotti utilizzate dai componenti dell’interfaccia utente. Di conseguenza, questa limitazione non riguarda tutte le griglie di prodotti. Solo quelli che utilizzano `Magento\Catalog\Ui\DataProvider\Product\ProductCollection`.
Puoi limitare le raccolte della griglia di prodotti solo sulle pagine seguenti:

* Griglia prodotti catalogo
* Aggiungi griglia prodotti correlati/up-selling/cross-selling
* Aggiungi prodotti al bundle prodotto
* Aggiungi prodotti al prodotto gruppo
* Pagina Crea ordine amministratore

Se non desideri che la griglia prodotti sia limitata, ti consigliamo di utilizzare i filtri in modo più preciso affinché la raccolta dei risultati contenga meno elementi di **[!UICONTROL Records Limit]**.
