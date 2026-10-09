---
title: 'ACSD-50234: nome cliente errato nell''e-mail di conferma per gli ordini effettuati utilizzando [!DNL PayPal]'
description: Applicare la patch ACSD-50234 per risolvere il problema di Adobe Commerce, in cui il nome del cliente non viene visualizzato correttamente nell'e-mail di conferma per gli ordini effettuati utilizzando [!DNL PayPal].
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
exl-id: 9a8a7cef-0166-4b4b-96a0-87fd4f1a0ef3
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: bb03f6c4-cab9-560e-9d02-5816e1808d17
    internal-label: Communications
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
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
source-wordcount: '380'
ht-degree: 0%
---
# ACSD-50234: nome cliente errato nell&#39;e-mail di conferma per gli ordini effettuati utilizzando [!DNL PayPal]

La patch ACSD-50234 risolve il problema relativo alla visualizzazione errata del nome del cliente nell&#39;e-mail di conferma per gli ordini effettuati utilizzando [!DNL PayPal]. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.29. L’ID della patch è ACSD-50234. Il problema è stato risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.4-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;e-mail di conferma per gli ordini effettuati utilizzando [!DNL PayPal] mostra il nome cliente errato.

<u>Passaggi da riprodurre</u>

1. Abilita **[!UICONTROL PayPal Express Checkout]**.
1. Passa al front-end come ospite.
1. Aggiungi prodotti al carrello.
1. Estrai utilizzando **[!UICONTROL PayPal Express Checkout]** come metodo di pagamento.
1. Controlla l’e-mail di conferma dell’ordine.

<u>Risultati previsti</u>

L&#39;e-mail di conferma dell&#39;ordine, l&#39;e-mail di fattura e tutte le e-mail relative alla spedizione sono indirizzate al nome del cliente.

<u>Risultati effettivi</u>

L&#39;e-mail di conferma dell&#39;ordine, l&#39;e-mail di fattura e tutte le e-mail relative alla spedizione sono indirizzate a *Guest*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
