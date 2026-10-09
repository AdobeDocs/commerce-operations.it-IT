---
title: 'ACSD-52824: Metodi di pagamento disattivati visualizzati per i clienti aziendali'
description: Applicare la patch ACSD-52824 per risolvere il problema Adobe Commerce relativo alla visualizzazione dei metodi di pagamento [!DNL PayPal Express], [!DNL Google Pay] e [!DNL Apple Pay] per i clienti della società nonostante la disabilitazione delle impostazioni della società.
feature: Payments, B2B, Shopping Cart
role: Admin, Developer
exl-id: 39d67de6-1796-4067-ae7a-ef17fcf794e5
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 3dcbfa9e-51f8-569c-a0e4-7f59098f730f
    internal-label: Payments
  - id: df8eaa0e-dd74-553a-8ad5-28129f8e8d3d
    internal-label: Shopping Cart
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
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
source-wordcount: '445'
ht-degree: 0%
---
# ACSD-52824: Metodi di pagamento disattivati visualizzati per i clienti aziendali

La patch ACSD-52824 risolve il problema per cui i metodi di pagamento [!DNL PayPal Express], [!DNL Google Pay] e [!DNL Apple Pay] vengono visualizzati per i clienti della società nonostante siano disabilitati nelle impostazioni della società. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.45. L’ID della patch è ACSD-52824. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I metodi di pagamento disattivati vengono visualizzati per i clienti della società.

<u>Passaggi da riprodurre</u>:

1. Configurare e abilitare [!DNL PayPal Express Checkout]. Passa a **[!UICONTROL Basic Settings]** > seleziona **[!DNL PayPal Express Checkout]** e imposta l&#39;opzione per **[!UICONTROL Display on Shopping Cart]** su *Sì*.
1. Configurare [!DNL Braintree] e abilitare [!DNL Apple Pay] e [!DNL Google Pay] tramite [!DNL Braintree].
1. Passa a **[!UICONTROL Customers]** > **[!UICONTROL Companies]** e crea una nuova società.
1. Fare clic su **[!UICONTROL Advanced Settings]**, individuare **[!UICONTROL Applicable Payment Methods]** e scegliere **[!UICONTROL Selected Payment Methods]**.
1. In **[!UICONTROL Selected Payment Methods]** scegliere i metodi di pagamento abilitati e non associati a *[!DNL PayPal Express Checkout]*, *[!DNL Apple Pay]* o *[!DNL Google Pay]*. Selezionare ad esempio **[!UICONTROL Check/Money Order]**.
1. Dopo aver selezionato i metodi di pagamento appropriati, creare un nuovo cliente e associarlo alla società creata in precedenza.
1. Accedi con l&#39;account cliente associato alla società e procedi all&#39;aggiunta di articoli al carrello.
1. Presta attenzione al mini carrello, al carrello e alla fase di pagamento durante il processo di pagamento.

<u>Risultati previsti</u>:

Le opzioni di pagamento di [!DNL PayPal] e [!DNL Braintree] non sono visibili nel mini carrello e nel carrello.

<u>Risultati effettivi</u>:

Le opzioni di pagamento di [!DNL PayPal] e [!DNL Braintree] rimangono visibili nel mini carrello e nel carrello.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
