---
title: Come accedere [!DNL Site-Wide Analysis Tool]
description: Scopri come accedere al [!DNL Site-Wide Analysis Tool]
source-git-commit: c7fabdd83e03a288d627b70d48cdf57184d43603
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# Accesso al [!DNL Site-Wide Analysis Tool]

La [!DNL Site-Wide Analysis Tool] il servizio è disponibile in [modalità di produzione](https://docs.magento.com/user-guide/magento/installation-modes.html) per [!DNL Admin] utenti autorizzati ad accedere all&#39;utente [risorse ruolo](https://docs.magento.com/user-guide/system/permissions-user-roles.html).

>[!NOTE]
>
>Se disponi di un’installazione on-premise di Adobe Commerce, devi installare un’ [agente](../site-wide-analysis-tool/installation.md) sull&#39;infrastruttura per utilizzare lo strumento.

![Dashboard di analisi a livello di sito](../../assets/tools/site-wide-analysis-tool-dashboard.png)
*[!DNL Site-Wide Analysis Tool]Dashboard*

## Passaggio 1: Verifica autorizzazioni

Verifica che [!DNL Admin] l&#39;account utente dispone dell&#39;autorizzazione per accedere al [!DNL Site-Wide Analysis Tool] attraverso [ruolo utente assegnato](https://docs.magento.com/user-guide/system/permissions-user-roles.html).

>[!IMPORTANT]
>
>La [!DNL Site-Wide Analysis Tool] risorsa ruolo (autorizzazione) **not** assegnati automaticamente. DEVE essere attivato per il ruolo utente e il ruolo singolarmente assegnato a ciascun account utente nel [!UICONTROL Admin].

Per il ruolo personalizzato necessario [!DNL Site-Wide Analysis Tool] accedere, effettua le seguenti operazioni:

1. Seleziona la **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]** risorsa ruolo.

   ![Dashboard di analisi a livello di sito](../../assets/tools/swat-role-access.png)
   *[!DNL Site-Wide Analysis Tool]autorizzazione selezionata per il ruolo*

1. Clic **[!UICONTROL Save Role]**.

1. Notifica agli utenti a cui è stato assegnato quel ruolo di disconnettersi [!DNL Admin]e accedi di nuovo.

>[!NOTE]
>
>Se hai verificato che l’account utente dispone dell’autorizzazione per accedere al [!DNL Site-Wide Analysis Tool] e l&#39;utente riceve un errore 403 quando cerca di accedere allo strumento dal [!DNL Admin], l’istanza di Adobe Commerce sull’infrastruttura cloud potrebbe avere il controllo degli accessi HTTP abilitato. La [!DNL Site-Wide Analysis Tool] Il dashboard NON è supportato se è abilitata l&#39;autenticazione HTTP. Per ulteriori informazioni sulla risoluzione del problema, consulta la nostra [Articolo di supporto](https://support.magento.com/hc/en-us/articles/360057400172-403-errors-when-accessing-Site-Wide-Analysis-Tool-on-Magento?_ga=2.168901729.117144580.1649172612-1623400270.1640858671).

## Passaggio 2: Accesso [!DNL Site-Wide Analysis Tool]

1. Sulla *[!UICONTROL Admin]* barra laterale, vai a **[!UICONTROL Reports]** > *[!UICONTROL System Insights]* > **[!UICONTROL Site-Wide Analysis Tool]**.

1. Leggi la sezione *Condizioni d&#39;uso* per [!DNL Site-Wide Analysis Tool] e fai clic su **[!UICONTROL Accept]** per continuare.

   Ogni utente è tenuto ad accettare i Termini d&#39;uso per la sessione. Questo passaggio viene ripetuto per ogni sessione di accesso.

   ![Dashboard di analisi a livello di sito](../../assets/tools/swat-tos.png)
   *Condizioni d&#39;uso*

1. Nella parte superiore del dashboard, fai clic sulla scheda che desideri visualizzare.

   ![Dashboard di analisi a livello di sito](../../assets/tools/swat-information-tab.png)
   *[!DNL Site-Wide Analysis Tool]informazioni*

## Passaggio 3: Genera report

1. Nell’angolo in alto a destra del dashboard, fai clic su **[!UICONTROL Generate Report]**.

1. Seleziona la casella di controllo per ogni **[!UICONTROL Type]** e **[!UICONTROL Priority]** che desideri includere nel rapporto.

1. Clic **[!UICONTROL Generate Report]**.

   ![Dashboard di analisi a livello di sito](../../assets/tools/swat-report-settings.png)
   *Impostazioni dei rapporti*

| SCHEDA | DESCRIZIONE |
| --- | --- |
| Dashboard | Mostra lo stato di salute del sistema con le notifiche e i consigli correnti per priorità. |
| Informazioni | Fornisce informazioni sui contatti dei clienti e un riepilogo dei ticket correnti, con informazioni dettagliate su ciascun prodotto Adobe Commerce installato. |
| Recommendations | Elenca i consigli in base alle best practice per risolvere i problemi rilevati sul sito. |
| Eccezioni | Elenca gli errori lanciati dall&#39;applicazione causati da condizioni anomale senza un gestore di errori. |
| Estensioni | Elenca tutte le estensioni di terze parti e le librerie di terze parti. |

>[!NOTE]
>
>Dopo aver applicato una raccomandazione, potrebbero essere necessari alcuni giorni per aggiornarla nel [!DNL Site-Wide Analysis Tool] Dashboard o report generato.
