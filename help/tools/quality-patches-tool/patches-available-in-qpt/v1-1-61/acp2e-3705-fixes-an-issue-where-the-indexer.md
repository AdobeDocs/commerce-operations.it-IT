---
title: 'ACP2E-3705: l’esecuzione del cron "indexer_update_all_views" non riesce quando "MAGE_INDEXER_THREADS_COUNT" è impostato'
description: Applica la patch ACP2E-3705 per risolvere il problema Adobe Commerce per cui l’esecuzione del cron "indexer_update_all_views" non riesce quando è impostato "MAGE_INDEXER_THREADS_COUNT".
feature: Catalog Management, B2B
role: Admin, Developer
exl-id: 111325fa-8ed5-45f9-9e68-b52f4425d253
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# ACP2E-3705: l&#39;esecuzione del cron `indexer_update_all_views` non riesce quando `MAGE_INDEXER_THREADS_COUNT` è impostato

>[!NOTE]
>
>Questa patch sostituisce [ACSD-64112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-59/acsd-64112-indexer-update-all-views-cron-execution-fails.md) per le versioni 2.4.7 e successive.

La patch ACP2E-3705 risolve il problema in cui l&#39;esecuzione del cron `indexer_update_all_views` non riesce quando `MAGE_INDEXER_THREADS_COUNT` è impostato. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61. L’ID della patch è ACP2E-3705. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;esecuzione del cron `indexer_update_all_views` ha esito negativo quando `MAGE_INDEXER_THREADS_COUNT` è impostato su un valore maggiore di *2*, con effetti specifici sull&#39;indicizzatore [!UICONTROL Customer Segments] con B2B abilitato.

<u>Passaggi da riprodurre</u>:

1. Applica la patch QPT [ACSD-64112](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-59/acsd-64112-indexer-update-all-views-cron-execution-fails.md).
1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Category permissions]**.
1. Abilita **[!UICONTROL Category Permissions]**.
1. Impostare i seguenti indicizzatori sulla modalità **[!UICONTROL Update on Schedule]**:

   ```
   bin/magento indexer:set-mode schedule catalogpermissions_category catalogpermissions_product
   ```

1. Crea alcuni prodotti e assegnali a una categoria.
1. Esegui una reindicizzazione completa.
1. Passare a una categoria e impostare **[!UICONTROL Category Permissions]**.
1. Esegui il processo cron `indexer_update_all_views` con `MAGE_INDEXER_THREADS_COUNT` impostato su *8*.

<u>Risultati previsti</u>:

La reindicizzazione è stata completata senza errori.

<u>Risultati effettivi</u>:

Il processo cron `indexer_update_all_views` rileva il seguente errore:

```
Magento\Framework\DB\Adapter\TableNotFoundException: SQLSTATE[42S02]: Base table or view not found: 1146 Table 'magento.catalogpermissions_category_cl__tmp67acb6582cec12_69065236' doesn't exist, query was: SELECT MAX(id) as max, COUNT(*) as cnt FROM (SELECT `catalogpermissions_category_cl__tmp67acb6582cec12_69065236`.* FROM
```


## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: Aggiornamenti e patch > Applica patch nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
