---
title: 'ACSD-48634: [!DNL JS] errori quando [!DNL Google Analytics Content Experiments] è abilitato'
description: Applicare la patch ACSD-48634 per correggere gli errori [!DNL JS] in una pagina di aggiornamento [!DNL staging] quando [!DNL Google Analytics Content Experiments] è abilitato.
feature: Catalog Management, Categories, Console, Page Content
role: Admin
exl-id: 99368346-157f-4283-bb8c-192a62501717
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: 125c1f49-aefd-5f34-a252-288937f95f6b
    internal-label: Marketing Tools
subfeature_v2:
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
  - id: c4af0798-d497-5e6b-8380-19812c26d00a
    internal-label: Console
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 12%
---
# ACSD-48634: [!DNL JS] errori quando [!DNL Google Analytics Content Experiments] è abilitato

La patch ACSD-48634 corregge [!DNL JS] errori in una pagina di aggiornamento [!DNL staging] quando [!DNL Google Analytics Content Experiments] è abilitato. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.27. L’ID della patch è ACSD-48634. Il problema è stato risolto in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

[!DNL JS] errori si verificano in una pagina di aggiornamento [!DNL staging] quando [!DNL Google Analytics Content Experiments] è abilitato.

<u>Passaggi da riprodurre</u>:

1. In **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**, creare un altro sito Web, store e **[!UICONTROL Store View]**. Assicurarsi che **[!UICONTROL Store View]** sia *[!UICONTROL Enabled]*.
1. Configura **[!DNL Configure Google Analytics]** andando in **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Google API]**:
   * Per **[!DNL Main]** e altri siti Web [!DNL scope]:
     * **[!UICONTROL Enabled]**: *[!UICONTROL Yes]*
     * **[!UICONTROL Account type]**: *[!UICONTROL Google Tag Manager]*
     * **[!UICONTROL Anonymize IP]**: *[!UICONTROL Yes]*
     * **[!UICONTROL Enable Content Experiments]**: *[!UICONTROL Yes]*
     * **[!UICONTROL Container Id]**: *[!UICONTROL (GTM container ID)]*
     * **[!DNL Uncheck]** *[!UICONTROL Use Default]* per altri campi, ma non modificarli.
   * Per **[!DNL Default Config]** [!DNL scope]:
     * **[!UICONTROL Enabled]**: *[!UICONTROL Yes]*
     * **[!UICONTROL Account type]**: *[!UICONTROL Universal Analytics]*
     * **[!UICONTROL Account Number]**: *[!UICONTROL (Universal Analytics account number)]*
     * **[!UICONTROL Anonymize IP]**: *[!UICONTROL Yes]*
     * **[!UICONTROL Enable Content Experiments]**: *[!UICONTROL Yes]*
1. Disabilitare **[!DNL Configure Google Analytics]** su **[!DNL Default Config]** [!DNL scope] modificando **[!UICONTROL Enable]** da *[!UICONTROL Yes]* a *[!UICONTROL No]*. Assicurati di non cambiare altro!
1. Vai a **[!UICONTROL Catalog]** > **[!UICONTROL Categories]**.
1. Crea e modifica qualsiasi **[!UICONTROL category]** e aggiungi un aggiornamento pianificato:
   * Qualsiasi nome, data di inizio futura, data di fine futura ed eventuali modifiche in **[!UICONTROL category]** ([!UICONTROL For Example]: *[!UICONTROL disable category]*).
1. Salvare l&#39;aggiornamento e verificare la presenza di errori in [!DNL browser developer console].

<u>Risultati previsti</u>:

Nessun errore [!DNL JS] e le modifiche all&#39;aggiornamento [!DNL staging] sono state salvate correttamente.

<u>Risultati effettivi</u>:

[!DNL JS] errori sono visibili nella console, il modulo non è corretto e [!DNL spinner] non viene mai disabilitato dopo il salvataggio.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
