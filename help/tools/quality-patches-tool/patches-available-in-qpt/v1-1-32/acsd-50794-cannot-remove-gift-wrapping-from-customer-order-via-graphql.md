---
title: 'ACSD-50794: impossibile rimuovere la confezione regalo dall''ordine del cliente tramite GraphQL'
description: Applica la patch ACSD-50794 per risolvere il problema di Adobe Commerce che impedisce agli utenti di rimuovere la confezione regalo dall’ordine del cliente tramite GraphQL.
feature: Gift, GraphQL, Orders
role: Admin
exl-id: e088fb18-89d3-47e4-ad02-54068c1ab653
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4fc0a729-4349-5307-bd06-1b4bfbaf5d0c
    internal-label: Gift
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '435'
ht-degree: 0%
---
# ACSD-50794: impossibile rimuovere la confezione regalo dall&#39;ordine del cliente tramite GraphQL

La patch ACSD-50794 risolve il problema che impediva agli utenti di rimuovere la confezione regalo dall’ordine del cliente tramite GraphQL. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.32. L’ID della patch è ACSD-50794. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli utenti non possono rimuovere la confezione regalo dall’ordine del cliente tramite GraphQL.

<u>Passaggi da riprodurre</u>:

1. Crea un cliente dal front-end.
1. Crea un prodotto semplice.
1. Abilita *[!UICONTROL Gift Messages]* andando in **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Gift Options]** e impostando *[!UICONTROL Allow Gift Messages]* = *[!UICONTROL Yes]*.
1. Crea *[!UICONTROL Gift Wrapping]* andando in **[!UICONTROL Stores]** > **[!UICONTROL Other Settings]** > **[!UICONTROL Gift Wrapping]**.
1. Ottieni token cliente.
1. Crea un carrello vuoto, customerCart.
   * Aggiungi prodotti al carrello: `addProductsToCart` mutazione
   * Imposta indirizzo di fatturazione: `setBillingAddressOnCart` mutazione
   * Imposta indirizzo di spedizione: `setShippingAddressesOnCart` mutazione
   * Imposta metodo di spedizione: mutazione `setShippingMethodsOnCart` (velocità piatta)
   * Imposta metodo di pagamento: mutazione `setPaymentMethodOnCart` (checkmo)
1. Ora controlla la confezione regalo *Uid* con questa query del carrello:

   ```GraphQL
   {
     cart(cart_id: "{{CART_ID}}") {
       available_gift_wrappings{
           uid
       }
   }
   }
   ```

1. Impostare il wrapping regalo utilizzando `setGiftOptionsOnCart`.
1. Controlla la query cart: cart.
1. Annullare l&#39;impostazione del wrapping regalo utilizzando `setGiftOptionsOnCart` (valore impostato su null).
1. Di nuovo, controlla la query cart: cart.
1. Ordine dei luoghi: mutazione `placeOrder`.
1. Esegui query cliente: cliente.

   ```GraphQL
   query {
     customer {
       firstname
       middlename
       lastname
       suffix
       email
       orders {
           items {
               order_date
               gift_wrapping {
                   design
                   uid
               }
           }
       }
       addresses {
         firstname
         middlename
         lastname
         street
         city
         region {
           region_code
           region
         }
         postcode
         country_code
         telephone
       }
     }
   }
   ```

<u>Risultati previsti</u>:

Una volta che un utente imposta un gift wrap e lo annulla, la query del cliente restituisce null.

<u>Risultati effettivi</u>:

La query del cliente restituisce comunque la confezione regalo come applicata.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
