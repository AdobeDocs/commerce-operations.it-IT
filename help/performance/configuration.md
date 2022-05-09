---
title: Tecniche consigliate per la configurazione
description: Ottimizza il tempo di risposta della distribuzione Adobe Commerce o Magenti Open Source utilizzando queste best practice.
source-git-commit: 20c4f55162b25be8906562c395abf4671437992b
workflow-type: tm+mt
source-wordcount: '959'
ht-degree: 0%

---


# Best practice di configurazione

Commerce fornisce molte impostazioni e strumenti che è possibile utilizzare per migliorare il tempo di risposta sulle pagine e fornire un throughput più elevato.

## Processi Cron

Tutte le operazioni asincrone in [!DNL Commerce] vengono eseguite utilizzando Linux `cron` comando. Vedi [Configurare ed eseguire cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html) per configurarlo correttamente.

## Indicizzatori

Un indicizzatore può essere eseguito in **[!UICONTROL Update on Save]** o **[!UICONTROL Update on Schedule]** modalità. La **[!UICONTROL Update on Save]** la modalità indicizza immediatamente ogni volta che il catalogo o altri dati cambiano. Questa modalità presuppone una bassa intensità di operazioni di aggiornamento e navigazione nello store. Può causare ritardi significativi e indisponibilità dei dati durante carichi elevati. Si consiglia di utilizzare **Aggiorna secondo programma** in produzione, perché memorizza informazioni sugli aggiornamenti dei dati ed esegue l&#39;indicizzazione per parti in background attraverso un processo cron specifico. È possibile modificare la modalità di ogni [!DNL Commerce] indicizzatore separatamente  **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Index Management]** pagina di configurazione.

La reindicizzazione su MariaDB 10.4 richiede più tempo rispetto ad altre MariaDB o [!DNL MySQL] versioni. Come soluzione alternativa, si consiglia di modificare la configurazione MariaDB predefinita e impostare i seguenti parametri:

