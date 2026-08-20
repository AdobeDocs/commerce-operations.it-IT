---
title: Best practice per la risoluzione dei problemi
description: Scopri come risolvere i problemi di implementazione di Adobe Commerce.
role: Developer
feature: Best Practices
exl-id: 6690eccf-d58d-4cbd-b278-90d020ee7c63
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: '597'
ht-degree: 0%

---

# Best practice per la risoluzione dei problemi

Segui queste best practice per una risoluzione efficace dei problemi di Adobe Commerce relativi all’infrastruttura cloud.

## Prodotti e versioni interessati

Adobe Commerce sull’infrastruttura cloud

## Best practice

| Tipo di problema | Best practice | Risorsa |
|----------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Problemi di distribuzione | **Segui le best practice per la distribuzione.** Il 13% dei ticket di supporto riguarda problemi di distribuzione. Le best practice sono state aggiornate per includere modi per prevenire molte di queste cause. | [Best practice per le build e la distribuzione](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/deploy/best-practices#best-practices) nella documentazione per gli sviluppatori. |
| Problemi di inattività del sito | **Utilizzare Risoluzione dei problemi di inattività del sito.** Le ronde possono essere lunghe e possono sovrapporsi l&#39;una all&#39;altra. Sono all’origine di molte interruzioni e problemi di prestazioni. | [Risoluzione dei problemi del sito inattivo](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27152) e [Come ripristinare i processi cron](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/cron-job-is-stuck-in-running-status) nella Knowledge Base di supporto. |
| Problemi relativi alle prestazioni | **Se non utilizzi il banner Adobe Commerce, disattivalo.** Quando il banner è abilitato ma non utilizzato, le risorse vengono utilizzate per eseguire ricerche nel database quando non sono necessarie e ciò causerà problemi di prestazioni. | [Disattiva l&#39;output del banner Adobe Commerce per migliorare le prestazioni](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-26909) nella knowledge base di supporto. |
| Problemi di ricerca | **Il motore di ricerca del catalogo MySQL è stato rimosso in Adobe Commerce 2.4.0.** Prima di installare la versione 2.4.0, è necessario aver configurato e configurato l’host Elasticsearch. Consulta Installare e configurare Elasticsearch nella documentazione per gli sviluppatori. | [Configura il servizio Elasticsearch](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/configure/service/elasticsearch) nella documentazione per gli sviluppatori. |
| Errori personalizzati | **Non distribuire durante gli orari di punta.** L’aggiunta e la rimozione di utenti attiveranno una distribuzione. | [Distribuzione senza tempi di inattività](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/deploy/reduce-downtime) nella documentazione per gli sviluppatori. |
| Errori e problemi del database | **I problemi del database causano problemi di distribuzione (post hook), prestazioni e situazioni di inattività del sito.** Molti di questi problemi comportano errori o allocazione insufficiente dello spazio del database. | [Codici di errore MariaDB](https://mariadb.com/docs/server/reference/error-codes/mariadb-error-code-reference); [Gestione spazio di archiviazione](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/storage/manage-disk-space) (incluso il database) nella documentazione per gli sviluppatori. |
| Problemi di configurazione | **Indice per pianificazione anziché Indice al salvataggio.** Si tratta della configurazione di indicizzazione più efficiente. L’indice al salvataggio causerà la reindicizzazione completa. | [Configura gli indicizzatori](../../../configuration/cli/manage-indexers.md#configure-indexers) nella documentazione per gli sviluppatori. |
| Problemi relativi al codice personalizzato | **Controlla i registri di query lenti per individuare le opportunità di identificare e potenzialmente terminare i processi che richiedono troppo tempo per essere completati.** Le query lente possono causare deadlock del database con conseguente abbandono del sito e problemi di prestazioni. | [Verifica di query lente e processi che richiedono troppo tempo in MySQL](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/database/checking-slow-queries-and-processes-mysql) |
| Problemi di estensione | **Utilizza solo estensioni verificate attualmente in Commerce Marketplace.** | [Estensioni per Adobe Commerce](https://commercemarketplace.adobe.com//extensions.html) |
| Problemi relativi alle risorse | **Monitoraggio della memoria e dello spazio disponibili e ottimizzazione dello spazio di archiviazione.** Prima di un’azione che consuma risorse significative (ad esempio, per l’implementazione), potrebbe essere disponibile dello spazio. Anche una scarsa ottimizzazione dell’archiviazione dei file (ad esempio, troppe immagini di grandi dimensioni e ricche di contenuti) può contribuire a ridurre lo spazio disponibile. Le risorse insufficienti causano problemi di prestazioni, inattività del sito, installazioni bloccate e errori di distribuzione. | [Gestisci lo spazio su disco](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/storage/manage-disk-space) nella documentazione per gli sviluppatori; [Archiviazione dei file insufficiente/esaurita, caricamenti di pagine specifici lenti](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow) nella Knowledge Base di supporto. |
