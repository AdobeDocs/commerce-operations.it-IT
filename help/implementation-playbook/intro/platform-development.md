---
title: Principi di sviluppo della piattaforma
description: Comprendi i principi fondamentali di sviluppo delle piattaforme quando lavori con Adobe Commerce.
exl-id: 3d822a8c-0e81-4a80-a820-46cf2702e0bf
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# Principi di sviluppo delle piattaforme

In questo playbook, approfondiamo alcuni dei principali standard di sviluppo per Adobe Commerce, tra cui:

- Valutazione funzionale e tecnica in linea con il processo di sviluppo
- Best practice di sviluppo in linea con l’architettura MVC
- Considerazioni di architettura, compreso il GRA
- Standard di sicurezza contro scripting e exploit
- Best practice per lo sviluppo di estensioni
- Integrazioni API web con REST, SOAP e GraphQL
- Miglioramenti delle prestazioni per la codifica e l&#39;infrastruttura
- Strumenti di test, strategie e metodologie

Anche se alcuni implementatori di soluzioni possono avere le proprie preferenze per quanto riguarda le metodologie, i processi e gli strumenti utilizzati in un progetto di implementazione, questo playbook si concentra sulle best practice e le metodologie generalmente accettate che possono essere condivise nella maggior parte delle implementazioni.

Come qualsiasi progetto IT di grandi dimensioni, Adobe Commerce è basato su standard di codifica che sfruttano le best practice e le standardizzazioni delle tecnologie sottostanti (ad esempio, PHP/Zend, Symfony, JavaScript, jQuery e HTML), nonché sugli standard stabiliti all’interno di Adobe Commerce Coding Standard. Il rispetto di questi standard è fondamentale per eliminare i bug e migliorare la qualità e la gestibilità del codice personalizzato.

## Adobe Commerce sull’infrastruttura cloud

Adobe Commerce on cloud infrastructure è una piattaforma di hosting gestita e automatizzata per il software Adobe Commerce. Adobe Commerce on cloud infrastructure viene fornito con una varietà di funzioni aggiuntive che lo distinguono dalle implementazioni on-premise di Adobe Commerce e Magento Open Source:

![Infografiche dei componenti di Adobe Commerce](../../assets/playbooks/commerce-cloud.svg)

Adobe Commerce sull’infrastruttura cloud fornisce un’infrastruttura prefornita che include PHP, MySQL, Redis, [!DNL RabbitMQ], e tecnologie Elasticsearch; un flusso di lavoro basato su Git con operazioni automatiche di creazione e distribuzione per uno sviluppo rapido efficiente e una distribuzione continua ogni volta che le modifiche al codice vengono inviate in un ambiente Platform as a Service (PaaS); file e strumenti di configurazione dell’ambiente altamente personalizzabili; e hosting AWS che offre un ambiente scalabile e sicuro per le vendite online e la vendita al dettaglio.

![Infografiche dei componenti di Adobe Commerce](../../assets/playbooks/cloud-tech-stack.svg)
