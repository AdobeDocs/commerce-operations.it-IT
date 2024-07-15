---
title: Riferimento per le informazioni personali del cliente (versione 1.x)
description: Scopri i mapping di entità di database e flussi di dati per le informazioni personali dei clienti nel Magento 1.x.
exl-id: 8b01418d-8ca1-48fc-9577-a324ed3109d1
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 0%

---

# Riferimento per le informazioni personali del cliente (versione 1.x)

>[!NOTE]
>
>Questo è uno di una serie di argomenti per aiutare i commercianti e gli sviluppatori di Adobe Commerce a prepararsi per il rispetto delle normative sulla privacy. Rivolgiti al tuo consulente legale per determinare se e come la tua azienda debba conformarsi ad obblighi di legge.

Utilizza i seguenti diagrammi di flusso di dati e mappature di entità di database come riferimento durante lo sviluppo di programmi di conformità per le normative sulla privacy, ad esempio:

- [RGPD](gdpr.md)
- [CCPA](ccpa.md)

## Diagrammi di flusso di dati

I diagrammi di flusso di dati mostrano i tipi di dati che clienti e amministratori possono immettere e recuperare nella vetrina e in Amministrazione.

### Punti di immissione dati front-end

L&#39;utente può immettere le informazioni relative al cliente, all&#39;indirizzo e al pagamento al momento della registrazione per un conto, durante il pagamento ed eventi simili.

![Punti di ingresso dati front-end](../../assets/security-compliance/frontend-data-entry-points.svg)

### Punti di accesso ai dati front-end

Commerce carica le informazioni del cliente quando effettua l’accesso e visualizza diverse pagine o estrazioni.

![Punti di accesso ai dati front-end](../../assets/security-compliance/frontend-data-access-points.svg)

### Punti di immissione dati back-end

Per creare un cliente o un ordine, un commerciante può immettere le informazioni relative a cliente, indirizzo e pagamento dall&#39;amministratore.

![Punti di ingresso dati back-end](../../assets/security-compliance/backend-data-entry-points.svg)

### Punti di accesso ai dati back-end

Commerce carica le informazioni sul cliente quando un commerciante visualizza diversi tipi di griglie, fa clic su una griglia per visualizzare informazioni dettagliate ed esegue varie altre attività.

![Punti di accesso ai dati back-end](../../assets/security-compliance/backend-data-access-points.svg)

## Entità di database

Il Magento 1 memorizza le informazioni sui clienti in tabelle di clienti, vendite e altri database.

### Dati dei clienti

Il Magento 1 memorizza le informazioni del cliente nelle tabelle `customer_entity` e `customer_address_entity`. Entrambe queste tabelle hanno diverse tabelle di riferimento che possono contenere attributi cliente personalizzati.

#### `customer_entity` e tabelle di riferimento

Le colonne seguenti della tabella `customer_entity` contengono informazioni sul cliente:

| Colonna | Tipo di dati |
| --- | --- |
| `email` | varchar(255) |

Queste tabelle fanno riferimento a `customer_entity` e possono contenere attributi cliente personalizzati:

| Tabella | Colonna | Tipo di dati |
| --- | --- | --- |
| `customer_entity_datetime` | `value` | datetime |
| `customer_entity_decimal` | `value` | decimal(12,4) |
| `customer_entity_int` | `value` | int(11) |
| `customer_entity_text` | `value` | text |
| `customer_entity_varchar` | `value` | varchar(255) |

#### `customer_address_entity` e tabelle di riferimento

Le tabelle seguenti fanno riferimento a `customer_address_entity` e possono contenere attributi cliente personalizzati:

| Tabella | Colonna | Tipo di dati |
| --- | --- | --- |
| `customer_address_entity_datetime` | `value` | datetime |
| `customer_address_entity_decimal` | `value` | decimale(12,4) |
| `customer_address_entity_int` | `value` | numero intero(11) |
| `customer_address_entity_text` | `value` | Testo |
| `customer_address_entity_varchar` | `value` | Varchar(255) |

### Dati dell&#39;ordine

Le `sales_flat_order` tabelle correlate contengono il nome, gli indirizzi fatturazione e di spedizione del cliente e le informazioni correlate.

#### `sales_flat_order` tavolo

Le colonne seguenti della tabella contengono informazioni `sales_order` sui clienti:

