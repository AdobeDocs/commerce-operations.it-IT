---
title: Best practice per la risoluzione dei problemi
description: Scopri come risolvere i problemi di implementazione di Adobe Commerce.
role: Developer
feature: Best Practices
feature-set: Commerce
exl-id: 6690eccf-d58d-4cbd-b278-90d020ee7c63
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '523'
ht-degree: 0%

---

# Best practice per la risoluzione dei problemi

Segui queste best practice per una risoluzione efficace dei problemi di Adobe Commerce relativi all’infrastruttura cloud.

## Prodotti e versioni interessati

Adobe Commerce sull’infrastruttura cloud

## Best practice

| Tipo di problema | Best practice | Risorsa |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Problemi di distribuzione | **Segui le best practice di distribuzione.** Il 13% dei ticket di supporto riguarda problemi di distribuzione. Le best practice sono state aggiornate per includere modi per prevenire molte di queste cause. | [Best practice per le build e la distribuzione](https://devdocs.magento.com/cloud/reference/discover-deploy.html#best-practices) nella documentazione per gli sviluppatori. |
| Problemi di inattività del sito | **Utilizzare Risoluzione problemi sito inattivo.** Le ronde possono essere lunghe e possono sovrapporsi l&#39;una all&#39;altra. Sono all’origine di molte interruzioni e problemi di prestazioni. | [Risoluzione dei problemi di inattività del sito](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/site-down-or-unresponsive/magento-site-down-troubleshooter.html?lang=en) e [Come ripristinare i processi cron](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status.html?lang=en) nella nostra knowledge base di supporto. |
| Problemi relativi alle prestazioni | **Se non utilizzi il banner Adobe Commerce, disattivalo.** Quando il banner è abilitato ma non utilizzato, le risorse vengono utilizzate per eseguire ricerche nel database quando non sono necessarie e ciò causerà problemi di prestazioni. | [Disattiva l&#39;output del banner Adobe Commerce per migliorare le prestazioni](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/disable-magento-banner-output-to-improve-site-performance.html) nella nostra knowledge base di supporto. |
| Problemi di ricerca | **Il motore di ricerca del catalogo MySQL è stato rimosso in Adobe Commerce 2.4.0.** Prima di installare la versione 2.4.0, è necessario aver configurato e configurato l’host Elasticsearch. Consulta Installare e configurare Elasticsearch nella documentazione per gli sviluppatori. | [Configura servizio Elasticsearch](https://devdocs.magento.com/cloud/project/services-elastic.html) nella documentazione per gli sviluppatori. |
| Errori personalizzati | **Non distribuire durante gli orari di picco.** L’aggiunta e la rimozione di utenti attiveranno una distribuzione. | [Installazione senza downtime](https://devdocs.magento.com/cloud/deploy/reduce-downtime.html) nella documentazione per gli sviluppatori. |
| Errori e problemi del database | **I problemi del database causano problemi di distribuzione (post hook), prestazioni e situazioni di inattività del sito.** Molti di questi problemi comportano errori o allocazione insufficiente dello spazio del database. | [Codici di errore MariaDB](https://mariadb.com/kb/en/library/mariadb-error-codes/#mariadb-specific-error-codes); [Gestione spazio di archiviazione](https://devdocs.magento.com/cloud/project/manage-disk-space.html) (incluso il database) nella documentazione per gli sviluppatori. |
| Problemi di configurazione | **Indice per pianificazione invece di Indice al salvataggio.** Si tratta della configurazione di indicizzazione più efficiente. L’indice al salvataggio causerà la reindicizzazione completa. | [Configurare gli indici](../../../configuration/cli/manage-indexers.md#configure-indexers) nella documentazione per gli sviluppatori. |
| Problemi relativi al codice personalizzato | **Controlla i registri di query lenti per individuare le opportunità di identificare e potenzialmente terminare i processi che richiedono troppo tempo.** Le query lente possono causare deadlock del database con conseguente abbandono del sito e problemi di prestazioni. | [Verifica di query lente e processi che richiedono troppo tempo in MySQL](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql.html) |
| Problemi di estensione | **Utilizza solo estensioni verificate attualmente sulla Commerce Marketplace.** | [Estensioni per Adobe Commerce](https://marketplace.magento.com/extensions.html) |
| Problemi relativi alle risorse | **Monitoraggio della memoria e dello spazio disponibili e ottimizzazione dello storage.** Prima di un’azione che consuma risorse significative (ad esempio, per l’implementazione), potrebbe essere disponibile dello spazio. Anche una scarsa ottimizzazione dell’archiviazione dei file (ad esempio, troppe immagini di grandi dimensioni e ricche di contenuti) può contribuire a ridurre lo spazio disponibile. Le risorse insufficienti causano problemi di prestazioni, inattività del sito, installazioni bloccate e errori di distribuzione. | [Gestione dello spazio su disco](https://devdocs.magento.com/cloud/project/manage-disk-space.html) nella documentazione per gli sviluppatori; [Archiviazione dei file bassa/esaurita, caricamento di pagine specifiche lento](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html?lang=en) nella nostra knowledge base di supporto. |
