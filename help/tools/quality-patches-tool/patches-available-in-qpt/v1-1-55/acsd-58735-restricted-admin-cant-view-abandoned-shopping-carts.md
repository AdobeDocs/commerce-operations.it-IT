---
title: 'ACSD-58735: l’amministratore con restrizioni non può visualizzare i carrelli acquisti abbandonati sull’account del cliente per il sito web associato'
description: Applica la patch ACSD-58735 per risolvere il problema di Adobe Commerce, a causa del quale un amministratore con restrizioni non può visualizzare i carrelli acquisti abbandonati nella pagina dell’account cliente in Commerce Admin per un sito web associato.
feature: Shopping Cart, Admin Workspace, Customers
role: Admin, Developer
exl-id: b5dcc12f-325d-4de5-bae5-ff938ec77b13
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
  - id: 22bad240-8308-569b-a9d5-578f1ff890ca
    internal-label: Customers
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
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
source-wordcount: '408'
ht-degree: 0%
---
# ACSD-58735: l’amministratore con restrizioni non può visualizzare i carrelli acquisti abbandonati sull’account del cliente per il sito web associato

La patch ACSD-58735 risolve il problema che impediva a un utente amministratore con un ruolo limitato di visualizzare i carrelli acquisti dei clienti abbandonati dalla scheda Commerce **[!UICONTROL Admin]** > **[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]** > **[!UICONTROL Select Cart]** > **[!UICONTROL Shopping Cart]**.

Il problema si verifica perché quando si visualizza la vista a griglia per più siti web, se per impostazione predefinita nel pannello di amministrazione viene caricato un carrello abbandonato, non viene visualizzato l’ID store associato.

Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55. L’ID della patch è ACSD-58735. Il problema è pianificato per essere risolto in Adobe Commerce 2.5.0.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Gli amministratori con restrizioni non possono visualizzare i carrelli acquisti abbandonati sulla pagina dell’account del cliente nel pannello di amministrazione.

<u>Passaggi da riprodurre</u>:

1. Crea un ruolo di amministratore con accesso a uno solo dei siti web.
1. Crea un carrello abbandonato.
1. Accedi come utente amministratore con privilegi completi. Controlla **[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]** e osserva che il carrello viene visualizzato.
1. Selezionare **[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]** come utente amministratore con restrizioni.

<u>Risultati previsti</u>:

L’amministratore con restrizioni può visualizzare i carrelli abbandonati per il sito web associato.

<u>Risultati effettivi</u>:

L’amministratore con restrizioni non visualizza i carrelli acquisti abbandonati per il sito web associato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
