---
title: Fase di pianificazione dell’implementazione
description: Scopri le best practice di implementazione per la fase di pianificazione dei progetti Adobe Commerce.
role: Developer, Admin, User
feature: Best Practices
exl-id: 6baeac79-8dc3-45b4-bb25-8f2add8b3443
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 1%

---

# Fase di pianificazione

La fase di pianificazione prevede le seguenti attività:

- Progettazione architettonica
- Progettazione catalogo
- Acquisto dell’estensione
- Ambito progetto
- Raccolta dei requisiti
- Vendite e marketing

Nelle sezioni seguenti sono incluse informazioni sulle procedure consigliate per la fase di pianificazione.

## Raccolta dei requisiti

<table>
<thead>
  <tr>
    <th>Best practice</th>
    <th>Descrizione</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td colspan="2"><em>Configurazione dell'applicazione</em></td>
  </tr>
  <tr>
    <td><a href="sites-stores-store-views.md">Configurazione di visualizzazioni di siti, archivi e store</a></td>
    <td>Configura siti, archivi e visualizzazioni store per massimizzare la prestazioni del sito.</td>
  </tr>
  <tr>
    <td><a href="https://business.adobe.com/blog/how-to/the-usual-suspects-5-configuration-issues-to-maximize-your-peak-sales">Problemi di configurazione comuni</a></td>
    <td>Risolvi e previeni i cinque problemi di configurazione più comuni per i siti Adobe Systems Commerce.</td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cache-management.html">Memorizzazione in cache</a></td>
    <td>Utilizza gli strumenti di gestione della cache per migliorare le prestazioni del sito.</td>
  </tr>
  <tr>
    <td><a href="https://developer.adobe.com/commerce/php/development/cache/page/public-content/">caching a pagina intera</a></td>
    <td>Scopri come lavorare con i dati pubblici quando implementi caching nell'estensione Adobe Systems Commerce.</td>
  </tr>
  <tr>
    <td><a href="opcache-memory-size.md">Dimensione della memoria OPcache</a></td>
    <td>Evita il degrado delle prestazioni con impostazioni specifiche di consumo della memoria OPcache.</td>
  </tr>
  <tr>
    <td><a href="reporting-configuration.md">Configurare la generazione di rapporti</a></td>
    <td>Ottimizza le prestazioni del sito rimuovendo il modulo di reporting se non lo utilizzi.</td>
  </tr>
  <tr>
    <td colspan="2"><em>Configurazione del database</em></td>
  </tr>
  <tr>
    <td><a href="database-on-cloud.md">Configurare il database per le distribuzioni cloud</a></td>
    <td>Configurare le impostazioni del database e della applicazione per migliorare le prestazioni durante la distribuzione di Adobe Systems Commerce su progetti infrastruttura cloud.</td>
  </tr>
  <tr>
    <td><a href="mysql-configuration.md">Configura MySQL</a></td>
    <td>Scopri come i trigger MySQL e le connessioni slave influenzano prestazioni del sito e come usarli in modo efficace.</td>
  </tr>
  <tr>
    <td colspan="2"><em>Configurazione dei servizi</em></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html">Configurazione rapida</a></td>
    <td>Configura i servizi Fastly per il tuo progetto Adobe Systems Commerce su infrastruttura cloud.</td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic.html">Configurare notifica canali per Nuovo Relic</a></td>
    <td>Accedi alla dashboard di Nuovo Relic e analizza i dati del tuo progetto Adobe Systems Commerce su infrastruttura cloud.</td>
  </tr>
  <tr>
    <td><a href="redis-service-configuration.md">Configurare Redis</a></td>
    <td>Migliora le prestazioni di caching utilizzando l’implementazione della cache Redis estesa per Adobe Commerce.</td>
  </tr>
  <tr>
    <td><a href="realpath-cache-size.md">Dimensione cache Realpath</a></td>
    <td>Ottimizza le prestazioni aggiornando la configurazione della cache 'readlpath' di PHP per utilizzare le impostazioni consigliate.</td>
  </tr>
</tbody>
</table>

## Progettazione architettonica

| Best practice | Descrizione |
|----------------------------------------------------------------------------------------|----------------------------------------------------------|
| [Architettura di riferimento globale (GRA)](../../architecture/global-reference/examples.md) | Comprendere i metodi comuni per organizzare una base di codice GRA. |

## Progettazione catalogo

| Best practice | Descrizione |
|---------------------------------------------------------------------------------------------------|---------------------------------------------------------------|
| [Categoria configurazione](catalog-management.md#category-limits) | Configura le categorie di prodotti per ottenere prestazioni ottimali. |
| [Configurazione del prodotto](catalog-management.md#product-sku-limits) | Configura gli SKU dei prodotti per ottenere prestazioni ottimali. |
| [Configurazione della variante di prodotto](catalog-management.md#product-variations) | Configura le varianti di prodotto per ottenere prestazioni ottimali. |
| [Configurazione opzioni prodotto](catalog-management.md#product-options) | Configurare le opzioni del prodotto per prestazioni ottimali. |
| [Configurazione attributi prodotto&#x200B;](catalog-management.md#product-attributes) | Configura gli attributi del prodotto per ottenere prestazioni ottimali. |
| [Configurazione dell&#39;impaginazione per le offerte di prodotti](catalog-management.md#product-listing-pagination) | Configura l’impaginazione dell’elenco dei prodotti per prestazioni ottimali. |

## Estensioni

| Best practice | Descrizione |
|-----------------------------------------------------------------|----------------------------------------------------------------------------------------|
| [Utilizzo di estensioni di terze parti in Adobe Commerce](extensions.md) | Scopri come evitare problemi di prestazioni causati da estensioni Adobe Commerce di terze parti. |

## Ambito del progetto

| Best practice | Descrizione |
|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| [Escalation dei partner](partner-escalation.md) | Preparati a risolvere un problema di partner con un team di account Adobe Systems o scopri come evitare un&#39;escalation. |
| [Elaborazione archiviazione pagamenti](payment-processing-storage.md) | Elabora e store dati di pagamento in modo sicuro. |

## Vendite e marketing

| Best practice | Descrizione |
|------------------------------------------------------------|--------------------------------------------------------------|
| [Limiti del carrello prodotti](catalog-management.md#cart-limits) | Gestisci i limiti del carrello per prestazioni ottimali. |
| [Configurazione delle promozioni](catalog-management.md#promotions) | Configura le vendite e le promozioni per gli articoli in un carrello. |
