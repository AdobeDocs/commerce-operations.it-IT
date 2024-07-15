---
title: Come utilizzare il nerdlet  [!DNL Observation for Adobe Commerce]
description: Scopri come utilizzare il nerdlet  [!DNL Observation for Adobe Commerce] .
exl-id: 3c368814-0786-4e8f-ac81-9a77cec94677
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '627'
ht-degree: 0%

---

# Come utilizzare il nerdlet [!DNL Observation for Adobe Commerce]

## Approccio generale all&#39;esame dei problemi

Verifica gli stati delle risorse dell’ambiente:

* Esaminare la percentuale di **[!UICONTROL Storage Free and MySQL % free storage by node]** frame.

   * Se la memoria è insufficiente, seguire i collegamenti nell&#39;intestazione del frame.

* Esaminare la percentuale di **[!UICONTROL free system memory and Swap memory free in bytes]** frame.

   * Se questi presentano stati di memoria molto bassi, possono contribuire ai problemi.

* Esaminare il frame **[!UICONTROL Alerts during the timeframe]**.

   * Adobe Commerce su infrastruttura cloud fornisce [!DNL Managed alerts]. Puoi fare clic sul collegamento nell&#39;intestazione per visualizzare [!DNL Support Knowledge Base] articoli che ti aiuteranno a determinare le azioni da parte tua per avvisi specifici.

* Esaminare il frame **[!UICONTROL CPU % by host]**: se è presente un utilizzo elevato della CPU, controllare il frame nell&#39;articolo [!DNL Support Knowledge Base] nell&#39;intestazione. Inoltre, verificare che le importazioni/esportazioni del database o i backup non vengano eseguiti durante i periodi di traffico di picco.

* Controlla il frame **[!UICONTROL Web Traffic volume compared to one week ago]**: se il traffico è molto più elevato della settimana precedente durante lo stesso periodo, è possibile spiegarlo (ad esempio, campagna di vendita o nuovi prodotti commercializzati)?
   * Se non è possibile spiegare un aumento del traffico, considera il tempo medio di risposta (millisecondi) per l’ambiente di produzione. Il traffico più elevato contribuisce a un tempo di risposta diverso rispetto al normale? Espandi l’intervallo di tempo per verificare se si tratta di un’anomalia.
   * L’aumento del traffico incide sulle transazioni web? Verificare la presenza di errori nel frame **[!UICONTROL Response Code]**. Se il sito non è attivo, è possibile fare clic sul collegamento `Site Down?` nell&#39;intestazione del frame. Il fotogramma identificherà tutti gli errori che si verificano e la loro frequenza.
   * Qualcuno ha implementato le modifiche al tuo sito web? Il frame **[!UICONTROL Deployment Log Entries]** indica se sono state eseguite distribuzioni durante l&#39;intervallo di tempo del problema. Se il problema si verifica subito dopo la distribuzione, è possibile che le attività di distribuzione stiano aggiungendo ulteriore carico al sito (cache cancellate, servizi riavviati, ecc.).
   * Si è verificato un upsize o un downsize? Se il sito è stato temporaneamente sottoposto a un aggiornamento, è possibile che le dimensioni del cluster siano state ripristinate. Se è stata effettuata una richiesta per aumentare la capacità del sito, potrebbe verificarsi un upsize. Controllare il frame **[!UICONTROL Upsize/Downsize – vCPU view over the timeline]**. Questo fotogramma a volte rileva un’interruzione su un nodo particolare. Se la dimensione diminuisce, potrebbe indicare un problema con uno o più nodi.

* La scheda **[!UICONTROL IP Frequency]** identifica la frequenza delle richieste dagli indirizzi IP effettuate sui server di origine (il che significa che la richiesta non può essere servita da [!DNL Fastly] poiché 74 non è stata memorizzata nella cache).

   * Per qualsiasi problema correlato a [!DNL Fastly], controlla il frame **[!UICONTROL Fastly Cache]** e seleziona il facet Error per visualizzare la percentuale di richieste che sono errori. Possono indicare un problema di back-end se coincidono con un caricamento non web.
   * Se il caricamento non sembra essere dovuto al traffico web, potrebbero esserci errori o un accumulo di richieste non web, ad esempio query lente o [!DNL crons].

* Controllare il frame **[!UICONTROL Database Errors]** per individuare eventuali errori che potrebbero coincidere con la sequenza temporale del problema.
* Controllare il frame **[!UICONTROL Database mysql-slow.log]** per identificare le istruzioni SQL in esecuzione. I comandi `INSERT`, `UPDATE` e `DELETE` potrebbero richiedere alcuni minuti se la query non è ottimizzata. Anche le istruzioni `SELECT` possono essere molto inefficienti se eseguite su tabelle di grandi dimensioni.
* **[!UICONTROL PHP States]** e **[!UICONTROL PHP Errors]** fotogrammi mostreranno potenziali problemi con PHP. Nel frame **[!UICONTROL PHP States]** verranno visualizzate le interruzioni del processo PHP, gli avvii e il momento in cui il servizio raggiunge lo stato ready per nodo. Il frame **[!UICONTROL PHP Errors]** può aiutare a isolare la posizione del problema con PHP, ad esempio le dimensioni della memoria, i processi di lavoro o il numero di server.
* Per visualizzare la latenza nelle transazioni, la tabella Transazioni - Media, Max, Min può essere ordinata per colonna in modo da mostrare la durata della transazione più lunga. Un cluster sovraccarico avrà durate latenti nelle transazioni, ma mostrerà anche anomalie che potrebbero individuare un problema con un metodo o [!DNL cron].
* Nel frame **[!UICONTROL Cron error]** verranno visualizzati [!DNL cron] blocchi, errori SQL che possono essere associati a [!DNL cron] registri e gestione temporanea condivisa [!DNL crons] che potrebbero essere in esecuzione in ambienti di produzione in presenza di un ambiente di gestione temporanea dedicato.
* Il frame [!UICONTROL ElasticSearch Errors] mostra errori che possono indicare problemi gravi con [!DNL Elasticsearch] query, dati o indici.
