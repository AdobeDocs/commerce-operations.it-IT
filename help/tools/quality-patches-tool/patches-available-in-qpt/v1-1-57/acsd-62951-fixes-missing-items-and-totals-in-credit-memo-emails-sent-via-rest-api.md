---
title: 'ACSD-62951: sono stati corretti gli elementi mancanti e i totali nelle e-mail [!UICONTROL Credit Memo] inviate tramite API REST'
description: Applica la patch ACSD-62951 per risolvere il problema Adobe Commerce per cui l'e-mail [!UICONTROL Credit Memo] viene inviata senza includere gli elementi dell'ordine e i totali.
feature: REST
role: Admin, Developer
exl-id: e0c6d4c1-ecaf-46e7-af2d-05a148970d71
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-62951: sono stati corretti gli elementi mancanti e i totali nelle e-mail *[!UICONTROL Credit Memo]* inviate tramite API REST

La patch ACSD-62951 risolve il problema che causa l&#39;invio dell&#39;e-mail [!UICONTROL Credit Memo] senza includere gli elementi dell&#39;ordine e i totali. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57. L’ID della patch è ACSD-62951. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p10

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;e-mail *[!UICONTROL Credit Memo]* inviata quando viene creata una nota di credito tramite l&#39;API REST `POST V1/order/:orderId/refund` non include gli elementi dell&#39;ordine e i totali.

<u>Passaggi da riprodurre</u>:

1. Crea un ordine con qualsiasi prodotto.
1. Spedire e fatturare l&#39;ordine. Assicurarsi che l&#39;e-mail della fattura sia inviata e che includa i dettagli del prodotto.
1. Genera un token di amministrazione utilizzando il client API.
1. Utilizza il token per creare una nota di credito tramite l’API REST.
   1. Endpoint: `POST V1/order/:orderId/refund`
   1. Payload richiesta:

      ```
      {  
          "notify": true,  
          "items": [  
              {  
                  "order_item_id": 1,  
                  "qty": 1  
              }  
          ]  
      }  
      ```

<u>Risultati previsti</u>:

L&#39;e-mail *[!UICONTROL Credit Memo]* deve includere gli elementi rimborsati e i totali

<u>Risultati effettivi</u>:

L&#39;e-mail *[!UICONTROL Credit Memo]* non contiene elementi o totali. Le informazioni sono incomplete.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.


## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
