---
title: Ottimizzare le immagini per un sito più reattivo
description: Scopri i passaggi per ottimizzare le immagini e utilizzare l’ottimizzazione Fastly per ottimizzare i tempi di risposta sui siti Adobe Commerce.
role: Developer, Admin
feature: Best Practices
exl-id: ada8b987-97ed-4232-9e1b-7e0a791a0807
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%
---
# Ottimizzare le immagini per un sito più reattivo

Per le distribuzioni dell’infrastruttura cloud di Adobe Commerce, migliora i tempi di risposta del sito ottimizzando le immagini prima di caricarle. Quindi, utilizza l’ottimizzazione delle immagini Fastly per velocizzare la consegna delle immagini e semplificare la manutenzione dei set di sorgenti delle immagini.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

Adobe Commerce sull’infrastruttura cloud


## Ottimizzare e comprimere le immagini

Prima di caricare le immagini nei siti Commerce, ottimizzale e comprimi per bilanciare le prestazioni con la qualità di visualizzazione. Questo consente di aumentare lo spazio e ridurre i tempi di caricamento delle pagine.

- Il formato PNG offre immagini di dimensioni ridotte per le immagini con grandi aree di colore a tinta unita.

- Il formato JPEG offre immagini di dimensioni ridotte per tutti gli altri tipi di immagini. Utilizza la compressione più elevata (senza degradazioni evidenti). Di solito è tra il 60 e l&#39;80%.

## Abilitare e configurare l’ottimizzazione Fastly delle immagini

Dopo aver configurato il servizio Fastly per il progetto Adobe Commerce Cloud, consulta [Ottimizzazione immagine Fastly](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/fastly-image-optimization) per le istruzioni su come abilitare e configurare l&#39;ottimizzazione immagine.

## Informazioni aggiuntive

- [Configura Fastly](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/cdn/setup-fastly/fastly-configuration)
- [Immagini scarsamente ottimizzate possono causare problemi di prestazioni](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow)
