---
title: Riferimento per le informazioni personali dei clienti (versione 2.x)
description: Scopri i diagrammi del flusso di dati e le mappature delle entità del database per le informazioni personali dei clienti in Adobe Commerce e Magenti Open Source 2.x.
source-git-commit: 0640b59cc529123911537475bbfc179c917ac258
workflow-type: tm+mt
source-wordcount: '759'
ht-degree: 0%

---


# Riferimento per le informazioni personali dei clienti (versione 2.x)

>[!NOTE]
>
>Questo è uno degli argomenti trattati in una serie di argomenti che aiutano i commercianti e gli sviluppatori di Adobe Commerce e Magenti Open Source a prepararsi per la conformità alle normative sulla privacy. Rivolgiti al tuo consulente legale per determinare se e come la tua azienda debba rispettare eventuali obblighi legali.

Utilizza i seguenti diagrammi di flusso di dati e mappature delle entità di database come riferimento durante lo sviluppo di programmi di conformità per le normative sulla privacy come:

- [RGPD](gdpr.md)
- [CCPA](ccpa.md)

## Diagrammi di flusso dei dati

I diagrammi del flusso di dati mostrano i tipi di dati che clienti e amministratori possono immettere e recuperare dalla vetrina e dall’amministratore.

### Punti di entrata dati frontalieri

Un utente può inserire informazioni su clienti, indirizzi e pagamenti durante la registrazione a un account, durante il pagamento e eventi simili.

![Punti di entrata dati frontalieri](../../assets/security-compliance/frontend-data-entry-points.svg)

### Punti di accesso ai dati frontalieri

Adobe Commerce e Magenti Open Source caricano le informazioni sui clienti quando il cliente effettua l’accesso e visualizza diverse pagine o effettua un Check-Out.

![Punti di accesso ai dati frontalieri](../../assets/security-compliance/frontend-data-access-points.svg)

### Punti di ingresso dati di backend

Quando crei un cliente o un ordine dall&#39;amministratore, un commerciante può inserire informazioni sul cliente, dati sull&#39;indirizzo e dati di pagamento.

![Punti di ingresso dati di backend](../../assets/security-compliance/backend-data-entry-points.svg)

### Punti di accesso ai dati di back-end

Adobe Commerce e Magenti Open Source caricano le informazioni sui clienti quando un commerciante visualizza diversi tipi di griglie, fa clic su una griglia per visualizzare informazioni dettagliate ed esegue varie altre attività.

![Punti di accesso ai dati di back-end](../../assets/security-compliance/backend-data-access-points.svg)

## Entità di database

Adobe Commerce e Magenti Open Source memorizzano principalmente informazioni specifiche per il cliente in tabelle relative a clienti, indirizzi, ordini, preventivi e pagamenti. Altre tabelle contengono riferimenti all’ID cliente.

### Dati dei clienti

Adobe Commerce e Magenti Open Source possono essere configurati per memorizzare i seguenti attributi del cliente:

- Data di nascita
- E-mail
- Nome
- Genere
- Cognome
- Nome/Iniziale
- Prefisso nome
- Suffisso nome

>[!NOTE]
>
>In linea con le best practice in materia di sicurezza e privacy correnti, assicurati di essere a conoscenza di eventuali rischi legali e di sicurezza associati all&#39;archiviazione della data completa di nascita (mese, giorno, anno) del cliente insieme ad altri identificatori personali, come il nome completo, prima di raccogliere o elaborare tali dati.

#### `customer_entity` e riferimenti a &quot;customer_entity&quot;

Le colonne seguenti nel `customer_entity` La tabella contiene informazioni sui clienti:

| Colonna | Tipo di dati |
| ------------ | ------------ |
| `email` | varchar(255) |
| `prefix` | varchar(40) |
| `firstname` | varchar(255) |
| `middlename` | varchar(255) |
| `lastname` | varchar(255) |
| `suffix` | varchar(40) |
| `dob` | date |
| `gender` | piccolo(5) |

Riferimento alle tabelle `customer_entity` e può contenere attributi personalizzati del cliente:

