---
title: 'ACSD-48212: l’importazione del prodotto assegna il prodotto a un’origine errata'
description: Applica la patch ACSD-48212 per risolvere il problema di Adobe Commerce, a causa del quale l’importazione del prodotto assegna il prodotto alla sorgente errata.
feature: Admin Workspace, Data Import/Export, Products
role: Admin
exl-id: d573d95b-95fc-4f59-b518-18088855a154
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 601e4abe-d9bf-58de-a779-32ed6794dcbe
    internal-label: Data Import/Export
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: bb2df8be-afdd-4818-b6b5-95ca1dd3bc3a
    internal-label: Admin workspace
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%
---
# ACSD-48212: l’importazione del prodotto assegna il prodotto a un’origine errata

La patch ACSD-48212 risolve il problema che causa l’importazione del prodotto, il quale viene assegnato all’origine errata. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.26. L’ID della patch è ACSD-48212. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’importazione del prodotto assegna il prodotto all’origine errata.

<u>Passaggi da riprodurre</u>:

1. Crea un&#39;origine magazzino secondaria.
1. Crea un prodotto solo con l&#39;origine di magazzino predefinita.
1. Esporta il prodotto.
1. Esegui `bin/magento cron:run`.
1. Apri **[!UICONTROL Catalog]** > **[!UICONTROL Prdoucts]**.
1. Seleziona il prodotto dalla griglia.
1. Annullare l&#39;assegnazione del titolo utilizzando il menu *[!UICONTROL mass action]*.
1. Esegui `bin/magento cron:run`.
1. Assegnare l&#39;origine secondaria utilizzando il menu *[!UICONTROL mass action]*.
1. Esegui `bin/magento cron:run`.
1. Eliminare il prodotto utilizzando il menu *[!UICONTROL mass action]*.
1. Esegui `bin/magento cron:run`.
1. Importa il prodotto utilizzando il file CSV esportato in precedenza.
1. Controllare l&#39;assegnazione di origine.

<u>Risultati previsti</u>:

Il prodotto viene assegnato solo all&#39;origine predefinita.

<u>Risultati effettivi</u>:

Il prodotto viene assegnato sia all&#39;origine predefinita che a quella secondaria.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
