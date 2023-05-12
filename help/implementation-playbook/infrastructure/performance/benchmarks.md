---
title: Benchmark delle prestazioni
description: Esamina i risultati del benchmark delle prestazioni per le implementazioni Adobe Commerce ospitate sull’infrastruttura cloud di Adobe.
exl-id: cc9b090a-a504-4df3-aa32-81882f431dd9
source-git-commit: 09a42dc68836b34eab2c9d90879b897729cd1b09
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 0%

---

# Riepilogo benchmark

I risultati del benchmark delle prestazioni di Adobe Commerce 2.4.5 riflettono le prestazioni misurate su un&#39;istanza Adobe Commerce implementata con la seguente infrastruttura e componenti aggiuntivi.
- [Ambiente cloud Pro](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html) con [architettura scalata](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html)
- [B2B per Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-admin/b2b/introduction.html)
- [Adobe Commerce Inventory management](https://experienceleague.adobe.com/docs/commerce-admin/inventory/introduction.html)
- [Adobe Stock](https://experienceleague.adobe.com/docs/commerce-admin/content-design/media/adobe-stock/adobe-stock.html)

Non sono disponibili personalizzazioni aggiuntive.

Le informazioni seguenti riassumono i risultati del benchmark e forniscono informazioni sull&#39;ambiente e i dati utilizzati durante il test.

## Metriche delle prestazioni chiave

La figura seguente mostra la configurazione Commerce Store per il benchmark delle prestazioni e le metriche delle prestazioni chiave dai risultati del test.

![Performance Benchmark JMeter e infrastruttura di produzione](../../../assets/performance/images/performance-benchmark-kpis-245-cloud.png){width="700" zoomable="yes"}

In base ai criteri di test che imitano un&#39;organizzazione B2C aziendale, il sistema può gestire il traffico richiesto e i numeri d&#39;ordine durante i picchi, a un flusso di carico standard.

### Funzioni principali

- **Ordini**—Elaborato 3.481 ordini al minuto mantenendo al tempo stesso un tempo di risposta inferiore a 2 secondi per il 99o percentile (il 99% delle richieste sono state servite con un tempo di risposta inferiore a 2 secondi).
- **Visualizzazioni pagina**- Gestito oltre 2 milioni di visualizzazioni di pagina all’ora mantenendo i tempi di risposta inferiori a 2 secondi per il 99o percentile.
- **SKU efficaci**—Il profilo del cliente comprendeva 242 milioni di variazioni di prezzo diverse (<a href="https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/planning/product-sku-limits.html">eSKU</a>) per 250.000 prodotti.
- **Richieste GraphQL**- Il sistema è stato scalato a 10.500 richieste GraphQL non memorizzate nella cache al minuto, mantenendo i tempi di risposta inferiori a 2 secondi per il 99o percentile.
- **Utenti amministratori simultanei**- Il sistema è stato scalato per supportare 500 utenti amministratori simultanei mantenendo tempi di risposta inferiori a 2 secondi per il 99o percentile.

## Ambiente di prova

I risultati di benchmark delle prestazioni sono stati ottenuti effettuando test su un’istanza Adobe Commerce 2.4.5 implementata in un ambiente cloud Pro con architettura scalata. Nell&#39;istanza sono stati inoltre installati, configurati e abilitati i moduli di integrazione Adobe Commerce B2B, Inventory management e Adobe Stock.

I dati del test delle prestazioni per il profilo di test sono stati generati utilizzando <a href="https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html">Toolkit di prestazioni</a>.

Le misurazioni delle prestazioni si basano su simulazioni delle attività quotidiane per i clienti e gli utenti aziendali. I valori riflettono una velocità effettiva vicina al massimo per ogni singolo caso, ma non riflettono modelli di business unici, come vendite private o vendite flash.

- **LUMA Storefront**
   - 3000 utenti simultanei su vetrina
   - Imposta al 30% della frequenza di hit della cache CDN

      L’utilizzo efficace del livello di cache aumenta il numero di visualizzazioni di pagina all’ora.

- **API GraphQL**
   - 250 thread simultanei
   - Imposta a 0% tasso di hit della cache CDN

      I tempi di risposta migliorano notevolmente con un livello di memorizzazione in cache davanti a GraphQL.

- **Web amministratore**
   - 500 utenti simultanei
   - Imposta a 0% tasso di hit della cache CDN

## Specifiche dell&#39;ambiente di prova

Il test di carico è stato completato utilizzando i profili di carico JMeter eseguiti sull’istanza Adobe Commerce. Durante il test sono stati utilizzati tre nodi web e tre nodi di servizio. L&#39;immagine seguente descrive il punto di ingresso dell&#39;infrastruttura JMeter e Production.

![Performance Benchmark JMeter e infrastruttura di produzione](https://git.corp.adobe.com/storage/user/43354/files/4d801e3e-96b7-4193-b94f-12571263b495){width="700" zoomable="yes"}

### Applicazione

<a href="https://experienceleague.adobe.com/docs/commerce-operations/release/notes/adobe-commerce/2-4-5.html">Adobe Commerce 2.4.5</a> implementato su infrastruttura cloud con architettura Pro.

### Infrastruttura

Per il benchmark delle prestazioni, Adobe Commerce 2.4.5 è stato distribuito su un [infrastruttura scalabile](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html) con la seguente capacità.

- **Specifiche dei nodi web**
   - vCPU 216 (72 x 3 nodi)
   - Memoria 432 GiB (144 x 3 nodi)
   - Larghezza di banda di rete 768 Gb/s (256 x 3 nodi)
   - Storage con provisioning 100 GB

- **Specifiche dei nodi di servizio**
   - vCPU 192 (64 x 3 nodi)
   - Memoria 768 GiB (256 x 3 nodi)
   - Larghezza di banda di rete 60 Gb/s (20 x 3 nodi)
   - Larghezza di banda EBS 40800 Mbps (13600 x 3 nodi)
   - Storage con provisioning di 1100 GB
