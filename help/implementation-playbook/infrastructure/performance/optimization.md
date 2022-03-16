---
title: Ottimizzazione delle prestazioni
description: Scopri tutte le informazioni sull’ottimizzazione delle prestazioni e i passaggi da intraprendere per rivedere le prestazioni dell’implementazione Adobe Commerce.
exl-id: 506ef2cc-c6fd-4401-afa5-a71e7b9871e6
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Ottimizzazione delle prestazioni

Le prestazioni sono un grande argomento. Quando gli utenti sperimentano un sito lento o non reattivo, influisce sulla conversione. Per ottimizzare le prestazioni di Adobe Commerce sull’implementazione dell’infrastruttura cloud, si consiglia di effettuare le seguenti operazioni:

- Valutare il problema
- Misurare le prestazioni
- Identificare una parte del sistema fondamentale per il miglioramento delle prestazioni
- Modifica parte del sistema per rimuovere il collo di bottiglia
- Misurare le prestazioni dopo la modifica
- Se meglio, adottarlo o ripristinarlo

## Problemi di prestazioni tipici

L&#39;impatto di un&#39;esperienza lenta è solitamente definito da due indicatori, e ogni fattore può essere causato per tonnellate di ragioni.

L’elevato tempo-al-primo byte (TTFB) è di solito considerato come un indicatore che definisce la velocità di risposta del server. L’ora non proviene solo dall’esecuzione del codice sorgente per la gestione della richiesta, ma può anche essere influenzata dai seguenti fattori:

- Ricerca DNS
- Query lente da livello DB
- Tempo CPU da ogni livello di applicazione
- Limitazione della memoria
- L&#39;attesa I/O può influire sulla lettura e scrittura del file, il servizio di connessione tramite socket
- Impostazioni software (nginx, PHP, MySQL, Redis, Varnish)
- Larghezza di banda della rete
- Memorizzazione in cache non valida
- Codice non valido
- Metodo di integrazione non valido
- Dipendenza della risposta lenta del servizio di terze parti
- Architettura senza scalabilità

Le risorse a caricamento lento sono solitamente considerate un indicatore che definisce la risorsa statica (CSS, JavaScript, immagini, video, risposta di chiamate Ajax di terze parti).

Adobe Commerce può essere scalato con la tua azienda attraverso le sue funzionalità:

![Diagramma che mostra le funzionalità scalabili di Adobe Commerce](../../../assets/playbooks/scalable-capabilities.svg)

Ci sono anche fattori chiave che determinano la scala del commercio, che influiscono anche sulle prestazioni complessive.

- Catalogo prodotti complesso e di grandi dimensioni
- Ampio numero di amministratori
- vetrine globali
- Traffico ad alta variabile
- Espansione dei punti di contatto
- Transazioni ad alto volume

Per architetture a strati e memorizzabili in cache costruite per la scala, potete usare questo grafico come riferimento.

![Diagramma che mostra come utilizzare l’API GraphQL di Adobe Commerce in un’architettura memorizzabile in cache](../../../assets/playbooks/cacheable-architecture.svg)
