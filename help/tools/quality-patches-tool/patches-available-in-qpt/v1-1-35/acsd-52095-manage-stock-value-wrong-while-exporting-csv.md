---
title: 'ACSD-52095: errore nella gestione del valore delle azioni durante l’esportazione del file CSV'
description: Applica la patch ACSD-52095 per risolvere il problema Adobe Commerce in cui il valore delle azioni di gestione del prodotto non è corretto durante l’esportazione del file CSV.
feature: Inventory, Products
role: Admin, Developer
exl-id: 1f8415aa-23c6-480a-b54d-37b2b2d3199a
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 8dc0e58b-adf0-51bb-8db5-bb36e3e656fb
    internal-label: Inventory
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
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
source-wordcount: '400'
ht-degree: 0%
---
# ACSD-52095: il valore [!UICONTROL Manage Stock] non è corretto durante l&#39;esportazione del file CSV

La patch ACSD-52095 risolve il problema se il valore del prodotto `manage_stock` non è corretto durante l&#39;esportazione del file CSV. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.35. L’ID della patch è ACSD-52095. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.5-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il valore `manage_stock` è erroneamente impostato su 0 nel file CSV dopo l&#39;esportazione del prodotto.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** e imposta **[!UICONTROL Manage Stock]** = *[!UICONTROL No]*.
1. Crea un nuovo prodotto e salvalo.
1. Vai a **[!UICONTROL System]** > **[!UICONTROL Export]**.
1. Selezionare *[!UICONTROL Entity Type]* = *[!UICONTROL Products]* ed esportare i prodotti.
1. Controllare il file CSV generato: `manage_stock` = 0, `use_config_manage_stock` = 1.
1. Di nuovo vai a **[!UICONTROL Admin]** > **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Product Stock Options]** e imposta **[!UICONTROL Manage Stock]** = *[!UICONTROL Yes]*.
1. Vai a **Sistema** > **Esporta**.
Selezionare *[!UICONTROL Entity Type]* = *[!UICONTROL Products and export the products]*.
1. Controllare il file CSV generato: `manage_stock` = 0, `use_config_manage_stock` = 1.
1. Apri il prodotto nell&#39;Admin, vai a **[!UICONTROL Advanced Inventory]** e controlla il valore **[!UICONTROL Manage Stock]**.

<u>Risultati previsti</u>

Il valore **[!UICONTROL Manage Stock]** è *1* quando è abilitato per i prodotti.

<u>Risultati effettivi</u>

Il valore **[!UICONTROL Manage Stock]** è *0* quando è abilitato per i prodotti.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
