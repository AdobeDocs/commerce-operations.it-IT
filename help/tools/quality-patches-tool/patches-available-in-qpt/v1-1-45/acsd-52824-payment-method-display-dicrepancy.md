---
title: 'ACSD-52824: Metodi di pagamento disattivati visualizzati per i clienti aziendali'
description: Applica la patch ACSD-52824 per risolvere il problema di Adobe Commerce, in cui  [!DNL PayPal Express], [!DNL Google Pay], and [!DNL Apple Pay] i metodi di pagamento vengono visualizzati per i clienti aziendali nonostante siano disabilitati nelle impostazioni aziendali.
feature: Payments, B2B, Shopping Cart
role: Admin, Developer
exl-id: 39d67de6-1796-4067-ae7a-ef17fcf794e5
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 0%

---

# ACSD-52824: Metodi di pagamento disattivati visualizzati per i clienti aziendali

La patch ACSD-52824 risolve il problema per cui i metodi di pagamento [!DNL PayPal Express], [!DNL Google Pay] e [!DNL Apple Pay] vengono visualizzati per i clienti della società nonostante siano disabilitati nelle impostazioni della società. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.45. L’ID della patch è ACSD-52824. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

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
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
