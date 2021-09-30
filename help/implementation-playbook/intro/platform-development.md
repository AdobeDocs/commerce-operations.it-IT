---
title: Principles of Platform Development
description: Comprendere i principi fondamentali di sviluppo delle piattaforme quando si lavora con Adobe Commerce.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---


# Principles of platform development

In questo playbook approfondiamo alcuni dei principali standard di sviluppo del Commercio Adobe, tra cui:

- Functional and technical scoping in line with the development process
- Development best practices aligning with the MVC architecture
- Considerazioni architettoniche, tra cui GRA
- Standard di sicurezza contro script e sfruttamento
- Extension development best practices
- Integrazioni API web con REST, SOAP e GraphQL
- Performance improvements for coding and infrastructure
- Strumenti, strategie e metodologie di test

Anche se alcuni implementatori di soluzioni possono avere le proprie preferenze quando si tratta di metodologie, processi e strumenti utilizzati in un progetto di implementazione, questo playbook si concentra su best practice e metodologie generalmente accettate che possono essere condivise nella maggior parte delle implementazioni.

Like any large IT project, Adobe Commerce is built on coding standards that leverage best practices and standardizations of the underlying technologies (for example, PHP/Zend,Symfony, JavaScript, jQuery, and HTML), as well as standards that have been established within the Adobe Commerce Coding Standard. Following these standards is an absolute must to eliminate bugs and improve the quality and maintainability of custom-built code.

## Adobe Commerce on cloud infrastructure

Adobe Commerce on cloud Infrastructure è una piattaforma di hosting gestita e automatizzata per il software Adobe Commerce. Adobe Commerce on cloud infrastructure comes with a variety of additional features that sets it apart from on-premises Adobe Commerce and Magento Open Source implementations:

![Informazioni sui componenti di Adobe Commerce](../../assets/playbooks/commerce-cloud.svg)

Adobe Commerce sull&#39;infrastruttura cloud fornisce un&#39;infrastruttura preconfigurata che include tecnologie PHP, MySQL, Redis, RabbitMQ e Elasticsearch; un flusso di lavoro basato su Git con operazioni automatiche di compilazione e implementazione per uno sviluppo rapido ed efficiente e la distribuzione continua ogni volta che le modifiche al codice temporale vengono inviate in un ambiente Platform as a Service (PaaS); file e strumenti di configurazione dell&#39;ambiente altamente personalizzabili; e l&#39;hosting AWS che offre un ambiente scalabile e sicuro per le vendite online e il retail.

![Informazioni sui componenti di Adobe Commerce](../../assets/playbooks/cloud-tech-stack.svg)
