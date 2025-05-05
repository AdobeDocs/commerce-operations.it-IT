---
title: 'MDVA-43414: errore irreversibile PHP durante l''esecuzione di "inventory.Reservation.updateSalabilityStatus"'
description: La patch MDVA-43414 risolve l’errore irreversibile PHP che si verifica durante l’esecuzione del consumer di coda "inventory.Reservation.updateSalabilityStatus" sugli SKU numerici. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12. L'ID della patch è MDVA-43414. Il problema è stato risolto in Adobe Commerce 2.4.2.
feature: Inventory, Orders
role: Admin
exl-id: 893a5665-ff1b-4862-a984-d9abf642fba3
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# MDVA-43414: errore irreversibile PHP durante l&#39;esecuzione di &quot;inventory.Reservation.updateSalabilityStatus&quot;

La patch MDVA-43414 risolve l&#39;errore irreversibile PHP che si verifica durante l&#39;esecuzione del consumer di coda `inventory.reservations.updateSalabilityStatus` sugli SKU numerici. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12. L&#39;ID della patch è MDVA-43414. Il problema è stato risolto in Adobe Commerce 2.4.2.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.6-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.6 - 2.3.7-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Si verifica un errore irreversibile PHP durante l’esecuzione del consumer di code &quot;inventory.Reservations.updateSalabilityStatus&quot; su SKU numeriche.

<u>Prerequisiti</u>:

Moduli inventario installati.

<u>Passaggi da riprodurre</u>:

1. Creare un&#39;origine di magazzino personalizzata e assegnarla a una nuova scorta di magazzino.
1. Crea un prodotto con origine inventario personalizzata.
1. Assicurati che lo SKU del prodotto sia un valore intero.
1. Effettua un ordine.
1. Eseguire il comando `bin/magento queue:consumer:start inventory.reservations.updateSalabilityStatus`.

<u>Risultati previsti</u>:

La coda viene avviata senza errori.

<u>Risultati effettivi</u>:

Si verifica un errore irreversibile PHP:

```PHP
PHP Fatal error:  Uncaught TypeError: Argument 1 passed to Magento\InventoryIndexer\Model\Queue\UpdateIndexSalabilityStatus\IndexProcessor::getIndexSalabilityStatus() must be of the type string, int given, called in /vendor/magento/module-inventory-indexer/Model/Queue/UpdateIndexSalabilityStatus/IndexProcessor.php on line 119 and defined in /vendor/magento/module-inventory-indexer/Model/Queue/UpdateIndexSalabilityStatus/IndexProcessor.php:136
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
