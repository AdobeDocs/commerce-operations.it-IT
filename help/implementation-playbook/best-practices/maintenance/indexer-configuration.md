---
title: Best practice di configurazione per gli indicizzatori
description: Gestisci e ottimizza le prestazioni del sito seguendo le best practice per la configurazione dell’indicizzatore.
role: Admin, User
feature: Best Practices
exl-id: b35806f9-4bc6-407e-bedd-5ce3f09c1b9f
source-git-commit: af66d47279245f8ee105030bbb33d77b1b35c3e5
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# Best practice per la configurazione dell’indicizzatore

Per ottimizzare e mantenere le prestazioni del sito, esaminare e aggiornare la configurazione dell&#39;indicizzatore utilizzando le best practice relative alle prestazioni descritte in questo articolo.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

## Imposta gli indicizzatori da aggiornare in base a una pianificazione

Adobe Commerce dispone di due tipi di modalità di indicizzazione: [!UICONTROL Update on Save] (impostazione predefinita) e [!DNL Update on Schedule].

- **[!UICONTROL Update on Save]** la modalità aggiorna immediatamente gli indici ogni volta che il catalogo o altri dati cambiano. Ad esempio, se un utente amministratore aggiunge nuovi prodotti a una categoria, l’indice dei prodotti della categoria viene reindicizzato immediatamente al salvataggio dell’aggiornamento.

- **[!UICONTROL Update on Schedule]** la modalità memorizza informazioni sugli aggiornamenti dei dati e le operazioni di reindicizzazione e gli aggiornamenti degli indici sono gestiti da un processo cron eseguito in background a intervalli pianificati. Il processo cron non esegue sempre una reindicizzazione ogni volta che viene eseguito. Reindicizza solo quando sono presenti nuove voci nei registri di modifica dell’indicizzatore (ad esempio, è presente un backlog sugli indicizzatori).

La presenza di un archivio di grandi dimensioni con più amministratori che lavorano nel back-end o il numero elevato di importazioni ed esportazioni provoca frequenti aggiornamenti dell’indice. Se la configurazione dell’indice del sito è impostata su [!UICONTROL Update on Save] modalità, la reindicizzazione frequente riduce le prestazioni del database, rallentando le prestazioni del sito e causando lunghi ritardi nel processo di reindicizzazione, in particolare per i negozi di grandi dimensioni.

Per ottimizzare le prestazioni del sito, segui queste best practice per l’indicizzazione:

- Rivedi la configurazione dell’indice.
- Imposta gli indicizzatori su _[!UICONTROL Update on Schedule]_per siti di grandi dimensioni e siti con aggiornamenti frequenti e traffico elevato. Consulta [Gestione indice](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode).
- Segui [best practice per le prestazioni](../../../performance/configuration.md) per la gestione degli indici.

>[!IMPORTANT]
>
>Il [!DNL Customer Grid] può essere reindicizzato solo utilizzando [!UICONTROL Update on Save] opzione. Questo indice non supporta `Update by Schedule` opzione.

## Informazioni aggiuntive

- [Gestione dell’indice per gli utenti amministratori](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [Gestione dell’indice tramite CLI di Magento](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [Panoramica sull’indicizzazione per sviluppatori](https://developer.adobe.com/commerce/php/development/components/indexing/)
