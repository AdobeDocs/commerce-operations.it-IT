---
title: 'ACSD-52095: errore nella gestione del valore delle azioni durante l’esportazione del file CSV'
description: Applica la patch ACSD-52095 per risolvere il problema Adobe Commerce in cui il valore delle azioni di gestione del prodotto non è corretto durante l’esportazione del file CSV.
feature: Inventory, Products
role: Admin, Developer
exl-id: 1f8415aa-23c6-480a-b54d-37b2b2d3199a
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '366'
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
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) nella guida di [!DNL Quality Patches Tool].
