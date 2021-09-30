---
title: Panoramica dell'infrastruttura cloud
description: Informazioni su Adobe Commerce sull’infrastruttura cloud.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '536'
ht-degree: 0%

---


# Overview

One of the most popular managed-hosting options for Adobe Commerce on AWS is offered by Adobe Commerce itself. Adobe Commerce on cloud Infrastructure è una piattaforma di hosting automatizzata completamente gestita per il software Adobe Commerce.

Adobe Commerce on cloud infrastructure is a platform-as-a-service (PaaS) offering that enables rapid deployment of fully customizable, secure, and scalable web storefronts combined with a leading hosting and managed services infrastructure. It offers two plans with different infrastructures. Adobe Commerce Starter is best suited for smaller stores with less complexity and smaller catalogs. Adobe Commerce Pro è progettato per negozi di grandi dimensioni con maggiore complessità, cataloghi di prodotti più grandi o con un picco di traffico. Adobe Commerce determinerà l’architettura appropriata con il contributo dei partner.

Adobe Commerce is cloud-ready with a fully redundant multi-cloud hosting infrastructure that provides optimized performance, resilience, and elastic scalability. È possibile eseguire in modo efficiente la piattaforma di e-commerce sulla rete CDN (Content Delivery Network) di Flast e, grazie a New Relic per il monitoraggio e la gestione, è possibile mantenere l&#39;ambiente del negozio senza intoppi.

Adobe Commerce offre tutti i vantaggi del cloud computing moderno che sono più comunemente associati alle soluzioni SaaS: scalabilità elastica, elevata resilienza e disponibilità, conformità PCI, disponibilità globale e patch automatizzate, mantenendo al tempo stesso la flessibilità nella personalizzazione del software richiesta dai nostri commercianti.

![Diagramma che mostra gli elementi architettonici di Adobe Commerce sull’infrastruttura cloud](../../../assets/playbooks/adobe-commerce-cloud-infrastructure.svg)

## Vantaggi

Altri vantaggi del commercio Adobe includono:

- **Ottimizzato per Adobe Commerce**. Gli script di build e la configurazione del servizio sviluppati da Adobe Commerce garantiscono la corretta sintonizzazione e configurazione di ogni istanza per ottenere prestazioni di merchant ottimali.

- **Consistent, secure releases**. Tutte le implementazioni di codice sono basate su Git per coerenza e ripetibilità, con ambienti di produzione di sola lettura per una sicurezza maggiore.

- **Flessibilità per i partner**. Un’API REST completa e un’interfaccia a riga di comando scriptable assicurano la facilità di integrazione con i sistemi esterni e la compatibilità con i flussi di lavoro esistenti per la gestione del codice.

- **Flexible deployment toolset**. Rapidly spin up, merge, clone, and tear down unlimited environments at will for development tasks, QA testing, or production-issue diagnosis.

- **Distribuzione continua del cloud**. Move with confidence straight from development to UAT to production, in a continuous manner across code branches and development teams.

## Third-party services

Let’s also take a look at the software that makes Adobe Commerce’s benefits a reality.

![Diagramma che mostra lo stack di tecnologie Adobe Commerce su infrastrutture cloud](../../../assets/playbooks/cloud-tech-stack.svg)

- CDN: Man mano che i clienti accedono al tuo sito e ai tuoi archivi, le richieste hanno raggiunto un notevole successo per caricare più rapidamente le pagine memorizzate nella cache. Flast WAF fornisce anche il servizio di protezione DDoS.

- Nuova Relic offre una visione completa delle applicazioni e dell&#39;ambiente operativo. It allows you to combine key metrics from mobile and browser applications with supporting services, data stores, and hosts so you can optimize performance holistically and ensure the success of every initiative.

- Il Compositore gestisce le dipendenze e gli aggiornamenti in Adobe Commerce e fornisce il contesto dei pacchetti inclusi, di cosa fanno i pacchetti e di come si integrano.

- Git è il tuo codice negli archivi. Consente il branching locale, aree di staging convenienti e flussi di lavoro multipli con la creazione e l&#39;implementazione automatica per uno sviluppo rapido ed efficiente e l&#39;implementazione continua.

- Platform-as-a-Service (PaaS) fornisce un&#39;infrastruttura preconfigurata che include tecnologie PHP, MySQL, Redis, RabbitMQ e Elasticsearch.

- L’hosting cloud di AWS o Azure potenzia l’infrastruttura sottostante (IaaS, Infrastructure-as-a-Service), che offre un ambiente scalabile e sicuro per le vendite online e il retail.