| Tabella | Colonna | Tipo di dati |
| -------------------------- | ------- | ------------- |
| `customer_entity_datetime` | `value` | datetime |
| `customer_entity_decimal` | `value` | decimale(12,4) |
| `customer_entity_int` | `value` | int(11) |
| `customer_entity_text` | `value` | text |
| `customer_entity_varchar` | `value` | varchar(255) |

#### `customer_grid_flat` tabella

Le colonne seguenti nel `customer_grid_flat` La tabella contiene informazioni sui clienti:

| Colonna | Tipo di dati |
| -------------------- | ------------ |
| `name` | text |
| `email` | varchar(255) |
| `dob` | date |
| `gender` | int(11) |
| `shipping_full` | text |
| `billing_full` | text |
| `billing_firstname` | varchar(255) |
| `billing_lastname` | varchar(255) |
| `billing_telephone` | varchar(255) |
| `billing_postcode` | varchar(255) |
| `billing_country_id` | varchar(255) |
| `billing_region` | varchar(255) |
| `billing_city` | varchar(255) |
| `billing_fax` | varchar(255) |
| `billing_vat_id` | varchar(255) |
| `billing_company` | varchar(255) |

### Dati indirizzo

Adobe Commerce e Magenti Open Source memorizzano i seguenti attributi del cliente:

- Città
- Azienda
- Paese
- Fax
- Nome
- Cognome
- Nome/Iniziale
- Prefisso nome
- Suffisso nome
- Numero di telefono
- Provincia
- ID stato/provincia
- Indirizzo via
- Numero IVA
- Codice postale

#### `customer_address_entity` e `customer_address_entity` riferimenti

Le colonne seguenti nel `customer_address_entity` La tabella contiene informazioni sui clienti:

| Colonna | Tipo di dati |
| ------------ | ------------ |
| `city` | varchar(255) |
| `company` | varchar(255) |
| `country_id` | varchar(255) |
| `fax` | varchar(255) |
| `firstname` | varchar(255) |
| `lastname` | varchar(255) |
| `middlename` | varchar(255) |
| `postcode` | varchar(255) |
| `region` | varchar(255) |
| `region_id` | int(10) |
| `street` | text |
| `suffix` | varchar(40) |
| `telephone` | varchar(255) |
| `vat_id` | varchar(255) |

Riferimento alle tabelle `customer_address_entity` e può contenere attributi personalizzati del cliente:

| Tabella | Colonna | Tipo di dati |
| ---------------------------------- | ------- | ------------- |
| `customer_address_entity_datetime` | `value` | datetime |
| `customer_address_entity_decimal` | `value` | decimale(12,4) |
| `customer_address_entity_int` | `value` | int(11) |
| `customer_address_entity_text` | `value` | text |
| `customer_address_entity_varchar` | `value` | varchar(255) |

### Dati ordine

La `sales_order` e le tabelle correlate contengono il nome del cliente, gli indirizzi di fatturazione e spedizione e i dati correlati.

#### `sales_order` tabella

Le colonne seguenti nel `sales_order` La tabella contiene informazioni sui clienti:

| Colonna | Tipo di dati |
| --------------------- | ------------ |
| `customer_dob` | datetime |
| `customer_email` | varchar(128) |
| `customer_firstname` | varchar(128) |
| `customer_gender` | int(11) |
| `customer_group_id` | int(11) |
| `customer_id` | int(10) |
| `customer_lastname` | varchar(128) |
| `customer_middlename` | varchar(128) |
| `customer_prefix` | varchar(32) |
| `customer_suffix` | varchar(32) |
| `customer_taxvat` | varchar(32) |
| `quote_address_id` | int(11) |
| `remote_ip` | varchar(32) |
| `x_forwarded_for` | varchar(32) |

#### `sales_order_address` tabella

La `sales_order_address` contiene l&#39;indirizzo del cliente.

