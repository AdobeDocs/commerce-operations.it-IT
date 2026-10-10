---
title: 'MDVA-38447: i prodotti secondari configurabili "Not visible individual" vengono restituiti nella risposta di GraphQL e la query MySQL è lenta'
description: La patch di MDVA-38447 Adobe Commerce risolve il problema relativo alla restituzione di prodotti secondari configurabili "Non visibile singolarmente" nella risposta di GraphQL e alla lentezza della query MySQL per i prodotti GraphQL con filtro categoria. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2. L'ID della patch è MDVA-38447. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
feature: B2B, GraphQL, Categories, Configuration, Products, Services
role: Admin
exl-id: d97297c5-e8e8-407b-b43b-033937426fe2
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: da76473c-f99b-5ad0-9b14-896aed473f8a
    internal-label: Services
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
  - id: e91a50b1-0b31-436e-9033-00e4776e94cb
    internal-label: Categories
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '528'
ht-degree: 1%
---
# MDVA-38447: i prodotti secondari configurabili &quot;Not visible individual&quot; vengono restituiti nella risposta di GraphQL e la query MySQL è lenta

La patch di MDVA-38447 Adobe Commerce risolve il problema relativo alla restituzione di prodotti secondari configurabili &quot;Non visibile singolarmente&quot; nella risposta di GraphQL e alla lentezza della query MySQL per i prodotti GraphQL con filtro categoria. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.2. L&#39;ID della patch è MDVA-38447. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Nella risposta di GraphQL vengono restituiti prodotti secondari configurabili &quot;Non visibili singolarmente&quot; e la query MySQL lenta per la query prodotti GraphQL con filtro categoria.

<u>Prerequisiti</u>:

I moduli B2B devono essere installati.

<u>Passaggi da riprodurre</u>:

1. Creare un prodotto configurabile con prodotti semplici impostati su **Non visibile singolarmente**.
1. Esegui una **reindicizzazione completa**.
1. Esegui una **query GraphQL** come:

<pre>query getFilteredProducts(
  $filter: ProductAttributeFilterInput.
  $sort: ProductAttributeSortInput.
  $search: String
  $pageSize: int!
  $currentPage: Int!
) &lbrace;
  products(
    filtro: $filter
    sort: $sort
    ricerca: $search
    pageSize: $pageSize
    currentPage: $currentPage
  ) &lbrace;
    total_count
    page_info &lbrace;
      total_pages
      current_page
      page_size
    &rbrace;
    elementi &lbrace;
      name
      sku
    &rbrace;
  &rbrace;
&rbrace;</pre>

Variabili:

<pre>{"filter":{"user_group":{"eq":""}&#x200B;},"search":"config-100","sort":{},"pageSize":200,"currentPage":1}
</pre>

<u>Risultati previsti</u>:

I prodotti con visibilità impostata su &quot;Non visibile singolarmente&quot; non verranno restituiti nella risposta.

<u>Risultati effettivi</u>:

I prodotti con visibilità impostata su &quot;Non visibile singolarmente&quot; vengono restituiti in risposta.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti a seconda del tipo di distribuzione:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sulle patch di qualità per Adobe Commerce, consulta:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it).
