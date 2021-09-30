---
title: Adobe Commerce Microservices
description: Essere in grado di differenziare tra i servizi sanitari e i microservizi in quanto si riferiscono al commercio Adobe.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---


# Senza testa e microservizi

It is important not to confuse headless with microservices. A lot of the time, we hear conversations about microservices in the same sentence as headless. They are completely different things. They can be used together, but they’re completely different concepts.

Un&#39;architettura di microservizi è un termine utilizzato per descrivere la pratica di suddividere un&#39;applicazione in una raccolta di servizi più piccoli e liberamente accoppiati. I microservizi consentono ai singoli servizi di back-end di essere:

- **Isolato l’uno dall’altro**: ad esempio, il servizio di determinazione dei prezzi non ha alcuna dipendenza dal servizio di catalogo.

- **Distribuito a la carte**: i clienti distribuiscono solo le parti dell’applicazione di cui hanno bisogno.

- **Scala in modo indipendente**: le risorse possono essere assegnate a servizi ad alta domanda, ad esempio alla ricerca di scorte.

- **Autonomously developed**—Can be developed and deployed independently of one another.

Microservices have nothing to do with chopping the head off of the commerce stack or the APIs. Quando pensiamo ai servizi commerce nel codice core che si trovano nel back office di Adobe Commerce, si tratta di isolare questi servizi l’uno dall’altro. So, a microservices architecture is loosely breaking up all of those services like the pricing services, catalog service, and inventory service, and making each one isolated from another. This ensures that they are a la cart so that you don’t need to buy and deploy all of Adobe Commerce in one go.

I microservizi possono essere ridimensionati in modo indipendente e sviluppati autonomamente. I microservizi sono simili a un processo di sviluppo SaaS multi-tenant. A lot of modern multi-tenant SaaS products are developed using a multi-service approach. Even Adobe’s own SaaS products, like Order Management, the new AI-driven Product Recommendations tool, and other SaaS components of Adobe Commerce are being developed using a microservices approach. Per essere chiari, Adobe Commerce 2.4.x non è un’architettura microservizi, ma piuttosto un’architettura headless.
