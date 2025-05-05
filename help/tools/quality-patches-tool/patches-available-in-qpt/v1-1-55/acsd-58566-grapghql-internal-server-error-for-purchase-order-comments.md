---
title: 'ACSD-58566: errore interno del server GraphQL per i commenti dell''ordine fornitore'
description: Applica la patch ACSD-58566 per risolvere il problema di Adobe Commerce, in cui GraphQL restituisce un errore interno del server quando esegue una query sul campo "created_at" nella mutazione "addPurchaseOrderComment".
feature: B2B, Purchase Orders, GraphQL
role: Admin, Developer
source-git-commit: 3b8cc44ea8d71982b8a2eb76d9d7ec2a5c3180b0
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-58566: errore interno del server GraphQL per i commenti dell&#39;ordine fornitore

La patch ACSD-58566 risolve il problema per cui l&#39;esecuzione di una query sul campo `created_at` nella mutazione `addPurchaseOrderComment` restituisce un valore null invece del datetime previsto. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55. L’ID della patch è ACSD-58566. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

GraphQL restituisce un errore interno del server durante la query sul campo `created_at` nella mutazione `addPurchaseOrderComment`.

<u>Prerequisiti</u>:

Vengono installati moduli B2B e sono abilitati gli ordini aziendali e di acquisto.

<u>Passaggi da riprodurre</u>:

1. Genera un token cliente per un utente della società.
1. Esegui la seguente sequenza di richieste GraphQL:
   1. Crea un *carrello* utilizzando `customerCart`.
   1. Aggiungi un prodotto al *carrello* utilizzando `addProductsToCart`.
   1. Effettuare l&#39;ordine utilizzando `placePurchaseOrder`.
   1. Aggiungere un commento all&#39;ordine di acquisto utilizzando `addPurchaseOrderComment`.

   ```
   mutation {
       addPurchaseOrderComment(
           input: { purchase_order_uid: "MQ==", comment: "Looks good to me" }
   ) {
           comment {
               uid
               created_at
               author {
                   firstname
                   lastname
                   email
               }
               text
           }
       }
   }
   ```

<u>Risultati previsti</u>:

Il campo `created_at` restituisce il datetime del commento dell&#39;ordine fornitore.

<u>Risultati effettivi</u>:

Visualizza null invece della data `created_at`.

```
{
  "errors": [
    {
      "message": "Internal server error",
      "locations": [
        {
          "line": 10,
          "column": 1
        }
      ],
      "path": [
        "addPurchaseOrderComment",
        "comment",
        "created_at"
      ]
    }
  ],
  "data": {
    "addPurchaseOrderComment": null
  }
}
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

[[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
