---
title: 'ACSD-62056: se MSI è installato, il caricamento dell’immagine per il prodotto configurabile non riesce'
description: Applica la patch ACSD-62056 per risolvere il problema di Adobe Commerce per cui le immagini per i prodotti configurabili non vengono aggiunte se è installato MSI.
feature: Products, Media
role: Admin, Developer
exl-id: bab8e617-d80c-4456-8ade-bdc6b4294d26
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# ACSD-62056: se MSI è installato, il caricamento dell’immagine per il prodotto configurabile non riesce

La patch ACSD-62056 risolve il problema che impedisce l&#39;aggiunta di immagini per i prodotti configurabili se MSI è installato. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54. L’ID della patch è ACSD-62056. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando si modifica un prodotto configurabile con [!UICONTROL Inventory Management/MSI] abilitato, le opzioni per aggiungere immagini non funzionano. Questo problema riguarda sia le opzioni [!UICONTROL Apply a single set of images to all SKUs] che [!UICONTROL Apply unique images by attribute to each SKU].

<u>Prerequisiti</u>:

[!UICONTROL Inventory Management/MSI] moduli sono installati e abilitati.

<u>Passaggi da riprodurre</u>:

1. Crea una nuova origine.
1. Create un nuovo materiale e assegnate la nuova origine.
1. Modifica un prodotto configurabile.
1. Fare clic su **[!UICONTROL Edit Configurations]** > **[!UICONTROL Next]** > **[!UICONTROL Next]**.
1. Selezionate una delle seguenti opzioni e aggiungete un&#39;immagine.

   * [!UICONTROL Apply a single set of images to all SKUs]
   * [!UICONTROL Apply unique images by attribute to each SKU]

<u>Risultati previsti</u>:

Le immagini vengono aggiunte.

<u>Risultati effettivi</u>:

Le immagini non vengono aggiunte.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
