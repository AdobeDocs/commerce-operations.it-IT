---
title: Ottimizzare le immagini per un sito più reattivo
description: Scopri i passaggi per ottimizzare le immagini e utilizzare l’ottimizzazione di immagini finali per ottimizzare il tempo di risposta sui tuoi siti Adobe Commerce.
role: Developer, Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: e156fcafc5792036b37d9b199b870f1888c3f1ff
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Ottimizzare le immagini per un sito più reattivo

Per Adobe Commerce sulle implementazioni di infrastrutture cloud, migliora il tempo di risposta del sito ottimizzando le immagini prima di caricarle. Quindi, utilizza l&#39;ottimizzazione Flast image per velocizzare la distribuzione delle immagini e semplificare la manutenzione dei set di immagini sorgente.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

Adobe Commerce su infrastruttura cloud


## Ottimizzare e comprimere le immagini

Prima di caricare le immagini sui siti Commerce, ottimizzale e comprimili per bilanciare le prestazioni con la qualità di visualizzazione. Questo consente di aumentare lo spazio e di ridurre i tempi di caricamento delle pagine.

- Il formato PNG offre immagini di dimensioni più piccole per immagini con grandi aree di colore solido.

- Il formato JPEG offre immagini di dimensioni più ridotte per tutti gli altri tipi di immagini. Utilizzare la compressione più elevata (senza degrado notevole). Di solito è dal 60 all&#39;80%.

## Abilita e configura l&#39;ottimizzazione di immagini finali

Dopo aver configurato il servizio Flast per il progetto Adobe Commerce Cloud, consulta [Ottimizzazione delle immagini](https://devdocs.magento.com/cloud/cdn/fastly-image-optimization.html) per istruzioni su come abilitare e configurare l’ottimizzazione delle immagini.

## Informazioni aggiuntive

- [Imposta in modo rapido](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
- [Le immagini scarsamente ottimizzate possono causare problemi di prestazioni](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html)
