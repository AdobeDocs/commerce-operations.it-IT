---
title: Coupled Storefront Architecture
description: Scopri cosa significa una vetrina accoppiata nel contesto delle architetture headless Adobe Commerce.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---


# Architettura della vetrina Adobe Commerce (legacy) abbinata

L’attuale opzione di distribuzione predefinita per la maggior parte dei clienti commerciali include:

- 100% feature support across B2B &amp; B2C
- Mature reference theme (Luma) that can be quickly deployed/customized
- Mature SI partner implementation expertise
- Completamente compatibile con le funzionalità di e-commerce come Page Builder o Staging e Preview
- Broad compatibility with extensions in Adobe Commerce Marketplace

![Diagramma che mostra un’architettura della vetrina di Adobe Commerce associata](../../../assets/playbooks/coupled-storefront-architecture.svg)

## Cons of legacy storefront

- **Non headless** - Tutte le parti dell&#39;applicazione Commerce di Adobe monolitico. No separation of business logic and processes between the frontend and the backend.

- **Not PWA**—Although theme is responsive, site performance lags far behind best-in-class PWA.

- **Architettura front-end (componenti dell’interfaccia utente Adobe Commerce)**: specialisti di Adobe Commerce/PHP per sviluppare la vetrina legacy.

Prima di passare alle opzioni headless, iniziamo con l’architettura storefront più familiare. Se i headless vengono disaccoppiati, questa sarebbe l&#39;architettura della vetrina associata, più comunemente vista con i nostri demo Luma.

In questo punto le funzionalità di vetrina sono strettamente integrate con i servizi di e-commerce di base, non separate dal livello API GraphQL. Quindi, c&#39;è molta logica di business legata a quel tema. Questo approccio non è headless e non è PWA.

This is currently the most common option merchants use because it has 100% feature support with both B2B and B2C Commerce capabilities. The community is familiar with it, there is a mature ecosystem of expertise around it, and it has broad compatibility with Adobe Commerce Marketplace extensions.

Tuttavia, mancano i benefici di cui abbiamo parlato prima. Without separation of layers, there are many dependencies and potential points of failure when changes are made. It’s not as performant as a well-implemented PWA and if a merchant doesn’t have expertise in Adobe Commerce or PHP development, they will have to go find those resources.
