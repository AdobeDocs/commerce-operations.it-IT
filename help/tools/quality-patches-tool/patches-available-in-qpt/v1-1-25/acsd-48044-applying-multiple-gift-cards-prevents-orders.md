---
title: 'ACSD-48044: l''applicazione di più gift card impedisce l''effettuazione di ordini'
description: Applica la patch ACSD-48044 per risolvere il problema Adobe Commerce, in cui l’applicazione di più carte regalo a un singolo ordine con spedizione multipla impedisce l’inserimento di ordini.
feature: Admin Workspace, Gift, Orders
role: Admin
exl-id: c7b72b1f-2f1b-4445-b842-5847d05d5ae9
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4fc0a729-4349-5307-bd06-1b4bfbaf5d0c
    internal-label: Gift
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
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
source-wordcount: '511'
ht-degree: 0%
---
# ACSD-48044: l&#39;applicazione di più gift card impedisce l&#39;effettuazione di ordini

La patch ACSD-48044 risolve il problema se l&#39;applicazione di più carte regalo a un singolo ordine con spedizione multipla impedisce di effettuare ordini. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.25. L’ID della patch è ACSD-48044. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.4 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;applicazione di più carte regalo a un singolo ordine con spedizione multipla impedisce l&#39;inserimento di ordini.

<u>Passaggi da riprodurre</u>:

1. Installa una versione pulita di Adobe Commerce.
1. Crea un prodotto semplice con un prezzo di $ 100 e un altro prodotto semplice con un prezzo di $ 10.
1. Accedi a [!UICONTROL Admin panel] e crea due gift card.

   * 02 KB8M0H0GRD = $50
   * 00GXM6SUGBLW = 25 $

1. Crea un cliente con due indirizzi.
1. Aggiungi due prodotti al carrello.

   * Aggiungi prima il prodotto da 10 $, quindi aggiungi il prodotto da 100 $. Il problema non può essere riprodotto se il prodotto da 100 $ viene aggiunto per primo.

1. Vai al carrello e aggiungi le due gift card create.
1. Fai clic su **[!UICONTROL Ship to Multiple Addresses]** nella pagina del carrello.
1. Assegna ogni prodotto a un indirizzo diverso.
1. Passare alla pagina **[!UICONTROL Shipping information]**.
1. Passare alla pagina **[!UICONTROL Billing information]**.
1. Vai alla pagina **[!UICONTROL Review Your Order]**, dove puoi vedere il problema.
1. Provi ad effettuare l&#39;ordine.

<u>Risultati previsti</u>:

* Le carte regalo vengono applicate correttamente all&#39;importo totale.
* Gli ordini vengono inseriti.

<u>Risultati effettivi</u>:

Gli importi delle gift card sono misti con un errore *&quot;Correggere il codice gift card.&quot;* al momento dell’ordine.

* Primo prodotto:

  * Rimuovi gift card (00GXM6SUGBLW) - $15,00
  * Rimuovi gift card (02KB8M0H0GRD) - $0,00

* Secondo prodotto:

  * Rimuovi gift card (00GXM6SUGBLW) - $25,00
  * Rimuovi gift card (02KB8M0H0GRD) - $ 35,00

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
