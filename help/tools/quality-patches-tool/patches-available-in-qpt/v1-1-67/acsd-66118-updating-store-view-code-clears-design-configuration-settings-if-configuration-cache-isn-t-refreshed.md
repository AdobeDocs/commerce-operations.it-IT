---
title: 'ACSD-66118: l''aggiornamento di [!UICONTROL Store View Code] cancella [!UICONTROL Design Configuration] impostazioni se [!UICONTROL Configuration Cache] non è aggiornato'
description: Applica la patch ACSD-66118 per risolvere il problema di Adobe Commerce per cui l'aggiornamento di [!UICONTROL Store View Code] cancella [!UICONTROL Design Configuration] (tema e impostazioni personalizzate) se [!UICONTROL Configuration Cache] non è aggiornato correttamente.
feature: Cache, Configuration, Themes
role: Admin, Developer
type: Troubleshooting
exl-id: ecfdff54-99e0-4dbe-a0bb-80f60aafc7b6
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 8b440f30-6794-5ed6-981f-391de4e9b0cc
    internal-label: Themes
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
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
source-wordcount: '347'
ht-degree: 0%
---
# ACSD-66118: l&#39;aggiornamento di **[!UICONTROL Store View Code]** cancella **[!UICONTROL Design Configuration]** impostazioni se **[!UICONTROL Configuration Cache]** non è aggiornato

La patch ACSD-66118 risolve il problema per cui l&#39;aggiornamento di **[!UICONTROL Store View Code]** cancella le impostazioni di **[!UICONTROL Design Configuration]** se **[!UICONTROL Configuration Cache]** non è aggiornato. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67. L’ID della patch è ACSD-66118. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le impostazioni di **[!UICONTROL Design Configuration]** (come il tema e le impostazioni personalizzate) vengono cancellate durante l&#39;aggiornamento del campo **[!UICONTROL Store View Code]**, se **[!UICONTROL Configuration Cache]** non viene aggiornato.

<u>Passaggi da riprodurre</u>:

1. Accedere al pannello **[!UICONTROL Admin]**.
2. Passa a **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL All Stores]**.
3. Modificare una visualizzazione archivio con un tema personalizzato configurato in **[!UICONTROL Content]** > *[!UICONTROL Design]* > **[!UICONTROL Configuration]**.
4. Cambia il campo **[!UICONTROL Code]** (ad esempio, da `storeview_1` a `storeview_main`).
5. Fare clic su **[!UICONTROL Save Store View]** per salvare le modifiche.
6. Aggiorna o riapri la pagina **[!UICONTROL Content]** > *[!UICONTROL Design]* > **[!UICONTROL Configuration]** per il **[!UICONTROL Store View]** aggiornato e non verrà selezionato alcun tema.

<u>Risultati previsti</u>:

Dopo aver aggiornato **[!UICONTROL Store View Code]**, **[!UICONTROL Design Configuration]** (incluso il tema e le impostazioni personalizzate) deve rimanere intatto.

<u>Risultati effettivi</u>:

**[!UICONTROL Design Configuration]** è cancellato. Il tema torna alle impostazioni predefinite e le impostazioni personalizzate andranno perse.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
