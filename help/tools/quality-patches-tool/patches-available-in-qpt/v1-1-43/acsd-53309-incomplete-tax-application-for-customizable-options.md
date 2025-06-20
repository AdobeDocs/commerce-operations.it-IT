---
title: 'ACSD-53309: applicazione fiscale incompleta per le opzioni personalizzabili e l''etichetta [!UICONTROL Regular Price]'
description: Applicare la patch ACSD-53309 per risolvere il problema di Adobe Commerce in cui l'imposta non viene applicata completamente nell'etichetta '[!UICONTROL Regular Price]' quando si seleziona un'opzione personalizzabile.
feature: Taxes, Shipping/Delivery
role: Admin, Developer
exl-id: 7f4a8923-11dd-48b2-9d97-77de5c2b24ce
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-53309: applicazione fiscale incompleta per opzioni personalizzabili ed etichetta &#39;[!UICONTROL Regular Price]&#39;

La patch ACSD-53309 risolve il problema in cui l&#39;imposta non viene applicata completamente nell&#39;etichetta &#39;[!UICONTROL Regular Price]&#39; quando viene selezionata un&#39;opzione personalizzabile. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.43. L’ID della patch è ACSD-53309. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;imposta non viene riflessa completamente nell&#39;etichetta &#39;[!UICONTROL Regular Price]&#39; quando si sceglie un&#39;opzione personalizzabile.

<u>Passaggi da riprodurre</u>:

1. Accedi al pannello di amministrazione.
1. Passa a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]** per configurare le impostazioni delle imposte.

   * [!UICONTROL Tax Classes]:

      * [!UICONTROL Tax Class for Shipping] = [!UICONTROL Taxable Goods]
      * [!UICONTROL Tax Class for Gift Options] = [!UICONTROL Taxable Goods]

   * [!UICONTROL Calculation Settings]:

      * [!UICONTROL Catalog Prices] = [!UICONTROL Including Tax]
      * [!UICONTROL Shipping Prices] = [!UICONTROL Including Tax]
      * [!UICONTROL Apply Discount On Prices] = [!UICONTROL Including Tax]

   * [!UICONTROL Default Tax Destination Calculation]:

      * [!UICONTROL Default Post Code] = *

   * [!UICONTROL Price Display Settings]:

      * [!UICONTROL Display Product Prices In Catalog] = [!UICONTROL Including Tax]
      * [!UICONTROL Display Shipping Prices] = [!UICONTROL Including Tax]

   * [!UICONTROL Shopping Cart Display Settings]:

      * [!UICONTROL Display Prices] = [!UICONTROL Including Tax]
      * [!UICONTROL Display Subtotal] = [!UICONTROL Including Tax]
      * [!UICONTROL Display Shipping Amount] = [!UICONTROL Including Tax]

1. Imposta **[!UICONTROL Shipping Settings]** > **[!UICONTROL Origin]** > **[!UICONTROL Country]** = *Regno Unito*.

1. Creare i seguenti *[!UICONTROL Tax Rate]* e *[!UICONTROL Tax Rules]*:

   * [!UICONTROL Country] = Stati Uniti
   * [!UICONTROL Zip Code] = *
   * [!UICONTROL State] = *
   * [!UICONTROL Rate] = 20%
1. Crea un prodotto semplice e imposta quanto segue:
   * [!UICONTROL Price = 110]
   * [!UICONTROL Special Price = 100]
   * Nell’elenco a discesa, imposta il tipo su opzione personalizzata con prezzo impostato al 15%
1. Vai alla pagina del prodotto per l’elemento semplice realizzato nella vetrina.
1. Scegli l&#39;opzione personalizzata creata, *15%*.

<u>Risultati previsti</u>:

* L’opzione personalizzata selezionata prevede l’applicazione di un’imposta del 20%.
* &#39;[!UICONTROL Regular Price]&#39; = 151,80.

<u>Risultati effettivi</u>:

* L&#39;imposta del 20% non viene applicata all&#39;opzione personalizzata selezionata.
* &#39;[!UICONTROL Regular Price]&#39; = 148,50.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
