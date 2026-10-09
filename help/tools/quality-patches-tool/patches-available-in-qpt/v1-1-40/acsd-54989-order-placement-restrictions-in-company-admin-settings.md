---
title: 'ACSD-54989: l''amministratore della società non può ordinare se [!UICONTROL Enable Purchase Orders] è impostato su Sì e [!UICONTROL Purchase Order] su No'
description: Applicare la patch ACSD-54989 per risolvere il problema Adobe Commerce che impedisce all'amministratore della società di effettuare ordini se [!UICONTROL Enable Purchase Orders] è impostato su Sì e [!UICONTROL Purchase Order] su No.
feature: Orders, Companies, Purchase Orders
role: Admin, Developer
exl-id: 13830361-dd0c-486f-b07f-34280a17ab76
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: e9004f3c-09ae-5d24-acd2-fa0987fdb66e
    internal-label: Companies
subfeature_v2:
  - id: 2d6d41d4-a5c1-5baf-8dbe-bf7300b68bb3
    internal-label: Purchase Orders
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
source-wordcount: '413'
ht-degree: 0%
---
# ACSD-54989: l&#39;amministratore della società non può ordinare se *[!UICONTROL Enable Purchase Orders]* è impostato su *Sì* e *[!UICONTROL Purchase Order]* su *No*

La patch ACSD-54989 risolve il problema che impedisce l&#39;inserimento di ordini se **[!UICONTROL Enable Purchase Orders]** è impostato su *Sì* e **[!UICONTROL Purchase Order]** su *No*. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.40. L’ID della patch è ACSD-54989. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p5 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli amministratori della società non possono effettuare ordini se **[!UICONTROL Enable Purchase Orders]** è impostato su *Sì* e **Ordine di acquisto** è impostato su *No*.

<u>Prerequisiti</u>:

Installa [!DNL B2B] moduli.

<u>Passaggi da riprodurre</u>:

1. Abilita la società e lascia [!UICONTROL **Order Approval Configuration]** > **[!UICONTROL Purchase Order**] = *No*.
1. Crea un prodotto semplice al prezzo di 100.
1. Crea una nuova società tramite l’Amministratore.
1. Impostare [!UICONTROL **Abilita ordini di acquisto**] su *Sì*.
1. Accedi come amministratore aziendale sulla vetrina.
1. Aggiungi al carrello il prodotto semplice creato.
1. Passare alla pagina di pagamento e fare clic su **[!UICONTROL Place Order]** per completare l&#39;acquisto.

<u>Risultati previsti</u>:

È possibile effettuare un ordine con successo.

<u>Risultati effettivi</u>:

La pagina **[!UICONTROL My Account]** si apre e l&#39;ordine non viene effettuato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
