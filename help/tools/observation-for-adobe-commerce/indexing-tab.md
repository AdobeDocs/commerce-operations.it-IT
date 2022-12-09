---
title: "Il [!UICONTROL Indexing] scheda"
description: Scopri le [!UICONTROL Indexing] scheda di [!DNL Observation for Adobe Commerce].
source-git-commit: e6038d6f0add9d01d650914b35a1daba885fa7f8
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# La [!UICONTROL Indexing] scheda

La **[!UICONTROL Indexing]** tab tenta di spiegare i problemi relativi all’indicizzazione e di identificare le potenziali cause.

## [!UICONTROL Core index invalidated]

![Indice di base non convalidato](../../assets/tools/observation-for-adobe-commerce/indexing-tab-1.jpg)

La **[!UICONTROL Core index invalidated]** esamina l’invalidazione dell’indicizzazione in un arco temporale selezionato. Se l’indicizzazione si verifica contemporaneamente ad altre risorse intensive [!DNL crons], le risorse del sito saranno soggette a un carico pesante.

* `%Catalog Product Rule indexer has been invalidated%`) come `catalog_product_rule_idx_reset`
* `%Catalog Rule Product indexer has been invalidated%`) come `catalog_rule_product_idx_reset`
* `%Catalog Search indexer has been invalidated%`) come `catalog_search_idx_reset`
* `%Category Products indexer has been invalidated%`) come `category_products_idx_reset`
* `%Customer Grid indexer has been invalidated%`) come `customer_grid_idx_reset`
* `%Design Config Grid indexer has been invalidated%`) come `design_config_grid_idx_`
* `%Product Categories indexer has been invalidated%`) come `product_categories_idx_reset`
* `%Product EAV indexer has been invalidated%`) come `product_eav_idx_reset`
* `%Product Price indexer has been invalidated%`) come `product_price_idx_reset`
* `%Stock indexer has been invalidated%`) come `stock_idx_reset`
* `%Inventory indexer has been invalidated%`) come `inventory_idx_reset`
* `%Inventory indexer has been invalidated%`) come `inventory_idx_reset`
* `%Sales Rule indexer has been invalidated%`) come `sales_rule_idx_reset`

## [!UICONTROL Core index rebuilds]

![Ricostruzioni dell&#39;indice di base](../../assets/tools/observation-for-adobe-commerce/indexing-tab-2.jpg)

La **[!UICONTROL Core index rebuilds]** frame esamina le ricostruzioni dell&#39;indice di base in un arco temporale selezionato. Di seguito sono riportate le stringhe analizzate dai log per indicare il completamento della ricostruzione dell&#39;indice.

* `%Catalog Product Rule index has been rebuilt%`) come `catalog_product_rule_idx`
* `%Catalog Rule Product index has been rebuilt%`) come `catalog_rule_product_idx`
* `%Catalog Search index has been rebuilt%`) come `catalog_search_idx`
* `%Category Products index has been rebuilt successfully%`) come `category_products_idx`
* `%Customer Grid index has been rebuilt%`) come `customer_grid_idx`
* `%Design Config Grid index has been rebuilt%`) come `design_config_grid_idx`
* `%Product Categories index has been rebuilt%`) come `product_categories_idx`
* `%Product EAV index has been rebuilt%`) come `product_eav_idx`
* `%Product Price index has been rebuilt%`) come `product_price_idx`
* `%Stock index has been rebuilt%`) come `stock_idx`
* `%Inventory index has been rebuilt successfully%`) come `inventory_idx`
* `%Product/Target Rule index has been rebuilt successfully%`) come `prod_target_rule_idx`
* `%Sales Rule index has been rebuilt successfully%`) come `sales_rule_idx`


## [!UICONTROL catalogsearch index table(s)]

![tabella/e dell’indice/i di catalogsearch](../../assets/tools/observation-for-adobe-commerce/indexing-tab-3.jpg)

La **[!UICONTROL catalogsearch index table(s)]** frame esamina le tabelle dell&#39;indice di ricerca catalogica in un arco temporale selezionato. Questa query sta esaminando la durata di qualsiasi operazione del datastore a fronte di tabelle con `%catalogsearch%` nel nome della tabella.

## [!UICONTROL product index table(s)]

![tabella(e) dell&#39;indice(i) del prodotto](../../assets/tools/observation-for-adobe-commerce/indexing-tab-4.jpg)

La **[!UICONTROL product index table(s)]** frame esamina le tabelle dell&#39;indice del prodotto in un arco temporale selezionato. Questa query sta esaminando la durata di qualsiasi operazione del datastore a fronte di tabelle con `%product%` nel nome della tabella.
