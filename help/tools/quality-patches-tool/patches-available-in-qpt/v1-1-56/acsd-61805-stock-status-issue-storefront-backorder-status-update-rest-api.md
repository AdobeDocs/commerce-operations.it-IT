---
title: 'ACSD-61805: risolve un problema di stock nella vetrina dopo l’aggiornamento dello stato dell’ordine inevaso tramite API REST'
description: Applica la patch ACSD-61805 per risolvere il problema di Adobe Commerce, se i prodotti rimangono esauriti nella vetrina dopo l’aggiornamento dello stato dell’ordine inevaso tramite l’API REST
feature: REST, Catalog Management, Inventory
role: Admin, Developer
exl-id: ff85e747-6394-43db-a02a-87b1e5e59f00
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# ACSD-61805: risolve un problema di stock nella vetrina dopo l’aggiornamento dello stato dell’ordine inevaso tramite API REST

La patch ACSD-61805 risolve il problema se i prodotti rimangono esauriti nella vetrina dopo l’aggiornamento dello stato dell’ordine inevaso tramite API REST. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. L’ID della patch è ACSD-61805. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I prodotti rimangono esauriti nella vetrina dopo l’aggiornamento dello stato dell’ordine inevaso tramite API REST.

<u>Passaggi da riprodurre</u>:

1. Installa un’istanza pulita con dati di esempio.
1. Crea una nuova origine inventario.
1. Creare una nuova scorta di magazzino e assegnarvi la nuova origine.
1. Assegna la nuova origine al prodotto 24-MB01.
1. Imposta **[!UICONTROL Source Item Status]** su `In Stock` per entrambe le origini prodotto.
1. Impostare la quantità (**[!UICONTROL QTY]**) su *0* per entrambe le quantità di prodotto.
1. Salva il prodotto.
1. Recupera il token di amministrazione da questo URL endpoint: `/rest/default/V1/integration/admin/token`

   ```json
   {
     "username":"admin", 
     "password":"password" 
   }
   ```

1. Aggiornare il prodotto utilizzando l&#39;endpoint: `/rest/default/V1/products`

   ```json
   {
     "product":{
       "sku": "24-MB01",
       "extension_attributes": {
           "stock_item": {
               "stock_id": "1",
               "is_in_stock": "0",
               "use_config_backorders": "false",
               "backorders": "0"
           }
       }
     }
   }
   ```

1. Eseguire i job cron due volte (una volta per creare pianificazioni e una volta per eseguire la pianificazione):

   ```bash
   bin/magento cron:run
   ```

1. Vai al front-end e controlla il prodotto.

<u>Risultati previsti</u>:

Il prodotto deve essere *In magazzino*.

<u>Risultati effettivi</u>:

Prodotto *esaurito*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
