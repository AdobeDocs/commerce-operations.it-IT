---
title: 'ACSD-49389: e-mail pronta per il prelievo inviata dall’API quando non è pronta per il prelievo'
description: Applica la patch ACSD-49389 per risolvere il problema di Adobe Commerce, a causa del quale l’API invia un’e-mail pronta per il prelievo quando l’ordine non è pronto per il prelievo.
feature: REST, Communications
role: Admin
exl-id: d1bc430a-3021-40d1-9091-db8ed9125619
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bb03f6c4-cab9-560e-9d02-5816e1808d17
    internal-label: Communications
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%
---
# ACSD-49389: e-mail pronta per il prelievo inviata dall’API quando non è pronta per il prelievo

La patch ACSD-49389 risolve il problema per cui un’e-mail pronta per il prelievo viene inviata dall’API quando l’ordine non è pronto per il prelievo. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.29. L’ID della patch è ACSD-49389. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella [pagina di destinazione QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando l’ordine non è pronto per il prelievo, l’API invia un’e-mail pronta per il prelievo.

<u>Passaggi da riprodurre</u>:

1. Abilita il metodo *[!UICONTROL In-Store Delivery]*.
1. Creare un&#39;origine di magazzino con l&#39;ubicazione di prelievo abilitata.
1. Crea nuovo stock utilizzando il sito Web principale con l&#39;origine creata in precedenza.
1. Crea un prodotto assegnando la stessa origine.
1. Imposta qtà magazzino = 1.
1. Controllare il prodotto creato al passaggio 4 utilizzando il metodo *[!UICONTROL In-Store Delivery]* dalla vetrina.
1. Creare una fattura per l&#39;ordine.
1. Impostare la quantità del prodotto su *0* e renderlo esaurito.
1. Pubblica la seguente richiesta API:

```json
{
    "orderIds": [
        1
    ]
}
```

<u>Risultati previsti</u>:

L’e-mail pronta per il prelievo non viene inviata.

<u>Risultati effettivi</u>:

L&#39;API ha restituito *L&#39;ordine non è pronto per il prelievo*, ma l&#39;e-mail pronta per il prelievo è stata inviata.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, consultare [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
