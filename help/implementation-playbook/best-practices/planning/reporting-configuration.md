---
title: Procedure consigliate per la configurazione dei rapporti
description: Ottimizza le prestazioni del sito rimuovendo il modulo di reporting se non lo utilizzi.
role: Admin
feature: Best Practices, Configuration
exl-id: 8c991b8a-affb-4a9e-9383-671f595ff89e
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '148'
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

- [Generare rapporti in Adobe Commerce](https://experienceleague.adobe.com/it/docs/commerce-admin/start/reporting/reports-menu)
- [Segmenti dinamici del cliente](https://experienceleague.adobe.com/it/docs/commerce-admin/customers/segments/customer-segments)
