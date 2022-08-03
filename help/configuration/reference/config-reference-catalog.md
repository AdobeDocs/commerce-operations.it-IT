---
title: Riferimento per i percorsi di configurazione del catalogo
description: Consulta un elenco dei valori di configurazione del catalogo.
source-git-commit: bd1bf6edd131ec93902246e95ce857b509f2a619
workflow-type: tm+mt
source-wordcount: '827'
ht-degree: 0%

---


# Riferimento per i percorsi di configurazione del catalogo

In questa sezione sono elencati i nomi delle variabili e i percorsi di configurazione disponibili per le opzioni in Amministratore in **Negozi** > Impostazioni > **Configurazione** > **Catalogo**.

La [`magento app:config:dump` command](../cli/export-configuration.md) scrive questi valori nel file di configurazione condiviso, `app/etc/config.php`, che dovrebbe essere nel controllo della sorgente. Per ignorare facoltativamente le impostazioni di configurazione o per impostare le impostazioni sensibili, vedi [Utilizzare le variabili di ambiente per ignorare le impostazioni di configurazione](override-config-settings.md#environment-variables). Questo argomento _not_ elenco [valori sensibili e specifici del sistema](config-reference-sens.md).

## Percorsi del catalogo

Questi valori di configurazione sono disponibili in Amministratore in **Negozi** > Impostazioni > **Configurazione** > **Catalogo** > **Catalogo**.

| Nome | Percorso di configurazione | Solo commercio? |
|--------------|--------------|--------------|
| Maschera per SKU | `catalog/fields_masks/sku` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maschera per il titolo meta | `catalog/fields_masks/meta_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maschera per parole chiave | `catalog/fields_masks/meta_keyword` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maschera per descrizione Meta | `catalog/fields_masks/meta_description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modalità elenco | `catalog/frontend/list_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prodotti per pagina nei valori consentiti dalla griglia | `catalog/frontend/grid_per_page_values` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prodotti per pagina nel valore predefinito della griglia | `catalog/frontend/grid_per_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prodotti per pagina nell’elenco dei valori consentiti | `catalog/frontend/list_per_page_values` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prodotti per pagina su Elenca valore predefinito | `catalog/frontend/list_per_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Elenco prodotti Ordina per | `catalog/frontend/default_sort_by` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Consenti tutti i prodotti per pagina | `catalog/frontend/list_allow_all` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usa categoria catalogo piatto | `catalog/frontend/flat_catalog_category` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usa prodotto catalogo piatto | `catalog/frontend/flat_catalog_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Campioni per prodotto | `catalog/frontend/swatches_per_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Consenti agli ospiti di scrivere recensioni | `catalog/review/allow_guest` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Consenti avviso quando cambia il prezzo del prodotto | `catalog/productalert/allow_price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail avviso prezzo | `catalog/productalert/email_price_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Consenti avviso quando il prodotto torna in magazzino | `catalog/productalert/allow_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail di avviso Stock | `catalog/productalert/email_stock_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Invia e-mail avviso | `catalog/productalert/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequenza | `catalog/productalert_cron/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ora di inizio | `catalog/productalert_cron/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Errore mittente e-mail | `catalog/productalert_cron/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail errore | `catalog/productalert_cron/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostra per corrente | `catalog/recently_products/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Conteggio prodotti visualizzati di recente predefiniti | `catalog/recently_products/viewed_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Conteggio prodotti confrontati di recente | `catalog/recently_products/compared_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Video base autostart | `catalog/product_video/play_if_base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostra video correlati | `catalog/product_video/show_related` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Riavvio automatico del video | `catalog/product_video/video_auto_restart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Campo di applicazione del prezzo del catalogo | `catalog/price/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prezzo predefinito del prodotto | `catalog/price/default_product_price` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Visualizza conteggio prodotti | `catalog/layered_navigation/display_product_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calcolo del passaggio di navigazione del prezzo | `catalog/layered_navigation/price_range_calculation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Passaggio predefinito di navigazione dei prezzi | `catalog/layered_navigation/price_range_step` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizza intervallo di prezzo come prezzo unico | `catalog/layered_navigation/one_price_interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Numero massimo di intervalli di prezzo | `catalog/layered_navigation/price_range_max_intervals` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limite divisione a intervalli | `catalog/layered_navigation/interval_division_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Profondità massima | `catalog/navigation/max_depth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lunghezza minima query | `catalog/search/min_query_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lunghezza massima query | `catalog/search/max_query_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Motore di ricerca | `catalog/search/engine` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Timeout del server solare | `catalog/search/solr_server_timeout` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Modalità di indicizzazione | `catalog/search/engine_commit_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita suggerimenti di ricerca | `catalog/search/search_suggestion_enabled` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Conteggio suggerimenti di ricerca | `catalog/search/search_suggestion_count` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Mostra il conteggio dei risultati per ogni suggerimento | `catalog/search/search_suggestion_count_results_enabled` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Abilita ricerca in Recommendations | `catalog/search/search_recommendations_enabled` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Conteggio Recommendations di ricerca | `catalog/search/search_recommendations_count` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Mostra il conteggio dei risultati per ogni raccomandazione | `catalog/search/search_recommendations_count_results_enabled` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Termini minimi da abbinare | `catalog/search/minimum_should_match` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Termini di ricerca popolari | `catalog/seo/search_terms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Suffisso URL prodotto | `catalog/seo/product_url_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Suffisso URL categoria | `catalog/seo/category_url_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usa percorso categorie per gli URL dei prodotti | `catalog/seo/product_use_categories` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Crea reindirizzamento permanente per gli URL se la chiave URL è cambiata | `catalog/seo/save_rewrites_history` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Separatore dei titoli della pagina | `catalog/seo/title_separator` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usa Tag Meta Collegamento Canonico Per Categorie | `catalog/seo/category_canonical_tag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usa Tag Meta Collegamento Canonico Per I Prodotti | `catalog/seo/product_canonical_tag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita | `catalog/magento_catalogpermissions/enabled` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Consenti categoria di navigazione | `catalog/magento_catalogpermissions/grant_catalog_category_view` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Gruppi di clienti | `catalog/magento_catalogpermissions/grant_catalog_category_view_groups` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Pagina di destinazione | `catalog/magento_catalogpermissions/restricted_landing_page` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Visualizza i prezzi dei prodotti | `catalog/magento_catalogpermissions/grant_catalog_product_price` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Gruppi di clienti | `catalog/magento_catalogpermissions/grant_catalog_product_price_groups` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Consenti aggiunta al carrello | `catalog/magento_catalogpermissions/grant_checkout_items` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Gruppi di clienti | `catalog/magento_catalogpermissions/grant_checkout_items_groups` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Non consentire la ricerca nel catalogo per | `catalog/magento_catalogpermissions/deny_catalog_search` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Stato dell&#39;articolo dell&#39;ordine per abilitare i download | `catalog/downloadable/order_item_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Numero massimo predefinito di download | `catalog/downloadable/downloads_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| condivisibile | `catalog/downloadable/shareable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo campione predefinito | `catalog/downloadable/samples_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo collegamento predefinito | `catalog/downloadable/links_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Apri collegamenti in una nuova finestra | `catalog/downloadable/links_target_new_window` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usa disposizione dei contenuti | `catalog/downloadable/content_disposition` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Disattiva il pagamento degli ospiti se il carrello contiene elementi scaricabili | `catalog/downloadable/disable_guest_checkout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usa calendario JavaScript | `catalog/custom_options/use_calendar` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordine campi data | `catalog/custom_options/date_fields_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Formato ora | `catalog/custom_options/time_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Intervallo anno | `catalog/custom_options/year_range` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita funzionalità eventi catalogo | `catalog/magento_catalogevent/enabled` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Abilita Widget evento catalogo su Storefront | `catalog/magento_catalogevent/lister_output` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Numero di eventi da visualizzare nel Widget del cursore evento | `catalog/magento_catalogevent/lister_widget_limit` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Eventi da scorrere per clic nel widget Cursore eventi | `catalog/magento_catalogevent/lister_widget_scroll` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Numero massimo di prodotti nell&#39;elenco dei prodotti correlati | `catalog/magento_targetrule/related_position_limit` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Mostra prodotti correlati | `catalog/magento_targetrule/related_position_behavior` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Modalità di rotazione per i prodotti nell&#39;elenco dei prodotti correlati | `catalog/magento_targetrule/related_rotation_mode` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Numero massimo di prodotti nella lista di prodotti venduti incrociati | `catalog/magento_targetrule/crosssell_position_limit` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Mostra prodotti venduti | `catalog/magento_targetrule/crosssell_position_behavior` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Modalità di rotazione per i prodotti nell&#39;elenco dei prodotti venduti | `catalog/magento_targetrule/crosssell_rotation_mode` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Numero massimo di prodotti nell&#39;elenco dei prodotti di upselling | `catalog/magento_targetrule/upsell_position_limit` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Mostra prodotti di upselling | `catalog/magento_targetrule/upsell_position_behavior` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Modalità di rotazione per i prodotti in Upselling Product List | `catalog/magento_targetrule/upsell_rotation_mode` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |

{style=&quot;table-layout:auto&quot;}

## Percorsi inventario

Questi valori di configurazione sono disponibili in Amministratore in **Negozi** > Impostazioni > **Configurazione** > **Catalogo** > **Inventario**.

| Nome | Percorso di configurazione | Solo commercio? |
|--------------|--------------|--------------|
| Diminuisci stock quando l&#39;ordine viene posizionato | `cataloginventory/options/can_subtract` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Imposta lo stato degli elementi in magazzino quando l&#39;ordine viene annullato | `cataloginventory/options/can_back_in_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizzazione dei prodotti esauriti | `cataloginventory/options/show_out_of_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Solo X soglia sinistra | `cataloginventory/options/stock_threshold_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizza la disponibilità dei prodotti in magazzino su Storefront | `cataloginventory/options/display_product_stock_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sincronizza con catalogo | `cataloginventory/options/synchronize_with_catalog` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Gestire le azioni | `cataloginventory/item_options/manage_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Backorder | `cataloginventory/item_options/backorders` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usa aggiornamento azioni differite | `cataloginventory/item_options/use_deferred_stock_update` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Quantità massima consentita nel carrello acquisti | `cataloginventory/item_options/max_sale_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Soglia esaurita | `cataloginventory/item_options/min_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Quantità minima consentita nel carrello acquisti | `cataloginventory/item_options/min_sale_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Notifica per la quantità sotto indicata | `cataloginventory/item_options/notify_stock_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita incrementi di quantità | `cataloginventory/item_options/enable_qty_increments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Incrementi di quantità | `cataloginventory/item_options/qty_increments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Restituisci automaticamente l&#39;articolo della nota di accredito in magazzino | `cataloginventory/item_options/auto_return` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Esegui in modo asincrono | `cataloginventory/bulk_operations/async` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Dimensione batch asincrona | `cataloginventory/bulk_operations/batch_size` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Provider | `cataloginventory/source_selection_distance_based/provider` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modalità di calcolo | `cataloginventory/source_selection_distance_based_google/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valore | `cataloginventory/source_selection_distance_based_google/value` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Percorsi di Visual Merchandiser

Questi valori di configurazione sono disponibili in Amministratore in **Negozi** > Impostazioni > **Configurazione** > **Catalogo** > **Merchandiser visivo**.

| Nome | Percorso di configurazione | Solo commercio? |
|--------------|--------------|--------------|
| Attributi visibili per le regole di categoria | `visualmerchandiser/options/smart_attributes` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Soglia minima scorte | `visualmerchandiser/options/minimum_stock_threshold` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Codice attributo colore | `visualmerchandiser/options/color_attribute_code` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |
| Ordine del colore | `visualmerchandiser/options/color_order` | ![Solo commercio](/help/assets/configuration/cloud-ee.png) |

{style=&quot;table-layout:auto&quot;}

## Percorsi mappa del sito XML

Questi valori di configurazione sono disponibili in Amministratore in **Negozi** > Impostazioni > **Configurazione** > **Catalogo** > **Mappa del sito XML**.

| Nome | Percorso di configurazione | Solo commercio? |
|--------------|--------------|--------------|
| Frequenza | `sitemap/category/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Priorità | `sitemap/category/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequenza | `sitemap/product/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Priorità | `sitemap/product/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aggiungi immagini a mappa del sito | `sitemap/product/image_include` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequenza | `sitemap/page/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Priorità | `sitemap/page/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `sitemap/generate/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ora di inizio | `sitemap/generate/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequenza | `sitemap/generate/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Errore mittente e-mail | `sitemap/generate/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail errore | `sitemap/generate/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Numero massimo di URL per file | `sitemap/limit/max_lines` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Dimensione massima del file | `sitemap/limit/max_file_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita invio a Robots.txt | `sitemap/search_engines/submission_robots` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Percorsi feed RSS

Questi valori di configurazione sono disponibili in Amministratore in **Negozi** > Impostazioni > **Configurazione** > **Catalogo** > **Feed RSS**.

| Nome | Percorso di configurazione | Solo commercio? |
|--------------|--------------|--------------|
| Attiva RSS | `rss/config/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Attiva RSS | `rss/wishlist/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuovi prodotti | `rss/catalog/new` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prodotti speciali | `rss/catalog/special` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Coupon/Sconti | `rss/catalog/discounts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Categoria di livello principale | `rss/catalog/category` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Notifica stato ordine cliente | `rss/order/status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}

## Invia un&#39;e-mail a percorsi amici

Questi valori di configurazione sono disponibili in Amministratore in **Negozi** > Impostazioni > **Configurazione** > **Catalogo** > **Invia un&#39;e-mail a un amico**.

| Nome | Percorso di configurazione | Solo commercio? |
|--------------|--------------|--------------|
| Abilitato | `sendfriend/email/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Seleziona modello e-mail | `sendfriend/email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Consenti ospiti | `sendfriend/email/allow_guest` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Destinatari massimi | `sendfriend/email/max_recipients` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Numero massimo di prodotti inviati in 1 ora | `sendfriend/email/max_per_hour` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limita invio per | `sendfriend/email/check_by` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style=&quot;table-layout:auto&quot;}
