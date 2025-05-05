---
title: Procedure consigliate per la configurazione per gli indicizzatori
description: Mantenere e ottimizzare prestazioni del sito seguendo le best practice per la configurazione dell'indicizzatore.
role: Admin, User
feature: Best Practices
exl-id: b35806f9-4bc6-407e-bedd-5ce3f09c1b9f
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# Procedure consigliate per la configurazione dell&#39;indicizzatore

Per ottimizzare e gestire prestazioni del sito, rivedere e aggiornare la configurazione dell&#39;indicizzatore utilizzando le best practice sulle prestazioni descritte in questo articolo.

## Prodotti e versioni interessati

[Tutte le versioni](../../../release/versions.md) supportate di:

- Adobe Systems Commerce su infrastruttura cloud
- Adobe Systems Commerce locale

## Impostare gli indicizzatori per l&#39;aggiornamento in una programmare

Adobe Systems Commerce dispone di due tipi di modalità di indicizzazione: [!UICONTROL Update on Save] e [!DNL Update on Schedule].

- **[!UICONTROL Update on Save]** La modalità aggiorna gli indici immediatamente ogni volta che il catalogo o altri dati cambiano. Ad esempio, se un amministratore aggiunge utente nuovi prodotti a una categoria, l&#39;indice dei prodotti della categoria viene reindicizzato immediatamente quando viene salvato l&#39;aggiornamento.

- **[!UICONTROL Update on Schedule]** Mode memorizza le informazioni sugli aggiornamenti dei dati e le operazioni di reindicizzazione e gli aggiornamenti degli indici sono gestiti da un cron job che viene eseguito in background a intervalli pianificati. Il cron job non esegue sempre una reindicizzazione ogni volta che viene eseguito. Reindicizza solo quando sono presenti nuove voci nei log delle modifiche dell&#39;indicizzatore (ad esempio, c&#39;è un backlog sugli indicizzatori).

Avere una grande store con più amministratori che lavorano nel back-end o avere molte importazioni ed esportazioni innesca frequenti aggiornamenti dell&#39;indice. Se la configurazione dell&#39;indice del sito è impostata su [!UICONTROL Update on Save] mode, la reindicizzazione frequente riduce le prestazioni del database, rallentando prestazioni del sito e causando lunghi ritardi nel processo di reindicizzazione, soprattutto per i grandi archivi.

Per massimizzare la prestazioni del sito, seguire queste best practice per l&#39;indicizzazione:

- Esamina la configurazione dell&#39;indice.
- Impostare gli indicizzatori su _[!UICONTROL Update on Schedule]_&#x200B;per siti di grandi dimensioni e siti con aggiornamenti frequenti e traffico pesanti. Consulta [Gestione Index](https://experienceleague.adobe.com/it/docs/commerce-admin/systems/tools/index-management#change-the-index-mode).
- Seguire [le best practice](../../../performance/configuration.md) sulle prestazioni per la gestione degli indici.

>[!IMPORTANT]
>
>Il [!DNL Customer Grid] può essere reindicizzato solo utilizzando questa [!UICONTROL Update on Save] opzione. Questo indice non supporta l&#39;opzione `Update by Schedule` .

## Informazioni aggiuntive

- [Gestione Index per gli utenti Admin](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [Gestione Index utilizzando l&#39;interfaccia della riga di comando di Magento](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html?lang=it)
- [Panoramica sull&#39;indicizzazione per gli sviluppatori](https://developer.adobe.com/commerce/php/development/components/indexing/)
