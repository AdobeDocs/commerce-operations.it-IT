---
title: Riferimento percorsi configurazione vendite
description: Visualizza un elenco di valori di configurazione vendite.
feature: Configuration, Checkout, Gift, Shipping/Delivery, Taxes
exl-id: 7981f78a-5e5f-422c-9bff-54022e1fb9f3
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '1473'
ht-degree: 0%

---

# Riferimento percorsi configurazione vendite

In questa sezione sono elencati i nomi delle variabili e i percorsi di configurazione disponibili per le opzioni dell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Vendite**.

Il comando [`magento app:config:dump`](../cli/export-configuration.md) scrive questi valori nel file di configurazione condiviso, `app/etc/config.php`, che deve trovarsi nel controllo del codice sorgente. Per ignorare eventuali impostazioni di configurazione o per impostare impostazioni sensibili, vedere [Utilizzare le variabili di ambiente per ignorare le impostazioni di configurazione](override-config-settings.md#environment-variables). Questo argomento _non_ elenca [valori sensibili e specifici del sistema](config-reference-sens.md).

## Percorsi di vendita

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Vendite** > **Vendite**.

| Nome | Percorso configurazione | Solo Commerce? |
|--------------|--------------|--------------|
| Nascondi IP cliente | `sales/general/hide_customer_ip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Subtotale | `sales/totals_sort/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Sconto | `sales/totals_sort/discount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Spedizione | `sales/totals_sort/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Imposta | `sales/totals_sort/tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Imposta Prodotto Fissa | `sales/totals_sort/weee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale complessivo | `sales/totals_sort/grand_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Biglietti regalo | `sales/totals_sort/giftcardaccount` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Credito store | `sales/totals_sort/customerbalance` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Consenti riordino | `sales/reorder/allow` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Logo per stampe PDF (200x50) | `sales/identity/logo` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Logo per la visualizzazione Stampa di HTML | `sales/identity/logo_html` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Indirizzo | `sales/identity/address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita | `sales/minimum_order/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Importo minimo | `sales/minimum_order/amount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Includi imposta in importo | `sales/minimum_order/tax_including` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Messaggio descrizione | `sales/minimum_order/description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Errore da visualizzare nel carrello | `sales/minimum_order/error_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Convalida ogni indirizzo separatamente nel Check-Out con più indirizzi | `sales/minimum_order/multi_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Messaggio di descrizione per più indirizzi | `sales/minimum_order/multi_address_description` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Errore con più indirizzi da visualizzare nel carrello | `sales/minimum_order/multi_address_error_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usa dati aggregati | `sales/dashboard/use_aggregated_data` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durata ordine di pagamento in sospeso (minuti) | `sales/orders/delete_pending_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Consenti messaggi regalo a livello di ordine | `sales/gift_options/allow_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Consenti messaggi regalo per articoli ordine | `sales/gift_options/allow_items` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Consenti confezione regalo a livello di ordine | `sales/gift_options/wrapping_allow_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Consenti confezione regalo per articoli ordine | `sales/gift_options/wrapping_allow_items` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Consenti ricevuta regalo | `sales/gift_options/allow_gift_receipt` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Consenti scheda stampata | `sales/gift_options/allow_printed_card` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Prezzo predefinito per la carta stampata | `sales/gift_options/printed_card_price` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilita MAP | `sales/msrp/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizza prezzo effettivo | `sales/msrp/display_price_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Messaggio di testo popup predefinito | `sales/msrp/explanation_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Messaggio di testo predefinito | `sales/msrp/explanation_message_whats_this` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita Ordina per SKU sul mio account in Storefront | `sales/product_sku/my_account_enable` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilitato | `sales/instant_purchase/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Testo pulsante | `sales/instant_purchase/button_text` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gruppi di clienti | `sales/product_sku/allowed_groups` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilita archiviazione | `sales/magento_salesarchive/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Archivia ordini acquistati | `sales/magento_salesarchive/age` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Stati ordine da archiviare | `sales/magento_salesarchive/order_statuses` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilita RMA su Storefront | `sales/magento_rma/enabled` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilita RMA a livello di prodotto | `sales/magento_rma/enabled_on_product` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Usa indirizzo store | `sales/magento_rma/use_store_address` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |

{style="table-layout:auto"}

## Percorsi e-mail vendite

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Vendite** > **E-mail vendite**.

| Nome | Percorso configurazione | Solo Commerce? |
|--------------|--------------|--------------|
| Invio asincrono | `sales_email/general/async_sending` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `sales_email/order/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mittente e-mail di conferma nuovo ordine | `sales_email/order/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuovo modello di conferma ordine | `sales_email/order/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuovo modello di conferma ordine per ospite | `sales_email/order/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Metodo di invio copia e-mail ordine | `sales_email/order/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `sales_email/order_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mittente e-mail commento ordine | `sales_email/order_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail commento ordine | `sales_email/order_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail commenti ordine per ospite | `sales_email/order_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Invia commenti ordine metodo di copia e-mail | `sales_email/order_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `sales_email/invoice/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mittente e-mail fattura | `sales_email/invoice/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail fattura | `sales_email/invoice/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail fattura per ospite | `sales_email/invoice/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Metodo di invio copia e-mail fattura | `sales_email/invoice/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `sales_email/invoice_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mittente e-mail commento fattura | `sales_email/invoice_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail commento fattura | `sales_email/invoice_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail commento fattura per ospite | `sales_email/invoice_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Invia commenti fattura metodo di copia e-mail | `sales_email/invoice_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `sales_email/shipment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mittente e-mail spedizione | `sales_email/shipment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail spedizione | `sales_email/shipment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail spedizione per ospite | `sales_email/shipment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Metodo di invio copia e-mail spedizione | `sales_email/shipment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `sales_email/shipment_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mittente e-mail commento spedizione | `sales_email/shipment_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail commento spedizione | `sales_email/shipment_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail per commento spedizione per ospite | `sales_email/shipment_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Invia commenti spedizione metodo di copia e-mail | `sales_email/shipment_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `sales_email/creditmemo/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mittente e-mail nota di credito | `sales_email/creditmemo/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail nota di credito | `sales_email/creditmemo/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail nota di credito per ospite | `sales_email/creditmemo/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Metodo di invio copia e-mail per nota di credito | `sales_email/creditmemo/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `sales_email/creditmemo_comment/enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mittente e-mail per commento nota di credito | `sales_email/creditmemo_comment/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail per commento nota di credito | `sales_email/creditmemo_comment/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail per commento nota di credito per ospite | `sales_email/creditmemo_comment/guest_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Invia commenti nota di credito metodo di copia e-mail | `sales_email/creditmemo_comment/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `sales_email/magento_rma/enabled` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Mittente e-mail RMA | `sales_email/magento_rma/identity` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Modello e-mail RMA | `sales_email/magento_rma/template` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Modello e-mail RMA per ospite | `sales_email/magento_rma/guest_template` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Metodo di invio copia e-mail RMA | `sales_email/magento_rma/copy_method` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilitato | `sales_email/magento_rma_auth/enabled` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Mittente e-mail autorizzazione RMA | `sales_email/magento_rma_auth/identity` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Modello e-mail autorizzazione RMA | `sales_email/magento_rma_auth/template` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Modello e-mail di autorizzazione RMA per ospite | `sales_email/magento_rma_auth/guest_template` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Metodo di copia e-mail per l’invio dell’autorizzazione RMA | `sales_email/magento_rma_auth/copy_method` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilitato | `sales_email/magento_rma_comment/enabled` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Mittente e-mail commento RMA | `sales_email/magento_rma_comment/identity` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Modello e-mail commenti RMA | `sales_email/magento_rma_comment/template` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Modello e-mail commenti RMA per ospite | `sales_email/magento_rma_comment/guest_template` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Metodo di invio copia e-mail RMA | `sales_email/magento_rma_comment/copy_method` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilitato | `sales_email/magento_rma_customer_comment/enabled` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Mittente e-mail commento RMA | `sales_email/magento_rma_customer_comment/identity` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Destinatario e-mail commento RMA | `sales_email/magento_rma_customer_comment/recipient` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Modello e-mail commenti RMA | `sales_email/magento_rma_customer_comment/template` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Metodo di invio copia e-mail RMA | `sales_email/magento_rma_customer_comment/copy_method` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Visualizza ID ordine nell’intestazione | `sales_pdf/invoice/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizza ID ordine nell’intestazione | `sales_pdf/shipment/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizza ID ordine nell’intestazione | `sales_pdf/creditmemo/put_order_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Percorsi imposta

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Vendite** > **Imposta**.

| Nome | Percorso configurazione | Solo Commerce? |
|--------------|--------------|--------------|
| Classe imposta per la spedizione | `tax/classes/shipping_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Classe imposta per le opzioni regalo | `tax/classes/wrapping_tax_class` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Classe imposta predefinita per prodotto | `tax/classes/default_product_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Classe imposta predefinita per il cliente | `tax/classes/default_customer_tax_class` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Metodo di calcolo delle imposte basato su | `tax/calculation/algorithm` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calcolo delle imposte basato su | `tax/calculation/based_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prezzi catalogo | `tax/calculation/price_includes_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prezzi di spedizione | `tax/calculation/shipping_includes_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Applica imposta cliente | `tax/calculation/apply_after_discount` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Applica sconto sui prezzi | `tax/calculation/discount_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Applica imposta su | `tax/calculation/apply_tax_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitare il commercio transfrontaliero | `tax/calculation/cross_border_trade_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Paese predefinito | `tax/defaults/country` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato predefinito | `tax/defaults/region` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Codice Post predefinito | `tax/defaults/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizza Prezzi Prodotto Nel Catalogo | `tax/display/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizza prezzi di spedizione | `tax/display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizza prezzi | `tax/cart_display/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizza subtotale | `tax/cart_display/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizza importo spedizione | `tax/cart_display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizza prezzi per confezione regalo | `tax/cart_display/gift_wrapping` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Visualizza prezzi delle carte stampate | `tax/cart_display/printed_card` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Includi l&#39;imposta nel totale ordine | `tax/cart_display/grandtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizza riepilogo imposte completo | `tax/cart_display/full_summary` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizza subtotale imposte pari a zero | `tax/cart_display/zero_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizza prezzi | `tax/sales_display/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizza subtotale | `tax/sales_display/subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizza importo spedizione | `tax/sales_display/shipping` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizza prezzi per confezione regalo | `tax/sales_display/gift_wrapping` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Visualizza prezzi delle carte stampate | `tax/sales_display/printed_card` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Includi l&#39;imposta nel totale ordine | `tax/sales_display/grandtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizza riepilogo imposte completo | `tax/sales_display/full_summary` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizza subtotale imposte pari a zero | `tax/sales_display/zero_tax` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita FPT | `tax/weee/enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizza Prezzi In Elenchi Prodotti | `tax/weee/display_list` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizza Prezzi Nella Pagina Di Visualizzazione Del Prodotto | `tax/weee/display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizza Prezzi In Moduli Di Vendita | `tax/weee/display_sales` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostra Prezzi Nelle E-Mail | `tax/weee/display_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Applica imposta a FPT | `tax/weee/apply_vat` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Includi FPT nel subtotale | `tax/weee/include_in_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Percorsi di checkout

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Vendite** > **Pagamento**.

| Nome | Percorso configurazione | Solo Commerce? |
|--------------|--------------|--------------|
| Abilita estrazione pagina iniziale | `checkout/options/onepage_checkout_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Consenti estrazione come ospite | `checkout/options/guest_checkout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizza indirizzo di fatturazione attivato | `checkout/options/display_billing_address_on` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita termini e condizioni | `checkout/options/enable_agreements` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durata offerta (giorni) | `checkout/cart/delete_quote_after` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Dopo l’aggiunta di un reindirizzamento prodotto al carrello | `checkout/cart/redirect_to_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Immagine prodotto raggruppato | `checkout/cart/grouped_product_image` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Immagine del prodotto configurabile | `checkout/cart/configurable_product_image` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Anteprima durata offerta (minuti) | `checkout/cart/preview_quota_lifetime` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Visualizza riepilogo carrello | `checkout/cart_link/use_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizza barra laterale carrello | `checkout/sidebar/display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Numero massimo di elementi aggiunti di recente | `checkout/sidebar/count` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mittente e-mail per pagamento non riuscito | `checkout/payment_failed/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Destinatario e-mail per pagamento non riuscito | `checkout/payment_failed/receiver` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello per pagamento non riuscito | `checkout/payment_failed/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Metodo di copia e-mail per invio pagamento non riuscito | `checkout/payment_failed/copy_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Percorsi delle impostazioni di spedizione

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Vendite** > **Impostazioni spedizione**.

| Nome | Percorso configurazione | Solo Commerce? |
|--------------|--------------|--------------|
| Applica criteri di spedizione personalizzati | `shipping/shipping_policy/enable_shipping_policy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Politica di spedizione | `shipping/shipping_policy/shipping_policy_content` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Percorsi di impostazioni multidimensionali

Questi valori di configurazione sono disponibili nell&#39;Admin in **Archivi** > Impostazioni > **Configurazione** > **Vendite** > **Impostazioni di multipipping**.

| Nome | Percorso configurazione | Solo Commerce? |
|--------------|--------------|--------------|
| Consenti spedizione a più indirizzi | `multishipping/options/checkout_multiple` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Quantità massima consentita per la spedizione a più indirizzi | `multishipping/options/checkout_multiple_maximum_qty` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Percorsi dei metodi di consegna

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Vendite** > **Metodi di consegna**.

| Nome | Percorso configurazione | Solo Commerce? |
|--------------|--------------|--------------|
| Abilitato | `carriers/flatrate/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `carriers/flatrate/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nome metodo | `carriers/flatrate/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo | `carriers/flatrate/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prezzo | `carriers/flatrate/price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calcola commissione di imballaggio | `carriers/flatrate/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Spese di imballaggio | `carriers/flatrate/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Messaggio di errore visualizzato | `carriers/flatrate/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Spedisci a paesi applicabili | `carriers/flatrate/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Spedisci a paesi specifici | `carriers/flatrate/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostra metodo se non applicabile | `carriers/flatrate/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `carriers/flatrate/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `carriers/freeshipping/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `carriers/freeshipping/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nome metodo | `carriers/freeshipping/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Importo minimo ordine | `carriers/freeshipping/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Messaggio di errore visualizzato | `carriers/freeshipping/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Spedisci a paesi applicabili | `carriers/freeshipping/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Spedisci a paesi specifici | `carriers/freeshipping/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostra metodo se non applicabile | `carriers/freeshipping/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `carriers/freeshipping/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `carriers/tablerate/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `carriers/tablerate/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nome metodo | `carriers/tablerate/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Condizione | `carriers/tablerate/condition_name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Includi prodotti virtuali nel calcolo del prezzo | `carriers/tablerate/include_virtual_price` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Esporta | `carriers/tablerate/export` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Importa | `carriers/tablerate/import` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calcola commissione di imballaggio | `carriers/tablerate/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Spese di imballaggio | `carriers/tablerate/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Messaggio di errore visualizzato | `carriers/tablerate/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Spedisci a paesi applicabili | `carriers/tablerate/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Spedisci a paesi specifici | `carriers/tablerate/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostra metodo se non applicabile | `carriers/tablerate/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `carriers/tablerate/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato per l&#39;estrazione | `carriers/ups/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato per RMA | `carriers/ups/active_rma` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipo di UPS | `carriers/ups/type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modalità | `carriers/ups/mode_xml` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Origine della spedizione | `carriers/ups/origin_shipment` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| URL gateway | `carriers/ups/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `carriers/ups/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita tassi negoziati | `carriers/ups/negotiated_active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo di richiesta pacchetti | `carriers/ups/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Contenitore | `carriers/ups/container` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Unità di peso | `carriers/ups/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo di destinazione | `carriers/ups/dest_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Peso massimo del pacchetto (consultare il vettore di spedizione per conoscere il peso massimo supportato) | `carriers/ups/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Metodo di prelievo | `carriers/ups/pickup` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Peso minimo del pacchetto (consultare il vettore di spedizione per conoscere il peso minimo supportato) | `carriers/ups/min_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calcola commissione di imballaggio | `carriers/ups/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gestione applicata | `carriers/ups/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Spese di imballaggio | `carriers/ups/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Metodi consentiti | `carriers/ups/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Metodo Free | `carriers/ups/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita soglia spedizione gratuita | `carriers/ups/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Soglia importo spedizione gratuita | `carriers/ups/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Messaggio di errore visualizzato | `carriers/ups/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Spedisci a paesi applicabili | `carriers/ups/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Spedisci a paesi specifici | `carriers/ups/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostra metodo se non applicabile | `carriers/ups/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `carriers/ups/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato per l&#39;estrazione | `carriers/usps/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato per RMA | `carriers/usps/active_rma` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Modalità | `carriers/usps/mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo di richiesta pacchetti | `carriers/usps/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Contenitore | `carriers/usps/container` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Dimensione | `carriers/usps/size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lunghezza | `carriers/usps/length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Larghezza | `carriers/usps/width` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Altezza | `carriers/usps/height` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Girth | `carriers/usps/girth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lavorabile | `carriers/usps/machinable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Peso massimo del pacchetto (consultare il vettore di spedizione per conoscere il peso massimo supportato) | `carriers/usps/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calcola commissione di imballaggio | `carriers/usps/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gestione applicata | `carriers/usps/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Spese di imballaggio | `carriers/usps/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Metodi consentiti | `carriers/usps/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Metodo Free | `carriers/usps/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita soglia spedizione gratuita | `carriers/usps/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Soglia importo spedizione gratuita | `carriers/usps/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Messaggio di errore visualizzato | `carriers/usps/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Spedisci a paesi applicabili | `carriers/usps/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Spedisci a paesi specifici | `carriers/usps/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Debug | `carriers/usps/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostra metodo se non applicabile | `carriers/usps/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `carriers/usps/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato per l&#39;estrazione | `carriers/fedex/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato per RMA | `carriers/fedex/active_rma` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `carriers/fedex/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| URL servizi Web (produzione) | `carriers/fedex/production_webservices_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| URL dei servizi web (sandbox) | `carriers/fedex/sandbox_webservices_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo di richiesta pacchetti | `carriers/fedex/shipment_requesttype` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Imballaggio | `carriers/fedex/packaging` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Dropoff | `carriers/fedex/dropoff` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Unità di peso | `carriers/fedex/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Peso massimo del pacchetto (consultare il vettore di spedizione per conoscere il peso massimo supportato) | `carriers/fedex/max_package_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calcola commissione di imballaggio | `carriers/fedex/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gestione applicata | `carriers/fedex/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Spese di imballaggio | `carriers/fedex/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Consegna residenziale | `carriers/fedex/residence_delivery` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Metodi consentiti | `carriers/fedex/allowed_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ID hub | `carriers/fedex/smartpost_hubid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Metodo Free | `carriers/fedex/free_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita soglia spedizione gratuita | `carriers/fedex/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Soglia importo spedizione gratuita | `carriers/fedex/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Messaggio di errore visualizzato | `carriers/fedex/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Spedisci a paesi applicabili | `carriers/fedex/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Spedisci a paesi specifici | `carriers/fedex/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Debug | `carriers/fedex/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostra metodo se non applicabile | `carriers/fedex/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `carriers/fedex/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato per l&#39;estrazione | `carriers/dhl/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato per RMA | `carriers/dhl/active_rma` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `carriers/dhl/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo di contenuto | `carriers/dhl/content_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Calcola commissione di imballaggio | `carriers/dhl/handling_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Gestione applicata | `carriers/dhl/handling_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Spese di imballaggio | `carriers/dhl/handling_fee` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Dividi peso ordine | `carriers/dhl/divide_order_weight` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Unità di peso | `carriers/dhl/unit_of_measure` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Dimensione | `carriers/dhl/size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Altezza | `carriers/dhl/height` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Profondità | `carriers/dhl/depth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Larghezza | `carriers/dhl/width` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Metodi consentiti | `carriers/dhl/doc_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Metodi consentiti | `carriers/dhl/nondoc_methods` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tempo di preparazione | `carriers/dhl/ready_time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Messaggio di errore visualizzato | `carriers/dhl/specificerrmsg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Metodo Free | `carriers/dhl/free_method_doc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Metodo Free | `carriers/dhl/free_method_nondoc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita soglia spedizione gratuita | `carriers/dhl/free_shipping_enable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Soglia importo spedizione gratuita | `carriers/dhl/free_shipping_subtotal` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Spedisci a paesi applicabili | `carriers/dhl/sallowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Spedisci a paesi specifici | `carriers/dhl/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostra metodo se non applicabile | `carriers/dhl/showmethod` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `carriers/dhl/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Percorsi API Google

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Vendite** > **API Google**.

| Nome | Percorso configurazione | Solo Commerce? |
|--------------|--------------|--------------|
| Abilita | `google/analytics/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo di account | `google/analytics/type` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilita esperimenti sui contenuti | `google/analytics/experiments` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Proprietà elenco per la pagina del catalogo | `google/analytics/catalog_page_list_value` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Proprietà elenco per il blocco di cross-selling | `google/analytics/crosssell_block_list_value` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Proprietà elenco per il blocco up-sell | `google/analytics/upsell_block_list_value` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Proprietà elenco per il blocco prodotti correlati | `google/analytics/related_block_list_value` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Proprietà elenco per la pagina dei risultati di ricerca | `google/analytics/search_page_list_value` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| &#39;Promozioni interne&#39; per il campo &quot;Etichetta&quot; delle promozioni. | `google/analytics/promotions_list_value` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilita | `google/adwords/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ID conversione | `google/adwords/conversion_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lingua di conversione | `google/adwords/conversion_language` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Formato di conversione | `google/adwords/conversion_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Colore conversione | `google/adwords/conversion_color` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Etichetta di conversione | `google/adwords/conversion_label` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipo di valore di conversione | `google/adwords/conversion_value_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valore di conversione | `google/adwords/conversion_value` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Percorsi carte regalo

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Vendite** > **Biglietti regalo**.

| Nome | Percorso configurazione | Solo Commerce? |
|--------------|--------------|--------------|
| Mittente e-mail di notifica gift card | `giftcard/email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello e-mail di notifica gift card | `giftcard/email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rimborsabile | `giftcard/general/is_redeemable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Durata (giorni) | `giftcard/general/lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Consenti messaggio regalo | `giftcard/general/allow_message` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lunghezza massima messaggio regalo | `giftcard/general/message_max_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Genera conto gift card quando l&#39;ordine è | `giftcard/general/order_item_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mittente e-mail gift card | `giftcard/giftcardaccount_email/identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Modello gift card | `giftcard/giftcardaccount_email/template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Lunghezza codice | `giftcard/giftcardaccount_general/code_length` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Formato del codice | `giftcard/giftcardaccount_general/code_format` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Prefisso codice | `giftcard/giftcardaccount_general/code_prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Suffisso codice | `giftcard/giftcardaccount_general/code_suffix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Trattino Ogni X Caratteri | `giftcard/giftcardaccount_general/code_split` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Nuova dimensione pool | `giftcard/giftcardaccount_general/pool_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Soglia pool di codici bassa | `giftcard/giftcardaccount_general/pool_threshold` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}