| Colonna | Tipo di dati |
| --- | --- |
| `customer_id` | numero intero(10) |
| `customer_email` | Varchar(128) |
| `customer_firstname` | Varchar(128) |
| `customer_gender` | numero intero(11) |
| `customer_lastname` | varchar(128) |
| `customer_middlename` | varchar(128) |
| `customer_prefix` | varchar(32) |
| `customer_suffix` | varchar(32) |
| `customer_taxvat` | varchar(32) |
| `remote_ip` | varchar(32) |

#### Tabella `sales_flat_order_address`

La tabella `sales_flat_order_address` contiene l&#39;indirizzo del cliente.

| Colonna | Tipo di dati |
| --- | --- |
| `customer_id` | int(10) |
| `fax` | varchar(255) |
| `region` | varchar(255) |
| `postcode` | varchar(255) |
| `lastname` | varchar(255) |
| `street` | varchar(255) |
| `city` | varchar(255) |
| `email` | varchar(255) |
| `telephone` | varchar(255) |
| `firstname` | varchar(255) |
| `prefix` | varchar(255) |
| `suffix` | varchar(255) |
| `middlename` | varchar(255) |
| `company` | varchar(255) |
| `vat_id` | text |

#### Tabella `sales_flat_order_grid`

Le colonne seguenti della tabella `sales_flat_order_grid` contengono informazioni sul cliente:

| Colonna | Tipo di dati |
| --- | --- |
| `customer_id` | int(10) |
| `shipping_name` | varchar(255) |
| `billing_name` | varchar(255) |

#### Tabella `sales_flat_order_payment`

Le colonne seguenti della tabella `sales_flat_order_payment` contengono informazioni sul cliente:

| Colonna | Tipo di dati |
| --- | --- |
| `cc_exp_month` | varchar(255) |
| `cc_ss_start_year` | varchar(255) |
| `echeck_bank_name` | varchar(128) |
| `echeck_type` | varchar(255) |
| `cc_ss_start_month` | varchar(255) |
| `cc_owner` | varchar(255) |
| `cc_exp_year` | varchar(255) |
| `echeck_routing_number` | Varchar(255) |
| `echeck_account_name` | varchar(255) |

### Dati offerta

I preventivi contengono il nome, l&#39;indirizzo e-mail e le informazioni correlate di un cliente.

#### Tabella `sales_flat_quote`

Le colonne seguenti della tabella `sales_flat_quote` contengono informazioni sul cliente:

| Colonna | Tipo di dati |
| --- | --- |
| `customer_id` | numero intero(10) |
| `customer_tax_class_id` | numero intero(10) |
| `customer_group_id` | numero intero(10) |
| `customer_email` | Varchar(255) |
| `customer_prefix` | varchar(40) |
| `customer_firstname` | Varchar(255) |
| `customer_middlename` | varchar(40) |
| `customer_lastname` | Varchar(255) |
| `customer_suffix` | varchar(40) |
| `customer_dob` | datetime |
| `customer_note` | varchar(255) |
| `remote_ip` | varchar(255) |
| `customer_gender` | varchar(255) |

#### Tabella `sales_flat_quote_address`

Le colonne seguenti della tabella `sales_flat_quote_address` contengono informazioni sul cliente:

| Colonna | Tipo di dati |
| --- | --- |
| `email` | varchar(255) |
| `prefix` | varchar(40) |
| `firstname` | varchar(255) |
| `middlename` | varchar(40) |
| `lastname` | varchar(255) |
| `suffix` | varchar(40) |
| `company` | varchar(255) |
| `street` | varchar(255) |
| `city` | varchar(255) |
| `region` | varchar(255) |
| `postcode` | varchar(255) |
| `fax` | varchar(255) |

#### Tabella `sales_flat_quote_payment`

La tabella `sales_flat_quote_payment` include informazioni sulla carta di credito e altre informazioni sulle transazioni.

| Colonna | Tipo di dati |
| --- | --- |
| `cc_last_4` | varchar(255) |
| `cc_owner` | varchar(255) |
| `cc_exp_month` | smallint(5) |
| `cc_exp_year` | smallint(5) |
| `cc_ss_owner` | varchar(255) |
| `cc_ss_start_month` | smallint(5) |
| `cc_ss_start_year` | smallint(5) |

