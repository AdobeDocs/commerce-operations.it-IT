---
title: 'MDVA-40134: GraphQL non restituisce prodotti correlati quando è abilitato il catalogo condiviso'
description: La patch MDVA-40134 risolve il problema per cui GraphQL non restituisce prodotti correlati quando il catalogo condiviso è abilitato. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.2. L'ID della patch è MDVA-40134. Il problema è stato risolto in Adobe Commerce 2.4.3.
feature: B2B, Catalog Management, GraphQL, Products
role: Admin
exl-id: 5d31e042-4396-40ce-8bf1-63ad9a55214d
type: Troubleshooting
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: c18ed297-2187-4aec-affb-9d9654eca6fc
    internal-label: Catalog management
  - id: 4067ab89-2e97-5de1-8d98-de8318461a8d
    internal-label: Products
  - id: bd989d82-1e15-4534-88db-f1f51dd77ffa
    internal-label: Accounts
  - id: c32adafa-ed01-4b31-997e-2413013911b0
    internal-label: Integrations
subfeature_v2:
  - id: f56d26ed-050b-4fb7-b29b-8e6e994e80a2
    internal-label: B2B
  - id: e396cff5-f586-484c-89f0-7f1da3308f92
    internal-label: GraphQL
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '515'
ht-degree: 0%
---
# MDVA-40134: GraphQL non restituisce prodotti correlati quando è abilitato il catalogo condiviso

La patch MDVA-40134 risolve il problema per cui GraphQL non restituisce prodotti correlati quando il catalogo condiviso è abilitato. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.2. L&#39;ID della patch è MDVA-40134. Il problema è stato risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1 - 2.4.2-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

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
  products(filter: {sku: {eq: "24-MB01"}&#x200B;}, sort: {name: ASC}) &lbrace;
    elementi &lbrace;
      related_products &lbrace;
        uid
        name
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
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
