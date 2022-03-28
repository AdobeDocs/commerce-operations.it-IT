---
title: Panoramica [!DNL Upgrade Compatibility Tool]
description: Scopri le [!DNL Upgrade Compatibility Tool] e come può aiutarti con il tuo progetto Adobe Commerce.
source-git-commit: fbe47245623469a93cce5cc5a83baf467a007bc4
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Panoramica [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

La [!DNL Upgrade Compatibility Tool] è uno strumento a riga di comando che controlla un’istanza personalizzata di Adobe Commerce rispetto a una versione specifica analizzando tutti i moduli e il codice di base installati al suo interno. Restituisce un elenco di problemi critici, errori e avvisi che devono essere risolti prima di eseguire l’aggiornamento alla versione più recente di Adobe Commerce. Identifica anche i potenziali problemi che devono essere risolti nel codice prima di tentare di eseguire l&#39;aggiornamento a una versione più recente di Adobe Commerce.

La [!DNL Upgrade Compatibility Tool] consente di identificare quando sono state apportate modifiche al codice di base alle funzionalità personalizzate. Consulta la sezione [Esegui lo strumento](../upgrade-compatibility-tool/run.md) per ulteriori informazioni.

Viene distribuito come pacchetto Composer con ogni versione di una versione di Adobe Commerce. Consulta la sezione [Sviluppatore](../upgrade-compatibility-tool/developer.md) per ulteriori informazioni.

Fai riferimento a [Installa](../upgrade-compatibility-tool/install.md) argomento per i primi passi con [!DNL Upgrade Compatibility Tool].

## Flusso di lavoro

Il diagramma seguente mostra il flusso di lavoro previsto durante l’esecuzione del [!DNL Upgrade Compatibility Tool]:

![[!DNL Upgrade Compatibility Tool] Diagramma](../../assets/upgrade-guide/mvp-diagram-v3.png)

## La [!DNL Upgrade Compatibility Tool] caso d&#39;uso

Il seguente caso d’uso descrive il processo tipico di un partner Adobe Commerce per aggiornare l’istanza di un client:

1. Scarica la [!DNL Upgrade Compatibility Tool] pacchetto dall’archivio Adobe Commerce (`https://repo.magento.com/`). Consulta la sezione [Scarica la [!DNL Upgrade Compatibility Tool]](../upgrade-compatibility-tool/install.md#download-the-upgrade-compatibility-tool) per ulteriori informazioni.
1. Esegui il [!DNL Upgrade Compatibility Tool] durante il [beta](https://devdocs.magento.com/release/beta-program.html) fase più recente [Versione Adobe Commerce](https://devdocs.magento.com/release/).
1. Il comando principale è `upgrade:check`. Questo comando analizza l’istanza e controlla la presenza di errori, avvisi e problemi critici nell’istanza. Per ottimizzare i risultati:

   - Opzione Aggiungi `--ignore-current-version-compatibility-issues` per ignorare tutti i problemi critici noti, gli errori e gli avvisi relativi alla versione corrente di Adobe Commerce. Mostra solo i risultati della versione desiderata.
   - Opzione Usa `--min-issue-level` per impostare il livello minimo di problema. Consente di assegnare priorità solo ai problemi più importanti con l’aggiornamento. Se si desidera analizzare solo un determinato fornitore, modulo o persino directory, è possibile specificare anche il percorso. Consulta la sezione [Esegui lo strumento](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/run.html?lang=en) per ulteriori dettagli.

1. Genera un’istanza di vaniglia per la versione specifica di Adobe Commerce attualmente installata. Consulta la sezione [Guida collaboratore](https://devdocs.magento.com/contributor-guide/contributing.html#vanilla-pr) per ulteriori informazioni sull&#39;utilizzo di `instance` comando per generare un&#39;installazione di vaniglia.

   >[!NOTE]
   >
   >Un’istanza di vaniglia è un’installazione pulita di un tag di versione o di un ramo specifico per una versione specifica di rilascio.

1. La [!DNL Upgrade Compatibility Tool] Identifica le aree interrotte personalizzate. Il tecnico del software è in grado di comprendere la complessità e stimare lo sforzo dell&#39;aggiornamento. Queste informazioni sono condivise con le parti interessate.
1. Per l’aggiornamento verrà definito un budget e una timeline.
1. Gli ingegneri software possono quindi lavorare sulle modifiche di codice richieste per correggere i moduli interrotti.
1. La [!DNL Upgrade Compatibility Tool] può essere eseguito per tenere traccia dell’avanzamento dell’aggiornamento.
1. Tutti i controlli e l’ingegneria possono ora inviare il codice a un ambiente di staging in cui i test di regressione confermano che tutti i test sono verdi, il che consente loro di rilasciare l’ultima versione di Adobe Commerce in produzione lo stesso giorno in cui viene rilasciato il pre-rilascio di Adobe Commerce.

   ![[!DNL Upgrade Compatibility Tool] pubblico](../../assets/upgrade-guide/audience-uct-v3.png)

## Aiutare a migliorare [!DNL Upgrade Compatibility Tool]

Per connettersi al [!DNL Upgrade Compatibility Tool] team, contattateci sul canale di Slack ingegneristico [[!DNL Upgrade Compatibility Tool]](https://magentocommeng.slack.com/archives/C019Y143U9F). Vogliamo sentire i tuoi feedback, problemi e suggerimenti per aiutarci a migliorare lo strumento.

La [!DNL Upgrade Compatibility Tool] utilizza le regole definite nella [Standard di codifica](https://devdocs.magento.com/guides/v2.4/coding-standards/bk-coding-standards.html) per garantire che il progetto segua le best practice di Adobe Commerce e per migliorare ed estendere la [!DNL Upgrade Compatibility Tool].

Fai riferimento a [Collaborare](https://devdocs.magento.com/guides/v2.4/coding-standards/contributing.html)  per ulteriori informazioni sul contributo a questo progetto.

## Risorse

Abbiamo sviluppato le seguenti risorse per aiutarti a comprendere gli aggiornamenti di Adobe Commerce:

- [Guida all’aggiornamento](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/overview.html)
- [Versioni future](https://devdocs.magento.com/release/)
- [Risorse della community](https://devdocs.magento.com/community/resources/resources.html) per ulteriori informazioni.
