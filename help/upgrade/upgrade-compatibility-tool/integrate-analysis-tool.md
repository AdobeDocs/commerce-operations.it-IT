---
title: '"Integrare il [!DNL Site-Wide Analysis Tool]"'
description: Segui questi passaggi per recuperare [!DNL Upgrade Compatibility Tool] dal [!DNL Site-Wide Analysis Tool] dashboard nel progetto Adobe Commerce.
source-git-commit: 5ff08d231269ea0bcb69f8c80aa546b171a5e4a0
workflow-type: tm+mt
source-wordcount: '172'
ht-degree: 0%

---


# Integrare le [!DNL Site-Wide Analysis Tool]

La [!DNL Site-Wide Analysis Tool] fornisce monitoraggio delle prestazioni, report e raccomandazioni in tempo reale 24/7 per garantire la sicurezza e l&#39;operabilità delle installazioni di Adobe Commerce.

La [!DNL Upgrade Compatibility Tool] è ora integrato con [!DNL Site-Wide Analysis Tool] al fine di fornire alle persone non tecniche la possibilità di eseguire il [!DNL Upgrade Compatibility Tool] e ottenere un [Rapporto HTML](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/run.html?lang=en#output) contenente un elenco di problemi per ogni file, specificando la sua gravità, il codice di errore e la descrizione dell’errore.

Consulta la sezione [[!DNL Site-Wide Analysis Tool] guida utente](https://docs.magento.com/user-guide/reports/site-wide-analysis-tool.html) per ulteriori informazioni.

## Esegui il [!DNL Upgrade Compatibility Tool] da SWAT

Passa a [!DNL Site-Wide Analysis Tool] dashboard per il progetto e individua [!DNL Upgrade Compatibility Tool] widget.

![widget UCT SWAT - Iniziale](../../assets/upgrade-guide/uct-swat-initial.png)

Clic **[!UICONTROL Run Upgrade Scan]**. La scansione può richiedere un po&#39; di tempo a seconda della dimensione del progetto. Un rotore indica che la scansione è in corso.

![Widget SWAT UCT - In corso](../../assets/upgrade-guide/uct-swat-progress.png)

Una volta completata la scansione, i risultati di alto livello vengono visualizzati nel widget.

![Widget SWAT UCT - Risultati](../../assets/upgrade-guide/uct-swat-results.png)

Fai clic su **[!UICONTROL Download Report]** per recuperare [!DNL Upgrade Compatibility Tool] HTML crea un rapporto e controlla i dettagli.
