---
title: Passaggi di migrazione post-dati
description: Scopri come eseguire la migrazione dei dati da Magento 1 a Magento 2 dopo l'utilizzo di  [!DNL Data Migration Tool] .
exl-id: 00171c41-ccea-4ebe-8958-becb9aa09973
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---

# Passaggi di migrazione post-dati

Dopo aver completato la migrazione e testato in modo approfondito il nuovo sito Magento 2, eseguire le attività seguenti:

* Metti Magento 1 in modalità di manutenzione e interrompi definitivamente tutte le attività di amministrazione

* Avvia processi cron di Magento 2

* [Svuota tutti i tipi di cache di Magento 2](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [Reindicizza tutti gli indicizzatori di Magento 2](../../../configuration/cli/manage-indexers.md#reindex)

* Modificare il DNS e i load balancer in modo che puntino all&#39;hardware di produzione Magento 2
