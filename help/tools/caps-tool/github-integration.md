---
title: Configurare l'integrazione GitHub per  [!DNL CAPS]
description: Scopri come installare l’app GitHub  [!DNL Cloud Automation Patching Service (CAPS)]  per abilitare le operazioni patch per i progetti Adobe Commerce Cloud connessi a GitHub.
hide: true
source-git-commit: 2887956e8644ffbcaadde36b90a0fc984369008a
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 1%

---


# Configurare l&#39;integrazione GitHub per [!DNL CAPS]

Se il progetto Adobe Commerce Cloud è connesso a un archivio GitHub, è necessario installare l&#39;app GitHub [!DNL CAPS] prima di poter utilizzare [!DNL Cloud Automation Patching Service] ([!DNL CAPS]) per applicare o ripristinare le patch. L&#39;app concede a [!DNL CAPS] l&#39;accesso necessario per apportare modifiche all&#39;archivio per tuo conto.

## Prerequisiti

* Un abbonamento Adobe Commerce Cloud attivo
* Integrazione [GitHub](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github) già configurata per il progetto Adobe Commerce Cloud, con opzione [`fetch-branches` abilitata](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github#enable-the-github-integration). [!DNL CAPS] crea e invia rami temporanei dell&#39;integrazione dell&#39;ambiente, pertanto le operazioni di patch non riescono a creare l&#39;ambiente quando questa opzione è disabilitata.
* Un archivio ospitato su [!DNL github.com]. Le integrazioni GitHub configurate con un dominio personalizzato non sono supportate.
* Accesso del proprietario o dell’amministratore all’organizzazione o all’archivio GitHub

## Installa l&#39;app GitHub [!DNL CAPS]

1. Apri la pagina di installazione dell&#39;app GitHub [CAPS](https://github.com/apps/adobe-commerce-patching-automation).
1. Fare clic su **[!UICONTROL Install]**.
1. Seleziona l’organizzazione GitHub a cui appartiene l’archivio Adobe Commerce.
1. In **[!UICONTROL Repository access]**, seleziona **[!UICONTROL Only select repositories]** e scegli l&#39;archivio per il tuo progetto Adobe Commerce.
1. Fai clic su **[!UICONTROL Install]** per confermare.

Una volta installata, [!DNL CAPS] rileva automaticamente la connessione GitHub e utilizza l&#39;app per tutte le operazioni patch. Non è richiesta alcuna ulteriore configurazione.

## Disinstalla l&#39;app GitHub [!DNL CAPS]

Se non desideri più che [!DNL CAPS] acceda al tuo archivio:

1. In GitHub, apri le impostazioni per l’account proprietario dell’installazione:
   * Per un repository **di proprietà dell&#39;organizzazione**: **[!UICONTROL Organization settings]** > **[!UICONTROL Third-party Access]** > **[!UICONTROL GitHub Apps]**.
   * Per un repository **personal**: **[!UICONTROL Settings]** > **[!UICONTROL Applications]** > **[!UICONTROL Installed GitHub Apps]**.
1. Trovare `adobe-commerce-patching-automation` e fare clic su **[!UICONTROL Configure]**.
1. Fai clic su **[!UICONTROL Uninstall]** e conferma.

>[!WARNING]
>
>Se durante la disinstallazione dell’app GitHub sono ancora in corso operazioni di applicazione o ripristino CAPS, tali operazioni potrebbero non riuscire. Dopo aver disinstallato l’app, gli utenti non possono avviare nuove operazioni perché i pulsanti di azione non sono più attivi.

## Argomenti correlati

* [Introduzione CAPS](intro.md)
* [Come accedere](access.md)
* [Panoramica del flusso di lavoro](workflow.md)
* [Best practice](best-practices.md)
* [Risoluzione dei problemi](troubleshooting.md)
