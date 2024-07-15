---
title: Benchmark delle prestazioni
description: Rivedi i risultati dei benchmark delle prestazioni per le implementazioni Adobe Commerce in hosting sull’infrastruttura cloud Adobe.
exl-id: cc9b090a-a504-4df3-aa32-81882f431dd9
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '574'
ht-degree: 0%

---

# Riepilogo benchmark

I risultati del benchmark delle prestazioni di Adobe Commerce 2.4.5 riflettono le prestazioni misurate su un’istanza Adobe Commerce implementata con l’infrastruttura e i componenti aggiuntivi seguenti.
- [Ambiente cloud Pro](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html) con [architettura scalata](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html)
- [B2B per Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-admin/b2b/introduction.html)
- [Adobe Commerce Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html)
- [Adobe Stock](https://experienceleague.adobe.com/docs/commerce-admin/content-design/media/adobe-stock/adobe-stock.html)

Non sono disponibili personalizzazioni aggiuntive.

Le informazioni seguenti riassumono i risultati del benchmark e forniscono informazioni sull’ambiente e sui dati utilizzati durante il test.

## Metriche delle prestazioni chiave

La figura seguente mostra la configurazione dell’archivio Commerce per il benchmark delle prestazioni e le metriche delle prestazioni chiave dai risultati del test.

![Benchmark delle prestazioni JMeter e infrastruttura di produzione](../../../assets/performance/images/performance-benchmark-kpis-245-cloud.png){width="700" zoomable="yes"}

In base a criteri di test che simulano un&#39;organizzazione B2C aziendale, il sistema è in grado di gestire il traffico richiesto e i numeri di ordine durante i periodi di picco, con un flusso di carico standard.

### Elementi di rilievo sulle prestazioni

- **Ordini**: elaborati 3.481 ordini al minuto mantenendo i tempi di risposta inferiori a 2 secondi per il 99° percentile (il 99% delle richieste è stato servito con un tempo di risposta inferiore a 2 secondi).
- **Visualizzazioni pagina**: gestite oltre 2 milioni di visualizzazioni di pagina all&#39;ora mantenendo i tempi di risposta inferiori a 2 secondi per il 99° percentile.
- **SKU effettivi**. Il profilo cliente include 242 milioni di variazioni di prezzo diverse (<a href="https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/product-sku-limits.html">eSKU</a>) per 250.000 prodotti.
- **Richieste GraphQL**: il sistema è stato scalato a 10.500 richieste GraphQL non memorizzate nella cache al minuto, mantenendo al contempo tempi di risposta inferiori a 2 secondi per il 99° percentile.
- **Utenti amministratori simultanei** - Il sistema è stato scalato per supportare 500 utenti amministratori simultanei, mantenendo al contempo i tempi di risposta inferiori a 2 secondi per il 99° percentile.

## Ambiente di test

I risultati dei benchmark delle prestazioni sono stati ottenuti testando un’istanza Adobe Commerce 2.4.5 implementata in un ambiente cloud Pro con architettura scalata. L’istanza aveva anche i moduli di integrazione Adobe Commerce B2B, Inventory management e Adobe Stock installati, configurati e abilitati.

I dati di test delle prestazioni per il profilo di test sono stati generati utilizzando <a href="https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html">Performance Toolkit</a>.

Le misurazioni delle prestazioni si basano sulle attività quotidiane simulate del punto vendita per i clienti e gli utenti aziendali. I valori riflettono un throughput vicino al massimo per ogni caso, ma non riflettono modelli di business univoci, come le vendite private o flash.

- **Vetrina LUMA**
   - 3000 utenti simultanei in vetrina
   - Imposta su 30% di hit della cache CDN

     L’utilizzo effettivo del livello di cache aumenta il numero di visualizzazioni di pagina all’ora.

- **API GraphQL**
   - 250 thread simultanei
   - Imposta su 0% di hit della cache CDN

     I tempi di risposta migliorano in modo significativo con un livello di caching davanti a GraphQL.

- **Web amministratore**
   - 500 utenti simultanei
   - Imposta su 0% di hit della cache CDN

## Specifiche dell’ambiente di test

Il test di carico è stato completato utilizzando i profili di carico JMeter eseguiti sull’istanza Adobe Commerce. Durante il test sono stati utilizzati tre nodi web e tre nodi di servizio. L’immagine seguente descrive il punto di ingresso di JMeter e dell’infrastruttura di produzione.

![Benchmark delle prestazioni JMeter e infrastruttura di produzione](https://git.corp.adobe.com/storage/user/43354/files/4d801e3e-96b7-4193-b94f-12571263b495){width="700" zoomable="yes"}

### Applicazione

<a href="https://experienceleague.adobe.com/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html">Adobe Commerce 2.4.5</a> implementato in un&#39;infrastruttura cloud con architettura Pro.

### Infrastruttura

Per il benchmark delle prestazioni, Adobe Commerce 2.4.5 è stato distribuito su un&#39;infrastruttura [scalabile](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html) con la seguente capacità.

- **Specifiche nodo Web**
   - vCPU 216 (72 x 3 nodi)
   - Memoria 432 GiB (144 x 3 nodi)
   - Larghezza di banda di rete 768 Gb/s (256 x 3 nodi)
   - Larghezza di banda EBS 57000 Mbps (19000 x 3 nodi)
   - Storage con provisioning da 100 GB

- **Specifiche del nodo di servizio**
   - vCPU 192 (64 x 3 nodi)
   - Memoria 768 GiB (256 x 3 nodi)
   - Larghezza di banda di rete 60 Gb/s (20 x 3 nodi)
   - Larghezza di banda EBS 40800 Mbps (13600 x 3 nodi)
   - Storage con provisioning da 1100 GB
