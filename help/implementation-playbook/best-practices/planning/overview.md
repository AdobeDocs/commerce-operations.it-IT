---
title: Fase di pianificazione dell’implementazione
description: Scopri le best practice di implementazione per la fase di pianificazione dei progetti Adobe Commerce.
role: Developer, Admin, User
feature: Best Practices
exl-id: 6baeac79-8dc3-45b4-bb25-8f2add8b3443
source-git-commit: 3e0187b7eeb6475ea9c20bc1da11c496b57853d1
workflow-type: tm+mt
source-wordcount: '243'
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
   - [Configurazione MySQL&#x200B;](mysql-configuration.md)

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

- [Configurazione categoria](catalog-management.md#category-limits)
- [Configurazione del prodotto&#x200B;](catalog-management.md#product-sku-limits)
- [Configurazione della variante di prodotto](catalog-management.md#product-variations)
- [Configurazione delle opzioni prodotto](catalog-management.md#product-options)
- [Configurazione attributi prodotto&#x200B;](catalog-management.md#product-attributes)
- [Configurazione dell’impaginazione per gli elenchi di prodotti](catalog-management.md#product-listing-pagination)

## **Vendite e marketing**

- [Best practice per il limite del carrello prodotti](catalog-management.md#cart-limits)
- [Best practice per la configurazione delle promozioni](catalog-management.md#promotions)

## **Ambito progetto**

- [Inoltri per partner](partner-escalation.md)
- [Elaborazione archiviazione pagamenti](payment-processing-storage.md)

## **Estensioni di acquisto**

- [Best practice per l’utilizzo di estensioni di terze parti in Adobe Commerce](extensions.md)
