---
title: 'BB2B-2598: aggiunge la funzionalità di caching per memorizzare le query GraphQl in Config, currency, country, countries e availableStores'
description: Applica la patch BB2B-2598 per aggiungere la funzionalità di caching alle query GraphQl storeConfig, currency, country, countries e availableStores.
feature: B2B, GraphQL, Cache
role: Admin
exl-id: b842fab4-d2c0-4ef1-be13-182f09015cd7
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# BB2B-2598: aggiunge funzionalità di caching alle query GraphQl `storeConfig`, `currency`, `country`, `countries` e `availableStores`

La patch BB2B-2598 aggiunge la funzionalità di caching alle query GraphQl `storeConfig`, `currency`, `country`, `countries` e `availableStores`. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30. L’ID della patch è BB2B-2598. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7-beta1.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Non è possibile memorizzare nella cache le query di GraphQL `availableStores`, `countries`, `country`, `currency`, `storeConfig` e `customAttributeMetadata`.

<u>Prerequisiti</u>:

* Il server punta a [!DNL Varnish] per il proxy al backend di Adobe Commerce.
* L&#39;impostazione di configurazione `system/full_page_cache/caching_application` è impostata su *2* ([!DNL Varnish]) oppure passare ad Amministrazione Adobe Commerce > **[!UICONTROL Stores]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Caching Application]** > e impostarla su [!DNL Varnish].

Dopo aver applicato la patch, esegui i passaggi seguenti per assicurarti che la funzionalità di caching sia ora disponibile:

1. Invia la richiesta `GET` a una qualsiasi delle query GraphQL elencate in precedenza, utilizzando qualsiasi campo arbitrario.
1. Invia di nuovo la richiesta senza modifiche; noterai che è molto più veloce. La richiesta non viene inviata al backend ma è completamente gestita da [!DNL Varnish] come hit della cache.
1. Se sono necessarie ulteriori bozze, commentare l&#39;annullamento dell&#39;intestazione `X-Magento-Debug` presente in [VCL](https://github.com/magento/magento2/blob/026e5b29a5edfd619bbdea62d636b3cab2ea03b4/app/code/Magento/PageCache/etc/varnish6.vcl#L227), quindi riavviare [!DNL Varnish] ed eseguire nuovamente i passaggi precedenti.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
