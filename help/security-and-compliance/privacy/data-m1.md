---
title: Riferimento per le informazioni personali dei clienti (versione 1.x)
description: Scopri le mappature del flusso di dati e delle entità del database per le informazioni personali dei clienti in Magento 1.x.
source-git-commit: 0640b59cc529123911537475bbfc179c917ac258
workflow-type: tm+mt
source-wordcount: '609'
ht-degree: 0%

---


# Riferimento per le informazioni personali dei clienti (versione 1.x)

>[!NOTE]
>
>Questo è uno degli argomenti trattati in una serie di argomenti che aiutano i commercianti e gli sviluppatori di Adobe Commerce e Magenti Open Source a prepararsi per la conformità alle normative sulla privacy. Rivolgiti al tuo consulente legale per determinare se e come la tua azienda debba rispettare eventuali obblighi legali.

Utilizza i seguenti diagrammi di flusso di dati e mappature delle entità di database come riferimento durante lo sviluppo di programmi di conformità per le normative sulla privacy come:

- [RGPD](gdpr.md)
- [CCPA](ccpa.md)

## Diagrammi di flusso di dati

I diagrammi del flusso di dati mostrano i tipi di dati che i clienti e gli amministratori possono immettere e recuperare nella vetrina e in Admin.

### Punti di entrata dati frontalieri

Un utente può inserire informazioni su clienti, indirizzi e pagamenti durante la registrazione a un account, durante il pagamento e eventi simili.

![Punti di entrata dati frontalieri](../../assets/security-compliance/frontend-data-entry-points.svg)

### Punti di accesso ai dati frontalieri

Commerce carica le informazioni sui clienti quando il cliente effettua l’accesso e visualizza diverse pagine o estrazioni diverse.

![Punti di accesso ai dati frontalieri](../../assets/security-compliance/frontend-data-access-points.svg)

### Punti di ingresso dati di backend

Un commerciante può inserire informazioni su clienti, indirizzi e pagamenti dall&#39;amministratore per creare un cliente o un ordine.

![Punti di ingresso dati di backend](../../assets/security-compliance/backend-data-entry-points.svg)

### Punti di accesso ai dati di back-end

Commerce carica le informazioni sui clienti quando un commerciante visualizza diversi tipi di griglie, fa clic su una griglia per visualizzare informazioni dettagliate ed esegue varie altre attività.

![Punti di accesso ai dati di back-end](../../assets/security-compliance/backend-data-access-points.svg)

## Entità di database

Il Magento 1 memorizza le informazioni sui clienti in tabelle di database, vendite e altre tabelle di database.

### Dati dei clienti

Il Magento 1 memorizza le informazioni sui clienti nel `customer_entity` e `customer_address_entity` tabelle. Entrambe queste tabelle dispongono di diverse tabelle di riferimento che possono contenere attributi personalizzati del cliente.

#### `customer_entity` e tabelle di riferimento

Le colonne seguenti nel `customer_entity`La tabella contiene informazioni sui clienti:

| Colonna | Tipo di dati |
| --- | --- |
| `email` | varchar(255) |

Riferimento alle tabelle `customer_entity` e può contenere attributi personalizzati del cliente:

| Tabella | Colonna | Tipo di dati |
| --- | --- | --- |
| `customer_entity_datetime` | `value` | datetime |
| `customer_entity_decimal` | `value` | decimale(12,4) |
| `customer_entity_int` | `value` | int(11) |
| `customer_entity_text` | `value` | text |
| `customer_entity_varchar` | `value` | varchar(255) |

#### `customer_address_entity` e tabelle di riferimento

Riferimento alle tabelle seguenti `customer_address_entity` e può contenere attributi personalizzati del cliente:

| Tabella | Colonna | Tipo di dati |
| --- | --- | --- |
| `customer_address_entity_datetime` | `value` | datetime |
| `customer_address_entity_decimal` | `value` | decimale(12,4) |
| `customer_address_entity_int` | `value` | int(11) |
| `customer_address_entity_text` | `value` | text |
| `customer_address_entity_varchar` | `value` | varchar(255) |

### Dati ordine

La `sales_flat_order` e le tabelle correlate contengono il nome del cliente, gli indirizzi di fatturazione e spedizione e le relative informazioni.

#### `sales_flat_order` tabella

Le colonne seguenti nel `sales_order` La tabella contiene informazioni sui clienti:

| Colonna | Tipo di dati |
| --- | --- |
| `customer_id` | int(10) |
| `customer_email` | varchar(128) |
| `customer_firstname` | varchar(128) |
| `customer_gender` | int(11) |
| `customer_lastname` | varchar(128) |
| `customer_middlename` | varchar(128) |
| `customer_prefix` | varchar(32) |
| `customer_suffix` | varchar(32) |
| `customer_taxvat` | varchar(32) |
| `remote_ip` | varchar(32) |

