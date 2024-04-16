---
title: Consumatori coda messaggi
description: Scopri gli utenti della coda di messaggi di Adobe Commerce, incluse le funzioni e le impostazioni di configurazione del sistema associate.
exl-id: 7fd7ab3f-581f-493c-956c-731f111d1b14
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '825'
ht-degree: 0%

---

# Consumatori coda messaggi

La tabella seguente identifica tutti i consumer della coda di messaggi, ne descrive le operazioni eseguite e identifica le impostazioni di configurazione del sistema di amministrazione associate:

| Consumatore e descrizione | Adobe Commerce | Adobe Commerce con B2B | Magento Open Source |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------|---------------------|
| `async.operations.all` | + | + | + |
| Crea messaggi per ogni singola attività di un [operazione in blocco](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/)ad esempio l&#39;importazione o l&#39;esportazione di articoli, la modifica dei prezzi su scala di massa e l&#39;assegnazione di prodotti a un magazzino. Obbligatorio quando [**[!UICONTROL Admin bulk operations]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html?#admin-bulk-operations) è impostata su **[!UICONTROL Run asynchronously]**nelle impostazioni di configurazione del sistema di amministrazione. |                |                         |                     |
| `codegeneratorProcessor` | + | + | + |
| Genera coupon in background in modo asincrono. Necessario per utilizzare [generazione coupon batch](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html#method-2%3A-generate-a-batch-of-coupons) funzionalità. |                |                         |                     |
| `commerce.eventing.event.publish` | + | + |                     |
| Verifica la presenza di eventi registrati come priorità in [Eventi di Adobe I/O per Adobe Commerce](https://developer.adobe.com/commerce/events/get-started/). |
| `exportProcessor` | + | + | + |
| Impedisce timeout di connessione durante [esportare](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-export.html) di grandi set di dati (ad esempio 200.000 prodotti). |                |                         |                     |
| `inventoryQtyCounter` | + | + |                     |
| Corregge in modo asincrono l&#39;indice azionario dopo aver effettuato un ordine o rimosso un prodotto. Obbligatorio quando [**[!UICONTROL Use deferred stock update]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#product-stock-options) nelle impostazioni di configurazione dell’amministratore. Consulta [Best practice per le prestazioni](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/configuration.html#deferred-stock-update). |                |                         |                     |
| `inventory.source.items.cleanup` | + | + | + |
| Elimina in modo asincrono gli elementi sorgente in base allo SKU del prodotto quando un prodotto viene rimosso. Obbligatorio quando [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) L&#39;opzione Stock è abilitata nelle impostazioni di configurazione del sistema di amministrazione. |                |                         |                     |
| `inventory.mass.update` | + | + | + |
| Elabora in modo asincrono gli articoli di magazzino legacy, aggiorna gli articoli di magazzino legacy, aggiorna gli articoli di origine predefiniti e reindicizza l’inventario per SKU di prodotto specifici. Obbligatorio quando [**[!UICONTROL Run asynchronously]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#admin-bulk-operations) L&#39;operazione in blocco è abilitata nelle impostazioni di configurazione del sistema di amministrazione. |                |                         |                     |
| `inventory.reservations.cleanup` | + | + | + |
| Elimina in modo asincrono le prenotazioni per SKU prodotto dopo la rimozione di un prodotto. Obbligatorio quando [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) L&#39;opzione Stock è abilitata nelle impostazioni di configurazione del sistema di amministrazione. |                |                         |                     |
| `inventory.reservations.update` | + | + | + |
| Aggiorna in modo asincrono le prenotazioni per SKU prodotto dopo la rimozione di un prodotto. Obbligatorio quando [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) L&#39;opzione Stock è abilitata nelle impostazioni di configurazione del sistema di amministrazione. |                |                         |                     |
| `inventory.reservations.updateSalabilityStatus` | + | + | + |
| Aggiorna in modo asincrono la quantità vendibile di ciascun prodotto assegnato a una scorta. Questo consumer deve essere sempre operativo se si utilizza [!DNL Inventory Management]. |                |                         |                     |
| `inventory.indexer.sourceItem` | + | + | + |
| Reindicizza in modo asincrono gli elementi di origine. Obbligatorio quando [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) è impostato su &quot;[!UICONTROL asynchronous]&quot; nelle impostazioni di configurazione del sistema di amministrazione. |                |                         |                     |
| `inventory.indexer.stock` | + | + | + |
| Reindicizza in modo asincrono le azioni. Obbligatorio quando [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) è impostato su &quot;[!UICONTROL asynchronous]&quot; nelle impostazioni di configurazione del sistema di amministrazione. |                |                         |                     |
| `matchCustomerSegmentProcessor` | + | + |                     |
| Crea una tabella di database temporanea, sposta ogni tabella [segmento cliente](https://docs.magento.com/user-guide/marketing/customer-segments.html) elimina tutti i segmenti che corrispondono all’ID del segmento e li copia nei segmenti dei clienti utilizzando l’ID del segmento come indicatore. Tutto ciò viene eseguito in una transazione in modo che, se qualcosa non va a buon fine, la transazione viene ripristinata allo stato precedente all&#39;esecuzione. Dopo una transazione, il consumatore elimina la tabella temporanea. |                |                         |                     |
| `media.content.synchronization` | + | + | + |
| Assegna correttamente alla risorsa i collegamenti ai contenuti multimediali assegnati per prodotti, categorie, blocchi CMS e pagine CMS. Rimuove le risorse obsolete non più utilizzate. |                |                         |                     |
| `media.gallery.renditions.update` | + | + | + |
| Genera e convalida i percorsi delle risorse multimediali. Il percorso assoluto di una risorsa è determinato dalla posizione in cui si trova sul server dall’interno della directory multimediale. Le immagini vengono ridimensionate (se necessario) e copiate nella directory dei file multimediali all&#39;interno del percorso generato. |                |                         |                     |
| `media.gallery.synchronization` | + | + | + |
| Importa i file immagine in `media_gallery_asset` tabella di database. |                |                         |                     |
| `media.storage.catalog.image.resize` | + | + | + |
| Asincrono [ridimensiona](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#resize-catalog-images) immagini del catalogo. |                |                         |                     |
| `negotiableQuotePriceUpdate` |                | + |                     |
| Aggiorna i prezzi per i preventivi negoziabili. Obbligatorio quando [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) nelle impostazioni di configurazione del sistema di amministrazione. |                |                         |                     |
| `placeOrderProcessor` | + | + |                     |
| Asincrono [elabora gli ordini](https://developer.adobe.com/commerce/php/module-reference/module-async-order/), che contrassegna gli ordini come ricevuti, li inserisce nella coda dei messaggi ed li elabora in base al principio &quot;first in first out&quot;. Considerato un [best practice](../../implementation-playbook/best-practices/maintenance/order-processing-configuration.md) per migliorare il numero di ordini che possono essere elaborati perché i clienti non devono attendere il completamento dei processi back-end prima di visualizzare un messaggio di successo. |                |                         |                     |
| `product_action_attribute.update` | + | + | + |
| Scrive in modo asincrono le modifiche agli attributi del prodotto nel database dopo aver utilizzato l’amministratore per [apportare aggiornamenti](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |                |                         |                     |
| `product_action_attribute.website.update` | + | + | + |
| Scrive in modo asincrono le modifiche agli attributi del prodotto per una specifica vista store nel database dopo aver utilizzato l’amministratore per [apportare aggiornamenti](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |                |                         |                     |
| `product_alert` | + | + | + |
| Invia e-mail di notifica ai clienti sulle variazioni di prezzo del prodotto e inventario. Obbligatorio quando la proprietà Obbligatorio quando [**[!UICONTROL Product Alerts]**](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup.html) nelle impostazioni di configurazione del sistema di amministrazione. |                |                         |                     |
| `purchaseorder.toorder` |                | + |                     |
| Converte l&#39;ordine fornitore in [ordine](https://docs.magento.com/user-guide/stores/b2b-purchase-order-flow.html#approval-rules). Obbligatorio quando [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) nelle impostazioni di configurazione del sistema di amministrazione. |                |                         |                     |
| `purchaseorder.transactional.email` |                | + |                     |
| Invia e-mail ordine fornitore. Obbligatorio quando [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) nelle impostazioni di configurazione del sistema di amministrazione. |                |                         |                     |
| `purchaseorder.validation` |                | + |                     |
| Convalida l&#39;ordine fornitore a fronte dei relativi [regole di approvazione](https://docs.magento.com/user-guide/customers/account-dashboard-approval-rules.html). Obbligatorio quando [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) nelle impostazioni di configurazione del sistema di amministrazione. |                |                         |                     |
| `saveConfigProcessor` | + |                         | + |
| Salva in modo asincrono le modifiche alla configurazione dell&#39;archivio inserendo i processi di salvataggio in una coda di messaggi, il che può migliorare le prestazioni in implementazioni che contengono un numero elevato di configurazioni a livello di archivio. Necessario per utilizzare [`AsyncConfig`](../../performance/configuration.md#asynchronous-configuration-save) modulo. |                |                         |                     |
| `sales.rule.update.coupon.usage` | + | + | + |
| Impedisce la [problema](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/coupon-code-used-more-than-once-adobe-commerce.html) dove i coupon monouso possono essere utilizzati più volte. |                |                         |                     |
| `sharedCatalogUpdateCategoryPermissions` |                | + |                     |
| Aggiorna le categorie assegnate a una categoria di catalogo condiviso. Obbligatorio quando [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) nelle impostazioni di configurazione del sistema di amministrazione. |                |                         |                     |
| `sharedCatalogUpdatePrice` |                | + |                     |
| Aggiorna il prezzo per ogni prodotto in un catalogo condiviso. Obbligatorio quando [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) nelle impostazioni di configurazione del sistema di amministrazione. |                |                         |                     |
| `quoteItemCleaner` | + | + |                     |
| Elimina i preventivi di prezzo non validi o inattivi quando un prodotto viene eliminato dal catalogo o rimosso dal carrello. Obbligatorio quando [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) nelle impostazioni di configurazione del sistema di amministrazione. |                |                         |                     |
| `sales.rule.quote.trigger.recollect` | + | + | + |
| Aggiorna i carrelli acquisti attivi per riflettere le modifiche nella regola del prezzo del carrello. Obbligatorio durante l’aggiornamento [**[!UICONTROL Catalog price rules]**](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/catalog-rules/price-rules-catalog.html). |                |                         |                     |

{style="table-layout:auto"}
