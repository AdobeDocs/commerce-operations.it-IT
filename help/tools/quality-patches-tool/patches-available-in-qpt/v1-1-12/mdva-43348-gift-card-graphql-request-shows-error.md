---
title: 'MDVA-43348: la richiesta GraphQL di gift card mostra un errore'
description: La patch MDVA-43348 risolve il problema per cui la richiesta GraphQL di Gift Card mostra un errore se "gift_card_options" contiene "uid". Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12. L'ID della patch è MDVA-43348. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
feature: Gift, GraphQL
role: Admin
exl-id: 94cb939a-fad2-4f01-a641-d8d5b656d931
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# MDVA-43348: la richiesta GraphQL di gift card mostra un errore

La patch di MDVA-43348 risolve il problema relativo alla visualizzazione di un errore nella richiesta GraphQL Gift Card se `gift_card_options` contiene &quot;uid&quot;. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12. L&#39;ID della patch è MDVA-43348. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La richiesta GraphQL di gift card mostra un errore se gift_card_options contiene &quot;uid&quot;.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto gift card.
1. Eseguire la reindicizzazione.
1. Effettua una chiamata GraphQL in cui la chiave URL è &quot;gift-card&quot;:

<pre>
<code class="language-graphql">
query getProductOptionsForProductPage_bypassFastly($urlKey: String!) &lbrace;
  products(filter: { url_key: { eq: $urlKey } }) &lbrace;
    items &lbrace;
      id
      url_key
      ... on GiftCardProduct &lbrace;
        allow_open_amount
        open_amount_min
        open_amount_max
        giftcard_type
        is_redeemable
        lifetime
        allow_message
        message_max_length
        gift_card_options &lbrace;
          uid
          title
          required
        &rbrace;
      &rbrace;
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

<u>Risultati previsti</u>:

I dati della gift card vengono restituiti su richiesta.

<u>Risultati effettivi</u>:

Il seguente errore si verifica in seguito alla richiesta di dati della Gift Card:

<pre>
<code class="language-graphql">
&lbrace;
  "errors": &lbrack;
    &lbrace;
      "debugMessage": "Cannot return null for non-nullable field \"CustomizableFieldOption.uid\".",
      "message": "Internal server error",
      "extensions": &lbrace;
        "category": "internal"
      &rbrace;,
      "locations": &lbrack;
        &lbrace;
          "line": 16,
          "column": 1
        &rbrace;
      &rbrack;,
      "path": &lbrack;
        "products",
        "items",
        0,
        "gift_card_options",
        0,
        "uid"
      &rbrack;
    &rbrace;,
    &lbrace;
      "debugMessage": "Cannot return null for non-nullable field \"CustomizableFieldOption.uid\".",
      "message": "Internal server error",
      "extensions": &lbrace;
        "category": "internal"
      &rbrace;,
      "locations": &lbrack;
        &lbrace;
          "line": 16,
          "column": 1
        &rbrace;
      &rbrack;,
      "path": &lbrack;
        "products",
        "items",
        0,
        "gift_card_options",
        1,
        "uid"
      &rbrack;
    &rbrace;,
    &lbrace;
      "debugMessage": "Cannot return null for non-nullable field \"CustomizableFieldOption.uid\".",
      "message": "Internal server error",
      "extensions": &lbrace;
        "category": "internal"
      &rbrace;,
      "locations": &lbrack;
        &lbrace;
          "line": 16,
          "column": 1
        &rbrace;
      &rbrack;,
      "path": &lbrack;
        "products",
        "items",
        0,
        "gift_card_options",
        2,
        "uid"
      &rbrack;
    &rbrace;,
    &lbrace;
      "debugMessage": "Cannot return null for non-nullable field \"CustomizableFieldOption.uid\".",
      "message": "Internal server error",
      "extensions": &lbrace;
        "category": "internal"
      &rbrace;,
      "locations": &lbrack;
        &lbrace;
          "line": 16,
          "column": 1
        &rbrace;
      &rbrack;,
      "path": &lbrack;
        "products",
        "items",
        0,
        "gift_card_options",
        3,
        "uid"
      &rbrack;
    &rbrace;,
    &lbrace;
      "debugMessage": "Cannot return null for non-nullable field \"CustomizableFieldOption.uid\".",
      "message": "Internal server error",
      "extensions": &lbrace;
        "category": "internal"
      &rbrace;,
      "locations": &lbrack;
        &lbrace;
          "line": 16,
          "column": 1
        &rbrace;
      &rbrack;,
      "path": &lbrack;
        "products",
        "items",
        0,
        "gift_card_options",
        4,
        "uid"
      &rbrack;
    &rbrace;
  &rbrack;,
  "data": &lbrace;
    "products": &lbrace;
      "items": &lbrack;
        &lbrace;
          "id": 2,
          "url_key": "gitf-card",
          "allow_open_amount": false,
          "open_amount_min": null,
          "open_amount_max": null,
          "giftcard_type": "VIRTUAL",
          "is_redeemable": true,
          "lifetime": 0,
          "allow_message": true,
          "message_max_length": 255,
          "gift_card_options": &lbrack;
            null,
            null,
            null,
            null,
            null
          &rbrack;
        &rbrace;
      &rbrack;
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
