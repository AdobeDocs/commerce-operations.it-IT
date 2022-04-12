---
title: Migrazione da Elasticsearch a OpenSearch
description: Scopri come sostituire il motore di ricerca utilizzato per le installazioni on-premise di Adobe Commerce e Magenti Open Source.
source-git-commit: 8007ff2e77689ec2058a326924dc34b8d91ee570
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---


# Migrazione a OpenSearch

OpenSearch è un fork open source di Elasticsearch 7.10.2 creato dopo la modifica delle licenze di Elasticsearch.

A partire dalla versione 2.4.4, 2.4.3-p2 e 2.3.7-p3, Adobe Commerce e Magenti Open Source supportano OpenSearch. Le installazioni on-premise continuano a supportare l’Elasticsearch, anche se non è più supportato per Adobe Commerce su infrastruttura cloud.

## Percorso di migrazione

I passaggi da eseguire per la migrazione a OpenSearch sono semplici e in gran parte seguono i passaggi per la configurazione di Elasticsearch. Questi passaggi presuppongono che Adobe Commerce sia l’unica applicazione che utilizza il motore di ricerca. Nei casi in cui più applicazioni utilizzano il motore di ricerca, segui la guida ufficiale alla migrazione [Passaggio dall’Elasticsearch open source a OpenSearch](https://opensearch.org/blog/technical-posts/2021/10/moving-from-opensource-elasticsearch-to-opensearch/).

1. Assicurati che l&#39;installazione rispetti le [prerequisiti per i motori di ricerca](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html).

1. Posiziona il sito in [Modalità di manutenzione](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html).

1. È possibile disinstallare Elasticsearch.

1. [Installa OpenSearch](https://opensearch.org/docs/latest/opensearch/install/important-settings/).

1. [Configurare il motore di ricerca](https://devdocs.magento.com/guides/v2.4/config-guide/elasticsearch/configure-magento.html) ed esegui le attività correlate, ad esempio scaricando la cache e reindicizzando l&#39;indice di ricerca del catalogo.

Non sono necessarie ulteriori modifiche al valore di configurazione.
