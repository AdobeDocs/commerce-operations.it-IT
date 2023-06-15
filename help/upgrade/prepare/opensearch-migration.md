---
title: Migrare da Elasticsearch a OpenSearch
description: Scopri come sostituire il motore di ricerca utilizzato per le installazioni locali di Adobe Commerce e Magenti Open Source.
feature: Upgrade, Search
exl-id: 56f1e609-83d2-4705-99d8-b395bb511411
source-git-commit: 012cba58b336b032b1c911539008c1fb961c2e07
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---

# Migrazione a OpenSearch

OpenSearch è un fork open source di Elasticsearch 7.10.2 creato dopo la modifica della licenza di Elasticsearch.

A partire da 2.4.4, 2.4.3-p2 e 2.3.7-p3, Adobe Commerce e il Magento Open Source supportano OpenSearch. Le installazioni on-premise continuano a supportare Elasticsearch, anche se non è più supportato per Adobe Commerce sull’infrastruttura cloud. A partire dalla versione 2.4.6, OpenSearch dispone di un proprio modulo e di campi nelle impostazioni di configurazione dell’amministratore.

## Percorso di migrazione

I passaggi per migrare a OpenSearch sono semplici e seguono in gran parte i passaggi per Elasticsearch la configurazione. Questi passaggi presuppongono che Adobe Commerce sia l’unica applicazione che utilizza il motore di ricerca. Se il motore di ricerca viene utilizzato da più applicazioni, seguire la guida ufficiale alla migrazione [Passaggio dall&#39;Elasticsearch open source a OpenSearch](https://opensearch.org/blog/technical-posts/2021/10/moving-from-opensource-elasticsearch-to-opensearch/).

1. Assicurarsi che l&#39;installazione soddisfi i [prerequisiti per i motori di ricerca](../../installation/prerequisites/search-engine/overview.md).

1. Inserisci il sito in [Modalità manutenzione](../../installation/tutorials/maintenance-mode.md).

1. È possibile disinstallare Elasticsearch.

1. [Installa OpenSearch](https://opensearch.org/docs/latest/opensearch/install/important-settings/).

1. [Configurare il motore di ricerca](../../configuration/search/configure-search-engine.md) ed eseguire attività correlate, come lo scaricamento della cache e la reindicizzazione dell’indice di ricerca del catalogo.

Non sono necessarie ulteriori modifiche al valore di configurazione.
