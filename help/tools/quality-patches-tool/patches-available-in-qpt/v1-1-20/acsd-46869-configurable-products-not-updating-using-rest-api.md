---
title: 'ACSD-46869: i prodotti configurabili non vengono aggiornati utilizzando l’API REST al momento del pagamento'
description: La patch ACSD-46869 risolve il problema che impedisce l’aggiornamento dei prodotti configurabili tramite l’API REST al momento del pagamento. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.20. L’ID della patch è ACSD-46869. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.
feature: REST, Checkout, Configuration, Orders, Products
role: Admin
exl-id: f03d4b24-ac95-406e-8e9d-908149b9207c
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-46869: i prodotti configurabili non vengono aggiornati utilizzando l’API REST al momento del pagamento

La patch ACSD-46869 risolve il problema che impedisce l’aggiornamento dei prodotti configurabili tramite l’API REST al momento del pagamento. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.20. L’ID della patch è ACSD-46869. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [[!DNL QPT] pagina di destinazione](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I prodotti configurabili non vengono aggiornati utilizzando l’API REST durante il pagamento.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto configurabile con attributi di colore e dimensioni.
1. Selezionare **[!UICONTROL Options]** e aggiungere il prodotto al carrello.
1. Vai a **[!UICONTROL Checkout]**, aggiorna le dimensioni più volte tranne che per la quantità, quindi controlla la richiesta e la risposta.
1. Quando si aggiornano le dimensioni, viene visualizzata la seguente risposta.

```REST API
{"extension_attributes":{"configurable_item_options":[
{"option_id":"960","option_value":25083},
{"option_id":"801","option_value":177}
]}}
```

<u>Risultati previsti</u>:

Il valore viene aggiornato in base alle modifiche.

<u>Risultati effettivi</u>:

`option_value` non è aggiornato, quindi quando l&#39;ordine viene effettuato, ha il valore di dimensione precedente.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tools] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida dello strumento Patch di qualità.
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
