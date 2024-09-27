---
title: 'ACSD-49973: Miglioramento delle prestazioni nel recupero dei prodotti in bundle tramite [!DNL GraphQL]'
description: Applica la patch ACSD-49973 per risolvere il problema di Adobe Systems Commerce in cui si verifica un degrado delle prestazioni durante il recupero di prodotti in bundle tramite [!DNL GraphQL].
feature: GraphQL, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# ACSD-49973: Miglioramento delle prestazioni nel recupero dei prodotti in bundle tramite [!DNL GraphQL]

La patch ACSD-49973 migliora le prestazioni recuperando i prodotti in bundle tramite [!DNL GraphQL]. Questa patch è disponibile quando è installata la [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) versione 1.1.30. L&#39;ID della patch è ACSD-49973. Nota: il problema è stato risolto in Adobe Systems Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Systems Commerce (tutti i metodi di distribuzione) 2.4.4 - 2.4.4-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Systems Commerce in uso, aggiornare il `magento/quality-patches` pacchetto alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]pagina](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) : Search for patches. Utilizzare l&#39;ID patch come parola chiave di ricerca per individuare la patch.

## Questione

La riduzione delle prestazioni si verifica quando si recuperano prodotti in bundle tramite [!DNL GraphQL].

<u>Prerequisiti</u>:

Crea 2000 pacchetti di prodotti utilizzando il [toolkit](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/generate-data.html) Performance.

<u>Passaggi da riprodurre</u>:

1. Abilita il logger di query [!DNL DB]:

   ```
   bin/magento dev:query-log:enable
   ```

1. Eseguire la seguente query [!DNL GraphQL]:

   ```GraphQL
   {
     products(
       search: "bundle"
       pageSize: 2000,
       sort: { relevance: DESC }
     ) {
       total_count
       items {
         name
         sku
       }
     }
   }
   ```

1. Controllare `var/log/db.log` per le richieste alla tabella `catalog_product_bundle_selection`.

<u>Risultati attesi</u>:

Le richieste alla `catalog_product_bundle_selection` tabella non devono essere presenti in `var/log/db.log`.

<u>Risultati effettivi</u>:

Sono presenti 2000 richieste da `catalog_product_bundle_selection` presentare che vengono attivate contemporaneamente, causando un degrado delle prestazioni.

## Applica la patch

Per applicare singole patch, utilizzare i seguenti collegamenti a seconda del metodo di distribuzione:

* Adobe Systems Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella [!DNL Quality Patches Tool] guida.
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Controlla se la patch è disponibile per il tuo problema di Adobe Systems Commerce utilizzando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) la [!UICONTROL Quality Patches Tool] guida.


Per informazioni su altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Search per le](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) patch nella [!DNL Quality Patches Tool] guida.