#### `sales_flat_order_address` tabella

La `sales_flat_order_address` contiene l&#39;indirizzo del cliente.

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

#### `sales_flat_order_grid` tabella

Le colonne seguenti nel `sales_flat_order_grid` La tabella contiene informazioni sui clienti:

| Colonna | Tipo di dati |
| --- | --- |
| `customer_id` | int(10) |
| `shipping_name` | varchar(255) |
| `billing_name` | varchar(255) |

#### `sales_flat_order_payment` tabella

Le colonne seguenti nel `sales_flat_order_payment` La tabella contiene informazioni sui clienti:

| Colonna | Tipo di dati |
| --- | --- |
| `cc_exp_month` | varchar(255) |
| `cc_ss_start_year` | varchar(255) |
| `echeck_bank_name` | varchar(128) |
| `echeck_type` | varchar(255) |
| `cc_ss_start_month` | varchar(255) |
| `cc_owner` | varchar(255) |
| `cc_exp_year` | varchar(255) |
| `echeck_routing_number` | varchar(255) |
| `echeck_account_name` | varchar(255) |

### Dati del preventivo

I preventivi contengono il nome, l&#39;e-mail, l&#39;indirizzo e le informazioni relative di un cliente.

#### `sales_flat_quote` tabella

Le colonne seguenti nel `sales_flat_quote` La tabella contiene informazioni sui clienti:

| Colonna | Tipo di dati |
| --- | --- |
| `customer_id` | int(10) |
| `customer_tax_class_id` | int(10) |
| `customer_group_id` | int(10) |
| `customer_email` | varchar(255) |
| `customer_prefix` | varchar(40) |
| `customer_firstname` | varchar(255) |
| `customer_middlename` | varchar(40) |
| `customer_lastname` | varchar(255) |
| `customer_suffix` | varchar(40) |
| `customer_dob` | datetime |
| `customer_note` | varchar(255) |
| `remote_ip` | varchar(255) |
| `customer_gender` | varchar(255) |

#### `sales_flat_quote_address` tabella

Le colonne seguenti nel `sales_flat_quote_address` La tabella contiene informazioni sui clienti:

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

#### `sales_flat_quote_payment` tabella

La `sales_flat_quote_payment` la tabella include informazioni sulla carta di credito e altre informazioni sulle transazioni.

| Colonna | Tipo di dati |
| --- | --- |
| `cc_last_4` | varchar(255) |
| `cc_owner` | varchar(255) |
| `cc_exp_month` | piccolo(5) |
| `cc_exp_year` | piccolo(5) |
| `cc_ss_owner` | varchar(255) |
| `cc_ss_start_month` | piccolo(5) |
| `cc_ss_start_year` | piccolo(5) |

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

### Dati sulle vendite

Le tabelle e le colonne seguenti contengono informazioni sui clienti:

| Tabella | Colonna | Tipo di dati |
| --- | --- | --- |
| `sales_flat_creditmemo_grid` | `billing_name` | varchar(255) |
| `sales_flat_invoice_grid` | `billing_name` | varchar(255) |

### Dati RMA

Le tabelle e colonne RMA seguenti contengono informazioni sui clienti:

| Tabella | Colonna | Tipo di dati |
| --- | --- | --- |
| `enterprise_rma` | `customer_custom_email` | varchar(255) |
| `enterprise_rma_grid` | `customer_id` | int(10) |
| `enterprise_rma_grid` | `customer_name` | varchar(255) |

### Dati vari

Le tabelle e le colonne seguenti contengono informazioni sui clienti:

| Tabella | Colonna | Tipo di dati |
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
| `enterprise_reminder_rule_coupon` | `emails_failed` | piccolo(5) |
| `enterprise_scheduled_operations` | `email_receiver` | varchar(150) |
| `enterprise_scheduled_operations` | `email_sender` | varchar(150) |
| `gift_message` | `customer_id` | int(10) |
| `gift_message` | `recipient` | varchar(255) |
| `gift_message` | `sender` | varchar(255) |
| `newsletter_subscriber` | `customer_id` | int(10) |
| `newsletter_subscriber` | `subscriber_email` | varchar(150) |
| `persistent_session` | `customer_id` | int(10) |
| `persistent_session` | `info` | text |
| `poll_vote` | `customer_id` | int(10) |
| `poll_vote` | `ip_address` | varbinary(16) |
| `rating_option_vote` | `customer_id` | int(10) |
| `rating_option_vote` | `remote_ip` | varchar(50) |
| `rating_option_vote` | `remote_ip_long` | varbinary(516) |
| `send_friend_log` | `ip` | varbinary(16) |

Altre tabelle che fanno riferimento a Cliente:

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
