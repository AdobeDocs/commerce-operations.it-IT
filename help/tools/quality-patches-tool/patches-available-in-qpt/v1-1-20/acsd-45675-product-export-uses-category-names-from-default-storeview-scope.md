---
title: 'ACSD-45675: l’esportazione del prodotto utilizza i nomi delle categorie dall’ambito di visualizzazione predefinito dell’archivio'
description: La patch ACSD-45675 risolve il problema relativo all’esportazione di prodotti che utilizza nomi di categoria dell’ambito predefinito di visualizzazione archivio. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.20. L’ID della patch è ACSD-45675. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.
feature: Categories, Data Import/Export, Products
role: Admin
exl-id: ebe72038-511d-43e1-bd65-e5b468342f05
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%
---
# ACSD-45675: l’esportazione del prodotto utilizza i nomi delle categorie dall’ambito di visualizzazione predefinito dell’archivio

La patch ACSD-45675 risolve il problema relativo all’esportazione di prodotti che utilizza nomi di categoria dell’ambito predefinito di visualizzazione archivio. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.20. L’ID della patch è ACSD-45675. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’esportazione del prodotto utilizza i nomi delle categorie dell’ambito di visualizzazione predefinito dell’archivio.

<u>Passaggi da riprodurre</u>:

1. Creare una visualizzazione dell&#39;archivio personalizzato **[!UICONTROL Thai]** nell&#39;archivio principale.
1. Imposta **[!UICONTROL Thai]** come visualizzazione predefinita dell&#39;archivio del sito Web principale.
1. Crea la seguente struttura di categorie in **[!UICONTROL Default Category]**:

   *[!UICONTROL Default category/Tea/Black]*

1. Selezionare la categoria **[!UICONTROL Tea]** e cambiare **[!UICONTROL Scope]** in **[!UICONTROL Thai]**.
1. Imposta **[!UICONTROL Category Name]** come **[!UICONTROL ชาดำ]**.
1. Creare un prodotto semplice **[!UICONTROL SP001]** e assegnare la categoria **[!UICONTROL Black]**.
1. Assicurarsi che il cron non venga eseguito.
1. Esportare un prodotto. Filtra per SKU e seleziona **[!UICONTROL SP001]**.
1. Controlla la colonna **[!UICONTROL categories]** nel file CSV esportato.

<u>Risultati previsti</u>:

Poiché non è stato selezionato alcun archivio durante l&#39;esportazione, è necessario ottenere un percorso di categoria simile al seguente: *[!UICONTROL Default Category/Tea/Black]*.

<u>Risultati effettivi</u>:

Il percorso della categoria contiene lingue miste: *[!UICONTROL Default Category/ชาดำ/Black]*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tools] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida dello strumento Patch di qualità.
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
