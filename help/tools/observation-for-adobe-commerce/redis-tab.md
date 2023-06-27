---
title: Il [!UICONTROL Redis] scheda
description: Scopri di più su [!UICONTROL Redis] scheda di [!DNL Observation for Adobe Commerce].
exl-id: 9c52350d-45a7-4afe-9dd7-c3968bd84d71
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---

# Il [!DNL Redis] scheda

## [!UICONTROL Redis Node summary]

![Riepilogo nodo Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-1.jpg)

Il **[!UICONTROL Redis Node summary]** include tutti i nodi di un ambiente. L’esempio precedente include i nodi per la gestione temporanea condivisa. Ci sono un primario e due secondari sulla produzione e anche un primario e due secondari sulla staging.

## [!UICONTROL Redis node detail]

![Dettagli nodo Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-2.jpg)

Il **[!UICONTROL Redis node detail]** frame indica l&#39;ambiente, [!DNL Redis] ruolo, versione del software e dimensioni del nodo.

## [!UICONTROL Redis node roles timeline]

![Timeline dei ruoli dei nodi Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-3.jpg)

Il **[!UICONTROL Redis node roles timeline]** il frame indica la perdita di [!DNL Redis] servizio in ruoli particolari. Se una linea si abbassa, indica che il ruolo particolare rappresentato dalla linea ha perso uno o più nodi.

## [!UICONTROL Connection to Redis]

![Connessione a Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-4.jpg)

Il **[!UICONTROL Connection to Redis]** frame visualizza il valore net.connectedClients dal [!DNL New Relic Redis] dati di esempio. Visualizza il conteggio delle connessioni per [!DNL New Relic] applicazione (ambiente) e nodo.

## [!UICONTROL Commands per second by node]

![Comandi al secondo per nodo](../../assets/tools/observation-for-adobe-commerce/redis-tab-5.jpg)

Il **[!UICONTROL Commands per second by node]** il frame mostra il [!DNL Redis] comandi per nodo al secondo nell&#39;intervallo di tempo selezionato.

## [!UICONTROL Redis % of memory used]

![Redis % della memoria utilizzata](../../assets/tools/observation-for-adobe-commerce/redis-tab-6.jpg)

Il **[!UICONTROL Redis % of memory used]** mostra la percentuale di memoria massima utilizzata dal [!DNL Redis] server.

## [!UICONTROL Redis used memory]

![Memoria Redis utilizzata](../../assets/tools/observation-for-adobe-commerce/redis-tab-7.jpg)

Il **[!UICONTROL Redis used memory]** frame mostra l&#39;utilizzo della memoria del nodo in GB/MB.

## [!UICONTROL Redis changes since last db save]

![Redis modifiche dall&#39;ultimo salvataggio del database](../../assets/tools/observation-for-adobe-commerce/redis-tab-8.jpg)

[!DNL Redis] è residente in memoria e salva le informazioni nell&#39;archivio. Il **[!UICONTROL Redis changes since last db save]** frame indica il numero di modifiche apportate alla memoria dall&#39;ultimo salvataggio del database nell&#39;archivio. Fai riferimento a [Persistenza Redis](https://redis.io/docs/manual/persistence/) per ulteriori informazioni su [!DNL Redis's] persistenza.

## [!UICONTROL Redis synchronization from Log]

![Sincronizzazione Redis dal registro](../../assets/tools/observation-for-adobe-commerce/redis-tab-9.jpg)

Il **[!UICONTROL Redis synchronization from Log]** il frame è incentrato sugli errori riscontrati durante [!DNL Redis] sincronizzazione o errori dovuti a problemi di sincronizzazione. Per ulteriori informazioni su [!DNL Redis], fare riferimento a [[!DNL Redis] Documentazione](https://redis.io/docs/).
