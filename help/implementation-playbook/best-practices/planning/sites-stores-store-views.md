---
title: Procedure consigliate per la configurazione di siti, store e viste store
description: Scopri le best practice per la configurazione di siti, store e viste Store per massimizzare le prestazioni del sito.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Procedure consigliate per la configurazione di siti, archivi e viste Store

Per ottenere le migliori prestazioni del sito, configura un massimo di 50 siti, 50 store e 50 viste store per Adobe Commerce su progetti di infrastruttura cloud.

>[!NOTE]
>
>Per Adobe Commerce sull’infrastruttura cloud, le best practice si applicano in modo specifico all’ambiente di produzione (e possibilmente all’architettura Pro, soggetta a vincoli di risorse), che disporrebbe di più risorse rispetto agli ambienti di integrazione e sviluppo. Per gli ambienti di integrazione (Pro e Starter) e Staging (Starter), riduci il numero di visualizzazioni dello store a meno di 5 o 10 (soggetto a revisione tecnica).

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce su infrastruttura cloud
- Adobe Commerce on-premise

## Strategie per migliorare le prestazioni

Se il progetto richiede diverse viste sito, store o store, puoi utilizzare le seguenti strategie per migliorare le prestazioni:

- Ristrutturare il catalogo spostando la logica in categorie
- Separare i listini prezzi dai dati del catalogo utilizzando i prezzi esterni e un sistema di gestione dei prezzi (PMS).
- Utilizzare un archivio dati noSQL alternativo, ad Elasticsearch

## Effetti potenziali sulle prestazioni

I siti web e gli archivi sono moltiplicatori per i dati di catalogo, pertanto avere molti siti web e negozi può influire negativamente sulle prestazioni del sito nei seguenti modi:

- Tabelle indice più grandi aumentano il tempo necessario per completare le operazioni di indicizzazione [Indice dei prezzi].
- Il tempo aumentato per recuperare la configurazione dell&#39;applicazione riduce il tempo di risposta della vetrina per le pagine di catalogo non memorizzate nella cache.
- Incremento significativo del tempo necessario per completare le operazioni di salvataggio nell’amministratore, in quanto i dati vengono salvati separatamente per ciascun sito web.


## Informazioni aggiuntive

- [Informazioni su siti web, store e viste store](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [Configurazione di più siti web o negozi](https://devdocs.magento.com/cloud/project/project-multi-sites.html)

