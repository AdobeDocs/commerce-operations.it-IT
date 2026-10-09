---
title: '49843 ACSD: collegamento per il download del prodotto non disponibile dopo la fatturazione automatica con [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]'
description: Applicare la patch ACSD-49843 per risolvere il problema di Adobe Commerce in cui il collegamento di download del prodotto non è disponibile dopo la fatturazione automatica dell'articolo ordinato tramite un metodo di pagamento online quando [!UICONTROL Payment Action] è impostato su [!UICONTROL Intent Sale].
feature: Catalog Management, Configuration, Invoices, Orders, Storefront
role: Admin, Developer
exl-id: e990b550-fb32-48d2-9c39-2176d7ab34c9
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 591c578b-908e-5b79-a9d3-931dfe60c24c
    internal-label: Invoices
  - id: 4820f335-ec9f-5611-8fe3-f5b7e3e56967
    internal-label: Orders
  - id: d1e21356-0064-4f48-9089-16e3f0dbd2a6
    internal-label: Storefront
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
source-wordcount: '510'
ht-degree: 0%
---
# ACSD-49843: collegamento per il download del prodotto non disponibile dopo la fatturazione automatica con [!UICONTROL Payment Action] = [!UICONTROL Intent Sale]

La patch ACSD-49843 risolve il problema relativo alla mancata disponibilità del collegamento di download del prodotto dopo la fatturazione automatica dell&#39;articolo ordinato tramite un metodo di pagamento online quando [!UICONTROL Payment Action] è impostato su [!UICONTROL Intent Sale]. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.37. L’ID della patch è ACSD-49843. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.3.7-p4, 2.4.1 - 2.4.6-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il collegamento di download del prodotto non è disponibile dopo la fatturazione automatica dell&#39;articolo ordinato tramite un metodo di pagamento online quando [!UICONTROL Payment Action] è impostato su [!UICONTROL Intent Sale].

<u>Passaggi da riprodurre</u>:

1. Accedi all&#39;amministratore di Adobe Commerce e passa a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Configure Braintree]**.

   * Nel menu a discesa [!UICONTROL Payment Action], selezionare **[!UICONTROL Intent Sale]** e impostare *[!UICONTROL Enable Card Payments]* su *Sì*.

1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Downloadable Product Option]** > **[!UICONTROL Order Item status for Download]** e assicurati che sia impostato su *&quot;Fatturato&quot;*.
1. Nella vetrina, accedi come cliente.

   * Aggiungi al carrello qualsiasi prodotto scaricabile e un prodotto semplice.
   * Utilizza [!DNL Braintree Pay] per effettuare l&#39;ordine utilizzando l&#39;opzione della scheda.

1. Andare a **[!UICONTROL My Orders]** e verificare che la fattura sia creata automaticamente per l&#39;ordine e che entrambi gli stati dell&#39;articolo siano *&quot;Fatturati&quot;*.
1. Vai a **[!UICONTROL My Downloadable Products]** e osserva che il collegamento per il download non è ancora disponibile.
1. In Amministratore, vai a tale ordine e crea una spedizione per esso.
1. Nella vetrina, vai a **[!UICONTROL My Downloadable Products]** e osserva che il collegamento per il download è ora disponibile.

<u>Risultati previsti</u>:

Il collegamento di download è disponibile quando lo stato del prodotto scaricabile è *&quot;Fatturato&quot;*.

<u>Risultati effettivi</u>:

Il collegamento di download non è disponibile anche quando lo stato del prodotto scaricabile indica *&quot;Fatturato&quot;*. È disponibile solo dopo la creazione di una spedizione per il prodotto fisico.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
