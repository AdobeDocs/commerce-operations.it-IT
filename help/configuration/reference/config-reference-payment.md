---
title: Riferimento ai percorsi di configurazione dei pagamenti
description: Consulta un elenco di valori del metodo di pagamento configurabile.
feature: Configuration, Payments
exl-id: f3e356aa-7262-4d99-9ed4-d77cbd93708c
source-git-commit: 16e9396f19693436dfc7bdac78d84624a78f0c21
workflow-type: tm+mt
source-wordcount: '4100'
ht-degree: 0%

---

# Riferimento ai percorsi di configurazione dei pagamenti

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Vendite** > **Metodi di pagamento**.

Il [`magento app:config:dump` comando](../cli/export-configuration.md) scrive questi valori nel file di configurazione condiviso, `app/etc/config.php`, che deve trovarsi nel controllo del codice sorgente. Per ignorare eventuali impostazioni di configurazione o per impostare impostazioni sensibili, vedi [Utilizzare le variabili di ambiente per ignorare le impostazioni di configurazione](override-config-settings.md#environment-variables). Questo argomento fa _non_ list [valori sensibili e specifici del sistema](config-reference-sens.md).

Le impostazioni sono ulteriormente organizzate per metodo di pagamento.

## Percorsi PayPal

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? |
|--------------|--------------|--------------|--------------|
| Abilita questa soluzione | `payment/payflowpro/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita esperienza di estrazione nel contesto | `payment/paypal_express/in_context` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita credito PayPal | `payment/payflow_express_bml/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita credito PayPal | `payment/paypal_express_bml/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizzazione | `payment/paypal_express_bml/homepage_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Posizione | `payment/paypal_express_bml/homepage_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Dimensione | `payment/paypal_express_bml/homepage_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizzazione | `payment/paypal_express_bml/categorypage_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Posizione | `payment/paypal_express_bml/categorypage_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Dimensione | `payment/paypal_express_bml/categorypage_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizzazione | `payment/paypal_express_bml/productpage_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Posizione | `payment/paypal_express_bml/productpage_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Dimensione | `payment/paypal_express_bml/productpage_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizzazione | `payment/paypal_express_bml/checkout_display` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Posizione | `payment/paypal_express_bml/checkout_position` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Dimensione | `payment/paypal_express_bml/checkout_size` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizza nella pagina Dettagli prodotto | `payment/payflow_express/visible_on_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostra sul carrello | `payment/payflow_express/visible_on_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento applicabile da | `payment/payflow_express/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento paesi applicabile da | `payment/payflow_express/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita verifica SSL | `payment/payflow_express/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Trasferisci elementi riga carrello | `payment/payflow_express/line_items_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ignora passaggio di revisione ordine | `payment/paypal_express/skip_order_review_step` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Trasferisci elementi riga carrello | `payment/paypal_express/line_items_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Opzioni di spedizione trasferimento | `payment/paypal_express/transfer_shipping_options` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Aspetto pulsanti di scelta rapida | `paypal/wpp/button_flavor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita pagamento PayPal come ospite | `payment/paypal_express/solution_type` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Richiedi indirizzo di fatturazione del cliente | `payment/paypal_express/require_billing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Iscrizione al contratto di fatturazione | `payment/paypal_express/allow_ba_signup` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment/paypal_billing_agreement/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment/paypal_billing_agreement/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment/paypal_billing_agreement/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Azione di pagamento | `payment/paypal_billing_agreement/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento applicabile da | `payment/paypal_billing_agreement/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento paesi applicabile da | `payment/paypal_billing_agreement/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita verifica SSL | `payment/paypal_billing_agreement/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Trasferisci elementi riga carrello | `payment/paypal_billing_agreement/line_items_enabled` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Consenti in Creazione guidata contratto di fatturazione | `payment/paypal_billing_agreement/allow_billing_agreement_wizard` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita recupero automatico | `paypal/fetch_reports/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pianificazione | `paypal/fetch_reports/schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ora del giorno | `paypal/fetch_reports/time` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Logo prodotto PayPal | `paypal/style/logo` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stile pagina | `paypal/style/page_style` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| URL immagine intestazione | `paypal/style/paypal_hdrimg` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Colore di sfondo intestazione | `paypal/style/paypal_hdrbackcolor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Colore bordo intestazione | `paypal/style/paypal_hdrbordercolor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Colore di sfondo pagina | `paypal/style/paypal_payflowcolor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita questa soluzione | `payment/paypal_express/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento credito PayPal | `payment/paypal_express_bml/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment/paypal_express/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment/paypal_express/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Azione di pagamento | `payment/paypal_express/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizza nella pagina Dettagli prodotto | `payment/paypal_express/visible_on_product` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Periodo di autorizzazione (giorni) | `payment/paypal_express/authorization_honor_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Periodo valido ordine (giorni) | `payment/paypal_express/order_valid_period` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Numero di autorizzazioni figlio | `payment/paypal_express/child_authorization_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Mostra sul carrello | `payment/paypal_express/visible_on_cart` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento applicabile da | `payment/paypal_express/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento paesi applicabile da | `payment/paypal_express/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita verifica SSL | `payment/paypal_express/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recupero pianificato | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stile pagine PayPal per esercenti | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Pagamenti PayPal Pro

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? |
|--------------|--------------|--------------|--------------|
| Metodi di autenticazione API | `paypal/wpp/api_authentication` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| L&#39;API utilizza il proxy | `paypal/wpp/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recupero pianificato | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recupero pianificato | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Payments Pro Hosted Solution (Regno Unito)

Queste opzioni sono disponibili solo se si sceglie Regno Unito come [paese commerciante](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths).

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? |
|--------------|--------------|--------------|--------------|
| Abilita questa soluzione | `payment/hosted_pro/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment/hosted_pro/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment/hosted_pro/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Azione di pagamento | `payment/hosted_pro/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Visualizza Pagamento rapido nel passaggio Informazioni pagamento | `payment/hosted_pro/display_ec` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento applicabile da | `payment/hosted_pro/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento paesi applicabile da | `payment/hosted_pro/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita verifica SSL | `payment/hosted_pro/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## PayPal Payflow Pro

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? |
|--------------|--------------|--------------|--------------|
| Vault abilitato | `payment/payflowpro_cc_vault/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment/payflowpro/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo Vault | `payment/payflowpro_cc_vault/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment/payflowpro/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Azione di pagamento | `payment/payflowpro/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipi di carta di credito consentiti | `payment/payflowpro/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento applicabile da | `payment/payflowpro/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento paesi applicabile da | `payment/payflowpro/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita verifica SSL | `payment/payflowpro/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Richiedi voce CVV | `payment/payflowpro/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rifiuta transazione se: | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Strada AVS non corrispondente | `payment/payflowpro/avs_street` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Zip AVS non corrispondente | `payment/payflowpro/avs_zip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Indicatore AVS internazionale non corrispondente | `payment/payflowpro/avs_international` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Il Codice Di Sicurezza Della Carta Non Corrisponde | `payment/payflowpro/avs_security_code` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fornitore | `payment/payflowpro/vendor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usa proxy | `payment/payflowpro/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment/payflow_express/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment/payflow_express/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Azione di pagamento | `payment/payflow_express/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recupero pianificato | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stile pagine PayPal per esercenti | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Partner | `payment/payflow_advanced/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fornitore | `payment/payflow_advanced/vendor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Usa proxy | `payment/payflow_advanced/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita questa soluzione | `payment/payflow_advanced/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment/payflow_advanced/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment/payflow_advanced/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Azione di pagamento | `payment/payflow_advanced/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento applicabile da | `payment/payflow_advanced/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento paesi applicabile da | `payment/payflow_advanced/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita verifica SSL | `payment/payflow_advanced/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Voce CVV modificabile | `payment/payflow_advanced/csc_editable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Richiedi voce CVV | `payment/payflow_advanced/csc_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Invia conferma e-mail | `payment/payflow_advanced/email_confirmation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Collegamento flusso di pagamento PayPal

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? |
|--------------|--------------|--------------|--------------|
| Partner | `payment/payflow_link/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fornitore | `payment/payflow_link/vendor` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita collegamento payflow | `payment/payflow_link/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita estrazione rapida | `payment/payflow_express/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento credito PayPal | `payment/payflow_express_bml/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento applicabile da | `payment/payflow_link/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento paesi applicabile da | `payment/payflow_link/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita verifica SSL | `payment/payflow_link/verify_peer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Voce CVV modificabile | `payment/payflow_link/csc_editable` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Richiedi voce CVV | `payment/payflow_link/csc_required` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Invia conferma e-mail | `payment/payflow_link/email_confirmation` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recupero pianificato | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment/payflow_link/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment/payflow_link/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Azione di pagamento | `payment/payflow_link/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Percorsi di estrazione subtotale zero

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? |
|--------------|--------------|--------------|--------------|
| Abilitato | `payment/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fattura automaticamente tutti gli articoli | `payment/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Percorsi di pagamento in contrassegno

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? |
|--------------|--------------|--------------|--------------|
| Abilitato | `payment/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Istruzioni | `payment/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Percorsi di pagamento bonifico bancario

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? |
|--------------|--------------|--------------|--------------|
| Abilitato | `payment/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Istruzioni | `payment/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Controlla o percorsi ordini di pagamento

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? |
|--------------|--------------|--------------|--------------|
| Abilitato | `payment/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Imposta come assegno da pagare a | `payment/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Percorsi ordine di acquisto

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? |
|--------------|--------------|--------------|--------------|
| Abilitato | `payment/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |

{style="table-layout:auto"}

## Percorsi internazionali

>[!INFO]
>
>I percorsi disponibili sono determinati dalla scelta di [Paese esercente](../reference/config-reference-sens.md#payment-sensitive-and-system-specific-paths).

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? |
|--------------|--------------|--------------|--------------|
| Credenziali SFTP | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recupero pianificato | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stile pagine PayPal per esercenti | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita questa soluzione | `payment/wps_express/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recupero pianificato | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stile pagine PayPal per esercenti | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Impostazioni carta di credito | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rifiuta transazione se: | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recupero pianificato | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_nz/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_nz/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_nz/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fattura automaticamente tutti gli articoli | `payment_nz/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_nz/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_nz/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_nz/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_nz/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_nz/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_nz/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_nz/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_nz/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Istruzioni | `payment_nz/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_nz/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_nz/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_nz/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_nz/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_nz/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_nz/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_nz/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_nz/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Istruzioni | `payment_nz/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_nz/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_nz/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_nz/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_nz/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_nz/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_nz/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_nz/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_nz/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Imposta come assegno da pagare a | `payment_nz/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Invia assegno a | `payment_nz/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_nz/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_nz/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_nz/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_nz/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_nz/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_nz/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_nz/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_nz/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_nz/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_nz/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_nz/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_nz/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Azione di pagamento | `payment_nz/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_nz/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_nz/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valuta accettata | `payment_nz/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Debug | `payment_nz/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipi di carta di credito | `payment_nz/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verifica con carta di credito | `payment_nz/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_nz/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_nz/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_nz/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_nz/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_nz/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_nz/cybersource/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_nz/cybersource/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_nz/cybersource/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Stato nuovo ordine | `payment_nz/cybersource/order_status` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Debug | `payment_nz/cybersource/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipi di carta di credito | `payment_nz/cybersource/cctypes` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento dai paesi applicabili | `payment_nz/cybersource/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento da paesi specifici | `payment_nz/cybersource/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Totale ordine minimo | `payment_nz/cybersource/min_order_total` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Totale ordine massimo | `payment_nz/cybersource/max_order_total` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_nz/cybersource/sort_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilitato | `payment_nz/worldpay/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_nz/worldpay/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Consenti Di Modificare Le Informazioni Di Contatto | `payment_nz/worldpay/fix_contact` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Nascondi informazioni di contatto | `payment_nz/worldpay/hide_contact` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Campi firma | `payment_nz/worldpay/signature_fields` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Debug | `payment_nz/worldpay/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento per test | `payment_nz/worldpay/test_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_nz/worldpay/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento Da Paesi Applicabili | `payment_nz/worldpay/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento Da Paesi Specifici | `payment_nz/worldpay/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Imposta stato ordine su Sospetta frode per CVV | `payment_nz/worldpay/cvv_fraud_case` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Imposta lo stato dell&#39;ordine su Sospetta frode per AVS CAP | `payment_nz/worldpay/avs_fraud_case` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_nz/worldpay/sort_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilitato | `payment_nz/eway/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipo di connessione | `payment_nz/eway/connection_type` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_nz/eway/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_nz/eway/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Debug | `payment_nz/eway/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipi di carta di credito | `payment_nz/eway/cctypes` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento dai paesi applicabili | `payment_nz/eway/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento da paesi specifici | `payment_nz/eway/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_nz/eway/sort_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Recupero pianificato | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stile pagine PayPal per esercenti | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recupero pianificato | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recupero pianificato | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stile pagine PayPal per esercenti | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_hk/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_hk/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_hk/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fattura automaticamente tutti gli articoli | `payment_hk/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_hk/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_hk/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_hk/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_hk/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_hk/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_hk/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_hk/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_hk/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Istruzioni | `payment_hk/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_hk/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_hk/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_hk/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_hk/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_hk/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_hk/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_hk/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_hk/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Istruzioni | `payment_hk/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_hk/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_hk/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_hk/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_hk/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_hk/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_hk/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_hk/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_hk/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_hk/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_hk/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_hk/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_hk/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_hk/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_hk/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_hk/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_hk/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_hk/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_hk/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_hk/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_hk/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Azione di pagamento | `payment_hk/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_hk/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_hk/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valuta accettata | `payment_hk/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Debug | `payment_hk/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipi di carta di credito | `payment_hk/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verifica con carta di credito | `payment_hk/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_hk/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_hk/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_hk/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_hk/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_hk/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_hk/cybersource/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_hk/cybersource/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_hk/cybersource/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Stato nuovo ordine | `payment_hk/cybersource/order_status` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Debug | `payment_hk/cybersource/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipi di carta di credito | `payment_hk/cybersource/cctypes` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento dai paesi applicabili | `payment_hk/cybersource/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento da paesi specifici | `payment_hk/cybersource/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Totale ordine minimo | `payment_hk/cybersource/min_order_total` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Totale ordine massimo | `payment_hk/cybersource/max_order_total` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_hk/cybersource/sort_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilitato | `payment_hk/worldpay/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_hk/worldpay/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Consenti Di Modificare Le Informazioni Di Contatto | `payment_hk/worldpay/fix_contact` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Nascondi informazioni di contatto | `payment_hk/worldpay/hide_contact` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Debug | `payment_hk/worldpay/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento per test | `payment_hk/worldpay/test_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_hk/worldpay/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento Da Paesi Applicabili | `payment_hk/worldpay/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento Da Paesi Specifici | `payment_hk/worldpay/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Imposta stato ordine su Sospetta frode per CVV | `payment_hk/worldpay/cvv_fraud_case` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Imposta lo stato dell&#39;ordine su Sospetta frode per AVS CAP | `payment_hk/worldpay/avs_fraud_case` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_hk/worldpay/sort_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilitato | `payment_hk/eway/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipo di connessione | `payment_hk/eway/connection_type` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_hk/eway/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Modalità sandbox | `payment_hk/eway/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_hk/eway/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Debug | `payment_hk/eway/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipi di carta di credito | `payment_hk/eway/cctypes` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento dai paesi applicabili | `payment_hk/eway/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento da paesi specifici | `payment_hk/eway/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_hk/eway/sort_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Recupero pianificato | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stile pagine PayPal per esercenti | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recupero pianificato | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recupero pianificato | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stile pagine PayPal per esercenti | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_es/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_es/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_es/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fattura automaticamente tutti gli articoli | `payment_es/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_es/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_es/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_es/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_es/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_es/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_es/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_es/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_es/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Istruzioni | `payment_es/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_es/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_es/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_es/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_es/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_es/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_es/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_es/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_es/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Istruzioni | `payment_es/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_es/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_es/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_es/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_es/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_es/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_es/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_es/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_es/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Imposta come assegno da pagare a | `payment_es/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_es/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_es/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_es/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_es/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_es/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_es/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_es/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_es/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_es/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_es/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_es/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_es/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Azione di pagamento | `payment_es/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_es/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_es/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valuta accettata | `payment_es/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Debug | `payment_es/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipi di carta di credito | `payment_es/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verifica con carta di credito | `payment_es/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_es/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_es/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_es/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_es/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_es/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_es/cybersource/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_es/cybersource/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_es/cybersource/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| ID profilo | `payment_es/cybersource/profile_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) |
| Stato nuovo ordine | `payment_es/cybersource/order_status` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Debug | `payment_es/cybersource/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipi di carta di credito | `payment_es/cybersource/cctypes` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento dai paesi applicabili | `payment_es/cybersource/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento da paesi specifici | `payment_es/cybersource/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Totale ordine minimo | `payment_es/cybersource/min_order_total` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Totale ordine massimo | `payment_es/cybersource/max_order_total` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_es/cybersource/sort_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilitato | `payment_es/worldpay/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_es/worldpay/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| ID installazione | `payment_es/worldpay/installation_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| ID installazione amministratore remoto | `payment_es/worldpay/admin_installation_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Consenti Di Modificare Le Informazioni Di Contatto | `payment_es/worldpay/fix_contact` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Nascondi informazioni di contatto | `payment_es/worldpay/hide_contact` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Campi firma | `payment_es/worldpay/signature_fields` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Modalità di prova | `payment_es/worldpay/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento per test | `payment_es/worldpay/test_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_es/worldpay/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento Da Paesi Applicabili | `payment_es/worldpay/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento Da Paesi Specifici | `payment_es/worldpay/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Imposta stato ordine su Sospetta frode per CVV | `payment_es/worldpay/cvv_fraud_case` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Imposta lo stato dell&#39;ordine su Sospetta frode per AVS CAP | `payment_es/worldpay/avs_fraud_case` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_es/worldpay/sort_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilitato | `payment_es/eway/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipo di connessione | `payment_es/eway/connection_type` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_es/eway/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_es/eway/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Debug | `payment_es/eway/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipi di carta di credito | `payment_es/eway/cctypes` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento dai paesi applicabili | `payment_es/eway/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento da paesi specifici | `payment_es/eway/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_es/eway/sort_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Recupero pianificato | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stile pagine PayPal per esercenti | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recupero pianificato | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recupero pianificato | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stile pagine PayPal per esercenti | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_it/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_it/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_it/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fattura automaticamente tutti gli articoli | `payment_it/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_it/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_it/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_it/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_it/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_it/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_it/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_it/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_it/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Istruzioni | `payment_it/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_it/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_it/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_it/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_it/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_it/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_it/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_it/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_it/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Istruzioni | `payment_it/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_it/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_it/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_it/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_it/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_it/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_it/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_it/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_it/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_it/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_it/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_it/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_it/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_it/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_it/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_it/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_it/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_it/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_it/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_it/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_it/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Azione di pagamento | `payment_it/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_it/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_it/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valuta accettata | `payment_it/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Debug | `payment_it/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipi di carta di credito | `payment_it/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verifica con carta di credito | `payment_it/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_it/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_it/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_it/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_it/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_it/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_it/cybersource/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_it/cybersource/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_it/cybersource/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Stato nuovo ordine | `payment_it/cybersource/order_status` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Debug | `payment_it/cybersource/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipi di carta di credito | `payment_it/cybersource/cctypes` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento dai paesi applicabili | `payment_it/cybersource/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento da paesi specifici | `payment_it/cybersource/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Totale ordine minimo | `payment_it/cybersource/min_order_total` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Totale ordine massimo | `payment_it/cybersource/max_order_total` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_it/cybersource/sort_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilitato | `payment_it/worldpay/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_it/worldpay/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Consenti Di Modificare Le Informazioni Di Contatto | `payment_it/worldpay/fix_contact` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Nascondi informazioni di contatto | `payment_it/worldpay/hide_contact` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Campi firma | `payment_it/worldpay/signature_fields` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Debug | `payment_it/worldpay/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento per test | `payment_it/worldpay/test_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_it/worldpay/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento Da Paesi Applicabili | `payment_it/worldpay/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento Da Paesi Specifici | `payment_it/worldpay/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Imposta stato ordine su Sospetta frode per CVV | `payment_it/worldpay/cvv_fraud_case` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Imposta lo stato dell&#39;ordine su Sospetta frode per AVS CAP | `payment_it/worldpay/avs_fraud_case` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_it/worldpay/sort_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilitato | `payment_it/eway/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipo di connessione | `payment_it/eway/connection_type` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_it/eway/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_it/eway/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Debug | `payment_it/eway/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipi di carta di credito | `payment_it/eway/cctypes` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento dai paesi applicabili | `payment_it/eway/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento da paesi specifici | `payment_it/eway/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_it/eway/sort_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Recupero pianificato | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stile pagine PayPal per esercenti | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recupero pianificato | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recupero pianificato | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stile pagine PayPal per esercenti | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_fr/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_fr/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_fr/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fattura automaticamente tutti gli articoli | `payment_fr/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_fr/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_fr/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_fr/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_fr/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_fr/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_fr/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_fr/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_fr/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Istruzioni | `payment_fr/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_fr/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_fr/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_fr/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_fr/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_fr/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_fr/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_fr/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_fr/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Istruzioni | `payment_fr/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_fr/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_fr/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_fr/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_fr/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_fr/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_fr/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_fr/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_fr/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_fr/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_fr/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_fr/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_fr/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_fr/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_fr/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_fr/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_fr/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_fr/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_fr/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_fr/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_fr/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Azione di pagamento | `payment_fr/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_fr/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_fr/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valuta accettata | `payment_fr/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Debug | `payment_fr/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipi di carta di credito | `payment_fr/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verifica con carta di credito | `payment_fr/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_fr/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_fr/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_fr/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_fr/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_fr/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_fr/cybersource/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_fr/cybersource/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_fr/cybersource/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Stato nuovo ordine | `payment_fr/cybersource/order_status` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Debug | `payment_fr/cybersource/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipi di carta di credito | `payment_fr/cybersource/cctypes` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento dai paesi applicabili | `payment_fr/cybersource/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento da paesi specifici | `payment_fr/cybersource/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Totale ordine minimo | `payment_fr/cybersource/min_order_total` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Totale ordine massimo | `payment_fr/cybersource/max_order_total` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_fr/cybersource/sort_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilitato | `payment_fr/worldpay/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_fr/worldpay/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Consenti Di Modificare Le Informazioni Di Contatto | `payment_fr/worldpay/fix_contact` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Nascondi informazioni di contatto | `payment_fr/worldpay/hide_contact` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Debug | `payment_fr/worldpay/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento per test | `payment_fr/worldpay/test_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_fr/worldpay/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento Da Paesi Applicabili | `payment_fr/worldpay/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento Da Paesi Specifici | `payment_fr/worldpay/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Imposta stato ordine su Sospetta frode per CVV | `payment_fr/worldpay/cvv_fraud_case` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Imposta lo stato dell&#39;ordine su Sospetta frode per AVS CAP | `payment_fr/worldpay/avs_fraud_case` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_fr/worldpay/sort_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilitato | `payment_fr/eway/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipo di connessione | `payment_fr/eway/connection_type` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_fr/eway/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_fr/eway/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Debug | `payment_fr/eway/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipi di carta di credito | `payment_fr/eway/cctypes` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento dai paesi applicabili | `payment_fr/eway/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento da paesi specifici | `payment_fr/eway/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_fr/eway/sort_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Recupero pianificato | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stile pagine PayPal per esercenti | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recupero pianificato | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recupero pianificato | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stile pagine PayPal per esercenti | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_jp/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_jp/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_jp/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fattura automaticamente tutti gli articoli | `payment_jp/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_jp/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_jp/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_jp/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_jp/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_jp/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_jp/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_jp/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_jp/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Istruzioni | `payment_jp/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_jp/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_jp/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_jp/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_jp/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_jp/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_jp/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_jp/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_jp/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Istruzioni | `payment_jp/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_jp/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_jp/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_jp/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_jp/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_jp/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_jp/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_jp/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_jp/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_jp/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_jp/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_jp/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_jp/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_jp/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_jp/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_jp/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_jp/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_jp/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_jp/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_jp/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_jp/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Azione di pagamento | `payment_jp/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_jp/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_jp/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valuta accettata | `payment_jp/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Debug | `payment_jp/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipi di carta di credito | `payment_jp/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verifica con carta di credito | `payment_jp/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_jp/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_jp/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_jp/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_jp/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_jp/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_jp/cybersource/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_jp/cybersource/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_jp/cybersource/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Debug | `payment_jp/cybersource/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipi di carta di credito | `payment_jp/cybersource/cctypes` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento dai paesi applicabili | `payment_jp/cybersource/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento da paesi specifici | `payment_jp/cybersource/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Totale ordine minimo | `payment_jp/cybersource/min_order_total` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Totale ordine massimo | `payment_jp/cybersource/max_order_total` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_jp/cybersource/sort_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilitato | `payment_jp/worldpay/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_jp/worldpay/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Consenti Di Modificare Le Informazioni Di Contatto | `payment_jp/worldpay/fix_contact` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Nascondi informazioni di contatto | `payment_jp/worldpay/hide_contact` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Debug | `payment_jp/worldpay/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento per test | `payment_jp/worldpay/test_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_jp/worldpay/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento Da Paesi Applicabili | `payment_jp/worldpay/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento Da Paesi Specifici | `payment_jp/worldpay/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Imposta stato ordine su Sospetta frode per CVV | `payment_jp/worldpay/cvv_fraud_case` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Imposta lo stato dell&#39;ordine su Sospetta frode per AVS CAP | `payment_jp/worldpay/avs_fraud_case` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_jp/worldpay/sort_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilitato | `payment_jp/eway/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipo di connessione | `payment_jp/eway/connection_type` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_jp/eway/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_jp/eway/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Debug | `payment_jp/eway/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipi di carta di credito | `payment_jp/eway/cctypes` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento dai paesi applicabili | `payment_jp/eway/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento da paesi specifici | `payment_jp/eway/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_jp/eway/sort_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Recupero pianificato | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stile pagine PayPal per esercenti | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recupero pianificato | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recupero pianificato | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stile pagine PayPal per esercenti | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Impostazioni carta di credito | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rifiuta transazione se: | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recupero pianificato | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_au/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_au/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_au/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fattura automaticamente tutti gli articoli | `payment_au/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_au/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_au/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_au/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_au/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_au/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_au/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_au/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_au/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Istruzioni | `payment_au/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_au/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_au/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_au/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_au/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_au/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_au/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_au/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_au/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Istruzioni | `payment_au/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_au/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_au/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_au/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_au/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_au/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_au/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_au/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_au/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Imposta come assegno da pagare a | `payment_au/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Invia assegno a | `payment_au/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_au/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_au/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_au/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_au/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_au/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_au/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_au/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_au/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_au/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_au/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_au/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_au/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Azione di pagamento | `payment_au/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_au/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_au/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valuta accettata | `payment_au/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Debug | `payment_au/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipi di carta di credito | `payment_au/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verifica con carta di credito | `payment_au/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_au/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_au/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_au/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_au/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_au/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_au/cybersource/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_au/cybersource/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_au/cybersource/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| ID esercente | `payment_au/cybersource/merchant_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) |
| ID profilo | `payment_au/cybersource/profile_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) |
| Stato nuovo ordine | `payment_au/cybersource/order_status` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Debug | `payment_au/cybersource/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipi di carta di credito | `payment_au/cybersource/cctypes` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento dai paesi applicabili | `payment_au/cybersource/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento da paesi specifici | `payment_au/cybersource/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Totale ordine minimo | `payment_au/cybersource/min_order_total` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Totale ordine massimo | `payment_au/cybersource/max_order_total` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_au/cybersource/sort_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilitato | `payment_au/worldpay/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_au/worldpay/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| ID installazione | `payment_au/worldpay/installation_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Consenti Di Modificare Le Informazioni Di Contatto | `payment_au/worldpay/fix_contact` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Nascondi informazioni di contatto | `payment_au/worldpay/hide_contact` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Campi firma | `payment_au/worldpay/signature_fields` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Debug | `payment_au/worldpay/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Modalità di prova | `payment_au/worldpay/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento per test | `payment_au/worldpay/test_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_au/worldpay/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento Da Paesi Applicabili | `payment_au/worldpay/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento Da Paesi Specifici | `payment_au/worldpay/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Imposta stato ordine su Sospetta frode per CVV | `payment_au/worldpay/cvv_fraud_case` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Imposta lo stato dell&#39;ordine su Sospetta frode per AVS CAP | `payment_au/worldpay/avs_fraud_case` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_au/worldpay/sort_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilitato | `payment_au/eway/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipo di connessione | `payment_au/eway/connection_type` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_au/eway/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_au/eway/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Debug | `payment_au/eway/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipi di carta di credito | `payment_au/eway/cctypes` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento dai paesi applicabili | `payment_au/eway/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento da paesi specifici | `payment_au/eway/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_au/eway/sort_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Recupero pianificato | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stile pagine PayPal per esercenti | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recupero pianificato | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stile pagine PayPal per esercenti | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita questa soluzione | `payment/paypal_payment_pro/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Impostazioni carta di credito | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rifiuta transazione se: | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recupero pianificato | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Impostazioni carta di credito | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rifiuta transazione se: | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recupero pianificato | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recupero pianificato | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stile pagine PayPal per esercenti | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_ca/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_ca/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_ca/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fattura automaticamente tutti gli articoli | `payment_ca/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_ca/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_ca/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_ca/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_ca/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_ca/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_ca/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_ca/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_ca/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Istruzioni | `payment_ca/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_ca/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_ca/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_ca/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_ca/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_ca/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_ca/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_ca/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_ca/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Istruzioni | `payment_ca/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_ca/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_ca/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_ca/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_ca/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_ca/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_ca/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_ca/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_ca/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_ca/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_ca/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_ca/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_ca/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_ca/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_ca/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_ca/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_ca/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_ca/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_ca/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_ca/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_ca/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Azione di pagamento | `payment_ca/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_ca/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valuta accettata | `payment_ca/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Debug | `payment_ca/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipi di carta di credito | `payment_ca/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verifica con carta di credito | `payment_ca/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_ca/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_ca/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_ca/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_ca/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_ca/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_ca/cybersource/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_ca/cybersource/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_ca/cybersource/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Debug | `payment_ca/cybersource/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipi di carta di credito | `payment_ca/cybersource/cctypes` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento dai paesi applicabili | `payment_ca/cybersource/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento da paesi specifici | `payment_ca/cybersource/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Totale ordine minimo | `payment_ca/cybersource/min_order_total` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Totale ordine massimo | `payment_ca/cybersource/max_order_total` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_ca/cybersource/sort_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilitato | `payment_ca/worldpay/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_ca/worldpay/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Consenti Di Modificare Le Informazioni Di Contatto | `payment_ca/worldpay/fix_contact` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Nascondi informazioni di contatto | `payment_ca/worldpay/hide_contact` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Campi firma | `payment_ca/worldpay/signature_fields` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Debug | `payment_ca/worldpay/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento per test | `payment_ca/worldpay/test_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_ca/worldpay/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento Da Paesi Applicabili | `payment_ca/worldpay/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento Da Paesi Specifici | `payment_ca/worldpay/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Imposta stato ordine su Sospetta frode per CVV | `payment_ca/worldpay/cvv_fraud_case` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Imposta lo stato dell&#39;ordine su Sospetta frode per AVS CAP | `payment_ca/worldpay/avs_fraud_case` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_ca/worldpay/sort_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilitato | `payment_ca/eway/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipo di connessione | `payment_ca/eway/connection_type` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_ca/eway/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_ca/eway/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Debug | `payment_ca/eway/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipi di carta di credito | `payment_ca/eway/cctypes` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento dai paesi applicabili | `payment_ca/eway/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento da paesi specifici | `payment_ca/eway/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_ca/eway/sort_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Recupero pianificato | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stile pagine PayPal per esercenti | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recupero pianificato | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stile pagine PayPal per esercenti | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_other/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_other/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_other/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fattura automaticamente tutti gli articoli | `payment_other/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_other/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_other/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_other/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_other/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_other/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_other/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_other/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_other/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Istruzioni | `payment_other/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_other/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_other/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_other/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_other/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_other/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_other/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_other/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_other/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Istruzioni | `payment_other/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_other/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_other/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_other/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_other/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_other/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_other/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_other/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_other/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_other/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_other/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_other/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_other/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_other/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_other/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_other/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_other/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_other/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_other/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_other/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_other/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Azione di pagamento | `payment_other/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_other/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valuta accettata | `payment_other/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Debug | `payment_other/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Invia e-mail al cliente | `payment_other/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipi di carta di credito | `payment_other/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verifica con carta di credito | `payment_other/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_other/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_other/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_other/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_other/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_other/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_other/cybersource/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_other/cybersource/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_other/cybersource/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Debug | `payment_other/cybersource/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipi di carta di credito | `payment_other/cybersource/cctypes` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento dai paesi applicabili | `payment_other/cybersource/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento da paesi specifici | `payment_other/cybersource/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Totale ordine minimo | `payment_other/cybersource/min_order_total` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Totale ordine massimo | `payment_other/cybersource/max_order_total` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_other/cybersource/sort_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilitato | `payment_other/worldpay/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_other/worldpay/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Consenti Di Modificare Le Informazioni Di Contatto | `payment_other/worldpay/fix_contact` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Nascondi informazioni di contatto | `payment_other/worldpay/hide_contact` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Campi firma | `payment_other/worldpay/signature_fields` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Debug | `payment_other/worldpay/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento per test | `payment_other/worldpay/test_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_other/worldpay/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento Da Paesi Applicabili | `payment_other/worldpay/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento Da Paesi Specifici | `payment_other/worldpay/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Imposta stato ordine su Sospetta frode per CVV | `payment_other/worldpay/cvv_fraud_case` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Imposta lo stato dell&#39;ordine su Sospetta frode per AVS CAP | `payment_other/worldpay/avs_fraud_case` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_other/worldpay/sort_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilitato | `payment_other/eway/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipo di connessione | `payment_other/eway/connection_type` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_other/eway/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_other/eway/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Debug | `payment_other/eway/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipi di carta di credito | `payment_other/eway/cctypes` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento dai paesi applicabili | `payment_other/eway/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento da paesi specifici | `payment_other/eway/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_other/eway/sort_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Recupero pianificato | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stile pagine PayPal per esercenti | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_de/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_de/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_de/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_de/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_de/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_de/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_de/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_de/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_de/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_de/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_de/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_de/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_de/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Istruzioni | `payment_de/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_de/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_de/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_de/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_de/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_de/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_de/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_de/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_de/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Istruzioni | `payment_de/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_de/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_de/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_de/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_de/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_de/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_de/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fattura automaticamente tutti gli articoli | `payment_de/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_de/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_de/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_de/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_de/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_de/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_de/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_de/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_de/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_de/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_de/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_de/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_de/cybersource/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_de/cybersource/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_de/cybersource/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Stato nuovo ordine | `payment_de/cybersource/order_status` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Debug | `payment_de/cybersource/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipi di carta di credito | `payment_de/cybersource/cctypes` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento dai paesi applicabili | `payment_de/cybersource/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento da paesi specifici | `payment_de/cybersource/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Totale ordine minimo | `payment_de/cybersource/min_order_total` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Totale ordine massimo | `payment_de/cybersource/max_order_total` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_de/cybersource/sort_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilitato | `payment_de/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Azione di pagamento | `payment_de/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_de/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_de/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valuta accettata | `payment_de/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Debug | `payment_de/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipi di carta di credito | `payment_de/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verifica con carta di credito | `payment_de/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_de/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_de/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_de/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_de/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_de/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_de/worldpay/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_de/worldpay/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Consenti Di Modificare Le Informazioni Di Contatto | `payment_de/worldpay/fix_contact` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Nascondi informazioni di contatto | `payment_de/worldpay/hide_contact` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Campi firma | `payment_de/worldpay/signature_fields` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Modalità di prova | `payment_de/worldpay/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento per test | `payment_de/worldpay/test_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_de/worldpay/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento Da Paesi Applicabili | `payment_de/worldpay/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento Da Paesi Specifici | `payment_de/worldpay/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Imposta stato ordine su Sospetta frode per CVV | `payment_de/worldpay/cvv_fraud_case` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Imposta lo stato dell&#39;ordine su Sospetta frode per AVS CAP | `payment_de/worldpay/avs_fraud_case` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_de/worldpay/sort_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilitato | `payment_de/eway/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipo di connessione | `payment_de/eway/connection_type` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_de/eway/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_de/eway/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Debug | `payment_de/eway/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipi di carta di credito | `payment_de/eway/cctypes` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento dai paesi applicabili | `payment_de/eway/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento da paesi specifici | `payment_de/eway/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_de/eway/sort_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Recupero pianificato | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stile pagine PayPal per esercenti | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recupero pianificato | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stile pagine PayPal per esercenti | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recupero pianificato | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stile pagine PayPal per esercenti | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_gb/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_gb/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_gb/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_gb/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_gb/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Imposta come assegno da pagare a | `payment_gb/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_gb/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_gb/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_gb/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_gb/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_gb/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_gb/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_gb/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_gb/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Istruzioni | `payment_gb/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_gb/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_gb/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_gb/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_gb/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_gb/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_gb/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_gb/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_gb/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Istruzioni | `payment_gb/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_gb/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_gb/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_gb/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_gb/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_gb/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_gb/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fattura automaticamente tutti gli articoli | `payment_gb/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_gb/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_gb/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_gb/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_gb/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_gb/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_gb/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_gb/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_gb/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_gb/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_gb/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_gb/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_gb/cybersource/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_gb/cybersource/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_gb/cybersource/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Stato nuovo ordine | `payment_gb/cybersource/order_status` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Debug | `payment_gb/cybersource/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipi di carta di credito | `payment_gb/cybersource/cctypes` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento dai paesi applicabili | `payment_gb/cybersource/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento da paesi specifici | `payment_gb/cybersource/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Totale ordine minimo | `payment_gb/cybersource/min_order_total` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Totale ordine massimo | `payment_gb/cybersource/max_order_total` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_gb/cybersource/sort_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilitato | `payment_gb/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Azione di pagamento | `payment_gb/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_gb/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_gb/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valuta accettata | `payment_gb/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Debug | `payment_gb/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipi di carta di credito | `payment_gb/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verifica con carta di credito | `payment_gb/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_gb/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_gb/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_gb/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_gb/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_gb/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_gb/worldpay/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_gb/worldpay/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Segreto MD5 per le transazioni | `payment_gb/worldpay/md5_secret` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Consenti Di Modificare Le Informazioni Di Contatto | `payment_gb/worldpay/fix_contact` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Nascondi informazioni di contatto | `payment_gb/worldpay/hide_contact` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Campi firma | `payment_gb/worldpay/signature_fields` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Debug | `payment_gb/worldpay/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento per test | `payment_gb/worldpay/test_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_gb/worldpay/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento Da Paesi Applicabili | `payment_gb/worldpay/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento Da Paesi Specifici | `payment_gb/worldpay/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Imposta stato ordine su Sospetta frode per CVV | `payment_gb/worldpay/cvv_fraud_case` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Imposta lo stato dell&#39;ordine su Sospetta frode per AVS CAP | `payment_gb/worldpay/avs_fraud_case` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_gb/worldpay/sort_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilitato | `payment_gb/eway/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipo di connessione | `payment_gb/eway/connection_type` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_gb/eway/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_gb/eway/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Debug | `payment_gb/eway/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipi di carta di credito | `payment_gb/eway/cctypes` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento dai paesi applicabili | `payment_gb/eway/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento da paesi specifici | `payment_gb/eway/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_gb/eway/sort_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Recupero pianificato | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stile pagine PayPal per esercenti | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recupero pianificato | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stile pagine PayPal per esercenti | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Impostazioni carta di credito | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rifiuta transazione se: | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recupero pianificato | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stile pagine PayPal per esercenti | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilita credito PayPal | `payment/wps_express_bml/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recupero pianificato | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stile pagine PayPal per esercenti | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Impostazioni carta di credito | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Rifiuta transazione se: | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_avs_check/heading_avs_settings` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recupero pianificato | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stile pagine PayPal per esercenti | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Recupero pianificato | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_schedule` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stile pagine PayPal per esercenti | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_frontend/paypal_pages` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_us/free/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_us/free/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_us/free/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Fattura automaticamente tutti gli articoli | `payment_us/free/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_us/free/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_us/free/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_us/free/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_us/cashondelivery/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_us/cashondelivery/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_us/cashondelivery/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_us/cashondelivery/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_us/cashondelivery/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Istruzioni | `payment_us/cashondelivery/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_us/cashondelivery/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_us/cashondelivery/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_us/cashondelivery/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_us/banktransfer/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_us/banktransfer/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_us/banktransfer/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_us/banktransfer/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_us/banktransfer/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Istruzioni | `payment_us/banktransfer/instructions` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_us/banktransfer/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_us/banktransfer/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_us/banktransfer/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_us/checkmo/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_us/checkmo/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_us/checkmo/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_us/checkmo/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_us/checkmo/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Imposta come assegno da pagare a | `payment_us/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_us/checkmo/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_us/checkmo/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_us/checkmo/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_us/purchaseorder/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_us/purchaseorder/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_us/purchaseorder/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_us/purchaseorder/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_us/purchaseorder/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_us/purchaseorder/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_us/purchaseorder/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_us/purchaseorder/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_us/authorizenet_directpost/active` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Azione di pagamento | `payment_us/authorizenet_directpost/payment_action` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Titolo | `payment_us/authorizenet_directpost/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Stato nuovo ordine | `payment_us/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Valuta accettata | `payment_us/authorizenet_directpost/currency` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Debug | `payment_us/authorizenet_directpost/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Tipi di carta di credito | `payment_us/authorizenet_directpost/cctypes` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Verifica con carta di credito | `payment_us/authorizenet_directpost/useccv` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento dai paesi applicabili | `payment_us/authorizenet_directpost/allowspecific` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Pagamento da paesi specifici | `payment_us/authorizenet_directpost/specificcountry` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine minimo | `payment_us/authorizenet_directpost/min_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Totale ordine massimo | `payment_us/authorizenet_directpost/max_order_total` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Ordinamento | `payment_us/authorizenet_directpost/sort_order` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| Abilitato | `payment_us/cybersource/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_us/cybersource/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_us/cybersource/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Stato nuovo ordine | `payment_us/cybersource/order_status` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Debug | `payment_us/cybersource/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipi di carta di credito | `payment_us/cybersource/cctypes` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento dai paesi applicabili | `payment_us/cybersource/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento da paesi specifici | `payment_us/cybersource/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Totale ordine minimo | `payment_us/cybersource/min_order_total` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Totale ordine massimo | `payment_us/cybersource/max_order_total` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_us/cybersource/sort_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilitato | `payment_us/worldpay/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_us/worldpay/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Consenti Di Modificare Le Informazioni Di Contatto | `payment_us/worldpay/fix_contact` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Nascondi informazioni di contatto | `payment_us/worldpay/hide_contact` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Campi firma | `payment_us/worldpay/signature_fields` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Debug | `payment_us/worldpay/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento per test | `payment_us/worldpay/test_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_us/worldpay/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento Da Paesi Applicabili | `payment_us/worldpay/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento Da Paesi Specifici | `payment_us/worldpay/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Imposta stato ordine su Sospetta frode per CVV | `payment_us/worldpay/cvv_fraud_case` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Imposta lo stato dell&#39;ordine su Sospetta frode per AVS CAP | `payment_us/worldpay/avs_fraud_case` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_us/worldpay/sort_order` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Abilitato | `payment_us/eway/active` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipo di connessione | `payment_us/eway/connection_type` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Titolo | `payment_us/eway/title` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Azione di pagamento | `payment_us/eway/payment_action` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Debug | `payment_us/eway/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Tipi di carta di credito | `payment_us/eway/cctypes` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento dai paesi applicabili | `payment_us/eway/allowspecific` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Pagamento da paesi specifici | `payment_us/eway/specificcountry` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Ordinamento | `payment_us/eway/sort_order` |  |

{style="table-layout:auto"}
