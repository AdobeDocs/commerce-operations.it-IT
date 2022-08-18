---
title: '"Il [!UICONTROL Infra] scheda"'
description: La [!UICONTROL Infra] La scheda isola i problemi e le cause dei problemi dell'infrastruttura.
source-git-commit: b0d80d97f60b24bc801063dc484f3a495cf0a036
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---


# La [!UICONTROL Infra] scheda

La **[!UICONTROL Infra]** La scheda isola i problemi e le cause dei problemi dell&#39;infrastruttura. Vengono inoltre descritti i fotogrammi che è possibile visualizzare nella scheda .

## [!UICONTROL Service Alerts – Infrastructure Alerts by Application name]

![Avvisi di servizio](../../assets/tools/observation-for-adobe-commerce/service-alerts.jpg)

La **[!UICONTROL Service Alerts – Infrastructure Alerts by Application name]** il grafico mostra gli avvisi del servizio raccolti da [!DNL New Relic] agente dell&#39;infrastruttura. Verranno visualizzati i riavvii del servizio, molti dei quali associati alle distribuzioni.

## [!UICONTROL Inode usage by mount]

![Utilizzo nodo per montaggio](../../assets/tools/observation-for-adobe-commerce/inode-usage-mount.jpg)

La **[!UICONTROL Inode usage by mount]** il frame mostra l&#39;utilizzo dell&#39;inodo in base al montaggio nell&#39;arco temporale selezionato. Anche se ci può essere un sacco di spazio libero di archiviazione, se un nodo esaurisce gli inodi, mostrerà una mancanza di spazio di archiviazione disponibile. La rimozione dei file (soprattutto di quelli piccoli) libererà spazio e renderà disponibili i nodi.

## [!UICONTROL vCPU tier view over timeline GREATER 2 weeks]

![Visualizzazione a livello di CPU sulla timeline MAGGIORE di 2 settimane](../../assets/tools/observation-for-adobe-commerce/vCPU-tier.jpg)

La **[!UICONTROL vCPU tier view over timeline GREATER 2 weeks]** frame mostra la visualizzazione del livello vCPU nell&#39;arco temporale selezionato di più di due settimane. Questo frame esamina il numero di vCPU assegnate al [!DNL New Relic] nome dell&#39;applicazione visualizzato.

## [!UICONTROL vCPU tier view over timeline]

![Visualizzazione a livello di CPU sulla timeline](../../assets/tools/observation-for-adobe-commerce/vcpu-tier-24.jpg)

La **[!UICONTROL vCPU tier view over timeline]** frame mostra la visualizzazione del livello vCPU nell&#39;arco temporale selezionato di oltre 24 ore. Questo frame esamina il numero di vCPU assegnate al [!DNL New Relic] nome dell&#39;applicazione visualizzato. Mostrerà sia gli aggiornamenti che i download del cluster.

## [!UICONTROL vCPU tier view over timeline BY NODE]

![Visualizzazione a livello di CPU sulla timeline da NODE](../../assets/tools/observation-for-adobe-commerce/infra_by_node.png)

La **[!UICONTROL vCPU tier view over timeline BY NODE]** frame mostra le visualizzazioni a livello di vCPU nell’arco temporale selezionato per nodo. Questo frame è utile per rilevare la perdita di nodi o quando i nodi vengono ingranditi o ridimensionati. Visualizzazione del livello vCPU sulla timeline BY NODE, dovrebbe guardare la timeline meno di 24 ore.

## [!UICONTROL Instance details]

![Dettagli istanza](../../assets/tools/observation-for-adobe-commerce/instance-details.jpg)

La **[!UICONTROL Instance details]** la tabella mostra i dettagli dell’istanza di ogni [!DNL New Relic] applicazione.

## [!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]

![nodo non reattivo](../../assets/tools/observation-for-adobe-commerce/non-responsive-node.jpg)

La **[!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]** il frame mostra i nodi non reattivi in un periodo di tempo.
