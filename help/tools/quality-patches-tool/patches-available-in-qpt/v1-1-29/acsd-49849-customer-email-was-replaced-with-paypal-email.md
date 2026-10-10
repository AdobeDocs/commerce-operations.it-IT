---
title: 'ACSD-49849: l''e-mail del cliente è stata sostituita con l''e-mail PayPal'
description: Applica la patch ACSD-49849 per risolvere il problema Adobe Commerce in cui l’e-mail del cliente è stata sostituita con l’e-mail PayPal al momento di effettuare un ordine con PayPal Express tramite GraphQL.
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
exl-id: 1d7a2bde-892a-4ded-a4b4-9450989c8aee
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
source-wordcount: '446'
ht-degree: 0%
---
# ACSD-49849: l&#39;e-mail del cliente è stata sostituita con l&#39;e-mail [!DNL PayPal]

La patch ACSD-49849 risolve il problema della sostituzione dell&#39;e-mail di un cliente con un&#39;e-mail di [!DNL PayPal's] durante l&#39;ordine con [!DNL PayPal Express] tramite GraphQL. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.29. L’ID della patch è ACSD-49849. Il problema è stato risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.5-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;e-mail di un cliente viene sostituita con un&#39;e-mail [!DNL PayPal's] quando si effettua un ordine con [!DNL PayPal Express] tramite GraphQL.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Payments]**.
1. Abilita e configura [!DNL PayPal Express] e imposta **[!UICONTROL Payment Action]** = **[!UICONTROL Sale]**.
1. Vai a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** e crea un prodotto semplice.
1. Completa il pagamento tramite GraphQL. Per ulteriori informazioni, consulta l&#39;[esercitazione sull&#39;estrazione di GraphQL](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/) nella documentazione per sviluppatori di Adobe Commerce.
1. Utilizza [!DNL PayPal Express] come metodo di pagamento.
1. Nota l&#39;e-mail utilizzata nel passaggio in cui [configura l&#39;e-mail per il carrello](https://developer.adobe.com/commerce/webapi/graphql/tutorials/checkout/set-email-address/) nella documentazione per sviluppatori di Adobe Commerce.
1. Dopo aver effettuato l’ordine, passa all’amministratore Adobe Commerce e controlla l’e-mail nell’ordine creato.

<u>Risultati previsti</u>:

L’e-mail è la stessa impostata durante il pagamento.

<u>Risultati effettivi</u>:

L&#39;e-mail impostata durante l&#39;estrazione viene sostituita dall&#39;e-mail impostata nell&#39;account [!DNL PayPal].

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
