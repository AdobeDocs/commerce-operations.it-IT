---
title: Panoramica di [!DNL Upgrade Compatibility Tool]
description: Scopri di più su [!DNL Upgrade Compatibility Tool] e come può aiutarti con il tuo progetto Adobe Commerce.
exl-id: 9493406a-1690-462b-b119-1b685b026c0b
source-git-commit: fc1be3362863d3b0fa3468380fe62ca698abac43
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Panoramica della guida

{{commerce-only}}

Questa guida è destinata agli amministratori e ai tecnici del software di Adobe Commerce. Include informazioni dettagliate sull&#39;installazione del [!DNL Upgrade Compatibility Tool], nonché la relativa configurazione e gestione. È necessario conoscere già le nozioni di base della configurazione e delle funzionalità principali di Commerce.

## Panoramica di [!DNL Upgrade Compatibility Tool]

Il [!DNL Upgrade Compatibility Tool] è uno strumento che confronta un’istanza personalizzata di Adobe Commerce con una versione specifica analizzando tutti i moduli e il codice di base installati in essa. Restituisce un elenco di problemi critici, errori e avvisi che devono essere risolti prima di eseguire l’aggiornamento a una versione più recente di Adobe Commerce.

## Utilizza il [!DNL Upgrade Compatibility Tool]

È possibile utilizzare [!DNL Upgrade Compatibility Tool] tramite:

- Come indipendente [interfaccia della riga di comando](../upgrade-compatibility-tool/run.md) strumento. Per l&#39;elenco completo dei comandi disponibili, vedere [`bin/uct` riferimento](../../tools/reference/uct.md).
- Integrazione di [!DNL Upgrade Compatibility Tool] con [[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md).
- Una configurazione di esecuzione all&#39;interno di [Plug-in Magento PHPStorm](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md).

## Flusso di lavoro

Il diagramma seguente mostra i possibili flussi di lavoro durante l’esecuzione di [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] Diagramma](../../assets/upgrade-guide/uct-diagram-v5.png)

## [!DNL Upgrade Compatibility Tool] demo

Guarda questo video per scoprire di più su [!DNL Upgrade Compatibility Tool]:

>[!VIDEO](https://video.tv.adobe.com/v/341245?quality=12)

## Contribuisci a migliorare [!DNL Upgrade Compatibility Tool]

Se hai bisogno di informazioni o hai domande che non sono trattate in questa guida, utilizza le risorse seguenti:

Per connettersi con [!DNL Upgrade Compatibility Tool] team, contattaci sul canale di Slack del team di progettazione [#upgrade-compatibility-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). Desideriamo ricevere feedback, problemi e suggerimenti per aiutarci a migliorare lo strumento.

Il [!DNL Upgrade Compatibility Tool] utilizza le regole definite in [Standard di codifica](https://developer.adobe.com/commerce/php/coding-standards/) per assicurarti che il progetto segua le best practice di Adobe Commerce e per migliorare ed estendere la [!DNL Upgrade Compatibility Tool].

Consulta la sezione [Contribuisci](https://developer.adobe.com/commerce/php/coding-standards/contributing/) per ulteriori informazioni su come contribuire agli standard di codifica.

## Risorse

Consulta le seguenti risorse per comprendere meglio gli aggiornamenti di Adobe Commerce:

- Il [guida all’aggiornamento](../overview.md) fornisce una panoramica del tipico percorso di aggiornamento di Adobe Commerce e delle best practice da seguire lungo tale percorso.
- Il [prossime versioni](https://devdocs.magento.com/release/) fornisce le date per le versioni pianificate e future.
- Il [risorse della community](https://developer.adobe.com/commerce/contributor/community/) pagina consente di avviare discussioni o di trovare ulteriori informazioni.
- Controlla la [strumenti correlati](../upgrade-compatibility-tool/related-tools.md) pagina per strumenti utili nel tipico percorso di aggiornamento.
