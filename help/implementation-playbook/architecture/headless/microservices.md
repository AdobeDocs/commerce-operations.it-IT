---
title: Microservizi Adobe Commerce
description: Essere in grado di distinguere tra headless e microservizi per quanto riguarda Adobe Commerce.
exl-id: 078e0e8e-7acc-4913-8b78-585a950f3f5e
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Senza testa e microservizi

E&#39; importante non confondere testa senza testa con microservizi. Molte volte, sentiamo conversazioni sui microservizi nella stessa frase come senza testa. Sono cose completamente diverse. Possono essere utilizzati insieme, ma sono concetti completamente diversi.

Un&#39;architettura di microservizi è un termine utilizzato per descrivere la pratica di suddividere un&#39;applicazione in una raccolta di servizi più piccoli e liberamente accoppiati. I microservizi consentono ai singoli servizi di back-end di essere:

- **Isolati l&#39;uno dall&#39;altro**- Ad esempio, il servizio di determinazione prezzi non ha alcuna dipendenza dal servizio catalogo.

- **Distribuito a la carte**- I clienti distribuiscono solo le parti dell&#39;applicazione di cui hanno bisogno.

- **Scalabilità indipendente**- Le risorse possono essere assegnate a servizi ad alta domanda, ad esempio alla ricerca di inventario.

- **Sviluppato autonomamente**- Può essere sviluppato e distribuito indipendentemente l&#39;uno dall&#39;altro.

I microservizi non hanno nulla a che fare con l’eliminazione dell’intestazione dello stack di e-commerce o delle API. Quando pensiamo ai servizi commerce nel codice core che si trovano nel back office di Adobe Commerce, si tratta di isolare questi servizi l’uno dall’altro. Quindi, un&#39;architettura dei microservizi sta liberamente disgregando tutti quei servizi come i servizi di prezzo, il servizio di catalogo e il servizio di inventario, e sta rendendo ognuno isolato dall&#39;altro.

I microservizi possono essere ridimensionati in modo indipendente e sviluppati autonomamente. I microservizi sono simili a un processo di sviluppo SaaS multi-tenant. Molti prodotti SaaS multi-tenant moderni sono sviluppati utilizzando un approccio multi-servizio. Anche i prodotti SaaS di Adobe, come Order Management, il nuovo strumento di Recommendations prodotto basato sull’intelligenza artificiale e altri componenti SaaS di Adobe Commerce, vengono sviluppati utilizzando un approccio basato sui microservizi. Per essere chiari, Adobe Commerce 2.4.x non è un&#39;architettura di microservizi, ma piuttosto un&#39;architettura headless.
