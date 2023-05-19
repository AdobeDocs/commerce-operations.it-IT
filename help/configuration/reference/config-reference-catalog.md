---
title: Riferimento percorsi di configurazione catalogo
description: Consulta un elenco di valori di configurazione del catalogo.
exl-id: 19451443-228e-437d-a3eb-7dc968b9fb0d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 0%

---

# Riferimento percorsi di configurazione catalogo

In questa sezione sono elencati i nomi delle variabili e i percorsi di configurazione disponibili per le opzioni in Admin (Amministrazione) in **Negozi** > Impostazioni > **Configurazione** > **Catalogo**.

Il [`magento app:config:dump` comando](../cli/export-configuration.md) scrive questi valori nel file di configurazione condiviso, `app/etc/config.php`, che deve trovarsi nel controllo del codice sorgente. Per ignorare eventuali impostazioni di configurazione o per impostare impostazioni sensibili, vedi [Utilizzare le variabili di ambiente per ignorare le impostazioni di configurazione](override-config-settings.md#environment-variables). Questo argomento fa _non_ list [valori sensibili e specifici del sistema](config-reference-sens.md).

## Percorsi catalogo

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Catalogo** > **Catalogo**.

| Nome | Percorso configurazione | Solo Commerce? |
|--------------|--------------|--------------|
| Maschera per SKU | `catalog/fields_masks/sku` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maschera per metatitolo | `catalog/fields_masks/meta_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maschera per parole chiave meta | `catalog/fields_masks/meta_keyword` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Maschera per descrizione metadati | `catalog/fields_masks/meta_description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modalità elenco | `catalog/frontend/list_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prodotti per pagina sulla griglia valori consentiti | `catalog/frontend/grid_per_page_values` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prodotti per pagina sulla griglia Valore predefinito | `catalog/frontend/grid_per_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prodotti per pagina nell’elenco dei valori consentiti | `catalog/frontend/list_per_page_values` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prodotti per pagina nell’elenco Valore predefinito | `catalog/frontend/list_per_page` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Elenco prodotti Ordina per | `catalog/frontend/default_sort_by` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Consenti tutti i prodotti per pagina | `catalog/frontend/list_allow_all` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usa categoria catalogo semplice | `catalog/frontend/flat_catalog_category` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usa prodotto catalogo semplice | `catalog/frontend/flat_catalog_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Campioni per prodotto | `catalog/frontend/swatches_per_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Consenti agli ospiti di scrivere recensioni | `catalog/review/allow_guest` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Consenti avviso quando il prezzo del prodotto cambia | `catalog/productalert/allow_price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail avviso prezzo | `catalog/productalert/email_price_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Consenti avviso quando il prodotto torna disponibile | `catalog/productalert/allow_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail avviso magazzino | `catalog/productalert/email_stock_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mittente e-mail avviso | `catalog/productalert/email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequenza | `catalog/productalert_cron/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ora di inizio | `catalog/productalert_cron/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Errore mittente e-mail | `catalog/productalert_cron/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail per errore | `catalog/productalert_cron/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostra per corrente | `catalog/recently_products/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Conteggio predefinito dei prodotti visualizzati di recente | `catalog/recently_products/viewed_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Conteggio predefinito dei prodotti confrontati di recente | `catalog/recently_products/compared_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Video di base con avvio automatico | `catalog/product_video/play_if_base` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostra video correlato | `catalog/product_video/show_related` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Riavvia automaticamente il video | `catalog/product_video/video_auto_restart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ambito prezzo catalogo | `catalog/price/scope` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prezzo del prodotto predefinito | `catalog/price/default_product_price` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Visualizza il conteggio dei prodotti | `catalog/layered_navigation/display_product_count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calcolo passaggio di navigazione prezzo | `catalog/layered_navigation/price_range_calculation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Passaggio di navigazione prezzo predefinito | `catalog/layered_navigation/price_range_step` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizza intervallo di prezzo come un solo prezzo | `catalog/layered_navigation/one_price_interval` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Numero massimo di intervalli di prezzo | `catalog/layered_navigation/price_range_max_intervals` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limite divisione intervallo | `catalog/layered_navigation/interval_division_limit` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Profondità massima | `catalog/navigation/max_depth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lunghezza minima query | `catalog/search/min_query_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lunghezza massima query | `catalog/search/max_query_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Motore di ricerca | `catalog/search/engine` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Timeout server Solr | `catalog/search/solr_server_timeout` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Modalità indicizzazione | `catalog/search/engine_commit_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita suggerimenti di ricerca | `catalog/search/search_suggestion_enabled` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Conteggio suggerimenti di ricerca | `catalog/search/search_suggestion_count` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Mostra conteggio risultati per ogni suggerimento | `catalog/search/search_suggestion_count_results_enabled` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilita Recommendations di ricerca | `catalog/search/search_recommendations_enabled` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Conteggio Recommendations di ricerca | `catalog/search/search_recommendations_count` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Mostra il conteggio dei risultati per ogni consiglio | `catalog/search/search_recommendations_count_results_enabled` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Condizioni minime da rispettare | `catalog/search/minimum_should_match` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Genera riscritture URL &quot;categoria/prodotto&quot; | `catalog/seo/generate_category_product_rewrites` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Termini di ricerca popolari | `catalog/seo/search_terms` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Suffisso URL prodotto | `catalog/seo/product_url_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Suffisso URL categoria | `catalog/seo/category_url_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usa il percorso delle categorie per gli URL dei prodotti | `catalog/seo/product_use_categories` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Crea un reindirizzamento permanente per gli URL se la chiave URL è stata modificata | `catalog/seo/save_rewrites_history` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Separatore titolo pagina | `catalog/seo/title_separator` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usa tag meta collegamento canonico per le categorie | `catalog/seo/category_canonical_tag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usa tag meta collegamento canonico per i prodotti | `catalog/seo/product_canonical_tag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita | `catalog/magento_catalogpermissions/enabled` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Consenti esplorazione categoria | `catalog/magento_catalogpermissions/grant_catalog_category_view` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Gruppi di clienti | `catalog/magento_catalogpermissions/grant_catalog_category_view_groups` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagina di destinazione | `catalog/magento_catalogpermissions/restricted_landing_page` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Visualizza prezzi prodotto | `catalog/magento_catalogpermissions/grant_catalog_product_price` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Gruppi di clienti | `catalog/magento_catalogpermissions/grant_catalog_product_price_groups` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Consenti aggiunta al carrello | `catalog/magento_catalogpermissions/grant_checkout_items` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Gruppi di clienti | `catalog/magento_catalogpermissions/grant_checkout_items_groups` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Non consentire ricerca nel catalogo per | `catalog/magento_catalogpermissions/deny_catalog_search` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Stato articolo ordine per abilitare i download | `catalog/downloadable/order_item_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Numero massimo predefinito di download | `catalog/downloadable/downloads_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Condivisibile | `catalog/downloadable/shareable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo campione predefinito | `catalog/downloadable/samples_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo collegamento predefinito | `catalog/downloadable/links_title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Apri collegamenti in una nuova finestra | `catalog/downloadable/links_target_new_window` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Utilizza Content-Disposition | `catalog/downloadable/content_disposition` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Disattiva estrazione guest se il carrello contiene elementi scaricabili | `catalog/downloadable/disable_guest_checkout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usa calendario JavaScript | `catalog/custom_options/use_calendar` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordine campi data | `catalog/custom_options/date_fields_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Formato ora | `catalog/custom_options/time_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Intervallo di anni | `catalog/custom_options/year_range` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita funzionalità eventi catalogo | `catalog/magento_catalogevent/enabled` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilita widget eventi catalogo in Storefront | `catalog/magento_catalogevent/lister_output` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Numero di eventi da visualizzare nel widget Cursore eventi | `catalog/magento_catalogevent/lister_widget_limit` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Eventi da scorrere per clic nel widget Cursore eventi | `catalog/magento_catalogevent/lister_widget_scroll` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Numero massimo di prodotti nell’elenco dei prodotti correlati | `catalog/magento_targetrule/related_position_limit` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Mostra prodotti correlati | `catalog/magento_targetrule/related_position_behavior` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Modalità di rotazione per i prodotti nell&#39;elenco prodotti correlati | `catalog/magento_targetrule/related_rotation_mode` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Numero massimo di prodotti nell&#39;elenco dei prodotti di cross-selling | `catalog/magento_targetrule/crosssell_position_limit` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Mostra prodotti di cross-selling | `catalog/magento_targetrule/crosssell_position_behavior` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Modalità di rotazione per i prodotti nell’elenco dei prodotti di cross-selling | `catalog/magento_targetrule/crosssell_rotation_mode` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Numero massimo di prodotti nell&#39;elenco dei prodotti di upselling | `catalog/magento_targetrule/upsell_position_limit` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Mostra prodotti di upselling | `catalog/magento_targetrule/upsell_position_behavior` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Modalità di rotazione per i prodotti nell’elenco dei prodotti di upselling | `catalog/magento_targetrule/upsell_rotation_mode` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Percorsi inventario

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Catalogo** > **Inventario**.

| Nome | Percorso configurazione | Solo Commerce? |
|--------------|--------------|--------------|
| Diminuisci scorte al momento dell&#39;ordine | `cataloginventory/options/can_subtract` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Imposta lo stato articoli in magazzino quando l&#39;ordine viene annullato | `cataloginventory/options/can_back_in_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizza prodotti esauriti | `cataloginventory/options/show_out_of_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Solo X soglia sinistra | `cataloginventory/options/stock_threshold_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizza la disponibilità dei prodotti in magazzino su Storefront | `cataloginventory/options/display_product_stock_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sincronizza con catalogo | `cataloginventory/options/synchronize_with_catalog` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Gestisci Stock | `cataloginventory/item_options/manage_stock` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordini arretrati | `cataloginventory/item_options/backorders` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usa aggiornamento azioni differite | `cataloginventory/item_options/use_deferred_stock_update` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Quantità massima consentita nel carrello | `cataloginventory/item_options/max_sale_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Soglia esaurita | `cataloginventory/item_options/min_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Quantità minima consentita nel carrello | `cataloginventory/item_options/min_sale_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Notifica per quantità inferiore | `cataloginventory/item_options/notify_stock_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita incrementi quantità | `cataloginventory/item_options/enable_qty_increments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Incrementi quantità | `cataloginventory/item_options/qty_increments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Restituisci automaticamente articolo nota di accredito alle scorte | `cataloginventory/item_options/auto_return` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Esegui in modo asincrono | `cataloginventory/bulk_operations/async` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Dimensione batch asincrono | `cataloginventory/bulk_operations/batch_size` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Provider | `cataloginventory/source_selection_distance_based/provider` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modalità di calcolo | `cataloginventory/source_selection_distance_based_google/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valore | `cataloginventory/source_selection_distance_based_google/value` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Percorsi di Visual Merchandiser

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Catalogo** > **Visual Merchandiser**.

| Nome | Percorso configurazione | Solo Commerce? |
|--------------|--------------|--------------|
| Attributi visibili per le regole di categoria | `visualmerchandiser/options/smart_attributes` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Soglia minima scorte | `visualmerchandiser/options/minimum_stock_threshold` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Codice attributo colore | `visualmerchandiser/options/color_attribute_code` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordine colori | `visualmerchandiser/options/color_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Percorsi sitemap XML

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Catalogo** > **XML Sitemap**.

| Nome | Percorso configurazione | Solo Commerce? |
|--------------|--------------|--------------|
| Frequenza | `sitemap/category/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Priorità | `sitemap/category/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequenza | `sitemap/product/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Priorità | `sitemap/product/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aggiungi immagini in Sitemap | `sitemap/product/image_include` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequenza | `sitemap/page/changefreq` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Priorità | `sitemap/page/priority` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `sitemap/generate/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ora di inizio | `sitemap/generate/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Frequenza | `sitemap/generate/frequency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Errore mittente e-mail | `sitemap/generate/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail per errore | `sitemap/generate/error_email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Numero massimo di URL per file | `sitemap/limit/max_lines` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Dimensione massima file | `sitemap/limit/max_file_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita invio a robot.txt | `sitemap/search_engines/submission_robots` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Percorsi feed RSS

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Catalogo** > **Feed RSS**.

| Nome | Percorso configurazione | Solo Commerce? |
|--------------|--------------|--------------|
| Abilita RSS | `rss/config/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita RSS | `rss/wishlist/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuovi prodotti | `rss/catalog/new` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prodotti speciali | `rss/catalog/special` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Coupon/sconti | `rss/catalog/discounts` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Categoria di primo livello | `rss/catalog/category` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Notifica stato ordine cliente | `rss/order/status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Percorsi per l’e-mail a un amico

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Catalogo** > **E-mail a un amico**.

| Nome | Percorso configurazione | Solo Commerce? |
|--------------|--------------|--------------|
| Abilitato | `sendfriend/email/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Seleziona modello e-mail | `sendfriend/email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Consenti agli ospiti | `sendfriend/email/allow_guest` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Numero massimo destinatari | `sendfriend/email/max_recipients` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Numero massimo di prodotti inviati in 1 ora | `sendfriend/email/max_per_hour` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Limita invio per | `sendfriend/email/check_by` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
