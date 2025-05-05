---
title: Consumatori coda messaggi
description: Scopri gli utenti della coda di messaggi di Adobe Commerce, incluse le funzioni e le impostazioni di configurazione del sistema associate.
exl-id: 7fd7ab3f-581f-493c-956c-731f111d1b14
source-git-commit: 95ea96a566b0579a22b2ba738bd4a4bceef8cd9c
workflow-type: tm+mt
source-wordcount: '824'
ht-degree: 0%

---

# Consumatori coda messaggi

La tabella seguente identifica tutti i consumer della coda di messaggi, ne descrive le operazioni eseguite e identifica le impostazioni di configurazione del sistema di amministrazione associate:

| Consumatore e descrizione | Adobe Commerce | Adobe Commerce con B2B | Magento Open Source |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------|---------------------|
| `async.operations.all` | + | + | + |
| Crea messaggi per ogni singola attività di una [operazione in blocco](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/), ad esempio l&#39;importazione o l&#39;esportazione di articoli, la modifica dei prezzi su scala di massa e l&#39;assegnazione di prodotti a un magazzino. Obbligatorio se l&#39;opzione [**[!UICONTROL Admin bulk operations]**](https://experienceleague.adobe.com/it/docs/commerce-admin/config/catalog/inventory#admin-bulk-operations) è impostata su **[!UICONTROL Run asynchronously]**&#x200B;nelle impostazioni di configurazione del sistema di amministrazione. |                |                         |                     |
| `codegeneratorProcessor` | + | + | + |
| Genera coupon in background in modo asincrono. Necessario per utilizzare la funzionalità [generazione coupon batch](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html?lang=it#method-2%3A-generate-a-batch-of-coupons). |                |                         |                     |
| `commerce.eventing.event.publish` | + | + |                     |
| Cerca gli eventi registrati come prioritari in [Eventi Adobi I/O per Adobe Commerce](https://developer.adobe.com/commerce/events/get-started/). |
| `exportProcessor` | + | + | + |
| Impedisce timeout di connessione durante l&#39;[esportazione](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-export.html?lang=it) di set di dati di grandi dimensioni (ad esempio 200.000 prodotti). |                |                         |                     |
| `inventoryQtyCounter` | + | + |                     |
| Corregge in modo asincrono l&#39;indice azionario dopo aver effettuato un ordine o rimosso un prodotto. Obbligatorio se l&#39;opzione [**[!UICONTROL Use deferred stock update]**](https://experienceleague.adobe.com/it/docs/commerce-admin/config/catalog/inventory#product-stock-options) è abilitata nelle impostazioni di configurazione dell&#39;amministratore. Consulta [Best practice per le prestazioni](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/configuration.html?lang=it#deferred-stock-update). |                |                         |                     |
| `inventory.source.items.cleanup` | + | + | + |
| Elimina in modo asincrono gli elementi sorgente in base allo SKU del prodotto quando un prodotto viene rimosso. Obbligatorio se l&#39;opzione di magazzino [**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/it/docs/commerce-admin/config/catalog/inventory) è abilitata nelle impostazioni di configurazione del sistema di amministrazione. |                |                         |                     |
| `inventory.mass.update` | + | + | + |
| Elabora in modo asincrono gli articoli di magazzino legacy, aggiorna gli articoli di magazzino legacy, aggiorna gli articoli di origine predefiniti e reindicizza l’inventario per SKU di prodotto specifici. Obbligatorio se l&#39;operazione collettiva [**[!UICONTROL Run asynchronously]**](https://experienceleague.adobe.com/it/docs/commerce-admin/config/catalog/inventory#admin-bulk-operations) è abilitata nelle impostazioni di configurazione del sistema di amministrazione. |                |                         |                     |
| `inventory.reservations.cleanup` | + | + | + |
| Elimina in modo asincrono le prenotazioni per SKU prodotto dopo la rimozione di un prodotto. Obbligatorio se l&#39;opzione di magazzino [**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/it/docs/commerce-admin/config/catalog/inventory) è abilitata nelle impostazioni di configurazione del sistema di amministrazione. |                |                         |                     |
| `inventory.reservations.update` | + | + | + |
| Aggiorna in modo asincrono le prenotazioni per SKU prodotto dopo la rimozione di un prodotto. Obbligatorio se l&#39;opzione di magazzino [**[!UICONTROL Synchronize with Catalog]**](https://experienceleague.adobe.com/it/docs/commerce-admin/config/catalog/inventory) è abilitata nelle impostazioni di configurazione del sistema di amministrazione. |                |                         |                     |
| `inventory.reservations.updateSalabilityStatus` | + | + | + |
| Aggiorna in modo asincrono la quantità vendibile di ciascun prodotto assegnato a una scorta. Questo consumer deve essere sempre operativo se si utilizza [!DNL Inventory Management]. |                |                         |                     |
| `inventory.indexer.sourceItem` | + | + | + |
| Reindicizza in modo asincrono gli elementi di origine. Obbligatorio se [**[!UICONTROL Stock/Source reindex strategy]**](https://experienceleague.adobe.com/it/docs/commerce-admin/config/catalog/inventory#inventory-indexer-settings) è impostato su &quot;[!UICONTROL asynchronous]&quot; nelle impostazioni di configurazione del sistema di amministrazione. |                |                         |                     |
| `inventory.indexer.stock` | + | + | + |
| Reindicizza in modo asincrono le azioni. Obbligatorio se [**[!UICONTROL Stock/Source reindex strategy]**](https://experienceleague.adobe.com/it/docs/commerce-admin/config/catalog/inventory#inventory-indexer-settings) è impostato su &quot;[!UICONTROL asynchronous]&quot; nelle impostazioni di configurazione del sistema di amministrazione. |                |                         |                     |
| `matchCustomerSegmentProcessor` | + | + |                     |
| Crea una tabella di database temporanea, sposta in essa ogni [segmento cliente](https://experienceleague.adobe.com/it/docs/commerce-admin/customers/segments/customer-segments), elimina tutti i segmenti che corrispondono all&#39;ID del segmento e li copia nei segmenti cliente utilizzando l&#39;ID del segmento come indicatore. Tutto ciò viene eseguito in una transazione in modo che, se qualcosa non va a buon fine, la transazione viene ripristinata allo stato precedente all&#39;esecuzione. Dopo una transazione, il consumatore elimina la tabella temporanea. |                |                         |                     |
| `media.content.synchronization` | + | + | + |
| Assegna correttamente alla risorsa i collegamenti ai contenuti multimediali assegnati per prodotti, categorie, blocchi CMS e pagine CMS. Rimuove le risorse obsolete non più utilizzate. |                |                         |                     |
| `media.gallery.renditions.update` | + | + | + |
| Genera e convalida i percorsi delle risorse multimediali. Il percorso assoluto di una risorsa è determinato dalla posizione in cui si trova sul server dall’interno della directory multimediale. Le immagini vengono ridimensionate (se necessario) e copiate nella directory dei file multimediali all&#39;interno del percorso generato. |                |                         |                     |
| `media.gallery.synchronization` | + | + | + |
| Importa i file di immagine nella tabella del database `media_gallery_asset`. |                |                         |                     |
| `media.storage.catalog.image.resize` | + | + | + |
| [ridimensiona](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#resize-catalog-images) le immagini del catalogo in modo asincrono. |                |                         |                     |
| `negotiableQuotePriceUpdate` |                | + |                     |
| Aggiorna i prezzi per i preventivi negoziabili. Obbligatorio se l&#39;opzione [**[!UICONTROL Quotes]**](https://experienceleague.adobe.com/it/docs/commerce-admin/b2b/quotes/quotes) è abilitata nelle impostazioni di configurazione del sistema di amministrazione. |                |                         |                     |
| `placeOrderProcessor` | + | + |                     |
| [elabora in modo asincrono gli ordini](https://developer.adobe.com/commerce/php/module-reference/module-async-order/), che contrassegnano gli ordini come ricevuti, li inserisce nella coda dei messaggi ed li elabora in base al principio &quot;first in first out&quot;. Considerata una [best practice](../../implementation-playbook/best-practices/maintenance/order-processing-configuration.md) per il miglioramento del numero di ordini che possono essere elaborati perché i clienti non devono attendere il completamento dei processi back-end prima di visualizzare un messaggio di successo. |                |                         |                     |
| `product_action_attribute.update` | + | + | + |
| Scrive in modo asincrono le modifiche agli attributi del prodotto nel database dopo aver utilizzato l&#39;amministratore per [apportare aggiornamenti](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html?lang=it). |                |                         |                     |
| `product_action_attribute.website.update` | + | + | + |
| Scrive in modo asincrono le modifiche agli attributi del prodotto per una visualizzazione archivio specifica nel database dopo aver utilizzato l&#39;amministratore per [apportare aggiornamenti](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html?lang=it). |                |                         |                     |
| `product_alert` | + | + | + |
| Invia e-mail di notifica ai clienti sulle variazioni di prezzo del prodotto e inventario. Obbligatorio quando l&#39;opzione [**[!UICONTROL Product Alerts]**](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup.html?lang=it) è abilitata nelle impostazioni di configurazione del sistema di amministrazione. |                |                         |                     |
| `purchaseorder.toorder` |                | + |                     |
| Converte l&#39;ordine fornitore in [ordine](https://experienceleague.adobe.com/it/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow#approval-rules). Obbligatorio se l&#39;opzione [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html?lang=it) è abilitata nelle impostazioni di configurazione del sistema di amministrazione. |                |                         |                     |
| `purchaseorder.transactional.email` |                | + |                     |
| Invia e-mail ordine fornitore. Obbligatorio se l&#39;opzione [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html?lang=it) è abilitata nelle impostazioni di configurazione del sistema di amministrazione. |                |                         |                     |
| `purchaseorder.validation` |                | + |                     |
| Convalida l&#39;ordine fornitore in base alle [regole di approvazione](https://experienceleague.adobe.com/it/docs/commerce-admin/b2b/purchase-orders/account-dashboard-approval-rules) pertinenti. Obbligatorio se l&#39;opzione [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html?lang=it) è abilitata nelle impostazioni di configurazione del sistema di amministrazione. |                |                         |                     |
| `saveConfigProcessor` | + |                         | + |
| Salva in modo asincrono le modifiche alla configurazione dell&#39;archivio inserendo i processi di salvataggio in una coda di messaggi, il che può migliorare le prestazioni in implementazioni che contengono un numero elevato di configurazioni a livello di archivio. Obbligatorio per utilizzare il modulo [`AsyncConfig`](../../performance/configuration.md#asynchronous-configuration-save). |                |                         |                     |
| `sales.rule.update.coupon.usage` | + | + | + |
| Evita un problema in cui i coupon monouso possono essere utilizzati più volte. |                |                         |                     |
| `sharedCatalogUpdateCategoryPermissions` |                | + |                     |
| Aggiorna le categorie assegnate a una categoria di catalogo condiviso. Obbligatorio se l&#39;opzione [**[!UICONTROL Shared Catalogs]**](https://experienceleague.adobe.com/it/docs/commerce-admin/b2b/shared-catalogs/catalog-shared) è abilitata nelle impostazioni di configurazione del sistema di amministrazione. |                |                         |                     |
| `sharedCatalogUpdatePrice` |                | + |                     |
| Aggiorna il prezzo per ogni prodotto in un catalogo condiviso. Obbligatorio se l&#39;opzione [**[!UICONTROL Shared Catalogs]**](https://experienceleague.adobe.com/it/docs/commerce-admin/b2b/shared-catalogs/catalog-shared) è abilitata nelle impostazioni di configurazione del sistema di amministrazione. |                |                         |                     |
| `quoteItemCleaner` | + | + |                     |
| Elimina i preventivi di prezzo non validi o inattivi quando un prodotto viene eliminato dal catalogo o rimosso dal carrello. Obbligatorio se l&#39;opzione [**[!UICONTROL Quotes]**](https://experienceleague.adobe.com/it/docs/commerce-admin/b2b/quotes/quotes) è abilitata nelle impostazioni di configurazione del sistema di amministrazione. |                |                         |                     |
| `sales.rule.quote.trigger.recollect` | + | + | + |
| Aggiorna i carrelli acquisti attivi per riflettere le modifiche nella regola del prezzo del carrello. Obbligatorio per l&#39;aggiornamento di [**[!UICONTROL Catalog price rules]**](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/catalog-rules/price-rules-catalog.html?lang=it). |                |                         |                     |

{style="table-layout:auto"}
