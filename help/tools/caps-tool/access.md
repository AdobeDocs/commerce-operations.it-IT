---
title: Come accedere a  [!DNL Cloud Automation Patching Service (CAPS)]
description: Scopri come accedere a e utilizzare  [!DNL Cloud Automation Patching Service (CAPS)]
hide: true
hidefromtoc: true
source-git-commit: ca388bd78affd4def19a5539d8529f2563d35e8c
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 1%

---

# Come accedere a [!DNL Cloud Automation Patching Service (CAPS)]

## Prerequisiti

[!DNL CAPS] utilizza il controllo degli accessi basato sul ruolo di Adobe Commerce Cloud. Il tuo livello di accesso nella Cloud Console determina le operazioni possibili con [!DNL CAPS].

### Chi può utilizzare [!DNL CAPS]

* **Amministratore progetto** - Può applicare o ripristinare le patch in tutti gli ambienti
* **Collaboratore** - È possibile applicare o ripristinare le patch negli ambienti assegnati
* **Visualizzatore** - Può solo visualizzare il progetto e gli ambienti, nessuna azione consentita

### Richiedere l’accesso a un progetto

Se nell&#39;interfaccia utente di [!DNL CAPS] non sono presenti progetti, è necessario richiedere l&#39;accesso alla persona appropriata:

* Contatta il proprietario dell’account o l’amministratore del progetto
* Ti assegneranno il ruolo appropriato tramite Cloud Console
* Una volta ottenuto l&#39;accesso, puoi accedere alla console cloud per utilizzare [!DNL CAPS]

>[!NOTE]
>
>[!DNL CAPS] segue lo stesso modello di autorizzazione di Adobe Commerce Cloud, pertanto il tuo livello di accesso nella console Cloud determina cosa puoi fare con [!DNL CAPS].

## Accesso a [!DNL CAPS]

Lo strumento CAPS è disponibile nel dashboard dello strumento di analisi a livello di sito all&#39;indirizzo [https://supportinsights.adobe.com/commerce/](https://supportinsights.adobe.com/commerce/). Nella scheda Automazione applicazione di patch è possibile selezionare il progetto e l&#39;ambiente.

1. Passa a Strumento di analisi a livello di sito all&#39;indirizzo [https://supportinsights.adobe.com/commerce/](https://supportinsights.adobe.com/commerce/).
1. Fare clic sulla scheda [!UICONTROL Patching Automation] nell&#39;interfaccia.
1. Selezionare il progetto e l&#39;ambiente in cui applicare le patch.
1. Verificare le patch disponibili e il relativo stato di compatibilità.
1. Selezionare le patch da applicare o ripristinare.

## Accesso all’ambiente di produzione

Per gli ambienti di produzione, si applicano ulteriori salvaguardie:

* **Modalità manutenzione** - Deve essere abilitata
* **Processi Cron** - Devono essere disabilitati
* **Finestra di dialogo di conferma** - Deve essere completata prima di procedere

>[!IMPORTANT]
>
>L&#39;applicazione delle patch nell&#39;ambiente di produzione richiede una preparazione e misure di protezione adeguate per evitare interruzioni accidentali.

## Argomenti correlati

* [Introduzione CAPS](intro.md)
* [Flusso di lavoro](workflow.md)
* [Best practice](best-practices.md)
* [Risoluzione dei problemi](troubleshooting.md)
