---
title: 'ACSD-64118: le richieste di salvataggio simultaneo del prodotto per lo stesso prodotto causano incoerenza dei dati e voci duplicate'
description: Applica la patch ACSD-64118 per risolvere il problema di Adobe Commerce, in cui le richieste simultanee di salvataggio e aggiornamento dello stesso prodotto causano incoerenza dei dati o prodotti duplicati.
feature: REST
role: Admin, Developer
type: Troubleshooting
source-git-commit: 4235511ccbef028e1564d7626daadaa5beae0fd4
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---


# ACSD-64118: le richieste di salvataggio simultaneo del prodotto per lo stesso prodotto causano incoerenza dei dati e voci duplicate

La patch ACSD-64118 risolve il problema relativo alle richieste simultanee di salvataggio e aggiornamento dello stesso prodotto che causano incoerenza dei dati o duplicazione dei prodotti. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65. L’ID della patch è ACSD-64118. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p7

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6-p10

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le richieste simultanee di salvataggio e aggiornamento dello stesso prodotto causano incongruenze nei dati o la duplicazione dei prodotti.

<u>Passaggi da riprodurre</u>:

1. Configurare più processi per i consumatori in `env.php`:

   ```
   'multiple_processes' =>
       array (
           'async.operations.all' => 4,
       ),
   ```

1. Aggiungi un altro store e una nuova vetrina al sito web principale.
1. Invia una richiesta API in blocco all&#39;endpoint predefinito storeview `/rest/default/async/bulk/V1/products` con il seguente payload per creare un prodotto:

   ```
   [
     {
       "product": {
         "sku": "Test_Prod",
         "name": "Test Product",
         "attribute_set_id": 4
       }
     }
   ]
   ```

1. Utilizzare lo stesso payload per inviare una richiesta API in blocco al nuovo endpoint storeview `/rest/store/async/bulk/V1/products` per aggiornare il prodotto.
1. Svuota cache.
1. Eseguire processi cron.
1. Controllare la tabella `catalog_product_entity` per le voci del prodotto dei passaggi precedenti.

<u>Risultati previsti</u>:

* Nella tabella `catalog_product_entity` deve essere presente una singola voce per lo SKU del prodotto.
* La prima richiesta REST API deve creare una voce di database e tutte le richieste successive devono aggiornare tale voce.

<u>Risultati effettivi</u>:

Nella tabella `catalog_product_entity` sono presenti più voci per lo stesso SKU.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
