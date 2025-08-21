---
title: 'ACSD-66139: l’ordine GraphQL non riesce e viene visualizzato un errore NON DEFINITO per il carrello inattivo'
description: Applica la patch ACSD-66139 per risolvere il problema di Adobe Commerce per cui, quando effettui un ordine per un carrello inesistente o inattivo, GraphQL restituisce un codice di errore NON DEFINITO invece di uno specifico quando i messaggi di errore vengono tradotti.
feature: GraphQL
role: Admin, Developer
type: Troubleshooting
source-git-commit: 16d95ae0d58dfdc88a5fab725a37d353d3ee5c96
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---


# ACSD-66139: l’ordine GraphQL non riesce e viene visualizzato l’errore &quot;NON DEFINITO&quot; per il carrello inattivo

La patch ACSD-66139 risolve il problema per cui, quando si ordina un carrello inesistente o inattivo, GraphQL restituisce un codice di errore *UNDEFINED* invece di uno specifico quando vengono tradotti i messaggi di errore. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67. L’ID della patch è ACSD-66139. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` all&#39;ultima versione e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

GraphQL restituisce un codice di errore *UNDEFINED* invece di uno specifico quando si ordina un carrello inesistente o inattivo, se il messaggio di errore è stato tradotto.

<u>Passaggi da riprodurre</u>:

1. Aggiungi `app/i18n/Magento/de_DE/de_DE.csv` e includi la seguente traduzione della stringa di errore:

```
"Could not find a cart with ID ""%masked_cart_id""","Oh noo, we have an UNDEFINED issue, see!",module,Magento_QuoteGraphQl
```

1. Crea una visualizzazione store nel pannello Amministratore. Vai a **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL All Stores]**. Fare clic su **[!UICONTROL Create Store View]** e per **[!UICONTROL Code]** immettere il codice `test`.
1. Assegna la lingua `german` alla visualizzazione dello store appena creata.
1. Eseguire `setup:upgrade` e `setup:static-content:deploy -f`.
1. Esegui la seguente query GraphQL con intestazione &#39;Store:test&#39;:

```
mutation {
    placeOrder(input: { cart_id: "test" }) {
        orderV2 {
            id
            number
        }
    }
}
```

<u>Risultati previsti</u>:

Risposta di errore corretta:

```
{
    "errors": [
        {
            "message": "Oh noo, we have an UNDEFINED issue, see!",
            "locations": [
                {
                    "line": 2,
                    "column": 2
                }
            ],
            "path": [
                "placeOrder"
            ],
            "extensions": {
                "category": "graphql-input",
                "error_code": "CART_NOT_FOUND"
            }
        }
    ],
    "data": {
        "placeOrder": null
    }
}
```

<u>Risultati effettivi</u>:

`error_code` restituito è *NON DEFINITO*:

```
{
    "errors": [
        {
            "message": "Oh noo, we have an UNDEFINED issue, see!",
            "locations": [
                {
                    "line": 2,
                    "column": 2
                }
            ],
            "path": [
                "placeOrder"
            ],
            "extensions": {
                "category": "graphql-input",
                "error_code": "UNDEFINED"
            }
        }
    ],
    "data": {
        "placeOrder": null
    }
}
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
