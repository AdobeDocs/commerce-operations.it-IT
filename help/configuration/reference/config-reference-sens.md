---
title: Percorsi sensibili e specifici del sistema
description: Consulta un elenco di valori di configurazione sensibili e specifici per il sistema.
source-git-commit: 4c18f00e0b92e49924676274c4ed462a175a7e4b
workflow-type: tm+mt
source-wordcount: '3702'
ht-degree: 0%

---


# Impostazioni sensibili e specifiche del sistema

In questo argomento vengono elencati i percorsi di configurazione per le impostazioni sensibili e specifiche del sistema:

- Il [`magento app:config:dump` comando](../cli/export-configuration.md) scrive le impostazioni specifiche del sistema nel file di configurazione specifico del sistema, `app/etc/env.php`, che dovrebbe _non_ essere nel controllo del codice sorgente. Scrive inoltre la configurazione condivisa per tutte le istanze Commerce in `app/etc/config.php`, questo file _dovrebbe_ essere nel controllo del codice sorgente.
- Il [`magento config:sensitive:set` comando](../cli/set-configuration-values.md) scrive le impostazioni sensibili in `app/etc/env.php`.

   Puoi anche impostare valori sensibili utilizzando le variabili di configurazione, come descritto in [Utilizzare le variabili di ambiente per ignorare le impostazioni di configurazione](../reference/override-config-settings.md#environment-variables).

Per un elenco degli altri percorsi di configurazione, vedi:

- [Tutti i percorsi di configurazione tranne i pagamenti](../reference/config-reference-general.md)
- [Percorsi di configurazione del pagamento](../reference/config-reference-payment.md).

>[!INFO]
>
>Tutti i percorsi di configurazione elencati in questo argomento sono sensibili. Il `System-specific?` mostra quali valori sono anche specifici del sistema.

## Percorsi generali sensibili alle categorie e specifici del sistema

In questa sezione sono elencati i nomi delle variabili e i percorsi di configurazione disponibili per le opzioni in Admin in **Negozi** > Impostazioni > **Configurazione** > **Generale**.

### Percorsi sensibili ai percorsi web e specifici del sistema

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Generale** > **Web**.

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| URL di base | `web/unsecure/base_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| URL collegamento base | `web/unsecure/base_link_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| URL di base per file di visualizzazione statica | `web/unsecure/base_static_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| URL di base per file multimediali utente | `web/unsecure/base_media_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| URL di base sicuro | `web/secure/base_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| URL collegamento base sicuro | `web/secure/base_link_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| URL di base sicuro per file di visualizzazione statica | `web/secure/base_static_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| URL di base sicuro per file multimediali utente | `web/secure/base_media_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| URL Web predefinito | `web/default/front` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| URL predefinito senza indirizzamento | `web/default/no_route` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Percorso cookie | `web/cookie/cookie_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Dominio cookie | `web/cookie/cookie_domain` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Durata dei cookie | `web/cookie/cookie_lifetime` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Usa solo HTTP | `web/cookie/cookie_httponly` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Modalità di restrizione cookie | `web/cookie/cookie_restriction` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

### Percorsi sensibili all’impostazione della valuta e specifici del sistema

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Generale** > **Impostazione valuta**.

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Destinatario e-mail per errore | `currency/import/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Archivia percorsi sensibili agli indirizzi e-mail e specifici del sistema

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione e-mail** > **Generale** > **Memorizza indirizzi e-mail**.

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Nome mittente | `trans_email/ident_general/name` |  |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| E-mail mittente | `trans_email/ident_general/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Nome mittente | `trans_email/ident_sales/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| E-mail mittente | `trans_email/ident_sales/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Nome mittente | `trans_email/ident_support/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| E-mail mittente | `trans_email/ident_support/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Nome mittente | `trans_email/ident_custom1/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| E-mail mittente | `trans_email/ident_custom1/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Nome mittente | `trans_email/ident_custom2/name` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| E-mail mittente | `trans_email/ident_custom2/email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Percorsi sensibili ai contatti e specifici del sistema

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Generale** > **Contatti**.

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Invia e-mail a | `contact/email/recipient_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Mittente e-mail | `contact/email/sender_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Modello e-mail | `contact/email/email_template` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Percorsi sensibili alla generazione di rapporti e specifici per il sistema di New Relic

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Generale** > **Generazione rapporti New Relic**.

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| ID account New Relic | `newrelicreporting/general/account_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID applicazione New Relic | `newrelicreporting/general/app_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave API New Relic | `newrelicreporting/general/api` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave API approfondimenti | `newrelicreporting/general/insights_insert_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| URL API NEW RELIC | `newrelicreporting/general/api_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| URL API approfondimenti | `newrelicreporting/general/insights_api_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## Percorsi sensibili alle categorie e specifici del sistema dei clienti

In questa sezione sono elencati i nomi delle variabili e i percorsi di configurazione disponibili per le opzioni in Admin (Amministrazione) in **Negozi** > Impostazioni > **Configurazione** > **Clienti**.

### Percorsi sensibili alla configurazione del cliente e specifici del sistema

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Clienti** > **Configurazione cliente**.

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Dominio e-mail predefinito | `customer/create_account/email_domain` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

## Categoria catalogo

In questa sezione sono elencati i nomi delle variabili e i percorsi di configurazione disponibili per le opzioni in Admin (Amministrazione) in **Negozi** > Impostazioni > **Configurazione** > **Catalogo**.

### Percorsi sensibili al catalogo e specifici del sistema

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Catalogo** > **Catalogo**.

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Destinatario e-mail per errore | `catalog/productalert_cron/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave API YouTube | `catalog/product_video/youtube_api_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Nome host server Solr | `catalog/search/solr_server_hostname` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Porta server Solr | `catalog/search/solr_server_port` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Nome Utente Solr Server | `catalog/search/solr_server_username` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password server Solr | `catalog/search/solr_server_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Percorso server Solr | `catalog/search/solr_server_path` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Nome host server di Elasticsearch | `catalog/search/elasticsearch_server_hostname` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Porta server Elasticsearch | `catalog/search/elasticsearch_server_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Prefisso indice Elasticsearch | `catalog/search/elasticsearch_index_prefix` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Abilita autenticazione HTTP Elasticsearch | `catalog/search/elasticsearch_enable_auth` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Nome utente HTTP Elasticsearch | `catalog/search/elasticsearch_username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Password HTTP Elasticsearch | `catalog/search/elasticsearch_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Timeout del server Elasticsearch | `catalog/search/elasticsearch_server_timeout` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Nome utente HTTP Elasticsearch | `catalog/search/elasticsearch_username` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) |
| Password HTTP Elasticsearch | `catalog/search/elasticsearch_password` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) |
| Timeout del server Elasticsearch | `catalog/search/elasticsearch_server_timeout` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) |
| Nome host OpenSearch Server | `catalog/search/opensearch_server_hostname` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Porta OpenSearch Server | `catalog/search/opensearch_server_port` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Prefisso indice OpenSearch | `catalog/search/opensearch_index_prefix` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Abilita autenticazione HTTP OpenSearch | `catalog/search/opensearch_enable_auth` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) |
| Nome utente HTTP OpenSearch | `catalog/search/opensearch_username` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) |
| Password HTTP OpenSearch | `catalog/search/opensearch_password` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) |
| Timeout di OpenSearch Server | `catalog/search/opensearch_server_timeout` | <!-- ![Not EE-only](/help/assets/configuration/red-x.png) --> |  | !![Sys-specific]({{ site.baseurl }}/common/images/cloud_env.png) |

{style="table-layout:auto"}

>[!NOTE]
>
>Le impostazioni OpenSearch sono state introdotte in Adobe Commerce 2.4.6.

### Percorsi sensibili all’inventario e specifici per il sistema

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Catalogo** > **Inventario**.

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Chiave API Google | `cataloginventory/source_selection_distance_based_google/api_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Percorsi specifici del sistema e sensibili alla mappa del sito XML

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Catalogo** > **XML Sitemap**.

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Destinatario e-mail per errore | `sitemap/generate/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## Categoria di vendita

In questa sezione sono elencati i nomi delle variabili e i percorsi di configurazione disponibili per le opzioni in Admin (Amministrazione) in **Negozi** > Impostazioni > **Configurazione** > **Vendite**.

### Impostazioni di spedizione sensibili e percorsi specifici del sistema

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Vendite** > **Impostazioni spedizione**.

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Paese | `shipping/origin/country_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Regione/Stato | `shipping/origin/region_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| CAP | `shipping/origin/postcode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Città | `shipping/origin/city` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Indirizzo | `shipping/origin/street_line1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Indirizzo 2 | `shipping/origin/street_line2` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Account live | `carriers/ups/is_account_live` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

### Percorsi sensibili alle e-mail per le vendite e specifici per il sistema

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Vendite** > **E-mail vendite**.

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Invia copia e-mail ordine a | `sales_email/order/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia la copia e-mail del commento dell&#39;ordine a | `sales_email/order_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia copia e-mail fattura a | `sales_email/invoice/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia copia e-mail commento fattura a | `sales_email/invoice_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia copia e-mail spedizione a | `sales_email/shipment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia copia e-mail commento spedizione a | `sales_email/shipment_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia Email Nota Di Credito A | `sales_email/creditmemo/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia Email Di Commento Nota Di Credito A | `sales_email/creditmemo_comment/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia copia e-mail pronta per il ritiro a | `sales_email/temando_pickup/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Percorsi sensibili al checkout e specifici per il sistema

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Vendite** > **Pagamento**.

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Invia copia e-mail pagamento non riuscito a | `checkout/payment_failed/copy_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Percorsi sensibili alle API Google e specifici del sistema

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Vendite** > **API GOOGLE**.

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| ID contenitore | `google/analytics/container_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Percorsi sensibili ai metodi di consegna e specifici del sistema

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Vendite** > **Metodi di consegna**.

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| URL gateway | `carriers/usps/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| URL gateway protetto | `carriers/usps/gateway_secure_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Titolo | `carriers/usps/title` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |
| ID utente | `carriers/usps/userid` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password | `carriers/usps/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID utente | `carriers/ups/username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password | `carriers/ups/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Numero licenza di accesso | `carriers/ups/access_license_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| URL XML di tracciamento | `carriers/ups/tracking_xml_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| URL XML gateway | `carriers/ups/gateway_xml_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Numero corriere | `carriers/ups/shipper_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Debug | `carriers/ups/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID account | `carriers/fedex/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave | `carriers/fedex/key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Numero misuratore | `carriers/fedex/meter_number` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password | `carriers/fedex/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID accesso | `carriers/dhl/id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password | `carriers/dhl/password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Debug | `carriers/dhl/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |
| Numero account | `carriers/dhl/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| URL gateway | `carriers/dhl/gateway_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Modalità sandbox | `carriers/fedex/sandbox_mode` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Percorsi sensibili alle vendite e specifici del sistema

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Vendite** > **Vendite**.

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Nome contatto | `sales/magento_rma/store_name` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Indirizzo | `sales/magento_rma/address` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Indirizzo | `sales/magento_rma/address1` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Città | `sales/magento_rma/city` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Stato/Provincia | `sales/magento_rma/region_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| CAP | `sales/magento_rma/zip` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Paese | `sales/magento_rma/country_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia copia e-mail RMA a | `sales_email/magento_rma/copy_to` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia copia e-mail autorizzazione RMA a | `sales_email/magento_rma_auth/copy_to` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia copia e-mail per commento RMA a | `sales_email/magento_rma_comment/copy_to` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia copia e-mail per commento RMA a | `sales_email/magento_rma_customer_comment/copy_to` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Percorsi API Google

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Vendite** > **API GOOGLE**.

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Numero account | `google/analytics/account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## Categoria avanzata

In questa sezione sono elencati i nomi delle variabili e i percorsi di configurazione disponibili per le opzioni in Admin (Amministrazione) in **Negozi** > Impostazioni > **Configurazione** > **Avanzate**.

### Percorsi sensibili all’amministratore e specifici per il sistema

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Avanzate** > **Amministratore**.

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| URL amministratore personalizzato | `admin/url/custom` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Percorso amministratore personalizzato | `admin/url/custom_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Percorsi sensibili al sistema e specifici del sistema

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Avanzate** > **Sistema**.

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Destinatario e-mail per errore | `system/magento_scheduled_import_export_log/error_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Elenco di accesso | `system/full_page_cache/varnish/access_list` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Errore mittente e-mail | `system/magento_scheduled_import_export_log/error_email_identity` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Percorsi sensibili per sviluppatori e specifici per il sistema

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Avanzate** > **Sviluppatore**.

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| IP consentiti (separati da virgola) | `dev/restrict/allow_ips` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

## Categoria avanzata

In questa sezione sono elencati i nomi delle variabili e i percorsi di configurazione disponibili per le opzioni in Admin (Amministrazione) in **Negozi** > Impostazioni > **Configurazione** > **Avanzate**.

### Percorsi di sistema

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Avanzate** > **Sistema**.

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Host | `system/smtp/host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Porta (25) | `system/smtp/port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Host back-end | `system/full_page_cache/varnish/backend_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Porta back-end | `system/full_page_cache/varnish/backend_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Percorsi per sviluppatori

Questi valori di configurazione sono disponibili in Amministrazione in **Negozi** > Impostazioni > **Configurazione** > **Avanzate** > **Sviluppatore**.

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Registra errori JS nella chiave di archiviazione della sessione | `dev/js/session_storage_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

## Percorsi sensibili ai pagamenti e specifici del sistema

In questa sezione sono elencati i nomi delle variabili e i percorsi di configurazione disponibili per le opzioni in Admin (Amministrazione) in **Negozi** > Impostazioni > **Configurazione** > **Vendite** > **Pagamento**.

### Variabile generale

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? |
|--------------|--------------|--------------|--------------|
| Paese esercente | `paypal/general/merchant_country` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

>[!INFO]
>
>La scelta di questa variabile determina quale [Percorsi internazionali](#international-paths) puoi utilizzare.

### Percorsi sensibili a PayPal e specifici per il sistema

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| E-mail associata al conto PayPal dell&#39;esercente (facoltativo) | `paypal/general/business_account` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID account esercente | `payment/paypal_express/merchant_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID editore | `payment/paypal_express_bml/publisher_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password | `paypal/fetch_reports/ftp_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Login | `paypal/fetch_reports/ftp_login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Nome host o indirizzo IP dell’endpoint personalizzato | `paypal/fetch_reports/ftp_ip` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Modalità sandbox | `paypal/fetch_reports/ftp_sandbox` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Modalità di debug | `payment/paypal_express/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Modalità di debug | `payment/paypal_billing_agreement/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Credenziali SFTP | `payment_all_paypal/express_checkout/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### PayPal Payflow Pro percorsi sensibili e specifici del sistema

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Utente | `payment/payflow_advanced/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password | `payment/payflow_advanced/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Percorso personalizzato | `paypal/fetch_reports/ftp_path` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Utente | `payment/payflowpro/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password | `payment/payflowpro/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Modalità di prova | `payment/payflowpro/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Partner | `payment/payflowpro/partner` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Host proxy | `payment/payflowpro/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Porta proxy | `payment/payflowpro/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Modalità di debug | `payment/payflowpro/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Credenziali SFTP | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Impostazioni carta di credito | `payment_all_paypal/paypal_payflowpro/settings_paypal_payflow/heading_cc` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### PayPal Payflow Link percorsi sensibili e specifici del sistema

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Utente | `payment/payflow_link/user` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password | `payment/payflow_link/pwd` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Modalità di prova | `payment/payflow_link/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Usa proxy | `payment/payflow_link/use_proxy` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Host proxy | `payment/payflow_link/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Porta proxy | `payment/payflow_link/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Modalità di debug | `payment/payflow_link/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Metodo URL per URL di annullamento e URL restituito | `payment/payflow_link/url_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Modalità di debug | `payment/payflow_express/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Credenziali SFTP | `payment_all_paypal/payflow_link/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### PayPal Payments Pro percorsi sensibili e specifici del sistema

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Nome utente API | `paypal/wpp/api_username` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password API | `paypal/wpp/api_password` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Firma API | `paypal/wpp/api_signature` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Certificato API | `paypal/wpp/api_cert` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Host proxy | `paypal/wpp/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Porta proxy | `paypal/wpp/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Modalità sandbox | `paypal/wpp/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Credenziali SFTP | `payment_all_paypal/payments_pro_hosted_solution_without_bml/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### PayPal Payments Pro Percorsi sensibili e specifici del sistema ospitati

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Modalità di debug | `payment/hosted_pro/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Credenziali SFTP | `payment_all_paypal/payments_pro_hosted_solution/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_au/paypal_group_all_in_one/payments_pro_hosted_solution_au/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Braintree percorsi sensibili e specifici del sistema

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| ID esercente | `payment/braintree/merchant_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave pubblica | `payment/braintree/public_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave privata | `payment/braintree/private_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID account esercente | `payment/braintree/merchant_account_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID commerciante Kount | `payment/braintree/kount_id` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Ignora nome commerciante | `payment/braintree_paypal/merchant_name_override` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Telefono | `payment/braintree/descriptor_phone` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| URL | `payment/braintree/descriptor_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |

{style="table-layout:auto"}

### Percorsi assegno/vaglia postale

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Invia assegno a | `payment/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia assegno a | `payment_us/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}

### Percorsi internazionali

| Nome | Percorso configurazione | Solo Commerce? | Crittografato? | Specifico per il sistema? | Sensibili? |
|--------------|--------------|--------------|--------------|--------------|--------------|
| Chiave transazione | `payment_au/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Modalità di prova | `payment_au/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| URL gateway | `payment_au/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| URL dettagli transazione | `payment_au/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave transazione | `payment_au/cybersource/transaction_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di accesso | `payment_au/cybersource/access_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave segreta | `payment_au/cybersource/secret_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Modalità di prova | `payment_au/cybersource/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Password risposta pagamento | `payment_au/worldpay/response_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password di autorizzazione amministratore remoto | `payment_au/worldpay/auth_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Modalità sandbox | `payment_au/eway/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Chiave API live | `payment_au/eway/live_api_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password API live | `payment_au/eway/live_api_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di crittografia lato client live | `payment_au/eway/live_encryption_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave API sandbox | `payment_au/eway/sandbox_api_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password API sandbox | `payment_au/eway/sandbox_api_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di crittografia lato client sandbox | `payment_au/eway/sandbox_encryption_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave transazione | `payment_es/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Modalità di prova | `payment_es/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| URL gateway | `payment_es/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| URL dettagli transazione | `payment_es/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave transazione | `payment_es/cybersource/transaction_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di accesso | `payment_es/cybersource/access_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave segreta | `payment_es/cybersource/secret_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Modalità di prova | `payment_es/cybersource/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Password risposta pagamento | `payment_es/worldpay/response_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password di autorizzazione amministratore remoto | `payment_es/worldpay/auth_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Segreto MD5 per le transazioni | `payment_es/worldpay/md5_secret` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Debug | `payment_es/worldpay/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Modalità sandbox | `payment_es/eway/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Chiave API live | `payment_es/eway/live_api_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password API live | `payment_es/eway/live_api_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di crittografia lato client live | `payment_es/eway/live_encryption_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave API sandbox | `payment_es/eway/sandbox_api_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password API sandbox | `payment_es/eway/sandbox_api_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di crittografia lato client sandbox | `payment_es/eway/sandbox_encryption_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave transazione | `payment_nz/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Modalità di prova | `payment_nz/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| URL gateway | `payment_nz/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| URL dettagli transazione | `payment_nz/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Modalità di prova | `payment_nz/cybersource/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Modalità di prova | `payment_nz/worldpay/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Modalità sandbox | `payment_nz/eway/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Chiave API live | `payment_nz/eway/live_api_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password API live | `payment_nz/eway/live_api_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di crittografia lato client live | `payment_nz/eway/live_encryption_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave API sandbox | `payment_nz/eway/sandbox_api_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password API sandbox | `payment_nz/eway/sandbox_api_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di crittografia lato client sandbox | `payment_nz/eway/sandbox_encryption_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Modalità di prova | `payment/payflow_advanced/sandbox_flag` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Host proxy | `payment/payflow_advanced/proxy_host` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Porta proxy | `payment/payflow_advanced/proxy_port` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Modalità di debug | `payment/payflow_advanced/debug` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Metodo URL per URL di annullamento e URL restituito | `payment/payflow_advanced/url_method` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Modalità di prova | `payment_us/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| URL gateway | `payment_us/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| URL dettagli transazione | `payment_us/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di accesso | `payment_us/cybersource/access_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave segreta | `payment_us/cybersource/secret_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Modalità di prova | `payment_us/cybersource/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Modalità di prova | `payment_us/worldpay/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Modalità sandbox | `payment_us/eway/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Chiave API live | `payment_us/eway/live_api_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password API live | `payment_us/eway/live_api_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di crittografia lato client live | `payment_us/eway/live_encryption_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave API sandbox | `payment_us/eway/sandbox_api_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password API sandbox | `payment_us/eway/sandbox_api_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di crittografia lato client sandbox | `payment_us/eway/sandbox_encryption_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Modalità di prova | `payment_gb/cybersource/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Modalità di prova | `payment_gb/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| URL gateway | `payment_gb/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| URL dettagli transazione | `payment_gb/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Modalità di prova | `payment_gb/worldpay/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Modalità sandbox | `payment_gb/eway/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Chiave API live | `payment_gb/eway/live_api_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password API live | `payment_gb/eway/live_api_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di crittografia lato client live | `payment_gb/eway/live_encryption_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave API sandbox | `payment_gb/eway/sandbox_api_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password API sandbox | `payment_gb/eway/sandbox_api_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di crittografia lato client sandbox | `payment_gb/eway/sandbox_encryption_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave transazione | `payment_de/cybersource/transaction_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di accesso | `payment_de/cybersource/access_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave segreta | `payment_de/cybersource/secret_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Modalità di prova | `payment_de/cybersource/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Chiave transazione | `payment_de/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Modalità di prova | `payment_de/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| URL gateway | `payment_de/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| URL dettagli transazione | `payment_de/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password risposta pagamento | `payment_de/worldpay/response_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password di autorizzazione amministratore remoto | `payment_de/worldpay/auth_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Debug | `payment_de/worldpay/debug` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Modalità sandbox | `payment_de/eway/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Chiave API live | `payment_de/eway/live_api_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password API live | `payment_de/eway/live_api_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di crittografia lato client live | `payment_de/eway/live_encryption_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave API sandbox | `payment_de/eway/sandbox_api_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password API sandbox | `payment_de/eway/sandbox_api_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di crittografia lato client sandbox | `payment_de/eway/sandbox_encryption_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave transazione | `payment_other/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Modalità di prova | `payment_other/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| URL gateway | `payment_other/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| URL dettagli transazione | `payment_other/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Chiave transazione | `payment_other/cybersource/transaction_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di accesso | `payment_other/cybersource/access_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave segreta | `payment_other/cybersource/secret_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Stato nuovo ordine | `payment_other/cybersource/order_status` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Modalità di prova | `payment_other/cybersource/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Password risposta pagamento | `payment_other/worldpay/response_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password di autorizzazione amministratore remoto | `payment_other/worldpay/auth_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Modalità di prova | `payment_other/worldpay/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Modalità sandbox | `payment_other/eway/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Chiave API live | `payment_other/eway/live_api_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password API live | `payment_other/eway/live_api_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di crittografia lato client live | `payment_other/eway/live_encryption_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave API sandbox | `payment_other/eway/sandbox_api_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password API sandbox | `payment_other/eway/sandbox_api_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di crittografia lato client sandbox | `payment_other/eway/sandbox_encryption_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave transazione | `payment_ca/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Modalità di prova | `payment_ca/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| URL gateway | `payment_ca/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| URL dettagli transazione | `payment_ca/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave transazione | `payment_ca/cybersource/transaction_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di accesso | `payment_ca/cybersource/access_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave segreta | `payment_ca/cybersource/secret_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Stato nuovo ordine | `payment_ca/cybersource/order_status` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| Modalità di prova | `payment_ca/cybersource/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Password risposta pagamento | `payment_ca/worldpay/response_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Password di autorizzazione amministratore remoto | `payment_ca/worldpay/auth_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Modalità di prova | `payment_ca/worldpay/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Modalità sandbox | `payment_ca/eway/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Chiave API live | `payment_ca/eway/live_api_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password API live | `payment_ca/eway/live_api_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di crittografia lato client live | `payment_ca/eway/live_encryption_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave API sandbox | `payment_ca/eway/sandbox_api_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password API sandbox | `payment_ca/eway/sandbox_api_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di crittografia lato client sandbox | `payment_ca/eway/sandbox_encryption_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave transazione | `payment_hk/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Modalità di prova | `payment_hk/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| URL gateway | `payment_hk/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| URL dettagli transazione | `payment_hk/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave transazione | `payment_hk/cybersource/transaction_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di accesso | `payment_hk/cybersource/access_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave segreta | `payment_hk/cybersource/secret_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Modalità di prova | `payment_hk/cybersource/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password risposta pagamento | `payment_hk/worldpay/response_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password di autorizzazione amministratore remoto | `payment_hk/worldpay/auth_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Modalità di prova | `payment_hk/worldpay/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave API live | `payment_hk/eway/live_api_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password API live | `payment_hk/eway/live_api_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di crittografia lato client live | `payment_hk/eway/live_encryption_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave API sandbox | `payment_hk/eway/sandbox_api_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password API sandbox | `payment_hk/eway/sandbox_api_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di crittografia lato client sandbox | `payment_hk/eway/sandbox_encryption_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave transazione | `payment_jp/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Modalità di prova | `payment_jp/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| URL gateway | `payment_jp/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| URL dettagli transazione | `payment_jp/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave transazione | `payment_jp/cybersource/transaction_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di accesso | `payment_jp/cybersource/access_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave segreta | `payment_jp/cybersource/secret_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Stato nuovo ordine | `payment_jp/cybersource/order_status` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Modalità di prova | `payment_jp/cybersource/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Password risposta pagamento | `payment_jp/worldpay/response_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password di autorizzazione amministratore remoto | `payment_jp/worldpay/auth_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Modalità di prova | `payment_jp/worldpay/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Modalità sandbox | `payment_jp/eway/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Chiave API live | `payment_jp/eway/live_api_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password API live | `payment_jp/eway/live_api_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di crittografia lato client live | `payment_jp/eway/live_encryption_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave API sandbox | `payment_jp/eway/sandbox_api_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password API sandbox | `payment_jp/eway/sandbox_api_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di crittografia lato client sandbox | `payment_jp/eway/sandbox_encryption_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave transazione | `payment_fr/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Modalità di prova | `payment_fr/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| URL gateway | `payment_fr/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| URL dettagli transazione | `payment_fr/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave transazione | `payment_fr/cybersource/transaction_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di accesso | `payment_fr/cybersource/access_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave segreta | `payment_fr/cybersource/secret_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Modalità di prova | `payment_fr/cybersource/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Password risposta pagamento | `payment_fr/worldpay/response_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password di autorizzazione amministratore remoto | `payment_fr/worldpay/auth_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Modalità di prova | `payment_fr/worldpay/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Modalità sandbox | `payment_fr/eway/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Chiave API live | `payment_fr/eway/live_api_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password API live | `payment_fr/eway/live_api_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di crittografia lato client live | `payment_fr/eway/live_encryption_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave API sandbox | `payment_fr/eway/sandbox_api_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password API sandbox | `payment_fr/eway/sandbox_api_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di crittografia lato client sandbox | `payment_fr/eway/sandbox_encryption_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave transazione | `payment_it/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Modalità di prova | `payment_it/authorizenet_directpost/test` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| URL gateway | `payment_it/authorizenet_directpost/cgi_url` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| URL dettagli transazione | `payment_it/authorizenet_directpost/cgi_url_td` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave transazione | `payment_it/cybersource/transaction_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di accesso | `payment_it/cybersource/access_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave segreta | `payment_it/cybersource/secret_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Modalità di prova | `payment_it/cybersource/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Password risposta pagamento | `payment_it/worldpay/response_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password di autorizzazione amministratore remoto | `payment_it/worldpay/auth_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Modalità di prova | `payment_it/worldpay/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Modalità sandbox | `payment_it/eway/sandbox_flag` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) |
| Chiave API live | `payment_it/eway/live_api_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password API live | `payment_it/eway/live_api_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di crittografia lato client live | `payment_it/eway/live_encryption_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave API sandbox | `payment_it/eway/sandbox_api_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password API sandbox | `payment_it/eway/sandbox_api_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di crittografia lato client sandbox | `payment_it/eway/sandbox_encryption_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave API | `fraud_protection/signifyd/api_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| URL API | `fraud_protection/signifyd/api_url` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  | ![Specifico per sistema](/help/assets/configuration/cloud-env.png) | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_au/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_au/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_au/paypal_payment_gateways/paypal_payflowpro_au/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID accesso API | `payment_au/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Commerciante MD5 | `payment_au/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia e-mail al cliente | `payment_au/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| E-mail commerciante | `payment_au/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID installazione amministratore remoto | `payment_au/worldpay/admin_installation_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Segreto MD5 per le transazioni | `payment_au/worldpay/md5_secret` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_es/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_es/paypal_group_all_in_one/payments_pro_hosted_solution_es/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_es/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia assegno a | `payment_es/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID accesso API | `payment_es/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Commerciante MD5 | `payment_es/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia e-mail al cliente | `payment_es/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| E-mail commerciante | `payment_es/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID esercente | `payment_es/cybersource/merchant_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID profilo | `payment_es/cybersource/profile_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID installazione amministratore remoto | `payment_es/worldpay/admin_installation_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_nz/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP |
| Credenziali SFTP | `payment_nz/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_nz/paypal_payment_gateways/paypal_payflowpro_nz/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID accesso API | `payment_nz/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Commerciante MD5 | `payment_nz/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia e-mail al cliente | `payment_nz/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| E-mail commerciante | `payment_nz/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID esercente | `payment_nz/cybersource/merchant_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave transazione | `payment_nz/cybersource/transaction_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID profilo | `payment_nz/cybersource/profile_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di accesso | `payment_nz/cybersource/access_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave segreta | `payment_nz/cybersource/secret_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID installazione | `payment_nz/worldpay/installation_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password risposta pagamento | `payment_nz/worldpay/response_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID installazione amministratore remoto | `payment_nz/worldpay/admin_installation_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password di autorizzazione amministratore remoto | `payment_nz/worldpay/auth_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Segreto MD5 per le transazioni | `payment_nz/worldpay/md5_secret` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_us/paypal_alternative_payment_methods/express_checkout_us/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_us/paypal_group_all_in_one/payflow_advanced/settings_payments_advanced/settings_payments_advanced_advanced/settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_us/paypal_group_all_in_one/wpp_usuk/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_us/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_us/paypal_payment_gateways/paypal_payflowpro_with_express_checkout/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_us/paypal_payment_gateways/payflow_link_us/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID accesso API | `payment_us/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave transazione | `payment_us/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Commerciante MD5 | `payment_us/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia e-mail al cliente | `payment_us/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| E-mail commerciante | `payment_us/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID esercente | `payment_us/cybersource/merchant_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave transazione | `payment_us/cybersource/transaction_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID profilo | `payment_us/cybersource/profile_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID installazione | `payment_us/worldpay/installation_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password risposta pagamento | `payment_us/worldpay/response_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID installazione amministratore remoto | `payment_us/worldpay/admin_installation_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password di autorizzazione amministratore remoto | `payment_us/worldpay/auth_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Segreto MD5 per le transazioni | `payment_us/worldpay/md5_secret` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_gb/paypal_alternative_payment_methods/express_checkout_gb/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_gb/paypal_group_all_in_one/payments_pro_hosted_solution_with_express_checkout/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_gb/paypal_group_all_in_one/wps_express/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia assegno a | `payment_gb/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID esercente | `payment_gb/cybersource/merchant_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave transazione | `payment_gb/cybersource/transaction_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID profilo | `payment_gb/cybersource/profile_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave di accesso | `payment_gb/cybersource/access_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave segreta | `payment_gb/cybersource/secret_key` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID accesso API | `payment_gb/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Chiave transazione | `payment_gb/authorizenet_directpost/trans_key` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Commerciante MD5 | `payment_gb/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia e-mail al cliente | `payment_gb/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| E-mail commerciante | `payment_gb/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID installazione | `payment_gb/worldpay/installation_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password risposta pagamento | `payment_gb/worldpay/response_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID installazione amministratore remoto | `payment_gb/worldpay/admin_installation_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Password di autorizzazione amministratore remoto | `payment_gb/worldpay/auth_password` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_de/paypal_payment_solutions/express_checkout_de/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Imposta come assegno da pagare a | `payment_de/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia assegno a | `payment_de/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID esercente | `payment_de/cybersource/merchant_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID profilo | `payment_de/cybersource/profile_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID accesso API | `payment_de/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Commerciante MD5 | `payment_de/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia e-mail al cliente | `payment_de/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| E-mail commerciante | `payment_de/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID installazione | `payment_de/worldpay/installation_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| ID installazione amministratore remoto | `payment_de/worldpay/admin_installation_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Segreto MD5 per le transazioni | `payment_de/worldpay/md5_secret` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_other/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_other/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Imposta come assegno da pagare a | `payment_other/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia assegno a | `payment_other/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID accesso API | `payment_other/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Commerciante MD5 | `payment_other/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Stato nuovo ordine | `payment_other/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| E-mail commerciante | `payment_other/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID esercente | `payment_other/cybersource/merchant_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID profilo | `payment_other/cybersource/profile_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID installazione | `payment_other/worldpay/installation_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID installazione amministratore remoto | `payment_other/worldpay/admin_installation_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Segreto MD5 per le transazioni | `payment_other/worldpay/md5_secret` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_ca/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_ca/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_ca/paypal_payment_gateways/wpp_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_ca/paypal_payment_gateways/paypal_payflowpro_ca/settings_paypal_payflow/settings_paypal_payflow_advanced/paypal_payflow_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_ca/paypal_payment_gateways/payflow_link_ca/settings_payflow_link/settings_payflow_link_advanced/payflow_link_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Imposta come assegno da pagare a | `payment_ca/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia assegno a | `payment_ca/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID accesso API | `payment_ca/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Commerciante MD5 | `payment_ca/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Stato nuovo ordine | `payment_ca/authorizenet_directpost/order_status` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia e-mail al cliente | `payment_ca/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| E-mail commerciante | `payment_ca/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID esercente | `payment_ca/cybersource/merchant_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID profilo | `payment_ca/cybersource/profile_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID installazione | `payment_ca/worldpay/installation_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID installazione amministratore remoto | `payment_ca/worldpay/admin_installation_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Segreto MD5 per le transazioni | `payment_ca/worldpay/md5_secret` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_hk/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_hk/paypal_group_all_in_one/payments_pro_hosted_solution_hk/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_hk/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Imposta come assegno da pagare a | `payment_hk/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia assegno a | `payment_hk/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID accesso API | `payment_hk/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Commerciante MD5 | `payment_hk/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia e-mail al cliente | `payment_hk/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| E-mail commerciante | `payment_hk/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID esercente | `payment_hk/cybersource/merchant_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID profilo | `payment_hk/cybersource/profile_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID installazione | `payment_hk/worldpay/installation_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID installazione amministratore remoto | `payment_hk/worldpay/admin_installation_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Segreto MD5 per le transazioni | `payment_hk/worldpay/md5_secret` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Campi firma | `payment_hk/worldpay/signature_fields` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_jp/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_jp/paypal_group_all_in_one/payments_pro_hosted_solution_jp/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_jp/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Imposta come assegno da pagare a | `payment_jp/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia assegno a | `payment_jp/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID accesso API | `payment_jp/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Commerciante MD5 | `payment_jp/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia e-mail al cliente | `payment_jp/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| E-mail commerciante | `payment_jp/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID esercente | `payment_jp/cybersource/merchant_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID profilo | `payment_jp/cybersource/profile_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID installazione | `payment_jp/worldpay/installation_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |
| ID installazione amministratore remoto | `payment_jp/worldpay/admin_installation_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Segreto MD5 per le transazioni | `payment_jp/worldpay/md5_secret` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Campi firma | `payment_jp/worldpay/signature_fields` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_fr/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_fr/paypal_group_all_in_one/payments_pro_hosted_solution_fr/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_fr/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Imposta come assegno da pagare a | `payment_fr/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia assegno a | `payment_fr/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID accesso API | `payment_fr/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Commerciante MD5 | `payment_fr/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia e-mail al cliente | `payment_fr/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| E-mail commerciante | `payment_fr/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID esercente | `payment_fr/cybersource/merchant_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID profilo | `payment_fr/cybersource/profile_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID installazione | `payment_fr/worldpay/installation_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID installazione amministratore remoto | `payment_fr/worldpay/admin_installation_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Segreto MD5 per le transazioni | `payment_fr/worldpay/md5_secret` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Campi firma | `payment_fr/worldpay/signature_fields` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_it/express_checkout_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_it/paypal_group_all_in_one/payments_pro_hosted_solution_it/pphs_settings/pphs_settings_advanced/pphs_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Credenziali SFTP | `payment_it/paypal_group_all_in_one/wps_other/settings_ec/settings_ec_advanced/express_checkout_settlement_report/heading_sftp` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Imposta come assegno da pagare a | `payment_it/checkmo/payable_to` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia assegno a | `payment_it/checkmo/mailing_address` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID accesso API | `payment_it/authorizenet_directpost/login` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Commerciante MD5 | `payment_it/authorizenet_directpost/trans_md5` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Invia e-mail al cliente | `payment_it/authorizenet_directpost/email_customer` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| E-mail commerciante | `payment_it/authorizenet_directpost/merchant_email` | <!-- ![Not Commerce-only](/help/assets/configuration/red-x.png) --> |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID esercente | `payment_it/cybersource/merchant_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID profilo | `payment_it/cybersource/profile_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) | ![Crittografato](/help/assets/configuration/cloud-enc.png) |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID installazione | `payment_it/worldpay/installation_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| ID installazione amministratore remoto | `payment_it/worldpay/admin_installation_id` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |
| Segreto MD5 per le transazioni | `payment_it/worldpay/md5_secret` | ![Solo Commerce](/help/assets/configuration/cloud-ee.png) |  |  | ![Sensibile](/help/assets/configuration/cloud-sens.png) |

{style="table-layout:auto"}
