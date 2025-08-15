---
title: Best practice per la configurazione di siti, store e visualizzazioni dello store
description: Scopri le best practice per la configurazione di siti, store e visualizzazioni dello store per massimizzare le prestazioni del sito.
role: Admin
feature: Best Practices
exl-id: 3ea0c6c5-15a9-4e77-b4d0-ce15721c7167
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Procedure consigliate per la configurazione di siti, archivi e visualizzazione archivio

Per Adobe Commerce sull’infrastruttura cloud, le best practice si applicano in modo specifico all’ambiente di produzione (e possibilmente all’architettura di staging su Pro, soggetta a vincoli di risorse) che avrebbe più risorse degli ambienti di integrazione e sviluppo.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

## Strategie per migliorare le prestazioni

Se il progetto richiede più siti, store o visualizzazioni dello store, puoi utilizzare le seguenti strategie per migliorare le prestazioni:

- Ristrutturare il catalogo spostando la logica nelle categorie
- Separare i listini prezzi dai dati del catalogo utilizzando un prezzo esterno e un sistema di gestione dei prezzi (PMS).
- Utilizzare un’archiviazione dati noSQL alternativa come Elasticsearch

## Potenziali impatti sulle prestazioni

I siti Web e i negozi sono moltiplicatori per i dati di catalogo, pertanto la presenza di numerosi siti Web e negozi può influire negativamente sulle prestazioni del sito nei seguenti modi:

- Le tabelle indice più grandi aumentano il tempo necessario per completare le operazioni di indicizzazione [Indice prezzo].
- L&#39;aumento del tempo di recupero della configurazione dell&#39;applicazione riduce il tempo di risposta della vetrina per le pagine di catalogo non memorizzate nella cache.
- Aumenta in modo significativo il tempo necessario per completare le operazioni di salvataggio nell’amministratore, in quanto i dati vengono salvati separatamente per ciascun sito web.


## Informazioni aggiuntive

- [Informazioni su siti Web, archivi e visualizzazioni dello store](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/configure-store/best-practices)
- [Configurazione di più siti Web o store](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites)
