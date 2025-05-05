---
title: 'MDVA-38447: i prodotti secondari configurabili "Not visible individual" vengono restituiti nella risposta di GraphQL e la query MySQL è lenta'
description: La patch di MDVA-38447 Adobe Commerce risolve il problema relativo alla restituzione di prodotti secondari configurabili "Non visibile singolarmente" nella risposta di GraphQL e alla lentezza della query MySQL per i prodotti GraphQL con filtro categoria. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2. L'ID della patch è MDVA-38447. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
feature: B2B, GraphQL, Categories, Configuration, Products, Services
role: Admin
source-git-commit: c1055ed10813aa6e585f93ec3091d216af06affd
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# MDVA-38447: i prodotti secondari configurabili &quot;Not visible individual&quot; vengono restituiti nella risposta di GraphQL e la query MySQL è lenta

La patch di MDVA-38447 Adobe Commerce risolve il problema relativo alla restituzione di prodotti secondari configurabili &quot;Non visibile singolarmente&quot; nella risposta di GraphQL e alla lentezza della query MySQL per i prodotti GraphQL con filtro categoria. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.2. L&#39;ID della patch è MDVA-38447. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

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
      nome
      sku
    &rbrace;
  &rbrace;
&rbrace;</pre>

Variabili:

<pre>{"filter":{"user_group":{"eq":"}},"search":"config-100","sort":{},"pageSize":200,"currentPage":1}
</pre>

<u>Risultati previsti</u>:

I prodotti con visibilità impostata su &quot;Non visibile singolarmente&quot; non verranno restituiti nella risposta.

<u>Risultati effettivi</u>:

I prodotti con visibilità impostata su &quot;Non visibile singolarmente&quot; vengono restituiti in risposta.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti a seconda del tipo di distribuzione:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sulle patch di qualità per Adobe Commerce, consulta:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html).
