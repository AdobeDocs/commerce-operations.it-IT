---
title: Recommendations hardware
description: Rivedi un elenco di hardware consigliati relativi alle prestazioni ottimali delle distribuzioni Adobe Commerce e Magenti Open Source.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---


# Raccomandazioni in materia di hardware

## CPU

[!DNL Commerce] i nodi web servono tutte le richieste che non sono memorizzate nella cache o che non possono essere memorizzate nella cache tramite l’applicazione. Un nucleo CPU può essere utilizzato intorno a due (a volte fino a quattro) [!DNL Commerce] richiede in modo efficace. Utilizza la seguente equazione per determinare quanti nodi/core web devi elaborare tutte le richieste in arrivo senza metterle in coda:

```
N[Cores] = (N[Expected Requests] / 2) + N [Expected Cron Processes]
```

Se si prevede un cambiamento del carico di un negozio, è possibile aumentare manualmente il numero di nodi/core Web per un periodo di vendita attivo. In alternativa, è possibile utilizzare un modello di ridimensionamento automatico per estendere automaticamente i livelli web.

## Memoria

### PHP

Il Magento ha requisiti di memoria PHP diversi, in base alla modalità di implementazione del sistema.  In generale, se si sta configurando un singolo server store, si consiglia di configurare la memoria PHP per 2G.  Se stai configurando un sito utilizzando la distribuzione della pipeline, consigliamo 2 GB sul server di build e 1 GB sui nodi web.

Scenari e requisiti di memoria PHP previsti:

* Webnode che serve solo pagine di vetrina: 256 MB
* Webnode che serve pagine di amministrazione con un catalogo grande: 1 GB
* [!DNL Commerce] cron indicizzazione di un sito con un catalogo grande: >256 MB (Vedi [configurazione avanzata](../performance/advanced-setup.md) per ottimizzare le prestazioni).
* [!DNL Commerce] compilare e distribuire risorse statiche: 756 MB
* [!DNL Commerce] generazione di profili toolkit di prestazioni: >1 GB di RAM PHP, >16 MB [!DNL MySQL] Impostazioni TMP_TABLE_SIZE e MAX_HEAP_TABLE_SIZE

### [!DNL MySQL]

La [!DNL Commerce] il database (così come qualsiasi altro database) è sensibile alla quantità di memoria disponibile per la memorizzazione di dati e indici. Per sfruttare in modo efficace [!DNL MySQL] l&#39;indicizzazione dei dati, la quantità di memoria disponibile deve essere almeno pari alla metà della dimensione dei dati memorizzati nel database.

### Cache

Se distribuisci più [!DNL Commerce] e utilizzando Redis o [!DNL Varnish] per le cache, tieni a mente i seguenti principi:

* [!DNL Varnish] l&#39;annullamento della validità della memoria cache a pagina intera è efficace, si consiglia di allocare una quantità sufficiente di memoria a [!DNL Varnish] per conservare le pagine più popolari in memoria
* La cache della sessione è un buon candidato per la configurazione per un&#39;istanza separata di Redis.  La configurazione della memoria per questo tipo di cache dovrebbe considerare la strategia di abbandono del carrello del sito e per quanto tempo una sessione dovrebbe rimanere nella cache
* Redis dovrebbe avere una memoria sufficiente allocata per contenere tutte le altre cache in memoria per ottenere prestazioni ottimali.  La cache del blocco sarà il fattore chiave per determinare la quantità di memoria da configurare.  La cache del blocco cresce in base al numero di pagine su un sito (numero di skus x numero di visualizzazioni dello store)

## Larghezza di banda della rete

Una larghezza di banda di rete sufficiente è uno dei requisiti chiave per lo scambio di dati tra nodi web, database, server di memorizzazione in cache/sessione e altri servizi. Perché [!DNL Commerce] sfrutta efficacemente la memorizzazione in cache per prestazioni elevate, il sistema può scambiare attivamente i dati con server di caching come Redis. Se Redis si trova su un server remoto, è necessario fornire un canale di rete sufficiente tra i nodi web e il server di caching per evitare i colli di bottiglia nelle operazioni di lettura/scrittura.
