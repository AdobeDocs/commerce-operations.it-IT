---
title: Scheda [!UICONTROL Indexing]
description: Scopri la scheda [!UICONTROL Indexing] di [!DNL Observation for Adobe Commerce].
exl-id: c7e123b7-2d0c-49d4-9f76-128939dc02a8
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 0%

---

# Scheda [!UICONTROL Indexing]

La scheda **[!UICONTROL Indexing]** tenta di spiegare i problemi di indicizzazione e identificare le potenziali cause.

## [!UICONTROL Core index invalidated]

![Indice core invalidato](../../assets/tools/observation-for-adobe-commerce/indexing-tab-1.jpg)

Il frame **[!UICONTROL Core index invalidated]** esamina l&#39;invalidazione dell&#39;indicizzazione in un intervallo temporale selezionato. Se l&#39;indicizzazione si verifica contemporaneamente ad altri [!DNL crons] a uso intensivo di risorse, le risorse del sito saranno soggette a un carico elevato.

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

![Ricostruzioni indice core](../../assets/tools/observation-for-adobe-commerce/indexing-tab-2.jpg)

Il fotogramma **[!UICONTROL Core index rebuilds]** esamina le ricompilazioni dell&#39;indice di base in un arco temporale selezionato. Di seguito sono riportate le stringhe analizzate dai registri per indicare il completamento della ricostruzione dell’indice.

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

![tabelle indice catalogsearch](../../assets/tools/observation-for-adobe-commerce/indexing-tab-3.jpg)

Il frame **[!UICONTROL catalogsearch index table(s)]** esamina le tabelle dell&#39;indice catalogsearch in un intervallo temporale selezionato. Questa query esamina la durata delle operazioni dell&#39;archivio dati rispetto alle tabelle il cui nome contiene `%catalogsearch%`.

## [!UICONTROL product index table(s)]

![tabelle indice prodotto](../../assets/tools/observation-for-adobe-commerce/indexing-tab-4.jpg)

Il frame **[!UICONTROL product index table(s)]** esamina le tabelle dell&#39;indice di prodotto in un intervallo temporale selezionato. Questa query esamina la durata delle operazioni dell&#39;archivio dati rispetto alle tabelle il cui nome contiene `%product%`.
