---
title: Il [!DNL Cron] scheda
description: Scopri di più su [!DNL Cron] scheda di [!DNL Observation for Adobe Commerce].
exl-id: 66f5ffd6-4118-4534-b2d6-09c7a30e5e13
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# Il [!DNL Cron] scheda

Questa scheda è un tentativo di isolare rapidamente i problemi e le cause di [!DNL cron] problemi.

## [!UICONTROL Cron transaction duration in seconds]

![Durata della transazione del controllo in secondi](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

Il **[!UICONTROL Cron transaction duration in seconds]** visualizzazioni frame [!DNL crons] durata della transazione in secondi. Verranno visualizzate le transazioni con tempi di esecuzione lunghi. Un approfondimento su APM mostrerà ulteriori dettagli su quale query la transazione/operazione potrebbe essere in esecuzione.

## [!UICONTROL MySQL Non-Sleeping Threads by Node]

![Thread MySQL non sospesi per nodo](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

Il **[!UICONTROL MySQL Non-Sleeping Threads by Node]** Il fotogramma mostra i thread MySQL non sospesi per nodo nell&#39;intervallo temporale selezionato.

## [!UICONTROL SQL Trace count by path]

![Numero traccia SQL per percorso](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)

Il **[!UICONTROL SQL Trace count by path]** Il frame esamina i conteggi di traccia MySQL in base al percorso, che possono aiutare a tracciare le istruzioni SQL in un arco temporale selezionato.

## [!UICONTROL Cron database call]

![Chiamata al database Cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

Il **[!UICONTROL Cron database call]** il frame visualizza il numero di [!DNL crons] chiamata al database in un arco temporale selezionato.

## [!UICONTROL Cron schedule table locks]

![Blocchi della tabella di pianificazione delle credenziali](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

Il **[!UICONTROL Cron schedule table locks]** il frame guarda [!DNL cron] la tabella di pianificazione si blocca in un arco temporale selezionato.

## [!UICONTROL Cron schedule clean cron fired]

![Blocchi della tabella di pianificazione delle credenziali](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

Il **[!UICONTROL Cron schedule clean cron fired]** il frame visualizza il numero di [!DNL crons] puliti in un intervallo temporale selezionato. Se in questo frame non vengono visualizzati dati, potrebbe indicare un problema con [!DNL crons] correttamente. Se il [!DNL cron] pianificazione del processo non pulita, [!DNL crons] non viene eseguito in modo ottimale e l&#39;esecuzione potrebbe richiedere più tempo.

## [!UICONTROL Cron schedule clean records details table]

![Tabella dei dettagli dei record puliti per la pianificazione della corona](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

Il **[!UICONTROL Cron schedule clean records details table]** nella tabella vengono fornite informazioni dettagliate sul job per la pulizia dei record `cron_schedule` in un arco temporale selezionato.

## [!UICONTROL cron_schedule table updates]

![aggiornamenti tabella cron_schedule](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

Il **[!UICONTROL cron_schedule table updates]** il frame visualizza il numero di [!DNL cron] la tabella pianificata viene aggiornata nell’arco temporale selezionato. Un’attività elevata sull’eliminazione o l’aggiornamento di questa tabella può indicare un problema con [!DNL crons]. Inoltre, [!DNL crons] aggiorna questa tabella quando vengono eseguite e completate, quindi se non vi è alcuna attività in questa tabella e sono [!DNL crons] configurato, potrebbe essersi verificato un problema con [!DNL crons].

## [!UICONTROL Datastore Operations Tables]

![Tabelle delle operazioni dell’archivio dati](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

Il **[!UICONTROL Datastore Operations Tables]** esamina le operazioni delle tabelle del database, tra cui `SELECT`, `DELETE`, e `UPDATE` in un arco temporale selezionato. Questo frame mostra le tabelle di database con la frequenza di operazione più elevata rispetto a esse.
