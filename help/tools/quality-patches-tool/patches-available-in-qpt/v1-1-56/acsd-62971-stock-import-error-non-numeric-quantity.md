---
title: 'ACSD-62971: l''importazione di origini di magazzino con valori di quantità non numerici determina l''impostazione della quantità su 0'
description: Applicare la patch ACSD-62971 per risolvere il problema Adobe Commerce, in cui l'importazione di origini di magazzino con valori non numerici nella colonna 'quantità' comporta l'impostazione della quantità su 0.
feature: Data Import/Export, Inventory
role: Admin, Developer
exl-id: ece23153-4932-4ac5-b46e-49327a8e84a1
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
  - id: 8dc0e58b-adf0-51bb-8db5-bb36e3e656fb
    internal-label: Inventory
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%
---
# ACSD-62971: l&#39;importazione di origini di magazzino con valori di quantità non numerici determina l&#39;impostazione della quantità su 0

La patch di ACSD-62971 risolve il problema che causa l&#39;importazione di origini di magazzino con valori non numerici nella colonna &quot;quantità&quot;, la quantità viene impostata su 0. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. L’ID della patch è ACSD-62971. Il problema era pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Corregge il problema che causa l&#39;importazione di origini di magazzino con valori non numerici nella colonna **[!UICONTROL Quantity]**, la quantità viene impostata su 0.

<u>Passaggi da riprodurre</u>:

1. Crea **[!UICONTROL Simple Product]** con qtà=100
1. Eseguire un&#39;importazione **[!UICONTROL Stock Sources]** utilizzando il file con una quantità non corretta (&quot;abc&quot;)

   ```table
   source_code    sku    status    quantity
     default     simple    1         abc
   ```

1. Controllare la quantità dopo l&#39;importazione.

<u>Risultati previsti</u>:
La convalida dei dati di importazione dovrebbe avere esito negativo.

<u>Risultati effettivi</u>:
La quantità di prodotto semplice è diventata 0 e il prodotto viene aggiornato come [!UICONTROL Out of Stock].

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
