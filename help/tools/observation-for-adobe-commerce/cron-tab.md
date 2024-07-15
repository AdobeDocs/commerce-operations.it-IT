---
title: Il [!DNL Cron] scheda
description: Scopri circa la [!DNL Cron] scheda di [!DNL Observation for Adobe Commerce].
exl-id: 66f5ffd6-4118-4534-b2d6-09c7a30e5e13
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Il [!DNL Cron] scheda

Questo scheda è un tentativo di isolare rapidamente i problemi e le cause dei [!DNL cron] problemi.

## [!UICONTROL Cron transaction duration in seconds]

![Durata della transazione in secondi](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

Il **[!UICONTROL Cron transaction duration in seconds]** frame visualizza [!DNL crons] la durata della transazione in secondi. Verranno visualizzate le transazioni con tempi di esecuzione lunghi. Un approfondimento su APM mostrerà maggiori dettagli su quale query potrebbe essere in esecuzione la transazione/operazione.

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![Thread MySQL non dormienti per nodo](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

Il **[!UICONTROL MySQL Non-Sleeping Threads by Node]** frame mostra i thread MySQL Non-Sleeping per nodo nel arco temporale selezionato.

## [!UICONTROL SQL Trace count by path]

![Conteggio delle tracce SQL per percorso](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)

Il **[!UICONTROL SQL Trace count by path]** frame esamina i conteggi delle tracce MySQL per percorso, che può aiutare a tracciare le istruzioni SQL su un arco temporale selezionato.

## [!UICONTROL Cron database call]

![Chiamata al database cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

Il **[!UICONTROL Cron database call]** frame esamina il numero di [!DNL crons] chiamate al database in un arco temporale selezionato.

## [!UICONTROL Cron schedule table locks]

![Blocchi da tavolo Cron programmare](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

Il frame **[!UICONTROL Cron schedule table locks]** esamina i blocchi della tabella di pianificazione [!DNL cron] in un intervallo temporale selezionato.

## [!UICONTROL Cron schedule clean cron fired]

![Blocchi della tabella di pianificazione Cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

La **[!UICONTROL Cron schedule clean cron fired]** cornice esamina il numero di [!DNL crons] elementi puliti in un arco temporale selezionato. Se nessun dato viene visualizzato in questo frame, potrebbe indicare che problema con [!DNL crons] l&#39;esecuzione corretta. Se il processo programmare non viene pulito, [!DNL crons] non verrà eseguito in modo ottimale e l&#39;esecuzione [!DNL cron] potrebbe richiedere più tempo.

## [!UICONTROL Cron schedule clean records details table]

![Tabella dettagli cron programmare clean records](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

La **[!UICONTROL Cron schedule clean records details table]** tabella fornisce dettagli sul processo di pulizia dei record dalla `cron_schedule` tabella in un arco temporale selezionato.

## [!UICONTROL cron_schedule table updates]

![Aggiornamenti tabella cron_programmare](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

Il **[!UICONTROL cron_schedule table updates]** frame esamina il numero di [!DNL cron] aggiornamenti pianificati delle tabelle in un arco temporale selezionato. Un&#39;elevata attività sull&#39;eliminazione o l&#39;aggiornamento di questa tabella può indicare un problema con [!DNL crons]. Inoltre, [!DNL crons] aggiorna questa tabella quando vengono eseguiti e completati, quindi se non c&#39;è attività su questa tabella e sono [!DNL crons] configurati, potrebbe esserci un problema con [!DNL crons].

## [!UICONTROL Datastore Operations Tables]

![Tables sulle operazioni dell&#39;archivio dati](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

Esamina **[!UICONTROL Datastore Operations Tables]** le operazioni della tabella di database, tra cui `SELECT`, `DELETE`e `UPDATE` in un arco temporale selezionato. Questo frame mostra le tabelle di database con la frequenza di operazione più elevata rispetto a esse.
