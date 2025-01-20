---
title: 'ACSD-63286: per visualizzare i prodotti assegnati al catalogo condiviso è necessaria la reindicizzazione manuale'
description: Applica la patch ACSD-63286 per risolvere il problema di Adobe Commerce, a causa del quale i prodotti assegnati a un catalogo condiviso tramite API non vengono visualizzati nella vetrina fino a quando non viene eseguita una reindicizzazione manuale.
feature: Products, REST
role: Admin, Developer
exl-id: 0435c06e-337e-4320-acc6-fa79a3b34008
source-git-commit: e18a41c5abb1cc8b407ff6c188acdeed0e8a7659
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-63286: per visualizzare i prodotti assegnati al catalogo condiviso è necessaria la reindicizzazione manuale

La patch ACSD-63286 risolve il problema per cui i prodotti assegnati a un catalogo condiviso tramite API non vengono visualizzati nella vetrina fino a quando non viene eseguita una reindicizzazione manuale. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57. L’ID della patch è ACSD-63286. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando i prodotti vengono assegnati a un catalogo condiviso tramite API, non vengono visualizzati sul front-end dopo l’esecuzione dei processi di indicizzazione parziale e cron del consumatore. Tuttavia, vengono visualizzate dopo una reindicizzazione completa manuale.

<u>Passaggi da riprodurre</u>:

1. Imposta [!DNL RabbitMQ] come servizio di coda.
1. Creare un catalogo condiviso e assegnargli una società.
1. Crea un prodotto semplice e assegnalo a una categoria.
1. Eseguire la reindicizzazione parziale.

   ```
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. Utilizzare la seguente richiesta API per assegnare il prodotto creato al catalogo condiviso `pub/rest/all/V1/sharedCatalog/<id>/assignProducts`:

   ```
   {
       "products":[{
           "sku": "24-MB06"
           }
       ]
   }
   ```

1. Eseguire la seguente cron per cancellare le code ed eseguire la reindicizzazione parziale.

   ```
   bin/magento cron:run --group=consumers
   ```

   ```
   bin/magento cron:run --group=index --bootstrap=standaloneProcessStarted=1
   ```

1. Accedi al front-end come utente aziendale.
1. Consultate la pagina delle categorie front-end. I prodotti appena assegnati non sono visibili.
1. Eseguire una reindicizzazione manuale:

   ```
   bin/magento index:reindex
   ```

<u>Risultati previsti</u>:

Il prodotto viene visualizzato sul front-end senza una reindicizzazione manuale.

<u>Risultati effettivi</u>:

Il prodotto viene visualizzato sul front-end solo dopo la reindicizzazione manuale.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.


## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