| Colonna | Tipo di dati |
| --------------------- | ------------ |
| `customer_address_id` | int(11) |
| `quote_address_id` | int(11) |
| `region_id` | int(11) |
| `customer_id` | int(11) |
| `fax` | varchar(255) |
| `region` | varchar(255) |
| `postcode` | varchar(255) |
| `lastname` | varchar(255) |
| `street` | varchar(255) |
| `city` | varchar(255) |
| `email` | varchar(255) |
| `telephone` | varchar(255) |
| `country_id` | varchar(2) |
| `firstname` | varchar(255) |
| `suffix` | varchar(255) |
| `company` | varchar(255) |

#### `sales_order_grid` tabella

Le colonne seguenti nel `sales_order_grid` La tabella contiene informazioni sui clienti:

| Colonna | Tipo di dati |
| ---------------------- | ------------ |
| `customer_id` | int(10) |
| `shipping_name` | varchar(255) |
| `billing_name` | varchar(255) |
| `billing_address` | varchar(255) |
| `shipping_address` | varchar(255) |
| `shipping_information` | varchar(255) |
| `customer_email` | varchar(255) |
| `customer_name` | varchar(255) |

### Dati del preventivo

I preventivi contengono il nome, l&#39;e-mail, l&#39;indirizzo e le informazioni relative di un cliente.

#### `quote` tabella

Le colonne seguenti nel `quote` La tabella contiene informazioni sui clienti:

| Colonna | Tipo di dati |
| --------------------- | ------------ |
| `customer_id` | int(10) |
| `customer_email` | varchar(255) |
| `customer_prefix` | varchar(40) |
| `customer_firstname` | varchar(255) |
| `customer_middlename` | varchar(40) |
| `customer_lastname` | varchar(255) |
| `customer_dob` | datetime |
| `remote_ip` | varchar(32) |
| `customer_taxvat` | varchar(255) |
| `customer_gender` | varchar(255) |

#### `quote_address` tabella

Le colonne seguenti nel `quote_address` La tabella contiene informazioni sui clienti:

| Colonna | Tipo di dati |
| ------------- | ------------ |
| `customer_id` | int(10) |
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
| `region_id` | int(10) |
| `postcode` | varchar(20) |
| `country_id` | varchar(30) |
| `telephone` | varchar(255) |
| `fax` | varchar(255) |

### Dati di pagamento

La `sales_order_payment` la tabella include informazioni sulla carta di credito e altre informazioni sulle transazioni.

| Colonna | Tipo di dati |
| ------------------------ | ------------ |
| `cc_exp_month` | varchar(12) |
| `echeck_bank_name` | varchar(128) |
| `cc_last_4` | varchar(100) |
| `cc_owner` | varchar(128) |
| `po_number` | varchar(32) |
| `cc_exp_year` | varchar(4) |
| `echeck_routing_number` | varchar(32) |
| `cc_debug_response_body` | varchar(32) |
| `echeck_account_name` | varchar(32) |
| `cc_number_enc` | varchar(128) |
| `additional_information` | text |

### Dati dell’invito

Adobe Commerce e Magenti Open Source possono essere configurati in modo che i clienti possano inviare inviti a vendite ed eventi privati.

#### `magento_invitation` tabella

La `magento_invitation` contiene l’ID cliente, l’e-mail e l’ID di riferimento.

| Colonna | Tipo di dati |
| ------------- | ------------ |
| `customer_id` | int(10) |
| `email` | varchar(255) |
| `referral_id` | int(10) |

#### `magento_invitation_track` tabella

La `magento_invitation_track` contiene anche informazioni sui clienti.

| Colonna | Tipo di dati |
| ------------- | --------- |
| `inviter_id` | int(10) |
| `referral_id` | int(10) |

### Tabelle varie che fanno riferimento a un cliente

Le tabelle seguenti contengono un `customer_id` colonna:

- `catalog_compare_item`
- `catalog_product_frontend_action`
- `downloadable_link_purchased`
- `magento_customerbalance`
- `magento_customersegment_customer`
- `magento_reward`
- `magento_rma`
- `oauth_token`
- `paypal_billing_agreement`
- `persistent_session`
- `product_alert_price`
- `product_stock_alert`
- `report_compared_product_index`
- `report_viewed_product_index`
- `review_detail`
- `salesrule_coupon_usage`
- `salesrule_customer`
- `wishlist`
