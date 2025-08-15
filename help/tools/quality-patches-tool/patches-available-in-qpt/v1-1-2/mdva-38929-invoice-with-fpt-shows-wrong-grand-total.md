---
title: 'MDVA-38929: la fattura con FPT mostra un totale errato'
description: La patch MDVA-38929 risolve il problema che la fattura con FPT presenta un totale complessivo errato quando l'ordine viene pagato con il credito del negozio. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2. L'ID della patch è MDVA-38929. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
feature: Invoices, Orders
role: Admin
exl-id: fd0ca2f3-c6bf-4f09-a0fa-c931df94158b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# MDVA-38929: la fattura con FPT mostra un totale errato

La patch MDVA-38929 risolve il problema che la fattura con FPT presenta un totale complessivo errato quando l&#39;ordine viene pagato con il credito del negozio. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2. L&#39;ID della patch è MDVA-38929. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La fattura con FPT mostra un totale complessivo errato quando l&#39;ordine viene pagato con il credito del negozio.

<u>Passaggi da riprodurre</u>:

1. Creare un cliente e assicurarsi che il cliente disponga di credito di punto vendita sufficiente per coprire l&#39;ordine.
1. Abilitare FPT e aggiungere FPT a un prodotto.
1. Dal front-end, accedi come il cliente ha appena creato.
1. Aggiungi il prodotto con FPT al carrello.
1. Pagare con il credito del negozio. Dovrebbe essere un ordine di paga pari a zero.
1. Passare a Ordini e fatturare manualmente l&#39;ordine.
1. Controllare il totale complessivo della fattura.

<u>Risultati previsti</u>:

* Il totale complessivo della fattura è zero.
* L&#39;importo totale pagato dell&#39;ordine è zero.

<u>Risultati effettivi</u>:

* Il totale complessivo della fattura mostra ancora l&#39;importo FPT.
* Il totale pagato mostra ancora l&#39;importo FPT.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
