---
title: 'MDVA-40399: impossibile creare contemporaneamente fatture parziali per lo stesso ordine tramite API'
description: La patch MDVA-40399 risolve il problema che impedisce la creazione simultanea di fatture parziali per lo stesso ordine tramite l'API REST. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4. L'ID della patch è MDVA-40399. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
feature: REST, Invoices, Orders
role: Admin
exl-id: aa400a15-57b9-4f80-a49f-f4680b7e4705
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 591c578b-908e-5b79-a9d3-931dfe60c24c
    internal-label: Invoices
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
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
source-wordcount: '471'
ht-degree: 0%
---
# MDVA-40399: impossibile creare contemporaneamente fatture parziali per lo stesso ordine tramite API

La patch MDVA-40399 risolve il problema che impedisce la creazione simultanea di fatture parziali per lo stesso ordine tramite l&#39;API REST. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.4. L&#39;ID della patch è MDVA-40399. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Non è possibile creare contemporaneamente fatture parziali per gli stessi ordini utilizzando l&#39;API REST.

<u>Prerequisiti</u>:

Un prodotto configurabile con almeno due varianti.

<u>Passaggi da riprodurre</u>:

1. Aggiungi al carrello entrambe le varianti del prodotto configurabile.
1. Effettua l’ordine.
1. Creare due fatture contemporaneamente per l&#39;ordine tramite l&#39;API Rest.

<u>Risultati previsti</u>:

* Entrambe le fatture devono essere create correttamente.
* È necessario aggiornare `qty_invoiced` per entrambe le fatture nella tabella `sales_order_item`.
* Entrambi i prodotti devono avere una quantità fatturata.

<u>Risultati effettivi</u>:

* Entrambe le fatture sono state create correttamente.
* `qty_invoiced` non è aggiornato in base a una delle fatture nella tabella `sales_order_item`.
* Nella pagina **Visualizzazione ordini** dell&#39;amministratore, la quantità delle fatture viene visualizzata solo per un prodotto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it).
