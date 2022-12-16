---
title: Contenuti della coda dei messaggi
description: Scopri Adobe Commerce e i consumatori della coda dei messaggi di Magento Open Source, comprese le funzioni e le impostazioni di configurazione del sistema ad essi associate.
source-git-commit: 2eecaab32b090cfd3c1a8e8832027d3531cf0edc
workflow-type: tm+mt
source-wordcount: '929'
ht-degree: 0%

---


# Contenuti della coda dei messaggi

La tabella seguente identifica tutti i consumatori nella coda dei messaggi, descrive le loro attività e identifica le impostazioni di configurazione del sistema di amministrazione ad essi associate:

| Consumatore e descrizione | Adobe Commerce | Adobe Commerce con B2B | Magento Open Source |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------|-------------------------|---------------------|
| `async.operations.all` | + | + | + |
| Crea messaggi per ogni singola attività di un [funzionamento in serie](https://developer.adobe.com/commerce/php/development/components/message-queues/bulk-operations/), come l&#39;importazione o l&#39;esportazione di articoli, la modifica dei prezzi su scala di massa e l&#39;assegnazione di prodotti a un magazzino. Obbligatorio quando [**[!UICONTROL Admin bulk operations]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html?#admin-bulk-operations) è impostata su **[!UICONTROL Run asynchronously]**nelle impostazioni di configurazione del sistema di amministrazione. |  |  |  |
| `codegeneratorProcessor` | + | + | + |
| Genera coupon in modo asincrono in background. Obbligatorio per utilizzare [generazione di buoni a sconto](https://experienceleague.adobe.com/docs/commerce-admin/marketing/promotions/cart-rules/price-rules-cart-coupon.html#method-2%3A-generate-a-batch-of-coupons) funzionalità. |  |  |  |
| `exportProcessor` | + | + | + |
| Impedisce i timeout di connessione durante il [esportare](https://experienceleague.adobe.com/docs/commerce-admin/systems/data-transfer/data-export.html) di set di dati di grandi dimensioni (ad esempio 200.000 prodotti). |  |  |  |
| `inventoryQtyCounter` | + | + |  |
| Corregge in modo asincrono l&#39;indice azionario dopo aver effettuato un ordine o rimosso un prodotto. Obbligatorio quando [**[!UICONTROL Use deferred stock update]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#product-stock-options) è abilitata nelle impostazioni di configurazione amministratore. Vedi [Best practice sulle prestazioni](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/configuration.html#deferred-stock-update). |  |  |  |
| `inventory.source.items.cleanup` | + | + | + |
| Quando un prodotto viene rimosso, gli elementi sorgente vengono eliminati in modo asincrono in base alla SKU del prodotto. Obbligatorio quando [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) l&#39;opzione stock è abilitata nelle impostazioni di configurazione del sistema di amministrazione. |  |  |  |
| `inventory.mass.update` | + | + | + |
| Elabora in modo asincrono gli articoli di magazzino legacy, aggiorna gli articoli di stock legacy, aggiorna gli articoli di origine predefiniti e reindicizza l’inventario per SKU di prodotto specifici. Obbligatorio quando [**[!UICONTROL Run asynchronously]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#admin-bulk-operations) il funzionamento in blocco è abilitato nelle impostazioni di configurazione del sistema di amministrazione. |  |  |  |
| `inventory.reservations.cleanup` | + | + | + |
| Elimina in modo asincrono le prenotazioni per SKU del prodotto dopo la rimozione di un prodotto. Obbligatorio quando [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) l&#39;opzione stock è abilitata nelle impostazioni di configurazione del sistema di amministrazione. |  |  |  |
| `inventory.reservations.update` | + | + | + |
| Aggiorna in modo asincrono le prenotazioni per SKU del prodotto dopo la rimozione di un prodotto. Obbligatorio quando [**[!UICONTROL Synchronize with Catalog]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html) l&#39;opzione stock è abilitata nelle impostazioni di configurazione del sistema di amministrazione. |  |  |  |
| `inventory.reservations.updateSalabilityStatus` | + | + | + |
| Aggiorna in modo asincrono la quantità salabile di ciascun prodotto assegnato a un magazzino. Questo consumatore deve essere sempre attivo se utilizzi [!DNL Inventory Management]. |  |  |  |
| `inventory.indexer.sourceItem` | + | + | + |
| Reindicizza in modo asincrono gli elementi sorgente. Obbligatorio quando [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) è impostato su &quot;[!UICONTROL asynchronous]&quot; nelle impostazioni di configurazione del sistema di amministrazione. |  |  |  |
| `inventory.indexer.stock` | + | + | + |
| Reindicizza in modo asincrono le risorse. Obbligatorio quando [**[!UICONTROL Stock/Source reindex strategy]**](https://docs.magento.com/user-guide/configuration/catalog/inventory.html#inventory-indexer-settings) è impostato su &quot;[!UICONTROL asynchronous]&quot; nelle impostazioni di configurazione del sistema di amministrazione. |  |  |  |
| `matchCustomerSegmentProcessor` | + | + |  |
| Crea una tabella di database temporanea, sposta ogni [segmento del cliente](https://docs.magento.com/user-guide/marketing/customer-segments.html) elimina tutti i segmenti che corrispondono all’ID segmento e li copia nei segmenti cliente utilizzando l’ID segmento come indicatore. Questo viene fatto in una transazione in modo che se qualcosa non riesce, riporta la transazione a quello che era prima di questa esecuzione. Dopo una transazione, il consumatore rilascia la tabella temporanea. |  |  |  |
| `media.content.synchronization` | + | + | + |
| Assicura che i collegamenti ai file multimediali assegnati per i prodotti, le categorie, i blocchi CMS e le pagine CMS siano correttamente assegnati alla risorsa. Rimuove le risorse precedenti che non sono più utilizzate. |  |  |  |
| `media.gallery.renditions.update` | + | + | + |
| Genera e convalida i percorsi delle risorse multimediali. Il percorso assoluto di una risorsa è determinato dalla posizione del server all’interno della directory multimediale. Le immagini vengono ridimensionate (se necessario) e copiate nella directory multimediale all’interno del percorso generato. |  |  |  |
| `media.gallery.synchronization` | + | + | + |
| Importa i file di immagine in `media_gallery_asset` tabella del database. |  |  |  |
| `media.storage.catalog.image.resize` | + | + | + |
| Asincrono [ridimensionare](https://developer.adobe.com/commerce/frontend-core/guide/themes/configure/#resize-catalog-images) immagini di catalogo. |  |  |  |
| `negotiableQuotePriceUpdate` |  | + |  |
| Aggiorna i prezzi per le quotazioni negoziabili. Obbligatorio quando [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) è abilitata nelle impostazioni di configurazione del sistema di amministrazione. |  |  |  |
| `placeOrderProcessor` | + | + |  |
| Asincrono [elabora ordini](https://developer.adobe.com/commerce/php/module-reference/module-async-order/), che contrassegna gli ordini ricevuti, li inserisce nella coda dei messaggi ed elabora gli ordini in base al principio di &quot;first in first out&quot;. Considerato come [best practice](../../implementation-playbook/best-practices/maintenance/order-processing-configuration.md) per migliorare il numero di ordini che possono essere elaborati, perché i clienti non devono attendere il completamento dei processi di backend prima di visualizzare un messaggio di successo. |  |  |  |
| `product_action_attribute.update` | + | + | + |
| Scrive in modo asincrono le modifiche agli attributi del prodotto nel database dopo aver utilizzato l’amministratore in [effettuare aggiornamenti](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |  |  |  |
| `product_action_attribute.website.update` | + | + | + |
| Scrive in modo asincrono le modifiche agli attributi del prodotto per una visualizzazione archivio specifica nel database dopo aver utilizzato l&#39;amministratore in [effettuare aggiornamenti](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/bulk-product-attribute-update.html). |  |  |  |
| `product_alert` | + | + | + |
| Invia e-mail di notifica ai clienti in merito alle modifiche al prezzo del prodotto e all’inventario. Obbligatorio quando il campo [**[!UICONTROL Product Alerts]**](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-alerts/alert-setup.html) è abilitata nelle impostazioni di configurazione del sistema di amministrazione. |  |  |  |
| `purchaseorder.toorder` |  | + |  |
| Converte l&#39;ordine di acquisto in [ordine](https://docs.magento.com/user-guide/stores/b2b-purchase-order-flow.html#approval-rules). Obbligatorio quando [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) è abilitata nelle impostazioni di configurazione del sistema di amministrazione. |  |  |  |
| `purchaseorder.transactional.email` |  | + |  |
| Invia e-mail nell&#39;ordine di acquisto. Obbligatorio quando [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) è abilitata nelle impostazioni di configurazione del sistema di amministrazione. |  |  |  |
| `purchaseorder.validation` |  | + |  |
| Convalida l&#39;ordine di acquisto in base alle [norme di approvazione](https://docs.magento.com/user-guide/customers/account-dashboard-approval-rules.html). Obbligatorio quando [**[!UICONTROL Purchase Order]**](https://experienceleague.adobe.com/docs/commerce-admin/b2b/purchase-orders/purchase-order-flow.html) è abilitata nelle impostazioni di configurazione del sistema di amministrazione. |  |  |  |
| `sales.rule.update.coupon.usage` | + | + | + |
| Impedisce la [problema](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/coupon-code-used-more-than-once-adobe-commerce.html) in cui i coupon monouso possono essere utilizzati più volte. |  |  |  |
| `sharedCatalogUpdateCategoryPermissions` |  | + |  |
| Aggiorna le categorie assegnate a una categoria di catalogo condiviso. Obbligatorio quando [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) è abilitata nelle impostazioni di configurazione del sistema di amministrazione. |  |  |  |
| `sharedCatalogUpdatePrice` |  | + |  |
| Aggiorna il prezzo di ciascun prodotto in un catalogo condiviso. Obbligatorio quando [**[!UICONTROL Shared Catalogs]**](https://docs.magento.com/user-guide/catalog/catalog-shared.html) è abilitata nelle impostazioni di configurazione del sistema di amministrazione. |  |  |  |
| `quoteItemCleaner` | + | + |  |
| Elimina le quotazioni di prezzo non valide o inattive quando un prodotto viene eliminato dal catalogo o rimosso dal carrello. Obbligatorio quando [**[!UICONTROL Quotes]**](https://docs.magento.com/user-guide/sales/quotes.html) è abilitata nelle impostazioni di configurazione del sistema di amministrazione. |  |  |  |

{style=&quot;table-layout:auto&quot;}
