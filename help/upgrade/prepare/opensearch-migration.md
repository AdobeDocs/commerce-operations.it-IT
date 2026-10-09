---
title: Migrazione da Elasticsearch a OpenSearch
description: Scopri come sostituire il motore di ricerca utilizzato per le installazioni locali di Adobe Commerce.
feature: Upgrade, Search
exl-id: 56f1e609-83d2-4705-99d8-b395bb511411
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '201'
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
