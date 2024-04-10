---
title: Best practice per la configurazione
description: Ottimizza i tempi di risposta dell’implementazione di Adobe Commerce o di Magento Open Source utilizzando queste best practice.
feature: Best Practices, Configuration
exl-id: 4cb0f5e7-49d5-4343-a8c7-b8e351170f91
source-git-commit: 602a1ef82fcb8d30ff027db0fe0aacb981c7e08e
workflow-type: tm+mt
source-wordcount: '1425'
ht-degree: 0%

---

# Best practice di configurazione

Commerce offre molte impostazioni e strumenti che puoi utilizzare per migliorare i tempi di risposta sulle pagine e fornire una velocità effettiva più elevata.

## Processi Cron

Tutte le operazioni asincrone in [!DNL Commerce] vengono eseguiti utilizzando Linux `cron` comando. Consulta [Configurare ed eseguire cron](../configuration/cli/configure-cron-jobs.md) per configurarlo correttamente.

## Indicizzatori

Un indicizzatore può essere eseguito in **[!UICONTROL Update on Save]** o **[!UICONTROL Update on Schedule]** modalità. Il **[!UICONTROL Update on Save]** La modalità indicizza immediatamente ogni volta che il catalogo o altri dati cambiano. Questa modalità presuppone un&#39;intensità ridotta di operazioni di aggiornamento e navigazione nel negozio. Può causare notevoli ritardi e la mancata disponibilità dei dati in caso di carichi elevati. È consigliabile utilizzare **Aggiorna secondo programma** ai fini delle prestazioni, perché memorizza informazioni sugli aggiornamenti dei dati ed esegue l’indicizzazione per porzioni in background tramite un processo cron specifico. È possibile modificare la modalità di ogni [!DNL Commerce] indicizzatore separatamente sulla  **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Index Management]** pagina di configurazione. Il [!UICONTROL Customer Grid] l&#39;indice deve essere sempre impostato su **[!UICONTROL Update on Save]** modalità.

>[!TIP]
>
>La reindicizzazione su MariaDB 10.4 e 10.6 richiede più tempo rispetto ad altri MariaDB o [!DNL MySQL] versioni. Si consiglia di modificare l’impostazione di configurazione predefinita di MariaDB, descritta nella [prerequisiti per l&#39;installazione](../installation/prerequisites/database/mysql.md).

## Cache

Quando avvii lo store in produzione, attiva tutte le cache da **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Cache Management]** pagina. Si consiglia vivamente di utilizzare [!DNL Varnish], in quanto si tratta di una soluzione efficiente per la cache delle pagine di produzione.

## Notifiche e-mail asincrone

