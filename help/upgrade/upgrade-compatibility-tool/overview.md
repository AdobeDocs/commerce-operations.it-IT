---
title: Panoramica di  [!DNL Upgrade Compatibility Tool]
description: Scopri  [!DNL Upgrade Compatibility Tool]  e come può aiutarti con il tuo progetto Adobe Commerce.
exl-id: 9493406a-1690-462b-b119-1b685b026c0b
source-git-commit: 79c8a15fb9686dd26d73805e9d0fd18bb987770d
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Panoramica della guida

{{commerce-only}}

Questa guida è destinata agli amministratori e ai tecnici del software di Adobe Commerce. Include informazioni dettagliate sull&#39;installazione di [!DNL Upgrade Compatibility Tool], nonché sulla relativa configurazione e gestione. È necessario conoscere già le nozioni di base della configurazione e delle funzionalità principali di Commerce.

## Panoramica di [!DNL Upgrade Compatibility Tool]

[!DNL Upgrade Compatibility Tool] è uno strumento che controlla un&#39;istanza personalizzata di Adobe Commerce rispetto a una versione specifica analizzando tutti i moduli e il codice di base in essa installati. Restituisce un elenco di problemi critici, errori e avvisi che devono essere risolti prima di eseguire l’aggiornamento a una versione più recente di Adobe Commerce.

## Utilizza [!DNL Upgrade Compatibility Tool]

È possibile utilizzare [!DNL Upgrade Compatibility Tool] tramite:

- Come strumento [interfaccia della riga di comando](../upgrade-compatibility-tool/run.md) autonomo. Per l&#39;elenco completo dei comandi disponibili, vedere il riferimento [`bin/uct`](../../tools/reference/uct.md).
- Integrazione di [!DNL Upgrade Compatibility Tool] con [[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md).
- Configurazione di esecuzione all&#39;interno del plug-in PHPStorm [ Magento](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md).

## Flusso di lavoro

Il diagramma seguente mostra i possibili flussi di lavoro durante l&#39;esecuzione di [!DNL Upgrade Compatibility Tool]:

Diagramma ![[!DNL Upgrade Compatibility Tool]](../../assets/upgrade-guide/uct-diagram-v5.png)

## Demo di [!DNL Upgrade Compatibility Tool]

Guarda questo video per saperne di più su [!DNL Upgrade Compatibility Tool]:

>[!VIDEO](https://video.tv.adobe.com/v/341245?quality=12)

## Contribuisci a migliorare [!DNL Upgrade Compatibility Tool]

Se hai bisogno di informazioni o hai domande che non sono trattate in questa guida, utilizza le risorse seguenti:

Per connetterti con il team [!DNL Upgrade Compatibility Tool], contattaci sul canale di Slack tecnico [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). Desideriamo ricevere feedback, problemi e suggerimenti per aiutarci a migliorare lo strumento.

[!DNL Upgrade Compatibility Tool] utilizza le regole definite nei nostri [Standard di codifica](https://developer.adobe.com/commerce/php/coding-standards/) per garantire che il progetto segua le best practice di Adobe Commerce e per aiutarti a migliorare ed estendere [!DNL Upgrade Compatibility Tool].

Fare riferimento all&#39;argomento [Contribute](https://developer.adobe.com/commerce/php/coding-standards/contributing/) per ulteriori informazioni sugli standard di codifica.

## Risorse

Consulta le seguenti risorse per comprendere meglio gli aggiornamenti di Adobe Commerce:

- La [guida all&#39;aggiornamento](../overview.md) fornisce una panoramica del tipico percorso di aggiornamento di Adobe Commerce e delle best practice da seguire in tale percorso.
- Nella pagina delle [prossime versioni](https://experienceleague.adobe.com/it/docs/commerce-operations/release/planning/schedule) sono incluse le date per le versioni pianificate e future.
- La pagina [Risorse community](https://developer.adobe.com/commerce/contributor/community/) deve essere utilizzata per avviare discussioni o per trovare ulteriori informazioni.
- Controlla la pagina [strumenti correlati](../upgrade-compatibility-tool/related-tools.md) per trovare strumenti utili nel tuo tipico percorso di aggiornamento.
