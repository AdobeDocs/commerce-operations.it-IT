---
title: 'ACSD-64112: l’esecuzione del cron "indexer_update_all_views" non riesce quando è impostato "MAGE_INDEXER_THREADS_COUNT"'
description: Applica la patch ACSD-64112 per risolvere il problema Adobe Commerce, in cui l’esecuzione del cron "indexer_update_all_views" non riesce quando è impostato "MAGE_INDEXER_THREADS_COUNT".
feature: Catalog Management, B2B
role: Admin, Developer
exl-id: c95f179d-5291-481f-b655-08a9db608513
source-git-commit: 0078cf5fb6d6c3a8650762d7cdf5556de642e201
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 0%

---

# ACSD-64112: l&#39;esecuzione del cron `indexer_update_all_views` non riesce quando `MAGE_INDEXER_THREADS_COUNT` è impostato

>[!NOTE]
>
>Questa patch è stata sostituita con [ACP2E-3705](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-61/acp2e-3705-fixes-an-issue-where-the-indexer.md) per le versioni Adobe Commerce superiori alla versione 2.4.7.

La patch ACSD-64112 risolve il problema in cui l&#39;esecuzione del cron `indexer_update_all_views` non riesce quando `MAGE_INDEXER_THREADS_COUNT` è impostato. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59. L’ID della patch è ACSD-64112. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p10

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6-p10

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;esecuzione del cron `indexer_update_all_views` ha esito negativo quando `MAGE_INDEXER_THREADS_COUNT` è impostato su un valore maggiore di 2, in modo specifico per l&#39;indicizzatore [!UICONTROL Customer Segments] con B2B abilitato.

<u>Passaggi da riprodurre</u>:

1. Installa un’istanza pulita con B2B.
1. Abilita **[!UICONTROL B2B Company]** e **[!UICONTROL Shared Catalog]**.
1. Crea una categoria.
1. Crea alcuni prodotti e assegnali alla categoria.
1. Esegui una reindicizzazione completa.
1. Imposta i seguenti indicizzatori su **[!UICONTROL Update on Schedule]**:

   ```
   bin/magento indexer:set-mode schedule catalogpermissions_category catalogpermissions_product
   ```

1. Vai al backend e carica la categoria appena creata.
1. Fare clic su **[!UICONTROL Category Permissions]** e creare **[!UICONTROL New Permission]** per un gruppo di clienti esistente.
1. Verificare che l&#39;indicizzatore `catalogpermissions_category` disponga di un backlog. Esegui il seguente comando per verificarlo:

   ```
   bin/magento indexer:status
   ```

1. Impostare il seguente conteggio thread di indicizzazione in `env.php`:

   ```php
   'MAGE_INDEXER_THREADS_COUNT' => 8
   ```

1. Esegui il processo cron:

   ```
   bin/magento cron:run
   ```

<u>Risultati previsti</u>:

Il processo cron deve essere eseguito senza alcun problema.

<u>Risultati effettivi</u>:

Il processo cron `indexer_update_all_views` rileva il seguente errore:

```
report.CRITICAL: PDOException: There is no active transaction in /home/vendor/magento/zend-db/library/Zend/Db/Adapter/Pdo/Abstract.php:326
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Passaggi aggiuntivi necessari dopo l&#39;installazione della patch

Questa sezione è facoltativa; potrebbero essere necessari alcuni passaggi dopo l’applicazione della patch per risolvere il problema. 

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
