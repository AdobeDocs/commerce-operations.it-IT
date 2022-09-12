---
title: Passaggi per la migrazione dei post-dati
description: Scopri quali passi intraprendere dopo l’utilizzo del [!DNL Data Migration Tool] migrare i dati dal Magento 1 al Magento 2.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '77'
ht-degree: 0%

---


# Passaggi per la migrazione dei post-dati

Dopo aver completato la migrazione e aver verificato accuratamente il nuovo sito Magento 2, esegui le seguenti attività:

* Mettere il Magento 1 in modalità di manutenzione e arrestare definitivamente tutti [Amministratore](https://glossary.magento.com/admin) attività

* Avvia lavori cron Magento 2

* [Svuotare tutti i tipi di cache Magento 2](../../../configuration/cli/manage-cache.md#clean-and-flush-cache-types)

* [Reindicizza tutti gli indici del Magento 2](../../../configuration/cli/manage-indexers.md#reindex)

* Cambiare DNS e bilanciatori di carico per puntare all&#39;hardware di produzione di Magento 2
