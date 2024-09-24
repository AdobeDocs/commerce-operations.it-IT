---
title: '[!DNL ACSD-47280]: la disattivazione del catalogo condiviso genera risultati di ricerca prodotti errati'
description: Applica la patch  [!DNL ACSD-47280]  per correggere la visualizzazione dei risultati di ricerca corretti quando la funzionalità di catalogo condiviso è disabilitata.
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# [!DNL ACSD-47280]: la disabilitazione del catalogo condiviso genera risultati di ricerca prodotti errati

La patch [!DNL ACSD-47280] corregge la visualizzazione dei risultati di ricerca corretti quando la funzionalità [!DNL shared catalog] è disabilitata. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.22. [!DNL patch ID] è [!DNL ACSD-47280]. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.5

**Compatibile con le versioni di Adobe Commerce:**
* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizzare [!DNL patch ID] come parola chiave di ricerca per individuare la patch.

## Problema

La disabilitazione di [!DNL shared catalog] genera risultati di ricerca prodotti errati.

<u>Prerequisiti</u>:

* [!DNL B2B] moduli installati

<u>Passaggi da riprodurre</u>:

1. Creare un secondo sito Web.
1. Assegna un prodotto al secondo sito Web.
1. Controlla i prodotti sul **secondo sito Web** utilizzando [!DNL GraphQL]:

   ```GraphQL
   {
     products(search: "bag", pageSize: 2) {
       total_count
       items {
         name
         sku
       }
       page_info {
         page_size
         current_page
       }
     }
   }
   ```

1. Abilita **[!UICONTROL Shared Catalog]** su [!DNL scope] predefinito.
1. La richiesta [!DNL GraphQL] non mostra più alcun prodotto per il secondo sito Web, che è il risultato corretto.
1. Andare al [!DNL scope] del secondo sito Web e disabilitare **[!UICONTROL Company]**.

<u>Risultati previsti</u>:

La richiesta [!DNL GraphQL] deve ancora mostrare i prodotti per il secondo sito Web.

<u>Risultati effettivi</u>:

La richiesta [!DNL GraphQL] non mostra alcun prodotto per il secondo sito Web.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
