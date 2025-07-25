---
title: 'ACSD-60234: [!DNL PayPal] mostra un importo errato quando viene applicato lo sconto'
description: Applica la patch ACSD-60234 per risolvere il problema di Adobe Commerce in cui [!DNL PayPal] mostra un importo errato quando lo sconto viene applicato tramite il metodo di pagamento.
feature: Products, Configuration
role: Admin, Developer
exl-id: 2ce7bde5-02a4-4989-80d6-ab1be0ca5fe9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---

# ACSD-60234: [!DNL PayPal] mostra un importo errato quando viene applicato lo sconto

La patch ACSD-60234 risolve il problema in cui [!DNL PayPal] mostra un importo errato quando lo sconto viene applicato tramite il metodo di pagamento. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.51. L’ID della patch è ACSD-60234. Il problema è pianificato per essere risolto in Adobe Commerce 2.5.0.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

[!DNL PayPal] mostra un importo errato quando lo sconto viene applicato tramite il metodo di pagamento.

<u>Passaggi da riprodurre</u>:

1. Configura *[!DNL PayPal Express]* in **[!UICONTROL Stores]** > **[!UICONTROL Config]** > **[!UICONTROL Sales]** > **[!UICONTROL Payment methods]** > **[!DNL PayPal]** > **[!UICONTROL Express checkout]**.
   * [!UICONTROL Enable In-Context Checkout] può essere [!UICONTROL Yes] o [!UICONTROL NO], il problema si riproduce in entrambi gli scenari.
1. Crea un *[!UICONTROL Cart Rule]* in **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Cart Price Rules]** > **[!UICONTROL Add New Rule]**.
   * Condizione: se tutte queste condizioni sono vere: *[!UICONTROL Payment Method]* è *[!DNL PayPal Express Checkout]*.
   * Azioni: qualsiasi azione.
1. Crea un prodotto.
1. Vai alla vetrina, aggiungi il prodotto al carrello, quindi vai al passaggio **[!UICONTROL Payment Method]** nell&#39;estrazione.
1. Selezionare *[!DNL PayPal Express]* e verificare che lo sconto sia applicato correttamente.
1. Fare clic sul pulsante **[!DNL PayPal]**.
1. Accedi e osserva il contenuto della finestra a comparsa.

<u>Risultati previsti</u>:

L&#39;importo da pagare passato a [!DNL PayPal] include lo sconto così come è nel carrello.

<u>Risultati effettivi</u>:

L&#39;importo totale da pagare non include lo sconto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
