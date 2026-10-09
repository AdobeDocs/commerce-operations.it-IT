---
title: Consigli hardware
description: Scopri i consigli sull’hardware per prestazioni Adobe Commerce ottimali. Scopri i requisiti di CPU, memoria e storage per le implementazioni di produzione.
feature: Best Practices, Install
exl-id: ab548c4b-6f56-4409-a4ed-5c959939e04b
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%
---
# Raccomandazioni per l&#39;hardware

## CPU

[!DNL Commerce] nodi web gestiscono tutte le richieste che non sono memorizzate nella cache o che non possono essere memorizzate nella cache tramite l&#39;applicazione. Un core CPU può servire circa due (a volte fino a quattro) [!DNL Commerce] richieste in modo efficace. Utilizza la seguente equazione per determinare quanti nodi/core web sono necessari per elaborare tutte le richieste in ingresso senza metterle in coda:

```text
N[Cores] = (N[Expected Requests] / 2) + N [Expected Cron Processes]
```

Se prevedi che il carico di un negozio cambi, puoi aumentare manualmente il numero di nodi/core web per un periodo di vendita attivo. In alternativa, è possibile utilizzare un modello di ridimensionamento automatico per estendere automaticamente i livelli web.

## Memoria

### PHP

Magento ha diversi requisiti di memoria PHP, in base alla modalità di implementazione del sistema.  In generale, se si sta configurando un singolo archivio server, si consiglia di configurare la memoria PHP per 2G.  Se imposti un sito utilizzando la distribuzione della pipeline, consigliamo 2 GB sul server di build e 1 GB sui nodi web.

Scenari e requisiti di memoria PHP previsti:

* Webnode che serve solo le pagine della vetrina: 256 MB
* Nodo web che serve pagine di amministrazione con un catalogo di grandi dimensioni: 1 GB
* [!DNL Commerce] cron indicizzazione di un sito con un catalogo di grandi dimensioni: >256 MB (vedere [advanced-setup](../performance/advanced-setup.md) per ottimizzare le prestazioni).
* [!DNL Commerce] compilazione e distribuzione di risorse statiche: 756 MB
* Generazione profilo toolkit di prestazioni [!DNL Commerce]: > 1 GB di RAM PHP, > 16 MB [!DNL MySQL] impostazioni TMP_TABLE_SIZE e MAX_HEAP_TABLE_SIZE

### [!DNL MySQL]

Il database [!DNL Commerce] (così come qualsiasi altro database) è sensibile alla quantità di memoria disponibile per l&#39;archiviazione di dati e indici. Per sfruttare in modo efficace l&#39;indicizzazione dei dati [!DNL MySQL], la quantità di memoria disponibile deve essere almeno pari alla metà dei dati archiviati nel database.

### Cache

Se distribuisci più di [!DNL Commerce] e utilizzi Redis o [!DNL Varnish] per le cache, tieni presente i seguenti principi:

* L&#39;annullamento della validità della memoria della cache di [!DNL Varnish] a pagina intera è effettivo. Si consiglia di allocare memoria sufficiente a [!DNL Varnish] per mantenere in memoria le pagine più popolari
* La cache di sessione è un buon candidato per la configurazione per un&#39;istanza separata di Redis.  La configurazione della memoria per questo tipo di cache deve tenere conto della strategia di abbandono del carrello del sito e di quanto tempo una sessione deve aspettarsi di rimanere nella cache
* I Redis devono avere una quantità di memoria sufficiente per contenere tutte le altre cache in memoria per ottenere prestazioni ottimali.  La cache di blocco sarà il fattore chiave per determinare la quantità di memoria da configurare.  La cache dei blocchi cresce in relazione al numero di pagine su un sito (numero di sku x numero di visualizzazioni dello store)

## Larghezza di banda di rete

Una larghezza di banda di rete sufficiente è uno dei requisiti chiave per lo scambio di dati tra nodi web, database, server di caching/sessione e altri servizi. Poiché [!DNL Commerce] sfrutta efficacemente il caching per prestazioni elevate, il sistema può scambiare attivamente dati con server di caching come Redis. Se Redis si trova su un server remoto, è necessario fornire un canale di rete sufficiente tra i nodi web e il server di caching per evitare colli di bottiglia nelle operazioni di lettura/scrittura.
