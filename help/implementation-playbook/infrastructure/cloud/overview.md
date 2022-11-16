---
title: Panoramica dell'infrastruttura cloud
description: Informazioni su Adobe Commerce sull’infrastruttura cloud.
exl-id: 94cf1505-0853-4e01-ba55-befc1117fbdb
source-git-commit: 639dca9ee715f2f9ca7272d3b951d3315a85346c
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# Panoramica

Adobe Commerce offre una delle opzioni di hosting gestito più popolari per Adobe Commerce su AWS. Adobe Commerce sull&#39;infrastruttura cloud è una piattaforma di hosting automatizzata completamente gestita per il software Adobe Commerce.

Adobe Commerce su infrastruttura cloud è un’offerta Platform-as-a-service (PaaS) che consente la rapida implementazione di vetrine web completamente personalizzabili, sicure e scalabili, combinate con un’infrastruttura di hosting e servizi gestiti leader. Offre due piani con diverse infrastrutture. Adobe Commerce Starter è ideale per negozi più piccoli con meno complessità e cataloghi più piccoli. Adobe Commerce Pro è progettato per negozi di grandi dimensioni con maggiore complessità, cataloghi di prodotti più grandi o con un picco di traffico. Adobe Commerce determinerà l’architettura appropriata con l’input dei partner.

Adobe Commerce è pronta per il cloud con un&#39;infrastruttura di hosting multi-cloud completamente ridondante che fornisce prestazioni ottimizzate, resilienza e scalabilità elastica. È possibile eseguire in modo efficiente la piattaforma di e-commerce sulla rete CDN (Content Delivery Network) di Flast e, grazie a New Relic per il monitoraggio e la gestione, è possibile mantenere l&#39;ambiente del negozio senza intoppi.

Adobe Commerce offre tutti i vantaggi del cloud computing moderno che sono più comunemente associati alle soluzioni SaaS: scalabilità elastica, elevata resilienza e disponibilità, conformità PCI, disponibilità globale e patch automatizzate, mantenendo al tempo stesso la flessibilità nella personalizzazione del software richiesta dai nostri commercianti.

![Diagramma che mostra gli elementi architettonici di Adobe Commerce sull’infrastruttura cloud](../../../assets/playbooks/adobe-commerce-cloud-infrastructure.svg)

## Vantaggi

Altri vantaggi di Adobe Commerce includono:

- **Ottimizzato per Adobe Commerce**. Gli script di build e la configurazione del servizio sviluppati da Adobe Commerce garantiscono che ogni istanza sia sintonizzata e configurata correttamente per prestazioni di merchant ottimali.

- **Versioni coerenti e sicure**. Tutte le implementazioni di codice sono basate su Git per coerenza e ripetibilità, con ambienti di produzione di sola lettura per una sicurezza maggiore.

- **Flessibilità per i partner**. Un’API REST completa e un’interfaccia a riga di comando scriptable assicurano la facilità di integrazione con i sistemi esterni e la compatibilità con i flussi di lavoro esistenti per la gestione del codice.

- **Strumenti di installazione flessibili**. Esegui rapidamente il spin up, l’unione, il clone e l’eliminazione di ambienti illimitati a piacimento per attività di sviluppo, test QA o diagnosi di problemi di produzione.

- **Distribuzione continua del cloud**. Passa direttamente dallo sviluppo all’UAT alla produzione, in modo continuo tra i rami di codice e i team di sviluppo.

## Servizi di terzi

Diamo anche un’occhiata al software che fa sì che i vantaggi di Adobe Commerce diventino realtà.

![Diagramma che mostra lo stack di tecnologie per l’infrastruttura cloud di Adobe Commerce](../../../assets/playbooks/cloud-tech-stack.svg)

- CDN: Man mano che i clienti accedono al tuo sito e ai tuoi archivi, le richieste hanno raggiunto un notevole successo per caricare più rapidamente le pagine memorizzate nella cache. Flast WAF fornisce anche il servizio di protezione DDoS.

- Nuova Relic offre una visione completa delle applicazioni e dell&#39;ambiente operativo. Consente di combinare le metriche chiave delle applicazioni per dispositivi mobili e browser con servizi di supporto, archivi di dati e host per ottimizzare le prestazioni in modo olistico e garantire il successo di ogni iniziativa.

- Il Compositore gestisce le dipendenze e gli aggiornamenti in Adobe Commerce e fornisce contesto sui pacchetti inclusi, sulle operazioni dei pacchetti e sul modo in cui si integrano.

- Git è il tuo codice negli archivi. Consente il branching locale, aree di staging convenienti e flussi di lavoro multipli con la creazione e l&#39;implementazione automatica per uno sviluppo rapido ed efficiente e l&#39;implementazione continua.

- Platform-as-a-Service (PaaS) fornisce un&#39;infrastruttura preconfigurata che include PHP, MySQL, Redis, [!DNL RabbitMQ], e le tecnologie di Elasticsearch.

- L’hosting cloud di AWS o Azure potenzia l’infrastruttura sottostante (IaaS, Infrastructure-as-a-Service), che offre un ambiente scalabile e sicuro per le vendite online e il retail.
