---
title: Come utilizzare il [!DNL Observation for Adobe Commerce] nerdlet
description: Scopri come utilizzare il [!DNL Observation for Adobe Commerce] nerdlet.
exl-id: 3c368814-0786-4e8f-ac81-9a77cec94677
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 0%

---

# Come utilizzare il [!DNL Observation for Adobe Commerce] nerdlet

## Approccio generale all&#39;esame dei problemi

Verifica gli stati delle risorse dell’ambiente:

* Esamina la percentuale di **[!UICONTROL Storage Free and MySQL % free storage by node]** fotogrammi.

   * Se la memoria è insufficiente, seguire i collegamenti nell&#39;intestazione del frame.

* Esamina la percentuale di **[!UICONTROL free system memory and Swap memory free in bytes]** fotogrammi.

   * Se questi presentano stati di memoria molto bassi, possono contribuire ai problemi.

* Esamina la **[!UICONTROL Alerts during the timeframe]** frame.

   * Adobe Commerce su infrastruttura cloud fornisce [!DNL Managed alerts]. Puoi fare clic sul collegamento nell’intestazione per visualizzare [!DNL Support Knowledge Base] articoli che ti aiuteranno a determinare le azioni da eseguire per avvisi specifici.

* Esamina la **[!UICONTROL CPU % by host]** frame: se presenta un utilizzo elevato della CPU, controllare [!DNL Support Knowledge Base] nell’intestazione del frame. Inoltre, verificare che le importazioni/esportazioni del database o i backup non vengano eseguiti durante i periodi di traffico di picco.

* Controlla la **[!UICONTROL Web Traffic volume compared to one week ago]** frame: se nello stesso periodo il traffico è molto più elevato rispetto alla settimana precedente, è possibile spiegarlo (ad esempio, campagna di vendita o nuovi prodotti commercializzati)?
   * Se non è possibile spiegare un aumento del traffico, considera il tempo medio di risposta (millisecondi) per l’ambiente di produzione. Il traffico più elevato contribuisce a un tempo di risposta diverso rispetto al normale? Espandi l’intervallo di tempo per verificare se si tratta di un’anomalia.
   * L’aumento del traffico incide sulle transazioni web? Controlla la **[!UICONTROL Response Code]** fotogramma per gli errori. Se il sito non è attivo, puoi fare clic sul pulsante `Site Down?` nell&#39;intestazione del frame. Il fotogramma identificherà tutti gli errori che si verificano e la loro frequenza.
   * Qualcuno ha implementato le modifiche al tuo sito web? Il **[!UICONTROL Deployment Log Entries]** Il fotogramma indica se sono state effettuate distribuzioni durante l’intervallo di tempo del problema. Se il problema si verifica subito dopo la distribuzione, è possibile che le attività di distribuzione stiano aggiungendo ulteriore carico al sito (cache cancellate, servizi riavviati, ecc.).
   * Si è verificato un upsize o un downsize? Se il sito è stato temporaneamente sottoposto a un aggiornamento, è possibile che le dimensioni del cluster siano state ripristinate. Se è stata effettuata una richiesta per aumentare la capacità del sito, potrebbe verificarsi un upsize. Controlla la **[!UICONTROL Upsize/Downsize – vCPU view over the timeline]** frame. Questo fotogramma a volte rileva un’interruzione su un nodo particolare. Se la dimensione diminuisce, potrebbe indicare un problema con uno o più nodi.

* Il **[!UICONTROL IP Frequency]** La scheda identifica la frequenza di richiesta dagli indirizzi IP che vengono eseguiti sui server di origine (il che significa che la richiesta non può essere trasmessa da [!DNL Fastly] come 74 non era memorizzato nella cache).

   * Per qualsiasi [!DNL Fastly] problemi correlati, controlla **[!UICONTROL Fastly Cache]** e selezionare il facet Error (Errore) per visualizzare la percentuale di richieste che rappresentano errori. Possono indicare un problema di back-end se coincidono con un caricamento non web.
   * Se il caricamento non sembra essere dovuto al traffico web, potrebbero esserci errori o un accumulo di richieste non web, ad esempio query lente o [!DNL crons].

* Controlla la **[!UICONTROL Database Errors]** fotogramma per gli errori che possono coincidere con la sequenza temporale del problema/problema.
* Controlla la **[!UICONTROL Database mysql-slow.log]** frame per identificare le istruzioni SQL in esecuzione. `INSERT`, `UPDATE`, e `DELETE` I comandi potrebbero richiedere un po’ di tempo se la query non è ottimizzata. Uniforme `SELECT` Le istruzioni possono essere molto inefficienti se eseguite su tabelle di grandi dimensioni.
* **[!UICONTROL PHP States]** e **[!UICONTROL PHP Errors]** i fotogrammi mostreranno potenziali problemi con PHP. Il **[!UICONTROL PHP States]** il fotogramma mostra le terminazioni del processo PHP, gli avvii e quando il servizio raggiunge lo stato pronto per ogni nodo. Il **[!UICONTROL PHP Errors]** Il frame può aiutare a isolare dove il problema è con PHP, come le dimensioni della memoria, i lavoratori, o il numero di server.
* Per visualizzare la latenza nelle transazioni, la tabella Transazioni - Media, Max, Min può essere ordinata per colonna in modo da mostrare la durata della transazione più lunga. Un cluster con sovraccarico avrà durate latenti nelle transazioni, ma mostrerà anche anomalie che potrebbero individuare un problema con un metodo o [!DNL cron].
* Il **[!UICONTROL Cron error]** il fotogramma verrà visualizzato [!DNL cron] blocchi, errori SQL che possono essere associati a [!DNL cron] registri e gestione temporanea condivisa [!DNL crons] che possono essere in esecuzione in ambienti di produzione in presenza di un ambiente di staging dedicato.
* Il [!UICONTROL ElasticSearch Errors] mostra errori che possono indicare problemi gravi con [!DNL Elasticsearch] query, dati o indici.
