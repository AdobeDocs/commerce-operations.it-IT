---
title: 'ACSD-62965: sono state corrette le correzioni per cui mancava il messaggio LocalizedException nella risposta di posizionamento dell’ordine di GraphQL'
description: Applica la patch ACSD-62965 per risolvere i problemi di Adobe Commerce in cui il messaggio "LocalizedException" non era incluso nella risposta di GraphQL durante il posizionamento dell’ordine.
feature: Orders, GraphQL
role: Admin, Developer
exl-id: cf9d1409-6fe3-4019-9207-df5f12a41505
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
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
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%
---
# ACSD-62965: sono state corrette le correzioni per la mancanza del messaggio `LocalizedException` nella risposta di posizionamento dell&#39;ordine di GraphQL

La patch ACSD-62965 risolve il problema che impediva l&#39;inclusione del messaggio `LocalizedException` nella risposta di GraphQL durante l&#39;inserimento dell&#39;ordine. Questa patch è disponibile con [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57. L’ID della patch è ACSD-62965. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.7

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La risposta di GraphQL per il posizionamento dell&#39;ordine non include un messaggio `LocalizedException`, con dettagli di errore insufficienti per il debug.

<u>Passaggi da riprodurre</u>:

1. Installa un&#39;istanza **[!DNL Adobe Commerce]** pulita.
1. Aggiungi un prodotto al carrello e procedi al passaggio di inserimento dell’ordine.
1. Aggiungi `LocalizedException` a `Magento\Framework\Exception\LocalizedException` in `app/code/Magento/QuoteGraphQl/Model/Resolver/PlaceOrder.php`.
1. Inserire l&#39;eccezione dopo la riga seguente:

   ```shell
   $cart = $this->getCartForCheckout->execute($maskedCartId, $userId, $storeId);
   ```

   Aggiungi l&#39;eccezione:

   ```text
   throw new LocalizedException(new Phrase("Test LocalizedException"));
   ```

1. Esegui la richiesta GraphQL dell&#39;ordine cliente:

   ```graphql
   mutation {
   placeOrder(input: {cart_id: "cart_id"}) {
       order {
       order_number
       }
   }
   }
   ```

1. Osserva la risposta:
   1. La risposta non include il messaggio `LocalizedException`.
   1. Esempio di risposta errata:

      ```json
      {
      "data": {
          "placeOrder": {
          "order": null
          }
      }
      }
      ```

<u>Risultati previsti</u>:

Se si verifica un `LocalizedException`, il messaggio di eccezione deve essere incluso nella risposta GraphQL di posizionamento dell&#39;ordine per migliorare la gestione degli errori.

<u>Risultati effettivi</u>:

Se si verifica un `LocalizedException`, il messaggio di eccezione non viene incluso nella risposta GraphQL di posizionamento dell&#39;ordine.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
