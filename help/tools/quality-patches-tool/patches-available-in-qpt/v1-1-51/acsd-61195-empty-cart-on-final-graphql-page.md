---
title: "ACSD-61195: la richiesta Cart GraphQL non restituisce gli elementi nella pagina finale"
description: Applica la patch ACSD-61195 per risolvere il problema di Adobe Commerce, per cui nell’ultima pagina della richiesta Cart GraphQL non vengono restituiti elementi del carrello.
feature: GraphQL
role: Admin, Developer
source-git-commit: f6e410e0787e56717b3910b7f3938108a7af9cd8
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# ACSD-61195: la richiesta Cart GraphQL non restituisce gli elementi nella pagina finale

La patch ACSD-61195 risolve il problema per cui non vengono restituiti elementi del carrello nell’ultima pagina della richiesta GraphQL del carrello. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=it) 1.1.51. L’ID della patch è ACSD-61195. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p1 - 2.4.7-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La richiesta Cart GraphQL non restituisce gli elementi nella pagina finale.

<u>Passaggi da riprodurre</u>:

1. Crea un nuovo carrello:

   ```
   mutation createEmptyCart($input: createEmptyCartInput) {
       createEmptyCart(input: $input)
   } 
   ```

1. Aggiungi più di cinque prodotti al carrello:

   ```
   addProductsToCart(
       cartId: "{{cartId}}"
       cartItems: [
         {
           quantity: 1
           sku: "test"
         }
       ]
     ) {
       cart {
          itemsV2 {
          items {
           product {
            name
            sku
           }
           quantity
       }
       total_count
       page_info {
         page_size
         current_page
         total_pages
       }
     }
   }
   user_errors {
     code
     message
   }
   }
   }
   ```

1. Esegui la seguente query:

   ```
   cart(cart_id: $cartId) {
   email
   itemsV2(pageSize: 2, currentPage: 3) {
       total_count
       page_info {
          page_size
          current_page
          total_pages
       }
     items {
       id
       product {
         name
         sku
       }
       quantity
       }
   }
   }  
   ```

<u>Risultati previsti</u>:

La query restituisce gli elementi dell&#39;ultima pagina.

<u>Risultati effettivi</u>:

```
  {
    "data": {
        "cart": {
            "email": "roni_cost@example.com",
            "itemsV2": {
                "total_count": 5,
                "page_info": {
                    "page_size": 2,
                    "current_page": 3,
                    "total_pages": 3
                },
                "items": []
            }
        }
    } 
    }  
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
