---
title: Architettura headless Adobe Commerce
description: Learn about what makes Adobe Commerce's headless architecture approach unique.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 0%

---


# Headless Adobe Commerce Architecture

The benefit of Adobe Commerce’s architecture is that it’s not an all-or-nothing proposition and a merchant can find the right mix of solutions for their business. Possono creare un PWA basato su PWA Studi per la loro esperienza di sito principale o utilizzare Adobe Experience Manager come livello in percorsi di clienti complessi, il tutto creando un front-end personalizzato per sperimentare nuovi punti di contatto. No other platform can match the time to market benefits and the flexibility that Adobe Commerce offers with its headless architecture.

![Diagramma che mostra un’architettura headless Adobe Commerce storefront](../../../assets/playbooks/headless-storefront-architecture.svg)

Ogni approccio non si escludono a vicenda. I clienti possono creare un proprio front-end (head), utilizzare PWA Studi per esperienze web/mobile e/o utilizzare Adobe Experience Manager per il vetro (in un’implementazione completa o ibrida).

Adobe Commerce ha sempre consentito distribuzioni headless con API REST. Sebbene REST sia potente, soprattutto per l’elaborazione in blocco, quando si tratta di attività headless, le API GraphQL consentono uno sviluppo più rapido grazie a un’esperienza di sviluppo intuitiva, una maggiore flessibilità consentendo modifiche che non influiscono sulle API esistenti e prestazioni migliori riducendo al minimo la quantità di dati recuperati solo per ciò che è necessario.

GraphQL è uno standard di settore per le API performanti, utilizzato da molte delle principali piattaforme di e-commerce. È una buona cosa, perché significa che è una soluzione e un&#39;esperienza comprovate sul mercato.

While Adobe Commerce does have a coupled storefront as an option, it is by no means required that a merchant use that Adobe Commerce legacy frontend. Un commerciante può sfruttare i servizi di e-commerce all’avanguardia di Adobe Commerce per gestire i processi aziendali di back-end e, utilizzando le nostre API storefront, integrare la propria vetrina disaccoppiata per guidare l’esperienza front-end.

Ora, diamo un&#39;occhiata alle varie opzioni headless.

## PWA Studi

La prima è un&#39;applicazione web progressiva creata con PWA Studi. Part of this is enabled by the fact that a PWA is a headless storefront decoupled from the commerce backend. Con PWA Studi, i commercianti possono creare PWA dalle prestazioni elevate, affidabili ed economici, oltre ad Adobe Commerce, per fornire esperienze web all’avanguardia sia su dispositivi mobili che su desktop. Con il passare del tempo, l’opzione predefinita supererà la vetrina associata.

Most merchants understand the direction that the industry is heading toward with regards to PWAs and many potential blockers are being removed rapidly.

Week over week, the number of partners building expertise in PWA Studio grows and we have an accelerating number of customer launches. L’aggiornamento più recente di PWA Studi includeva l’estensibilità che consentiva di compiere progressi significativi nella compatibilità con le estensioni di Commerce Marketplace Adobe.

Molti commercianti possono ritenere che non siano pronti per PWA e headless perché richiedono una forte dipendenza dagli sviluppatori. One of the huge benefits of having both the commerce application and the head developed by Adobe Commerce is that it helps ensure compatibility across commerce capabilities.

Per rendere i PWA più accessibili e facili da gestire per i nostri merchants, offriamo agli utenti aziendali la possibilità di gestire le modifiche giornaliere dei contenuti, creare nuove pagine di destinazione e altro ancora utilizzando Page Builder. Queste due potenti funzionalità consentono insieme di velocizzare il mercato su tutti i dispositivi e le esperienze.

## Adobe Experience Manager

A powerhouse combination for your content and digital asset management needs,Adobe Exeprience Manager helps merchants get personalized, content-led experiences into market faster, combining digital asset management with the power of machine learning, Adobe Sensei-powered content, and customer journey management.

Adobe Commerce plus Adobe Exeprience Manager is a powerful story in that the commerce engine allows businesses to enable commerce though customer interfaces that are powered by Adobe Experience Manager.

## Custom Heads

L&#39;opzione finale da discutere qui è la possibilità di costruire un fronte personalizzato. Questa opzione è destinata alle aziende che dispongono di competenze esistenti e agli sviluppatori interni qualificati in un particolare stack front-end, come React. Se non dispongono delle competenze necessarie per lo sviluppo front-end tradizionale di Adobe Commerce, possono decidere che è più conveniente creare un proprio fronte React personalizzato.

Naturally, this model requires strong customer or systems integration frontend development skills and resources, and you don’t get the benefit of native compatibility with things like Page Builder that you get with PWA Studio. Ogni volta che un commerciante costruisce qualcosa di completamente personalizzato, può perdere tempo a vantaggio del mercato.

Custom front ends also enable innovations and experimentation. Si parla molto di AR/VR o del commercio vocale, e un’architettura come quella di Adobe Commerce consente ai commercianti di esplorare queste opzioni senza influire sui loro negozi web esistenti.
