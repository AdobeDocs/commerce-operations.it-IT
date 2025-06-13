---
title: 'MDVA-43862: impossibile aggiornare gli elementi del carrello a causa di un errore di mutazione di GraphQL UpdateCartItems'
description: La patch MDVA-43862 risolve il problema che impedisce al cliente di aggiornare gli elementi del carrello a causa di un errore di mutazione di GraphQL UpdateCartItems. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13. L'ID della patch è MDVA-43862. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
feature: GraphQL, Orders, Shopping Cart
role: Admin
exl-id: d8a2579f-58f5-4407-8006-d58794a84b1f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-43862: impossibile aggiornare gli elementi del carrello a causa di un errore di mutazione di GraphQL UpdateCartItems

La patch MDVA-43862 risolve il problema che impedisce al cliente di aggiornare gli elementi del carrello a causa di un errore di mutazione di GraphQL UpdateCartItems. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.13. L&#39;ID della patch è MDVA-43862. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1, 2.4.2-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.3 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il cliente non può aggiornare gli articoli del carrello a causa di un errore di mutazione di GraphQL UpdateCartItems.

<u>Passaggi da riprodurre</u>:

1. Creare un prodotto configurabile (MH01) assegnando un semplice (MH01-XL-Gray).
1. Vai a Amministrazione Commerce > **Catalogo** > **Prodotti** > **SKU** > **MH01** > **Opzioni personalizzabili**.
1. Aggiungi un’opzione personalizzata al prodotto.
   * Titolo opzione: Opzione1
   * Tipo di opzione: Campo
   * Obbligatorio: sì
   * Prezzo: 10.00
   * Tipo di prezzo: fisso
   * SKU: MHC1
   * Numero massimo di caratteri: 25
1. Esegui la query GraphQL seguente per generare l’ID carrello.

   ```GraphQL
   mutation {
     createEmptyCart
   }
   ```

1. Prendi nota del codice ID del carrello.
1. Esegui la query seguente per aggiungere al carrello un prodotto configurabile:

   ```GraphQL
   mutation {
   addConfigurableProductsToCart(
   input: {
       cart_id: "<cart ID from above step>",
       cart_items: [{
       parent_sku: "MH01",
       data: {
           quantity: 1,
           sku: "MH01-XL-Gray"
           },
           customizable_options: {
               id: 1,
               value_string: "2"
               }
           }
       ]
   }
   )
   {
   cart {
     items {
       uid
       quantity
       product {
         name
         sku
       }
       ... on ConfigurableCartItem {
         configurable_options {
           option_label
         }
       }
     }
   }
   }
   }
   ```

1. Noterai che il carrello è compilato con l’articolo configurabile.
1. Prendi nota dell’UID restituito.
1. Esegui nuovamente la query seguente per aggiornare l’elemento del carrello.

   ```GraphQL
   mutation {
     updateCartItems(
       input: {
         cart_id: "<cart ID from previous step>",
         cart_items: [
           {
             cart_item_uid: "<uid from previous step>"
             quantity: 3,
             customizable_options:[{
                 id: 1,
                 value_string: "67"
             }]
           }
         ]
       }
     ){
       cart {
         items {
           uid
           product {
             name
           }
           quantity
         }
         prices {
           grand_total{
             value
             currency
           }
         }
       }
     }
   }
   ```

1. Osserva la risposta.

<u>Risultati previsti</u>:

Il carrello viene aggiornato senza alcun problema.

<u>Risultati effettivi</u>:

Viene visualizzato il seguente errore:

```GraphQL
{
  "errors": [
    {
      "message": "Could not update cart item: You need to choose options for your item.",
      "extensions": {
        "category": "graphql-input"
      },
      "locations": [
        {
          "line": 2,
          "column": 3
        }
      ],
      "path": [
        "updateCartItems"
      ]
    }
  ],
  "data": {
    "updateCartItems": null
  }
}
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
