---
title: Panoramica [!DNL Upgrade Compatibility Tool]
description: Scopri le [!DNL Upgrade Compatibility Tool] e come può aiutarti con il tuo progetto Adobe Commerce.
source-git-commit: 5ff08d231269ea0bcb69f8c80aa546b171a5e4a0
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 0%

---


# Panoramica della guida

Questa guida è destinata agli amministratori e ai tecnici del software di Adobe Commerce. Include informazioni dettagliate sull&#39;installazione del [!DNL Upgrade Compatibility Tool], nonché la sua configurazione e gestione. Assume una comprensione di base della configurazione e della funzionalità principali di Commerce.

## Panoramica [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

La [!DNL Upgrade Compatibility Tool] è uno strumento a riga di comando che controlla un’istanza personalizzata di Adobe Commerce rispetto a una versione specifica analizzando tutti i moduli e il codice di base installati al suo interno. Restituisce un elenco di problemi critici, errori e avvisi che devono essere risolti prima di eseguire l’aggiornamento a una versione più recente di Adobe Commerce.

Vedi [Esegui lo strumento](../upgrade-compatibility-tool/run.md) per ulteriori informazioni.

Fai riferimento a [Installa](../upgrade-compatibility-tool/install.md) per i primi passi con [!DNL Upgrade Compatibility Tool].

Vedi questo [tutorial video](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02) per saperne di più sul [!DNL Upgrade Compatibility Tool].

### Flusso di lavoro

Il diagramma seguente mostra i possibili flussi di lavoro durante l’esecuzione del [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] Diagramma](../../assets/upgrade-guide/uct-diagram-v5.png)

### La [!DNL Upgrade Compatibility Tool] caso d&#39;uso

Il seguente caso d’uso descrive il processo tipico di un partner Adobe Commerce per aggiornare l’istanza di un client:

1. Scarica la [!DNL Upgrade Compatibility Tool] pacchetto dall’archivio Adobe Commerce (`https://repo.magento.com/`). Consulta la sezione [Scarica la [!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/install.md#download-the-upgrade-compatibility-tool) per ulteriori informazioni.
1. Esegui il [!DNL Upgrade Compatibility Tool] durante il [beta](https://devdocs.magento.com/release/beta-program.html) fase più recente [Versione Adobe Commerce](https://devdocs.magento.com/release/).
1. Genera un’istanza di vaniglia per la versione specifica di Adobe Commerce attualmente installata. Consulta la sezione [Guida collaboratore](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) per ulteriori informazioni sull&#39;utilizzo di `instance` comando per generare un&#39;installazione di vaniglia.

   >[!NOTE]
   >
   >Un’istanza di vaniglia è un’installazione pulita di un tag di versione o di un ramo specifico per una versione specifica di rilascio.

1. La [!DNL Upgrade Compatibility Tool] Identifica i problemi di aggiornamento che aiuteranno i tecnici del software a comprendere la complessità e stimare lo sforzo dell&#39;aggiornamento.
1. Queste informazioni sono condivise con le parti interessate.
1. Per l’aggiornamento verrà definito un budget e una timeline.
1. Gli ingegneri software possono quindi lavorare sulle modifiche di codice richieste per correggere i moduli interrotti.
1. La [!DNL Upgrade Compatibility Tool] può essere eseguito per tenere traccia dell’avanzamento dell’aggiornamento.
1. Tutti i controlli e l’ingegneria possono ora inviare il codice a un ambiente di staging in cui i test di regressione confermano che tutti i test sono verdi, il che consente loro di rilasciare l’ultima versione di Adobe Commerce in produzione lo stesso giorno in cui viene rilasciato il pre-rilascio di Adobe Commerce.

   ![[!DNL Upgrade Compatibility Tool] pubblico](../../assets/upgrade-guide/audience-uct-v3.png)

### Aiutare a migliorare [!DNL Upgrade Compatibility Tool]

Se hai bisogno di informazioni o hai domande che non sono incluse in questa guida, utilizza le risorse seguenti:

Per connettersi al [!DNL Upgrade Compatibility Tool] team, contattateci sul canale di Slack ingegneristico [#upgrade-compatibilità-tool](https://magentocommeng.slack.com/archives/C019Y143U9F). Vogliamo sentire i tuoi feedback, problemi e suggerimenti per aiutarci a migliorare lo strumento.

La [!DNL Upgrade Compatibility Tool] utilizza le regole definite nella [Standard di codifica](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html) per garantire che il progetto segua le best practice di Adobe Commerce e per migliorare ed estendere la [!DNL Upgrade Compatibility Tool].

Fai riferimento a [Collaborare](https://devdocs.magento.com/guides/v2.4/coding-standards/contributing.html)  argomento per ulteriori informazioni su come contribuire agli standard di codifica.

### Risorse

Abbiamo sviluppato le seguenti risorse per aiutarti a comprendere gli aggiornamenti di Adobe Commerce:

- [Guida all’aggiornamento](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html)
- [Versioni future](https://devdocs.magento.com/release/)
- [Risorse della community](https://devdocs.magento.com/community/resources/resources.html) per ulteriori informazioni.
- [Strumenti correlati](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/related-tools.html)
