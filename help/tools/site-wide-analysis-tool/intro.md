---
title: '[!DNL Site-Wide Analysis Tool]'
description: Scopri lo strumento [!DNL Site-Wide Analysis] Tool, i suoi utilizzi, il processo di installazione e come ottenere l'accesso
exl-id: 32774040-d322-43d6-9c26-c340a0ab58a9
source-git-commit: 23c5da67003ecd1939ea168a843e974b65977063
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---

# [!DNL Site-Wide Analysis Tool]

>[!IMPORTANT]
>
>A decorrere dal 23 aprile 2024, le autorizzazioni di [!DNL Site-Wide Analysis Tool] verranno rimosse per tutti i clienti Adobe Commerce on-premise.

Questa guida fornisce una panoramica olistica di [!DNL Site-Wide Analysis Tool]. Descrive gli utilizzi, le istruzioni dettagliate per l’installazione e le modalità di accesso allo strumento.

## Cos&#39;è [!DNL Site-Wide Analysis Tool]?

[!DNL Site-Wide Analysis Tool] è uno strumento proattivo self-service e un archivio centrale che include informazioni dettagliate sul sistema e raccomandazioni per garantire la sicurezza e l&#39;operabilità dell&#39;installazione di Adobe Commerce. Fornisce monitoraggio delle prestazioni in tempo reale, report e consigli 24 ore su 24, 7 giorni su 7 per identificare potenziali problemi e migliorare la visibilità delle configurazioni di salute, sicurezza e applicazioni del sito. Consente di ridurre i tempi di risoluzione e di migliorare la stabilità e le prestazioni del sito.

>[!NOTE]
>
>[!DNL Site-Wide Analysis Tool] segnala i dati a livello di sistema. Per i report su prodotti Adobe Commerce, vendite, marketing e altri dati di applicazioni commerce, consulta [Rapporti Adobe Commerce](https://experienceleague.adobe.com/it/docs/commerce-admin/start/reporting/reports-menu).

![Dashboard dello strumento di analisi a livello di sito](../../assets/tools/swat-dashboard.png){zoomable="yes"}

Per ulteriori informazioni, guarda questo [video introduttivo](https://www.youtube.com/watch?v=KW2R8ki_RG4).

## Panoramica dello strumento

- **Dashboard**
   - Mostra lo stato generale del sistema, con notifiche dei problemi rilevati e raccomandazioni specifiche per priorità.<br>
Include anche un grafico cronologico per monitorare come cambia lo stato di salute del sito web nel tempo.
   - Mostra **[!UICONTROL Security Center Widget]** che ti consente di accedere a:
      - [Tech [!DNL Stack] Conformità della versione con [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html?lang=it)
      - [Bollettino sulla sicurezza di Adobe](https://helpx.adobe.com/it/security/security-bulletin.html)
      - [Consigli da [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=it)
      - [[!DNL Site-Wide Analysis Tool] Consigli sulla sicurezza per le best practice](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html?lang=it)

- **Informazioni** - Fornisce informazioni di contatto del cliente e un riepilogo dei ticket correnti, con informazioni dettagliate su ciascun prodotto Adobe Commerce installato.

- **Recommendations** - Fornisce un [punteggio SWAT Health Index](#swat-health-index.md) per tenere traccia dello stato di integrità del sito ed elenca i consigli basati sulle best practice per risolvere i problemi rilevati sul sito:
   - Per le modifiche che richiedono un aggiornamento dell’infrastruttura, invia una richiesta di supporto.
   - Per le modifiche che richiedono un aggiornamento dell’applicazione, apporta le modifiche autonomamente.
   - Per le modifiche che richiedono un intervento manuale, ad esempio una [distribuzione del codice](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html?lang=it#deployment-workflow), richiedere assistenza all&#39;amministratore di sistema o agli sviluppatori.

- **Eccezioni** - Elenca gli errori generati dall&#39;applicazione causati da condizioni anomale senza un gestore degli errori.

- **Estensioni** - Elenca tutte le estensioni di terze parti e le librerie di terze parti.

- **Patch** - Integrato con [!DNL Quality Patches Tool], fornisce un elenco di tutte le patch disponibili specifiche per la tua istanza Adobe Commerce.

## Integrazioni con altri strumenti di supporto Adobe Commerce

Visualizza tutte le informazioni importanti sul tuo sito in un’unica posizione. [!DNL Site-Wide Analysis Tool] consente di ottenere l&#39;accesso diretto alle informazioni e da [!UICONTROL Security Center Widget], [!DNL Upgrade Compatability Tool] e [!DNL Managed Alerts].

- **[!UICONTROL Security Center Widget]** - Visualizza informazioni sulla sicurezza per il sito.<br>
Le informazioni sulla sicurezza visualizzate includono [Tech [!DNL Stack] Conformità versione con [!DNL end of life (EOL)]](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html?lang=it), [Adobe Security Bulletin](https://helpx.adobe.com/it/security/security-bulletin.html), [Recommendations from the [!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=it), and [[!DNL Site-Wide Analysis Tool] Consigli sulla sicurezza delle best practice](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/recommendations.html?lang=it).<br>
[[!DNL Security Scan Tool]](https://experienceleague.adobe.com/docs/commerce-admin/systems/security/security-scan.html?lang=it) fornisce ai clienti Adobe Commerce e Magento Open-Source informazioni in tempo reale sullo stato di sicurezza del proprio archivio rilevando in modo proattivo il malware e notificando loro se il loro archivio è compromesso.

- [**[!DNL Upgrade Compatability Tool]**](../../upgrade/upgrade-compatibility-tool/overview.md) - Esegue l&#39;istanza personalizzata di Adobe Commerce rispetto alla versione dell&#39;aggiornamento di destinazione e restituisce un riepilogo dei problemi critici, degli errori e degli avvisi che devono essere risolti, rendendo il processo di analisi dell&#39;aggiornamento più semplice, rapido e conveniente.

- [**[!DNL Managed Alerts]**](https://support.magento.com/hc/en-us/sections/360010758472-Managed-alerts-for-Adobe-Commerce) - Monitora più metriche per monitorare in modo proattivo le prestazioni della piattaforma e fornire istruzioni specifiche sulla risoluzione dei problemi in modo che gli esercenti possano evitare tempi di inattività critici e rimanere informati su CPU, prestazioni delle applicazioni, disco, memoria e database.

## A chi serve questa guida?

Commercianti e partner che desiderano avere maggiore visibilità sui loro siti web Adobe Commerce. Consente ai commercianti di migliorare l’esperienza dei clienti e di allinearsi più strettamente alle raccomandazioni sulle best practice e alle questioni fondamentali.

## Demo di [!DNL Site-Wide Analysis Tool]

Guarda questo video per saperne di più su [!DNL Site-Wide Analysis Tool]:

>[!VIDEO](https://video.tv.adobe.com/v/3410778?quality=12&captions=ita)
