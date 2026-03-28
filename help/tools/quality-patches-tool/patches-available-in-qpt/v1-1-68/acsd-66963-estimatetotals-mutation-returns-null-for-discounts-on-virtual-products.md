---
title: 'ACSD-66963: la mutazione "estimateTotals" restituisce null per gli sconti sui prodotti virtuali'
description: Applica la patch ACSD-66963 per risolvere il problema Adobe Commerce per cui "estimateTotals" restituisce *null* per gli sconti quando un codice sconto viene applicato a un carrello con solo prodotti virtuali.
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
exl-id: b62e48f5-a9d6-456a-97e7-96f740d8e927
source-git-commit: 7054a5286f01e26e324401f4d8505e4e0faed93e
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---

# ACSD-66963: la mutazione `estimateTotals` restituisce null per gli sconti sui prodotti virtuali

La patch ACSD-66963 risolve il problema per cui `estimateTotals` restituisce *null* per gli sconti quando un codice sconto viene applicato a un carrello con solo prodotti virtuali. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68. L’ID della patch è ACSD-66963. Questo problema è stato risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La mutazione `estimateTotals` restituisce *null* per gli sconti quando viene applicato un codice sconto a un carrello contenente solo prodotti virtuali.

<u>Passaggi da riprodurre</u>:

1. Crea un carrello contenente solo prodotti virtuali.
1. Applica un codice sconto:

   ```
   mutation {
     estimateTotals(
       input: {
         cart_id: "cart_id",
         address: {
           country_code: US,
           postcode: "78732",
           region: {
             region_code: "TX"
           }
         },
         shipping_method: {
           carrier_code: "{$shipping}",
           method_code: "{$shipping}"
         }
       }
     ) {
       cart {
         prices {
           discounts {
             amount {
               value
               currency
             }
             label
             coupon {
               code
             }
             applied_to
             type
           }
         }
       }
     }
   }
   ```

<u>Risultati previsti</u>:

Le informazioni sugli sconti sono incluse per i carrelli che contengono solo prodotti virtuali.

```
    {
      "data": {
        "estimateTotals": {
          "cart": {
            "prices": {
              "discounts": [
                {
                  "amount": {
                    "value": 100.5,
                    "currency": "USD"
                  },
                  "label": "A second discount code for testing",
                  "coupon": {
                    "code": "z3r0c00l"
                  },
                  "applied_to": "ITEM",
                  "type": null
                }
              ]
            }
          }
        }
      },
      "extensions": {}
    }
```

<u>Risultati effettivi</u>:

Le informazioni sullo sconto restituiscono come *null* per i carrelli con solo prodotti virtuali.

```
    {
      "data": {
        "estimateTotals": {
          "cart": {
            "prices": {
              "discounts": null
            }
          }
        }
      },
      "extensions": {}
    }
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
