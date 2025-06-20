---
title: 'ACSD-63329: gli attributi di data e ora non sono impostati durante la creazione di prodotti con API REST'
description: Applica la patch ACSD-63329 per risolvere il problema di Adobe Commerce, in cui i valori predefiniti non vengono impostati per i campi di data e ora durante la creazione di prodotti con API REST.
feature: REST
Role: Admin, Developers
exl-id: d8e7917b-07a5-465b-944b-fd6168dea63c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-63329: i valori predefiniti per i campi di data e ora non vengono impostati durante la creazione di prodotti con API REST

La patch ACSD-63329 risolve il problema che impediva l&#39;impostazione dei valori predefiniti per i campi di data e ora durante la creazione di un nuovo prodotto con API REST: `/rest/default/V1/products`. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58. L’ID della patch è ACSD-63329. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I valori predefiniti non sono impostati per i campi di data e ora durante la creazione di prodotti con API REST: `/rest/default/V1/products`

<u>Passaggi da riprodurre</u>:

1. Creare un attributo **[!UICONTROL Product]**, impostarne il valore predefinito su `12/31/2020` e impostare **[!UICONTROL Catalog Input Type for Store Owner]** su ***[!UICONTROL Date]*** o ***[!UICONTROL Date and Time]***.
1. Creare un altro attributo di tipo testo e impostare il valore predefinito su ***valore di test***.
1. Creare un nuovo prodotto utilizzando una richiesta REST API POST a `/rest/all/V1/products/`.

   ```
       {
           "product": {
               "sku": "testsku2",
               "name": "Test Api Product 2",
               "attribute_set_id": 4,
               "price": 100,
               "status": 1,
               "visibility": 4,
               "type_id": "simple",
               "weight": 20,
               "extension_attributes": {
                   "website_ids": [
                       1
                   ]
               }
           }
       }
   ```

1. Verifica i valori salvati per gli attributi menzionati in precedenza.

<u>Risultati previsti</u>:

Il valore predefinito deve essere salvato negli attributi di tipo **[!UICONTROL Date/Datetime]** quando si crea un prodotto utilizzando l&#39;API.

<u>Risultati effettivi</u>:

Il valore predefinito viene salvato per l&#39;attributo **[!UICONTROL Text]** ma non per l&#39;attributo **[!UICONTROL Date type]**. Il valore per l&#39;attributo **[!UICONTROL Date]** è vuoto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
