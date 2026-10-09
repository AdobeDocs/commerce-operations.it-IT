---
title: 'ACSD-51114: i prodotti casuali scompaiono dai cataloghi di grandi dimensioni quando è abilitata l’indicizzazione asincrona'
description: Applica la patch ACSD-51114 per risolvere il problema di Adobe Commerce. I prodotti Random scompaiono dai cataloghi di grandi dimensioni quando è abilitata l’indicizzazione asincrona.
feature: Catalog Management, Categories, Products
role: Admin
exl-id: ab1816ef-fb09-46e7-8102-32865f806874
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
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
source-wordcount: '391'
ht-degree: 0%
---
# ACSD-51114: i prodotti casuali scompaiono dai cataloghi di grandi dimensioni quando è abilitata l’indicizzazione asincrona

>[!NOTE]
>
>Questa patch è obsoleta.

La patch ACSD-51114 risolve il problema Prodotti casuali scomparsi da cataloghi di grandi dimensioni quando l’indicizzazione asincrona è abilitata. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.30. L’ID della patch è ACSD-51114. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]:Search per le patch].Utilizzare l&#39;ID della patch come parola chiave di ricerca per individuare la patch.

## Problema

I prodotti casuali scompaiono dai cataloghi di grandi dimensioni quando è abilitata l’indicizzazione asincrona.

<u>Passaggi da riprodurre</u>:

1. Crea un set di 10 prodotti.
1. Imposta tutti gli indicizzatori sulla modalità **[!UICONTROL Update on Save]**.
1. Crea una categoria e assegna a essa tutti i prodotti.
1. Disattiva tutti i prodotti.
1. Apri la categoria e verifica che non vi siano prodotti.
1. Imposta tutti gli indicizzatori sulla modalità **[!UICONTROL Update on Schedule]**.
1. Impostare `DEFAULT_BATCH_SIZE` su 2 in `lib/internal/Magento/Framework/Mview/View.php#L31`.
1. Abilitare i prodotti nell&#39;ordine seguente: 1°, 9°, 2°, 5°, 10°, 3°.
1. Esegui il comando cron.
1. Apri nuovamente la categoria.

<u>Risultati previsti</u>:

Vengono visualizzati tutti i prodotti abilitati.

<u>Risultati effettivi</u>:

Tutti i prodotti abilitati non vengono visualizzati.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
