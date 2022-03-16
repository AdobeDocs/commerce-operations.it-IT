---
title: Architettura di Storefront accoppiata
description: Scopri cosa significa una vetrina accoppiata nel contesto delle architetture Adobe Commerce headless.
exl-id: 978e6853-4fbe-45b8-8e46-f491c6724fc6
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# Architettura della vetrina Adobe Commerce abbinata (legacy)

L’attuale opzione di distribuzione predefinita per la maggior parte dei clienti commerciali include:

- Supporto del 100% delle funzioni in B2B e B2C
- Tema di riferimento maturo (Luma) che può essere rapidamente implementato/personalizzato
- Competenze tecniche per l&#39;implementazione dei partner SI
- Completamente compatibile con le funzionalità di e-commerce come Page Builder o Staging e Preview
- Ampia compatibilità con le estensioni in Adobe Commerce Marketplace

![Diagramma che mostra un’architettura Adobe Commerce per vetrine accoppiata](../../../assets/playbooks/coupled-storefront-architecture.svg)

## Contenuti della vetrina legacy

- **Senza testa**- Tutte le parti dell&#39;applicazione monolitica Adobe Commerce. Nessuna separazione tra logica di business e processi tra front-end e backend.

- **Not PWA**- Anche se il tema è reattivo, le prestazioni del sito sono molto lente rispetto a PWA all’avanguardia.

- **Architettura front-end (componenti dell’interfaccia utente di Adobe Commerce)**- Specialisti Adobe Commerce/PHP per sviluppare la vetrina legacy.

Prima di passare alle opzioni headless, iniziamo con l’architettura storefront più familiare. Se i headless vengono disaccoppiati, questa sarebbe l&#39;architettura della vetrina associata, più comunemente vista con i nostri demo Luma.

In questo punto le funzionalità di vetrina sono strettamente integrate con i servizi di e-commerce di base, non separate dal livello API GraphQL. Quindi, c&#39;è molta logica di business legata a quel tema. Questo approccio non è headless e non è PWA.

Questa è attualmente l’opzione più comune utilizzata dai commercianti perché dispone del supporto del 100% delle funzioni sia con le funzionalità B2B che con le funzionalità Commerce B2C. La community lo conosce bene, è circondata da un ecosistema maturo di competenze ed è ampiamente compatibile con le estensioni di Adobe Commerce Marketplace.

Tuttavia, mancano i benefici di cui abbiamo parlato prima. Senza separazione dei livelli, ci sono molte dipendenze e potenziali punti di errore quando vengono apportate modifiche. Non è così performante come un PWA ben implementato e se un commerciante non ha esperienza nello sviluppo di Adobe Commerce o PHP, dovrà andare a trovare queste risorse.
