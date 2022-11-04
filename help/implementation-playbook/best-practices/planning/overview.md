---
title: Fase di pianificazione dell'implementazione
description: Scopri le best practice di implementazione per la fase di pianificazione dei progetti Adobe Commerce.
role: Developer, Admin, User
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Fase di pianificazione

La fase di pianificazione include le seguenti attività:

- Raccolta dei requisiti
- Progettazione architettonica
- Progettazione catalogo
- Ambito del progetto
- Provisioning dell&#39;account
- Accesso utente
- Acquisto di estensioni

Le sezioni seguenti contengono informazioni sulle best practice per la fase di pianificazione.

## Raccolta dei requisiti

- **Configurazione dell&#39;applicazione**
   - [Best practice per la configurazione di siti, store e viste store (infrastruttura cloud)](sites-stores-store-views.md)
   - [Come prevenire e risolvere i cinque problemi di configurazione più comuni per i siti Adobe Commerce](https://business.adobe.com/blog/how-to/usual-suspects-five-configuration-fixes-maximize-your-peak-sales)
   - [Best practice per la memorizzazione in cache](https://docs.magento.com/user-guide/system/cache-management.html#best-practices-for-caching)
   - [Memorizzazione in cache di pagine complete](https://developer.adobe.com/commerce/php/development/cache/page/public-content/)
   - [Dimensione della memoria OPcache](opcache-memory-size.md)
   - [Configurazione del reporting](reporting-configuration.md)

- **Configurazione del database**
   - [Best practice per la configurazione del database per le distribuzioni cloud &#x200B;](database-on-cloud.md)
   - [&#x200B; di configurazione della connessione slave MySQL](configure-mysql-slave-connection-on-cloud.md)
   - [Utilizzo di MySQL trigger](mysql-triggers-usage.md)

- **Configurazione dei servizi**
   - [Imposta in modo rapido](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
   - [Nuova relè: configurare i canali di notifica](https://devdocs.magento.com/cloud/project/new-relic.html#configure-notification-channels)
   - [Best practice per la configurazione del servizio Redis &#x200B;](redis-service-configuration.md)
   - [Best practice per le dimensioni della cache del percorso reale](realpath-cache-size.md)

## **Progettazione architettonica**

<!--Asset not yet integrated
- [GRA Architecture examples](https://wiki.corp.adobe.com/x/kD4ykw)
-->
- [Informazioni sull’architettura di riferimento globale](../../../implementation-playbook/architecture/global-reference.md)

## **Progettazione catalogo**

Gli argomenti seguenti descrivono le best practice per l’ottimizzazione delle prestazioni per la configurazione del catalogo Adobe Commerce, compresi i valori massimi consigliati per il numero di categorie, SKU per l’efficacia dei prodotti, varianti di prodotto, attributi e opzioni di prodotto e altro ancora.

- [Configurazione della categoria](category-limits.md)
- [&#x200B; di configurazione del prodotto](product-sku-limits.md)
- [Configurazione della variazione del prodotto](product-variations.md)
- [Configurazione delle opzioni di prodotto](product-options.md)
- [&#x200B; di configurazione degli attributi di prodotto](product-attributes-and-options.md)
- [Configurazione dell’impaginazione per gli elenchi di prodotti](product-listing-pagination.md)

## **Vendite e marketing**

- [Best practice per il limite del carrello dei prodotti &#x200B;](product-cart.md)
- [Best practice per la configurazione delle promozioni](product-cart-promotions.md)

## **Ambito del progetto**

- [Aumento dei partner](partner-escalation.md)

## **Estensioni di acquisto**

- [Tecniche consigliate per l’utilizzo di estensioni di terze parti in Adobe Commerce &#x200B;](extensions.md)
