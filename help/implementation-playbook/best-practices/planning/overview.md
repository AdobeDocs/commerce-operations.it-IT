---
title: Fase di pianificazione dell’implementazione
description: Scopri le best practice di implementazione per la fase di pianificazione dei progetti Adobe Commerce.
role: Developer, Admin, User
feature: Best Practices
exl-id: 6baeac79-8dc3-45b4-bb25-8f2add8b3443
source-git-commit: 40d850add2ef8c51e9192758135768306b163780
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 1%

---

# Fase di pianificazione

La fase di pianificazione comprende le seguenti attività:

- Progettazione architettonica
- Progettazione catalogo
- Acquisto dell’estensione
- Ambito progetto
- Raccolta dei requisiti
- Vendite e marketing

Le sezioni seguenti includono informazioni sulle best practice per la fase di pianificazione.

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
    <td colspan="2"><em>Configurazione dell’applicazione</em></td>
  </tr>
  <tr>
    <td><a href="sites-stores-store-views.md">Configurare siti, archivi e visualizzazioni dello store</a></td>
    <td>Configurare siti, archivi e visualizzazioni dello store per ottimizzare le prestazioni del sito.</td>
  </tr>
  <tr>
    <td><a href="https://business.adobe.com/blog/how-to/the-usual-suspects-5-configuration-issues-to-maximize-your-peak-sales">Problemi di configurazione comuni</a></td>
    <td>Correggi ed evita i cinque problemi di configurazione più comuni per i siti Adobe Commerce.</td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-admin/systems/tools/cache-management.html">Memorizzazione in cache</a></td>
    <td>Utilizza gli strumenti di gestione della cache per migliorare le prestazioni del sito.</td>
  </tr>
  <tr>
    <td><a href="https://developer.adobe.com/commerce/php/development/cache/page/public-content/">Memorizzazione in cache a pagina intera</a></td>
    <td>Scopri come utilizzare i dati pubblici durante l’implementazione del caching nell’estensione Adobe Commerce o di Magento Open Source.</td>
  </tr>
  <tr>
    <td><a href="opcache-memory-size.md">Dimensioni memoria OPcache</a></td>
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
    <td>Configura le impostazioni di database e applicazioni per migliorare le prestazioni durante la distribuzione di Adobe Commerce nei progetti di infrastruttura cloud.</td>
  </tr>
  <tr>
    <td><a href="mysql-configuration.md">Configura MySQL</a></td>
    <td>Scopri in che modo i trigger MySQL e le connessioni slave influiscono sulle prestazioni del sito e come utilizzarle in modo efficace.</td>
  </tr>
  <tr>
    <td colspan="2"><em>Configurazione servizi</em></td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html">Configura Fastly</a></td>
    <td>Configura i servizi Fastly per il progetto di infrastruttura cloud Adobe Commerce on.</td>
  </tr>
  <tr>
    <td><a href="https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/monitor/new-relic.html">Configurare i canali di notifica per New Relic</a></td>
    <td>Accedi al tuo dashboard di New Relic e analizza i dati del tuo progetto Adobe Commerce on cloud infrastructure.</td>
  </tr>
  <tr>
    <td><a href="redis-service-configuration.md">Configurare Redis</a></td>
    <td>Migliora le prestazioni di caching utilizzando l’implementazione della cache Redis estesa per Adobe Commerce.</td>
  </tr>
  <tr>
    <td><a href="realpath-cache-size.md">Dimensioni cache realpath</a></td>
    <td>Ottimizza le prestazioni aggiornando la configurazione della cache PHP "readlpath" per utilizzare le impostazioni consigliate.</td>
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
| [Configurazione categoria](catalog-management.md#category-limits) | Configura le categorie di prodotti per prestazioni ottimali. |
| [Configurazione del prodotto&#x200B;](catalog-management.md#product-sku-limits) | Configura le SKU del prodotto per prestazioni ottimali. |
| [Configurazione della variante di prodotto](catalog-management.md#product-variations) | Configura le varianti di prodotto per prestazioni ottimali. |
| [Configurazione delle opzioni prodotto](catalog-management.md#product-options) | Configurare le opzioni del prodotto per prestazioni ottimali. |
| [Configurazione attributi prodotto&#x200B;](catalog-management.md#product-attributes) | Configura gli attributi del prodotto per prestazioni ottimali. |
| [Configurazione dell’impaginazione per gli elenchi di prodotti](catalog-management.md#product-listing-pagination) | Configura l’impaginazione dell’elenco dei prodotti per prestazioni ottimali. |

## Estensioni

| Best practice | Descrizione |
|-----------------------------------------------------------------|----------------------------------------------------------------------------------------|
| [Utilizzo di estensioni di terze parti in Adobe Commerce](extensions.md) | Scopri come evitare problemi di prestazioni causati da estensioni Adobe Commerce di terze parti. |

## Ambito progetto

| Best practice | Descrizione |
|--------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------|
| [Inoltri per partner](partner-escalation.md) | Preparati a risolvere un problema dei partner con un Account Team Adobe o scopri come evitare un problema di segnalazione. |
| [Elaborazione archiviazione pagamenti](payment-processing-storage.md) | Elabora e archivia in modo sicuro i dettagli del pagamento. |

## Vendite e marketing

| Best practice | Descrizione |
|------------------------------------------------------------|--------------------------------------------------------------|
| [Limiti del carrello dei prodotti](catalog-management.md#cart-limits) | Gestisci i limiti del carrello per prestazioni ottimali. |
| [Configurazione delle promozioni](catalog-management.md#promotions) | Configura vendite e promozioni per gli articoli in un carrello. |
