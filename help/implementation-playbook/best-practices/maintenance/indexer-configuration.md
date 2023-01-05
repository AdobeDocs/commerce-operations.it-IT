---
title: Best practice di configurazione per gli indici
description: Gestisci e ottimizza le prestazioni del sito seguendo le best practice per la configurazione dell'indicizzatore.
role: Admin, User
feature: Best Practices
feature-set: Commerce
source-git-commit: ae9573f3766c59887aea177cb85bf889c2161bfc
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Best practice per la configurazione dell’indicizzatore

Per ottimizzare e mantenere le prestazioni del sito, rivedi e aggiorna la configurazione dell’indicizzatore utilizzando le best practice sulle prestazioni descritte in questo articolo.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce su infrastruttura cloud
- Adobe Commerce on-premise

## Imposta indici da aggiornare in base a una pianificazione

Adobe Commerce dispone di due tipi di modalità di indicizzazione: [!UICONTROL Update on Save] (impostazione predefinita) e [!DNL Update on Schedule].

- **[!UICONTROL Update on Save]** la modalità aggiorna immediatamente gli indici ogni volta che il catalogo o altri dati cambiano. Ad esempio, se un utente amministratore aggiunge nuovi prodotti a una categoria, l’indice dei prodotti della categoria viene reindicizzato immediatamente al momento del salvataggio dell’aggiornamento.

- **[!UICONTROL Update on Schedule]** in modalità vengono memorizzate informazioni sugli aggiornamenti dei dati e le operazioni di reindicizzazione e gli aggiornamenti dell&#39;indice sono gestiti da un processo cron in esecuzione in background a intervalli pianificati.

La presenza di un grande store con più amministratori che lavorano nel backend o con molte importazioni ed esportazioni attiva frequenti aggiornamenti dell&#39;indice. Se la configurazione dell&#39;indice del sito è impostata su [!UICONTROL Update on Save] modalità, la reindicizzazione frequente rallenta le prestazioni del database che rallenta le prestazioni del sito e causa lunghi ritardi nel processo di reindicizzazione, soprattutto per i grandi negozi.

Per massimizzare le prestazioni del sito, segui queste best practice per l’indicizzazione:

- Rivedi la configurazione dell&#39;indice.
- Imposta gli indici su _[!UICONTROL Update on Schedule]_per siti di grandi dimensioni e siti con aggiornamenti frequenti e traffico pesante. Vedi [Gestione dell&#39;indice](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode).
- Segui [best practice sulle prestazioni](../../../performance/configuration.md) per la gestione degli indici.

>[!IMPORTANT]
>
>La [!DNL Customer Grid] può essere reindicizzato solo utilizzando [!UICONTROL Update on Save] opzione . Questo indice non supporta il `Update by Schedule` opzione .

## Informazioni aggiuntive

- [Gestione dell&#39;indice per gli utenti amministratori](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [Gestione dell’indice utilizzando il Magento CLI](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [Panoramica sull’indicizzazione per gli sviluppatori](https://developer.adobe.com/commerce/php/development/components/indexing/)
