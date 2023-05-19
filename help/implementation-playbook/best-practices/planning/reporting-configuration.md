---
title: Procedure consigliate per la configurazione dei rapporti
description: Ottimizza le prestazioni del sito rimuovendo il modulo di reporting se non lo utilizzi.
role: Admin
feature: Best Practices
feature-set: Commerce
exl-id: 8c991b8a-affb-4a9e-9383-671f595ff89e
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---

# Procedure consigliate per la configurazione dei rapporti

Se la tua azienda non richiede la funzionalità di reporting o di segmenti dinamici dei clienti, disabilita [Funzionalità di reporting](https://docs.magento.com/user-guide/configuration/general/reports.html) per migliorare le prestazioni dello store.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

## Disattiva reporting

Se non utilizzi i segmenti Reports o clienti dinamici, disabilita la funzionalità Reports.

1. Dall’amministratore, passa a **Negozi** > **Impostazioni** > **Configurazione** > **Generale** > **Rapporti**.
1. Sotto **Opzioni generali**, impostato **Abilita rapporti** a *No*.
1. Svuota la cache eseguendo `php bin/magento cache:flush` o nell’Admin in **Sistema** > **Strumenti** > **Gestione cache**.

## Informazioni aggiuntive

- [Generare rapporti in Adobe Commerce](https://docs.magento.com/user-guide/reports.html)
- [Segmenti dinamici del cliente](https://docs.magento.com/user-guide/marketing/customer-segments.html)
