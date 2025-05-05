---
title: Ottimizzare le immagini per un sito più reattivo
description: Scopri i passaggi per ottimizzare le immagini e utilizzare l’ottimizzazione Fastly per ottimizzare i tempi di risposta sui siti Adobe Commerce.
role: Developer, Admin
feature: Best Practices
exl-id: ada8b987-97ed-4232-9e1b-7e0a791a0807
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 1%

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

Dopo aver configurato il servizio Fastly per il progetto Adobe Commerce Cloud, vedere [Ottimizzazione immagine Fastly](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/cdn/fastly-image-optimization) per istruzioni su come abilitare e configurare l&#39;ottimizzazione immagine.

## Informazioni aggiuntive

- [Configurazione rapida](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration)
- [Immagini non ottimizzate correttamente possono causare problemi di prestazioni](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html?lang=it)
