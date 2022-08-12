---
title: '"Il [!UICONTROL Indexing] scheda"'
description: Scopri le [!UICONTROL Indexing] scheda di [!DNL Observation for Adobe Commerce].
source-git-commit: 1f334f329b72b715afa7f3617b1ce2fb8004f816
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 0%

---

# La [!UICONTROL Indexing] scheda

La **[!UICONTROL Indexing]** tab tenta di spiegare i problemi relativi all’indicizzazione e di identificare le potenziali cause.

## [!UICONTROL Core index invalidated]

![Indice di base non convalidato](../../assets/tools/observation-for-adobe-commerce/indexing-tab-1.jpg)

La **[!UICONTROL Core index invalidated]** esamina l’invalidazione dell’indicizzazione in un arco temporale selezionato. Se l&#39;indicizzazione si verifica contemporaneamente ad altri cronisti ad uso intensivo di risorse, le risorse del sito subiranno un carico pesante.

* &#39;%Catalog Product Rule indexer è stato invalidato%&#39;) come &#39;catalog_product_rule_idx_reset&#39;
* &#39;%Catalog Rule Product indexer è stato invalidato%&#39;) come &#39;catalog_rule_product_idx_reset&#39;
* &#39;%Catalog Search indexer è stato invalidato%&#39;) come &#39;catalog_search_idx_reset&#39;
* &#39;%Category Products indexer è stato invalidato%&#39;) come &#39;category_products_idx_reset&#39;
* L&#39;indicizzatore della griglia del cliente &#39;%Customer è stato invalidato%&#39;) come &#39;customer_grid_idx_reset&#39;
* L&#39;indicizzatore della griglia di configurazione &#39;%Design è stato invalidato%&#39;) come &#39;design_config_grid_idx_
* &#39;%Product Categories indexer è stato invalidato%&#39;) come &#39;product_categories_idx_reset&#39;
* &#39;%Product EAV indexer è stato invalidato%&#39;) come &#39;product_eav_idx_reset&#39;
* &#39;%Product Price indexer è stato invalidato%&#39;) come &#39;product_price_idx_reset&#39;
* &#39;%Stock indexer è stato invalidato%&#39;) come &#39;stock_idx_reset&#39;
* &#39;%Inventory indexer è stato invalidato%&#39;) come &#39;inventory_idx_reset&#39;
* &#39;%Inventory indexer è stato invalidato%&#39;) come &#39;inventory_idx_reset&#39;
* L&#39;indicizzatore della regola di vendita &#39;%Sales è stato invalidato%&#39;) come &#39;sales_rule_idx_reset&#39;

## [!UICONTROL Core index rebuilds]

![Ricostruzioni dell&#39;indice di base](../../assets/tools/observation-for-adobe-commerce/indexing-tab-2.jpg)

La **[!UICONTROL Core index rebuilds]** frame esamina le ricostruzioni dell&#39;indice di base in un arco temporale selezionato. Di seguito sono riportate le stringhe analizzate dai log per indicare il completamento della ricostruzione dell&#39;indice.

* L&#39;indice della regola del prodotto del catalogo è stato ricostruito%) come &#39;catalog_product_rule_idx&#39;
* &#39;%Catalog Rule Indice prodotto è stato ricostruito%&#39;) come &#39;catalog_rule_product_idx&#39;
* &#39;%Catalog Search index è stato ricostruito%&#39;) come &#39;catalog_search_idx&#39;
* &#39;%Category Products index è stato ricostruito correttamente%&#39;) come &#39;category_products_idx&#39;
* L&#39;indice &#39;%Customer Grid è stato ricostruito%&#39;) come &#39;customer_grid_idx&#39;
* &#39;%Design Config Grid index è stato ricostruito%&#39;) come &#39;design_config_grid_idx&#39;
* &#39;%Product Categories index è stato ricostruito%&#39;) come &#39;product_categories_idx&#39;
* &#39;%Product EAV index è stato ricostruito%&#39;) come &#39;product_eav_idx&#39;
* &#39;%Product Price index è stato ricostruito%&#39;) come &#39;product_price_idx&#39;
* &#39;%Stock index è stato ricostruito%&#39;) come &#39;stock_idx&#39;
* &#39;%Inventory index è stato ricostruito correttamente%&#39;) come &#39;inventory_idx&#39;
* L&#39;indice della regola di prodotto/destinazione è stato ricostruito correttamente%) come &#39;prod_target_rule_idx&#39;
* L&#39;indice della regola di vendita &#39;%Sales è stato ricostruito correttamente%&#39;) come &#39;sales_rule_idx&#39;


## [!UICONTROL catalogsearch index table(s)]

![tabella/e dell’indice/i di catalogsearch](../../assets/tools/observation-for-adobe-commerce/indexing-tab-3.jpg)

La **[!UICONTROL catalogsearch index table(s)]** frame esamina le tabelle dell&#39;indice di ricerca catalogica in un arco temporale selezionato. Questa query sta esaminando la durata delle operazioni del datastore rispetto alle tabelle con &quot;%catalogsearch%&quot; nel nome della tabella.

## [!UICONTROL product index table(s)]

![tabella(e) dell&#39;indice(i) del prodotto](../../assets/tools/observation-for-adobe-commerce/indexing-tab-4.jpg)

La **[!UICONTROL product index table(s)]** frame esamina le tabelle dell&#39;indice del prodotto in un arco temporale selezionato. Questa query sta esaminando la durata delle operazioni del datastore rispetto alle tabelle con &quot;%product%&quot; nel nome della tabella.
