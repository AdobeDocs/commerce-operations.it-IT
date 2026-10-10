---
title: 'ACSD-51238: l’origine inventario viene rimossa quando si aggiorna un prodotto configurabile e si modifica il prezzo'
description: Applicare la patch ACSD-51238 per risolvere il problema di Adobe Commerce in cui l'origine inventario viene rimossa quando si aggiorna un prodotto configurabile e si modifica il prezzo.
feature: Configuration, Inventory, Orders, Products
role: Admin
exl-id: 785f012f-e064-4ac6-b559-9e9aa42c679c
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 8dc0e58b-adf0-51bb-8db5-bb36e3e656fb
    internal-label: Inventory
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%
---
# ACSD-51238: l’origine inventario viene rimossa quando si aggiorna un prodotto configurabile e si modifica il prezzo

La patch ACSD-51238 risolve il problema della rimozione dell&#39;origine inventario quando si aggiorna un prodotto configurabile e si modifica il prezzo. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.32. L’ID della patch è ACSD-51238. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’origine dell’inventario viene rimossa quando si aggiorna un prodotto configurabile e si modifica il prezzo.

<u>Passaggi da riprodurre</u>:

1. Installa **[!DNL Adobe Commerce]** con **[!DNL Inventory module]**
1. Vai a **[!UICONTROL Admin]** -> **[!UICONTROL Stores]** -> **[!UICONTROL Inventory]** e crea *due origini* e *due scorte*.
1. Creare un **[!UICONTROL configurable product]** e assegnarlo a **[!UICONTROL default sources]** o **[!UICONTROL newly created sources]**.
1. Fai clic su **[!UICONTROL next button]** e *salva* il prodotto.
1. Modificare lo stesso **[!UICONTROL Configurable Product]** e fare clic su **[!UICONTROL Edit Configuration]** all&#39;interno di **[!UICONTROL Configuration tab]**.
1. In `Step 3: Bulk Images,Price and Quantity`, modificare `price` e lasciare `Quantity` e `Images` rispettivamente in `Skip quantity at this time` e `Skip image uploading at this time`.
1. Fai clic su **[!UICONTROL next button]** e genera il prodotto.

<u>Risultati previsti</u>

La quantità per origine all&#39;interno di **[!UICONTROL Configuration tab]** non deve essere vuota.

<u>Risultati effettivi</u>

La quantità per origine in **[!UICONTROL Configuration tab]** è vuota.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
