---
title: 'ACSD-49042: prodotto con ordine infinito non può essere ordinato dalla vetrina'
description: Applica la patch ACSD-49042 per risolvere il problema di Adobe Commerce, a causa del quale non è possibile ordinare un prodotto con ordine inevaso dalla vetrina.
feature: Admin Workspace, Orders, Products, Storefront
role: Admin
exl-id: b94d06c0-806a-40be-bcd4-d6b8e5e474c3
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '444'
ht-degree: 0%
---
# ACSD-49042: prodotto con ordine infinito non può essere ordinato dalla vetrina

La patch ACSD-49042 risolve il problema che impediva di ordinare dalla vetrina un prodotto con ordine infinito. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.27. L’ID della patch è ACSD-49042. Il problema è stato risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.4-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’errore si verifica quando un prodotto con ordine inevaso infinito non può essere ordinato dalla vetrina.

<u>Passaggi da riprodurre</u>:

1. Imposta le seguenti impostazioni di configurazione:
   * **[!UICONTROL Display Out of Stock Products]** impostato su *[!UICONTROL Yes]*.
   * **[!UICONTROL Backorders]** impostato su *[!UICONTROL Allow Qty Below 0]*.
1. Aggiungi un nuovo **[!DNL custom stock]** e **[!DNL custom source]**.
1. Assegnare un prodotto a **[!DNL custom source]** e assicurarsi che sia impostato un numero di inventario (ad esempio: *10*).
1. Nella pagina di modifica del prodotto aprire **[!UICONTROL Advanced Inventory]**. Imposta **[!UICONTROL minimum quantity]** nel carrello, (ad esempio: *160*). La quantità deve essere superiore al magazzino.
1. Vai alla vetrina e acquista un prodotto per creare una prenotazione.
1. Cambia **[!UICONTROL product quantity]** in *0*. Il punto critico è salvare il prodotto da **[!DNL Admin panel]** quando è presente una prenotazione.
1. Apri **[!UICONTROL product page]** nella vetrina e prova ad aggiungere il prodotto al carrello.

<u>Risultati previsti</u>:

È possibile aggiungere il prodotto al carrello perché sono consentiti ordini inevasi per una quantità inferiore a *0*.

<u>Risultati effettivi</u>:

Il prodotto è esaurito.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
