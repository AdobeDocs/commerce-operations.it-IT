---
title: 'ACSD-62965: sono state corrette le correzioni per cui mancava il messaggio LocalizedException nella risposta di posizionamento dell’ordine di GraphQL'
description: Applica la patch ACSD-62965 per risolvere i problemi di Adobe Commerce in cui il messaggio "LocalizedException" non era incluso nella risposta di GraphQL durante il posizionamento dell’ordine.
feature: Orders, GraphQL
role: Admin, Developer
source-git-commit: 8191bf8feda8f8e041ecf83d9ddf5c5119930531
workflow-type: tm+mt
source-wordcount: '355'
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
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La risposta di GraphQL per il posizionamento dell&#39;ordine non include un messaggio `LocalizedException`, con dettagli di errore insufficienti per il debug.

<u>Passaggi da riprodurre</u>:

1. Installa un&#39;istanza **[!DNL Adobe Commerce]** pulita.
1. Aggiungi un prodotto al carrello e procedi al passaggio di inserimento dell’ordine.
1. Aggiungi `LocalizedException` a `Magento\Framework\Exception\LocalizedException` in `app/code/Magento/QuoteGraphQl/Model/Resolver/PlaceOrder.php`.
1. Inserire l&#39;eccezione dopo la riga seguente:

   ```
   $cart = $this->getCartForCheckout->execute($maskedCartId, $userId, $storeId);
   ```

   Aggiungi l&#39;eccezione:

   ```
   throw new LocalizedException(new Phrase("Test LocalizedException"));
   ```

1. Esegui la richiesta GraphQL dell&#39;ordine cliente:

   ```
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

      ```
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

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
