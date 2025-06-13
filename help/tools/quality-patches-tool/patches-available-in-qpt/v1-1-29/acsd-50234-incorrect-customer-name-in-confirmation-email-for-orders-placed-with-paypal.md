---
title: 'ACSD-50234: nome cliente errato nell''e-mail di conferma per gli ordini effettuati utilizzando  [!DNL PayPal]'
description: Applica la patch ACSD-50234 per risolvere il problema di Adobe Commerce in cui il nome del cliente non viene visualizzato correttamente nell'e-mail di conferma per gli ordini effettuati utilizzando  [!DNL PayPal].
feature: Admin Workspace, Communications, Orders, Payments
role: Admin
exl-id: 9a8a7cef-0166-4b4b-96a0-87fd4f1a0ef3
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '357'
ht-degree: 0%

---

# ACSD-50234: nome cliente errato nell&#39;e-mail di conferma per gli ordini effettuati utilizzando [!DNL PayPal]

La patch ACSD-50234 risolve il problema relativo alla visualizzazione errata del nome del cliente nell&#39;e-mail di conferma per gli ordini effettuati utilizzando [!DNL PayPal]. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29. L’ID della patch è ACSD-50234. Il problema è stato risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.4-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

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
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
