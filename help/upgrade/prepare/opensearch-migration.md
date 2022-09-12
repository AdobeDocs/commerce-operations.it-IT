---
title: Migrazione da Elasticsearch a OpenSearch
description: Scopri come sostituire il motore di ricerca utilizzato per le installazioni on-premise di Adobe Commerce e Magenti Open Source.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 0%

---


# Migrazione a OpenSearch

OpenSearch è un fork open source di Elasticsearch 7.10.2 creato dopo la modifica delle licenze di Elasticsearch.

A partire dalla versione 2.4.4, 2.4.3-p2 e 2.3.7-p3, Adobe Commerce e Magenti Open Source supportano OpenSearch. Le installazioni on-premise continuano a supportare l’Elasticsearch, anche se non è più supportato per Adobe Commerce su infrastruttura cloud.

## Percorso di migrazione

I passaggi da eseguire per la migrazione a OpenSearch sono semplici e in gran parte seguono i passaggi per la configurazione di Elasticsearch. Questi passaggi presuppongono che Adobe Commerce sia l’unica applicazione che utilizza il motore di ricerca. Nei casi in cui più applicazioni utilizzano il motore di ricerca, segui la guida ufficiale alla migrazione [Passaggio dall’Elasticsearch open source a OpenSearch](https://opensearch.org/blog/technical-posts/2021/10/moving-from-opensource-elasticsearch-to-opensearch/).

1. Assicurati che l&#39;installazione rispetti le [prerequisiti per i motori di ricerca](../../installation/prerequisites/search-engine/overview.md).

1. Posiziona il sito in [Modalità di manutenzione](../../installation/tutorials/maintenance-mode.md).

1. È possibile disinstallare Elasticsearch.

1. [Installa OpenSearch](https://opensearch.org/docs/latest/opensearch/install/important-settings/).

1. [Configurare il motore di ricerca](../../configuration/search/configure-search-engine.md) ed esegui le attività correlate, ad esempio scaricando la cache e reindicizzando l&#39;indice di ricerca del catalogo.

Non sono necessarie ulteriori modifiche al valore di configurazione.
