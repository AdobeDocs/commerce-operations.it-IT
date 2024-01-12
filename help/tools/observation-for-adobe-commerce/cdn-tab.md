---
title: Il [!UICONTROL CDN] scheda
description: Scopri di più su [!UICONTROL CDN] scheda di [!DNL Observation for Adobe Commerce].
exl-id: db22bbca-2033-4e9a-8799-b47d84bdd720
feature: Configuration, Observability
source-git-commit: e753528a1d74eda0a1393e2cc455f33f529db739
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 0%

---

# Il [!UICONTROL CDN] scheda

Questa scheda contiene informazioni incentrate su [!DNL content delivery network (CDN)]. Nel caso di Adobe Commerce Cloud, questo è il [!DNL Fastly] servizio.

## [!UICONTROL HIT rate]

![Percentuale di HIT](../../assets/tools/observation-for-adobe-commerce/cdn-tab-1.png)

Il **[!UICONTROL HIT rate]** mostra il numero di richieste memorizzabili in cache che hanno generato [!UICONTROL HITS] all&#39;ultimo minuto. Ciò indica che la memorizzazione in cache è avvenuta correttamente. La freccia a destra mostra la percentuale al di sopra o al di sotto della stessa ora di una settimana fa.

## [!UICONTROL HIT Processing]

![Elaborazione HIT](../../assets/tools/observation-for-adobe-commerce/cdn-tab-2.png)

Questo **[!UICONTROL HIT processing]** mostra il numero di richieste memorizzabili in cache che hanno generato [!UICONTROL HITS] durante la settimana.

## [!UICONTROL MISS rate]

![Percentuale mancati riscontri](../../assets/tools/observation-for-adobe-commerce/cdn-tab-3.png)

Questo **[!UICONTROL MISS rate]** mostra il numero di richieste memorizzabili in cache non riuscite all’ultimo minuto. Un errore si verifica quando la richiesta non viene memorizzata in cache e deve essere passata al server di origine per distribuire il contenuto. Il valore a destra è il confronto tra aumento/diminuzione e il numero di minuti al minuto una settimana prima.

## [!UICONTROL MISS time]

![Tempo per assenza](../../assets/tools/observation-for-adobe-commerce/cdn-tab-4.png)

## [!UICONTROL HIT Ratio]

![Percentuale di hit](../../assets/tools/observation-for-adobe-commerce/cdn-tab-5.png)

## [!UICONTROL Error Percentage]

![Percentuale errori](../../assets/tools/observation-for-adobe-commerce/cdn-tab-6.png)

Il **[!UICONTROL Error Percentage]** mostra il valore della percentuale di ERRORE delle richieste e mostra l’aumento o la diminuzione relativa rispetto alla stessa ora della settimana precedente.

## [!UICONTROL Total Requests]

![Richieste totali](../../assets/tools/observation-for-adobe-commerce/cdn-tab-7.png)

## [!UICONTROL ERROR rate]

![Percentuale di errori](../../assets/tools/observation-for-adobe-commerce/cdn-tab-8.png)

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds]

![Risposta media Fastly Cache per il periodo di tempo selezionato in secondi](../../assets/tools/observation-for-adobe-commerce/cdn-tab-9.png)

Questo fotogramma mostra la durata in secondi delle richieste memorizzabili in cache, il che significa che se `cache_response` è un [!UICONTROL MISS], visualizza la media delle risposte mancate nella cache per il tempo selezionato.

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds, faceted by POP]

![Risposta media Fastly Cache per il periodo di tempo selezionato in secondi con facet POP](../../assets/tools/observation-for-adobe-commerce/cdn-tab-10.png)

