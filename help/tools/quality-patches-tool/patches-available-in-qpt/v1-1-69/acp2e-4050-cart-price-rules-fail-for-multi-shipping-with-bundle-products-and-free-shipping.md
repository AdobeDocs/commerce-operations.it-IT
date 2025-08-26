---
title: 'ACP2E-4050: [!UICONTROL Free Shipping] non applicato con il pagamento multi-shipping'
description: Applicare la patch ACP2E-4050 per risolvere il problema di Adobe Commerce per cui [!UICONTROL Free Shipping] non viene applicato durante l'estrazione con più indirizzi quando [!UICONTROL Cart Price Rules] include condizioni di selezione secondaria e prodotti con prezzi specifici.
feature: Shopping Cart, Shipping/Delivery
role: Admin, Developer
type: Troubleshooting
source-git-commit: d36ce39fcd897261b784d57f8806b3eceb66fc01
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---


# ACP2E-4050: **[!UICONTROL Free Shipping]** non applicato con il pagamento multi-shipping

La patch ACP2E-4050 risolve il problema in cui **[!UICONTROL Free Shipping]** non viene applicato durante il pagamento di più spedizioni quando **[!UICONTROL Cart Price Rules]** include condizioni di selezione secondaria e prodotti con prezzi specifici. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69. L’ID della patch è ACP2E-4050. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p10

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.7-p6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

**[!UICONTROL Free Shipping]** non viene applicato durante il pagamento con spedizione multipla quando **[!UICONTROL Cart Price Rules]** include condizioni di selezione secondaria e prodotti con prezzi specifici.

<u>Passaggi da riprodurre</u>:

1. Creare un conto cliente con due indirizzi.
1. Abilita **[!UICONTROL Free Shipping]** e imposta **[!UICONTROL Minimum Order Amount]** su *999999*.
1. Passa a [!UICONTROL Admin] > [!UICONTROL Marketing] > [!UICONTROL Cart Price Rules] e crea una regola del prezzo del carrello con le seguenti condizioni:

```
If ALL of these conditions are TRUE:
 * Subtotal is at least 50
 * The subtotal is at most 500
 * Apply this condition if the total amount is 50 or more for a subset of cart items that meet all specified criteria:
 * Category is 23
```

1. Installa dati di esempio.
1. Aggiungi i seguenti prodotti al carrello nell’ordine specificato:
   * Borsa Messenger Wayfarer
   * Olivia 1/4 Zip Giacca leggera
   * Sprite Yoga Companion Kit.
1. Aprire il carrello e verificare che l&#39;opzione **[!UICONTROL Free Shipping]** sia disponibile.
1. Fare clic su **[!UICONTROL Check Out with Multiple Addresses]**.
1. Seleziona un indirizzo di spedizione diverso per il prodotto semplice.
1. Fare clic su **[!UICONTROL Go to Shipping Information]**.

<u>Risultati previsti</u>:

**[!UICONTROL Free Shipping]** si applica alle spedizioni di prodotti configurabili e in bundle.

<u>Risultati effettivi</u>:

**[!UICONTROL Free Shipping]** non è disponibile.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
