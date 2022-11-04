---
title: Procedure consigliate per la configurazione dei rapporti
description: Ottimizza le prestazioni del sito rimuovendo il modulo di reporting se non lo utilizzi.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Procedure consigliate per la configurazione dei rapporti

Se la tua azienda non richiede funzionalità di reporting o segmenti di clienti dinamici, disattiva la [Funzionalità dei rapporti](https://docs.magento.com/user-guide/configuration/general/reports.html) per migliorare le prestazioni dello store.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce su infrastruttura cloud
- Adobe Commerce on-premise

## Disattiva reporting

Se non utilizzi i rapporti o i segmenti dinamici dei clienti, disattiva la funzionalità Rapporti .

1. Dall’amministratore, passa a **Negozi** > **Impostazioni** > **Configurazione** > **Generale** > **Rapporti**.
1. Sotto **Opzioni generali**, set **Abilita rapporti** a *No*.
1. Svuotare la cache eseguendo `php bin/magento cache:flush` o nell’Admin in **Sistema** > **Strumenti** > **Gestione cache**.

## Informazioni aggiuntive

- [Generare report in Adobe Commerce](https://docs.magento.com/user-guide/reports.html)
- [Segmenti dinamici dei clienti](https://docs.magento.com/user-guide/marketing/customer-segments.html)
