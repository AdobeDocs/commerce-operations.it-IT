---
title: 'ACSD-46617: pulsante **[!UICONTROL Continue to Checkout]** disattivato quando il subtotale è maggiore dell''importo minimo dell''ordine configurato'
description: Applicare la patch ACSD-46617 per risolvere il problema di Adobe Commerce in cui il pulsante **[!UICONTROL Continue to Checkout]** è disattivato anche se il subtotale è maggiore dell'importo dell'ordine minimo configurato.
feature: Checkout, Orders
role: Admin
exl-id: 8e808fce-d31c-49ef-94e5-f5c89fffaa73
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8cd50456-5eb0-5364-922a-f14161feb828
    internal-label: Checkout
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 6%
---
# ACSD-46617: pulsante &quot;[!UICONTROL Continue to Checkout]&quot; disabilitato quando il subtotale è maggiore di &quot;[!UICONTROL Minimum Order Amount]&quot;

Questa patch ACSD-46617 risolve il problema in cui il pulsante **[!UICONTROL Continue to Checkout]** è disattivato anche se il subtotale è maggiore dell&#39;importo dell&#39;ordine minimo configurato. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.24. L’ID della patch è ACSD-46617. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

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
     [!UICONTROL Minimum Amount]&#x200B;: *2*

1. Crea un [!UICONTROL Cart Price Rule].
   * [!UICONTROL Coupon Code]: *[!UICONTROL TEST (optional)]*
   * [!UICONTROL Conditions]: *[!UICONTROL Keep empty]*
   * [!UICONTROL Actions]:
     * [!UICONTROL Apply]: *[!UICONTROL Percent of product price discount]*
     * &#x200B;
       [!UICONTROL Discount Amount]&#x200B;: *92*
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
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
