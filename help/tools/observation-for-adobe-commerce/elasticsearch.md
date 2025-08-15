---
title: Scheda [!UICONTROL Elasticsearch]
description: Scopri la scheda [!UICONTROL Elasticsearch] di [!DNL Observation for Adobe Commerce].
exl-id: e98d351d-b3b1-47bc-bc0d-f96ba9ec2b80
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '530'
ht-degree: 0%

---

# Scheda [!UICONTROL Elasticsearch]

## [!UICONTROL Cluster Status Summary]:

![Riepilogo stato cluster](../../assets/tools/cluster-status-summary.jpg)

Nel periodo di tempo selezionato, il frame **[!UICONTROL Cluster Status Summary]** mostra gli stati colore attraversati dal cluster [!DNL Elasticsearch]. In questo esempio, durante l’intervallo temporale selezionato, il cluster era in stato Verde una volta e in stato Giallo una volta durante l’intervallo temporale selezionato.

## [!UICONTROL Active Primary Shards]

![Parti primarie attive](../../assets/tools/active-primary-shards.jpg)

Il frame **[!UICONTROL Active Primary Shards]** mostra i numeri diversi a seconda del numero di partizioni primarie attive per il servizio [!DNL Elasticsearch] dell&#39;account selezionato.

Da [!DNL Elasticsearch]: Guida definitiva [2.x]:

&quot;In [Indici aggiornabili dinamicamente](https://www.elastic.co/guide/en/elasticsearch/guide/2.x/dynamic-indices.html), è stato spiegato che un frammento è un indice Lucene e che un indice [!DNL Elasticsearch] è una raccolta di frammenti. L&#39;applicazione comunica con un indice e [!DNL Elasticsearch] indirizza le richieste alle condivisioni appropriate. Un frammento è l&#39;unità di scala. L&#39;indice più piccolo che si può avere è quello con una singola partizione. Questo può essere più che sufficiente per le vostre esigenze — un singolo frammento può contenere molti dati — ma limita la vostra capacità di scalare.&quot;

Quando viene creato un indice, con tale indice vengono create diverse partizioni. Per impostazione predefinita, a ogni nuovo indice vengono assegnate cinque partizioni primarie, il che significa che un indice può essere distribuito su cinque nodi (una partizione per nodo). Sono inoltre disponibili frammenti di replica. Questi sono principalmente destinati al failover. I frammenti di replica possono servire le richieste di lettura.

## [!UICONTROL Active Shards in Cluster]

![Condivisioni attive nel cluster](../../assets/tools/active-shards-in-cluster.jpg)

Il frame **[!UICONTROL Active Shards in Cluster]** mostra il numero totale di condivisioni primarie e di replica in un cluster [!DNL Elasticsearch].

## [!UICONTROL Index health - this will show the index name and color status]

![Integrità indice](../../assets/tools/index-health.jpg)

Questa cornice mostra il nome dell&#39;indice e il conteggio dello stato del colore dell&#39;indice. Scorrere la tabella per visualizzare lo stesso nome di indice con gli stati Giallo e Rosso. Il numero che segue il nome dell’indice 27 è il conteggio del colore dello stato. Se è uguale a zero, non vi sono state istanze dell’indice che si trovavano nello stato di quel colore durante gli intervalli di tempo selezionati.

## [!UICONTROL Elasticsearch Status by node information]

![Stato Elasticsearch](../../assets/tools/elasticsearch-status-by-node.jpg)

Il frame **[!UICONTROL Elasticsearch Status by node information]** mostra lo stato del cluster [!DNL Elasticsearch] per colore e per nodo. Ciò consente di indicare quale nodo nel cluster [!DNL Elasticsearch] sta restituendo quale stato durante l&#39;intervallo di tempo selezionato.

## [!UICONTROL Elasticsearch index information]

![Informazioni indice Elasticsearch](../../assets/tools/elasticsearch-tab-elasticsearch-index-information-image-1.jpg)

La tabella **[!UICONTROL Elasticsearch index information]** mostra il nome dell&#39;indice, il nodo in cui si trova, il numero di documenti indicizzati, lo stato dell&#39;indice e la dimensione dell&#39;indice in MB in un determinato momento.

## [!UICONTROL Elasticsearch process CPU %]

![Elasticsearch elabora CPU](../../assets/tools/elasticsearch-process-cpu.jpg)

Il frame **[!UICONTROL Elasticsearch process CPU %]** mostra la percentuale di CPU del processo [!DNL Elasticsearch] nel periodo di tempo selezionato.

## [!UICONTROL Elasticsearch Memory garbage collection]

![Garbage di memoria Elasticsearch](../../assets/tools/elasticsearch-memory-garbage.jpg)

[!DNL Elasticsearch] è un processo Java. Se la memoria allocata è insufficiente, verrà avviata la raccolta di oggetti inattivi per liberare memoria. Se la raccolta di oggetti inattivi è frequente, è un’indicazione del fatto che potrebbero esserci troppi indici o frammenti per la memoria allocata. Potrebbe essere possibile pulire gli indici e le parti oppure [!DNL Elasticsearch] potrebbe richiedere più memoria.

## [!UICONTROL Elasticsearch Index information]

![Informazioni indice Elasticsearch](../../assets/tools/elasticsearch-index-information-2.jpg)

Quando gli indici vengono creati e aggiornati, lo stato dell’indice potrebbe cambiare.

## [!UICONTROL Elasticsearch Index Size]

![Dimensione indice Elasticsearch](../../assets/tools/elasticsearch-index-size.jpg)

Il frame **[!UICONTROL Elasticsearch Index Size]** indica il nome e la dimensione dell&#39;indice nell&#39;arco temporale selezionato. Potrebbe indicare problemi nel modo in cui un sito viene indicizzato.

## [!UICONTROL Elasticsearch Errors]

![Errori Elasticsearch](../../assets/tools/elasticsearch-tab-elasticsearch-errors.jpg)

Nel frame **[!UICONTROL Elasticsearch Errors]** vengono visualizzati errori con [!DNL Elasticsearch], ad esempio l&#39;esaurimento dello spazio, il passaggio dallo stato Giallo a Rosso, il mancato funzionamento di tutti i frammenti, problemi di parametri con ricerche, errori di versione e l&#39;indisponibilità di tutti i nodi.

## [!UICONTROL Elasticsearch Unassigned Shards]:

![Schede Elasticsearch non assegnate](../../assets/tools/elasticsearch-unassigned-shards.jpg)

Le parti non assegnate causeranno lo spostamento di un cluster dallo stato Verde allo stato Giallo.
