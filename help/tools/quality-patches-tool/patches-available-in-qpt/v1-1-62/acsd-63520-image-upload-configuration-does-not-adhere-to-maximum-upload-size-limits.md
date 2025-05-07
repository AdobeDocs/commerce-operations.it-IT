---
title: 'ACSD-63520: le immagini caricate tramite Configurazione caricamento immagine superano i limiti di dimensione configurati'
description: Applica la patch ACSD-63520 per risolvere il problema di Adobe Commerce per cui le immagini caricate tramite la configurazione di caricamento immagini nel pannello di amministrazione non rispettano i limiti configurati per la dimensione massima del caricamento.
feature: Media, Products
role: Admin, Developer
source-git-commit: 987d335f03d552763f75adb73890787abf235e66
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---


# ACSD-63520: le immagini caricate tramite [!UICONTROL Image Upload Configuration] superano i limiti di dimensione configurati

La patch ACSD-63520 risolve un problema in cui le immagini caricate tramite [!UICONTROL Images Upload Configuration] non rispettano i limiti configurati per la dimensione massima di caricamento. Per risolvere questo problema, configurare le impostazioni [!UICONTROL Images Upload Configuration] nel pannello [!UICONTROL Admin]. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62. L’ID della patch è ACSD-63520. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.7

**Compatibile con le versioni di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione [!DNL Adobe Commerce] in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le immagini caricate tramite [!UICONTROL Images Upload Configuration] nel pannello [!UICONTROL Admin] non rispettano il limite massimo di dimensioni di caricamento.

<u>Passaggi da riprodurre</u>:

1. Accedere al pannello **[!UICONTROL Admin]**.
1. Passa a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Images Upload Configuration]** e imposta:
   * Qualità: 100
   * Abilita ridimensionamento front-end: sì
   * Larghezza massima: 800
   * Altezza massima: 600
1. Espandi **[!UICONTROL Media Gallery Image Optimization]** e imposta:
   * Abilita ottimizzazione immagine: sì
   * Larghezza massima: 1000
   * Altezza massima: 1000
1. Passa a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Configurable Product]**.
   1. Aggiungi **[!UICONTROL Product Name]**, **[!UICONTROL SKU]** e **[!UICONTROL Price]**.
   1. Fare clic su **[!UICONTROL Create Configurations]**, selezionare **[!UICONTROL Attributes]** e fare clic su **[!UICONTROL Next]**.
   1. Scegliere le dimensioni (S, M, L, XL), fare clic su **[!UICONTROL Next]**.
   1. In **[!UICONTROL Images]**, selezionare **[!UICONTROL Apply single set of images to all SKUs]**.
   1. Caricare un&#39;immagine (minimo 1024x1024), fare clic su **[!UICONTROL Next]**.
   1. Fare clic su **[!UICONTROL Generate Product]**.
1. Fare clic su **[!UICONTROL Save]**.

<u>Risultati previsti</u>:

Le immagini devono rispettare i limiti configurati per le dimensioni di caricamento e di ridimensionamento.

<u>Risultati effettivi</u>:

Le immagini non vengono ridimensionate e superano i limiti configurati per le dimensioni di caricamento.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
