---
title: Percorsi sensibili e specifici del sistema
description: Scopri i percorsi di configurazione sensibili e specifici per il sistema per Adobe Commerce. Scopri la configurazione sicura e la gestione delle variabili di ambiente.
feature: Configuration, System
exl-id: 127880ab-7507-4e53-8b51-dfa6557d0b18
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '4206'
ht-degree: 0%

---

# Impostazioni sensibili e specifiche del sistema

In questo argomento vengono elencati i percorsi di configurazione per le impostazioni sensibili e specifiche del sistema:

- Il comando [`magento app:config:dump`](../cli/export-configuration.md) scrive le impostazioni specifiche del sistema nel file di configurazione specifico del sistema, `app/etc/env.php`, che dovrebbe _non_ essere incluso nel controllo del codice sorgente. Scrive inoltre la configurazione condivisa per tutte le istanze di Commerce in `app/etc/config.php`. Il file _dovrebbe_ essere incluso nel controllo del codice sorgente.
- Il comando [`magento config:sensitive:set`](../cli/set-configuration-values.md) scrive le impostazioni sensibili in `app/etc/env.php`.

  È inoltre possibile impostare valori sensibili utilizzando le variabili di configurazione come descritto in [Utilizzare le variabili di ambiente per sostituire le impostazioni di configurazione](../reference/override-config-settings.md#environment-variables).

Per un elenco degli altri percorsi di configurazione, vedi:

- [Tutti i percorsi di configurazione tranne i pagamenti](../reference/config-reference-general.md)
- [Percorsi di configurazione del pagamento](../reference/config-reference-payment.md).

>[!INFO]
>
>Tutti i percorsi di configurazione elencati in questo argomento sono sensibili. La colonna `System-specific?` mostra quali valori sono anche specifici del sistema.

## Percorsi generali sensibili alle categorie e specifici del sistema

In questa sezione sono elencati i nomi delle variabili e i percorsi di configurazione disponibili per le opzioni dell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Generale**.

### Percorsi sensibili ai percorsi web e specifici del sistema

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Generale** > **Web**.

| Nome | Percorso configurazione | Supporto delle versioni di Commerce | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| URL di base | `web/unsecure/base_url` |  | | Specifico del sistema | |
| URL collegamento base | `web/unsecure/base_link_url` |  | | Specifico del sistema | |
| URL di base per file di visualizzazione statica | `web/unsecure/base_static_url` |  | | Specifico del sistema | |
| URL di base per file multimediali utente | `web/unsecure/base_media_url` |  | | Specifico del sistema | |
| URL di base sicuro | `web/secure/base_url` |  | | Specifico del sistema | |
| URL collegamento base sicuro | `web/secure/base_link_url` |  | | Specifico del sistema | |
| URL di base sicuro per file di visualizzazione statica | `web/secure/base_static_url` |  | | Specifico del sistema | |
| URL di base sicuro per file multimediali utente | `web/secure/base_media_url` |  | | Specifico del sistema | |
| URL Web predefinito | `web/default/front` |  | | Specifico del sistema | |
| URL predefinito senza indirizzamento | `web/default/no_route` |  | | Specifico del sistema | |
| Percorso cookie | `web/cookie/cookie_path` |  | | Specifico del sistema | |
| Dominio cookie | `web/cookie/cookie_domain` |  | | Specifico del sistema | |
| Durata dei cookie | `web/cookie/cookie_lifetime` |  | | Specifico del sistema | |
| Usa solo HTTP | `web/cookie/cookie_httponly` |  | | Specifico del sistema | |
| Modalità di restrizione cookie | `web/cookie/cookie_restriction` |  | | Specifico del sistema | |

{style="table-layout:auto"}

### Percorsi sensibili all’impostazione della valuta e specifici del sistema

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Generale** > **Impostazione valuta**.

| Nome | Percorso configurazione | Supporto delle versioni di Commerce | Crittografato? | Specifico per il sistema? | Sensibili? |
| --- | --- | --- | --- | --- | --- |
| Destinatario e-mail per errore | `currency/import/error_email` |  | | | Sensibile |

{style="table-layout:auto"}

### Archivia percorsi sensibili agli indirizzi e-mail e specifici del sistema

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione e-mail** > **Generale** > **Indirizzi e-mail per archivio**.

| Nome | Percorso configurazione | Supporto delle versioni di Commerce | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Nome mittente | `trans_email/ident_general/name` | | | | Sensibile |
| E-mail mittente | `trans_email/ident_general/email` |  | | | Sensibile |
| Nome mittente | `trans_email/ident_sales/name` |  | | | Sensibile |
| E-mail mittente | `trans_email/ident_sales/email` |  | | | Sensibile |
| Nome mittente | `trans_email/ident_support/name` |  | | | Sensibile |
| E-mail mittente | `trans_email/ident_support/email` |  | | | Sensibile |
| Nome mittente | `trans_email/ident_custom1/name` |  | | | Sensibile |
| E-mail mittente | `trans_email/ident_custom1/email` |  | | | Sensibile |
| Nome mittente | `trans_email/ident_custom2/name` |  | | | Sensibile |
| E-mail mittente | `trans_email/ident_custom2/email` |  | | | Sensibile |

{style="table-layout:auto"}

### Percorsi sensibili ai contatti e specifici del sistema

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Generale** > **Contatti**.

| Nome | Percorso configurazione | Supporto delle versioni di Commerce | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Invia e-mail a | `contact/email/recipient_email` |  | | | Sensibile |
| Mittente e-mail | `contact/email/sender_email_identity` |  | | | Sensibile |
| Modello e-mail | `contact/email/email_template` |  | | | Sensibile |

{style="table-layout:auto"}

### Percorsi sensibili alla generazione di rapporti e specifici per il sistema di New Relic

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Generali** > **Generazione rapporti New Relic**.

| Nome | Percorso configurazione | Supporto delle versioni di Commerce | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| ID account New Relic | `newrelicreporting/general/account_id` |  | | | Sensibile |
| ID applicazione New Relic | `newrelicreporting/general/app_id` |  | | | Sensibile |
| Chiave API New Relic | `newrelicreporting/general/api` |  | Crittografato | | Sensibile |
| Chiave API approfondimenti | `newrelicreporting/general/insights_insert_key` |  | Crittografato | | Sensibile |
| URL API NEW RELIC | `newrelicreporting/general/api_url` |  | | Specifico del sistema | Sensibile |
| URL API approfondimenti | `newrelicreporting/general/insights_api_url` |  | | Specifico del sistema | Sensibile |

{style="table-layout:auto"}

## Percorsi sensibili alle categorie e specifici del sistema dei clienti

In questa sezione sono elencati i nomi delle variabili e i percorsi di configurazione disponibili per le opzioni dell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Clienti**.

### Percorsi sensibili alla configurazione del cliente e specifici del sistema

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Clienti** > **Configurazione cliente**.

| Nome | Percorso configurazione | Supporto delle versioni di Commerce | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Dominio e-mail predefinito | `customer/create_account/email_domain` |  | | Specifico del sistema | |

{style="table-layout:auto"}

## Categoria catalogo

In questa sezione sono elencati i nomi delle variabili e i percorsi di configurazione disponibili per le opzioni dell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Catalogo**.

### Percorsi sensibili al catalogo e specifici del sistema

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Catalogo** > **Catalogo**.

| Nome | Percorso configurazione | Supporto delle versioni di Commerce | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Destinatario e-mail per errore | `catalog/productalert_cron/error_email` |  | | | Sensibile |
| Chiave API YouTube | `catalog/product_video/youtube_api_key` |  | | | Sensibile |
| Nome host server Solr | `catalog/search/solr_server_hostname` | Solo Commerce Enterprise | | Specifico del sistema | Sensibile |
| Porta server Solr | `catalog/search/solr_server_port` | Solo Commerce Enterprise | | Specifico del sistema | Sensibile |
| Nome Utente Solr Server | `catalog/search/solr_server_username` | Solo Commerce Enterprise | | Specifico del sistema | Sensibile |
| Password server Solr | `catalog/search/solr_server_password` | Solo Commerce Enterprise | | Specifico del sistema | Sensibile |
| Percorso server Solr | `catalog/search/solr_server_path` | Solo Commerce Enterprise | | Specifico del sistema | Sensibile |
| Nome host server Elasticsearch | `catalog/search/elasticsearch_server_hostname` |  | | Specifico del sistema | Sensibile |
| Porta server Elasticsearch | `catalog/search/elasticsearch_server_port` |  | | Specifico del sistema | Sensibile |
| Prefisso indice Elasticsearch | `catalog/search/elasticsearch_index_prefix` |  | | Specifico del sistema | Sensibile |
| Abilita autenticazione HTTP Elasticsearch | `catalog/search/elasticsearch_enable_auth` |  | | Specifico del sistema | |
| Nome utente HTTP Elasticsearch | `catalog/search/elasticsearch_username` |  | | Specifico del sistema | |
| Password HTTP Elasticsearch | `catalog/search/elasticsearch_password` |  | | Specifico del sistema | |
| Timeout del server Elasticsearch | `catalog/search/elasticsearch_server_timeout` |  | | Specifico del sistema | |
| Nome utente HTTP Elasticsearch | `catalog/search/elasticsearch_username` | | | Specifico del sistema | |
| Password HTTP Elasticsearch | `catalog/search/elasticsearch_password` | | | Specifico del sistema | |
| Timeout del server Elasticsearch | `catalog/search/elasticsearch_server_timeout` | | | Specifico del sistema | |
| Nome host OpenSearch Server | `catalog/search/opensearch_server_hostname` | | | Specifico del sistema | Sensibile |
| Porta OpenSearch Server | `catalog/search/opensearch_server_port` | | | Specifico del sistema | Sensibile |
| Prefisso indice OpenSearch | `catalog/search/opensearch_index_prefix` | | | Specifico del sistema | Sensibile |
| Abilita autenticazione HTTP OpenSearch | `catalog/search/opensearch_enable_auth` | | | Specifico del sistema | |
| Nome utente HTTP OpenSearch | `catalog/search/opensearch_username` | | | Specifico del sistema | |
| Password HTTP OpenSearch | `catalog/search/opensearch_password` | | | Specifico del sistema | |
| Timeout di OpenSearch Server | `catalog/search/opensearch_server_timeout` | | | Specifico del sistema | |

{style="table-layout:auto"}

>[!NOTE]
>
>Le impostazioni OpenSearch sono state introdotte in Adobe Commerce 2.4.6.

### Percorsi sensibili all’inventario e specifici per il sistema

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Catalogo** > **Inventario**.

| Nome | Percorso configurazione | Supporto versione Commerce| Crittografato? | Specifico per sistema? | Sensibile? | |
--------------|--------------|--------------|--------------|--------------|--------------| |
| Chiave API Google | `cataloginventory/source_selection_distance_based_google/api_key` | | Crittografata | | Sensibile |

### Percorsi specifici del sistema e sensibili alla mappa del sito XML

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Catalogo** > **XML Sitemap**.

| Nome | Percorso configurazione | Supporto delle versioni di Commerce | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Destinatario e-mail per errore | `sitemap/generate/error_email` |  | | | Sensibile |

{style="table-layout:auto"}

## Categoria di vendita

In questa sezione sono elencati i nomi delle variabili e i percorsi di configurazione disponibili per le opzioni dell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Vendite**.

### Impostazioni di spedizione sensibili e percorsi specifici del sistema

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Vendite** > **Impostazioni spedizione**.

| Nome | Percorso configurazione | Supporto delle versioni di Commerce | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Paese | `shipping/origin/country_id` |  | | | Sensibile |
| Regione/Stato | `shipping/origin/region_id` |  | | | Sensibile |
| CAP | `shipping/origin/postcode` |  | | | Sensibile |
| Città | `shipping/origin/city` |  | | | Sensibile |
| Indirizzo | `shipping/origin/street_line1` |  | | | Sensibile |
| Indirizzo 2 | `shipping/origin/street_line2` |  | | | Sensibile |
| Account live | `carriers/ups/is_account_live` |  | | Specifico del sistema | |

{style="table-layout:auto"}

### Percorsi sensibili alle e-mail per le vendite e specifici per il sistema

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Vendite** > **E-mail vendite**.

| Nome | Percorso configurazione | Supporto delle versioni di Commerce | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Invia copia e-mail ordine a | `sales_email/order/copy_to` |  | | | Sensibile |
| Invia la copia e-mail del commento dell&#39;ordine a | `sales_email/order_comment/copy_to` |  | | | Sensibile |
| Invia copia e-mail fattura a | `sales_email/invoice/copy_to` |  | | | Sensibile |
| Invia copia e-mail commento fattura a | `sales_email/invoice_comment/copy_to` |  | | | Sensibile |
| Invia copia e-mail spedizione a | `sales_email/shipment/copy_to` |  | | | Sensibile |
| Invia copia e-mail commento spedizione a | `sales_email/shipment_comment/copy_to` |  | | | Sensibile |
| Invia Email Nota Di Credito A | `sales_email/creditmemo/copy_to` |  | | | Sensibile |
| Invia Email Di Commento Nota Di Credito A | `sales_email/creditmemo_comment/copy_to` |  | | | Sensibile |
| Invia copia e-mail pronta per il ritiro a | `sales_email/temando_pickup/copy_to` |  | | | Sensibile |

{style="table-layout:auto"}

### Percorsi sensibili al checkout e specifici per il sistema

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Vendite** > **Pagamento**.

| Nome | Percorso configurazione | Supporto delle versioni di Commerce | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Invia copia e-mail pagamento non riuscito a | `checkout/payment_failed/copy_to` |  | | | Sensibile |

{style="table-layout:auto"}

### Percorsi sensibili alle API Google e specifici del sistema

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Vendite** > **API Google**.

| Nome | Percorso configurazione | Supporto delle versioni di Commerce | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| ID contenitore | `google/analytics/container_id` | Solo Commerce Enterprise | | | Sensibile |

{style="table-layout:auto"}

### Percorsi sensibili ai metodi di consegna e specifici del sistema

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Vendite** > **Metodi di consegna**.

| Nome | Percorso configurazione | Supporto delle versioni di Commerce | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| URL gateway | `carriers/usps/gateway_url` |  | | | Sensibile |
| URL gateway protetto | `carriers/usps/gateway_secure_url` |  | | | Sensibile |
| Titolo | `carriers/usps/title` |  | | | |
| ID utente | `carriers/usps/userid` |  | Crittografato | | Sensibile |
| Password | `carriers/usps/password` |  | Crittografato | | Sensibile |
| ID utente | `carriers/ups/username` |  | Crittografato | | Sensibile |
| Password | `carriers/ups/password` |  | Crittografato | | Sensibile |
| Numero licenza di accesso | `carriers/ups/access_license_number` |  | Crittografato | | Sensibile |
| URL XML di tracciamento | `carriers/ups/tracking_xml_url` |  | | | Sensibile |
| URL XML gateway | `carriers/ups/gateway_xml_url` |  | | | Sensibile |
| Numero corriere | `carriers/ups/shipper_number` |  | | | Sensibile |
| Debug | `carriers/ups/debug` |  | | | Sensibile |
| ID account | `carriers/fedex/account` |  | Crittografato | | Sensibile |
| Chiave | `carriers/fedex/key` |  | Crittografato | | Sensibile |
| Numero misuratore | `carriers/fedex/meter_number` |  | Crittografato | | Sensibile |
| Password | `carriers/fedex/password` |  | Crittografato | | Sensibile |
| ID accesso | `carriers/dhl/id` |  | Crittografato | | Sensibile |
| Password | `carriers/dhl/password` |  | Crittografato | | Sensibile |
| Debug | `carriers/dhl/debug` |  | | | |
| Numero account | `carriers/dhl/account` |  | | | Sensibile |
| URL gateway | `carriers/dhl/gateway_url` |  | | | Sensibile |
| Modalità sandbox | `carriers/fedex/sandbox_mode` |  | | | Sensibile |

{style="table-layout:auto"}

### Percorsi sensibili alle vendite e specifici del sistema

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Vendite** > **Vendite**.

| Nome | Percorso configurazione | Supporto delle versioni di Commerce | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Nome contatto | `sales/magento_rma/store_name` | Solo Commerce Enterprise | | | Sensibile |
| Indirizzo | `sales/magento_rma/address` | Solo Commerce Enterprise | | | Sensibile |
| Indirizzo | `sales/magento_rma/address1` |  | | | Sensibile |
| Città | `sales/magento_rma/city` | Solo Commerce Enterprise | | | Sensibile |
| Stato/Provincia | `sales/magento_rma/region_id` | Solo Commerce Enterprise | | | Sensibile |
| CAP | `sales/magento_rma/zip` | Solo Commerce Enterprise | | | Sensibile |
| Paese | `sales/magento_rma/country_id` | Solo Commerce Enterprise | | | Sensibile |
| Invia copia e-mail RMA a | `sales_email/magento_rma/copy_to` | Solo Commerce Enterprise | | | Sensibile |
| Invia copia e-mail autorizzazione RMA a | `sales_email/magento_rma_auth/copy_to` | Solo Commerce Enterprise | | | Sensibile |
| Invia copia e-mail per commento RMA a | `sales_email/magento_rma_comment/copy_to` | Solo Commerce Enterprise | | | Sensibile |
| Invia copia e-mail per commento RMA a | `sales_email/magento_rma_customer_comment/copy_to` | Solo Commerce Enterprise | | | Sensibile |

{style="table-layout:auto"}

### Percorsi API Google

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Vendite** > **API Google**.

| Nome | Percorso configurazione | Supporto delle versioni di Commerce | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Numero account | `google/analytics/account` |  | | | Sensibile |

{style="table-layout:auto"}

## Categoria avanzata

In questa sezione sono elencati i nomi delle variabili e i percorsi di configurazione disponibili per le opzioni dell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Avanzate**.

### Percorsi sensibili all’amministratore e specifici per il sistema

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Avanzate** > **Amministratore**.

| Nome | Percorso configurazione | Supporto delle versioni di Commerce | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| URL amministratore personalizzato | `admin/url/custom` |  | | | Sensibile |
| Percorso amministratore personalizzato | `admin/url/custom_path` |  | | | Sensibile |

{style="table-layout:auto"}

### Percorsi sensibili al sistema e specifici del sistema

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Avanzate** > **Sistema**.

| Nome | Percorso configurazione | Supporto delle versioni di Commerce | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Destinatario e-mail per errore | `system/magento_scheduled_import_export_log/error_email` |  | | | Sensibile |
| Elenco di accesso | `system/full_page_cache/varnish/access_list` |  |  | | Sensibile |
| Errore mittente e-mail | `system/magento_scheduled_import_export_log/error_email_identity` |  |  | | Sensibile |

{style="table-layout:auto"}

### Percorsi sensibili per sviluppatori e specifici per il sistema

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Avanzate** > **Sviluppatore**.

| Nome | Percorso configurazione | Supporto delle versioni di Commerce | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| IP consentiti (separati da virgola) | `dev/restrict/allow_ips` |  | | Specifico del sistema | Sensibile |

{style="table-layout:auto"}

## Categoria avanzata

In questa sezione sono elencati i nomi delle variabili e i percorsi di configurazione disponibili per le opzioni dell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Avanzate**.

### Percorsi di sistema

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Avanzate** > **Sistema**.

| Nome | Percorso configurazione | Supporto delle versioni di Commerce | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Host | `system/smtp/host` |  | | Specifico del sistema | Sensibile |
| Porta (25) | `system/smtp/port` |  | | Specifico del sistema | Sensibile |
| Host back-end | `system/full_page_cache/varnish/backend_host` |  | | Specifico del sistema | Sensibile |
| Porta back-end | `system/full_page_cache/varnish/backend_port` |  | | Specifico del sistema | Sensibile |

{style="table-layout:auto"}

### Percorsi per sviluppatori

Questi valori di configurazione sono disponibili nell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Avanzate** > **Sviluppatore**.

| Nome | Percorso configurazione | Supporto delle versioni di Commerce | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Registra errori JS nella chiave di archiviazione della sessione | `dev/js/session_storage_key` | ![Non solo Commerce](/help/assets/configuration/red-x.png) | | Specifico del sistema | |

{style="table-layout:auto"}

## Percorsi sensibili ai pagamenti e specifici del sistema

In questa sezione sono elencati i nomi delle variabili e i percorsi di configurazione disponibili per le opzioni dell&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Vendite** > **Pagamento**.

### Variabile generale

| Nome | Percorso configurazione | Supporto delle versioni di Commerce | Crittografato? |
|--------------|--------------|--------------|--------------|
| Paese esercente | `paypal/general/merchant_country` |  | Sensibile |

{style="table-layout:auto"}

>[!INFO]
>
>La scelta di questa variabile determina quali [percorsi internazionali](#international-paths) puoi utilizzare.

### Percorsi sensibili a PayPal e specifici per il sistema

| Nome | Percorso configurazione | Supporto delle versioni di Commerce | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| E-mail associata al conto PayPal dell&#39;esercente (facoltativo) | `paypal/general/business_account` |  | | | Sensibile |
| ID account esercente | `payment/paypal_express/merchant_id` |  | | | Sensibile |
| ID editore | `payment/paypal_express_bml/publisher_id` |  | | | Sensibile |
| Password | `paypal/fetch_reports/ftp_password` |  | Crittografato | | Sensibile |
| Login | `paypal/fetch_reports/ftp_login` |  | Crittografato | | Sensibile |
| Nome host o indirizzo IP dell’endpoint personalizzato | `paypal/fetch_reports/ftp_ip` |  | | Specifico del sistema | Sensibile |
| Modalità sandbox | `paypal/fetch_reports/ftp_sandbox` |  | | Specifico del sistema | |
| Modalità di debug | `payment/paypal_express/debug` |  | | Specifico del sistema | |
| Modalità di debug | `payment/paypal_billing_agreement/debug` |  | | Specifico del sistema | |
| Credenziali SFTP | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibile |

{style="table-layout:auto"}

### PayPal Payflow Pro percorsi sensibili e specifici del sistema

| Nome | Percorso configurazione | Supporto delle versioni di Commerce | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Utente | `payment/payflow_advanced/user` |  | Crittografato | | Sensibile |
| Password | `payment/payflow_advanced/pwd` |  | Crittografato | | Sensibile |
| Percorso personalizzato | `paypal/fetch_reports/ftp_path` |  | | Specifico del sistema | Sensibile |
| Utente | `payment/payflowpro/user` |  | Crittografato | | Sensibile |
| Password | `payment/payflowpro/pwd` |  | Crittografato | Specifico del sistema | Sensibile |
| Modalità di prova | `payment/payflowpro/sandbox_flag` |  | | Specifico del sistema | |
| Partner | `payment/payflowpro/partner` |  | | | Sensibile |
| Host proxy | `payment/payflowpro/proxy_host` |  | | Specifico del sistema | Sensibile |
| Porta proxy | `payment/payflowpro/proxy_port` |  | | Specifico del sistema | Sensibile |
| Modalità di debug | `payment/payflowpro/debug` |  | | Specifico del sistema | |
| Credenziali SFTP | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | Specifico del sistema | |
| Impostazioni carta di credito | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/heading_cc` |  | | | Sensibile |

{style="table-layout:auto"}

### PayPal Payflow Link percorsi sensibili e specifici del sistema

| Nome | Percorso configurazione | Supporto delle versioni di Commerce | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Utente | `payment/payflow_link/user` |  | Crittografato | | Sensibile |
| Password | `payment/payflow_link/pwd` |  | Crittografato | | Sensibile |
| Modalità di prova | `payment/payflow_link/sandbox_flag` |  | | Specifico del sistema | |
| Usa proxy | `payment/payflow_link/use_proxy` |  | | Specifico del sistema | |
| Host proxy | `payment/payflow_link/proxy_host` |  | | Specifico del sistema | |
| Porta proxy | `payment/payflow_link/proxy_port` |  |  | Specifico del sistema | |
| Modalità di debug | `payment/payflow_link/debug` |  | | Specifico del sistema | |
| Metodo URL per URL di annullamento e URL restituito | `payment/payflow_link/url_method` |  | | Specifico del sistema | |
| Modalità di debug | `payment/payflow_express/debug` |  | | Specifico del sistema | |
| Credenziali SFTP | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` |  | | | Sensibile |

{style="table-layout:auto"}

### PayPal Payments Pro percorsi sensibili e specifici del sistema

| Nome | Percorso configurazione | Supporto delle versioni di Commerce | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Nome utente API | `paypal/wpp/api_username` |  | Crittografato | | Sensibile |
| Password API | `paypal/wpp/api_password` |  | Crittografato | | Sensibile |
| Firma API | `paypal/wpp/api_signature` |  | Crittografato | | Sensibile |
| Certificato API | `paypal/wpp/api_cert` |  | | | Sensibile |
| Host proxy | `paypal/wpp/proxy_host` |  | | Specifico del sistema | Sensibile |
| Porta proxy | `paypal/wpp/proxy_port` |  | | Specifico del sistema | Sensibile |
| Modalità sandbox | `paypal/wpp/sandbox_flag` |  | | Specifico del sistema | |
| Credenziali SFTP | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensibile |

{style="table-layout:auto"}

### PayPal Payments Pro Percorsi sensibili e specifici del sistema ospitati

| Nome | Percorso configurazione | Supporto delle versioni di Commerce | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Modalità di debug | `payment/hosted_pro/debug` |  | | Specifico del sistema | |
| Credenziali SFTP | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensibile |
| Credenziali SFTP | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensibile |

{style="table-layout:auto"}

### Percorsi sensibili a Braintree e specifici del sistema

| Nome | Percorso configurazione | Supporto delle versioni di Commerce | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| ID esercente | `payment/braintree/merchant_id` |  | | | Sensibile |
| Chiave pubblica | `payment/braintree/public_key` |  | Crittografato | | Sensibile |
| Chiave privata | `payment/braintree/private_key` |  | Crittografato | | Sensibile |
| ID account esercente | `payment/braintree/merchant_account_id` |  | | | Sensibile |
| ID commerciante Kount | `payment/braintree/kount_id` |  | | | Sensibile |
| Ignora nome commerciante | `payment/braintree_paypal/merchant_name_override` |  | | | Sensibile |
| Telefono | `payment/braintree/descriptor_phone` |  | | | Sensibile |
| URL | `payment/braintree/descriptor_url` |  | | Specifico del sistema | |

{style="table-layout:auto"}

### Percorsi assegno/vaglia postale

| Nome | Percorso configurazione | Supporto delle versioni di Commerce | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Invia assegno a | `payment/checkmo/mailing_address` |  | | | Sensibile |
| Invia assegno a | `payment_us/checkmo/mailing_address` |  | | | Sensibile |

{style="table-layout:auto"}

### Percorsi internazionali

| Nome | Percorso configurazione | Supporto delle versioni di Commerce | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Chiave transazione | `payment_au/authorizenet_directpost/trans_key` |  | Crittografato | Specifico del sistema | Sensibile |
| Modalità di prova | `payment_au/authorizenet_directpost/test` |  | | Specifico del sistema | |
| URL gateway | `payment_au/authorizenet_directpost/cgi_url` |  | | Specifico del sistema | Sensibile |
| URL dettagli transazione | `payment_au/authorizenet_directpost/cgi_url_td` |  | | Specifico del sistema | Sensibile |
| Chiave transazione | `payment_au/cybersource/transaction_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave di accesso | `payment_au/cybersource/access_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave segreta | `payment_au/cybersource/secret_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Modalità di prova | `payment_au/cybersource/sandbox_flag` | Solo Commerce Enterprise | | Specifico del sistema | |
| Password risposta pagamento | `payment_au/worldpay/response_password` | Solo Commerce Enterprise | | Specifico del sistema | Sensibile |
| Password di autorizzazione amministratore remoto | `payment_au/worldpay/auth_password` | Solo Commerce Enterprise | | Specifico del sistema | Sensibile |
| Modalità sandbox | `payment_au/eway/sandbox_flag` | Solo Commerce Enterprise | | Specifico del sistema | |
| Chiave API live | `payment_au/eway/live_api_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Password API live | `payment_au/eway/live_api_password` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave di crittografia lato client live | `payment_au/eway/live_encryption_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave API sandbox | `payment_au/eway/sandbox_api_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Password API sandbox | `payment_au/eway/sandbox_api_password` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave di crittografia lato client sandbox | `payment_au/eway/sandbox_encryption_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave transazione | `payment_es/authorizenet_directpost/trans_key` |  | Crittografato | Specifico del sistema | Sensibile |
| Modalità di prova | `payment_es/authorizenet_directpost/test` |  | | Specifico del sistema | |
| URL gateway | `payment_es/authorizenet_directpost/cgi_url` |  | | Specifico del sistema | Sensibile |
| URL dettagli transazione | `payment_es/authorizenet_directpost/cgi_url_td` |  | | Specifico del sistema | Sensibile |
| Chiave transazione | `payment_es/cybersource/transaction_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave di accesso | `payment_es/cybersource/access_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave segreta | `payment_es/cybersource/secret_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Modalità di prova | `payment_es/cybersource/sandbox_flag` | Solo Commerce Enterprise | | Specifico del sistema | |
| Password risposta pagamento | `payment_es/worldpay/response_password` | Solo Commerce Enterprise | | Specifico del sistema | Sensibile |
| Password di autorizzazione amministratore remoto | `payment_es/worldpay/auth_password` | Solo Commerce Enterprise | | Specifico del sistema | Sensibile |
| Segreto MD5 per le transazioni | `payment_es/worldpay/md5_secret` | Solo Commerce Enterprise | | Specifico del sistema | Sensibile |
| Debug | `payment_es/worldpay/debug` | Solo Commerce Enterprise | | Specifico del sistema | |
| Modalità sandbox | `payment_es/eway/sandbox_flag` | Solo Commerce Enterprise | | Specifico del sistema | |
| Chiave API live | `payment_es/eway/live_api_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Password API live | `payment_es/eway/live_api_password` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave di crittografia lato client live | `payment_es/eway/live_encryption_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave API sandbox | `payment_es/eway/sandbox_api_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Password API sandbox | `payment_es/eway/sandbox_api_password` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave di crittografia lato client sandbox | `payment_es/eway/sandbox_encryption_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave transazione | `payment_nz/authorizenet_directpost/trans_key` |  | Crittografato | Specifico del sistema | Sensibile |
| Modalità di prova | `payment_nz/authorizenet_directpost/test` |  | | Specifico del sistema | |
| URL gateway | `payment_nz/authorizenet_directpost/cgi_url` |  | | Specifico del sistema | Sensibile |
| URL dettagli transazione | `payment_nz/authorizenet_directpost/cgi_url_td` |  | | Specifico del sistema | Sensibile |
| Modalità di prova | `payment_nz/cybersource/sandbox_flag` | Solo Commerce Enterprise | | Specifico del sistema | |
| Modalità di prova | `payment_nz/worldpay/sandbox_flag` | Solo Commerce Enterprise | | Specifico del sistema | |
| Modalità sandbox | `payment_nz/eway/sandbox_flag` | Solo Commerce Enterprise | | Specifico del sistema | |
| Chiave API live | `payment_nz/eway/live_api_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Password API live | `payment_nz/eway/live_api_password` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave di crittografia lato client live | `payment_nz/eway/live_encryption_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave API sandbox | `payment_nz/eway/sandbox_api_key` | Solo Commerce Enterprise | Crittografato | | Sensibile |
| Password API sandbox | `payment_nz/eway/sandbox_api_password` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave di crittografia lato client sandbox | `payment_nz/eway/sandbox_encryption_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Modalità di prova | `payment/payflow_advanced/sandbox_flag` |  | | Specifico del sistema | |
| Host proxy | `payment/payflow_advanced/proxy_host` |  | | Specifico del sistema | Sensibile |
| Porta proxy | `payment/payflow_advanced/proxy_port` |  | | Specifico del sistema | |
| Modalità di debug | `payment/payflow_advanced/debug` |  | | Specifico del sistema | |
| Metodo URL per URL di annullamento e URL restituito | `payment/payflow_advanced/url_method` |  | | Specifico del sistema | |
| Modalità di prova | `payment_us/authorizenet_directpost/test` |  | | Specifico del sistema | |
| URL gateway | `payment_us/authorizenet_directpost/cgi_url` |  | | Specifico del sistema | Sensibile |
| URL dettagli transazione | `payment_us/authorizenet_directpost/cgi_url_td` |  | | Specifico del sistema | Sensibile |
| Chiave di accesso | `payment_us/cybersource/access_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave segreta | `payment_us/cybersource/secret_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Modalità di prova | `payment_us/cybersource/sandbox_flag` | Solo Commerce Enterprise | | Specifico del sistema | |
| Modalità di prova | `payment_us/worldpay/sandbox_flag` | Solo Commerce Enterprise | | Specifico del sistema | |
| Modalità sandbox | `payment_us/eway/sandbox_flag` | Solo Commerce Enterprise | | Specifico del sistema | |
| Chiave API live | `payment_us/eway/live_api_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Password API live | `payment_us/eway/live_api_password` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave di crittografia lato client live | `payment_us/eway/live_encryption_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave API sandbox | `payment_us/eway/sandbox_api_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Password API sandbox | `payment_us/eway/sandbox_api_password` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave di crittografia lato client sandbox | `payment_us/eway/sandbox_encryption_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | |
| Modalità di prova | `payment_gb/cybersource/sandbox_flag` | Solo Commerce Enterprise | | Specifico del sistema | |
| Modalità di prova | `payment_gb/authorizenet_directpost/test` |  | | Specifico del sistema | |
| URL gateway | `payment_gb/authorizenet_directpost/cgi_url` |  | | Specifico del sistema | Sensibile |
| URL dettagli transazione | `payment_gb/authorizenet_directpost/cgi_url_td` |  | | Specifico del sistema | Sensibile |
| Modalità di prova | `payment_gb/worldpay/sandbox_flag` | Solo Commerce Enterprise | | Specifico del sistema | |
| Modalità sandbox | `payment_gb/eway/sandbox_flag` | Solo Commerce Enterprise | | Specifico del sistema | |
| Chiave API live | `payment_gb/eway/live_api_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Password API live | `payment_gb/eway/live_api_password` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave di crittografia lato client live | `payment_gb/eway/live_encryption_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave API sandbox | `payment_gb/eway/sandbox_api_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Password API sandbox | `payment_gb/eway/sandbox_api_password` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave di crittografia lato client sandbox | `payment_gb/eway/sandbox_encryption_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave transazione | `payment_de/cybersource/transaction_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave di accesso | `payment_de/cybersource/access_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave segreta | `payment_de/cybersource/secret_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Modalità di prova | `payment_de/cybersource/sandbox_flag` | Solo Commerce Enterprise | | Specifico del sistema | |
| Chiave transazione | `payment_de/authorizenet_directpost/trans_key` |  | Crittografato | Specifico del sistema | Sensibile |
| Modalità di prova | `payment_de/authorizenet_directpost/test` |  | | Specifico del sistema | |
| URL gateway | `payment_de/authorizenet_directpost/cgi_url` |  | | Specifico del sistema | Sensibile |
| URL dettagli transazione | `payment_de/authorizenet_directpost/cgi_url_td` |  | | Specifico del sistema | Sensibile |
| Password risposta pagamento | `payment_de/worldpay/response_password` | Solo Commerce Enterprise | | Specifico del sistema | Sensibile |
| Password di autorizzazione amministratore remoto | `payment_de/worldpay/auth_password` | Solo Commerce Enterprise | | Specifico del sistema | Sensibile |
| Debug | `payment_de/worldpay/debug` | Solo Commerce Enterprise | | Specifico del sistema | |
| Modalità sandbox | `payment_de/eway/sandbox_flag` | Solo Commerce Enterprise | | Specifico del sistema | |
| Chiave API live | `payment_de/eway/live_api_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Password API live | `payment_de/eway/live_api_password` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave di crittografia lato client live | `payment_de/eway/live_encryption_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave API sandbox | `payment_de/eway/sandbox_api_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Password API sandbox | `payment_de/eway/sandbox_api_password` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave di crittografia lato client sandbox | `payment_de/eway/sandbox_encryption_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave transazione | `payment_other/authorizenet_directpost/trans_key` |  | Crittografato | Specifico del sistema | Sensibile |
| Modalità di prova | `payment_other/authorizenet_directpost/test` |  | | Specifico del sistema | Sensibile |
| URL gateway | `payment_other/authorizenet_directpost/cgi_url` |  | | Specifico del sistema | Sensibile |
| URL dettagli transazione | `payment_other/authorizenet_directpost/cgi_url_td` |  | | Specifico del sistema | |
| Chiave transazione | `payment_other/cybersource/transaction_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave di accesso | `payment_other/cybersource/access_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave segreta | `payment_other/cybersource/secret_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Stato nuovo ordine | `payment_other/cybersource/order_status` | Solo Commerce Enterprise | | Specifico del sistema | |
| Modalità di prova | `payment_other/cybersource/sandbox_flag` | Solo Commerce Enterprise | | Specifico del sistema | |
| Password risposta pagamento | `payment_other/worldpay/response_password` | Solo Commerce Enterprise | | Specifico del sistema | Sensibile |
| Password di autorizzazione amministratore remoto | `payment_other/worldpay/auth_password` | Solo Commerce Enterprise | | Specifico del sistema | Sensibile |
| Modalità di prova | `payment_other/worldpay/sandbox_flag` | Solo Commerce Enterprise | | Specifico del sistema | |
| Modalità sandbox | `payment_other/eway/sandbox_flag` | Solo Commerce Enterprise | | Specifico del sistema | |
| Chiave API live | `payment_other/eway/live_api_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Password API live | `payment_other/eway/live_api_password` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave di crittografia lato client live | `payment_other/eway/live_encryption_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave API sandbox | `payment_other/eway/sandbox_api_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Password API sandbox | `payment_other/eway/sandbox_api_password` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave di crittografia lato client sandbox | `payment_other/eway/sandbox_encryption_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave transazione | `payment_ca/authorizenet_directpost/trans_key` |  | Crittografato | Specifico del sistema | Sensibile |
| Modalità di prova | `payment_ca/authorizenet_directpost/test` |  | | Specifico del sistema | |
| URL gateway | `payment_ca/authorizenet_directpost/cgi_url` |  | | Specifico del sistema | Sensibile |
| URL dettagli transazione | `payment_ca/authorizenet_directpost/cgi_url_td` |  | | Specifico del sistema | Sensibile |
| Chiave transazione | `payment_ca/cybersource/transaction_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave di accesso | `payment_ca/cybersource/access_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave segreta | `payment_ca/cybersource/secret_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Stato nuovo ordine | `payment_ca/cybersource/order_status` | Solo Commerce Enterprise | | | |
| Modalità di prova | `payment_ca/cybersource/sandbox_flag` | Solo Commerce Enterprise | | Specifico del sistema | |
| Password risposta pagamento | `payment_ca/worldpay/response_password` | Solo Commerce Enterprise | | Specifico del sistema | |
| Password di autorizzazione amministratore remoto | `payment_ca/worldpay/auth_password` | Solo Commerce Enterprise | | Specifico del sistema | Sensibile |
| Modalità di prova | `payment_ca/worldpay/sandbox_flag` | Solo Commerce Enterprise | | Specifico del sistema | |
| Modalità sandbox | `payment_ca/eway/sandbox_flag` | Solo Commerce Enterprise | | Specifico del sistema | |
| Chiave API live | `payment_ca/eway/live_api_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Password API live | `payment_ca/eway/live_api_password` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave di crittografia lato client live | `payment_ca/eway/live_encryption_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave API sandbox | `payment_ca/eway/sandbox_api_key` | Solo Commerce Enterprise | Crittografato | | Sensibile |
| Password API sandbox | `payment_ca/eway/sandbox_api_password` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave di crittografia lato client sandbox | `payment_ca/eway/sandbox_encryption_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave transazione | `payment_hk/authorizenet_directpost/trans_key` |  | Crittografato | Specifico del sistema | Sensibile |
| Modalità di prova | `payment_hk/authorizenet_directpost/test` |  | | Specifico del sistema | |
| URL gateway | `payment_hk/authorizenet_directpost/cgi_url` |  | | | Sensibile |
| URL dettagli transazione | `payment_hk/authorizenet_directpost/cgi_url_td` |  | | Specifico del sistema | Sensibile |
| Chiave transazione | `payment_hk/cybersource/transaction_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave di accesso | `payment_hk/cybersource/access_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave segreta | `payment_hk/cybersource/secret_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Modalità di prova | `payment_hk/cybersource/sandbox_flag` | Solo Commerce Enterprise | | Specifico del sistema | Sensibile |
| Password risposta pagamento | `payment_hk/worldpay/response_password` | Solo Commerce Enterprise | | Specifico del sistema | Sensibile |
| Password di autorizzazione amministratore remoto | `payment_hk/worldpay/auth_password` | Solo Commerce Enterprise | | Specifico del sistema | Sensibile |
| Modalità di prova | `payment_hk/worldpay/sandbox_flag` | Solo Commerce Enterprise | | Specifico del sistema | Sensibile |
| Chiave API live | `payment_hk/eway/live_api_key` | Solo Commerce Enterprise | Crittografato | | Sensibile |
| Password API live | `payment_hk/eway/live_api_password` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave di crittografia lato client live | `payment_hk/eway/live_encryption_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave API sandbox | `payment_hk/eway/sandbox_api_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Password API sandbox | `payment_hk/eway/sandbox_api_password` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave di crittografia lato client sandbox | `payment_hk/eway/sandbox_encryption_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave transazione | `payment_jp/authorizenet_directpost/trans_key` |  | Crittografato | Specifico del sistema | Sensibile |
| Modalità di prova | `payment_jp/authorizenet_directpost/test` |  | | Specifico del sistema | |
| URL gateway | `payment_jp/authorizenet_directpost/cgi_url` |  | | Specifico del sistema | Sensibile |
| URL dettagli transazione | `payment_jp/authorizenet_directpost/cgi_url_td` |  | | Specifico del sistema | Sensibile |
| Chiave transazione | `payment_jp/cybersource/transaction_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave di accesso | `payment_jp/cybersource/access_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave segreta | `payment_jp/cybersource/secret_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Stato nuovo ordine | `payment_jp/cybersource/order_status` | Solo Commerce Enterprise | | Specifico del sistema | |
| Modalità di prova | `payment_jp/cybersource/sandbox_flag` | Solo Commerce Enterprise | | Specifico del sistema | |
| Password risposta pagamento | `payment_jp/worldpay/response_password` | Solo Commerce Enterprise | | Specifico del sistema | Sensibile |
| Password di autorizzazione amministratore remoto | `payment_jp/worldpay/auth_password` | Solo Commerce Enterprise | | Specifico del sistema | Sensibile |
| Modalità di prova | `payment_jp/worldpay/sandbox_flag` | Solo Commerce Enterprise | | Specifico del sistema | |
| Modalità sandbox | `payment_jp/eway/sandbox_flag` | Solo Commerce Enterprise | | Specifico del sistema | |
| Chiave API live | `payment_jp/eway/live_api_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Password API live | `payment_jp/eway/live_api_password` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave di crittografia lato client live | `payment_jp/eway/live_encryption_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave API sandbox | `payment_jp/eway/sandbox_api_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Password API sandbox | `payment_jp/eway/sandbox_api_password` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave di crittografia lato client sandbox | `payment_jp/eway/sandbox_encryption_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave transazione | `payment_fr/authorizenet_directpost/trans_key` |  | Crittografato | Specifico del sistema | Sensibile |
| Modalità di prova | `payment_fr/authorizenet_directpost/test` |  | | Specifico del sistema | |
| URL gateway | `payment_fr/authorizenet_directpost/cgi_url` |  | | Specifico del sistema | Sensibile |
| URL dettagli transazione | `payment_fr/authorizenet_directpost/cgi_url_td` |  | | Specifico del sistema | Sensibile |
| Chiave transazione | `payment_fr/cybersource/transaction_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave di accesso | `payment_fr/cybersource/access_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave segreta | `payment_fr/cybersource/secret_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Modalità di prova | `payment_fr/cybersource/sandbox_flag` | Solo Commerce Enterprise | | Specifico del sistema | |
| Password risposta pagamento | `payment_fr/worldpay/response_password` | Solo Commerce Enterprise | | Specifico del sistema | Sensibile |
| Password di autorizzazione amministratore remoto | `payment_fr/worldpay/auth_password` | Solo Commerce Enterprise | | Specifico del sistema | Sensibile |
| Modalità di prova | `payment_fr/worldpay/sandbox_flag` | Solo Commerce Enterprise |  | Specifico del sistema | |
| Modalità sandbox | `payment_fr/eway/sandbox_flag` | Solo Commerce Enterprise | | Specifico del sistema | |
| Chiave API live | `payment_fr/eway/live_api_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Password API live | `payment_fr/eway/live_api_password` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave di crittografia lato client live | `payment_fr/eway/live_encryption_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave API sandbox | `payment_fr/eway/sandbox_api_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Password API sandbox | `payment_fr/eway/sandbox_api_password` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave di crittografia lato client sandbox | `payment_fr/eway/sandbox_encryption_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave transazione | `payment_it/authorizenet_directpost/trans_key` |  | Crittografato | Specifico del sistema | Sensibile |
| Modalità di prova | `payment_it/authorizenet_directpost/test` |  | | Specifico del sistema | |
| URL gateway | `payment_it/authorizenet_directpost/cgi_url` |  | | Specifico del sistema | Sensibile |
| URL dettagli transazione | `payment_it/authorizenet_directpost/cgi_url_td` |  | | Specifico del sistema | Sensibile |
| Chiave transazione | `payment_it/cybersource/transaction_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave di accesso | `payment_it/cybersource/access_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave segreta | `payment_it/cybersource/secret_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Modalità di prova | `payment_it/cybersource/sandbox_flag` | Solo Commerce Enterprise | | Specifico del sistema | |
| Password risposta pagamento | `payment_it/worldpay/response_password` | Solo Commerce Enterprise | | Specifico del sistema | Sensibile |
| Password di autorizzazione amministratore remoto | `payment_it/worldpay/auth_password` | Solo Commerce Enterprise | | Specifico del sistema | Sensibile |
| Modalità di prova | `payment_it/worldpay/sandbox_flag` | Solo Commerce Enterprise | | Specifico del sistema | |
| Modalità sandbox | `payment_it/eway/sandbox_flag` | Solo Commerce Enterprise | | Specifico del sistema | |
| Chiave API live | `payment_it/eway/live_api_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Password API live | `payment_it/eway/live_api_password` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave di crittografia lato client live | `payment_it/eway/live_encryption_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave API sandbox | `payment_it/eway/sandbox_api_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Password API sandbox | `payment_it/eway/sandbox_api_password` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave di crittografia lato client sandbox | `payment_it/eway/sandbox_encryption_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| Chiave API | `fraud_protection/signifyd/api_key` | Solo Commerce Enterprise | Crittografato | Specifico del sistema | Sensibile |
| URL API | `fraud_protection/signifyd/api_url` | Solo Commerce Enterprise |  | Specifico del sistema | Sensibile |
| Credenziali SFTP | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibile |
| Credenziali SFTP | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibile |
| Credenziali SFTP | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | Sensibile |
| ID accesso API | `payment_au/authorizenet_directpost/login` |  | Crittografato | | Sensibile |
| Commerciante MD5 | `payment_au/authorizenet_directpost/trans_md5` |  | Crittografato | | Sensibile |
| Invia e-mail al cliente | `payment_au/authorizenet_directpost/email_customer` |  | | | Sensibile |
| E-mail commerciante | `payment_au/authorizenet_directpost/merchant_email` |  | | | Sensibile |
| ID installazione amministratore remoto | `payment_au/worldpay/admin_installation_id` | Solo Commerce Enterprise | | | Sensibile |
| Segreto MD5 per le transazioni | `payment_au/worldpay/md5_secret` | Solo Commerce Enterprise | | | Sensibile |
| Credenziali SFTP | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibile |
| Credenziali SFTP | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensibile |
| Credenziali SFTP | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibile |
| Invia assegno a | `payment_es/checkmo/mailing_address` |  | | | Sensibile |
| ID accesso API | `payment_es/authorizenet_directpost/login` |  | Crittografato | | Sensibile |
| Commerciante MD5 | `payment_es/authorizenet_directpost/trans_md5` |  | Crittografato | | Sensibile |
| Invia e-mail al cliente | `payment_es/authorizenet_directpost/email_customer` |  | | | Sensibile |
| E-mail commerciante | `payment_es/authorizenet_directpost/merchant_email` |  | | | Sensibile |
| ID esercente | `payment_es/cybersource/merchant_id` | Solo Commerce Enterprise | Crittografato | | Sensibile |
| ID profilo | `payment_es/cybersource/profile_id` | Solo Commerce Enterprise | Crittografato | | Sensibile |
| ID installazione amministratore remoto | `payment_es/worldpay/admin_installation_id` | Solo Commerce Enterprise | | | Sensibile |
| Credenziali SFTP | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibile |
| Credenziali SFTP | | | | | |
| Credenziali SFTP | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibile |
| Credenziali SFTP | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | Sensibile |
| ID accesso API | `payment_nz/authorizenet_directpost/login` |  | Crittografato | | Sensibile |
| Commerciante MD5 | `payment_nz/authorizenet_directpost/trans_md5` |  | Crittografato | | Sensibile |
| Invia e-mail al cliente | `payment_nz/authorizenet_directpost/email_customer` |  | | | Sensibile |
| E-mail commerciante | `payment_nz/authorizenet_directpost/merchant_email` |  | | | Sensibile |
| ID esercente | `payment_nz/cybersource/merchant_id` | Solo Commerce Enterprise | Crittografato | | Sensibile |
| Chiave transazione | `payment_nz/cybersource/transaction_key` | Solo Commerce Enterprise | Crittografato | | Sensibile |
| ID profilo | `payment_nz/cybersource/profile_id` | Solo Commerce Enterprise | Crittografato | | Sensibile |
| Chiave di accesso | `payment_nz/cybersource/access_key` | Solo Commerce Enterprise | Crittografato | | Sensibile |
| Chiave segreta | `payment_nz/cybersource/secret_key` | Solo Commerce Enterprise | Crittografato | | Sensibile |
| ID installazione | `payment_nz/worldpay/installation_id` | Solo Commerce Enterprise | | | Sensibile |
| Password risposta pagamento | `payment_nz/worldpay/response_password` | Solo Commerce Enterprise | | | Sensibile |
| ID installazione amministratore remoto | `payment_nz/worldpay/admin_installation_id` | Solo Commerce Enterprise | | | Sensibile |
| Password di autorizzazione amministratore remoto | `payment_nz/worldpay/auth_password` | Solo Commerce Enterprise | | | Sensibile |
| Segreto MD5 per le transazioni | `payment_nz/worldpay/md5_secret` | Solo Commerce Enterprise | | | Sensibile |
| Credenziali SFTP | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibile |
| Credenziali SFTP | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_sftp` |  | | | Sensibile |
| Credenziali SFTP | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | Sensibile |
| Credenziali SFTP | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibile |
| Credenziali SFTP | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | Sensibile |
| Credenziali SFTP | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` |  | | | Sensibile |
| ID accesso API | `payment_us/authorizenet_directpost/login` |  | Crittografato | | Sensibile |
| Chiave transazione | `payment_us/authorizenet_directpost/trans_key` |  | Crittografato | | Sensibile |
| Commerciante MD5 | `payment_us/authorizenet_directpost/trans_md5` |  | Crittografato | | Sensibile |
| Invia e-mail al cliente | `payment_us/authorizenet_directpost/email_customer` |  | | | Sensibile |
| E-mail commerciante | `payment_us/authorizenet_directpost/merchant_email` |  | | | Sensibile |
| ID esercente | `payment_us/cybersource/merchant_id` | Solo Commerce Enterprise | Crittografato | | Sensibile |
| Chiave transazione | `payment_us/cybersource/transaction_key` | Solo Commerce Enterprise | Crittografato | | Sensibile |
| ID profilo | `payment_us/cybersource/profile_id` | Solo Commerce Enterprise | Crittografato | | Sensibile |
| ID installazione | `payment_us/worldpay/installation_id` | Solo Commerce Enterprise | | | Sensibile |
| Password risposta pagamento | `payment_us/worldpay/response_password` | Solo Commerce Enterprise | | | Sensibile |
| ID installazione amministratore remoto | `payment_us/worldpay/admin_installation_id` | Solo Commerce Enterprise | | | Sensibile |
| Password di autorizzazione amministratore remoto | `payment_us/worldpay/auth_password` | Solo Commerce Enterprise | | | Sensibile |
| Segreto MD5 per le transazioni | `payment_us/worldpay/md5_secret` | Solo Commerce Enterprise | | | Sensibile |
| Credenziali SFTP | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  |  | | Sensibile |
| Credenziali SFTP | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensibile |
| Credenziali SFTP | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibile |
| Invia assegno a | `payment_gb/checkmo/mailing_address` |  | | | Sensibile |
| ID esercente | `payment_gb/cybersource/merchant_id` | Solo Commerce Enterprise | Crittografato | | Sensibile |
| Chiave transazione | `payment_gb/cybersource/transaction_key` | Solo Commerce Enterprise | Crittografato | | Sensibile |
| ID profilo | `payment_gb/cybersource/profile_id` | Solo Commerce Enterprise | Crittografato | | Sensibile |
| Chiave di accesso | `payment_gb/cybersource/access_key` | Solo Commerce Enterprise | Crittografato | | Sensibile |
| Chiave segreta | `payment_gb/cybersource/secret_key` | Solo Commerce Enterprise | Crittografato | | Sensibile |
| ID accesso API | `payment_gb/authorizenet_directpost/login` |  | Crittografato | | Sensibile |
| Chiave transazione | `payment_gb/authorizenet_directpost/trans_key` |  | Crittografato | | Sensibile |
| Commerciante MD5 | `payment_gb/authorizenet_directpost/trans_md5` |  | Crittografato | | Sensibile |
| Invia e-mail al cliente | `payment_gb/authorizenet_directpost/email_customer` |  | | | Sensibile |
| E-mail commerciante | `payment_gb/authorizenet_directpost/merchant_email` |  |  | | Sensibile |
| ID installazione | `payment_gb/worldpay/installation_id` | Solo Commerce Enterprise | | | Sensibile |
| Password risposta pagamento | `payment_gb/worldpay/response_password` | Solo Commerce Enterprise | | | Sensibile |
| ID installazione amministratore remoto | `payment_gb/worldpay/admin_installation_id` | Solo Commerce Enterprise | | | Sensibile |
| Password di autorizzazione amministratore remoto | `payment_gb/worldpay/auth_password` | Solo Commerce Enterprise | | | Sensibile |
| Credenziali SFTP | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibile |
| Imposta come assegno da pagare a | `payment_de/checkmo/payable_to` |  | | | Sensibile |
| Invia assegno a | `payment_de/checkmo/mailing_address` |  | | | Sensibile |
| ID esercente | `payment_de/cybersource/merchant_id` | Solo Commerce Enterprise | Crittografato | | Sensibile |
| ID profilo | `payment_de/cybersource/profile_id` | Solo Commerce Enterprise | Crittografato | | Sensibile |
| ID accesso API | `payment_de/authorizenet_directpost/login` |  | Crittografato | | Sensibile |
| Commerciante MD5 | `payment_de/authorizenet_directpost/trans_md5` |  | Crittografato | | Sensibile |
| Invia e-mail al cliente | `payment_de/authorizenet_directpost/email_customer` |  | | | Sensibile |
| E-mail commerciante | `payment_de/authorizenet_directpost/merchant_email` |  | | | Sensibile |
| ID installazione | `payment_de/worldpay/installation_id` | Solo Commerce Enterprise | | | |
| ID installazione amministratore remoto | `payment_de/worldpay/admin_installation_id` | Solo Commerce Enterprise | | | Sensibile |
| Segreto MD5 per le transazioni | `payment_de/worldpay/md5_secret` | Solo Commerce Enterprise | | | Sensibile |
| Credenziali SFTP | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  |  | | Sensibile |
| Credenziali SFTP | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibile |
| Imposta come assegno da pagare a | `payment_other/checkmo/payable_to` |  | | | Sensibile |
| Invia assegno a | `payment_other/checkmo/mailing_address` |  | | | Sensibile |
| ID accesso API | `payment_other/authorizenet_directpost/login` |  | Crittografato | | Sensibile |
| Commerciante MD5 | `payment_other/authorizenet_directpost/trans_md5` |  | Crittografato | | Sensibile |
| Stato nuovo ordine | `payment_other/authorizenet_directpost/order_status` |  | | | Sensibile |
| E-mail commerciante | `payment_other/authorizenet_directpost/merchant_email` |  | | | Sensibile |
| ID esercente | `payment_other/cybersource/merchant_id` | Solo Commerce Enterprise | Crittografato | | Sensibile |
| ID profilo | `payment_other/cybersource/profile_id` | Solo Commerce Enterprise | Crittografato | | Sensibile |
| ID installazione | `payment_other/worldpay/installation_id` | Solo Commerce Enterprise | | | Sensibile |
| ID installazione amministratore remoto | `payment_other/worldpay/admin_installation_id` | Solo Commerce Enterprise | | | Sensibile |
| Segreto MD5 per le transazioni | `payment_other/worldpay/md5_secret` | Solo Commerce Enterprise | | | Sensibile |
| Credenziali SFTP | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibile |
| Credenziali SFTP | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibile |
| Credenziali SFTP | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | Sensibile |
| Credenziali SFTP | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` |  | | | Sensibile |
| Credenziali SFTP | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` |  | | | Sensibile |
| Imposta come assegno da pagare a | `payment_ca/checkmo/payable_to` |  | | | Sensibile |
| Invia assegno a | `payment_ca/checkmo/mailing_address` |  | | | Sensibile |
| ID accesso API | `payment_ca/authorizenet_directpost/login` |  | Crittografato | | Sensibile |
| Commerciante MD5 | `payment_ca/authorizenet_directpost/trans_md5` |  | Crittografato | | Sensibile |
| Stato nuovo ordine | `payment_ca/authorizenet_directpost/order_status` |  | | | Sensibile |
| Invia e-mail al cliente | `payment_ca/authorizenet_directpost/email_customer` |  | | | Sensibile |
| E-mail commerciante | `payment_ca/authorizenet_directpost/merchant_email` |  | | | Sensibile |
| ID esercente | `payment_ca/cybersource/merchant_id` | Solo Commerce Enterprise | Crittografato | | Sensibile |
| ID profilo | `payment_ca/cybersource/profile_id` | Solo Commerce Enterprise | Crittografato | | Sensibile |
| ID installazione | `payment_ca/worldpay/installation_id` | Solo Commerce Enterprise | | | Sensibile |
| ID installazione amministratore remoto | `payment_ca/worldpay/admin_installation_id` | Solo Commerce Enterprise | | | Sensibile |
| Segreto MD5 per le transazioni | `payment_ca/worldpay/md5_secret` | Solo Commerce Enterprise | | | Sensibile |
| Credenziali SFTP | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibile |
| Credenziali SFTP | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  |  | | Sensibile |
| Credenziali SFTP | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibile |
| Imposta come assegno da pagare a | `payment_hk/checkmo/payable_to` |  | | | Sensibile |
| Invia assegno a | `payment_hk/checkmo/mailing_address` |  | | | Sensibile |
| ID accesso API | `payment_hk/authorizenet_directpost/login` |  | Crittografato | | Sensibile |
| Commerciante MD5 | `payment_hk/authorizenet_directpost/trans_md5` |  | Crittografato | | Sensibile |
| Invia e-mail al cliente | `payment_hk/authorizenet_directpost/email_customer` |  | | | Sensibile |
| E-mail commerciante | `payment_hk/authorizenet_directpost/merchant_email` |  | | | Sensibile |
| ID esercente | `payment_hk/cybersource/merchant_id` | Solo Commerce Enterprise | Crittografato | | Sensibile |
| ID profilo | `payment_hk/cybersource/profile_id` | Solo Commerce Enterprise | Crittografato | | Sensibile |
| ID installazione | `payment_hk/worldpay/installation_id` | Solo Commerce Enterprise | | | Sensibile |
| ID installazione amministratore remoto | `payment_hk/worldpay/admin_installation_id` | Solo Commerce Enterprise | | | Sensibile |
| Segreto MD5 per le transazioni | `payment_hk/worldpay/md5_secret` | Solo Commerce Enterprise | | | Sensibile |
| Campi firma | `payment_hk/worldpay/signature_fields` | Solo Commerce Enterprise | | | Sensibile |
| Credenziali SFTP | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibile |
| Credenziali SFTP | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensibile |
| Credenziali SFTP | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibile |
| Imposta come assegno da pagare a | `payment_jp/checkmo/payable_to` |  | | | Sensibile |
| Invia assegno a | `payment_jp/checkmo/mailing_address` |  | | | Sensibile |
| ID accesso API | `payment_jp/authorizenet_directpost/login` |  | Crittografato | | Sensibile |
| Commerciante MD5 | `payment_jp/authorizenet_directpost/trans_md5` |  | Crittografato | | Sensibile |
| Invia e-mail al cliente | `payment_jp/authorizenet_directpost/email_customer` |  | | | Sensibile |
| E-mail commerciante | `payment_jp/authorizenet_directpost/merchant_email` |  | | | Sensibile |
| ID esercente | `payment_jp/cybersource/merchant_id` | Solo Commerce Enterprise | Crittografato | | Sensibile |
| ID profilo | `payment_jp/cybersource/profile_id` | Solo Commerce Enterprise | Crittografato | | Sensibile |
| ID installazione | `payment_jp/worldpay/installation_id` | Solo Commerce Enterprise | | | |
| ID installazione amministratore remoto | `payment_jp/worldpay/admin_installation_id` | Solo Commerce Enterprise | | | Sensibile |
| Segreto MD5 per le transazioni | `payment_jp/worldpay/md5_secret` | Solo Commerce Enterprise | | | Sensibile |
| Campi firma | `payment_jp/worldpay/signature_fields` | Solo Commerce Enterprise | | | Sensibile |
| Credenziali SFTP | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibile |
| Credenziali SFTP | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensibile |
| Credenziali SFTP | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibile |
| Imposta come assegno da pagare a | `payment_fr/checkmo/payable_to` |  | | | Sensibile |
| Invia assegno a | `payment_fr/checkmo/mailing_address` |  | | | Sensibile |
| ID accesso API | `payment_fr/authorizenet_directpost/login` |  | Crittografato | | Sensibile |
| Commerciante MD5 | `payment_fr/authorizenet_directpost/trans_md5` |  | Crittografato | | Sensibile |
| Invia e-mail al cliente | `payment_fr/authorizenet_directpost/email_customer` |  | | | Sensibile |
| E-mail commerciante | `payment_fr/authorizenet_directpost/merchant_email` |  | | | Sensibile |
| ID esercente | `payment_fr/cybersource/merchant_id` | Solo Commerce Enterprise | Crittografato | | Sensibile |
| ID profilo | `payment_fr/cybersource/profile_id` | Solo Commerce Enterprise | Crittografato | | Sensibile |
| ID installazione | `payment_fr/worldpay/installation_id` | Solo Commerce Enterprise | | | Sensibile |
| ID installazione amministratore remoto | `payment_fr/worldpay/admin_installation_id` | Solo Commerce Enterprise | | | Sensibile |
| Segreto MD5 per le transazioni | `payment_fr/worldpay/md5_secret` | Solo Commerce Enterprise | | | Sensibile |
| Campi firma | `payment_fr/worldpay/signature_fields` | Solo Commerce Enterprise | | | Sensibile |
| Credenziali SFTP | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibile |
| Credenziali SFTP | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` |  | | | Sensibile |
| Credenziali SFTP | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` |  | | | Sensibile |
| Imposta come assegno da pagare a | `payment_it/checkmo/payable_to` |  | | | Sensibile |
| Invia assegno a | `payment_it/checkmo/mailing_address` |  | | | Sensibile |
| ID accesso API | `payment_it/authorizenet_directpost/login` |  | Crittografato | | Sensibile |
| Commerciante MD5 | `payment_it/authorizenet_directpost/trans_md5` |  | Crittografato | | Sensibile |
| Invia e-mail al cliente | `payment_it/authorizenet_directpost/email_customer` |  | | | Sensibile |
| E-mail commerciante | `payment_it/authorizenet_directpost/merchant_email` |  | | | Sensibile |
| ID esercente | `payment_it/cybersource/merchant_id` | Solo Commerce Enterprise | Crittografato | | Sensibile |
| ID profilo | `payment_it/cybersource/profile_id` | Solo Commerce Enterprise | Crittografato | | Sensibile |
| ID installazione | `payment_it/worldpay/installation_id` | Solo Commerce Enterprise | | | Sensibile |
| ID installazione amministratore remoto | `payment_it/worldpay/admin_installation_id` | Solo Commerce Enterprise | | | Sensibile |
| Segreto MD5 per le transazioni | `payment_it/worldpay/md5_secret` | Solo Commerce Enterprise | | | Sensibile |

{style="table-layout:auto"}
