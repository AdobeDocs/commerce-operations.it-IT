---
title: Passaggi di migrazione dei dati Post
description: Scopri come procedere dopo aver utilizzato  [!DNL Data Migration Tool]  per migrare i dati dal Magento 1 al Magento 2.
exl-id: 00171c41-ccea-4ebe-8958-becb9aa09973
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---

# Passaggi di migrazione dei dati Post

Dopo aver completato la migrazione e testato in modo approfondito il nuovo sito Magento 2, eseguire le operazioni seguenti:

* Metti il Magento 1 in modalità di manutenzione e interrompi definitivamente tutte le attività di amministrazione

* Avvia processi cron Magento 2

* [Svuota tutti i tipi di cache del Magento 2](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [Reindicizza tutti gli indicizzatori del Magento 2](../../../configuration/cli/manage-indexers.md#reindex)

* Modificare il DNS e i load balancer per puntare all&#39;hardware di produzione del Magento 2
