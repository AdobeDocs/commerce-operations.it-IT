---
title: "ACSD-47520: i clienti perdono punti premio quando viene creata una nota di credito"
description: Applicare la patch ACSD-47520 per risolvere il problema di Adobe Commerce, in cui i clienti perdono punti premio durante la creazione di una nota di credito.
feature: Admin Workspace, Cache, Orders, Rewards, Returns
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 0%

---

# ACSD-47520: i clienti perdono punti premio quando viene creata una nota di credito

La patch ACSD-47520 risolve il problema della perdita di punti premio da parte dei clienti al momento della creazione di una nota di credito. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.25. L’ID della patch è ACSD-47520. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.5-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I clienti perdono punti premio quando viene creata una nota di credito.

<u>Passaggi da riprodurre</u>:

1. Vai ad Adobe Commerce Admin > **[!UICONTROL Store]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Reward Points]**.
1. Modifica l&#39;impostazione:
   * **[!UICONTROL Enable Reward Points Functionality]** = _Sì_
   * **[!UICONTROL Enable Reward Points Functionality on Storefront]** = _Sì_
   * **[!UICONTROL Customers May See Reward Points History]** = _Sì_
   * **[!UICONTROL Refund Reward Points Automatically]** = _No_
   * **[!UICONTROL Deduct Reward Points from Refund Amount Automatically]** = _Sì_
1. Vai a Amministrazione > **[!UICONTROL Store]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Reward Exchange Rates]** e fai clic su **[!UICONTROL Add New Rate]**.
1. Aggiungi una nuova frequenza (1:1) ed esegui il flushing della cache.
1. Crea un cliente e aggiungi 10 punti premio a questo account.
1. Vai a Amministrazione > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL Create New Order]** > Seleziona il cliente creato nel passaggio precedente.
1. Selezionare un prodotto il cui prezzo è maggiore dei punti premio.
1. Effettuare un ordine tramite qualsiasi metodo di pagamento e i punti premio.
1. Creare una fattura per l&#39;ordine.
1. Creare una nota di credito, ma non rimborsare i punti premio.

<u>Risultati previsti</u>:

* L’Amministratore può rimborsare i punti premio.

* Lo stato dell’ordine verrà chiuso.

<u>Risultati effettivi</u>:

* Non c&#39;è modo di rimborsare i punti premio.

* Lo stato dell&#39;ordine è **[!UICONTROL Completed]**.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
