---
title: Integrare [!DNL Site-Wide Analysis Tool]
description: Per recuperare i [!DNL Upgrade Compatibility Tool] rapporto da [!DNL Site-Wide Analysis Tool] nel progetto Adobe Commerce.
exl-id: 1ef37294-a837-47a4-841c-4027087acf12
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---

# Integrare [!DNL Site-Wide Analysis Tool]

Il [!DNL Site-Wide Analysis Tool] fornisce monitoraggio delle prestazioni, rapporti e raccomandazioni in tempo reale, 24 ore su 24, 7 giorni su 7, per garantire la sicurezza e l’operabilità delle istanze di Adobe Commerce.

Il [!DNL Upgrade Compatibility Tool] è ora integrato con [!DNL Site-Wide Analysis Tool] per consentire a persone non tecniche di eseguire [!DNL Upgrade Compatibility Tool] e ottenere un [rapporto](../upgrade-compatibility-tool/reports.md) contenente un elenco di problemi per ciascun file.

Consulta la [[!DNL Site-Wide Analysis Tool] guida utente](https://docs.magento.com/user-guide/reports/site-wide-analysis-tool.html) per ulteriori informazioni.

## Esegui il [!DNL Upgrade Compatibility Tool] dal [!DNL Site-Wide Analysis Tool]

Accedi a [!DNL Site-Wide Analysis Tool] dashboard per il progetto e individuare [!DNL Upgrade Compatibility Tool] widget.

![Widget SWAT UCT - Iniziale](../../assets/upgrade-guide/uct-swat-initial.png)

Clic **[!UICONTROL Run Upgrade Scan]**. La scansione può richiedere un po’ di tempo a seconda delle dimensioni del progetto. Un rotatore indica che la scansione è in corso.

![Widget SWAT UCT - In corso](../../assets/upgrade-guide/uct-swat-progress.png)

Una volta completata la scansione, i risultati di alto livello vengono visualizzati nel widget.

![Widget SWAT UCT - Risultati](../../assets/upgrade-guide/uct-swat-results.png)

Clic **[!UICONTROL Download Report]** per recuperare [!DNL Upgrade Compatibility Tool] [Rapporto HTML](../upgrade-compatibility-tool/reports.md#html-report) e rivedi i dettagli.


>[!NOTE]
>
> Esecuzione di [!DNL Upgrade Compatibility Tool] tramite [!DNL Site-Wide Analysis Tool] ottimizza i risultati e consente di concentrarsi sui problemi nuovi e critici per l’aggiornamento di target. Utilizza il [`--ignore-current-version-compatibility-errors`](run.md#optimize-your-results) e mostra sempre i risultati confrontando la versione del progetto con l’ultima versione rilasciata.
