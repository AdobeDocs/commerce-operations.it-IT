---
title: Architettura Adobe Commerce headless
description: Scopri cosa rende unico l’approccio all’architettura headless di Adobe Commerce.
exl-id: eac9d5b1-4917-4d2a-a8af-7f85c825fa0d
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 0%

---

# Architettura Adobe Commerce headless

Il vantaggio dell’architettura di Adobe Commerce è che non si tratta di una proposta completa o nulla e un commerciante può trovare la giusta combinazione di soluzioni per la propria attività. Possono creare un PWA basato su PWA Studi per la loro esperienza di sito principale o utilizzare Adobe Experience Manager come livello in percorsi di clienti complessi, il tutto creando un front-end personalizzato per sperimentare nuovi punti di contatto. Nessun&#39;altra piattaforma può eguagliare i vantaggi in termini di time-to-market e la flessibilità offerta da Adobe Commerce con la sua architettura headless.

![Diagramma che mostra un’architettura Adobe Commerce storefront headless](../../../assets/playbooks/headless-storefront-architecture.svg)

Ogni approccio non si escludono a vicenda. I clienti possono creare un proprio front-end (head), utilizzare PWA Studi per esperienze web/mobile e/o utilizzare Adobe Experience Manager per il vetro (in un’implementazione completa o ibrida).

Adobe Commerce ha sempre consentito distribuzioni headless con API REST. Sebbene REST sia potente, soprattutto per l’elaborazione in blocco, quando si tratta di attività headless, le API GraphQL consentono uno sviluppo più rapido grazie a un’esperienza di sviluppo intuitiva, una maggiore flessibilità consentendo modifiche che non influiscono sulle API esistenti e prestazioni migliori riducendo al minimo la quantità di dati recuperati solo per ciò che è necessario.

GraphQL è uno standard di settore per le API performanti, utilizzato da molte delle principali piattaforme di e-commerce. È una buona cosa, perché significa che è una soluzione e un&#39;esperienza comprovate sul mercato.

Sebbene Adobe Commerce disponga di una vetrina associata come opzione, non è assolutamente necessario che un commerciante utilizzi quella precedente Adobe Commerce. Un commerciante può sfruttare i servizi di e-commerce all’avanguardia di Adobe Commerce per gestire i processi aziendali back-end e, utilizzando le API storefront, integrare la propria vetrina disaccoppiata per promuovere l’esperienza front-end.

Ora, diamo un&#39;occhiata alle varie opzioni headless.

## PWA Studi

La prima è un&#39;applicazione web progressiva creata con PWA Studi. Parte di questo è abilitata dal fatto che un PWA è una vetrina headless disaccoppiata dal back-end commerce. Con PWA Studi, i commercianti possono creare PWA ad alte prestazioni, affidabili e convenienti su Adobe Commerce per offrire esperienze web all’avanguardia, sia su dispositivi mobili che su desktop. Con il passare del tempo, l’opzione predefinita supererà la vetrina associata.

La maggior parte dei commercianti comprende la direzione verso cui l&#39;industria si sta dirigendo per quanto riguarda i PWA e molti potenziali blocchi vengono rimossi rapidamente.

Settimana dopo settimana, il numero di partner che sviluppano le proprie competenze in PWA Studi cresce e il numero di nuovi clienti è in aumento. L’aggiornamento più recente di PWA Studi includeva l’estensibilità che consentiva di compiere progressi significativi nella compatibilità con le estensioni Adobe Commerce Marketplace.

Molti commercianti possono ritenere che non siano pronti per PWA e headless perché richiedono una forte dipendenza dagli sviluppatori. Uno dei grandi vantaggi di avere sia l&#39;applicazione commerce che la testa sviluppata da Adobe Commerce è che contribuisce a garantire la compatibilità tra le funzionalità commerce.

Per rendere i PWA più accessibili e facili da gestire per i nostri merchants, offriamo agli utenti aziendali la possibilità di gestire le modifiche giornaliere dei contenuti, creare nuove pagine di destinazione e altro ancora utilizzando Page Builder. Queste due potenti funzionalità consentono insieme di velocizzare il mercato su tutti i dispositivi e le esperienze.

## Adobe Experience Manager

Una combinazione potente per le tue esigenze di gestione dei contenuti e delle risorse digitali, Adobe Experience Manager aiuta i commercianti a immettere sul mercato esperienze personalizzate basate su contenuti più rapidamente, combinando la gestione delle risorse digitali con la potenza dell’apprendimento automatico, dei contenuti basati su Adobe Sensei e della gestione dei percorsi dei clienti.

Adobe Commerce plus Adobe Experience Manager è una storia importante in quanto il motore di e-commerce consente alle aziende di abilitare l’e-commerce tramite le interfacce cliente fornite da Adobe Experience Manager.

## Intestazioni personalizzate

L&#39;opzione finale da discutere qui è la possibilità di costruire un fronte personalizzato. Questa opzione è destinata alle aziende che dispongono di competenze esistenti e agli sviluppatori interni qualificati in un particolare stack front-end, come React. Se non dispongono delle competenze necessarie per lo sviluppo front-end tradizionale di Adobe Commerce, possono decidere che è più conveniente creare un proprio fronte React personalizzato.

Naturalmente, questo modello richiede una forte integrazione dei clienti o dei sistemi e richiede competenze e risorse di sviluppo superiori a quelle dei clienti e non si ottiene il vantaggio della compatibilità nativa con elementi come Page Builder forniti con PWA Studi. Ogni volta che un commerciante costruisce qualcosa di completamente personalizzato, può perdere tempo a vantaggio del mercato.

I front-end personalizzati consentono inoltre innovazioni e sperimentazione. Si parla molto di AR/VR o del commercio vocale, e un’architettura come quella di Adobe Commerce consente ai commercianti di esplorare queste opzioni senza influire sui loro negozi web esistenti.
