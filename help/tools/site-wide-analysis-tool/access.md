---
title: Come accedere a  [!DNL Site-Wide Analysis Tool]
description: Scopri come accedere a  [!DNL Site-Wide Analysis Tool]
exl-id: b691fb2c-8d66-4cf9-8612-bbcb4df5b95f
source-git-commit: 18416ae29cee182a5d088069065d73814fc7d860
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# Come accedere a [!DNL Site-Wide Analysis Tool]

È possibile accedere a [!DNL Site-Wide Analysis Tool Dashboard] in due modi.

Puoi accedere a [!DNL dashboard] direttamente dal [[!DNL Site-Wide Analysis Tool] sito Web](https://supportinsights.adobe.com/commerce) **(solo per Adobe Commerce su infrastruttura cloud)** e al tuo Adobe ID oppure tramite [!DNL dashboard] dal [!DNL Admin Panel] del tuo archivio.

Il servizio [!DNL Site-Wide Analysis Tool] è disponibile in [modalità di produzione](https://docs.magento.com/user-guide/magento/installation-modes.html) per [!DNL Admin] utenti con autorizzazione di accesso all&#39;utente [risorse ruolo](https://docs.magento.com/user-guide/system/permissions-user-roles.html).

>[!NOTE]
>
>A decorrere dal 23 aprile 2024, [!DNL Site-Wide Analysis Tool] è stato disattivato e non è più disponibile per i clienti locali di Adobe Commerce.


![Dashboard di analisi a livello di sito](../../assets/tools/site-wide-analysis-tool-dashboard.png)
Dashboard *[!DNL Site-Wide Analysis Tool]*

## Opzione 1: accesso a [!DNL Site-Wide Analysis Tool Dashboard] direttamente dal dominio [!DNL Site-Wide Analysis Tool] (solo per Adobe Commerce su infrastruttura cloud)

È necessario **[!DNL Adobe ID]** per accedere a un account [!DNL Commerce].
Se si dispone già di un account [!DNL Commerce], ma non si dispone di un account [!DNL Adobe ID], è possibile crearne uno durante il processo di accesso.

1. Vai a [https://supportinsights.adobe.com/commerce](https://supportinsights.adobe.com/commerce).

1. Fare clic sul pulsante **[!UICONTROL Sign in with Adobe ID]** e seguire le istruzioni.

   ![Dashboard di analisi a livello di sito](../../assets/tools/adobe-id-login.jpg)
   Schermata di accesso *[!DNL Adobe ID]*

1. Accetta i termini e le condizioni.

1. **<u>Nota</u>:** Il tuo account deve avere diritto a **[!DNL Support Permissions]** per accedere a [!DNL Site-Wide Analysis Tool Dashboard].
Vedi ulteriori dettagli in [Condividi un [!DNL Commerce] account](https://experienceleague.adobe.com/docs/commerce-admin/start/commerce-account/commerce-account-share.html) nella nostra guida utente.

## Opzione 2: accesso a [!DNL Site-Wide Analysis Tool Dashboard] da [!DNL Admin Panel] dell&#39;archivio

### Passaggio 1: verificare le autorizzazioni

Verificare che l&#39;account utente [!DNL Admin] disponga dell&#39;autorizzazione per accedere a [!DNL Site-Wide Analysis Tool] tramite il relativo [ruolo utente assegnato](https://docs.magento.com/user-guide/system/permissions-user-roles.html).

>[!IMPORTANT]
>
>La risorsa ruolo [!DNL Site-Wide Analysis Tool] (autorizzazione) è **non** assegnata automaticamente. DEVE essere attivato per il ruolo utente e il ruolo assegnato singolarmente a ciascun account utente in [!UICONTROL Admin].

Per il ruolo personalizzato che richiede l&#39;accesso [!DNL Site-Wide Analysis Tool], eseguire le operazioni seguenti:

1. Selezionare la risorsa ruolo **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]**.

   ![Dashboard di analisi a livello di sito](../../assets/tools/swat-role-access.png)
   *[!DNL Site-Wide Analysis Tool]autorizzazione selezionata per il ruolo*

1. Fare clic su **[!UICONTROL Save Role]**.

1. Avvisa gli utenti a cui è stato assegnato il ruolo di uscire da [!DNL Admin] e accedere di nuovo.

>[!NOTE]
>
>Se si è verificato che l&#39;account utente dispone dell&#39;autorizzazione per accedere a [!DNL Site-Wide Analysis Tool] e l&#39;utente riceve un errore 403 quando tenta di accedere allo strumento da [!DNL Admin], il controllo degli accessi HTTP potrebbe essere abilitato nell&#39;istanza di Adobe Commerce sull&#39;infrastruttura cloud. Il dashboard [!DNL Site-Wide Analysis Tool] NON è supportato se è abilitata l&#39;autenticazione HTTP. Per ulteriori informazioni sulla risoluzione di questo problema, consulta l&#39;[articolo di supporto](https://support.magento.com/hc/en-us/articles/360057400172-403-errors-when-accessing-Site-Wide-Analysis-Tool-on-Magento?_ga=2.168901729.117144580.1649172612-1623400270.1640858671).

### Passaggio 2: accedere a [!DNL Site-Wide Analysis Tool]

1. Nella barra laterale *[!UICONTROL Admin]*, vai a **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]**.

   ![Dashboard di analisi a livello di sito](../../assets/tools/ac-admin-panel-marked.jpg)
   Posizione *[!DNL Site-Wide Analysis Tool]in [!DNL Admin Panel] in Adobe Commerce*

1. Leggi le *Condizioni per l&#39;utilizzo* di [!DNL Site-Wide Analysis Tool] e fai clic su **[!UICONTROL Accept]** per continuare.

   Ogni utente deve accettare le Condizioni d’uso per la sessione. Questo passaggio viene ripetuto per ogni sessione registrata.


1. Nella parte superiore del dashboard, fai clic sulla scheda che desideri visualizzare.

   ![Dashboard di analisi a livello di sito](../../assets/tools/swat-information-tab.png)
   *[!DNL Site-Wide Analysis Tool]informazioni*

## Genera report da [!DNL Site-Wide Analysis Tool Dashboard]

1. Nell&#39;angolo superiore destro del dashboard fare clic su **[!UICONTROL Generate Report]**.

1. Selezionare la casella di controllo per ogni impostazione di **[!UICONTROL Type]** e **[!UICONTROL Priority]** che si desidera includere nel report.

1. Fare clic su **[!UICONTROL Generate Report]**.

   ![Dashboard di analisi a livello di sito](../../assets/tools/swat-report-settings.png)
   *Impostazioni report*

| SCHEDA | DESCRIZIONE |
| --- | --- |
| Dashboard | Mostra l’integrità del sistema con le notifiche e i consigli correnti per priorità. |
| Informazioni | Fornisce informazioni di contatto dei clienti e un riepilogo dei ticket correnti, con informazioni dettagliate su ciascun prodotto Adobe Commerce installato. |
| Recommendations | Elenca i consigli basati sulle best practice per risolvere i problemi rilevati sul sito. |
| Eccezioni | Elenca gli errori generati dall&#39;applicazione causati da condizioni anomale senza un gestore degli errori. |
| Estensioni | Elenca tutte le estensioni e le librerie di terze parti. |

>[!NOTE]
>
>Dopo aver applicato un consiglio, potrebbero essere necessari alcuni giorni per aggiornarlo nel report [!DNL Site-Wide Analysis Tool Dashboard] o generato.
