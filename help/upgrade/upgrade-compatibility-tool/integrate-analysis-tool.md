---
title: '"Integrare il [!DNL Site-Wide Analysis Tool]"'
description: Segui questi passaggi per recuperare [!DNL Upgrade Compatibility Tool] dal [!DNL Site-Wide Analysis Tool] dashboard nel progetto Adobe Commerce.
source-git-commit: 1fc12289125a5954243e177a0c21505234eb2e81
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Integrare le [!DNL Site-Wide Analysis Tool]

La [!DNL Site-Wide Analysis Tool] fornisce monitoraggio delle prestazioni, report e raccomandazioni in tempo reale 24 ore su 24, 7 giorni su 7, per garantire la sicurezza e l’operabilità delle istanze Adobe Commerce.

La [!DNL Upgrade Compatibility Tool] è ora integrato con [!DNL Site-Wide Analysis Tool] al fine di fornire alle persone non tecniche la possibilità di eseguire il [!DNL Upgrade Compatibility Tool] e ottenere un [rapporto](../upgrade-compatibility-tool/reports.md) contenente un elenco di problemi per ogni file.

Consulta la sezione [[!DNL Site-Wide Analysis Tool] guida utente](https://docs.magento.com/user-guide/reports/site-wide-analysis-tool.html) per ulteriori informazioni.

## Esegui il [!DNL Upgrade Compatibility Tool] dal [!DNL Site-Wide Analysis Tool]

Passa a [!DNL Site-Wide Analysis Tool] dashboard per il progetto e individua [!DNL Upgrade Compatibility Tool] widget.

![widget UCT SWAT - Iniziale](../../assets/upgrade-guide/uct-swat-initial.png)

Clic **[!UICONTROL Run Upgrade Scan]**. La scansione può richiedere un po&#39; di tempo a seconda della dimensione del progetto. Un rotore indica che la scansione è in corso.

![Widget SWAT UCT - In corso](../../assets/upgrade-guide/uct-swat-progress.png)

Una volta completata la scansione, i risultati di alto livello vengono visualizzati nel widget.

![Widget SWAT UCT - Risultati](../../assets/upgrade-guide/uct-swat-results.png)

Fai clic su **[!UICONTROL Download Report]** per recuperare [!DNL Upgrade Compatibility Tool] [Rapporto HTML](../upgrade-compatibility-tool/reports.md#html-report) e controlla i dettagli.


>[!NOTE]
>
> Esecuzione del [!DNL Upgrade Compatibility Tool] attraverso [!DNL Site-Wide Analysis Tool] ottimizza i risultati e ti aiuta a concentrarti sui problemi nuovi e critici per l&#39;aggiornamento di target. Utilizza il [`--ignore-current-version-compatibility-errors`](run.md#optimize-your-results) mostra sempre i risultati confrontando la versione del progetto con l’ultima versione rilasciata.
