---
title: '"Il [!UICONTROL Cron] scheda"'
description: Scopri le [!UICONTROL Cron] scheda di [!DNL Observation for Adobe Commerce].
source-git-commit: 3c1e50b3bff1bd2b2760e2e763173275161b0044
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 0%

---

# La [!UICONTROL Cron] scheda

Questa scheda è un tentativo di isolare rapidamente i problemi e le cause dei cron.

## [!UICONTROL Cron transaction duration in seconds]

![Durata della transazione Cron in secondi](../../assets/tools/observation-for-adobe-commerce/cron-tab-1.jpg)

La **[!UICONTROL Cron transaction duration in seconds]** frame visualizza la durata della transazione cronica in secondi. Verranno visualizzate le transazioni con tempi di esecuzione lunghi. Un&#39;analisi più approfondita di APM mostrerà più dettagli su quale query potrebbe essere in esecuzione la transazione/operazione.

## [!UICONTROL MySql Non-Sleeping Threads by Node]

![Thread non server MySql per nodo](../../assets/tools/observation-for-adobe-commerce/cron-tab-2.jpg)

La **[!UICONTROL MySql Non-Sleeping Threads by Node]** Il frame mostra i thread non di sonno MySql per nodo nell&#39;arco temporale selezionato.

## [!UICONTROL SQL Trace count by path]

![Conteggio traccia SQL per percorso](../../assets/tools/observation-for-adobe-commerce/cron-tab-3.jpg)

La **[!UICONTROL SQL Trace count by path]** frame esamina i conteggi di traccia di MySql in base al percorso, che può aiutare a tracciare le istruzioni SQL in un arco temporale selezionato.

## [!UICONTROL Cron database call]

![Chiamata al database Cron](../../assets/tools/observation-for-adobe-commerce/cron-tab-4.jpg)

La **[!UICONTROL Cron database call]** frame esamina il numero di cronometri che chiamano il database in un arco temporale selezionato.

## [!UICONTROL Cron schedule table locks]

![Blocchi per tabelle di programmazione](../../assets/tools/observation-for-adobe-commerce/cron-tab-5.jpg)

La **[!UICONTROL Cron schedule table locks]** il frame esamina i blocchi della tabella di pianificazione cron in un arco temporale selezionato.

## [!UICONTROL Cron schedule clean cron fired]

![Blocchi per tabelle di programmazione](../../assets/tools/observation-for-adobe-commerce/cron-tab-6.jpg)

La **[!UICONTROL Cron schedule clean cron fired]** frame esamina il numero di cronometri ripuliti in un arco temporale selezionato. Se in questo frame non vengono visualizzati dati, potrebbe essere presente un problema di funzionamento corretto dei cronometri. Se la pianificazione del processo cron non viene pulita, gli crons non verranno eseguiti in modo ottimale e l&#39;esecuzione potrebbe richiedere più tempo.

## [!UICONTROL Cron schedule clean records details table]

![Tabella dei dettagli dei record puliti della pianificazione della CROR](../../assets/tools/observation-for-adobe-commerce/cron-tab-7.jpg)

La **[!UICONTROL Cron schedule clean records details table]** la tabella fornisce dettagli sul lavoro da pulire i record dal `cron_schedule` in un arco temporale selezionato.

## [!UICONTROL cron_schedule table updates]

![aggiornamenti tabella cron_Schedule](../../assets/tools/observation-for-adobe-commerce/cron-tab-8.jpg)

La **[!UICONTROL cron_schedule table updates]** frame esamina il numero di aggiornamenti della tabella pianificati cron in un arco temporale selezionato. Un’attività elevata sull’eliminazione o l’aggiornamento di questa tabella può indicare un problema relativo ai cronometri. Inoltre, gli cronisti aggiornano questa tabella quando vengono eseguiti e completati, quindi se non è presente alcuna attività in questa tabella e sono presenti cronometri configurati, potrebbe esserci un problema con gli crons.

## [!UICONTROL Datastore Operations Tables]

![Tabelle delle operazioni del datastore](../../assets/tools/observation-for-adobe-commerce/cron-tab-9.jpg)

La **[!UICONTROL Datastore Operations Tables]** esamina le operazioni della tabella di database, tra cui `SELECT`, `DELETE`e `UPDATE` in un arco temporale selezionato. Questo frame mostra le tabelle del database con la frequenza di funzionamento più elevata rispetto a esse.
