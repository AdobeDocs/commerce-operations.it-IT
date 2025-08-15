---
title: 'ACSD-46617: pulsante **[!UICONTROL Continue to Checkout]** disattivato quando il subtotale è maggiore dell''importo minimo dell''ordine configurato'
description: Applicare la patch ACSD-46617 per risolvere il problema di Adobe Commerce in cui il pulsante **[!UICONTROL Continue to Checkout]** è disattivato anche se il subtotale è maggiore dell'importo dell'ordine minimo configurato.
feature: Checkout, Orders
role: Admin
exl-id: 8e808fce-d31c-49ef-94e5-f5c89fffaa73
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-46617: pulsante &quot;[!UICONTROL Continue to Checkout]&quot; disabilitato quando il subtotale è maggiore di &quot;[!UICONTROL Minimum Order Amount]&quot;

Questa patch ACSD-46617 risolve il problema in cui il pulsante **[!UICONTROL Continue to Checkout]** è disattivato anche se il subtotale è maggiore dell&#39;importo dell&#39;ordine minimo configurato. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24. L’ID della patch è ACSD-46617. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il pulsante **[!UICONTROL Continue to Checkout]** è disattivato anche se il subtotale è maggiore dell&#39;importo minimo dell&#39;ordine configurato.

<u>Passaggi da riprodurre</u>:

1. Vai a Adobe Commerce Admin > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Minimum Order Amount]** e imposta quanto segue:
   * [!UICONTROL Enable]: *[!UICONTROL Yes]*
   * &#x200B;
     [!UICONTROL Minimum Amount]: *2*

1. Crea un [!UICONTROL Cart Price Rule].
   * [!UICONTROL Coupon Code]: *[!UICONTROL TEST (optional)]*
   * [!UICONTROL Conditions]: *[!UICONTROL Keep empty]*
   * [!UICONTROL Actions]:
      * [!UICONTROL Apply]: *[!UICONTROL Percent of product price discount]*
      * &#x200B;
        [!UICONTROL Discount Amount]: *92*
      * [!UICONTROL Apply to Shipping Amount]: *[!UICONTROL Yes]*
1. Crea un prodotto al prezzo di 25 $.
1. Aggiungi il prodotto al carrello.
1. Vai al carrello, seleziona il metodo $5 **[!UICONTROL Flat Rate shipping]** e applica il codice del coupon.
1. Passare al checkout, completare la spedizione e passare alla sezione **[!UICONTROL Paytment]**.
1. Torna al carrello.

<u>Risultati previsti</u>:

Non c&#39;è alcun errore relativo all&#39;importo minimo dell&#39;ordine in quanto il totale complessivo di $ 2,4 è maggiore dell&#39;importo richiesto di $ 2.

<u>Risultati effettivi</u>:

* Si è verificato un errore relativo all’importo minimo dell’ordine anche quando il totale complessivo di 2,4 $ è maggiore dell’importo minimo dell’ordine di 2 $.
* Il pulsante **[!UICONTROL Continue to Checkout]** è disattivato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
