---
title: 'ACSD-52160: risultato della convalida del prodotto rispetto alla regola del prezzo del carrello'
description: Applicare la patch ACSD-52160 per risolvere il problema di Adobe Commerce in cui il risultato della convalida del prodotto rispetto alla regola prezzo carrello non viene valutato correttamente in base alla condizione regola *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*.
exl-id: 8f8799c9-850a-4c8f-bde4-68df64e46c85
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '373'
ht-degree: 0%

---

# ACSD-52160: il risultato della convalida del prodotto in base alla regola del prezzo del carrello non viene valutato correttamente

La patch ACSD-52160 risolve il problema per cui il risultato della convalida del prodotto rispetto alla regola del prezzo del carrello non viene valutato correttamente in base alla condizione della regola *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.34. L’ID della patch è ACSD-52160. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il risultato della convalida del prodotto rispetto alla regola del prezzo del carrello non è stato valutato correttamente in base alla condizione della regola *[!UICONTROL If an item is FOUND/NOT FOUND in the cart with All/Any of these conditions true]*.

<u>Passaggi da riprodurre</u>:

1. Crea due prodotti assegnati a due diverse categorie.
1. Crea un **[!UICONTROL Cart Price Rule]** con condizioni come:

   * **SKU 1** nel parametro *[!UICONTROL FOUND]*
   * **SKU 2** nel parametro *[!UICONTROL NOT FOUND]*

1. Aggiungi entrambi i prodotti al carrello.
1. Applica il codice del coupon.

<u>Risultati previsti</u>

Il codice coupon non viene applicato in quanto il carrello contiene prodotti della categoria con restrizioni.

<u>Risultati effettivi</u>

Il codice del coupon viene applicato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it>) nella guida di [!DNL Quality Patches Tool].
