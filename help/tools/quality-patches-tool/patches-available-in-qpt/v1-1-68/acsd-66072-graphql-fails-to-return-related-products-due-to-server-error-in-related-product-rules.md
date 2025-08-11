---
title: 'ACSD-66072: GraphQL non restituisce i prodotti correlati nella pagina Dettagli prodotto'
description: Applica la patch ACSD-66072 per risolvere il problema di Adobe Commerce, se i prodotti correlati non vengono restituiti tramite GraphQL nella pagina Dettagli prodotto a causa di un errore interno del server quando sono configurate le regole prodotto correlate.
feature: GraphQL, Products
role: Admin, Developer
type: Troubleshooting
source-git-commit: b1cd5383d774ab0ed97b80a4abf7df5706706ea5
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---


# ACSD-66072: GraphQL non restituisce i prodotti correlati nella pagina Dettagli prodotto

La patch ACSD-66072 risolve il problema che impediva la restituzione dei prodotti correlati tramite GraphQL nella pagina Dettagli prodotto a causa di un errore interno del server durante la configurazione di **[!UICONTROL Related Products Rule]**. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68. L’ID della patch è ACSD-66072. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di distribuzione) 2.4.6-p8

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.8-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I prodotti correlati non vengono restituiti tramite GraphQL nella pagina Dettagli prodotto a causa di un errore interno del server quando **[!UICONTROL Related Products Rule]** è configurato.

<u>Passaggi da riprodurre</u>:

1. Creare prodotti configurabili:
   * **Prodotto 1**: `config1` con `option1`
   * **Prodotto 2**: `config2` con `option2`

1. Creare e assegnare prodotti a una categoria
   * Crea una **nuova categoria**.
   * Assegnare entrambi i prodotti (`config1` e `config2`) a questa categoria.

1. Passa a **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Related Products Rule]**, quindi crea una nuova regola con le seguenti impostazioni:

   * **[!UICONTROL Priority]**: 1
   * **[!UICONTROL Applies To]**: **[!UICONTROL Related Products]**
   * **[!UICONTROL Result Limit]**: 10
   * **[!UICONTROL Products to Match]**: **[!UICONTROL Attribute Set is Default]**
   * **[!UICONTROL Products to Display]**: `Product Category is the Same as Matched Product Categories`

1. Eseguire i seguenti comandi CLI di Magento:

   ```bash
   bin/magento indexer:reindex
   bin/magento cache:clean
   ```

1. Invia una richiesta POST a `../graphql` con il seguente payload:

   ```
   query getRelatedProductsForProductPage($urlKey: String!) 
   {
       products(filter: { url_key: { eq: $urlKey } }) 
       {
           items {
               id
               __typename
               uid
               url_key
               name
               sku
               related_products {
                   id
                   uid
                   name
                   sku
                   stock_status
                   url_key
                   small_image {
                       url
                       __typename
                       }
                       thumbnail {
                           url
                           __typename
                           }
                           image {
                               url
                               __typename
                               }
                               price_range {
                                   maximum_price {
                                       regular_price {
                                           currency
                                           value
                                           __typename
                                           }
                                           __typename
                                           }
                                           minimum_price {
                                               discount {
                                                   amount_off
                                                   percent_off
                                                   __typename
                                                   }
                                                   final_price {
                                                       currency
                                                       value
                                                       __typename
                                                       }
                                                       regular_price {
                                                           currency
                                                           value
                                                           __typename}
                                                           __typename}
                                                           __typename}
                                                           __typename
                                                           }
                                                           }
                                                           __typename
                                                           }
                                                           }
   ```

<u>Risultati previsti</u>:

La query restituisce il prodotto correlato (`config1`).

<u>Risultati effettivi</u>:

```graphql
{
    "errors": [
        {
            "message": "Internal server error",
            "locations": [
                {
                    "line": 10,
                    "column": 7
                }
            ],
            "path": [
                "products",
                "items",
                0,
                "related_products"
            ]
        }
    ],
    "data": {
        "products": {
            "items": [
                {
                    "id": 4,
                    "__typename": "ConfigurableProduct",
                    "uid": "NA==",
                    "url_key": "config2",
                    "name": "config2",
                    "sku": "config2",
                    "related_products": null
                }
            ],
            "__typename": "Products"
        }
    }
}
```

Il file `var/log/exception.log` contiene:

```
report.ERROR: Deprecated Functionality: explode(): Passing null to parameter #2 ($string) of type string is deprecated in /home/magento2ee/app/code/Magento/TargetRule/Model/ResourceModel/Index.php on line 557
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
