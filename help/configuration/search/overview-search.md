---
title: Panoramica del motore di ricerca
description: Panoramica delle opzioni del motore di ricerca per Adobe Commerce e Magenti Open Source.
source-git-commit: 52c472bf80942339b511292243b5da9babf829d9
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---


# Panoramica del motore di ricerca

A partire dalla versione 2.4.4, Adobe Commerce e Magenti Open Source richiedono [Elasticsearch] o [OpenSearch] essere il motore di ricerca del catalogo. Elasticsearch necessario per le versioni precedenti di 2.4.x . Per informazioni sull’installazione di un motore di ricerca e sulla configurazione iniziale, consulta i seguenti argomenti:

- [Prerequisiti per i motori di ricerca]
- [Configurare l’allegato per il motore di ricerca]
- [Configurare Apache per il motore di ricerca]
- [Installare il software Commerce] (interfaccia a riga di comando)

Dopo aver installato e integrato il motore di ricerca con Adobe Commerce, devi eseguire una manutenzione aggiuntiva:

- [Configurare le parole chiave di ricerca](search-stopwords.md)
- [Configurazione del motore di ricerca](configure-search-engine.md)

<!-- Link Definitions -->

[Prerequisiti per i motori di ricerca]: https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html
[Configurare l’allegato per il motore di ricerca]: https://devdocs.magento.com/guides/v2.4/install-gde/prereq/es-config-nginx.html
[Configurare Apache per il motore di ricerca]: https://devdocs.magento.com/guides/v2.4/install-gde/prereq/es-config-apache.html
[Elasticsearch]: https://www.elastic.co
[Elasticsearch documentation]: https://www.elastic.co/guide/en/elasticsearch/reference/current/index.html
[Installare il software Commerce]: https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-install.html
[OpenSearch]: https://opensearch.org/docs/latest/opensearch/install/index/