L’abilitazione dell’impostazione &quot;Notifiche e-mail asincrone&quot; sposta in background i processi che gestiscono le notifiche e-mail di pagamento e di elaborazione dell’ordine. Per abilitare questa funzione, vai a **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Sales] > [!UICONTROL Sales Emails] > [!UICONTROL General Settings] >[!UICONTROL Asynchronous Sending]**. Consulta [E-mail vendite](https://docs.magento.com/user-guide/configuration/sales/sales-emails.html) nel _Guida utente del Magento Open Source_ per ulteriori informazioni.

## Elaborazione dati ordine asincrono

Ci possono essere momenti in cui si verificano vendite intensive in una vetrina nello stesso momento in cui [!DNL Commerce] sta eseguendo un&#39;elaborazione intensiva degli ordini. Puoi configurare [!DNL Commerce] distinguere questi due pattern di traffico a livello di database per evitare conflitti tra le operazioni di lettura e scrittura nelle tabelle corrispondenti. Puoi archiviare e indicizzare i dati dell’ordine in modo asincrono. Gli ordini vengono archiviati temporaneamente e spostati in blocco nella griglia di Order Management senza conflitti. Puoi attivare questa opzione da **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Developer] > [!UICONTROL Grid Settings] >[!UICONTROL Asynchronous indexing]**. Consulta [Aggiornamenti pianificati alla griglia](https://docs.magento.com/user-guide/sales/order-grid-updates-schedule.html) nel _Guida utente del Magento Open Source_ per ulteriori informazioni.

>[!WARNING]
>
>Il **[!UICONTROL Developer]** scheda e opzioni sono disponibili solo in [Modalità sviluppatore](../configuration/cli/set-mode.md). [Adobe Commerce sull’infrastruttura cloud](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) non supporta `Developer` modalità.

## Salvataggio configurazione asincrona

Per i progetti con un numero elevato di configurazioni a livello di archivio, il salvataggio di una configurazione di archivio può richiedere un tempo eccessivo o causare un timeout. Il _Configurazione asincrona_ Il modulo consente il salvataggio asincrono della configurazione eseguendo un processo cron che utilizza un consumer per elaborare il salvataggio in una coda di messaggi. AsyncConfig è **disabilitato** per impostazione predefinita.

Puoi abilitare AsyncConfig utilizzando l’interfaccia della riga di comando:

```bash
bin/magento setup:config:set --config-async 1
```

Il `set` Il comando scrive quanto segue in `app/etc/env.php` file:

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

In tempi di vendite intensive, [!DNL Commerce] può posticipare gli aggiornamenti delle scorte relativi agli ordini. In questo modo si riduce al minimo il numero di operazioni e si accelera il processo di posizionamento dell&#39;ordine. Tuttavia, questa opzione è rischiosa e può essere utilizzata solo quando gli ordini inevasi vengono attivati nel punto vendita, perché può portare a quantità di scorte negative. Questa opzione consente di migliorare notevolmente le prestazioni dei flussi di cassa per i negozi che possono facilmente ricaricare le scorte su richiesta. Per attivare gli aggiornamenti delle azioni differite sul sito, vai a **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Catalog] > [!UICONTROL Inventory] > [!UICONTROL Product Stock Options] >[!UICONTROL Use Deferred Stock Update]**. Consulta [Gestione dell’inventario](https://docs.magento.com/user-guide/catalog/inventory.html) nel _Guida utente di Adobe Commerce_ per ulteriori informazioni.

>[!INFO]
>
>Questa opzione è disponibile solo se **[!UICONTROL Backorder with any mode]** è attivato.

>[!INFO]
>
>Questa opzione funziona anche con [Posizionamento dell’ordine asincrono](high-throughput-order-processing.md#asynchronous-order-placement) in combinazione con [Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/guide-overview.html).

## Impostazioni di ottimizzazione lato client

Per migliorare la reattività della vetrina [!DNL Commerce] , passa all’amministratore in modalità predefinita o in modalità sviluppatore e modifica le seguenti impostazioni:

**[!UICONTROL Stores]-> [!UICONTROL Configuration] -> [!UICONTROL Advanced] -> [!UICONTROL Developer]:**

| Gruppo impostazioni | Impostazione | Valore |
| ------------------- | -------------------------- | ------ |
| Impostazioni griglia | Indicizzazione asincrona | Abilita |
| Impostazioni CSS | Minimizza file CSS | Sì |
| [!DNL JavaScript] Impostazioni | Minimizza [!DNL JavaScript] File | Sì |
| [!DNL JavaScript] Impostazioni | Abilita [!DNL JavaScript] Bundling | Sì |
| Impostazioni modello | Minify HTML | Sì |

>[!INFO]
>
>Il **[!UICONTROL Developer]** scheda e opzioni sono disponibili solo in [Modalità sviluppatore](../configuration/cli/set-mode.md). [Adobe [!DNL Commerce] sull’infrastruttura cloud](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) non supporta `Developer` modalità.

Quando si attiva **[!UICONTROL Enable [!DNL JavaScript] Bundling]** Questa opzione consente a Commerce di unire tutte le risorse JS in uno o più bundle caricati nelle pagine di vetrina. Il bundling di JS comporta un numero inferiore di richieste al server, migliorando le prestazioni della pagina. Aiuta anche il browser a memorizzare in cache le risorse JS alla prima chiamata e a riutilizzarle per tutte le ulteriori ricerche. Questa opzione consente anche la valutazione lenta, in quanto tutto JS viene caricato come testo. Avvia l&#39;analisi e la valutazione del codice solo dopo che sono state attivate azioni specifiche sulla pagina. Tuttavia, questa impostazione non è consigliata per i negozi in cui il tempo di caricamento della prima pagina è estremamente critico, perché tutto il contenuto JS verrà caricato alla prima chiamata.

>[!INFO]
>
>Consulta [Ottimizzazione dei file CSS e JavaScript su Adobe Commerce nell’infrastruttura cloud e Adobe Commerce](https://support.magento.com/hc/en-us/articles/360044482152) nel Centro assistenza Adobe Commerce_ per ulteriori informazioni sull’ottimizzazione di CSS e JavaScript.

### Suggerimenti per il bundling

* È consigliabile utilizzare strumenti di terze parti per la minimizzazione e il bundling (come [r.js](https://requirejs.org/)). [!DNL Commerce] i meccanismi incorporati non sono ottimali e vengono spediti come alternative di fallback.
* L’attivazione del protocollo HTTP/2 può essere una buona alternativa all’utilizzo del bundling JS. Il protocollo offre molti degli stessi vantaggi. È abilitato per impostazione predefinita in Adobe Commerce sui progetti di infrastruttura cloud.
* È consigliabile non utilizzare impostazioni obsolete, come l’unione di file JS e CSS, in quanto sono state progettate solo per il file JS caricato in modo sincrono nella sezione HEAD della pagina. L’utilizzo di questa tecnica può causare il malfunzionamento del bundling e della logica requireJS.

## Convalida dei segmenti cliente

Mercanti che hanno un numero elevato di [segmenti cliente](https://docs.magento.com/user-guide/marketing/customer-segments.html) potrebbe verificarsi un significativo deterioramento delle prestazioni con le azioni del cliente, ad esempio l’accesso del cliente e l’aggiunta di prodotti al carrello.

Le azioni dei clienti attivano un processo di convalida per i segmenti dei clienti, che è ciò che può causare il deterioramento delle prestazioni. Per impostazione predefinita, Adobe Commerce convalida ogni segmento in tempo reale per definire quali segmenti dei clienti corrispondono e quali no.

Per evitare il peggioramento delle prestazioni, è possibile impostare **[!UICONTROL Real-time Check if Customer is Matched by Segment]** opzione di configurazione del sistema per **No** per convalidare i segmenti dei clienti tramite una singola query SQL combinata.

Per abilitare questa ottimizzazione, vai a **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Customers] > [!UICONTROL Customer Configuration] > [!UICONTROL Customer Segments] >[!UICONTROL Real-time Check if Customer is Matched by Segment]**.

Questa impostazione migliora le prestazioni della convalida del segmento del cliente se nel sistema sono presenti molti segmenti di clienti. Tuttavia, non funziona con [database diviso](../configuration/storage/multi-master.md) o quando non vi sono clienti registrati.

## Pianificazione della manutenzione del database {#database}

È consigliabile eseguire backup periodici del database per le istanze di staging e produzione. A causa dell&#39;intensa attività di I/O delle operazioni di backup, è possibile che si verifichino backup più lenti e potenziali problemi. L&#39;esecuzione simultanea di processi di database per più ambienti potrebbe risultare più lenta a causa di conflitti per le risorse disponibili.

Per migliorare le prestazioni, pianificare l&#39;esecuzione dei backup in successione, uno alla volta, nei momenti di minore utilizzo. Questo metodo evita i conflitti di I/O e riduce i tempi di completamento, in particolare per le istanze più piccole, i database più grandi e così via.

Ad esempio, consigliamo di pianificare un backup del database di produzione seguito dal database di staging quando gli store riscontrano visite minori.

## Limita il numero di prodotti nella griglia

Per migliorare le prestazioni della griglia di prodotti per i cataloghi di grandi dimensioni, si consiglia di limitare il numero di prodotti nella griglia con **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Admin] > [!UICONTROL Admin Grids] >[!UICONTROL Limit Number of Products in Grid]** configurazione del sistema.

Questa impostazione di configurazione del sistema è disabilitata per impostazione predefinita. Attivandola, puoi limitare il numero di prodotti nella griglia a un valore specifico. **[!UICONTROL Records Limit]** è un’impostazione personalizzabile con valore minimo predefinito di `20000`.
Quando **[!UICONTROL Limit Number of Products in Grid]** l&#39;impostazione è abilitata e il numero di prodotti nella griglia è maggiore del limite di record, quindi viene restituita la raccolta limitata di record. Al raggiungimento del limite, i record totali trovati, il numero di record selezionati e gli elementi di impaginazione sono nascosti dall&#39;intestazione della griglia.

Quando il numero totale di prodotti nella griglia è limitato, non influisce sulle azioni di massa della griglia del prodotto. Influisce solo sul livello di presentazione della griglia del prodotto. Ad esempio, il numero di `20000` prodotti nella griglia, l’utente fa clic su **[!UICONTROL Select All]**, seleziona il **[!UICONTROL Update attributes]** azione di massa e aggiorna alcuni attributi. Di conseguenza, vengono aggiornati tutti i prodotti, non la raccolta limitata di `20000` record.

La limitazione relativa alla griglia di prodotti influisce solo sulle raccolte di prodotti utilizzate dai componenti dell’interfaccia utente. Di conseguenza, questa limitazione non riguarda tutte le griglie di prodotti. Solo quelli che utilizzano `Magento\Catalog\Ui\DataProvider\Product\ProductCollection`.
Puoi limitare le raccolte della griglia di prodotti solo sulle pagine seguenti:

* Griglia prodotti catalogo
* Aggiungi griglia prodotti correlati/up-selling/cross-selling
* Aggiungi prodotti al bundle prodotto
* Aggiungi prodotti al prodotto gruppo
* Pagina Crea ordine amministratore

Se non desideri che la griglia di prodotto sia limitata, ti consigliamo di utilizzare i filtri in modo più preciso affinché la raccolta dei risultati abbia meno elementi di **[!UICONTROL Records Limit]**.
