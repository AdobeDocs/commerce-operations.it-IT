---
title: Configurare l'integrazione GitHub per  [!DNL Adobe Commerce Patching Automation]
description: Scopri come installare l’app GitHub  [!DNL Adobe Commerce Patching Automation]  per abilitare le operazioni patch per i progetti Adobe Commerce Cloud connessi a GitHub.
hide: true
source-git-commit: 1f92a1542c77954f10aa4c14de54f090581f9330
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%

---


# Configurare l&#39;integrazione GitHub per [!DNL Patching Automation]

Se il progetto Adobe Commerce Cloud è connesso a un archivio GitHub, è necessario installare l&#39;app GitHub [!DNL Patching Automation] prima di poter utilizzare il servizio per applicare o ripristinare le patch. L’app concede al servizio l’accesso necessario per apportare modifiche all’archivio per tuo conto.

## Prerequisiti

* Un abbonamento Adobe Commerce Cloud attivo
* Integrazione [GitHub](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github) già configurata per il progetto Adobe Commerce Cloud, con opzione [`fetch-branches` abilitata](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/dev-tools/integrations/github#enable-the-github-integration). [!DNL Patching Automation] crea e invia rami temporanei dell&#39;integrazione dell&#39;ambiente, pertanto le operazioni di patch non riescono a creare l&#39;ambiente quando questa opzione è disabilitata.
* Un archivio ospitato su [!DNL github.com]. Le integrazioni GitHub configurate con un dominio personalizzato non sono supportate.
* Accesso del proprietario o dell’amministratore all’organizzazione o all’archivio GitHub

## Installa l&#39;app GitHub [!DNL Patching Automation]

È possibile avviare l&#39;installazione da [!DNL Patching Automation] facendo clic su **[!UICONTROL Install GitHub App]** nell&#39;interfaccia utente, che reindirizza l&#39;utente alla pagina di installazione, oppure passando direttamente alla pagina di installazione.

1. Aprire la [pagina di installazione dell&#39;app GitHub di automazione patch](https://github.com/apps/adobe-commerce-patching-automation).
1. Fare clic su **[!UICONTROL Install]**.
1. Seleziona l’organizzazione GitHub a cui appartiene l’archivio Adobe Commerce.
1. In **[!UICONTROL Repository access]**, seleziona **[!UICONTROL Only select repositories]** e scegli l&#39;archivio per il tuo progetto Adobe Commerce.
1. Fai clic su **[!UICONTROL Install]** per confermare.

Una volta installato, il servizio rileva automaticamente la connessione GitHub e utilizza l’app per tutte le operazioni patch. Non è richiesta alcuna ulteriore configurazione.

## Controllare e gestire lo stato della connessione

L&#39;interfaccia utente di [!DNL Patching Automation] mostra lo stato corrente della connessione GitHub, con le azioni disponibili a seconda di tale stato:

* **[!UICONTROL Refresh]** / **[!UICONTROL Refresh status]** - Controlla nuovamente lo stato della connessione senza apportare modifiche.
* **[!UICONTROL Reinstall]** - Indica se l&#39;installazione non è più valida (ad esempio, se è stata sospesa o se l&#39;archivio connesso al progetto Cloud è stato modificato). Avvia lo stesso flusso di installazione descritto in precedenza.
* **[!UICONTROL Unlink GitHub App]** - Rimuove la connessione salvata di [!DNL Patching Automation] all&#39;app GitHub. **not** disinstalla l&#39;app dall&#39;archivio GitHub. Per rimuovere completamente l&#39;accesso, vedi la sezione Disinstalla di seguito.

## Disinstalla l&#39;app GitHub [!DNL Patching Automation]

Se non desideri più che il servizio acceda al tuo archivio:

1. In GitHub, apri le impostazioni per l’account proprietario dell’installazione:
   * Per un repository **di proprietà dell&#39;organizzazione**: **[!UICONTROL Organization settings]** > **[!UICONTROL Third-party Access]** > **[!UICONTROL GitHub Apps]**.
   * Per un repository **personal**: **[!UICONTROL Settings]** > **[!UICONTROL Applications]** > **[!UICONTROL Installed GitHub Apps]**.
1. Trovare `adobe-commerce-patching-automation` e fare clic su **[!UICONTROL Configure]**.
1. Fai clic su **[!UICONTROL Uninstall]** e conferma.

>[!WARNING]
>
>Se al momento della disinstallazione dell’app GitHub sono ancora in corso operazioni di applicazione o ripristino, tali operazioni potrebbero non riuscire. Dopo aver disinstallato l’app, gli utenti non possono avviare nuove operazioni perché i pulsanti di azione non sono più attivi.

## Argomenti correlati

* [Introduzione all’automazione dell’applicazione di patch](intro.md)
* [Come accedere](access.md)
* [Panoramica del flusso di lavoro](workflow.md)
* [Best practice](best-practices.md)
* [Risoluzione dei problemi](troubleshooting.md)
