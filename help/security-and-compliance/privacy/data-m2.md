---
title: Riferimento per le informazioni personali del cliente (versione 2.x)
description: Scopri i diagrammi di flusso dei dati e le mappature delle entità del database per le informazioni personali dei clienti in Adobe Commerce 2.x.
exl-id: f08f4f93-a7b6-4c43-bc07-f159822dc528
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 0%

---

# Riferimento per le informazioni personali del cliente (versione 2.x)

>[!NOTE]
>
>Questo è uno di una serie di argomenti per aiutare i commercianti e gli sviluppatori di Adobe Commerce a prepararsi per il rispetto delle normative sulla privacy. Rivolgiti al tuo consulente legale per determinare se e come la tua azienda debba conformarsi ad obblighi di legge.

Utilizza i seguenti diagrammi di flusso di dati e mappature di entità di database come riferimento durante lo sviluppo di programmi di conformità per le normative sulla privacy, ad esempio:

- [RGPD](gdpr.md)
- [CCPA](ccpa.md)

## Diagrammi di flusso di dati

I diagrammi di flusso dei dati mostrano i tipi di dati che clienti e amministratori possono immettere e recuperare dalla vetrina e dall’amministratore.

### Punti di immissione dati front-end

L&#39;utente può immettere le informazioni relative al cliente, all&#39;indirizzo e al pagamento al momento della registrazione per un conto, durante il pagamento ed eventi simili.

![Punti di immissione dati front-end](../../assets/security-compliance/frontend-data-entry-points.svg)

### Punti di accesso ai dati front-end

Adobe Commerce carica le informazioni del cliente quando il cliente effettua l’accesso e visualizza diverse pagine o effettua il check-out.

![Punti di accesso ai dati front-end](../../assets/security-compliance/frontend-data-access-points.svg)

### Punti di immissione dati back-end

Un esercente può inserire informazioni sul cliente, dati sull’indirizzo e dati di pagamento al momento della creazione di un cliente o di un ordine dall’amministratore.

![Punti di immissione dati back-end](../../assets/security-compliance/backend-data-entry-points.svg)

### Punti di accesso ai dati back-end

Adobe Commerce carica le informazioni sul cliente quando un commerciante visualizza diversi tipi di griglie, fa clic su una griglia per visualizzare informazioni dettagliate ed esegue varie altre attività.

![Punti di accesso ai dati back-end](../../assets/security-compliance/backend-data-access-points.svg)

## Entità di database

Adobe Commerce memorizza principalmente le informazioni specifiche del cliente in tabelle relative a clienti, indirizzi, ordini, preventivi e pagamenti. Altre tabelle contengono riferimenti all’ID cliente.

### Dati dei clienti

Adobe Commerce può essere configurato per memorizzare i seguenti attributi del cliente:

- Data di nascita
- E-mail
- Nome
- Genere
- Cognome
- Secondo nome/iniziale
- Prefisso nome
- Suffisso nome

>[!NOTE]
>
>In linea con le attuali best practice sulla sicurezza e la privacy, assicurati di essere a conoscenza di eventuali rischi legali e di sicurezza associati alla memorizzazione della data di nascita completa dei clienti (mese, giorno, anno) insieme ad altri identificatori personali, come il nome completo, prima di raccogliere o elaborare tali dati.

#### `customer_entity` e riferimenti &quot;customer_entity&quot;

Le seguenti colonne nella `customer_entity` la tabella contiene informazioni sul cliente:

| Colonna | Tipo di dati |
| ------------ | ------------ |
| `email` | varchar(255) |
| `prefix` | varchar(40) |
| `firstname` | varchar(255) |
| `middlename` | varchar(255) |
| `lastname` | varchar(255) |
| `suffix` | varchar(40) |
| `dob` | data |
| `gender` | smallint(5) |

Queste tabelle fanno riferimento a `customer_entity` e può contenere attributi cliente personalizzati:

| Tabella | Colonna | Tipo di dati |
| -------------------------- | ------- | ------------- |
| `customer_entity_datetime` | `value` | datetime |
| `customer_entity_decimal` | `value` | decimal(12,4) |
| `customer_entity_int` | `value` | int(11) |
| `customer_entity_text` | `value` | text |
| `customer_entity_varchar` | `value` | varchar(255) |

#### `customer_grid_flat` tabella

Le seguenti colonne nella `customer_grid_flat` la tabella contiene informazioni sul cliente:

| Colonna | Tipo di dati |
| -------------------- | ------------ |
| `name` | text |
| `email` | varchar(255) |
| `dob` | data |
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

Adobe Commerce memorizza i seguenti attributi cliente:

- Città
- Azienda
- Paese
- Fax
- Nome
- Cognome
- Secondo nome/iniziale
- Prefisso nome
- Suffisso nome
- Numero di telefono
- Stato/Provincia
- ID Stato/Provincia
- Indirizzo
- Partita IVA
- CAP

#### `customer_address_entity` e `customer_address_entity` riferimenti

Le seguenti colonne nella `customer_address_entity` la tabella contiene informazioni sul cliente:

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

Queste tabelle fanno riferimento a `customer_address_entity` e può contenere attributi cliente personalizzati:

| Tabella | Colonna | Tipo di dati |
| ---------------------------------- | ------- | ------------- |
| `customer_address_entity_datetime` | `value` | datetime |
| `customer_address_entity_decimal` | `value` | decimal(12,4) |
| `customer_address_entity_int` | `value` | int(11) |
| `customer_address_entity_text` | `value` | text |
| `customer_address_entity_varchar` | `value` | varchar(255) |

### Dati ordine

Il `sales_order` e le tabelle correlate contengono il nome del cliente, gli indirizzi di fatturazione e spedizione e i dati correlati.

#### `sales_order` tabella

Le seguenti colonne nella `sales_order` la tabella contiene informazioni sul cliente:

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

Il `sales_order_address` contiene l&#39;indirizzo del cliente.

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

Le seguenti colonne nella `sales_order_grid` la tabella contiene informazioni sul cliente:

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

### Dati offerta

I preventivi contengono il nome, l&#39;indirizzo e-mail e le informazioni correlate di un cliente.

#### `quote` tabella

Le seguenti colonne nella `quote` la tabella contiene informazioni sul cliente:

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

Le seguenti colonne nella `quote_address` la tabella contiene informazioni sul cliente:

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

Il `sales_order_payment` la tabella include le informazioni sulla carta di credito e altre informazioni sulle transazioni.

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

### Dati invito

Adobe Commerce può essere configurato in modo che i clienti possano inviare inviti a vendite ed eventi privati.

#### `magento_invitation` tabella

Il `magento_invitation` la tabella contiene l’ID cliente, l’e-mail e l’ID di riferimento.

| Colonna | Tipo di dati |
| ------------- | ------------ |
| `customer_id` | int(10) |
| `email` | varchar(255) |
| `referral_id` | int(10) |

#### `magento_invitation_track` tabella

Il `magento_invitation_track` La tabella contiene anche informazioni sul cliente.

| Colonna | Tipo di dati |
| ------------- | --------- |
| `inviter_id` | int(10) |
| `referral_id` | int(10) |

### Tabelle varie che fanno riferimento al cliente

Le tabelle seguenti contengono `customer_id` colonna:

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
