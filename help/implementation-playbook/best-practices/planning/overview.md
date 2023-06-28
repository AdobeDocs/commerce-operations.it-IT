---
title: Fase di pianificazione dell’implementazione
description: Scopri le best practice di implementazione per la fase di pianificazione dei progetti Adobe Commerce.
role: Developer, Admin, User
feature: Best Practices
exl-id: 6baeac79-8dc3-45b4-bb25-8f2add8b3443
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---

# Fase di pianificazione

La fase di pianificazione comprende le seguenti attività:

- Raccolta dei requisiti
- Progettazione architettonica
- Progettazione catalogo
- Ambito progetto
- Provisioning account
- Accesso utente
- Acquisto dell’estensione

Le sezioni seguenti includono informazioni sulle best practice per la fase di pianificazione.

## Raccolta dei requisiti

- **Configurazione dell’applicazione**
   - [Best practice per la configurazione di siti, store e visualizzazioni dello store (infrastruttura cloud)](sites-stores-store-views.md)
   - [Come evitare e risolvere i cinque problemi di configurazione più comuni per i siti Adobe Commerce](https://business.adobe.com/blog/how-to/usual-suspects-five-configuration-fixes-maximize-your-peak-sales)
   - [Best practice per il caching](https://docs.magento.com/user-guide/system/cache-management.html#best-practices-for-caching)
   - [Memorizzazione in cache di pagine intere](https://developer.adobe.com/commerce/php/development/cache/page/public-content/)
   - [Dimensioni memoria OPcache](opcache-memory-size.md)
   - [Configurazione del reporting](reporting-configuration.md)

- **Configurazione del database**
   - [Best practice per la configurazione del database per le distribuzioni cloud&#x200B;](database-on-cloud.md)
   - [Configurazione connessione slave MySQL&#x200B;](configure-mysql-slave-connection-on-cloud.md)
   - [Utilizzo trigger MySQL](mysql-triggers-usage.md)

- **Configurazione servizi**
   - [Configura Fastly](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
   - [New Relic - Configurare i canali di notifica](https://devdocs.magento.com/cloud/project/new-relic.html#configure-notification-channels)
   - [Best practice per la configurazione del servizio Redis&#x200B;](redis-service-configuration.md)
   - [Best practice per la dimensione della cache del realpath](realpath-cache-size.md)

## **Progettazione architettonica**

<!--Asset not yet integrated
- [GRA Architecture examples](https://wiki.corp.adobe.com/x/kD4ykw)
-->
- [Architettura di riferimento globale](../../../implementation-playbook/architecture/global-reference.md)

## **Progettazione catalogo**

Negli argomenti seguenti vengono descritte le best practice per l’ottimizzazione delle prestazioni per la configurazione del catalogo Adobe Commerce, inclusi i valori massimi consigliati per il numero di categorie, SKU per prodotti efficaci, varianti di prodotto, attributi e opzioni di prodotto e altro ancora.

- [Configurazione categoria](category-limits.md)
- [Configurazione del prodotto&#x200B;](product-sku-limits.md)
- [Configurazione della variante di prodotto](product-variations.md)
- [Configurazione delle opzioni prodotto](product-options.md)
- [Configurazione attributi prodotto&#x200B;](product-attributes-and-options.md)
- [Configurazione dell’impaginazione per gli elenchi di prodotti](product-listing-pagination.md)

## **Vendite e marketing**

- [Best practice per il limite del carrello prodotti](product-cart.md)
- [Best practice per la configurazione delle promozioni](product-cart-promotions.md)

## **Ambito progetto**

- [Inoltri per partner](partner-escalation.md)
- [Elaborazione archiviazione pagamenti](payment-processing-storage.md)

## **Estensioni di acquisto**

- [Best practice per l’utilizzo di estensioni di terze parti in Adobe Commerce](extensions.md)
