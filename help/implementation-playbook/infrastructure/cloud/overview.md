---
title: Panoramica dell’infrastruttura cloud
description: Scopri Adobe Commerce sull’infrastruttura cloud.
exl-id: 94cf1505-0853-4e01-ba55-befc1117fbdb
feature: Cloud
source-git-commit: c737a8e902c960c933e54e2521107475bb1e5a22
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---


# Panoramica

Una delle opzioni di hosting gestito più popolari per Adobe Commerce su AWS è offerta dalla stessa Adobe Commerce. Adobe Commerce su infrastruttura cloud è una piattaforma di hosting automatizzato completamente gestita per il software Adobe Commerce.

Adobe Commerce su infrastruttura cloud è un’offerta PaaS (Platform-as-a-Service) che consente la rapida implementazione di web store completamente personalizzabili, sicuri e scalabili, combinati con una delle principali infrastrutture di hosting e Managed Services. Offre due piani con infrastrutture diverse. I piani di Adobe Commerce [Starter](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#starter-projects) sono più adatti per gli store più piccoli con meno complessità e cataloghi più piccoli. I piani di Adobe Commerce [Pro](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/cloud-architecture.html#pro-projects) sono progettati per negozi più grandi con maggiore complessità, cataloghi di prodotti più grandi o picchi di traffico. Adobe determina l’architettura appropriata con l’input dei partner.

Adobe Commerce è predisposto per il cloud con un’infrastruttura di hosting multi-cloud completamente ridondante che offre prestazioni ottimizzate, resilienza e scalabilità elastica. È possibile eseguire in modo efficiente la piattaforma commerce sulla rete CDN (Content Delivery Network) di Fastly e con New Relic per il monitoraggio e la gestione è possibile mantenere l&#39;ambiente di store funzionante senza problemi.

Adobe Commerce offre tutti i vantaggi del cloud computing moderno che sono più comunemente associati alle soluzioni SaaS, pur mantenendo la flessibilità nella personalizzazione del software:

- Scalabilità elastica
- Elevata resilienza e disponibilità
- Conformità PCI
- Disponibilità globale e applicazione automatica di patch

![Diagramma che mostra gli elementi architettonici di Adobe Commerce sull&#39;infrastruttura cloud](../../../assets/playbooks/adobe-commerce-cloud-infrastructure.svg)

## Vantaggi

Altri vantaggi di Adobe Commerce includono:

- **Ottimizzato per Adobe Commerce**. Gli script di build sviluppati da Adobe Commerce e la configurazione del servizio garantiscono che ogni istanza sia correttamente sintonizzata e configurata per prestazioni ottimali da parte dell’esercente.

- **Versioni sicure coerenti**. Tutte le distribuzioni del codice sono basate su Git per coerenza e ripetibilità, con ambienti di produzione di sola lettura per una maggiore sicurezza.

- **Flessibilità per i partner**. Un’API REST completa e un’interfaccia della riga di comando scrivibile garantiscono una facile integrazione con i sistemi esterni e la compatibilità con i flussi di lavoro di gestione del codice esistenti.

- **Strumenti di distribuzione flessibili**. Possibilità di eseguire rapidamente lo spin up, l&#39;unione, la clonazione e l&#39;eliminazione di ambienti illimitati a proprio piacimento per attività di sviluppo, test di controllo qualità o diagnosi dei problemi di produzione.

- **Consegna cloud continua**. Passa con sicurezza direttamente dallo sviluppo a UAT e alla produzione, in modo continuo tra i rami di codice e i team di sviluppo.

## Servizi di terze parti

In questa sezione vengono riepilogati i servizi e gli strumenti chiave di terze parti per Adobe Commerce sui progetti di infrastruttura cloud. Per ulteriori dettagli, consulta [Stack tecnologia](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/tech-stack.html) nella _Guida cloud_.

- **Fastly CDN**: quando i clienti accedono al sito e agli store, le richieste arrivano rapidamente e le pagine memorizzate nella cache vengono caricate più rapidamente. Fastly WAF fornisce anche un servizio di protezione DDoS.

- **New Relic**: fornisce una visualizzazione completa delle applicazioni e dell&#39;ambiente operativo. New Relic consente di combinare metriche chiave da applicazioni mobili e browser con servizi di supporto, archivi dati e host, in modo da ottimizzare le prestazioni in modo olistico e garantire il successo di ogni iniziativa.

- **Compositore**: gestisce le dipendenze e gli aggiornamenti in Adobe Commerce e fornisce informazioni contestuali sui pacchetti inclusi, sul loro funzionamento e sulla loro combinazione.

- **Git**: fornisce la gestione del codice sorgente. Git consente diramazioni locali, aree di gestione temporanea convenienti e più flussi di lavoro con generazione e distribuzione automatiche per uno sviluppo rapido efficiente e una distribuzione continua.

- **Platform-as-a-Service (PaaS)**: fornisce un&#39;infrastruttura preconfigurata che include tecnologie PHP, MySQL, Redis, [!DNL RabbitMQ] e OpenSearch o Elasticsearch.

- **AWS o l&#39;hosting cloud di Azure**: abilita l&#39;IaaS (Infrastructure-as-a-Service) sottostante, che offre un ambiente scalabile e sicuro per le vendite e la vendita online.
