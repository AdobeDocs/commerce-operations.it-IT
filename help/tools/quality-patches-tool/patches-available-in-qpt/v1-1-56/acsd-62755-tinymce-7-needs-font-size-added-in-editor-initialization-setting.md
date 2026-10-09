---
title: 'ACSD-62755: [!DNL TinyMCE] 7 richiede che le impostazioni di inizializzazione dell''editor e le dimensioni e il tipo di carattere siano stati aggiunti'
description: Applicare la patch ACSD-62755 per risolvere il problema di Adobe Commerce per cui [!DNL TinyMCE] 7 richiede che *font size* e *font family* siano aggiunti in modo specifico nelle impostazioni di inizializzazione dell'editor.
feature: Page Content, Page Builder, Admin Workspace
role: Admin, Developer
exl-id: f61dc7b6-ac6b-45eb-a0a2-f3f0bff4422b
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 17d326fa-534a-55a5-b46f-8ae1de1e2f75
    internal-label: Page Content
  - id: cc250cf1-34eb-4863-80d0-d170d45ea067
    internal-label: Developer tools
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: ed510963-0b8c-4764-86f6-f3c7735bc334
    internal-label: Page Builder
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
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
source-wordcount: '328'
ht-degree: 0%
---
# ACSD-62755: [!DNL TinyMCE] 7 richiede che le impostazioni di inizializzazione dell&#39;editor e le dimensioni e il tipo di carattere siano stati aggiunti

La patch ACSD-62755 risolve il problema per cui [!DNL TinyMCE] 7 richiede che i selettori *font size* e *font family* siano aggiunti in modo specifico nelle impostazioni di inizializzazione dell&#39;editor. Questa patch è disponibile con [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 installato. L’ID della patch è ACSD-62755. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p10

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p11, 2.4.5-p10, 2.4.6-p8, 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

[!DNL TinyMCE] 7 richiede che i selettori *font size* e *font family* siano aggiunti in modo specifico nelle impostazioni di inizializzazione dell&#39;editor.

<u>Passaggi da riprodurre</u>:

Vai a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Content]** e seleziona *[!UICONTROL Show Editor]*.

<u>Risultati previsti</u>:

I selettori *Dimensione font* e *Famiglia font* sono visibili nell&#39;editor di WYSIWYG.

<u>Risultati effettivi</u>:

Il selettore *Dimensione font* non è presente nell&#39;editor di WYSIWYG.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
