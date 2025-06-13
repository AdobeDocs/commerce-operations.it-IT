---
title: 'ACSD-47920: un utente guest può effettuare ordini tramite API REST anche quando [!UICONTROL Allow Guest Checkout] è disattivato'
description: Applicare la patch ACSD-47920 per risolvere il problema di Adobe Commerce, in cui è possibile effettuare ordini tramite API REST come utente guest anche quando [!UICONTROL Allow Guest Checkout] è disattivato.
feature: REST, Checkout, Orders
role: Admin
exl-id: 27c74803-a3f3-46bc-9eb8-8e2c72c30cd9
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-47920: un utente guest può effettuare ordini tramite API REST anche quando **[!UICONTROL Allow Guest Checkout]** è disattivato

La patch ACSD-47920 risolve il problema che consente di effettuare ordini tramite API REST come utente guest anche quando **[!UICONTROL Allow Guest Checkout]** è disattivato. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24. L’ID della patch è ACSD-47920. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli ordini possono essere inseriti tramite API REST come utente guest anche quando **[!UICONTROL Allow Guest Checkout]** è disattivato.

<u>Passaggi da riprodurre</u>:

1. Vai a Amministrazione Adobe Commerce > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]** > e imposta **[!UICONTROL Allow Guest Checkout]** su _No_.
1. Utilizza l’API REST per aggiungere un prodotto al carrello e effettuare un ordine.

<u>Risultati previsti</u>:

L&#39;API di estrazione guest restituisce un errore *[!UICONTROL Sorry, guest checkout is not available]* se **[!UICONTROL Allow Guest Checkout]** è impostato su _No_.

<u>Risultati effettivi</u>:

L&#39;API di estrazione guest consente di eseguire un ordine anche se **[!UICONTROL Allow Guest Checkout]** è impostato su _No_.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
