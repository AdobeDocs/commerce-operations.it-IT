---
title: 'ACSD-60326: la query GraphQL sullo stato del cliente [!UICONTROL Returns] restituisce un errore'
description: Applicare la patch ACSD-60326 per risolvere il problema Adobe Commerce in cui si verifica un errore nella query GraphQL per lo stato del cliente [!UICONTROL Returns].
feature: GraphQL, Returns, Customers
role: Admin, Developer
exl-id: 5cfd7e0d-8703-43a0-86d3-e69612347534
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# ACSD-60326: la query GraphQL sullo stato del cliente [!UICONTROL Returns] restituisce un errore

La patch ACSD-60326 risolve il problema relativo a un errore nella query GraphQL per lo stato del cliente [!UICONTROL Returns]. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.51. L’ID della patch è ACSD-60326. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La query GraphQL sullo stato del cliente [!UICONTROL Returns] restituisce un errore.

<u>Passaggi da riprodurre</u>:

1. Inizializza una nuova istanza con dati di esempio.
1. Nella barra laterale *[!UICONTROL Admin]*, vai a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL RMA Settings]** e imposta **[!UICONTROL Enable RMA on Storefront]** su *Sì*.
1. Vai a **[!UICONTROL Sales]** > **[!UICONTROL Shipping Settings]** > **[!UICONTROL Origin]** e compila l&#39;indirizzo.
1. Modificare la password per il cliente `roni_cost@example.com`.
1. Accedi al pannello di amministrazione e ordina al cliente `roni_cost@example.com` i seguenti prodotti:
   * *WSH12-32-rosso*
   * *WSH12-32-Viola*
   * *WSH12-32-Verde*
1. Creare *[!UICONTROL Invoice]* e *[!UICONTROL Shipment]* per questo ordine.
1. Selezionare **[!UICONTROL Create Returns]**.
1. Vai a **[!UICONTROL Return Items]** > **[!UICONTROL Add Items]** e:
   * Seleziona *WSH12-32-Red* e *WSH12-32-Purple*
   * Fare clic su **[!UICONTROL Add Selected Products to returns]**:
      * Imposta **[!UICONTROL Requested]** = *1*
      * Imposta **[!UICONTROL Return Reason]** su *Fuori servizio*
      * Imposta **[!UICONTROL Item Condition]** su *Aperto*
      * Imposta **[!UICONTROL Resolution]** su *Rimborso*
   * Fare clic su **[!UICONTROL Submit Returns]**.
1. Apri **[!UICONTROL Returns]** e seleziona **[!UICONTROL Return Items]** a sinistra.
   * Imposta **[!UICONTROL Authorized]** = *1* per entrambi i prodotti
   * Imposta **[!UICONTROL Status]** come *Autorizzato* per *WSH12-32-Purple*
   * Imposta **[!UICONTROL Status]** come *Negato* per *WSH12-32-Rosso*
   * Fai clic su **[!UICONTROL Save]**
1. Crea un nuovo ordine con gli stessi prodotti.
1. Creare *[!UICONTROL Invoice]*, *[!UICONTROL Shipment]* e *[!UICONTROL Returns]* per gli stessi prodotti. Autorizzare entrambi e continuare fino alla fine del processo [!UICONTROL Returns].
1. Genera un token cliente utilizzando la seguente query GraphQL:

   ```GraphQL
    mutation {
     generateCustomerToken(email: "roni_cost@example.com", password: "password") {
       token
      }
   }
   ```

1. Autorizza con il token ricevuto ed esegui la seguente query:

   ```
   {
   customer {
       returns(pageSize: 20, currentPage: 1) {
        total_count
           items {
               uid
               number
               status
               created_at
           }
       }
   }
   }
   ```

<u>Risultati previsti</u>:

La query non mostra alcun errore. Lo stato del secondo ritorno non è *null*.

<u>Risultati effettivi</u>:

La query restituisce un errore interno del server:

```
    {
    "errors": [
        {
            "message": "Internal server error",
            "locations": [
                {
                    "line": 8,
                    "column": 5
                }
            ],
            "path": [
                "customer",
                "returns",
                "items",
                1,
                "status"
            ]
        }
    ],
    "data": {
        "customer": {
            "returns": {
                "total_count": 2,
                "items": [
                    {
                        "uid": "MQ==",
                        "number": "000000001",
                        "status": "PARTIALLY_AUTHORIZED",
                        "created_at": "2024-07-09 10:35:55"
                    },
                    {
                        "uid": "Mg==",
                        "number": "000000002",
                        "status": null,
                        "created_at": "2024-07-09 10:50:02"
                    }
                ]
            }
        }
    }
    } 
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
