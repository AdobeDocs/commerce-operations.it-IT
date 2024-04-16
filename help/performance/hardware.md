---
title: Recommendations hardware
description: Rivedi un elenco di componenti hardware consigliati relativi alle prestazioni ottimali delle implementazioni Adobe Commerce.
feature: Best Practices, Install
exl-id: ab548c4b-6f56-4409-a4ed-5c959939e04b
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '466'
ht-degree: 0%

---

# Raccomandazioni per l&#39;hardware

## CPU

[!DNL Commerce] i nodi web gestiscono tutte le richieste che non sono memorizzate nella cache o che non possono essere memorizzate nella cache tramite l’applicazione. Un core CPU può servire circa due (a volte fino a quattro) [!DNL Commerce] richieste efficaci. Utilizza la seguente equazione per determinare quanti nodi/core web sono necessari per elaborare tutte le richieste in ingresso senza metterle in coda:

```
N[Cores] = (N[Expected Requests] / 2) + N [Expected Cron Processes]
```

Se prevedi che il carico di un negozio cambi, puoi aumentare manualmente il numero di nodi/core web per un periodo di vendita attivo. In alternativa, è possibile utilizzare un modello di ridimensionamento automatico per estendere automaticamente i livelli web.

## Memoria

### PHP

Il Magento ha requisiti di memoria PHP diversi, in base alla modalità di distribuzione.  In generale, se si sta configurando un singolo archivio server, si consiglia di configurare la memoria PHP per 2G.  Se imposti un sito utilizzando la distribuzione della pipeline, consigliamo 2 GB sul server di build e 1 GB sui nodi web.

Scenari e requisiti di memoria PHP previsti:

* Webnode che serve solo le pagine della vetrina: 256 MB
* Nodo web che serve pagine di amministrazione con un catalogo di grandi dimensioni: 1 GB
* [!DNL Commerce] cron indicizzazione di un sito con un catalogo di grandi dimensioni: >256 MB (vedere [advanced-setup](../performance/advanced-setup.md) per ottimizzare le prestazioni).
* [!DNL Commerce] compilazione e distribuzione di risorse statiche: 756 MB
* [!DNL Commerce] generazione di profili toolkit di prestazioni: >1 GB di RAM PHP, >16 MB [!DNL MySQL] Impostazioni TMP_TABLE_SIZE e MAX_HEAP_TABLE_SIZE

### [!DNL MySQL]

Il [!DNL Commerce] Il database (così come qualsiasi altro database) è sensibile alla quantità di memoria disponibile per l&#39;archiviazione di dati e indici. Per sfruttare in modo efficace [!DNL MySQL] indicizzazione dei dati, la quantità di memoria disponibile deve essere, come minimo, quasi la metà dei dati memorizzati nel database.

### Cache

Se distribuisci più [!DNL Commerce] e utilizzando Redis o [!DNL Varnish] per le cache, tieni presente i seguenti principi:

* [!DNL Varnish] l&#39;annullamento della validità della memoria cache a pagina intera è valido. si consiglia di allocare una quantità di memoria sufficiente a [!DNL Varnish] per conservare in memoria le pagine più popolari
* La cache di sessione è un buon candidato per la configurazione per un&#39;istanza separata di Redis.  La configurazione della memoria per questo tipo di cache deve tenere conto della strategia di abbandono del carrello del sito e di quanto tempo una sessione deve aspettarsi di rimanere nella cache
* I Redis devono avere una quantità di memoria sufficiente per contenere tutte le altre cache in memoria per ottenere prestazioni ottimali.  La cache di blocco sarà il fattore chiave per determinare la quantità di memoria da configurare.  La cache dei blocchi cresce in relazione al numero di pagine su un sito (numero di sku x numero di visualizzazioni dello store)

## Larghezza di banda di rete

Una larghezza di banda di rete sufficiente è uno dei requisiti chiave per lo scambio di dati tra nodi web, database, server di caching/sessione e altri servizi. Perché [!DNL Commerce] sfrutta in modo efficace il caching per prestazioni elevate, il sistema può scambiare attivamente i dati con server di caching come Redis. Se Redis si trova su un server remoto, è necessario fornire un canale di rete sufficiente tra i nodi web e il server di caching per evitare colli di bottiglia nelle operazioni di lettura/scrittura.
