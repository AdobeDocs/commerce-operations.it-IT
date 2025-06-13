---
title: 'ACSD-56979: immagini del prodotto rimosse dopo l’aggiornamento di staging eliminate'
description: Applicare la patch ACSD-56979 per risolvere il problema di Adobe Commerce, in cui le immagini del prodotto vengono rimosse dopo l’eliminazione di un aggiornamento di staging
feature: Products
role: Admin, Developer
exl-id: 1e0fbd5c-285b-408e-ba52-72619e29167b
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-56979: immagini del prodotto rimosse dopo l’aggiornamento di staging eliminate

La patch ACSD-56979 risolve il problema della rimozione delle immagini del prodotto dopo l’eliminazione di un aggiornamento di staging. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49. L’ID della patch è ACSD-56979. Il problema è pianificato per essere risolto in Adobe Commerce 2.5.0.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con Adobe Commerce e Magento Open Source:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.6-p7

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le immagini del prodotto vengono rimosse dopo l’eliminazione di un aggiornamento di staging.

<u>Passaggi da riprodurre</u>:

1. Nella barra laterale di amministrazione di Commerce, vai a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** e crea un prodotto.
1. In **[!UICONTROL Images and Videos]**, carica un&#39;immagine e salva il prodotto.
1. Nella casella **[!UICONTROL Scheduled Changes]** selezionare **[!UICONTROL Schedule New Update]**.
   1. Scegli una data di inizio di alcuni minuti nel futuro.
   1. Non scegliere una data di fine.
1. Nella casella **[!UICONTROL Scheduled Changes]** selezionare il collegamento **[!UICONTROL View/Edit]**.
1. Vai a **[!UICONTROL Remove from Update]** > **[!UICONTROL Delete the Update]** e seleziona **[!UICONTROL Done]**.
1. Aggiorna la pagina.

<u>Risultati previsti</u>:

Poiché l’aggiornamento viene rimosso prima della data di inizio pianificata, il prodotto deve rimanere lo stesso.

<u>Risultati effettivi</u>:

Il contenuto dell&#39;immagine viene perso e viene visualizzato zero byte.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
