---
title: 'MDVA-40175: pulsanti di scelta non visualizzati durante il riordino'
description: La patch di MDVA-40175 risolve il problema relativo alla mancata visualizzazione dei pulsanti di scelta quando gli utenti tentano di riordinare il sistema. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10. L'ID della patch è MDVA-40175. Il problema è stato risolto in Adobe Commerce 2.4.3.
feature: Admin Workspace, Orders
role: Admin
exl-id: e84ff581-13ba-4f9f-9247-519b0b54807a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# MDVA-40175: pulsanti di scelta non visualizzati durante il riordino

La patch di MDVA-40175 risolve il problema relativo alla mancata visualizzazione dei pulsanti di scelta quando gli utenti tentano di riordinare il sistema. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10. L&#39;ID della patch è MDVA-40175. Il problema è stato risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I pulsanti di scelta non vengono visualizzati nella sezione Informazioni su pagamento e spedizione quando gli utenti tentano di riordinare.

<u>Prerequisiti</u>:

1. Viene creato un account cliente con un indirizzo di spedizione e un indirizzo di fatturazione.
1. Viene creato un prodotto semplice.
1. Sono configurati diversi metodi di consegna.
1. Viene creato almeno un ordine.

<u>Passaggi da riprodurre</u>:

1. Vai al pannello di amministrazione > **Vendite** > **Ordini**.
1. Seleziona l’ordine creato.
1. Fai clic sul collegamento **Visualizza**.
1. Fare clic sul pulsante **Riordina**.
1. Scorri verso il basso la pagina fino alla sezione **Informazioni su pagamento e spedizione**.
1. Fare clic su **Fare clic per modificare il metodo di spedizione**.

<u>Risultati previsti</u>:

Viene visualizzato l’elenco dei metodi di consegna con i pulsanti di scelta.

<u>Risultati effettivi</u>:

Viene visualizzato l’elenco dei metodi di consegna senza pulsanti di scelta.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
