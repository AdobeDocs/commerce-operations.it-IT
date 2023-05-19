---
title: Distribuire Esperienze Su Larga Scala
description: Scopri come distribuire esperienze su larga scala con Adobe Commerce e Adobe Experience Manager.
exl-id: e3166c46-fc9d-4ff4-a3a9-2cd740a95e9b
debug: true
source-git-commit: 442bb3f2c448de2ed70a3033d399025cc39e8744
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---

# Distribuisci esperienze su larga scala con Adobe Commerce, Commerce Integration Framework e Adobe Experience Manager

Un modello di integrazione consigliato tra AEM e Adobe Commerce che utilizza CIF come connettore è che l’AEM possieda il livello di presentazione (il &quot;vetro&quot;) e Adobe Commerce fornisca al backend di e-commerce la potenza di un back-end &quot;headless&quot;. Questo approccio di integrazione sfrutta i punti di forza di ogni applicazione: le funzionalità di authoring, personalizzazione e omnicanale delle operazioni AEM e e-commerce di Adobe Commerce.

In un ambiente AEM/CIF/Adobe Commerce, i visitatori del sito di e-commerce arriveranno inizialmente all’AEM. AEM controllerà se la pagina richiesta è disponibile nella cache del dispatcher. Se la pagina esiste, la pagina memorizzata in cache verrà trasmessa al visitatore e non è richiesta alcuna ulteriore elaborazione. Se il dispatcher non contiene la pagina richiesta o è scaduta, richiede all’editore dell’AEM di compilare la pagina; se necessario, l’editore chiama Adobe Commerce per i dati di e-commerce per generare la pagina. La pagina generata viene quindi passata al dispatcher per essere trasmessa al visitatore e viene memorizzata nella cache, impedendo la necessità di caricare ulteriormente sui server in occasione di successive richieste di altri visitatori alla stessa pagina.

![Diagramma di panoramica dell’architettura di Adobe Experience Manager e Adobe Commerce](../assets/commerce-at-scale/overview.png)

Nel modello AEM/CIF/Adobe Commerce è possibile utilizzare una combinazione di rendering lato server e rendering lato client: rendering lato server per fornire contenuto statico e rendering lato client per fornire contenuti dinamici personali o in continua evoluzione chiamando direttamente Adobe Commerce per componenti specifici dal browser dell’utente.

Un esempio dei diversi componenti di una pagina di dettagli del prodotto in una vetrina di esempio di e-commerce AEM è visibile nell’esempio seguente:

![Diagramma di panoramica dell’architettura di Adobe Experience Manager e Adobe Commerce](../assets/commerce-at-scale/product-details-page.svg)

## Rendering lato server

È improbabile che le pagine e-commerce, come le pagine di dettaglio del prodotto (PDP) e le pagine di elenco dei prodotti (PLP), vengano modificate frequentemente e sono idonee per essere completamente memorizzate nella cache dopo il rendering lato server utilizzando i componenti core CIF dell’AEM. Le pagine devono essere sottoposte a rendering nell’editore AEM utilizzando i modelli generici creati nell’AEM. Questi componenti ottengono i dati da Adobe Commerce tramite API GraphQL. Queste pagine vengono create in modo dinamico, sottoposte a rendering sul server, memorizzate nella cache del dispatcher AEM e quindi distribuite al browser. Esempi di ciò sono mostrati nelle caselle viola nell’esempio precedente.

## Rendering lato client

Se vengono visualizzati attributi più dinamici, ad esempio i livelli/disponibilità delle scorte o il prezzo, nelle pagine dei dettagli del prodotto (PDP), è possibile utilizzare i componenti lato client. Anche se la pagina del modello può essere generata e memorizzata nella cache di Dispatcher utilizzando l’approccio di rendering lato server descritto sopra, all’interno della pagina statica stessa possono essere presenti componenti web lato client dinamici. Questi componenti dinamici possono recuperare i dati direttamente nel browser del client da Adobe Commerce tramite API GraphQL per verificare, ad esempio, il prezzo corrente o il livello delle scorte in tempo reale sul PDP. In questo modo, al caricamento della pagina, viene sempre recuperato il contenuto che in genere è importante visualizzare in tempo reale. Esempi di ciò sono riportati nelle caselle rosse dell&#39;esempio precedente.

Durante il processo di pagamento è inoltre possibile utilizzare una combinazione di modelli AEM e rendering lato client: componenti del carrello lato client eseguono il rendering del carrello, del modulo di pagamento e dell’integrazione con il fornitore di servizi di pagamento. Questo approccio ibrido può essere utilizzato anche per le funzionalità di gestione degli account di Adobe Commerce, come la creazione di un account, l’accesso all’account e la password dimenticata.
