---
title: 'MDVA-41305: errore nella query GraphQL addProductsToWishlist per prodotti configurabili'
description: La patch MDVA-41305 risolve il problema che causa un errore nella query GraphQL "addProductsToWishlist" per i prodotti configurabili. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10. L'ID della patch è MDVA-41305. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
feature: GraphQL, Configuration, Products
role: Admin
exl-id: 985c3c46-d2c8-4479-b9e4-e5f9504ab03b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# MDVA-41305: errore nella query GraphQL addProductsToWishlist per prodotti configurabili

La patch MDVA-41305 risolve il problema relativo all&#39;errore nella query GraphQL `addProductsToWishlist` per i prodotti configurabili. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10. L&#39;ID della patch è MDVA-41305. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando gli utenti aggiungono prodotti configurabili (con/senza configurazione) alla lista dei desideri da GraphQL, non sono in grado di ottenere SKU configurabili e opzioni configurabili in risposta.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto configurabile (con le opzioni Blu, Grigio e una personalizzata).
1. Apri frontend; accedi come cliente e crea una lista dei desideri (controlla wishlist_id).
1. Apri Postman e crea un token cliente:

   <pre>
    <code class="language-graphql">
    mutation &lbrace;
      generateCustomerToken(email: "", password: "") &lbrace;
        token
      &rbrace;
     &rbrace;
     </code>
     </pre>

1. Imposta questo token per l&#39;autorizzazione Bearer.
1. Provare ad aggiungere un prodotto configurabile *Blu* alla lista dei desideri seguendo le istruzioni seguenti:

<pre>
<code class="language-graphql">
mutation &lbrace;
 addProductsToWishlist(
   wishlistId: 1
   wishlistItems: &lbrack;
     &lbrace;
       sku: "conf2"
       selected_options: &lbrack;
            "Y29uZmlndXJhYmxlLzkzLzUw"
       &rbrack;
       quantity: 1
       entered_options: &lbrack;
         &lbrace;
           uid: "Y3VzdG9tLW9wdGlvbi8x"
           value: "test"
         &rbrace;
       &rbrack;
     &rbrace;
    &rbrack;
  ) &lbrace;
    wishlist &lbrace;
      id
      items_count
      items_v2 (currentPage: 1, pageSize: 8 ) &lbrace;
        items &lbrace;
         id
         quantity
         ... on ConfigurableWishlistItem  &lbrace;
           child_sku
           customizable_options &lbrace;
             customizable_option_uid
           &rbrace;
         &rbrace;
         product &lbrace;
           uid
           name
           sku
           options_container
           ... on CustomizableProductInterface &lbrace;
             options &lbrace;
              title
              required
              sort_order
              option_id
              ... on CustomizableFieldOption &lbrace;
                value &lbrace;
                  uid
                  sku
                  price
                  price_type
                  max_characters
                &rbrace;
              &rbrace;
            &rbrace;
          &rbrace;
          price_range &lbrace;
            minimum_price &lbrace;
              regular_price &lbrace;
                currency
                value
              &rbrace;
            &rbrace;
            maximum_price &lbrace;
               regular_price &lbrace;
                 currency
                 value
               &rbrace;
             &rbrace;
           &rbrace;
         &rbrace;
       &rbrace;
     &rbrace;
   &rbrace;
  user_errors &lbrace;
    code
    message
   &rbrace;
 &rbrace;
&rbrace;
</code>
</pre>

<u>Risultati previsti</u>:

Gli utenti possono visualizzare un set di opzioni di prodotto configurate nella risposta specificata nel payload e aggiunta alla lista dei desideri.

<u>Risultati effettivi</u>:

Gli utenti ricevono in risposta *un errore interno del server*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
