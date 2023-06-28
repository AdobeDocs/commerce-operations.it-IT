---
title: Architettura di vetrina abbinata
description: Scopri cosa significa una vetrina abbinata nel contesto delle architetture Adobe Commerce headless.
exl-id: 978e6853-4fbe-45b8-8e46-f491c6724fc6
feature: Integration
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# Architettura di vetrina Adobe Commerce associata (legacy)

L’attuale opzione di distribuzione predefinita per la maggior parte dei clienti commerciali include:

- Supporto di funzioni al 100% in B2B e B2C
- Tema di riferimento maturo (Luma) che può essere rapidamente distribuito/personalizzato
- Competenze maturate nell&#39;implementazione dei partner SI
- Completamente compatibile con funzionalità commerce quali Page Builder o Staging e anteprima
- Ampia compatibilità con le estensioni in Adobe Commerce Marketplace

![Diagramma che mostra un’architettura abbinata per la vetrina Adobe Commerce](../../../assets/playbooks/coupled-storefront-architecture.svg)

## Contro della vetrina legacy

- **Non headless**- Parte integrante dell&#39;applicazione Adobe Commerce monolitica. Nessuna separazione di logica e processi di business tra front-end e back-end.

- **Non PWA**- Anche se il tema è reattivo, le prestazioni del sito sono nettamente inferiori a quelle dei migliori PWA della categoria.

- **Architettura front-end (componenti dell’interfaccia utente di Adobe Commerce)**: specialisti Adobe Commerce/PHP per sviluppare nuove soluzioni basate su una vetrina precedente.

Prima di passare alle opzioni headless, iniziamo con l’architettura più familiare della vetrina. Se headless è scollegato, questa sarebbe l’architettura della vetrina abbinata, più comunemente vista con le nostre demo Luma.

Qui le funzionalità della vetrina sono strettamente integrate con i servizi commerce di base, non separate da quel livello API di GraphQL. Quindi, c&#39;è molta logica di business unita a questo tema. Questo approccio non è headless, e non è PWA.

Questa è attualmente l’opzione più comune utilizzata dai commercianti perché dispone di supporto del 100% delle funzioni di e-commerce B2B e B2C. La community lo conosce, è circondata da un ecosistema maturo di competenze ed è ampiamente compatibile con le estensioni di Adobe Commerce Marketplace.

Mancano tuttavia i vantaggi di cui abbiamo parlato prima. Senza la separazione dei livelli, quando vengono apportate modifiche vi sono molte dipendenze e potenziali punti di errore. Non è performante come un PWA ben implementato e se un commerciante non ha esperienza nello sviluppo di Adobe Commerce o PHP, dovrà trovare quelle risorse.
