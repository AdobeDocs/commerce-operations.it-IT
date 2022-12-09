---
title: "Come utilizzare il [!DNL Observation for Adobe Commerce] nerdlet"
description: Scopri come utilizzare il [!DNL Observation for Adobe Commerce] nerdlet.
source-git-commit: e6038d6f0add9d01d650914b35a1daba885fa7f8
workflow-type: tm+mt
source-wordcount: '626'
ht-degree: 0%

---

# Come utilizzare il [!DNL Observation for Adobe Commerce] nerdlet

## Approccio generale per l&#39;esame delle questioni

Controlla gli stati delle risorse dell&#39;ambiente:

* Esamina la percentuale di **[!UICONTROL Storage Free and MySQL % free storage by node]** fotogrammi.

   * Seguire i collegamenti nell&#39;intestazione del frame se si vede poca memoria.

* Esamina la percentuale di **[!UICONTROL free system memory and Swap memory free in bytes]** fotogrammi.

   * Se questi stati di memoria di visualizzazione sono molto bassi, possono contribuire ai problemi.

* Esamina la **[!UICONTROL Alerts during the timeframe]** telaio.

   * L’infrastruttura Adobe Commerce su cloud fornisce [!DNL Managed alerts]. Puoi fare clic sul collegamento nell’intestazione per visualizzare [!DNL Support Knowledge Base] articoli che consentono di determinare le azioni da parte dell&#39;utente per avvisi specifici.

* Esamina la **[!UICONTROL CPU % by host]** frame: Se presenta un elevato utilizzo della CPU, controlla il [!DNL Support Knowledge Base] nell&#39;intestazione della cornice. Inoltre, verificare che le importazioni/esportazioni o i backup del database non vengano eseguiti durante i periodi di picco del traffico.

* Controlla la **[!UICONTROL Web Traffic volume compared to one week ago]** frame: Se il traffico è molto più elevato della settimana precedente durante lo stesso periodo, può essere spiegato (campagna di vendita o nuovi prodotti che sono stati commercializzati, ad esempio)?
   * Se non è possibile spiegare un aumento del traffico, guarda il tempo medio di risposta (millisecondi) per l&#39;ambiente di produzione. Il traffico più elevato contribuisce a un tempo di risposta è diverso da quello normale? Espandi l’intervallo di tempo per vedere se si tratta di un’anomalia.
   * L’aumento del traffico influisce sulle transazioni web? Controlla la **[!UICONTROL Response Code]** per gli errori. Se il sito è inattivo, puoi fare clic sul pulsante `Site Down?` nell&#39;intestazione del frame. Il frame identificherà eventuali errori e la relativa frequenza.
   * Qualcuno ha implementato le modifiche al tuo sito web? La **[!UICONTROL Deployment Log Entries]** indica se sono state eseguite distribuzioni durante l’intervallo di tempo del problema. Se il problema si verifica subito dopo la distribuzione, potrebbe essere che le attività di distribuzione stanno aggiungendo ulteriore carico al sito (cache cancellate, servizi riavviati, ecc.).
   * Si è verificato un aumento o un ridimensionamento? Se il sito è stato temporaneamente upsize, potrebbe essere stato ripristinato alle dimensioni originali del cluster. Se è stata effettuata una richiesta per aumentare la capacità del sito, potrebbe verificarsi un aggiornamento. Controlla la **[!UICONTROL Upsize/Downsize – vCPU view over the timeline]** telaio. Questo frame a volte rileva un&#39;interruzione su un particolare nodo. Se vedi la diminuzione delle dimensioni, ciò potrebbe indicare un problema con uno o più nodi.

* La **[!UICONTROL IP Frequency]** la scheda identifica la frequenza di richiesta dagli indirizzi IP effettuati rispetto ai server di origine (il che significa che non è stato possibile soddisfare la richiesta da [!DNL Fastly] come 74 non era memorizzato nella cache).

   * Per qualsiasi [!DNL Fastly] problemi correlati, controlla il **[!UICONTROL Fastly Cache]** e seleziona il facet Errore per visualizzare la percentuale di richieste che sono errori. Possono indicare un problema di backend se coincidono con il caricamento non web.
   * Se il caricamento non sembra dovuto al traffico web, potrebbero esserci errori o una compilazione di richieste non web, come query lente o [!DNL crons].

* Controlla la **[!UICONTROL Database Errors]** per gli errori che possono coincidere con la timeline del problema o del problema.
* Controlla la **[!UICONTROL Database mysql-slow.log]** per identificare le istruzioni SQL in corso. `INSERT`, `UPDATE`e `DELETE` Se la query non è ottimizzata, i comandi potrebbero richiedere un po&#39; di tempo. Pari `SELECT` le istruzioni possono essere molto inefficienti se eseguite contro tabelle di grandi dimensioni.
* **[!UICONTROL PHP States]** e **[!UICONTROL PHP Errors]** I frame mostreranno potenziali problemi con PHP. La **[!UICONTROL PHP States]** frame mostrerà le terminazioni del processo PHP, gli avvii e quando il servizio raggiunge lo stato pronto per nodo. La **[!UICONTROL PHP Errors]** Il frame può aiutare a isolare dove si verifica il problema con PHP, ad esempio le dimensioni della memoria, i lavoratori o il numero di server.
* Per visualizzare la latenza nelle transazioni, è possibile ordinare per colonna la tabella Transactions - Avg, Max, Min per visualizzare la durata della transazione più lunga. Un cluster sovraccaricato avrà durate latenti nelle transazioni, ma mostrerà anche anomalie che potrebbero identificare un problema con un metodo o [!DNL cron].
* La **[!UICONTROL Cron error]** il fotogramma verrà visualizzato [!DNL cron] blocchi, errori SQL che possono essere associati a [!DNL cron] registri e gestione temporanea condivisa [!DNL crons] che può essere in esecuzione negli ambienti di produzione quando è presente un ambiente di staging dedicato.
* La [!UICONTROL ElasticSearch Errors] il frame mostra errori che possono indicare problemi importanti con [!DNL Elasticsearch] query, dati o indici.
