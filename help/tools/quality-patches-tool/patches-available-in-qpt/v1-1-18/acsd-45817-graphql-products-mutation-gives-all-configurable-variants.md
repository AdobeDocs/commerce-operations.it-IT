---
title: 'ACSD-45817: la mutazione dei prodotti GraphQL offre tutte le varianti configurabili'
description: La patch ACSD-45817 risolve il problema in cui una mutazione "products" di GraphQL per un archivio specifico restituisce tutte le varianti configurabili, comprese quelle non assegnate all’archivio richiesto. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18. L’ID della patch è ACSD-45817. Il problema è stato risolto in Adobe Commerce 2.4.4.
feature: GraphQL, Configuration, Products
role: Admin
exl-id: f00e9a8e-c18b-4fa8-b7c6-c228b6a22a2c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '454'
ht-degree: 0%

---

# ACSD-45817: la mutazione dei prodotti GraphQL offre tutte le varianti configurabili

La patch ACSD-45817 risolve il problema per cui una mutazione di GraphQL `products` per un archivio specifico restituisce tutte le varianti configurabili, incluse quelle non assegnate all&#39;archivio richiesto. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18. L’ID della patch è ACSD-45817. Il problema è stato risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.3-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Una mutazione di GraphQL `products` per un archivio specifico restituisce tutte le varianti configurabili, incluse quelle non assegnate all&#39;archivio richiesto.

<u>Prerequisiti</u>:

Creare un secondo sito Web, un secondo store e una seconda visualizzazione store.

<u>Passaggi da riprodurre</u>:

1. Creare un prodotto configurabile con due sottoprodotti: &quot;configurable-a&quot; e &quot;configurable-b&quot;.
1. Assegna il prodotto configurabile a entrambi i siti web.
1. Assegna una sola variante &quot;configurabile-a&quot; al secondo sito web.
1. Vai a **Storefront**, passa al secondo sito Web e apri il prodotto configurabile.
1. Assicurati di visualizzare solo un’opzione figlio: &quot;configurable-a&quot;.
1. Esegui una query GraphQL utilizzando l&#39;endpoint `POST: /graphql` e `Headers: "store" = "new"`

   ```GraphQL
   {
     products(filter: { sku: { eq: "configurable" } }) {
       items {
         id
         attribute_set_id
         name
         sku
         __typename
         price_range{
           minimum_price{
             regular_price{
               value
               currency
             }
           }
         }
         categories {
           id
         }
         ... on ConfigurableProduct {
           configurable_options {
             id
             attribute_id_v2
             label
             position
             use_default
             attribute_code
             values {
               value_index
               label
             }
             product_id
           }
           variants {
             product {
               id
               name
               sku
               attribute_set_id
               ... on PhysicalProductInterface {
                 weight
               }
               price_range{
                 minimum_price{
                   regular_price{
                     value
                     currency
                   }
                 }
               }
             }
             attributes {
               uid
               label
               code
               value_index
             }
           }
         }
       }
     }
   }
   ```

<u>Risultati previsti</u>:

La variante &quot;configurable-b&quot; non è assegnata al secondo sito web e non deve essere visualizzata nella risposta.

<u>Risultati effettivi</u>:

La variante &quot;configurable-b&quot; viene visualizzata nella risposta.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
