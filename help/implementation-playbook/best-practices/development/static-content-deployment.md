---
title: Best practice per l’implementazione di contenuti statici
description: Scopri come evitare problemi con il contenuto statico che non viene visualizzato nella vetrina Adobe Commerce o Magenti Open Source.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 48c5666ee9b83bbf8a5c6375ec53762d918bcece
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Best practice per l’implementazione di contenuti statici

Questo articolo illustra le best practice per l’implementazione di contenuti statici (SCD) in Adobe Commerce per evitare problemi in cui il contenuto statico non sarebbe disponibile sul sito web.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

* Adobe Commerce su infrastruttura cloud
* Adobe Commerce on-premise
* Magento Open Source

## Best practice

Per evitare un problema a causa del quale il contenuto statico non è disponibile sul sito web, segui queste best practice per assicurarti che il contenuto statico sia configurato e distribuito correttamente:

1. Assicurati di seguire le linee guida di distribuzione:
   * Per Adobe Commerce on-premise e Magento Open Source (tutte le versioni), consulta [Panoramica sulla distribuzione](../../../configuration/deployment/overview.md) nella documentazione per gli sviluppatori.
   * Per Adobe Commerce sull’infrastruttura cloud (tutte le versioni), consulta [Processo di distribuzione cloud](https://devdocs.magento.com/cloud/deploy/cloud-deployment-process.html) e [Strategie di distribuzione dei contenuti statici](https://devdocs.magento.com/cloud/deploy/static-content-deployment.html) nella documentazione per gli sviluppatori.

1. Per Adobe Commerce sull’infrastruttura cloud (tutte le versioni), assicurati che gli strumenti per componenti siano nella versione più recente. Vedi: [Aggiorna la versione degli strumenti](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) nella documentazione per gli sviluppatori.
1. Per Adobe Commerce sull’infrastruttura cloud (tutte le versioni), assicurati che il contenuto statico venga distribuito durante la fase di creazione anziché durante la fase di distribuzione. Vedi: [Gestione della configurazione per le impostazioni dell&#39;archivio - Prestazioni di distribuzione del contenuto statico](https://devdocs.magento.com/cloud/live/sens-data-over.html#cloud-confman-scd-over) nella documentazione per gli sviluppatori.
1. Assicurati di non avere lavori cron a lungo termine e uccidere qualsiasi processo cron a lungo termine. I lavori cron a lungo termine possono assorbire le risorse della CPU e potenzialmente aumentare notevolmente i tempi di distribuzione.
1. Per Adobe Commerce on-premise e Magento Open Source (tutte le versioni), controlla che la `php` Il processo in CLI ha accesso al `pub/static` directory. In caso contrario, potresti riscontrare un problema a causa del quale una distribuzione di contenuto statico non sarà in grado di scrivere file in quella directory. Per ulteriori informazioni: [Autorizzazioni di accesso ai file system](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html) nella documentazione per gli sviluppatori.
1. Assicurati che `generated` directory non è una directory condivisa tra build; in caso contrario, le build potrebbero non riuscire in modo casuale. Per ulteriori informazioni:
   * Adobe Commerce on-premise e Magento Open Source (tutte le versioni): [Dettagli tecnici](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html) nella documentazione per gli sviluppatori.
   * Adobe Commerce su infrastruttura cloud (tutte le versioni): [Processo di distribuzione - Fase 2: build](https://devdocs.magento.com/cloud/reference/discover-deploy.html#cloud-deploy-over-phases-build) nella documentazione per gli sviluppatori.

1. Controlla la tua strategia SCD. La *rapido* strategia è l&#39;impostazione predefinita. Per ulteriori informazioni:
   * Adobe Commerce on-premise e Magento Open Source (tutte le versioni): [Strategie di distribuzione dei file statici](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/static-view/static-view-file-strategy.html) nella documentazione per gli sviluppatori.
   * Adobe Commerce su infrastruttura cloud (tutte le versioni): [Distribuzione di variabili - SCD\_STRATEGY](https://devdocs.magento.com/cloud/env/variables-deploy.html#scd_strategy) nella documentazione per gli sviluppatori.

## Informazioni aggiuntive

Nella documentazione per gli sviluppatori:

* [Contenitore di contenuto statico](https://developer.adobe.com/commerce/admin-developer/pattern-library/containers/static-content/)
* [Firma dei contenuti statici](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/static-content-signing.html)
* [Distribuisci variabili - STATIC\_CONTENT\_SYMLINK](https://devdocs.magento.com/cloud/env/variables-deploy.html#static_content_symlink)
* [Flusso di distribuzione](../../../performance/deployment-flow.md)
* [Installazione senza tempi di inattività](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html)
* [Ottimizzare l’implementazione cloud](https://devdocs.magento.com/cloud/deploy/optimize-cloud-deployment.html)

