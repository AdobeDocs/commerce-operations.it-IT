---
title: 'ACSD-48570: risoluzione del problema di collegamento per reimpostazione password amministratore con codice store nell’URL'
description: Applicare la patch ACSD-48570 per risolvere il problema di Adobe Commerce che impediva l'accesso alla pagina di reimpostazione della password tramite il collegamento della password di reimpostazione dell'amministratore quando la configurazione [!UICONTROL Add Store Code to URLs] era abilitata.
feature: Security, User Account
role: Admin, Developer
source-git-commit: a9d7f4f4c2f2e27ff9571de08bcec918b4605b03
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-48570: risoluzione del problema di collegamento per reimpostazione password amministratore con codice store nell’URL

La patch ACSD-48570 per risolvere il problema di Adobe Commerce che impediva l&#39;accesso alla pagina per la reimpostazione della password tramite il collegamento per la reimpostazione della password amministratore quando la configurazione *[!UICONTROL Add Store Code to URLs]* era abilitata. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58. L’ID della patch è ACSD-48570. Il problema è stato risolto in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando l&#39;impostazione **[!UICONTROL Add Store Code to URLs]** è attivata, la funzionalità di reimpostazione password dell&#39;amministratore non funziona correttamente.
Quando un utente amministratore richiede una reimpostazione della password e fa clic sul collegamento di ripristino nell’e-mail, viene reindirizzato alla pagina di accesso o riceve un errore 404 invece di essere reindirizzato al modulo di reimpostazione della password. In questo modo gli amministratori non potranno recuperare i propri account senza alcun intervento manuale.

<u>Passaggi da riprodurre</u>:

1. Abilita la configurazione **[!UICONTROL Add Store Code to URLs]** in **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** > **[!UICONTROL URL Options]**.
1. Disconnettersi dal pannello di amministrazione e fare clic sul collegamento **[!UICONTROL Forgot your password?]** nella pagina di accesso di amministrazione.
1. Immettere l&#39;indirizzo e-mail dell&#39;utente amministratore, passare il captcha e fare clic su **[!UICONTROL Retrieve Password]**.
1. Apri l’e-mail di reimpostazione della password e fai clic sul collegamento di recupero della password.

<u>Risultati previsti</u>:

Viene visualizzato il modulo per reimpostare la password.

<u>Risultati effettivi</u>:

Al posto del modulo di reimpostazione della password viene visualizzata la pagina di accesso o una pagina di errore 404.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
