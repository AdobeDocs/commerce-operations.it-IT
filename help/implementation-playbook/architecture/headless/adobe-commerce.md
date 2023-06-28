---
title: Architettura Adobe Commerce headless
description: Scopri cosa rende unico l’approccio all’architettura headless di Adobe Commerce.
exl-id: eac9d5b1-4917-4d2a-a8af-7f85c825fa0d
feature: Integration
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 0%

---

# Architettura Adobe Commerce headless

Il vantaggio dell&#39;architettura di Adobe Commerce è che non si tratta di una proposta &quot;tutto o niente&quot; e un commerciante può trovare la giusta combinazione di soluzioni per la propria azienda. Possono creare un PWA basato su PWA Studi per la loro esperienza del sito principale oppure utilizzare Adobe Experience Manager come livello in percorsi di clienti complessi, creando al contempo un front-end personalizzato per sperimentare nuovi punti di contatto. Nessun’altra piattaforma è in grado di eguagliare i vantaggi di time-to-market e la flessibilità offerta da Adobe Commerce con la sua architettura headless.

![Diagramma che mostra un’architettura headless della vetrina Adobe Commerce](../../../assets/playbooks/headless-storefront-architecture.svg)

Ogni approccio non si esclude a vicenda. I clienti possono creare il proprio front-end (head), utilizzare PWA Studi per esperienze web/mobili e/o utilizzare Adobe Experience Manager per il vetro (in una distribuzione completa o ibrida).

Adobe Commerce ha sempre consentito implementazioni headless con API REST. Anche se REST è potente, soprattutto per l’elaborazione in blocco, quando si tratta di headless, le API di GraphQL consentono uno sviluppo più veloce attraverso un’esperienza di sviluppo intuitiva, una maggiore flessibilità consentendo modifiche che non influiscono sulle API esistenti e prestazioni migliori riducendo la quantità di dati recuperati solo a ciò che è esattamente necessario.

GraphQL è uno standard di settore per le API performanti, utilizzato da molte delle principali piattaforme di e-commerce. È un aspetto positivo, perché offre una soluzione affidabile e ampia esperienza sul mercato.

Anche se Adobe Commerce ha una vetrina abbinata come opzione, non è affatto necessario che un commerciante utilizzi quella vetrina legacy di Adobe Commerce. Un commerciante può sfruttare i migliori servizi di e-commerce di Adobe Commerce per gestire i processi aziendali back-end e, utilizzando le nostre API storefront, integrare la propria vetrina scollegata per promuovere l’esperienza front-end.

Ora, diamo un’occhiata alle varie opzioni headless.

## PWA Studi

La prima è un’applicazione web progressiva creata con PWA Studi. Parte di questo è reso possibile dal fatto che un PWA è una vetrina headless scollegata dal back-end commerciale. Con PWA Studi, i commercianti possono creare PWA ad alte prestazioni, affidabili e a costi contenuti al di sopra di Adobe Commerce per offrire esperienze web all’avanguardia, sia su dispositivi mobili che desktop. Con il passare del tempo, questa opzione supera la vetrina abbinata come opzione predefinita.

La maggior parte dei commercianti comprende la direzione verso cui il settore sta andando per quanto riguarda i PWA e molti potenziali bloccanti sono stati rimossi rapidamente.

Settimana dopo settimana, il numero di partner che acquisiscono competenze nel settore PWA Studi cresce e il numero di lanci di nuovi clienti è in costante aumento. L’aggiornamento più recente di PWA Studi includeva l’estensibilità, che contribuirà a realizzare progressi significativi nella compatibilità con le estensioni di Adobe Commerce Marketplace.

Molti commercianti possono sentire di non essere pronti per headless e PWA perché richiedono una forte dipendenza dagli sviluppatori. Uno degli enormi vantaggi di avere sia l’applicazione commerce che la testa sviluppata da Adobe Commerce è che consente di garantire la compatibilità tra le funzionalità di commerce.

Per rendere i PWA più accessibili e facili da gestire per i nostri esercenti, diamo agli utenti aziendali la possibilità di gestire le modifiche ai contenuti quotidiane, creare nuove pagine di destinazione e molto altro ancora utilizzando Page Builder. Queste due potenti funzionalità consentono di commercializzare rapidamente tutti i dispositivi e le esperienze.

## Adobe Experience Manager

Una potente combinazione per le tue esigenze di gestione dei contenuti e delle risorse digitali, Adobe Experience Manager consente ai commercianti di introdurre più rapidamente sul mercato esperienze personalizzate basate sui contenuti, combinando la gestione delle risorse digitali con la potenza dell’apprendimento automatico, dei contenuti basati su Adobe Sensei e della gestione dei percorsi di clienti.

Adobe Commerce più Adobe Experience Manager è una storia potente in quanto il motore di commerce consente alle aziende di abilitare il commerce attraverso le interfacce cliente che sono alimentate da Adobe Experience Manager.

## Intestazioni personalizzate

L’ultima opzione da discutere qui è la creazione di un front-end personalizzato. Questa opzione è destinata alle aziende che dispongono di competenze esistenti e a sviluppatori interni esperti in uno stack front-end specifico, come React. Se non hanno competenze nello sviluppo front-end tradizionale di Adobe Commerce, possono decidere che è più conveniente creare il proprio front-end React personalizzato.

Naturalmente, questo modello richiede solide competenze e risorse di sviluppo front-end per l’integrazione di clienti o sistemi e non si ottiene il vantaggio della compatibilità nativa con elementi come Page Builder ottenuti con PWA Studi. Ogni volta che un commerciante costruisce qualcosa di completamente personalizzato, può perdere i vantaggi del time-to-market.

I front-end personalizzati consentono inoltre innovazioni e sperimentazione. Si parla molto di AR/VR o del voice commerce, e un&#39;architettura come Adobe Commerce permette ai commercianti di esplorare queste opzioni senza influire sui loro negozi web esistenti.