*POP* in questo contesto si riferisce a un punto di presenza (POP) configurato per funzionare come pool per l’archiviazione della cache. Consulta [Punti di presenza](https://developer.fastly.com/learning/concepts/pop/).

## [!UICONTROL Total Bandwidth (All POPs) during the selected timeframe, compared with 1 week ago (% increase/decrease)]

![Larghezza di banda totale (tutti i POP) durante l&#39;intervallo di tempo selezionato, rispetto a 1 settimana fa (% aumento/diminuzione)](../../assets/tools/observation-for-adobe-commerce/cdn-tab-11.png)

## [!UICONTROL Requests – Since selected timeframe compared with one week ago]

![Richieste: dall’intervallo di tempo selezionato rispetto a una settimana fa](../../assets/tools/observation-for-adobe-commerce/cdn-tab-12.png)

Questa cornice è simile alla casella di riepilogo per [!UICONTROL Total Requests] in alto, ma mostra i conteggi delle richieste delle settimane precedenti. Si tratta di tutte le richieste, non solo di quelle memorizzabili in cache (dove `is_cacheable` è true).

## [!UICONTROL Response Count]

![Conteggio risposte](../../assets/tools/observation-for-adobe-commerce/cdn-tab-13.png)

## [!UICONTROL Bandwidth by POP]

![Larghezza di banda per POP](../../assets/tools/observation-for-adobe-commerce/cdn-tab-14.png)

## [!UICONTROL Top 5 URLs (5xx or 3xx status codes)]

![Primi 5 URL (codici di stato 5xx o 3xx)](../../assets/tools/observation-for-adobe-commerce/cdn-tab-15.gif)

Il **[!UICONTROL Top 5 URLs]** visualizza mostra i primi 5 URL che presentano risposte di errore 5xx o 3xx. A causa del vincolo di spazio, dovrai passare il cursore sull’URL per visualizzare il codice di errore specifico associato a tale URL. (esempio nella casella rossa della figura precedente).

## [!UICONTROL Top 25 URLs (200 status)]

![Primi 25 URL (stato 200)](../../assets/tools/observation-for-adobe-commerce/cdn-tab-16.gif)

Il **[!UICONTROL Top 25 URLs]** frame mostra gli URL che hanno restituito uno stato 200 in base al conteggio durante l’intervallo di tempo selezionato.

## [!UICONTROL Duration by Response Status]

![Durata in base allo stato della risposta](../../assets/tools/observation-for-adobe-commerce/cdn-tab-17.png)

Il **[!UICONTROL Duration by Response Status]** in grafo vengono visualizzate le risposte di errore in base al conteggio durante l’arco temporale selezionato, interessato dal codice di stato dell’errore.

## [!UICONTROL Duration by Response Status, top 25 urls]

![Durata in base allo stato di risposta, primi 25 URL](../../assets/tools/observation-for-adobe-commerce/cdn-tab-18.gif)

Il **[!UICONTROL Duration by Response Status, top 25 URLs]** il grafico mostra i primi 25 URL in base alla durata della risposta in secondi. Per visualizzare l’intero percorso, potrebbe essere necessario passare il cursore del mouse sull’URL. Inoltre, per rimuovere tutti gli URL tranne uno, fai clic su di essi. Puoi quindi aggiungere nuovamente altri URL facendo clic su di essi singolarmente. Se desideri rimuovere singoli URL, tieni premuto il tasto e fai clic su ciascun URL per rimuoverli dal grafico.

## [!UICONTROL Duration by Response Status, top 25 non-200 status]

![Durata per stato risposta, primi 25 non 200 stati](../../assets/tools/observation-for-adobe-commerce/cdn-tab-19.gif)

Il **[!UICONTROL Duration by Response Status, top 25 non-200 status]** Il grafico è simile all&#39;ultimo tranne per il fatto che lo stato attivo è sui codici di stato diversi da 200 o sui codici di stato di errore. Il codice di errore e l’URL verranno visualizzati. Per visualizzare l’intero percorso, potrebbe essere necessario passare il cursore del mouse sull’URL. Inoltre, per rimuovere tutti gli URL tranne uno, fai clic su di essi. Puoi quindi aggiungere nuovamente altri URL facendo clic su di essi singolarmente. Se desideri rimuovere singoli URL, tieni premuto il tasto e fai clic su ciascun URL per rimuoverli dal grafico.

## [!UICONTROL Error Count by POP timeline]

![Conteggio degli errori per sequenza temporale POP](../../assets/tools/observation-for-adobe-commerce/cdn-tab-20.png)

Il **[!UICONTROL Error Count by POP timeline]** in grafo viene visualizzato il conteggio degli stati di errore lungo l’intervallo temporale selezionato, interessato dal codice di errore.

## [!UICONTROL Duration by Response status, top 25 client IP, non-200 status]

![Durata in base allo stato di risposta, primi 25 IP client, stato non 200](../../assets/tools/observation-for-adobe-commerce/cdn-tab-21.gif)

Il **[!UICONTROL Duration by Response status, top 25 client IP, non 200 status]** Il grafico mostra gli indirizzi IP per la durata media nell’arco temporale selezionato in cui erano presenti codici di errore di stato.

## [!UICONTROL IP Frequency]

![Frequenza IP](../../assets/tools/observation-for-adobe-commerce/cdn-tab-22.jpeg)

Il **[!UICONTROL IP Frequency]** conteggia gli stati (&quot;MISS&quot; e &quot;PASS&quot;) di ciascun IP proveniente da [!DNL Fastly] log. Le richieste web con questi stati raggiungono il server di origine e aggiungono un carico al server. Mostra i primi venti indirizzi in frequenza. Questo frame può essere utilizzato per rilevare attacchi IP o sorgenti di carico pesante su un sito web. Questo grafico è presente anche nella scheda di riepilogo e si trova qui per un facile confronto con ulteriori dettagli sulla [!DNL Fastly] informazioni di registro visualizzate in questa scheda.
