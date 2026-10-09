---
title: Integra [!DNL Site-Wide Analysis Tool]
description: Per recuperare il report [!DNL Upgrade Compatibility Tool] dal dashboard [!DNL Site-Wide Analysis Tool] nel progetto Adobe Commerce, segui la procedura riportata di seguito.
exl-id: 1ef37294-a837-47a4-841c-4027087acf12
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '190'
ht-degree: 0%
---
# Integra [!DNL Site-Wide Analysis Tool]

[!DNL Site-Wide Analysis Tool] fornisce monitoraggio delle prestazioni in tempo reale 24 ore su 24, 7 giorni su 7, rapporti e raccomandazioni per garantire la sicurezza e l&#39;operabilità delle istanze di Adobe Commerce.

[!DNL Upgrade Compatibility Tool] è ora integrato con [!DNL Site-Wide Analysis Tool] per consentire agli utenti non tecnici di eseguire [!DNL Upgrade Compatibility Tool] e ottenere un [report](../upgrade-compatibility-tool/reports.md) contenente un elenco di problemi per ogni file.

Per ulteriori informazioni, consulta la [[!DNL Site-Wide Analysis Tool] guida utente](/help/tools/site-wide-analysis-tool/access.md).

## Esegui [!DNL Upgrade Compatibility Tool] da [!DNL Site-Wide Analysis Tool]

Passa alla dashboard [!DNL Site-Wide Analysis Tool] per il progetto e individua il widget [!DNL Upgrade Compatibility Tool].

![Widget SWAT UCT - Iniziale](../../assets/upgrade-guide/uct-swat-initial.png)

Fare clic su **[!UICONTROL Run Upgrade Scan]**. La scansione può richiedere un po’ di tempo a seconda delle dimensioni del progetto. Un rotatore indica che la scansione è in corso.

![Widget SWAT UCT - In corso](../../assets/upgrade-guide/uct-swat-progress.png)

Una volta completata la scansione, i risultati di alto livello vengono visualizzati nel widget.

![Widget SWAT UCT - Risultati](../../assets/upgrade-guide/uct-swat-results.png)

Fare clic su **[!UICONTROL Download Report]** per recuperare il [!DNL Upgrade Compatibility Tool] [report HTML](../upgrade-compatibility-tool/reports.md#html-report) e rivedere i dettagli.


>[!NOTE]
>
> L&#39;esecuzione di [!DNL Upgrade Compatibility Tool] tramite [!DNL Site-Wide Analysis Tool] ottimizza i risultati e consente di concentrarsi sui problemi nuovi e critici per l&#39;aggiornamento di destinazione. Utilizza l&#39;opzione [`--ignore-current-version-compatibility-errors`](run.md#optimize-your-results) e mostra sempre i risultati confrontando la versione del progetto con l&#39;ultima versione rilasciata.
