---
title: 'ACSD-45488: prodotto configurabile con più origini non restituito automaticamente in magazzino'
description: La patch ACSD-45488 risolve il problema se un prodotto configurabile con più sorgenti non viene restituito automaticamente in magazzino. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18. L’ID della patch è ACSD-45488. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.
feature: Configuration, Orders, Products, Returns
role: Admin
exl-id: 53f34e8e-00bd-4386-bebf-b15882e36da1
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# ACSD-45488: prodotto configurabile con più origini non restituito automaticamente in magazzino

La patch ACSD-45488 risolve il problema se un prodotto configurabile con più sorgenti non viene restituito automaticamente in magazzino. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18. L’ID della patch è ACSD-45488. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Un prodotto configurabile con più sorgenti non viene restituito automaticamente allo stock.

<u>Passaggi da riprodurre</u>:

1. Creare un&#39;origine di magazzino secondaria.
1. Crea un prodotto configurabile con due prodotti virtuali associati.
1. Assegnare i prodotti associati all&#39;origine scorte predefinita e impostare la quantità su uno.
1. Controlla `stock_status` da `cataloginventory_stock_status`.
1. Impostare entrambi i prodotti associati come *esauriti*.
1. Controlla `stock_status` da `cataloginventory_stock_status`.
1. Imposta entrambi i prodotti associati come *in magazzino*.
1. Controlla `stock_status` da `cataloginventory_stock_status`.

<u>Risultati previsti</u>:

Lo stato stock del prodotto configurabile viene aggiornato a *in magazzino* quando i prodotti associati sono impostati per essere in magazzino.

<u>Risultati effettivi</u>:

Lo stato stock del prodotto configurabile non viene aggiornato a *in stock* quando i prodotti associati sono impostati per essere in stock.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
