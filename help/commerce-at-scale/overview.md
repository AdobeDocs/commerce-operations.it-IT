---
title: Fornire Esperienze Su Scala
description: Scopri come distribuire esperienze su larga scala con Adobe Commerce e Adobe Experience Manager.
exl-id: e3166c46-fc9d-4ff4-a3a9-2cd740a95e9b
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# Fornire esperienze su larga scala con Adobe Commerce, Commerce Integration Framework e Adobe Experience Manager

Un pattern di integrazione consigliato tra AEM e Adobe Commerce utilizzando CIF come connettore è quello di AEM possedere il livello di presentazione (il &quot;vetro&quot;) e Commerce di Adobe per alimentare il back-end di e-commerce come backend &quot;headless&quot;. Questo approccio di integrazione sfrutta i vantaggi di ogni applicazione: le funzionalità di authoring, personalizzazione e omnicanale delle operazioni di AEM ed e-commerce di Adobe Commerce.

In un ambiente Commerce AEM/CIF/Adobe, i visitatori del sito e-commerce arriveranno inizialmente a AEM. AEM verificherà se la pagina richiesta è disponibile nella cache del dispatcher. Se la pagina esiste, verrà trasmessa al visitatore la pagina memorizzata nella cache e non è richiesta alcuna ulteriore elaborazione. Se il dispatcher non contiene la pagina richiesta o è scaduta, richiede all’editore AEM di creare la pagina, utilizzando l’editore che richiama i dati Adobe Commerce for e per generare la pagina, se necessario. La pagina creata viene quindi trasmessa al dispatcher da servire al visitatore e quindi memorizzata nella cache per evitare che sia necessario caricare ulteriormente i server sulle richieste successive alla stessa pagina da parte di altri visitatori.

![Diagramma generale dell’architettura di Adobe Experience Manager e Adobe Commerce](../assets/commerce-at-scale/overview.png)

Nel modello Commerce di AEM/CIF/Adobe è possibile utilizzare una combinazione di rendering lato server e rendering lato client: Rendering lato server per fornire contenuti statici e rendering lato client per fornire contenuti dinamici di frequente modifica o personali richiamando direttamente Adobe Commerce per componenti specifici
dal browser dell’utente.

Un esempio dei diversi componenti di una pagina di dettagli prodotto in un esempio AEM vetrina di e-commerce è visibile nell’esempio seguente:

![Diagramma generale dell’architettura di Adobe Experience Manager e Adobe Commerce](../assets/commerce-at-scale/product-details-page.svg)

## Rendering lato server

È improbabile che le pagine di e-commerce, come le pagine di dettaglio dei prodotti (PDP) e le pagine di elenco dei prodotti (PLP), possano essere modificate frequentemente e sono adatte a essere memorizzate nella cache completa dopo il rendering lato server tramite i componenti core CIF di AEM. Le pagine devono essere sottoposte a rendering nell’editore AEM utilizzando modelli generici creati in AEM. Questi componenti ottengono i dati da Adobe Commerce tramite API GraphQL. Queste pagine vengono create in modo dinamico, sottoposte a rendering sul server, memorizzate nella cache del dispatcher AEM e quindi distribuite al browser. Esempi di questo sono visualizzati nelle caselle viola dell’esempio precedente.

## Rendering lato client

Quando vengono visualizzati attributi più dinamici, ad esempio livelli di stock/disponibilità o prezzo, ad esempio nelle pagine dei dettagli prodotto (PDP), è possibile utilizzare i componenti lato client. Anche se la pagina modello può essere creata e memorizzata in cache sul dispatcher utilizzando l’approccio di rendering lato server di cui sopra, all’interno della pagina statica stessa possono essere presenti componenti web dinamici lato client. Questi componenti dinamici possono recuperare i dati direttamente nel browser del cliente da Adobe Commerce tramite API GraphQL per verificare, ad esempio, il prezzo o il livello di stock corrente in tempo reale sul PDP. In questo modo i contenuti di solito critici per essere visualizzati in tempo reale vengono sempre recuperati al caricamento della pagina. Esempi di questo sono mostrati nelle caselle rosse dell’esempio precedente.

Durante il processo di pagamento è inoltre possibile utilizzare una combinazione di modelli AEM e rendering lato client: i componenti carrello lato client eseguono il rendering del carrello, del modulo di pagamento e dell’integrazione con il provider di servizi di pagamento. Questo approccio ibrido può essere utilizzato anche per le funzionalità di gestione degli account di Adobe Commerce, ad esempio crea account, accedi all’account e password dimenticate.