### Archiviare i dati

Le tabelle e le colonne seguenti contengono informazioni sui clienti:

| Tabella | Colonna | Tipo di dati |
| --- | --- | --- |
| `enterprise_sales_creditmemo_grid_archive` | `billing_name` | varchar(255) |
| `enterprise_sales_invoice_grid_archive` | `billing_name` | varchar(255) |
| `enterprise_sales_order_grid_archive` | `billing_name` | varchar(255) |
| `enterprise_sales_order_grid_archive` | `customer_id` | int(10) |
| `enterprise_sales_order_grid_archive` | `shipping_name` | varchar(255) |
| `enterprise_sales_shipment_grid_archive` | `shipping_name` | varchar(255) |

### Dati di vendita

Le tabelle e le colonne seguenti contengono informazioni sui clienti:

| Tabella | Colonna | Tipo di dati |
| --- | --- | --- |
| `sales_flat_creditmemo_grid` | `billing_name` | varchar(255) |
| `sales_flat_invoice_grid` | `billing_name` | varchar(255) |

### Dati RMA

Le seguenti tabelle e colonne RMA contengono informazioni sui clienti:

| Tavolo | Colonna | Tipo di dati |
| --- | --- | --- |
| `enterprise_rma` | `customer_custom_email` | Varchar(255) |
| `enterprise_rma_grid` | `customer_id` | numero intero(10) |
| `enterprise_rma_grid` | `customer_name` | Varchar(255) |

### Dati vari

Le tabelle e le colonne seguenti contengono informazioni sui clienti:

| Tavolo | Colonna | Tipo di dati |
| --- | --- | --- |
| `core_email_queue_recipients` | `recipient_email` | varchar(128) |
| `core_email_queue_recipients` | `recipient_name` | varchar(255) |
| `customer_flowpassword` | `email` | varchar(255) |
| `customer_flowpassword` | `ip` | varchar(50) |
| `enterprise_giftregistry_person` | `email` | varchar(150) |
| `enterprise_giftregistry_person` | `firstname` | varchar(100) |
| `enterprise_giftregistry_person` | `lastname` | varchar(100) |
| `enterprise_giftregistry_person` | `middlename` | text |
| `enterprise_invitation` | `customer_id` | int(10) |
| `enterprise_invitation` | `email` | varchar(255) |
| `enterprise_invitation` | `referral_id` | int(10) |
| `enterprise_reminder_rule_coupon` | `customer_id` | int(10) |
| `enterprise_reminder_rule_coupon` | `emails_failed` | smallint(5) |
| `enterprise_scheduled_operations` | `email_receiver` | varchar(150) |
| `enterprise_scheduled_operations` | `email_sender` | varchar(150) |
| `gift_message` | `customer_id` | int(10) |
| `gift_message` | `recipient` | varchar(255) |
| `gift_message` | `sender` | Varchar(255) |
| `newsletter_subscriber` | `customer_id` | numero intero(10) |
| `newsletter_subscriber` | `subscriber_email` | varchar(150) |
| `persistent_session` | `customer_id` | numero intero(10) |
| `persistent_session` | `info` | Testo |
| `poll_vote` | `customer_id` | numero intero(10) |
| `poll_vote` | `ip_address` | Binario(16) |
| `rating_option_vote` | `customer_id` | numero intero(10) |
| `rating_option_vote` | `remote_ip` | Varchar(50) |
| `rating_option_vote` | `remote_ip_long` | Varibinario(516) |
| `send_friend_log` | `ip` | varbinary(16) |

Altre tabelle che fanno riferimento al cliente:

- `catalog_compare_item`
- `downloadable_link_purchased`
- `enterprise_customerbalance`
- `enterprise_customersegment_customer`
- `enterprise_giftregistry_entity`
- `enterprise_reminder_rule_log`
- `enterprise_reward`
- `log_customer`
- `log_visitor_online`
- `oauth_token`
- `product_alert_price`
- `product_alert_stock`
- `report_compared_product_index`
- `report_viewed_product_index`
- `review_detail`
- `sales_billing_agreement`
- `sales_flat_shipment`
- `sales_recurring_profile`
- `salesrule_coupon_usage`
- `salesrule_customer`
- `tag`
- `tag_relation`
- `wishlist`
