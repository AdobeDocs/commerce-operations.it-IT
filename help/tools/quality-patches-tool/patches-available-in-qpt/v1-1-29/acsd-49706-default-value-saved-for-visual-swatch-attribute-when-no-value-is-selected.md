---
title: 'ACSD-49706: valore predefinito salvato per l’attributo campione visivo quando non è selezionato alcun valore'
description: Applicate la patch ACSD-49706 per risolvere il problema Adobe Commerce, se per un attributo di campione visivo non è selezionato alcun valore, in cui viene salvato un valore predefinito.
feature: Admin Workspace, Attributes
role: Admin
exl-id: fa3cb0a1-f898-4826-aa64-efeba1af58a8
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '404'
ht-degree: 0%

---

# ACSD-49706: valore predefinito salvato per l’attributo campione visivo quando non è selezionato alcun valore

La patch ACSD-49706 risolve il problema relativo al salvataggio di un valore predefinito per un attributo di campione visivo quando non viene selezionato alcun valore. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29. L’ID della patch è ACSD-49706. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Se non è selezionato alcun valore, viene salvato un valore predefinito per un attributo di campione visivo.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**.
1. Fare clic su **[!UICONTROL Add New Attribute]**.
1. Compila i campi.

   * Ad esempio, scegli il tipo di input *[!UICONTROL Visual Swatch]* e aggiungi più opzioni (come *Rosso*, *Verde*). Assicurati di scegliere una di queste opzioni come predefinita.
   * Fare clic su **[!UICONTROL Save Attribute]**.

1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Attribute Set]**.
1. Modifica il set di attributi *[!UICONTROL Default]*.
1. Sposta *[!UICONTROL New Attribute]* dalla colonna *[!UICONTROL Unassigned Attributes]* alla cartella *[!UICONTROL Product Details]* nella colonna centrale.

   * Fare clic su **[!UICONTROL Save]**.

1. Creare un nuovo prodotto utilizzando il set di attributi *[!UICONTROL Default]*.

   * Lascia *[!UICONTROL New Attribute]* vuoto e salvalo.

1. Una volta salvato, viene visualizzato un valore in *[!UICONTROL New Attribute]*.

<u>Risultati previsti</u>:

Nessun valore assegnato a *[!UICONTROL New Attribute]* per impostazione predefinita.

<u>Risultati effettivi</u>:

All’attributo viene applicato un valore predefinito al momento del salvataggio di un prodotto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
