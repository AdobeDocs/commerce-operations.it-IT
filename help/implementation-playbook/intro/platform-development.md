---
title: Principi di sviluppo della piattaforma
description: Comprendere i principi fondamentali di sviluppo delle piattaforme quando si lavora con Adobe Commerce.
exl-id: 3d822a8c-0e81-4a80-a820-46cf2702e0bf
source-git-commit: 6509c939c7abc5462bffbe104466b2ff9e6fadc9
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# Principi dello sviluppo delle piattaforme

In questo playbook approfondiamo alcuni dei principali standard di sviluppo Adobe Commerce, tra cui:

- Ambito funzionale e tecnico in linea con il processo di sviluppo
- Best practice di sviluppo in linea con l&#39;architettura MVC
- Considerazioni architettoniche, tra cui GRA
- Standard di sicurezza contro script e sfruttamento
- Best practice per lo sviluppo di estensioni
- Integrazioni API web con REST, SOAP e GraphQL
- Miglioramenti delle prestazioni per la codifica e l&#39;infrastruttura
- Strumenti, strategie e metodologie di test

Anche se alcuni implementatori di soluzioni possono avere le proprie preferenze quando si tratta di metodologie, processi e strumenti utilizzati in un progetto di implementazione, questo playbook si concentra su best practice e metodologie generalmente accettate che possono essere condivise nella maggior parte delle implementazioni.

Come per qualsiasi progetto IT di grandi dimensioni, Adobe Commerce si basa su standard di codifica che sfruttano le best practice e le standardizzazioni delle tecnologie sottostanti (ad esempio, PHP/Zend, Symfony, JavaScript, jQuery e HTML), nonché sugli standard stabiliti all’interno di Adobe Commerce Coding Standard. Il rispetto di questi standard è assolutamente necessario per eliminare gli errori e migliorare la qualità e la manutenibilità del codice personalizzato.

## Adobe Commerce su infrastruttura cloud

Adobe Commerce sull’infrastruttura cloud è una piattaforma di hosting gestita e automatizzata per il software Adobe Commerce. L’infrastruttura Adobe Commerce su cloud include una serie di funzioni aggiuntive che la distinguono dalle implementazioni Adobe Commerce on-premise di Magento Open Source:

![Informazioni sui componenti di Adobe Commerce](../../assets/playbooks/commerce-cloud.svg)

Adobe Commerce sull&#39;infrastruttura cloud fornisce un&#39;infrastruttura preconfigurata che include tecnologie PHP, MySQL, Redis, RabbitMQ e Elasticsearch; un flusso di lavoro basato su Git con operazioni automatiche di compilazione e implementazione per uno sviluppo rapido ed efficiente e la distribuzione continua ogni volta che le modifiche al codice temporale vengono inviate in un ambiente Platform as a Service (PaaS); file e strumenti di configurazione dell&#39;ambiente altamente personalizzabili; e l&#39;hosting AWS che offre un ambiente scalabile e sicuro per le vendite online e il retail.

![Informazioni sui componenti di Adobe Commerce](../../assets/playbooks/cloud-tech-stack.svg)
