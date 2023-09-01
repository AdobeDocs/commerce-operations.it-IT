---
title: Panoramica dell’infrastruttura cloud
description: Scopri Adobe Commerce sull’infrastruttura cloud.
exl-id: 94cf1505-0853-4e01-ba55-befc1117fbdb
feature: Cloud
source-git-commit: c737a8e902c960c933e54e2521107475bb1e5a22
workflow-type: tm+mt
source-wordcount: '557'
ht-degree: 0%

---


# Panoramica

Una delle opzioni di hosting gestito più popolari per Adobe Commerce su AWS è offerta dalla stessa Adobe Commerce. Adobe Commerce su infrastruttura cloud è una piattaforma di hosting automatizzato completamente gestita per il software Adobe Commerce.

Adobe Commerce su infrastruttura cloud è un’offerta PaaS (Platform-as-a-Service) che consente la rapida implementazione di web store completamente personalizzabili, sicuri e scalabili, combinati con una delle principali infrastrutture di hosting e Managed Services. Offre due piani con infrastrutture diverse. Adobe Commerce [Starter](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#starter-projects) i piani sono più adatti per i negozi più piccoli con meno complessità e cataloghi più piccoli. Adobe Commerce [Pro](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#pro-projects) i piani sono progettati per grandi magazzini con maggiore complessità, cataloghi di prodotti più grandi o traffico che raggiunge i massimi livelli. Adobe determina l’architettura appropriata con l’input dei partner.

Adobe Commerce è predisposto per il cloud con un’infrastruttura di hosting multi-cloud completamente ridondante che offre prestazioni ottimizzate, resilienza e scalabilità elastica. È possibile eseguire in modo efficiente la piattaforma commerce sulla rete CDN (Content Delivery Network) di Fastly e con New Relic per il monitoraggio e la gestione è possibile mantenere l&#39;ambiente di store funzionante senza problemi.

Adobe Commerce offre tutti i vantaggi del cloud computing moderno che sono più comunemente associati alle soluzioni SaaS, pur mantenendo la flessibilità nella personalizzazione del software:

- Scalabilità elastica
- Elevata resilienza e disponibilità
- Conformità PCI
- Disponibilità globale e applicazione automatica di patch

![Diagramma che mostra gli elementi architettonici di Adobe Commerce sull’infrastruttura cloud](../../../assets/playbooks/adobe-commerce-cloud-infrastructure.svg)

## Vantaggi

Altri vantaggi di Adobe Commerce includono:

- **Ottimizzato per Adobe Commerce**. Gli script di build sviluppati da Adobe Commerce e la configurazione del servizio garantiscono che ogni istanza sia correttamente sintonizzata e configurata per prestazioni ottimali da parte dell’esercente.

- **Versioni coerenti e sicure**. Tutte le distribuzioni del codice sono basate su Git per coerenza e ripetibilità, con ambienti di produzione di sola lettura per una maggiore sicurezza.

- **Flessibilità per i partner**. Un’API REST completa e un’interfaccia della riga di comando scrivibile garantiscono una facile integrazione con i sistemi esterni e la compatibilità con i flussi di lavoro di gestione del codice esistenti.

- **Set di strumenti di distribuzione flessibile**. Possibilità di eseguire rapidamente lo spin up, l&#39;unione, la clonazione e l&#39;eliminazione di ambienti illimitati a proprio piacimento per attività di sviluppo, test di controllo qualità o diagnosi dei problemi di produzione.

- **Consegna continua cloud**. Passa con sicurezza direttamente dallo sviluppo a UAT e alla produzione, in modo continuo tra i rami di codice e i team di sviluppo.

## Servizi di terze parti

In questa sezione vengono riepilogati i servizi e gli strumenti chiave di terze parti per Adobe Commerce sui progetti di infrastruttura cloud. Consulta [Stack tecnologico](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/tech-stack.html) nel _Guida a Cloud_ per ulteriori dettagli.

- **Fastly CDN**: quando i clienti accedono al sito e agli store, le richieste arrivano Fastly e consentono di caricare più rapidamente le pagine memorizzate in cache. Fastly WAF fornisce anche un servizio di protezione DDoS.

- **New Relic**: fornisce una visualizzazione completa delle applicazioni e dell’ambiente operativo. New Relic consente di combinare metriche chiave da applicazioni mobili e browser con servizi di supporto, archivi dati e host, in modo da ottimizzare le prestazioni in modo olistico e garantire il successo di ogni iniziativa.

- **Compositore**: gestisce le dipendenze e gli aggiornamenti in Adobe Commerce e fornisce informazioni contestuali sui pacchetti inclusi, su cosa fanno i pacchetti e come si adattano tra loro.

- **Git**: fornisce la gestione del codice sorgente. Git consente diramazioni locali, aree di gestione temporanea convenienti e più flussi di lavoro con generazione e distribuzione automatiche per uno sviluppo rapido efficiente e una distribuzione continua.

- **Platform-as-a-Service (PaaS)**: fornisce un’infrastruttura con preprovisioning che include PHP, MySQL, Redis, [!DNL RabbitMQ]e OpenSearch o Elasticsearch.

- **Hosting cloud di AWS o Azure**: fornisce i vantaggi dell&#39;infrastruttura IaaS (Infrastructure-as-a-Service) sottostante, che offre un ambiente scalabile e sicuro per le vendite online e al dettaglio.
