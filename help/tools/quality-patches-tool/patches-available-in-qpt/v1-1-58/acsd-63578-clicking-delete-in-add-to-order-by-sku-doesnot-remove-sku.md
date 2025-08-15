---
title: 'ACSD-63578: se si fa clic sull''icona [!UICONTROL Delete] in [!UICONTROL Add to Order by SKU], lo SKU non viene rimosso'
description: Applicare la patch ACSD-63578 per risolvere il problema di Adobe Commerce, in cui se si fa clic sull'icona [!UICONTROL Delete] in [!UICONTROL Add to Order by SKU] nell'interfaccia di amministrazione, lo SKU non viene rimosso.
feature: Orders
role: Admin, Developer
exl-id: 12afceb5-db3c-4783-a532-93c4c71f05f4
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# ACSD-63578: se si fa clic sull&#39;icona **[!UICONTROL Delete]** in *[!UICONTROL Add to Order by SKU]*, lo SKU non viene rimosso

La patch ACSD-63578 risolve il problema per cui se si fa clic sull&#39;icona **[!UICONTROL Delete]** in *[!UICONTROL Add to Order by SKU]* in Admin, lo SKU non viene rimosso. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58. L’ID della patch è ACSD-63578. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p7

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Se si fa clic sull&#39;icona **[!UICONTROL Delete]** in *[!UICONTROL Add to Order by SKU]* nell&#39;amministratore, lo SKU non viene rimosso dall&#39;ordine.

<u>Passaggi da riprodurre</u>:

1. Passare ad Admin > **[!UICONTROL Sales]** > **[!UICONTROL Orders]** e fare clic su **[!UICONTROL Create New Order]**.
1. Scegli un cliente.
1. Fare clic su **[!UICONTROL Add to Order by SKU]**.
   * Immettete uno SKU.
   * Fare clic sul pulsante **[!UICONTROL Add another]**.
1. Fare clic sull&#39;icona **[!UICONTROL Delete]**.

<u>Risultati previsti</u>:

* I prodotti vengono aggiunti e rimossi da un ordine in Admin.

<u>Risultati effettivi</u>:

* L&#39;icona **[!UICONTROL Delete]** non funziona.
* Si è verificato un errore nella console:

  `jquery.js:130 Refused to execute inline script because it violates the following Content Security Policy directive`

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
