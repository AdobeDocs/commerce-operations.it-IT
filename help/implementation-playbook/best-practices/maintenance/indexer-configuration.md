---
title: Best practice di configurazione per gli indicizzatori
description: Gestisci e ottimizza le prestazioni del sito seguendo le best practice per la configurazione dell’indicizzatore.
role: Admin, User
feature: Best Practices
exl-id: b35806f9-4bc6-407e-bedd-5ce3f09c1b9f
source-git-commit: 29168544e3a33b874b104f308bd53cb475ac2638
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# Best practice per la configurazione dell’indicizzatore

Per ottimizzare e mantenere le prestazioni del sito, esaminare e aggiornare la configurazione dell&#39;indicizzatore utilizzando le best practice relative alle prestazioni descritte in questo articolo.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

## Imposta gli indicizzatori da aggiornare in base a una pianificazione

Adobe Commerce dispone di due tipi di modalità di indicizzazione: [!UICONTROL Update on Save] e [!DNL Update on Schedule].

- La modalità **[!UICONTROL Update on Save]** aggiorna immediatamente gli indici ogni volta che il catalogo o altri dati cambiano. Ad esempio, se un utente amministratore aggiunge nuovi prodotti a una categoria, l’indice dei prodotti della categoria viene reindicizzato immediatamente al salvataggio dell’aggiornamento.

- La modalità **[!UICONTROL Update on Schedule]** memorizza informazioni sugli aggiornamenti dei dati e le operazioni di reindicizzazione e gli aggiornamenti degli indici sono gestiti da un processo cron eseguito in background a intervalli pianificati. Il processo cron non esegue sempre una reindicizzazione ogni volta che viene eseguito. Reindicizza solo quando sono presenti nuove voci nei registri di modifica dell’indicizzatore (ad esempio, è presente un backlog sugli indicizzatori).

La presenza di un archivio di grandi dimensioni con più amministratori che lavorano nel back-end o il numero elevato di importazioni ed esportazioni provoca frequenti aggiornamenti dell’indice. Se la configurazione dell&#39;indice del sito è impostata sulla modalità [!UICONTROL Update on Save], la reindicizzazione frequente riduce le prestazioni del database, rallentando le prestazioni del sito e causando lunghi ritardi nel processo di reindicizzazione, in particolare per i negozi di grandi dimensioni.

Per ottimizzare le prestazioni del sito, segui queste best practice per l’indicizzazione:

- Rivedi la configurazione dell’indice.
- Impostare gli indicizzatori su _[!UICONTROL Update on Schedule]_&#x200B;per i siti di grandi dimensioni e i siti con aggiornamenti frequenti e traffico elevato. Consulta [Gestione indice](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management#change-the-index-mode).
- Segui le [best practice per le prestazioni](../../../performance/configuration.md) per la gestione degli indici.

>[!IMPORTANT]
>
>Il comportamento dell&#39;indicizzatore [!DNL Customer Grid] è stato modificato nella versione 2.4.8:
>
>- **Prima della versione 2.4.8**: l&#39;indicizzatore [!DNL Customer Grid] può essere reindicizzato solo utilizzando l&#39;opzione [!UICONTROL Update on Save] e non supporta l&#39;opzione [!UICONTROL Update by Schedule].
>- **2.4.8 e versioni successive**: l&#39;indicizzatore [!DNL Customer Grid] supporta sia la modalità [!UICONTROL Update on Save] che la modalità [!UICONTROL Update by Schedule]. Impostazione predefinita: [!UICONTROL Update by Schedule].

## Informazioni aggiuntive

- [Gestione dell’indice per gli utenti amministratori](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [Gestione dell&#39;indice tramite Magento CLI](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [Panoramica sull&#39;indicizzazione per sviluppatori](https://developer.adobe.com/commerce/php/development/components/indexing/)
