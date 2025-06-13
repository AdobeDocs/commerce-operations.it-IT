---
title: 'ACSD-52287: lo stato degli ordini archiviati non cambia'
description: Applicare la patch ACSD-52287 per risolvere il problema Adobe Commerce, in cui lo stato degli ordini archiviati non cambia da *completato* a *chiuso* sulla griglia dopo l'invio della nota di credito.
feature: Orders, Checkout
role: Admin, Developer
exl-id: 012f49ba-fdc1-4e1e-87fe-7b9c661f231b
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# ACSD-52287: lo stato degli ordini archiviati non cambia

La patch ACSD-52287 risolve il problema che impedisce la modifica dello stato degli ordini archiviati da *completed* a *closed* nella griglia dopo l&#39;invio della nota di credito. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.38. L’ID della patch è ACSD-52287. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Lo stato degli ordini archiviati non cambia da *completato* a *chiuso* nella griglia dopo l&#39;invio della nota di credito.

<u>Passaggi da riprodurre</u>:

1. Configura *[!UICONTROL Asynchronous Indexing]*.
   * Nella barra laterale di amministrazione, vai a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**.
   * Nel pannello a sinistra, espandi la sezione **[!UICONTROL Advanced]** e scegli **[!UICONTROL Developer]** sotto.
   * Espandere la sezione **[!UICONTROL Grid Settings]**.
   * Imposta *[!UICONTROL Asynchronous indexing]* su *Sì*.
   * Fare clic su **[!UICONTROL Save Config]**.
1. Configura *[!UICONTROL Order Archive]*.
   * Nella barra laterale di amministrazione, vai a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]**.
   * Nel pannello a sinistra, espandi la sezione **[!UICONTROL Sales]** e scegli **[!UICONTROL Sales]** sotto.
   * Espandere la sezione **[!UICONTROL Orders, Invoices, Shipments, Credit Memos Archiving]**.
   * Imposta *[!UICONTROL Enable Archiving]* su *Sì* (Lascia le altre configurazioni come predefinite).
   * Fare clic su **[!UICONTROL Save Config]**.
1. Inserisci un ordine nel front-end.
1. Eseguire [!DNL cron] per visualizzare l&#39;ordine in *[!UICONTROL Admin Order Grid]*.
1. Fatturare e spedire l&#39;ordine per aggiornare lo stato dell&#39;ordine a *Completo*.
1. Eseguire [!DNL cron] per aggiornare *[!UICONTROL Sales Order Grid]* con lo stato dell&#39;ordine più recente.
1. Archivia l’ordine.
1. Passare a *[!UICONTROL Archived order grid]*.
1. Aprire l&#39;ordine archiviato e rimborsare l&#39;ordine offline creando un [!UICONTROL Credit Memo] per rendere [!UICONTROL Order status]: *Chiuso*.
1. Esegui [!DNL cron] per alcune volte.
1. Controllare *[!UICONTROL Archived order grid]* per il nuovo stato dell&#39;ordine.

<u>Risultati previsti</u>:

L&#39;ordine viene visualizzato come *Chiuso*.

<u>Risultati effettivi</u>:

L&#39;ordine viene visualizzato come *Completo*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
