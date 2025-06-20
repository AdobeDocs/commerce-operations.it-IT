---
title: 'ACSD-51305: prodotti secondari compositi esauriti non disponibili nella risposta GraphQL'
description: Applica la patch ACSD-51305 per risolvere il problema di Adobe Commerce per cui i prodotti secondari compositi esauriti non sono disponibili nella risposta di GraphQL.
feature: Categories, GraphQL, Orders, Products
role: Admin
exl-id: 110bb332-2032-4aaf-b95e-971fc3382262
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-51305: prodotti secondari compositi esauriti non disponibili nella risposta GraphQL

La patch ACSD-51305 risolve il problema se i prodotti secondari compositi esauriti non sono disponibili nella risposta di GraphQL. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.32. L’ID della patch è ACSD-51305. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I prodotti secondari compositi esauriti non sono disponibili nella risposta di GraphQL.

<u>Passaggi da riprodurre</u>:

1. Accedi al sito web dell’amministratore.
1. Crea una categoria (cat1, id=3).
1. Crea un prodotto *simple1* (esaurito, non visibile singolarmente, assegnato a *cat1*).
1. Crea un prodotto *simple2* (disponibile, non visibile singolarmente, assegnato a *cat1*).
1. Creare un prodotto *bundle1* con *simple1* e *simple2* prodotti secondari come prodotti *option1* con pulsante di opzione e assegnarlo alla categoria *cat1*.
1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]**.

   * Imposta **[!UICONTROL Display Out of Stock Products]** su *Sì*.

1. Apri il prodotto *bundle1* nella vetrina e accertati che sia *simple1* che *simple2* siano visualizzati al suo interno.
1. Esegui la seguente query GraphQL:

   ```GraphQL
   {
       categoryList(filters: { ids: { in: ["3"] } }) {
           id
           name
           products(pageSize: 8, sort: { position: ASC }) {
               total_count
               items {
                   id
                   sku
                   name
                   ... on BundleProduct {
                       url_key
                       items {
                           title
                           sku
                           options {
                               quantity
                               position
                               is_default
                               product {
                                   id
                                   name
                                   sku
                               }
                           }
                       }
                   }
               }
           }
       }
   }
   ```

<u>Risultati previsti</u>:

La sezione **[!UICONTROL Product]** all&#39;interno del blocco **[!UICONTROL Options]** non è vuota.

<u>Risultati effettivi</u>:

La sezione **[!UICONTROL Product]** all&#39;interno del blocco **[!UICONTROL Options]** è vuota.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
