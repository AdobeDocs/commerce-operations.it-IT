---
title: Procedure consigliate per la configurazione dei rapporti
description: Ottimizza le prestazioni del sito rimuovendo il modulo di reporting se non lo utilizzi.
role: Admin
feature: Best Practices, Configuration
exl-id: 8c991b8a-affb-4a9e-9383-671f595ff89e
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 1%

---

# Procedure consigliate per la configurazione dei rapporti

Se la tua azienda non richiede la funzionalità di reporting o segmenti cliente dinamici, disabilita la funzionalità [Rapporti](https://experienceleague.adobe.com/it/docs/commerce-admin/config/general/reports) per migliorare le prestazioni dello store.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

## Disattiva reporting

Se non utilizzi i segmenti Reports o clienti dinamici, disabilita la funzionalità Reports.

1. Dall&#39;amministratore, passare a **Archivi** > **Impostazioni** > **Configurazione** > **Generale** > **Rapporti**.
1. In **Opzioni generali**, impostare **Abilita report** su *No*.
1. Svuota la cache eseguendo `php bin/magento cache:flush` o nell&#39;amministratore in **Sistema** > **Strumenti** > **Gestione cache**.

## Informazioni aggiuntive

- [Genera report in Adobe Commerce](https://experienceleague.adobe.com/it/docs/commerce-admin/start/reporting/reports-menu)
- [Segmenti dinamici del cliente](https://experienceleague.adobe.com/it/docs/commerce-admin/customers/segments/customer-segments)
