---
title: Passaggi per la migrazione dei post-dati
description: Scopri quali passi intraprendere dopo l’utilizzo del [!DNL Data Migration Tool] migrare i dati dal Magento 1 al Magento 2.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '74'
ht-degree: 0%

---


# Passaggi per la migrazione dei post-dati

Dopo aver completato la migrazione e aver verificato accuratamente il nuovo sito Magento 2, esegui le seguenti attività:

* Metti il Magento 1 in modalità di manutenzione e interrompi definitivamente tutte le attività di amministrazione

* Avvia lavori cron Magento 2

* [Svuotare tutti i tipi di cache Magento 2](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [Reindicizza tutti gli indici del Magento 2](../../../configuration/cli/manage-indexers.md#reindex)

* Cambiare DNS e bilanciatori di carico per puntare all&#39;hardware di produzione di Magento 2
