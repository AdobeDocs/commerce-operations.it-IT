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

Utilizzare i diagrammi di flusso di dati e i mapping delle entità del database seguenti come riferimento quando si sviluppano programmi di conformità per le normative sulla privacy, ad esempio:

- [RGPD](gdpr.md)
- [CCPA](ccpa.md)

## Diagrammi di flusso di dati

I diagrammi di flusso dei dati mostrano i tipi di dati che clienti e amministratori possono immettere e recuperare dalla vetrina e dall’amministratore.

### Punti di immissione dati front-end

L&#39;utente può immettere le informazioni relative al cliente, all&#39;indirizzo e al pagamento al momento della registrazione per un conto, durante il pagamento ed eventi simili.

![Punti di ingresso dati front-end](../../assets/security-compliance/frontend-data-entry-points.svg)

### Punti di accesso ai dati front-end

Adobe Commerce carica le informazioni del cliente quando il cliente effettua l’accesso e visualizza diverse pagine o effettua il check-out.

![Dati frontend accesso punti](../../assets/security-compliance/frontend-data-access-points.svg)

### Punti di immissione dati back-end

Un esercente può inserire informazioni sul cliente, dati sull’indirizzo e dati di pagamento al momento della creazione di un cliente o di un ordine dall’amministratore.

![Punti di ingresso dati back-end](../../assets/security-compliance/backend-data-entry-points.svg)

### Punti di accesso ai dati back-end

Adobe Commerce carica le informazioni sul cliente quando un commerciante visualizza diversi tipi di griglie, fa clic su una griglia per visualizzare informazioni dettagliate ed esegue varie altre attività.

![Punti di accesso ai dati back-end](../../assets/security-compliance/backend-data-access-points.svg)

## Entità di database

Adobe Systems Commerce memorizza principalmente informazioni specifiche del cliente nelle tabelle di clienti, indirizzi, ordini, preventivi e pagamenti. Altre tabelle contengono riferimenti all&#39;ID cliente.

### Dati cliente

Adobe Systems Commerce può essere configurato per store i seguenti attributi del cliente:

- Data di nascita
- E-mail
- Nome di battesimo
- Genere
- Cognome
- Secondo nome/iniziale
- Prefisso nome
- Suffisso nome

>[!NOTE]
>
>In linea con le attuali best practice in materia di sicurezza e privacy, assicurati di essere a conoscenza di eventuali rischi legali e di sicurezza associati alla memorizzazione della data di nascita completa dei clienti (mese, giorno, anno) insieme ad altri identificatori personali, come il nome completo, prima di raccogliere o elaborare tali dati.

#### `customer_entity` e riferimenti &quot;customer_entity&quot;

Le colonne seguenti della tabella contengono informazioni `customer_entity` sui clienti:

| Colonna | Tipo di dati |
| ------------ | ------------ |
| `email` | Varchar(255) |
| `prefix` | varchar(40) |
| `firstname` | Varchar(255) |
| `middlename` | Varchar(255) |
| `lastname` | Varchar(255) |
| `suffix` | varchar(40) |
| `dob` | dattero |
| `gender` | smallint(5) |

Queste tabelle fanno riferimento `customer_entity` e possono contenere attributi personalizzati del cliente:

| Tavolo | Colonna | Tipo di dati |
| -------------------------- | ------- | ------------- |
| `customer_entity_datetime` | `value` | datetime |
| `customer_entity_decimal` | `value` | decimal(12,4) |
| `customer_entity_int` | `value` | int(11) |
| `customer_entity_text` | `value` | Testo |
| `customer_entity_varchar` | `value` | Varchar(255) |

#### `customer_grid_flat` tavolo

Le colonne seguenti della tabella contengono informazioni `customer_grid_flat` sui clienti:

| Colonna | Tipo di dati |
| -------------------- | ------------ |
| `name` | text |
| `email` | varchar(255) |
| `dob` | data |
| `gender` | int(11) |
| `shipping_full` | text |
| `billing_full` | Testo |
| `billing_firstname` | varchar(255) |
| `billing_lastname` | varchar(255) |
| `billing_telephone` | varchar(255) |
| `billing_postcode` | varchar(255) |
| `billing_country_id` | varchar(255) |
| `billing_region` | varchar(255) |
| `billing_city` | varchar(255) |
| `billing_fax` | varchar(255) |
| `billing_vat_id` | varchar(255) |
| `billing_company` | Varchar(255) |

### Dati indirizzo

Adobe Commerce memorizza i seguenti attributi cliente:

- Città
- Azienda
- Paese
- Fax
- Nome di battesimo
- Cognome
- Secondo nome/iniziale
- Prefisso nome
- Suffisso nome
- Numero di telefono
- Stato/Provincia
- ID stato/provincia
- Indirizzo
- Partita IVA
- Code postale/postale

#### `customer_address_entity` e `customer_address_entity` riferimenti

Le colonne seguenti della tabella contengono informazioni `customer_address_entity` sui clienti:

| Colonna | Tipo di dati |
| ------------ | ------------ |
| `city` | Varchar(255) |
| `company` | Varchar(255) |
| `country_id` | Varchar(255) |
| `fax` | Varchar(255) |
| `firstname` | Varchar(255) |
| `lastname` | Varchar(255) |
| `middlename` | Varchar(255) |
| `postcode` | Varchar(255) |
| `region` | Varchar(255) |
| `region_id` | numero intero(10) |
| `street` | Testo |
| `suffix` | varchar(40) |
| `telephone` | varchar(255) |
| `vat_id` | varchar(255) |

