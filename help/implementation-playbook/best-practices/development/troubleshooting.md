---
title: Procedure consigliate per la risoluzione dei problemi
description: Scopri come risolvere i problemi di implementazione di Adobe Commerce.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 48c5666ee9b83bbf8a5c6375ec53762d918bcece
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Procedure consigliate per la risoluzione dei problemi

Segui queste best practice per una risoluzione efficace dei problemi relativi all’infrastruttura cloud di Adobe Commerce.

## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud

## Best practice

| Tipo di problema | Best practice | Risorsa |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Problemi di distribuzione | **Segui le best practice di distribuzione.** Il 13% dei ticket di supporto include problemi di distribuzione. Le best practice sono state aggiornate per includere modi per prevenire molte di queste cause. | [Best practice per build e distribuzione](https://devdocs.magento.com/cloud/reference/discover-deploy.html#best-practices) nella documentazione per gli sviluppatori. |
| Problemi di inattività del sito | **Utilizzare lo strumento di risoluzione dei problemi di inattività del sito.** I cronisti possono essere a lungo in corso e possono superarsi a vicenda. Sono all&#39;origine di molte interruzioni e problemi di prestazioni. | [Risoluzione dei problemi di Site Down](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html?lang=en) e [Come ripristinare i lavori cron](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) nella nostra base di conoscenze di supporto. |
| Problemi di prestazioni | **Se non utilizzi il banner Adobe Commerce, disattivalo.** Quando il banner è abilitato ma non utilizzato, le risorse vengono utilizzate per eseguire ricerche nel database quando non sono necessarie e ciò causerà problemi di prestazioni. | [Disattiva l’output del banner Adobe Commerce per migliorare le prestazioni](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.html) nella nostra knowledge base di supporto. |
| Problemi di ricerca | **Il motore di ricerca del catalogo MySQL è stato rimosso in Adobe Commerce 2.4.0.** Prima di installare la versione 2.4.0, è necessario disporre della configurazione dell’host di Elasticsearch. Consulta Installare e configurare l’Elasticsearch nella documentazione per gli sviluppatori. | [Configurazione del servizio Elasticsearch](https://devdocs.magento.com/cloud/project/services-elastic.html) nella documentazione per gli sviluppatori. |
| Errori personalizzati | **Non distribuire durante i picchi.** L’aggiunta e la rimozione di utenti attiverà una distribuzione. | [Installazione senza tempi di inattività](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html) nella documentazione per gli sviluppatori. |
| Errori e problemi del database | **I problemi del database causano la distribuzione (problemi post-hook), le prestazioni e le situazioni di inattività del sito.** Molti di essi comportano errori o un&#39;allocazione insufficiente dello spazio del database. | [Codici di errore MariaDB](https://mariadb.com/kb/en/library/mariadb-error-codes/#mariadb-specific-error-codes); [Gestione dello spazio di archiviazione](https://devdocs.magento.com/cloud/project/manage-disk-space.html) (compreso il database) nella documentazione per gli sviluppatori. |
| Problemi di configurazione | **Indice per pianificazione invece di Indice al salvataggio.** Questa è la configurazione di indicizzazione più efficiente. L&#39;indice su Save causerà la reindicizzazione completa. | [Configurare gli indicizzatori](../../../configuration/cli/manage-indexers.md#configure-indexers) nella documentazione per gli sviluppatori. |
| Problemi di codice personalizzato | **Controlla i log delle query lente per individuare le opportunità per identificare e possibilmente terminare i processi che richiedono troppo tempo per essere completati.** Le query lente possono causare deadlock del database e causare guasti del sito e problemi di prestazioni. | [Controllo di query e processi lenti troppo a lungo in MySQL](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql.html) |
| Problemi di estensione | **Utilizza solo le estensioni verificate attualmente nella Commerce Marketplace.** | [Estensioni per Adobe Commerce](https://marketplace.magento.com/extensions.html) |
| Problemi relativi alle risorse | **Monitorare la memoria e lo spazio disponibili e ottimizzare lo storage.** Prima di un’azione, potresti avere a disposizione uno spazio che consuma risorse significative (ad esempio, la distribuzione). Anche una scarsa ottimizzazione dello spazio di archiviazione dei file (ad esempio, troppe immagini grandi e ricche) può contribuire a ridurre lo spazio disponibile. Risorse insufficienti causano problemi di prestazioni, inattività del sito, distribuzioni bloccate e errori di distribuzione. | [Gestione dello spazio su disco](https://devdocs.magento.com/cloud/project/manage-disk-space.html) nella documentazione per gli sviluppatori; [Archiviazione dei file esaurita o esaurita, il caricamento specifico della pagina è lento](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html?lang=en) nella nostra base di conoscenze di supporto. |
