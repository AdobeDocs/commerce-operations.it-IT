---
title: Ottimizzazione delle prestazioni
description: Scopri tutte le informazioni sull’ottimizzazione delle prestazioni e i passaggi da intraprendere per esaminare le prestazioni dell’implementazione di Adobe Commerce.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---


# Ottimizzazione delle prestazioni

Performance is a big topic. When users experience a slow or unresponsive site, it affects conversion. Per ottimizzare le prestazioni di Adobe Commerce sull’implementazione dell’infrastruttura cloud, si consiglia di effettuare le seguenti operazioni:

- Valutare il problema
- Measure performance
- Identificare una parte del sistema fondamentale per il miglioramento delle prestazioni
- Modifica parte del sistema per rimuovere il collo di bottiglia
- Misurare le prestazioni dopo la modifica
- Se meglio, adottarlo o ripristinarlo

## Problemi di prestazioni tipici

L&#39;impatto di un&#39;esperienza lenta è solitamente definito da due indicatori, e ogni fattore può essere causato per tonnellate di ragioni.

L’elevato tempo-al-primo byte (TTFB) è di solito considerato come un indicatore che definisce la velocità di risposta del server. The time not only comes from source code execution for handling the request, but it can also be impacted by the following factors:

- DNS lookup
- Query lente da livello DB
- Tempo CPU da ogni livello di applicazione
- Memory limitation
- L&#39;attesa I/O può influire sulla lettura e scrittura del file, il servizio di connessione tramite socket
- Impostazioni software (nginx, PHP, MySQL, Redis, Varnish)
- Network bandwidth
- Bad caching
- Codice non valido
- Metodo di integrazione non valido
- Dipendenza della risposta lenta del servizio di terze parti
- Architecture without scalability

Le risorse a caricamento lento sono solitamente considerate un indicatore che definisce la risorsa statica (CSS, JavaScript, immagini, video, risposta di chiamate Ajax di terze parti).

Adobe Commerce can scale with your business through its capabilities:

![Diagram showing the scalable capabilities of Adobe Commerce](../../../assets/playbooks/scalable-capabilities.svg)

Ci sono anche fattori chiave che determinano la scala del commercio, che influiscono anche sulle prestazioni complessive.

- Catalogo prodotti complesso e di grandi dimensioni
- Large numbers of admins
- vetrine globali
- Traffico ad alta variabile
- Espansione dei punti di contatto
- High-volume transactions

Per architetture a strati e memorizzabili in cache costruite per la scala, potete usare questo grafico come riferimento.

![Diagramma che mostra come utilizzare l’API GraphQL di Adobe Commerce in un’architettura memorizzabile in cache](../../../assets/playbooks/cacheable-architecture.svg)
