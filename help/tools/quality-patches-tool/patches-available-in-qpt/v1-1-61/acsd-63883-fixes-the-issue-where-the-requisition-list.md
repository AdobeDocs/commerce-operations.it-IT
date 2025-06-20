---
title: 'ACSD-63883: Correzione di "items_count" errato nella risposta  [!DNL GraphQL]  per [!UICONTROL Requisition List]'
description: Applica la patch ACSD-63883 per risolvere il problema per cui [!UICONTROL Requisition List] restituisce un "items_count" errato nella risposta  [!DNL GraphQL] .
feature: B2B, GraphQL
role: Admin, Developer
exl-id: 8946d7fb-558a-4867-a843-a61715416f25
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# ACSD-63883: correzione di `items_count` errato nella risposta [!DNL GraphQL] per [!UICONTROL Requisition List]

La patch ACSD-63883 risolve il problema per cui **[!UICONTROL Requisition List]** restituisce un `items_count` errato nella risposta [!DNL GraphQL]. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61. L’ID della patch è ACSD-63883. Il problema è pianificato per essere risolto in Adobe Commerce B2B 1.5.3.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

**[!UICONTROL Requisition List]** restituisce un `items_count` errato nella risposta [!DNL GraphQL].


<u>Passaggi da riprodurre</u>:

1. Abilita la funzione **[!UICONTROL Requisition List]** B2B.
1. Crea alcuni prodotti.
1. Crea un account cliente.
1. Fare clic su **[!UICONTROL Create new Requisition List]**.
1. Invia la richiesta di mutazione `addProductsToRequisitionList` [!DNL GraphQL] con un prodotto per aggiungerla a [!UICONTROL Requisition List].

   ```
   mutation addProductsToRequisitionList(
   $requisitionListUid: ID!
   $requisitionListItems: [RequisitionListItemsInput!]!
   ) {
   addProductsToRequisitionList(
   requisitionListUid: $requisitionListUid
   requisitionListItems: $requisitionListItems
   ) {
   requisition_list
   { uid name description items_count }
   }
   }
   ```

1. Invia la richiesta di mutazione `addProductsToRequisitionList` [!DNL GraphQL] con altri tre prodotti per aggiungerli a [!UICONTROL Requisition List].
1. Controlla `items_count` nella risposta.

**Risultati previsti**:

* `items_count`: nella risposta deve essere restituito 4.

**Risultati effettivi**:

* `items_count`: 2 viene restituito nella risposta.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.


## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
