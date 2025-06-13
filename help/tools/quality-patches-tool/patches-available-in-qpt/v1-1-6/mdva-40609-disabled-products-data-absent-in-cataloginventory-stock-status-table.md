---
title: 'MDVA-40609: dati dei prodotti disabilitati assenti nella tabella cataloginventory_stock_status'
description: La patch MDVA-40609 risolve il problema per cui i dati dei prodotti disabilitati non vengono visualizzati nella tabella di indice "cataloginventory_stock_status", causando la visualizzazione di quantità di prodotti errate. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6. L'ID della patch è MDVA-40609. Il problema è stato risolto in Adobe Commerce 2.4.3.
feature: Catalog Management, Inventory, Orders, Products
role: Admin
exl-id: e207ee55-b6ce-4065-bae1-2be89dcf5092
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# MDVA-40609: dati dei prodotti disabilitati assenti nella tabella cataloginventory_stock_status

La patch MDVA-40609 risolve il problema che causa la mancata visualizzazione dei dati dei prodotti disabilitati nella tabella dell&#39;indice `cataloginventory_stock_status`, causando la visualizzazione di quantità di prodotti errate. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.6. L&#39;ID della patch è MDVA-40609. Il problema è stato risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I dati dei prodotti disattivati non vengono visualizzati nella tabella dell&#39;indice `cataloginventory_stock_status` e le quantità dei prodotti non sono corrette.

<u>Prerequisiti</u>:

Il modulo Inventario è installato.

<u>Passaggi da riprodurre</u>:

1. Configura due siti Web con store e visualizzazioni dello store.
1. Create un&#39;origine e un magazzino aggiuntivi.
1. Aggiungi un prodotto semplice:
   * Impostare Abilita prodotto su *No*.
   * Assegna due origini con Stato articolo Source = Instock e Qtà maggiori di zero.
1. Salva il prodotto.
1. Controlla la scheda **Quantità venduta prodotto**.

<u>Risultati previsti</u>:

Entrambi gli stock hanno un valore superiore a zero.

<u>Risultati effettivi</u>:

Un titolo ha valore zero.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
