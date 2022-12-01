---
title: "Il [!UICONTROL CDN] scheda"
description: Scopri le [!UICONTROL CDN] scheda di [!DNL Observation for Adobe Commerce].
source-git-commit: 424c832ba7580e5d766dea33e3b776eaca7a0d77
workflow-type: tm+mt
source-wordcount: '699'
ht-degree: 0%

---

# La [!UICONTROL CDN] scheda

Questa scheda contiene informazioni incentrate sulle [!DNL content delivery network (CDN)]. Nel caso di Adobe Commerce Cloud, è la [!DNL Fastly] servizio.

## [!UICONTROL HIT rate]

![Tasso di hit](../../assets/tools/observation-for-adobe-commerce/cdn-tab-1.png)

La **[!UICONTROL HIT rate]** frame mostra il numero di richieste memorizzabili in cache che hanno generato [!UICONTROL HITS] all&#39;ultimo minuto. Questo indica che la memorizzazione in cache è riuscita. La freccia a destra mostra la percentuale sopra o sotto la stessa ora di una settimana fa.

## [!UICONTROL HIT Processing]

![Elaborazione HIT](../../assets/tools/observation-for-adobe-commerce/cdn-tab-2.png)

Questo **[!UICONTROL HIT processing]** mostra il numero di richieste memorizzabili nella cache che hanno generato [!UICONTROL HITS] durante la settimana.

## [!UICONTROL MISS rate]

![Tasso MISS](../../assets/tools/observation-for-adobe-commerce/cdn-tab-3.png)

Questo **[!UICONTROL MISS rate]** mostra il numero di mancate richieste memorizzabili nella cache all’ultimo minuto. Se la richiesta non viene memorizzata nella cache e deve essere trasmessa al server di origine per distribuire il contenuto, si verifica un errore di mancato recapito. Il valore a destra è il confronto tra aumento/diminuzione e il numero di minuti al minuto una settimana prima.

## [!UICONTROL MISS time]

![tempo mancato](../../assets/tools/observation-for-adobe-commerce/cdn-tab-4.png)

## [!UICONTROL HIT Ratio]

![Rapporto di hit](../../assets/tools/observation-for-adobe-commerce/cdn-tab-5.png)

## [!UICONTROL Error Percentage]

![Percentuale errori](../../assets/tools/observation-for-adobe-commerce/cdn-tab-6.png)

La **[!UICONTROL Error Percentage]** visualizza il valore della percentuale di ERRORE delle richieste e mostra l&#39;incremento/diminuzione relativi rispetto allo stesso tempo di una settimana prima.

## [!UICONTROL Total Requests]

![Richieste totali](../../assets/tools/observation-for-adobe-commerce/cdn-tab-7.png)

## [!UICONTROL ERROR rate]

![Frequenza errori](../../assets/tools/observation-for-adobe-commerce/cdn-tab-8.png)

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds]

![Risposta media della cache definitiva per il periodo di tempo selezionato in secondi](../../assets/tools/observation-for-adobe-commerce/cdn-tab-9.png)

Questo fotogramma mostra la durata in secondi delle richieste memorizzabili nella cache, il che significa che se un `cache_response` è un [!UICONTROL MISS], visualizza la media delle risposte memorizzate nella cache perse per il tempo selezionato.

## [!UICONTROL Fastly Cache Average Response for selected time period in seconds, faceted by POP]

![Risposta media della cache definitiva per il periodo di tempo selezionato in secondi sfaccettato da POP](../../assets/tools/observation-for-adobe-commerce/cdn-tab-10.png)

## [!UICONTROL Total Bandwidth (All POPs) during the selected timeframe, compared with 1 week ago (% increase/decrease)]

