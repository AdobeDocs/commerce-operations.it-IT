---
title: 'MDVA-36021: gli utenti ricevono un messaggio di errore all''apertura dei dettagli dell''ordine'
description: La patch MDVA-36021 risolve il problema relativo al messaggio di errore *Call to a member function getId()* durante il tentativo di aprire i dettagli dell'ordine. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.1. L'ID della patch è MDVA-36021. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
feature: Orders
role: Admin
exl-id: 737479fe-f363-4974-9c58-7ed9cd113fdb
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# MDVA-36021: gli utenti ricevono un messaggio di errore all&#39;apertura dei dettagli dell&#39;ordine

La patch di MDVA-36021 risolve il problema relativo al messaggio di errore *Chiamata a una funzione membro getId()* durante il tentativo di aprire i dettagli dell&#39;ordine. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.1. L&#39;ID della patch è MDVA-36021. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce sull’infrastruttura cloud 2.4.1, 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.2-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando gli utenti tentano di aprire i dettagli dell&#39;ordine, nella pagina dei dettagli dell&#39;ordine in Admin viene visualizzato il seguente messaggio di errore: *report.CRITICAL: Errore: Chiamata a una funzione membro getId() sull&#39;array in /magento2ce/app/code/Magento/Sales/view/adminhtml/templates/order/totals/tax.phtml:62*.

<u>Prerequisiti</u>:

Il sistema deve avere impostazioni di imposta e ordini con aliquote specifiche.

<u>Passaggi da riprodurre</u>:

1. Accedi all’amministratore di Commerce.
1. Vai a **Vendite** > **Ordini** > **Apri ordine**.

<u>Risultati previsti</u>:

L’ordine viene aperto senza errori.

<u>Risultati effettivi</u>:

Viene visualizzato un messaggio di errore simile al seguente: *report.CRITICAL: Errore: Chiamata a una funzione membro getId() nell&#39;array in /magento2ce/app/code/Magento/Sales/view/adminhtml/templates/order/totals/tax.phtml:62*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
