---
title: 'ACSD-55100: [!DNL GraphQL] non restituisce prodotti oltre i 10.000 nei risultati di ricerca'
description: Applica la patch ACSD-55100 per risolvere il problema di Adobe Commerce, in cui GraphQL non restituisce prodotti oltre *10k* nei risultati della ricerca.
feature: GraphQL, Products, Search
role: Admin, Developer
exl-id: f08b62b9-ed56-4eca-b7e7-6e2bd99df01f
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
subfeature_v2:
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
  - id: a1d22079-48b9-5e69-9ee6-eb236068ef34
    internal-label: Search
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '512'
ht-degree: 0%
---
# ACSD-55100: [!DNL GraphQL] non restituisce prodotti oltre i 10.000 nei risultati di ricerca

>[!NOTE]
>
>È stata rilasciata una patch aggiornata ([ACSD-62332](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-62332-product-listing-graphql-query-limit-plus-live-search-current-page.md)) per risolvere lo stesso problema per le versioni 2.4.6 - 2.4.6-p8. Per ulteriori dettagli, vedere [ACSD-62332](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-55/acsd-62332-product-listing-graphql-query-limit-plus-live-search-current-page.md).

La patch ACSD-55100 risolve il problema per cui [!DNL GraphQL] non restituisce prodotti oltre *10k* nei risultati di ricerca. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.46. L’ID della patch è ACSD-55100. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

[!DNL GraphQL] non restituisce prodotti oltre *10k* nei risultati di ricerca.

<u>Prerequisiti</u>:

Nel caso di **[!DNL OpenSearch]**, assicurati di utilizzare l&#39;ultima versione disponibile.

Per risolvere il problema segnalato, è stata introdotta la funzionalità Point in Time, disponibile dopo la versione **[!DNL OpenSearch]** 2.5.0 e che richiede la versione 2.2 del pacchetto `opensearch-project/opensearch-php`.

Tuttavia, si è verificato un conflitto con `magento/magento-cloud-metapackage`, che specifica una dipendenza dal pacchetto `opensearch-project/opensearch-php` che deve essere inferiore alla versione 2.0.1.


Questa dipendenza impedisce l&#39;aggiornamento del pacchetto [opensearch-project/opensearch-php] alla versione più recente 2.2.

Di conseguenza, il sistema rileva il seguente errore e restituisce risultati nulli per prodotti superiori a *10.000*.

`Namespace [createPointInTime] not found in /vendor/opensearch-project/opensearch-php/src/OpenSearch/Client.php:135`

La dipendenza esistente rende difficile aggiungere direttamente una versione al file `composer.json` e aggiornare il pacchetto `opensearch-project/opensearch-php` alla versione 2.2.

Per risolvere il problema, includere la riga seguente nel file `composer.json` principale sotto il blocco require. In seguito, ridistribuisci per aggiornare il pacchetto problematico alla versione più recente.

`"opensearch-project/opensearch-php": "2.2.0 as 2.0.0",`

<u>Passaggi da riprodurre</u>:

1. Genera il catalogo con *15k* prodotti.
1. Invia [!DNL GraphQL]:

```graphql
    query {
    products(
    filter: {
    # category_id:{eq:""}
    }
    , pageSize: 5, currentPage: 1

    ) {
    total_count
    page_info {
    current_page
    page_size
    total_pages
     }

     aggregations {

    attribute_code
    count
    label
    options {
    label
    value

    }
    }

    items {
    uid
    sku
    is_for_clearance
    categories {
    name
    breadcrumbs {
    category_name
    category_uid
    }
    display_mode
    description
    }
    }
    }
    }
```

<u>Risultati previsti</u>:

Totale = *15k*
Dovresti essere in grado di mostrare tutti i prodotti.

<u>Risultati effettivi</u>:

Totale = *10k*
Impossibile ottenere altri prodotti da mostrare dopo il batch *10k*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
