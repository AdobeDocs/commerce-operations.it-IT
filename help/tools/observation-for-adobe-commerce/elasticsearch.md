---
title: "Il [!UICONTROL Elasticsearch] scheda"
description: Scopri le [!UICONTROL Elasticsearch] scheda di [!DNL Observation for Adobe Commerce].
source-git-commit: b3cc9033eb9445af3edafd8c7ae9809dbb8174fc
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 0%

---


# La [!UICONTROL Elasticsearch] scheda

## [!UICONTROL Cluster Status Summary]:

![Riepilogo stato cluster](../../assets/tools/cluster-status-summary.jpg)

Nel periodo di tempo selezionato, la **[!UICONTROL Cluster Status Summary]** la cornice mostra lo stato del colore [!DNL Elasticsearch] cluster è passato attraverso. In questo esempio, durante l&#39;intervallo temporale selezionato, il cluster era in stato Verde una volta e in stato Giallo una volta durante l&#39;intervallo temporale selezionato.

## [!UICONTROL Active Primary Shards]

![Schede principali attive](../../assets/tools/active-primary-shards.jpg)

La **[!UICONTROL Active Primary Shards]** frame mostra i numeri diversi a seconda del numero di condivisioni principali attive per il conto selezionato [!DNL Elasticsearch] servizio.

Da [!DNL Elasticsearch]: Guida definitiva [2.x]:

&quot;In [Indici aggiornabili dinamicamente](https://www.elastic.co/guide/en/elasticsearch/guide/2.x/dynamic-indices.html), abbiamo spiegato che una barba è un indice Lucene e che un [!DNL Elasticsearch] index è una raccolta di frammenti. L&#39;applicazione parla a un indice e [!DNL Elasticsearch] indirizza le richieste ai frammenti appropriati. Un frammento è l&#39;unità di scala. L&#39;indice più piccolo che si possa avere è uno con una singola frammento. Questo può essere più che sufficiente per le vostre esigenze — un singolo frammento può contenere molti dati — ma limita la vostra capacità di scalare.&quot;

Quando viene creato un indice, con tale indice vengono create diverse frammenti. Per impostazione predefinita, cinque frammenti primari sono assegnati a ciascun nuovo indice, il che significa che un indice può essere distribuito su cinque nodi (uno condiviso per nodo). Ci sono anche frammenti di replica. Si tratta principalmente di failover. Le condivisioni di replica possono servire le richieste di lettura.

## [!UICONTROL Active Shards in Cluster]

![Schede attive nel cluster](../../assets/tools/active-shards-in-cluster.jpg)

La **[!UICONTROL Active Shards in Cluster]** il frame mostra il numero totale di condivisioni principali e di replica in un [!DNL Elasticsearch] cluster.

## [!UICONTROL Index health - this will show the index name and color status]

![Salute indice](../../assets/tools/index-health.jpg)

Questo fotogramma mostra il nome dell&#39;indice e il conteggio dello stato del colore dell&#39;indice. Scorrendo la tabella, viene visualizzato lo stesso nome di indice con gli stati di colore Giallo e Rosso. Il numero che segue il nome dell&#39;indice 27 è il conteggio del colore dello stato. Se è pari a zero, non vi erano istanze dell&#39;indice che si trovavano in tale stato di colore durante i tempi selezionati.

## [!UICONTROL Elasticsearch Status by node information]

![Stato Elasticsearch](../../assets/tools/elasticsearch-status-by-node.jpg)

La **[!UICONTROL Elasticsearch Status by node information]** la cornice mostra [!DNL Elasticsearch] stato del cluster per colore e per nodo. Questo aiuta a indicare quale nodo nel [!DNL Elasticsearch] il cluster restituisce lo stato durante l&#39;intervallo temporale selezionato.

## [!UICONTROL Elasticsearch index information]

![Elasticsearch di informazioni sull&#39;indice](../../assets/tools/elasticsearch-tab-elasticsearch-index-information-image-1.jpg)

La **[!UICONTROL Elasticsearch index information]** la tabella mostra il nome dell&#39;indice, il nodo su cui si trova, il numero di documenti indicizzati, lo stato dell&#39;indice e la dimensione dell&#39;indice in MB in un dato momento.

## [!UICONTROL Elasticsearch process CPU %]

![CPU del processo di Elasticsearch](../../assets/tools/elasticsearch-process-cpu.jpg)

La **[!UICONTROL Elasticsearch process CPU %]** frame mostra la percentuale di CPU del processo per [!DNL Elasticsearch] elabora nel tempo selezionato.

## [!UICONTROL Elasticsearch Memory garbage collection]

![Elasticsearch di memoria spazzatura](../../assets/tools/elasticsearch-memory-garbage.jpg)

[!DNL Elasticsearch] è un processo Java. Se la memoria allocata è insufficiente, avvierà la raccolta degli oggetti inattivi per liberare la memoria. Se la raccolta dei rifiuti è frequente, è un&#39;indicazione che ci possono essere troppi indici o frammenti per la memoria allocata. Può esservi l&#39;opportunità di ripulire gli indici e i frammenti o [!DNL Elasticsearch] potrebbe essere necessaria più memoria.

## [!UICONTROL Elasticsearch Index information]

![Informazioni sull&#39;indice Elasticsearch](../../assets/tools/elasticsearch-index-information-2.jpg)

Man mano che gli indici vengono creati e aggiornati, lo stato dell&#39;indice potrebbe cambiare.

## [!UICONTROL Elasticsearch Index Size]

![Dimensione indice Elasticsearch](../../assets/tools/elasticsearch-index-size.jpg)

La **[!UICONTROL Elasticsearch Index Size]** frame indica il nome e la dimensione dell&#39;indice nell&#39;arco temporale selezionato. Può indicare problemi relativi alla modalità di indicizzazione di un sito.

## [!UICONTROL Elasticsearch Errors]

![Elasticsearch di errori](../../assets/tools/elasticsearch-tab-elasticsearch-errors.jpg)

La **[!UICONTROL Elasticsearch Errors]** il frame visualizza gli errori con [!DNL Elasticsearch] come esaurimento dello spazio, passaggio dallo stato Giallo a Rosso, quando tutte le condivisioni non riescono, quando si verificano problemi di parametro con le ricerche, gli errori di versione e quando tutti i nodi non sono disponibili.

## [!UICONTROL Elasticsearch Unassigned Shards]:

![Elasticsearch Schede non assegnate](../../assets/tools/elasticsearch-unassigned-shards.jpg)

Le frammenti non assegnate causano lo spostamento dello stato Verde allo stato Giallo di un cluster.
