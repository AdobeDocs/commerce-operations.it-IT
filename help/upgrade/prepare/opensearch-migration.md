---
title: Migrazione da Elasticsearch a OpenSearch
description: Scopri come sostituire il motore di ricerca utilizzato per le installazioni locali di Adobe Commerce.
feature: Upgrade, Search
exl-id: 56f1e609-83d2-4705-99d8-b395bb511411
source-git-commit: 54aef3d7db7b8333721fb56db0ba8f098aea030b
workflow-type: tm+mt
source-wordcount: '185'
ht-degree: 0%

---

# Migrazione a OpenSearch

OpenSearch è un fork open source di Elasticsearch 7.10.2 creato dopo la modifica delle licenze di Elasticsearch.

A partire dalle versioni 2.4.4, 2.4.3-p2 e 2.3.7-p3, Adobe Commerce supporta OpenSearch. Le installazioni on-premise continuano a supportare Elasticsearch, anche se non è più supportato per Adobe Commerce sull’infrastruttura cloud. A partire dalla versione 2.4.6, OpenSearch dispone di un proprio modulo e di campi nelle impostazioni di configurazione dell’amministratore.

## Percorso di migrazione

I passaggi per migrare a OpenSearch sono semplici e seguono in gran parte i passaggi per la configurazione di Elasticsearch. Questi passaggi presuppongono che Adobe Commerce sia l’unica applicazione che utilizza il motore di ricerca. Nei casi in cui più applicazioni utilizzano il motore di ricerca, seguire la guida ufficiale alla migrazione [Passaggio da Elasticsearch open source a OpenSearch](https://opensearch.org/blog/moving-from-opensource-elasticsearch-to-opensearch/).

1. Assicurati che l&#39;installazione soddisfi i [prerequisiti del motore di ricerca](../../installation/prerequisites/search-engine/overview.md).

1. Posiziona il sito in [Modalità manutenzione](../../installation/tutorials/maintenance-mode.md).

1. Facoltativamente, disinstalla Elasticsearch.

1. [Installa OpenSearch](https://opensearch.org/docs/latest/opensearch/install/important-settings/).

1. [Configurare il motore di ricerca](../../configuration/search/configure-search-engine.md) ed eseguire le attività correlate, ad esempio svuotare la cache e reindicizzare l&#39;indice di ricerca del catalogo.

Non sono necessarie ulteriori modifiche al valore di configurazione.