Queste tabelle fanno riferimento a `customer_address_entity` e possono contenere attributi cliente personalizzati:

| Tabella | Colonna | Tipo di dati |
| ---------------------------------- | ------- | ------------- |
| `customer_address_entity_datetime` | `value` | datetime |
| `customer_address_entity_decimal` | `value` | decimale(12,4) |
| `customer_address_entity_int` | `value` | numero intero(11) |
| `customer_address_entity_text` | `value` | Testo |
| `customer_address_entity_varchar` | `value` | varchar(255) |

### Dati ordine

`sales_order` e tabelle correlate contengono il nome del cliente, gli indirizzi di fatturazione e spedizione e i dati correlati.

#### Tabella `sales_order`

Le colonne seguenti della tabella `sales_order` contengono informazioni sul cliente:

| Colonna | Tipo di dati |
| --------------------- | ------------ |
| `customer_dob` | datetime |
| `customer_email` | Varchar(128) |
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

#### Tabella `sales_order_address`

La tabella `sales_order_address` contiene l&#39;indirizzo del cliente.

| Colonna | Tipo di dati |
| --------------------- | ------------ |
| `customer_address_id` | numero intero(11) |
| `quote_address_id` | numero intero(11) |
| `region_id` | numero intero(11) |
| `customer_id` | numero intero(11) |
| `fax` | Varchar(255) |
| `region` | Varchar(255) |
| `postcode` | Varchar(255) |
| `lastname` | Varchar(255) |
| `street` | Varchar(255) |
| `city` | Varchar(255) |
| `email` | Varchar(255) |
| `telephone` | Varchar(255) |
| `country_id` | varchar(2) |
| `firstname` | Varchar(255) |
| `suffix` | Varchar(255) |
| `company` | Varchar(255) |

#### `sales_order_grid` tavolo

Le colonne seguenti della tabella contengono informazioni `sales_order_grid` sui clienti:

| Colonna | Tipo di dati |
| ---------------------- | ------------ |
| `customer_id` | numero intero(10) |
| `shipping_name` | Varchar(255) |
| `billing_name` | Varchar(255) |
| `billing_address` | Varchar(255) |
| `shipping_address` | Varchar(255) |
| `shipping_information` | Varchar(255) |
| `customer_email` | varchar(255) |
| `customer_name` | varchar(255) |

### Dati offerta

I preventivi contengono il nome, l&#39;indirizzo e-mail e le informazioni correlate di un cliente.

#### `quote` tavolo

Le colonne seguenti della tabella contengono informazioni `quote` sui clienti:

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
| `customer_taxvat` | Varchar(255) |
| `customer_gender` | varchar(255) |

#### Tabella `quote_address`

Le colonne seguenti della tabella `quote_address` contengono informazioni sul cliente:

| Colonna | Tipo di dati |
| ------------- | ------------ |
| `customer_id` | int(10) |
| `email` | varchar(255) |
| `prefix` | varchar(40) |
| `firstname` | varchar(255) |
| `middlename` | varchar(40) |
| `lastname` | varchar(255) |
| `suffix` | varchar(40) |
| `company` | Varchar(255) |
| `street` | Varchar(255) |
| `city` | Varchar(255) |
| `region` | Varchar(255) |
| `region_id` | numero intero(10) |
| `postcode` | varchar(20) |
| `country_id` | varchar(30) |
| `telephone` | Varchar(255) |
| `fax` | Varchar(255) |

### Dati di pagamento

La `sales_order_payment` tabella include informazioni sulla scheda creditizia e altre informazioni sulle transazioni.

| Colonna | Tipo di dati |
| ------------------------ | ------------ |
| `cc_exp_month` | varchar(12) |
| `echeck_bank_name` | Varchar(128) |
| `cc_last_4` | varchar(100) |
| `cc_owner` | Varchar(128) |
| `po_number` | varchar(32) |
| `cc_exp_year` | varchar(4) |
| `echeck_routing_number` | varchar(32) |
| `cc_debug_response_body` | varchar(32) |
| `echeck_account_name` | varchar(32) |
| `cc_number_enc` | Varchar(128) |
| `additional_information` | Testo |

### Dati dell&#39;invito

Adobe Systems Commerce può essere configurato in modo che i clienti possano inviare inviti a vendite ed eventi privati.

#### `magento_invitation` tavolo

La `magento_invitation` tabella contiene l&#39;ID cliente, l&#39;e-mail e l&#39;ID riferimento.

| Colonna | Tipo di dati |
| ------------- | ------------ |
| `customer_id` | numero intero(10) |
| `email` | varchar(255) |
| `referral_id` | int(10) |

#### Tabella `magento_invitation_track`

La tabella `magento_invitation_track` contiene anche informazioni sul cliente.

| Colonna | Tipo di dati |
| ------------- | --------- |
| `inviter_id` | numero intero(10) |
| `referral_id` | numero intero(10) |

### Tabelle varie che fanno riferimento al cliente

Le tabelle seguenti contengono una colonna `customer_id`:

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