* [`optimizer_switch='rowid_filter=off'`](https://mariadb.com/kb/en/optimizer-switch/)
* [`optimizer_use_condition_selectivity = 1`](https://mariadb.com/products/skysql/docs/reference/es/system-variables/optimizer_use_condition_selectivity/)

## Cache

Quando si avvia il negozio in produzione, attivare tutte le cache dal **[!UICONTROL System]** > [!UICONTROL Tools] > **[!UICONTROL Cache Management]** pagina. Si consiglia vivamente di utilizzare [!DNL Varnish], poiché si tratta di una soluzione efficiente per la cache delle pagine di produzione.

## Notifiche e-mail asincrone

L’abilitazione dell’impostazione &quot;Notifiche e-mail asincrone&quot; sposta in background i processi che gestiscono il pagamento e ordinano le notifiche e-mail di elaborazione. Per abilitare questa funzione, vai a **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Sales] > [!UICONTROL Sales Emails] > [!UICONTROL General Settings] >[!UICONTROL Asynchronous Sending]**. Vedi [E-mail di vendita](https://docs.magento.com/user-guide/configuration/sales/sales-emails.html) in _Guida utente di Magenti Open Source_ per ulteriori informazioni.

## Elaborazione dati ordine asincrono

Ci possono essere momenti in cui le vendite intensive su una vetrina si verificano nello stesso momento in cui [!DNL Commerce] sta eseguendo un&#39;elaborazione intensiva dell&#39;ordine. Puoi configurare [!DNL Commerce] distinguere questi due pattern di traffico a livello di database per evitare conflitti tra le operazioni di lettura e scrittura nelle tabelle corrispondenti. È possibile memorizzare e indicizzare i dati dell’ordine in modo asincrono. Gli ordini vengono inseriti in un archivio temporaneo e spostati in blocco nella griglia di Order Management senza eventuali conflitti. Puoi attivare questa opzione da **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Advanced] > [!UICONTROL Developer] > [!UICONTROL Grid Settings] >[!UICONTROL Asynchronous indexing]**. Vedi [Aggiornamenti alla griglia pianificati](https://docs.magento.com/user-guide/sales/order-grid-updates-schedule.html) in _Guida utente di Magenti Open Source_ per ulteriori informazioni.

>[!WARNING]
>
>La **[!UICONTROL Developer]** le schede e le opzioni sono disponibili solo in [Modalità Sviluppatore](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-mode.html). [Adobe Commerce su infrastruttura cloud](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) non supporta `Developer` modalità.

## Aggiornamento delle scorte differite

In periodi di vendite intensive, [!DNL Commerce] può differire gli aggiornamenti di stock relativi agli ordini. Questo riduce al minimo il numero di operazioni e velocizza il processo di posizionamento dell&#39;ordine. Tuttavia, questa opzione è rischiosa e può essere utilizzata solo quando gli ordini arretrati sono attivati nel negozio, perché questa opzione può portare a quantità di scorte negative. Questa opzione può portare un miglioramento significativo delle prestazioni sui flussi di cassa per i negozi che possono facilmente ripopolare il loro stock su richiesta. Per attivare gli aggiornamenti di stock differiti sul sito, vai a **[!UICONTROL Stores]> [!UICONTROL Settings] > [!UICONTROL Configuration] > [!UICONTROL Catalog] > [!UICONTROL Inventory] > [!UICONTROL Product Stock Options] >[!UICONTROL Use Deferred Stock Update]**. Vedi [Gestione dell&#39;inventario](https://docs.magento.com/user-guide/catalog/inventory.html) in _Guida utente di Adobe Commerce_ per ulteriori informazioni.

>[!INFO]
>
>Questa opzione è disponibile solo se **[!UICONTROL Backorder with any mode]** è attivato.

## Impostazioni di ottimizzazione lato client

Per migliorare la reattività della vetrina [!DNL Commerce] ad esempio, accedi ad Amministratore in modalità Predefinita o Sviluppatore e modifica le seguenti impostazioni:

**[!UICONTROL Stores]-> [!UICONTROL Configuration] -> [!UICONTROL Advanced] -> [!UICONTROL Developer]:**

| Gruppo impostazioni | Impostazione | Valore |
| ------------------- | -------------------------- | ------ |
| Impostazioni griglia | Indicizzazione asincrona | Abilita |
| Impostazioni CSS | Minimizzare i file CSS | Sì |
| [!DNL JavaScript] Impostazioni | Miniatura [!DNL JavaScript] File | Sì |
| [!DNL JavaScript] Impostazioni | Abilita [!DNL JavaScript] Bundle | Sì |
| Impostazioni modello | Minimizza HTML | Sì |

>[!INFO]
>
>La **[!UICONTROL Developer]** le schede e le opzioni sono disponibili solo in [Modalità Sviluppatore](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-mode.html). [Adobe [!DNL Commerce] sull&#39;infrastruttura cloud](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-test) non supporta `Developer` modalità.

Quando si attiva il pulsante **[!UICONTROL Enable [!DNL JavaScript] Bundling]** consente a Commerce di unire tutte le risorse JS in uno o più bundle caricati nelle pagine storefront. Il bundling di JS genera un minor numero di richieste al server, il che migliora le prestazioni della pagina. Aiuta anche le risorse JS nella cache del browser alla prima chiamata e riutilizzale per tutte le successive esplorazioni. Questa opzione porta anche una valutazione pigra, in quanto tutto JS viene caricato come testo. Avvia l’analisi e la valutazione del codice solo dopo l’attivazione di azioni specifiche sulla pagina. Tuttavia, questa impostazione non è consigliata per i negozi in cui il primo tempo di caricamento della pagina è estremamente critico, perché tutti i contenuti JS verranno caricati nella prima chiamata.

>[!INFO]
>
>Vedi [Ottimizzazione dei file CSS e JavaScript su Adobe Commerce su infrastruttura cloud e Adobe Commerce](https://support.magento.com/hc/en-us/articles/360044482152) in Adobe Commerce Help Center_ per ulteriori informazioni sull&#39;ottimizzazione di CSS e JavaScript.

### Suggerimenti per il bundle

* È consigliabile utilizzare strumenti di terze parti per la minimizzazione e il bundling (come [r.js](http://requirejs.org/)). [!DNL Commerce] i meccanismi incorporati non sono ottimali e vengono spediti come alternative di fallback.
* L&#39;attivazione del protocollo HTTP2 può essere una buona alternativa all&#39;utilizzo del bundling JS. Il protocollo offre più o meno gli stessi vantaggi.
* Non consigliamo di utilizzare impostazioni obsolete come l’unione di file JS e CSS, in quanto sono stati progettati solo per JS caricato in modo sincrono nella sezione HEAD della pagina. L&#39;utilizzo di questa tecnica può causare il funzionamento errato del bundling e richiedere il funzionamento errato della logica JS.

## Pianificazione della manutenzione del database {#database}

È consigliabile eseguire backup periodici del database per le istanze Staging e Production. A causa della natura intensiva di I/O delle operazioni di backup, è possibile che si verifichino backup più lenti e problemi potenziali. L’esecuzione simultanea di processi di database per più ambienti può potenzialmente essere più lenta a causa della controversia per le risorse disponibili.

Per migliorare le prestazioni, pianificare i backup in modo che vengano eseguiti in successione, uno alla volta, nei momenti di picco. Questo metodo evita i conflitti di I/O e riduce il tempo di completamento, soprattutto per le istanze più piccole, i database più grandi e così via.

Ad esempio, consigliamo di pianificare un backup del database di produzione seguito dal database di staging quando gli archivi incontrano visite inferiori.
