---
title: Best practice per l’implementazione di contenuti statici
description: Scopri come evitare problemi con il contenuto statico che non viene visualizzato nella vetrina Adobe Commerce.
role: Developer
feature: Best Practices
exl-id: 9f521963-6fe4-4844-b2d1-fd457b706900
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# Best practice per l’implementazione di contenuti statici

Questo articolo descrive le best practice per la distribuzione di contenuti statici (SCD) in Adobe Commerce per evitare problemi in cui il contenuto statico non sarebbe disponibile sul sito web.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

* Adobe Commerce sull’infrastruttura cloud
* Adobe Commerce on-premise

## Best practice

Per evitare un problema relativo alla mancata disponibilità del contenuto statico sul sito web, segui le best practice seguenti per assicurarti che il contenuto statico sia configurato e distribuito correttamente:

1. Assicurati di seguire le linee guida per la distribuzione:
   * Per Adobe Commerce on-premise (tutte le versioni), consulta [Panoramica della distribuzione](../../../configuration/deployment/overview.md) nella documentazione per gli sviluppatori.
   * Per Adobe Commerce sull&#39;infrastruttura cloud (tutte le versioni), consulta [Processo di distribuzione cloud](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/deploy/process) e [Strategie di distribuzione dei contenuti statici](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/deploy/static-content) nella documentazione per gli sviluppatori.

1. Per l’infrastruttura cloud di Adobe Commerce (tutte le versioni), assicurati che gli strumenti ece siano nella versione più recente. Consulta: [Aggiorna versione strumenti ece](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/release-notes/ece-tools-package) nella documentazione per gli sviluppatori.
1. Per l’infrastruttura cloud di Adobe Commerce (tutte le versioni), assicurati che il contenuto statico sia distribuito durante la fase di build anziché di distribuzione. Consulta: [Gestione della configurazione per le impostazioni dello store - Prestazioni della distribuzione di contenuti statici](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/configure-store/store-settings#cloud-confman-scd-over) nella documentazione per gli sviluppatori.
1. Assicurati di non avere processi cron con tempi di esecuzione lunghi e di non terminare i processi cron con tempi di esecuzione lunghi. I processi cron a esecuzione prolungata possono richiedere risorse CPU e potenzialmente aumentare notevolmente i tempi di installazione.
1. Per Adobe Commerce on-premise (tutte le versioni), verificare che il processo `php` in CLI abbia accesso alla directory `pub/static`. In caso contrario, potrebbe verificarsi un problema che impedirebbe a una distribuzione di contenuto statico di scrivere file in tale directory. Per ulteriori informazioni: [Autorizzazioni di accesso ai file system](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/file-system-permissions.html?lang=it) nella documentazione per gli sviluppatori.
1. Verificare che la directory `generated` non sia una directory condivisa tra le build. In caso contrario, le build potrebbero non riuscire in modo casuale. Per ulteriori informazioni:
   * Adobe Commerce on-premise (tutte le versioni): [Dettagli tecnici](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/deployment/technical-details.html?lang=it) nella documentazione per gli sviluppatori.
   * Adobe Commerce su infrastruttura cloud (tutte le versioni): [Processo di distribuzione - Fase 2: build](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices#cloud-deploy-over-phases-build) nella documentazione per gli sviluppatori.

1. Verifica la strategia SCD. La strategia *quick* è quella predefinita. Per ulteriori informazioni:
   * Adobe Commerce on-premise (tutte le versioni): [Strategie di distribuzione di file statici](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/static-view/static-view-file-strategy.html?lang=it) nella documentazione per gli sviluppatori.
   * Adobe Commerce sull&#39;infrastruttura cloud (tutte le versioni): [Distribuire le variabili - SCD\_STRATEGY](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#scd_strategy) nella documentazione per gli sviluppatori.

## Informazioni aggiuntive

Nella documentazione per gli sviluppatori:

* [Contenitore contenuto statico](https://developer.adobe.com/commerce/admin-developer/pattern-library/containers/static-content/)
* [Firma contenuto statico](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/static-content-signing.html?lang=it)
* [Distribuisci variabili - STATIC\_CONTENT\_SYMLINK](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy#static_content_symlink)
* [Flusso di distribuzione](../../../performance/deployment-flow.md)
* [Distribuzione senza tempi di inattività](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/deploy/reduce-downtime)
* [Ottimizza distribuzione cloud](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/deploy/optimization)