![Larghezza di banda totale (tutti gli POP) nell&#39;intervallo di tempo selezionato, rispetto a 1 settimana fa (% aumento/diminuzione)](../../assets/tools/observation-for-adobe-commerce/cdn-tab-11.png)

## [!UICONTROL Requests – Since selected timeframe compared with one week ago]

![Richieste: da un intervallo di tempo selezionato rispetto a una settimana fa](../../assets/tools/observation-for-adobe-commerce/cdn-tab-12.png)

Questo frame è simile alla casella di riepilogo per [!UICONTROL Total Requests] nella parte superiore, ma mostra il conteggio delle richieste delle settimane precedenti. Si tratta di tutte le richieste, non solo di quelle memorizzabili nella cache (dove `is_cacheable` è vero).

## [!UICONTROL Response Count]

![Conteggio risposte](../../assets/tools/observation-for-adobe-commerce/cdn-tab-13.png)

## [!UICONTROL Bandwidth by POP]

![Larghezza di banda per POP](../../assets/tools/observation-for-adobe-commerce/cdn-tab-14.png)

## [!UICONTROL Top 5 URLs (5xx or 3xx status codes)]

![Primi 5 URL (codici di stato 5xx o 3xx)](../../assets/tools/observation-for-adobe-commerce/cdn-tab-15.gif)

La **[!UICONTROL Top 5 URLs]** visualizza i primi 5 URL con risposte di errore 5xx o 3xx. A causa del vincolo di spazio, dovrai passare il cursore sull’URL per visualizzare il codice di errore specifico associato a tale URL. (esempio nella casella rossa della figura sopra).

## [!UICONTROL Top 25 URLs (200 status)]

![Primi 25 URL (stato 200)](../../assets/tools/observation-for-adobe-commerce/cdn-tab-16.gif)

La **[!UICONTROL Top 25 URLs]** frame mostra gli URL che hanno restituito uno stato di 200 per conteggio durante l&#39;intervallo temporale selezionato.

## [!UICONTROL Duration by Response Status]

![Durata in base allo stato della risposta](../../assets/tools/observation-for-adobe-commerce/cdn-tab-17.png)

La **[!UICONTROL Duration by Response Status]** Il grafico visualizza le risposte di errore in base al conteggio durante l’intervallo temporale selezionato, in base al codice di stato dell’errore.

## [!UICONTROL Duration by Response Status, top 25 urls]

![Durata per stato di risposta, primi 25 url](../../assets/tools/observation-for-adobe-commerce/cdn-tab-18.gif)

La **[!UICONTROL Duration by Response Status, top 25 URLs]** Il grafico mostra i primi 25 URL per la durata della risposta in secondi. Potrebbe essere necessario passare il mouse sull&#39;URL per visualizzare l&#39;intero percorso. Inoltre, per rimuovere tutti gli URL tranne uno, fai clic su di esso. Puoi quindi aggiungere nuovamente altri URL facendo clic su di essi singolarmente. Per rimuovere singoli URL, puoi tenere premuto il tasto e fare clic su ogni URL per rimuoverli dal grafico.

## [!UICONTROL Duration by Response Status, top 25 non-200 status]

![Durata in base allo stato di risposta, primo stato 25 non 200](../../assets/tools/observation-for-adobe-commerce/cdn-tab-19.gif)

La **[!UICONTROL Duration by Response Status, top 25 non-200 status]** Il grafico è simile all&#39;ultimo, tranne per il fatto che l&#39;attenzione è rivolta a codici di stato non-200 o a codici di stato di errore. Mostrerà il codice di errore e quindi l’URL. Potrebbe essere necessario passare il mouse sull&#39;URL per visualizzare l&#39;intero percorso. Inoltre, per rimuovere tutti gli URL tranne uno, fai clic su di esso. Puoi quindi aggiungere nuovamente altri URL facendo clic su di essi singolarmente. Per rimuovere singoli URL, puoi tenere premuto il tasto e fare clic su ogni URL per rimuoverli dal grafico.

## [!UICONTROL Error Count by POP timeline]

![Conteggio errori per timeline POP](../../assets/tools/observation-for-adobe-commerce/cdn-tab-20.png)

La **[!UICONTROL Error Count by POP timeline]** Il grafico mostra il conteggio degli stati di errore nella timeline dell’intervallo temporale selezionato, in base al codice di errore.

## [!UICONTROL Duration by Response status, top 25 client IP, non-200 status]

![Durata in base allo stato di risposta, primo 25 IP client, stato diverso da 200](../../assets/tools/observation-for-adobe-commerce/cdn-tab-21.gif)

La **[!UICONTROL Duration by Response status, top 25 client IP, non 200 status]** Il grafico mostra gli indirizzi IP in base alla durata media nell’arco temporale selezionato in cui erano presenti codici di errore di stato.

## [!UICONTROL IP Frequency]

![Frequenza IP](../../assets/tools/observation-for-adobe-commerce/cdn-tab-22.jpeg)

La **[!UICONTROL IP Frequency]** il frame conta gli stati (&quot;MISS&quot; e &quot;PASS&quot;) per ogni IP da [!DNL Fastly] registri. Le richieste web con questi stati raggiungeranno il server di origine e aggiungeranno il caricamento al server. Mostra i venti indirizzi principali in frequenza. Questo frame può essere utilizzato per rilevare attacchi IP o fonti di carico pesante su un sito web. Questo grafico è presente anche nella scheda di riepilogo e si trova qui per un semplice confronto con più dettagli sul [!DNL Fastly] informazioni di registro visualizzate in questa scheda.
