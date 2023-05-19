---
title: Microservizi Adobe Commerce
description: Essere in grado di distinguere tra headless e microservizi come si tratta di Adobe Commerce.
exl-id: 078e0e8e-7acc-4913-8b78-585a950f3f5e
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Headless e microservizi

È importante non confondere headless con i microservizi. Spesso sentiamo conversazioni su microservizi nella stessa frase come headless. Sono cose completamente diverse. Possono essere utilizzati insieme, ma sono concetti completamente diversi.

Architettura di microservizi è un termine utilizzato per descrivere la pratica di suddividere un&#39;applicazione in una raccolta di servizi più piccoli e liberamente accoppiati. I microservizi consentono ai singoli servizi back-end di:

- **Isolato l&#39;uno dall&#39;altro**- Ad esempio, il servizio di determinazione prezzi non ha alcuna dipendenza dal servizio catalogo.

- **Implementato su carta**- I clienti implementano solo le parti dell&#39;applicazione necessarie.

- **Scalabilità indipendente**- Le risorse possono essere assegnate a servizi ad alta richiesta, ad esempio la ricerca di scorte.

- **Sviluppato autonomamente**- Può essere sviluppato e distribuito indipendentemente l&#39;uno dall&#39;altro.

I microservizi non hanno nulla a che fare con la rimozione della testa dalla pila commerciale o dalle API. Quando pensiamo a quei servizi di e-commerce nel codice principale che si trovano nel back office di Adobe Commerce, si tratta di isolare tali servizi l’uno dall’altro. Un&#39;architettura di microservizi frantuma tutti quei servizi come il prezzo, il catalogo, e l&#39;inventario, isolandosi l&#39;uno dall&#39;altro.

I microservizi possono essere scalati in modo indipendente e sviluppati autonomamente. I microservizi sono simili a un processo di sviluppo SaaS multi-tenant. Molti dei moderni prodotti SaaS multi-tenant sono sviluppati utilizzando un approccio multi-servizio. Anche i prodotti SaaS di Adobe, come Order Management, il nuovo strumento di Product Recommendations basato sull’intelligenza artificiale e altri componenti SaaS di Adobe Commerce sono in fase di sviluppo utilizzando un approccio microservizi. Per essere chiari, Adobe Commerce 2.4.x non è un’architettura di microservizi, ma un’architettura headless.
