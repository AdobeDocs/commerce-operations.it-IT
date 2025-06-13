---
title: 'MDVA-42341: la query GraphQL "categoryList" non filtra i risultati'
description: La patch MDVA-42341 risolve il problema per cui la query GraphQL "categoryList" non filtra i risultati se una richiesta ha l'intestazione Store. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8. L'ID della patch è MDVA-42341. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
feature: GraphQL, Categories
role: Admin
exl-id: 56b81385-6db0-4e62-8e2b-bccfc9e0a581
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-42341: la query GraphQL &quot;categoryList&quot; non filtra i risultati

La patch MDVA-42341 risolve il problema per cui la query GraphQL &quot;categoryList&quot; non filtra i risultati se una richiesta ha l&#39;intestazione Store. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.8. L&#39;ID della patch è MDVA-42341. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La query GraphQL &quot;categoryList&quot; non filtra i risultati se una richiesta ha l’intestazione Store.

<u>Passaggi da riprodurre</u>:

1. Creare una nuova categoria radice e denominarla **radice2**.
1. Crea un secondo sito Web/store/storeview e assegna **root2** al nuovo store.
1. Crea una nuova categoria in Categoria principale predefinita = categoria1.
1. Utilizzando una richiesta di GraphQL, ottieni un elenco di categorie per il secondo sito web (usa Archivio intestazioni = nuovo).

<pre>
<code class="language-graphql">
&lbrace;
  categoryList(filters: {name: {match: "category1"}}) &lbrace;
    uid
    level
    name
    breadcrumbs &lbrace;
      category_uid
      category_name
      category_level
      category_url_key
    &rbrace;
  &rbrace;
&rbrace;
</code>
</pre>

<u>Risultati previsti</u>:

Le categorie della categoria principale predefinita non sono elencate in risposta perché si sta utilizzando una &quot;nuova&quot; intestazione store.

<u>Risultati effettivi</u>:

Le categorie della categoria principale predefinita sono disponibili nei risultati.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
