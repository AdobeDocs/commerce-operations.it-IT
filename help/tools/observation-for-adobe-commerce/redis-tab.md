---
title: '"Il [!UICONTROL Redis] scheda"'
description: Scopri le [!UICONTROL Redis] scheda di [!DNL Observation for Adobe Commerce].
source-git-commit: 3f2a401bb916fc04405f21ba2acfc42f7defdccb
workflow-type: tm+mt
source-wordcount: '237'
ht-degree: 0%

---

# La [!DNL Redis] scheda

## [!UICONTROL Redis Node summary]

![Riepilogo del nodo di Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-1.jpg)

La **[!UICONTROL Redis Node summary]** è comprensivo di tutti i nodi in un ambiente. Questo esempio include i nodi per la gestione temporanea condivisa. Vi è un primo e due secondari sulla produzione e anche un primario e due secondari sulla fase di staging.

## [!UICONTROL Redis node detail]

![Dettagli nodo Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-2.jpg)

La **[!UICONTROL Redis node detail]** frame indica l&#39;ambiente, [!DNL Redis] ruolo, versione software e dimensione del nodo.

## [!UICONTROL Redis node roles timeline]

![Timeline dei ruoli nodo di Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-3.jpg)

La **[!UICONTROL Redis node roles timeline]** frame indica la perdita di [!DNL Redis] in ruoli particolari. Se una riga scende, indica che il ruolo specifico rappresentato dalla riga ha perso uno o più nodi.

## [!UICONTROL Connection to Redis]

![Connessione a Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-4.jpg)

La **[!UICONTROL Connection to Redis]** frame visualizza il valore net.connectionClients dal [!DNL New Relic Redis] dati di esempio. Visualizza il conteggio delle connessioni per [!DNL New Relic] applicazione (ambiente) e nodo.

## [!UICONTROL Commands per second by node]

![Comandi al secondo per nodo](../../assets/tools/observation-for-adobe-commerce/redis-tab-5.jpg)

La **[!UICONTROL Commands per second by node]** la cornice mostra [!DNL Redis] comandi per nodo al secondo nell&#39;intervallo temporale selezionato.

## [!UICONTROL Redis % of memory used]

![Redis % della memoria utilizzata](../../assets/tools/observation-for-adobe-commerce/redis-tab-6.jpg)

La **[!UICONTROL Redis % of memory used]** il frame mostra la percentuale di memoria massima utilizzata dal [!DNL Redis] server.

## [!UICONTROL Redis used memory]

![Memoria utilizzata di Redis](../../assets/tools/observation-for-adobe-commerce/redis-tab-7.jpg)

La **[!UICONTROL Redis used memory]** frame mostra l&#39;utilizzo del nodo della memoria in GB/MB.

## [!UICONTROL Redis changes since last db save]

![Ripristina le modifiche dall&#39;ultimo salvataggio del db](../../assets/tools/observation-for-adobe-commerce/redis-tab-8.jpg)

[!DNL Redis] è una memoria residente e salva le informazioni in memoria. La **[!UICONTROL Redis changes since last db save]** frame indica il numero di modifiche apportate alla memoria che si sono verificate dopo il salvataggio dell&#39;ultimo database nell&#39;archivio. [Informazioni](https://redis.io/docs/manual/persistence/) spiega [!DNL Redis's] persistenza.

## [!UICONTROL Redis synchronization from Log]

![Sincronizzazione ridis dal log](../../assets/tools/observation-for-adobe-commerce/redis-tab-9.jpg)

La **[!UICONTROL Redis synchronization from Log]** frame si concentra sugli errori rilevati durante [!DNL Redis] sincronizzazione o errori dovuti a problemi di sincronizzazione. Vedi [Documentazione di Redis](https://redis.io/docs/).
