---
title: Procedure consigliate per la risoluzione dei problemi
description: Scopri come risolvere i problemi relativi a Adobe Systems Commerce implementazione.
role: Developer
feature: Best Practices
exl-id: 6690eccf-d58d-4cbd-b278-90d020ee7c63
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# Procedure consigliate per la risoluzione dei problemi

Segui queste best practice per una risoluzione efficace dei problemi di Adobe Commerce relativi all’infrastruttura cloud.

## Prodotti e versioni interessati

Adobe Systems Commerce su infrastruttura cloud

## Procedure consigliate

| Tipo di problema | Procedure consigliate | Risorsa |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Problemi di distribuzione | **Segui le best practice di distribuzione.** Il 13% dei ticket di supporto riguarda problemi di implementazione. Le best practice sono state aggiornate per includere modi per prevenire molte di queste cause. | [Best practice per la compilazione e la distribuzione](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices#best-practices) nella nostra documentazione per sviluppatori. |
| Problemi relativi al sito inattivo | **Utilizza lo strumento di risoluzione dei problemi Site Down.** I cron possono essere di lunga durata e possono sovraccaricarsi a vicenda. Sono all&#39;origine di molte interruzioni e problemi di prestazioni. | [Site Down Troubleshooter](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html?lang=it) e [How to reset cron job](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=it) nel nostro knowledge base di supporto. |
| Problemi di prestazioni | **Se non utilizzi Adobe Systems Commerce banner, disattivalo.** Quando il banner è abilitato ma non utilizzato, le risorse vengono utilizzate per eseguire ricerche nel database quando non sono necessarie e ciò causerà problemi di prestazioni. | [Disattiva Adobe Systems output del banner Commerce per migliorare le prestazioni](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.html?lang=it) nel nostro knowledge base di supporto. |
| Problemi Search | **Il motore di ricerca del catalogo MySQL è stato rimosso in Adobe Systems Commerce 2.4.0.** È necessario disporre di Elasticsearch host setup e configurato prima di installare la versione 2.4.0. Consulta Installare e configurare Elasticsearch nella documentazione per gli sviluppatori. | [Configura il servizio Elasticsearch](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/configure/service/elasticsearch) nella documentazione per gli sviluppatori. |
| Errori personalizzati | **Non distribuire durante le ore di punta.** L&#39;aggiunta e la rimozione di utenti attiverà una distribuzione. | [Distribuzione](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/deploy/reduce-downtime) senza tempi di inattività nella documentazione per sviluppatori. |
| Errori e problemi del database | **I problemi del database causano problemi di distribuzione (post hook), prestazioni e situazioni di inattività del sito.** Molti riguardano errori o allocazione insufficiente dello spazio del database. | [Codici](https://mariadb.com/kb/en/library/mariadb-error-codes/#mariadb-specific-error-codes) Errore MariaDB; [Gestisci lo spazio](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space) di archiviazione (incluso il database) nella nostra documentazione per sviluppatori. |
| Problemi di configurazione | **Index in base alla pianificazione anziché Index in Salva.** Questa è la configurazione di indicizzazione più efficiente. Index su Salva causerà la reindicizzazione completa. | [Configura gli indicizzatori](../../../configuration/cli/manage-indexers.md#configure-indexers) nella nostra documentazione per gli sviluppatori. |
| Problemi relativi al codice personalizzato | **Controlla i log delle query lente per individuare opportunità di identificare ed eventualmente terminare processi che richiedono troppo tempo per essere completati.** Le query lente possono causare blocchi del database con conseguenti inattività del sito e problemi di prestazioni. | [Controllo di query lente e processi che richiedono troppo tempo in MySQL](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql.html?lang=it) |
| Problemi di estensione | **Utilizza solo le estensioni verificate attualmente in Commerce Marketplace.** | [Estensioni per Adobe Systems Commerce](https://marketplace.magento.com/extensions.html) |
| Problemi relativi alle risorse | **Monitora la memoria e lo spazio disponibili e ottimizza lo storage.** È possibile disporre di spazio disponibile prima di un&#39;azione che consuma risorse significative (ad esempio, la distribuzione). Anche una scarsa ottimizzazione dell&#39;archiviazione dei file (troppe immagini grandi e ricche, ad esempio) può contribuire a insufficiente spazio. Le risorse insufficienti causano problemi di prestazioni, siti inattivi, distribuzioni bloccate e errori di distribuzione. | [Gestire lo spazio](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/develop/storage/manage-disk-space) su disco nella documentazione per gli sviluppatori; [File spazio di archiviazione basso/esaurito, i caricamenti di pagine specifiche sono lenti](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html?lang=it) nel nostro knowledge base di supporto. |
