---
title: 'MDVA-40134: GraphQL non restituisce prodotti correlati quando è abilitato il catalogo condiviso'
description: La patch MDVA-40134 risolve il problema per cui GraphQL non restituisce prodotti correlati quando il catalogo condiviso è abilitato. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2. L'ID della patch è MDVA-40134. Il problema è stato risolto in Adobe Commerce 2.4.3.
feature: B2B, Catalog Management, GraphQL, Products
role: Admin
exl-id: 5d31e042-4396-40ce-8bf1-63ad9a55214d
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '480'
ht-degree: 0%

---

# MDVA-40134: GraphQL non restituisce prodotti correlati quando è abilitato il catalogo condiviso

La patch MDVA-40134 risolve il problema per cui GraphQL non restituisce prodotti correlati quando il catalogo condiviso è abilitato. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2. L&#39;ID della patch è MDVA-40134. Il problema è stato risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1 - 2.4.2-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

GraphQL non restituisce prodotti correlati quando il catalogo condiviso è abilitato.

<u>Prerequisiti</u>:

I moduli B2B devono essere installati.
L’istanza deve essere pulita con solo i dati di esempio.

<u>Passaggi da riprodurre</u>:

1. Vai a **Archivi** > **Configurazione** > **Generale** > **Caratteristiche B2B** e abilita **Azienda e catalogo condiviso**.
1. Vai a **Catalogo** > **Catalogo condiviso** e aggiungi tutti i prodotti al **Catalogo generale**.
1. Utilizza i dati di esempio e modifica il Joust Duffle Bag (SKU 24-MB01).
1. In **Prodotti correlati**, aggiungi le due borse (ID 7 e 13).
1. Invia una richiesta **Post**:

<pre>&lbrace;
  products(filter: {sku: {eq: "24-MB01"}}, sort: {name: ASC}) &lbrace;
    elementi &lbrace;
      related_products &lbrace;
        uid
        nome
      &rbrace;
    &rbrace;
  &rbrace;
&rbrace;</pre>

<u>Risultati previsti</u>:

I prodotti correlati sono mostrati nella risposta di GraphQL.

<u>Risultati effettivi</u>:

Gli utenti ricevono il seguente errore:

<pre>Il valore restituito da Magento\CatalogPermissionsGraphQl\Model\Store\StoreProcessor::getStoreId() deve essere di tipo int, null ha restituito &lbrace;"exception":"[object] (GraphQL\\Error\\Error(code: 0): il valore restituito da Magento\\CatalogPermissionsGraphQl\\Model\\Store\\StoreProcessor::getStoreId() deve essere di tipo int, null ha restituito </pre>

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
