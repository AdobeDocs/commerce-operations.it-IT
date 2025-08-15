---
title: 'Scheda  [!DNL Cron] '
description: Scopri la scheda  [!DNL Cron]  di [!DNL Observation for Adobe Commerce].
exl-id: 66f5ffd6-4118-4534-b2d6-09c7a30e5e13
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Scheda [!DNL Cron]

Questa scheda è un tentativo di isolare rapidamente i problemi e le cause di [!DNL cron] problemi.

## [!UICONTROL Cron transaction duration in seconds]

![Durata della transazione in secondi](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

Nel frame **[!UICONTROL Cron transaction duration in seconds]** viene visualizzata la durata della transazione [!DNL crons] in secondi. Verranno visualizzate le transazioni con tempi di esecuzione lunghi. Un approfondimento su APM mostrerà ulteriori dettagli su quale query la transazione/operazione potrebbe essere in esecuzione.

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![Threads non sospesa MySQL per nodo](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

Il frame **[!UICONTROL MySQL Non-Sleeping Threads by Node]** mostra i thread MySQL non sospesi per nodo nel periodo di tempo selezionato.

## [!UICONTROL SQL Trace count by path]

![Conteggio traccia SQL per percorso](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)

Il frame **[!UICONTROL SQL Trace count by path]** esamina i conteggi di traccia MySQL in base al percorso, che possono aiutare a tracciare le istruzioni SQL in un intervallo temporale selezionato.

## [!UICONTROL Cron database call]

![Chiamata al database Cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

Il frame **[!UICONTROL Cron database call]** esamina il numero di [!DNL crons] chiamate al database in un intervallo di tempo selezionato.

## [!UICONTROL Cron schedule table locks]

![Blocchi della tabella di pianificazione Cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

Il frame **[!UICONTROL Cron schedule table locks]** esamina i blocchi della tabella di pianificazione [!DNL cron] in un intervallo temporale selezionato.

## [!UICONTROL Cron schedule clean cron fired]

![Blocchi della tabella di pianificazione Cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

Il frame **[!UICONTROL Cron schedule clean cron fired]** esamina il numero di [!DNL crons] eliminati in un intervallo di tempo selezionato. Se in questo frame non viene visualizzato alcun dato, potrebbe indicare un problema con il corretto funzionamento di [!DNL crons]. Se la pianificazione del processo [!DNL cron] non viene pulita, [!DNL crons] non verrà eseguita in modo ottimale e potrebbe richiedere più tempo.

## [!UICONTROL Cron schedule clean records details table]

![Tabella dettagli record puliti pianificazione corrente](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

La tabella **[!UICONTROL Cron schedule clean records details table]** fornisce dettagli sul processo per pulire i record dalla tabella `cron_schedule` in un intervallo temporale selezionato.

## [!UICONTROL cron_schedule table updates]

![aggiornamenti tabella cron_schedule](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

Il frame **[!UICONTROL cron_schedule table updates]** esamina il numero di [!DNL cron] aggiornamenti pianificati della tabella in un intervallo temporale selezionato. Un&#39;attività elevata sull&#39;eliminazione o l&#39;aggiornamento di questa tabella può indicare un problema con [!DNL crons]. Inoltre, [!DNL crons] aggiorna questa tabella quando viene eseguita e completata, quindi se in questa tabella non è presente alcuna attività e sono configurati [!DNL crons], potrebbe esserci un problema con [!DNL crons].

## [!UICONTROL Datastore Operations Tables]

![Tabelle operazioni archivio dati](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

**[!UICONTROL Datastore Operations Tables]** esamina le operazioni della tabella del database, tra cui `SELECT`, `DELETE` e `UPDATE` in un intervallo temporale selezionato. Questo frame mostra le tabelle di database con la frequenza di operazione più elevata rispetto a esse.
