---
title: Ottimizzazione delle prestazioni
description: Scopri tutto su ottimizzazione delle prestazioni e passaggi da intraprendere per rivedere le prestazioni dell’implementazione di Adobe Commerce.
exl-id: 506ef2cc-c6fd-4401-afa5-a71e7b9871e6
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Ottimizzazione delle prestazioni

Le prestazioni sono un argomento importante. Quando gli utenti rilevano un sito lento o che non risponde, la conversione viene influenzata. Per ottimizzare le prestazioni dell’implementazione dell’infrastruttura cloud di Adobe Commerce, consigliamo di seguire questi passaggi:

- Valutare il problema
- Misurare le prestazioni
- Identificare parte del sistema critica per il miglioramento delle prestazioni
- Modifica parte del sistema per rimuovere il collo di bottiglia
- Misura le prestazioni dopo la modifica
- Se preferisci, adottalo o ripristinalo

## Problemi tipici di prestazioni

L’impatto di un’esperienza lenta è solitamente definito da due indicatori e ogni fattore può essere causato da tonnellate di motivi.

L&#39;High Time-to-first-byte (TTFB) è solitamente considerato un indicatore che definisce la velocità di risposta del server. Il tempo proviene non solo dall’esecuzione del codice sorgente per la gestione della richiesta, ma può anche essere influenzato dai seguenti fattori:

- Ricerca DNS
- Query lente dal livello DB
- Tempo CPU da ogni livello applicazione
- Limitazione di memoria
- L&#39;attesa I/O può influire sulla lettura e scrittura dei file e sul servizio di connessione tramite socket
- Impostazioni software (nginx, PHP, MySQL, Redis, Varnish)
- Larghezza di banda di rete
- Memorizzazione in cache non valida
- Codice non valido
- Approccio di integrazione errato
- Dipendenza da una risposta lenta del servizio di terze parti
- Architettura senza scalabilità

Le risorse a caricamento lento sono solitamente considerate come un indicatore che definisce la risorsa statica (CSS, JavaScript, immagini, video, risposta di chiamata Ajax di terze parti).

Adobe Commerce è scalabile con la tua azienda grazie alle sue funzionalità:

![Diagramma che mostra le funzionalità scalabili di Adobe Commerce](../../../assets/playbooks/scalable-capabilities.svg)

Ci sono anche fattori chiave che guidano la scala nel commercio, che influiscono anche sulle prestazioni complessive.

- Catalogo di prodotti complesso e di grandi dimensioni
- Numero elevato di amministratori
- Storefront globali
- Traffico ad alta variabile
- Espansione dei punti di contatto
- Transazioni di volumi elevati

Per architetture su più livelli e memorizzabili in cache create per la scalabilità, puoi utilizzare questo grafico come riferimento.

![Diagramma che mostra come utilizzare l’API GraphQL di Adobe Commerce in un’architettura memorizzabile in cache](../../../assets/playbooks/cacheable-architecture.svg)
