---
title: Come accedere a  [!DNL Adobe Commerce Patching Automation]
description: Scopri come accedere a e utilizzare  [!DNL Adobe Commerce Patching Automation]
hide: true
source-git-commit: 1f92a1542c77954f10aa4c14de54f090581f9330
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 1%

---

# Come accedere a [!DNL Adobe Commerce Patching Automation]

## Prerequisiti

[!DNL Patching Automation] utilizza il controllo degli accessi basato sul ruolo di Adobe Commerce Cloud. Il tuo livello di accesso nella Cloud Console determina cosa puoi fare con il servizio.

### Chi può utilizzare [!DNL Patching Automation]

* **Amministratore progetto** - Può applicare o ripristinare le patch in tutti gli ambienti
* **Collaboratore** - È possibile applicare o ripristinare le patch negli ambienti assegnati
* **Visualizzatore** - Può solo visualizzare il progetto e gli ambienti, nessuna azione consentita

### Richiedere l’accesso a un progetto

Se nell&#39;interfaccia utente di [!DNL Patching Automation] non è presente alcun progetto, richiedere l&#39;accesso alla persona appropriata:

* Contatta il proprietario dell’account o l’amministratore del progetto
* Ti assegneranno il ruolo appropriato tramite Cloud Console
* Una volta ottenuto l’accesso, puoi accedere alla Cloud Console per utilizzare il servizio

>[!NOTE]
>
>[!DNL Patching Automation] segue lo stesso modello di autorizzazione di Adobe Commerce Cloud, pertanto il tuo livello di accesso alla console Cloud determina cosa puoi fare con il servizio.

## Accesso a [!DNL Patching Automation]

[!DNL Patching Automation] è disponibile come scheda nel dashboard [!DNL Site-Wide Analysis Tool]. Puoi accedervi dal tuo pannello di amministrazione andando in **Rapporti** > **Informazioni di sistema** > **Strumento di analisi a livello di sito** nella barra laterale di amministrazione. Consulta [Come accedere allo strumento di analisi a livello di sito](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/site-wide-analysis-tool/access) per i prerequisiti e la configurazione delle autorizzazioni.

Una volta nella dashboard:

1. Fare clic sulla scheda [!UICONTROL Patching Automation] nell&#39;interfaccia.
1. Selezionare il progetto e l&#39;ambiente in cui applicare le patch.
1. Verificare le patch disponibili e il relativo stato di compatibilità.
1. Selezionare le patch da applicare o ripristinare.

## Accesso all’ambiente di produzione

Per gli ambienti di produzione, si applicano per impostazione predefinita ulteriori salvaguardie:

* **Modalità manutenzione** - Deve essere abilitata
* **Processi Cron** - Devono essere disabilitati
* **Finestra di dialogo di conferma** - Deve essere completata prima di procedere

>[!IMPORTANT]
>
>L&#39;applicazione delle patch nell&#39;ambiente di produzione richiede una preparazione e misure di protezione adeguate per evitare interruzioni accidentali.

>[!NOTE]
>
>È possibile ignorare i controlli in modalità manutenzione e cron-job selezionando la casella di controllo di esclusione nell&#39;interfaccia utente (*[!UICONTROL I want to skip maintenance mode and cron checks before applying patches to production environment]*). Utilizzatelo solo se comprendete il rischio di applicare patch alla produzione senza tali protezioni in atto.

## Argomenti correlati

* [Introduzione all’automazione dell’applicazione di patch](intro.md)
* [Panoramica del flusso di lavoro](workflow.md)
* [Integrazione GitHub](github-integration.md)
* [Best practice](best-practices.md)
* [Risoluzione dei problemi](troubleshooting.md)
