---
title: '"Panoramica del [!DNL Upgrade Compatibility Tool]"'
description: Scopri le [!DNL Upgrade Compatibility Tool] e come può aiutarti con il tuo progetto Adobe Commerce.
source-git-commit: 9b0f97d36092d2a1057cdc905671cda8540881c9
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---


# Panoramica della guida

{{commerce-only}}

Questa guida è destinata agli amministratori e ai tecnici del software di Adobe Commerce. Include informazioni dettagliate sull&#39;installazione del [!DNL Upgrade Compatibility Tool], nonché la sua configurazione e gestione. Assume una comprensione di base della configurazione e della funzionalità principali di Commerce.

## Panoramica [!DNL Upgrade Compatibility Tool]

La [!DNL Upgrade Compatibility Tool] è uno strumento che controlla un’istanza personalizzata di Adobe Commerce rispetto a una versione specifica analizzando tutti i moduli e il codice core installati al suo interno. Restituisce un elenco di problemi critici, errori e avvisi che devono essere risolti prima di eseguire l’aggiornamento a una versione più recente di Adobe Commerce.

## Utilizza la [!DNL Upgrade Compatibility Tool]

È possibile utilizzare [!DNL Upgrade Compatibility Tool] tramite:

- Come indipendente [interfaccia a riga di comando](../upgrade-compatibility-tool/run.md) strumento.
- Integrazione di [!DNL Upgrade Compatibility Tool] con [[!DNL Site-Wide Analysis Tool]](../upgrade-compatibility-tool/integrate-analysis-tool.md).
- Una configurazione di esecuzione all&#39;interno di [Plug-in PHPStorm Magento](../upgrade-compatibility-tool/run-configuration-phpstorm-plugin.md).

## Flusso di lavoro

Il diagramma seguente mostra i possibili flussi di lavoro durante l’esecuzione del [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] Diagramma](../../assets/upgrade-guide/uct-diagram-v5.png)

## Aiutare a migliorare [!DNL Upgrade Compatibility Tool]

Se hai bisogno di informazioni o hai domande che non sono incluse in questa guida, utilizza le risorse seguenti:

Per connettersi al [!DNL Upgrade Compatibility Tool] team, contattateci sul canale di Slack ingegneristico [#upgrade-compatibilità-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). Vogliamo sentire i tuoi feedback, problemi e suggerimenti per aiutarci a migliorare lo strumento.

La [!DNL Upgrade Compatibility Tool] utilizza le regole definite nella [Standard di codifica](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html) per garantire che il progetto segua le best practice di Adobe Commerce e per migliorare ed estendere la [!DNL Upgrade Compatibility Tool].

Fai riferimento a [Collaborare](https://devdocs.magento.com/guides/v2.4/coding-standards/contributing.html) argomento per ulteriori informazioni su come contribuire agli standard di codifica.

## Risorse

Consulta le seguenti risorse per comprendere meglio gli aggiornamenti di Adobe Commerce:

- La [guida all&#39;aggiornamento](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html) fornisce una panoramica del percorso di aggiornamento Adobe Commerce o Magento Open Source tipico e delle best practice da seguire lungo quel percorso.
- La [prossime versioni](https://devdocs.magento.com/release/) fornisce le date delle versioni pianificate e future.
- La [risorse comunitarie](https://developer.adobe.com/commerce/contributor/community/) la pagina deve essere posizionata per avviare discussioni o trovare ulteriori informazioni.
- Controlla la [strumenti correlati](../upgrade-compatibility-tool/related-tools.md) per strumenti utili nel tipico percorso di aggiornamento.
