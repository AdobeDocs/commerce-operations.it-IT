---
title: Best practice per l’implementazione di contenuti statici
description: Scopri come evitare che i problemi relativi al contenuto statico non vengano visualizzati nella vetrina di Adobe Commerce o del Magento Open Source.
role: Developer
feature: Best Practices
exl-id: 9f521963-6fe4-4844-b2d1-fd457b706900
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '501'
ht-degree: 0%

---

# Best practice per l’implementazione di contenuti statici

Questo articolo descrive le best practice per la distribuzione di contenuti statici (SCD) in Adobe Commerce per evitare problemi in cui il contenuto statico non sarebbe disponibile sul sito web.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

* Adobe Commerce sull’infrastruttura cloud
* Adobe Commerce on-premise
* Magento Open Source

## Best practice

Per evitare un problema relativo alla mancata disponibilità del contenuto statico sul sito web, segui le best practice seguenti per assicurarti che il contenuto statico sia configurato e distribuito correttamente:

1. Assicurati di seguire le linee guida per la distribuzione:
   * Per Adobe Commerce on-premise e Magento Open Source (tutte le versioni), consulta [Panoramica della distribuzione](../../../configuration/deployment/overview.md) nella documentazione per gli sviluppatori.
   * Per l’infrastruttura cloud di Adobe Commerce (tutte le versioni), consulta [Processo di distribuzione cloud](https://devdocs.magento.com/cloud/deploy/cloud-deployment-process.html) e [Strategie di distribuzione dei contenuti statici](https://devdocs.magento.com/cloud/deploy/static-content-deployment.html) nella documentazione per gli sviluppatori.

1. Per l’infrastruttura cloud di Adobe Commerce (tutte le versioni), assicurati che gli strumenti ece siano nella versione più recente. Consulta: [Aggiorna versione strumenti ece](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) nella documentazione per gli sviluppatori.
1. Per l’infrastruttura cloud di Adobe Commerce (tutte le versioni), assicurati che il contenuto statico sia distribuito durante la fase di build anziché di distribuzione. Consulta: [Gestione della configurazione per le impostazioni dello store: prestazioni di distribuzione del contenuto statico](https://devdocs.magento.com/cloud/live/sens-data-over.html#cloud-confman-scd-over) nella documentazione per gli sviluppatori.
1. Assicurati di non avere processi cron con tempi di esecuzione lunghi e di non terminare i processi cron con tempi di esecuzione lunghi. I processi cron a esecuzione prolungata possono richiedere risorse della CPU e potenzialmente aumentare notevolmente i tempi di distribuzione.
1. Per Adobe Commerce on-premise e Magenti Open Source (tutte le versioni), verifica che il `php` processo in CLI ha accesso al `pub/static` directory. In caso contrario, potrebbe verificarsi un problema che impedirebbe a una distribuzione di contenuto statico di scrivere file in tale directory. Per ulteriori informazioni: [Autorizzazioni di accesso ai file system](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html) nella documentazione per gli sviluppatori.
1. Assicurati che `generated` la directory non è una directory condivisa tra le build; in caso contrario, le build potrebbero non riuscire in modo casuale. Per ulteriori informazioni:
   * Adobe Commerce on-premise e Magento Open Source (tutte le versioni): [Dettagli tecnici](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html) nella documentazione per gli sviluppatori.
   * Adobe Commerce su infrastruttura cloud (tutte le versioni): [Processo di implementazione - Fase 2: compilazione](https://devdocs.magento.com/cloud/reference/discover-deploy.html#cloud-deploy-over-phases-build) nella documentazione per gli sviluppatori.

1. Verifica la strategia SCD. Il *rapido* Strategia è l&#39;impostazione predefinita. Per ulteriori informazioni:
   * Adobe Commerce on-premise e Magento Open Source (tutte le versioni): [Strategie di distribuzione dei file statici](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/static-view/static-view-file-strategy.html) nella documentazione per gli sviluppatori.
   * Adobe Commerce su infrastruttura cloud (tutte le versioni): [Distribuisci variabili - SCD\_STRATEGY](https://devdocs.magento.com/cloud/env/variables-deploy.html#scd_strategy) nella documentazione per gli sviluppatori.

## Informazioni aggiuntive

Nella documentazione per gli sviluppatori:

* [Contenitore di contenuti statici](https://developer.adobe.com/commerce/admin-developer/pattern-library/containers/static-content/)
* [Firma contenuto statico](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/static-content-signing.html)
* [Distribuisci variabili - STATIC\_CONTENT\_SYMLINK](https://devdocs.magento.com/cloud/env/variables-deploy.html#static_content_symlink)
* [Flusso di distribuzione](../../../performance/deployment-flow.md)
* [Installazione senza downtime](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html)
* [Ottimizzare l’implementazione cloud](https://devdocs.magento.com/cloud/deploy/optimize-cloud-deployment.html)
