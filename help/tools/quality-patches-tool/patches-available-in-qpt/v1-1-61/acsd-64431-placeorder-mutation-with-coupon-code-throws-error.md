---
title: 'ACSD-64431: la mutazione "placeOrder" con codice coupon nella richiesta genera un errore interno del server'
description: Applica la patch ACSD-64431 per risolvere il problema di Adobe Commerce, in cui la mutazione "placeOrder" contenente le informazioni sul codice del coupon nella richiesta genera un errore interno del server invece di effettuare l’ordine correttamente.
feature: GraphQL, Orders, Promotions/Events
role: Admin, Developer
exl-id: 13918f3e-842b-4b2e-b2e2-2d8add542a87
source-git-commit: 43f4055d7c6bf681fde851d5132860ea7b68b677
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# ACSD-64431: la mutazione &quot;placeOrder&quot; con codice coupon nella richiesta genera un errore interno del server

La patch ACSD-64431 risolve il problema per cui la mutazione `placeOrder` contenente le informazioni sul codice coupon nella richiesta genera un errore interno del server invece di eseguire l&#39;ordine correttamente. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61. L’ID della patch è ACSD-64431. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La mutazione `placeOrder` che contiene le informazioni sul codice coupon nella richiesta genera un errore interno, invece di eseguire l&#39;ordine correttamente.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto semplice con _SKU 2836611_.
1. Creare un **[!UICONTROL Cart Price Rule]**, impostare **[!UICONTROL Coupon]** su `Specific Coupon` e immettere _TEST1234_ come codice coupon.
1. Creare un cliente:

   ```
   mutation {
   createCustomer(
       input: {
       firstname: "John"
       lastname: "Doe"
       email: "john.doe@example.com"
       password: "b1b2b3l@w+"
       is_subscribed: true
       }
   ) {
       customer {
       firstname
       lastname
       email
       is_subscribed
       }
   }
   }
   ```

1. Genera un token cliente. Puoi utilizzare questo token per le richieste successive.

   ```
   mutation {
   generateCustomerToken(email: "john.doe@example.com", password: "b1b2b3l@w+") {
       token
   }
   }
   ```

1. Crea un carrello vuoto. Salva l’ID carrello e utilizzalo per le richieste successive.

   ```
   mutation {
       createEmptyCart
   } 
   ```

1. Aggiungi il prodotto al carrello:

   ```
   mutation {
       addProductsToCart(
           cartId: "xxxx"
           cartItems: [{ quantity: 1, sku: "2836611" }]
       ) {
           cart {
               itemsV2 {
                   items {
                       product {
                           name
                           sku
                       }
                       ... on ConfigurableCartItem {
                           configurable_options {
                               configurable_product_option_uid
                               value_label
                           }
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

1. Applica il coupon:

   ```
   mutation {
       applyCouponToCart(input: { cart_id: "xxxx", coupon_code: "TEST1234" }) {
           cart {
               itemsV2 {
                   items {
                       product {
                           name
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
               applied_coupons {
                   code
               }
               prices {
                   grand_total {
                       value
                       currency
                   }
               }
           }
       }
   }
   ```

1. Impostare un indirizzo di spedizione:

   ```
   mutation {
       setShippingAddressesOnCart(
           input: {
               cart_id: "xxxxx"
               shipping_addresses: [
                   {
                       address: {
                           firstname: "John"
                           lastname: "Doe"
                           company: "Company Name"
                           street: ["3320 N Crescent Dr", "Beverly Hills"]
                           city: "Los Angeles"
                           region: "CA"
                           region_id: 12
                           postcode: "90210"
                           country_code: "US"
                           telephone: "123-456-0000"
                           save_in_address_book: false
                       }
                   }
               ]
           }
       ) {
           cart {
               shipping_addresses {
                   firstname
                   lastname
                   company
                   street
                   city
                   region {
                       code
                       label
                   }
                   postcode
                   telephone
                   country {
                       code
                       label
                   }
                   available_shipping_methods {
                       carrier_code
                       carrier_title
                       method_code
                       method_title
                   }
               }
           }
       }
   }
   ```

1. Impostare un metodo di spedizione:

   ```
   mutation {
       setShippingMethodsOnCart(
           input: {
               cart_id: "xxxx"
               shipping_methods: [{ carrier_code: "flatrate", method_code: "flatrate" }]
           }
       ) {
           cart {
               shipping_addresses {
                   selected_shipping_method {
                       carrier_code
                       carrier_title
                       method_code
                       method_title
                       amount {
                           value
                           currency
                       }
                   }
               }
           }
       }
   }
   ```

1. Imposta un indirizzo di fatturazione:

   ```
   mutation {
       setBillingAddressOnCart(
           input: {
               cart_id: "xxxx"
               billing_address: {
                   address: {
                       firstname: "John"
                       lastname: "Doe"
                       company: "Company Name"
                       street: ["64 Strawberry Dr", "Beverly Hills"]
                       city: "Los Angeles"
                       region: "CA"
                       region_id: 12
                       postcode: "90210"
                       country_code: "US"
                       telephone: "123-456-0000"
                       save_in_address_book: true
                   }
               }
           }
       ) {
           cart {
               billing_address {
                   firstname
                   lastname
                   company
                   street
                   city
                   region {
                       code
                       label
                   }
                   postcode
                   telephone
                   country {
                       code
                       label
                   }
               }
           }
       }
   }
   ```

1. Impostare un metodo di pagamento:

   ```
   mutation {
       setPaymentMethodOnCart(
           input: { cart_id: "xxxx", payment_method: { code: "checkmo" } }
       ) {
           cart {
               selected_payment_method {
                   code
               }
           }
       }
   }
   ```

1. Effettua l’ordine:

   ```
   mutation {
   placeOrder(
       input: {
       cart_id: "{{cart_id}}"
       }
   ) {
       orderV2 {
       number
       token
       }
       errors {
       message
       code
       }
   }
   }
   ```


<u>Risultati previsti</u>:

L’ordine deve essere effettuato.

<u>Risultati effettivi</u>:

Viene visualizzato il seguente messaggio di errore:
`"message": "Internal server error"`

`exception.log` contiene il seguente errore:

```
    report.ERROR: "discount_model" value should be specifiedGraphQL (1:135)
    1: mutation { placeOrder(input: {cart_id: "xxxx"}) { orderV2 { total { discounts { amount { currency value } coupon { code } } } } errors { message code } } }
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
