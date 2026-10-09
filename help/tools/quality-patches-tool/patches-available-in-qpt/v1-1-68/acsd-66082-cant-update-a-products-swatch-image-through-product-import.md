---
title: 'ACSD-66082: impossibile aggiornare l’immagine campione di un prodotto tramite l’importazione del prodotto'
description: Applica la patch ACSD-66082 per risolvere il problema di Adobe Commerce, se il caricamento di un file CSV con il campo swatch_image impostato su EMPTY_VALUE per annullare l’impostazione delle immagini campione genera un errore durante l’importazione.
feature: Products, Data Import/Export, Media
role: Admin, Developer
type: Troubleshooting
exl-id: 0bfff90e-5f1f-4c87-8a99-efc5bb0d814b
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
  - id: 4ca54350-01cb-5b22-8966-5f2873dc6d90
    internal-label: Media
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
source-wordcount: '405'
ht-degree: 0%
---
# ACSD-66082: impossibile aggiornare l’immagine campione di un prodotto tramite l’importazione del prodotto

La patch ACSD-66082 risolve il problema quando non era possibile aggiornare l’immagine campione di un prodotto tramite l’importazione del prodotto. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68. L’ID della patch è ACSD-66082. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.8-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Se si carica un file CSV con il campo `swatch_image` impostato su `EMPTY_VALUE` per annullare l&#39;impostazione delle immagini campione, il processo di importazione non riesce e viene restituito un errore.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto semplice. Vai a **[!UICONTROL Catalog]** > **[!UICONTROL Products]**. Fare clic sulla freccia giù accanto al pulsante **[!UICONTROL Add Product]** e scegliere **[!UICONTROL Simple Product]**. Imposta **[!UICONTROL SKU]** su *ABC*.
1. Carica un&#39;immagine PNG denominata *testing.png* in `var/import/images/`.
1. Crea un file CSV con il seguente contenuto:

   ```text
   sku,swatch_image,swatch_image_label
   ABC,testing.png,testing
   ```

1. Vai a **[!UICONTROL System]** > **[!UICONTROL Import]** per importare il file regolando le seguenti impostazioni:
   * **[!UICONTROL Entity type]**: *Prodotti*
   * **[!UICONTROL Import Behavior]**: *Aggiungi/Aggiorna*
   * Fare clic su **[!UICONTROL Choose File]** per selezionare il file CSV creato nel passaggio precedente da importare. L’importazione è andata a buon fine e il campione viene aggiunto.
1. Aggiorna il file CSV con il seguente contenuto:

   ```text
   sku,swatch_image,swatch_image_label
   ABC,__EMPTY__VALUE__,__EMPTY__VALUE__
   ```

1. Ripetere il processo di importazione.

<u>Risultati previsti</u>:

L&#39;immagine campione non è impostata.

<u>Risultati effettivi</u>:

Il processo di importazione genera un errore.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
