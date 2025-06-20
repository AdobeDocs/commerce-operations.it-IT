---
title: 'MDVA-41139: prodotto configurabile esaurito dopo l''importazione del prodotto'
description: La patch MDVA-41139 risolve il problema che causa l'esaurimento delle scorte del prodotto configurabile dopo l'importazione quando la quantità del prodotto semplice = 0 per una delle sue origini. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8. L'ID della patch è MDVA-41139. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
feature: Data Import/Export, Configuration, Orders, Products
role: Admin
exl-id: 7366230c-3b7f-4211-9f0d-55a528dffdbd
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---

# MDVA-41139: prodotto configurabile esaurito dopo l&#39;importazione del prodotto

La patch MDVA-41139 risolve il problema che causa l&#39;esaurimento delle scorte del prodotto configurabile dopo l&#39;importazione quando la quantità del prodotto semplice = 0 per una delle sue origini. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8. L&#39;ID della patch è MDVA-41139. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il prodotto configurabile diventa esaurito dopo l’importazione del prodotto quando la quantità del prodotto semplice = 0 per una delle sue origini.

<u>Prerequisiti</u>:

I moduli di inventario sono installati.

<u>Passaggi da riprodurre</u>:

1. Create una nuova origine e un nuovo materiale.
1. Crea un prodotto configurabile con prodotti secondari assegnati all’origine predefinita e alla nuova origine.
1. Impostate il valore del materiale di default per ciascun prodotto figlio = 0 e per altro materiale > 0.
1. Il prodotto configurabile è disponibile.
1. Esporta questo prodotto e importalo di nuovo.

<u>Risultati previsti</u>:

Il prodotto configurabile è in magazzino perché la seconda origine ha quantità > 0.

<u>Risultati effettivi</u>:

Il prodotto configurabile è esaurito.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
