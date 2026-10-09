---
title: Passaggi di migrazione post-dati
description: Scopri i passaggi da eseguire dopo aver utilizzato [!DNL Data Migration Tool] per migrare i dati da Magento 1 a Magento 2.
exl-id: 00171c41-ccea-4ebe-8958-becb9aa09973
topic: Commerce, Migration
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '84'
ht-degree: 0%
---
# Passaggi di migrazione post-dati

Dopo aver completato la migrazione e testato accuratamente il nuovo sito Magento 2, esegui le seguenti attività:

* Metti Magento 1 in modalità di manutenzione e interrompi definitivamente tutte le attività di amministrazione

* Avvia processi cron di Magento 2

* [Svuota tutti i tipi di cache di Magento 2](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [Reindicizza tutti gli indicizzatori di Magento 2](../../../configuration/cli/manage-indexers.md#reindex)

* Modifica il DNS e i load balancer per puntare all’hardware di produzione Magento 2
