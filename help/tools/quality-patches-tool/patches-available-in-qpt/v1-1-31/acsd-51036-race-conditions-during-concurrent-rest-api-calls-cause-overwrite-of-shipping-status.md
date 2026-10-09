---
title: 'ACSD-51036: le condizioni di concorrenza durante le chiamate API REST simultanee determinano una sovrascrittura dello stato di spedizione'
description: Applica la patch ACSD-51036 per risolvere il problema Adobe Commerce in presenza di race condition durante le chiamate REST API simultanee, causando la sovrascrittura dello stato di spedizione nella tabella articoli ordinati.
feature: REST, Orders, Shipping/Delivery
role: Admin
exl-id: 6150d072-05fe-4010-b31b-8ccde9cab656
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 04d3134c-2afb-5bd7-ac14-e19fa935e848
    internal-label: Shipping/Delivery
  - id: c4f010fa-1478-4300-a88d-706fbc036a7a
    internal-label: APIs and SDKs
subfeature_v2:
  - id: e0ca0e7a-9738-48d1-b98b-615468ab4aaf
    internal-label: REST API
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%
---
# ACSD-51036: le condizioni di gara durante le chiamate API REST simultanee determinano una sovrascrittura dello stato di spedizione nella tabella degli articoli ordinati

La patch ACSD-51036 risolve il problema in cui le race condition durante le chiamate API REST simultanee determinano una sovrascrittura dello stato di spedizione nella tabella articoli ordinati. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.31. L’ID della patch è ACSD-51036. Tieni presente che il problema è risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le condizioni di concorrenza durante le chiamate API REST simultanee determinano una sovrascrittura dello stato di spedizione nella tabella articoli ordinati.

<u>Passaggi da riprodurre</u>:

1. Crea un ordine con due elementi.
1. Voce fattura A.
1. Inviare contemporaneamente una richiesta di rimborso per l&#39;articolo A tramite API REST mentre si invia una richiesta di spedizione per l&#39;articolo B.
1. Passare all&#39;ordine in **[!UICONTROL Admin Panel]**.

<u>Risultati previsti</u>

Lo stato *[!UICONTROL Shipped 1]* deve essere presente per l&#39;elemento B nella tabella ordinata *[!UICONTROL Items]*.

<u>Risultati effettivi</u>

Stato *[!UICONTROL Shipped 1]* non presente per l&#39;elemento B nella tabella ordinata *[!UICONTROL Items]*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
