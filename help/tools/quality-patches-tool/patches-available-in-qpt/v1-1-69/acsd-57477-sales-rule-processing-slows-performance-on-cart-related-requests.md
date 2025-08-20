---
title: 'ACSD-57477: l’elaborazione delle regole di vendita rallenta le prestazioni sulle richieste relative al carrello'
description: Applica la patch ACSD-57477 per risolvere il problema di Adobe Commerce in cui, in un progetto con molti attributi di prodotto disponibili (ad esempio, 1000 attributi), quando l’operazione AddProductsToCart GraphQL viene eseguita con variabili, Commerce tenta di caricare tutti questi attributi di prodotto e causa problemi di prestazioni lente dall’operazione AddProductsToCart GraphQL.
feature: GraphQL, Shopping Cart
role: Admin, Developer
type: Troubleshooting
source-git-commit: 00fce49fbe5432a16324937e0430a08ec7c41188
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---


# ACSD-57477: l’elaborazione delle regole di vendita rallenta le prestazioni sulle richieste relative al carrello

La patch ACSD-57477 risolve il problema che causa un rallentamento delle prestazioni nelle richieste relative al carrello. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69. L’ID della patch è ACSD-57477. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p11

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’elaborazione delle regole di vendita rallenta le prestazioni nelle richieste relative al carrello se invii i parametri come variabili GraphQL.

<u>Passaggi da riprodurre</u>:

1. Aggiungi 1000 attributi di prodotto.
1. Crea un carrello utilizzando la query GraphQL di seguito.

   ```
   mutation {createEmptyCart}{noformat}
   ```

1. Aggiungi un prodotto al carrello utilizzando la query GraphQL di seguito.

   ```
   mutation AddProductsToCart($cartId: String!, $products: [CartItemInput!]!) {
       addProductsToCart(cartId: $cartId, cartItems: $products) {
         cart {
           id
           __typename
         }
         __typename
       }
     }
   ```

1. Imposta queste variabili.

   ```
   {
     "cartId": "id_here",
     "products": [
       {
         "sku": "product_dynamic_1",
         "parent_sku": "product_dynamic_1",
         "quantity": 1
       }
     ]
   }
   ```

1. Questo problema si verifica solo quando si inviano i parametri come variabili di GraphQL. Se includi i parametri nella query GraphQL stessa, questo problema non si verifica.
1. Invia la stessa richiesta **Aggiungi al carrello** dopo aver aggiunto i parametri alla query GraphQL stessa.

   ```
   mutation {
    addProductsToCart(
      cartId: "id_here"
      cartItems:  [
       {
         sku: "product_dynamic_1",
         parent_sku: "product_dynamic_1",
         quantity: 1
       }
     ]
    ) {
      cart {
           id
           __typename
         }
         __typename
    }
   }
   ```

<u>Risultati previsti</u>:

Le prestazioni dell&#39;operazione GraphQL `AddProductsToCart` non devono essere ridotte.

<u>Risultati effettivi</u>:

Le prestazioni dell&#39;operazione GraphQL `AddProductsToCart` peggiorano perché vengono caricati tutti gli attributi del prodotto quando i parametri vengono inviati come variabili.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool]
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti
