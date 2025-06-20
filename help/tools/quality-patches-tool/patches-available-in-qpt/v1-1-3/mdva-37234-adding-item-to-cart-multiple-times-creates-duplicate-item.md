---
title: 'MDVA-37234: l''aggiunta di più elementi al carrello crea un elemento riga duplicato'
description: La patch MDVA-37234 risolve il problema che, quando si aggiunge più volte un elemento al carrello (richiesta parallela) per lo stesso SKU, viene creato un elemento riga duplicato per lo stesso ID carrello. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3. L'ID della patch è MDVA-37234. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
feature: Orders, Shopping Cart
role: Admin
exl-id: d4e9fca1-7fba-4a33-9c5e-c9695cbfc61c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 0%

---

# MDVA-37234: l&#39;aggiunta di più elementi al carrello crea un elemento riga duplicato

La patch MDVA-37234 risolve il problema che, quando si aggiunge più volte un elemento al carrello (richiesta parallela) per lo stesso SKU, viene creato un elemento riga duplicato per lo stesso ID carrello. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.3. L&#39;ID della patch è MDVA-37234. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.6, 2.4.1 e 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.3.5 - 2.3.7-p1 e 2.4.1 - 2.4.2-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Se si aggiunge più volte un articolo al carrello (richiesta parallela) per lo stesso SKU, viene creata una riga duplicata per lo stesso ID carrello.

<u>Passaggi da riprodurre</u>:

1. Creare un prodotto semplice con SKU = simple1.
1. Crea un cliente.
1. Genera un token cliente per effettuare una richiesta GraphQL.

   <pre>
    <code class="language-graphql">
    mutation &lbrace;
        generateCustomerToken(
            email: "customer email"
            password: "customer password"
        )
        &lbrace;
            token
        &rbrace;
    &rbrace;
    </code>
    </pre>

1. Utilizza il token indicato nel passaggio 3 per creare un carrello vuoto per il cliente.

   <pre>
    <code class="language-graphql">
    mutation&lbrace;
     createEmptyCart
    &rbrace;
    </code>
    </pre>

1. Creare uno script per eseguire due richieste `addSimpleProductsToCart` in parallelo. Ad esempio:

   <pre>
    <code class="language-#!/bin/bash">
    curl -X POST -H "Content-Type: application/json" -H "Authorization: Bearer eyJraWQiOiIxIiwiYWxnIjoiSFMyNTYifQ.eyJ1aWQiOjEsInV0eXBpZCI6MywiaWF0IjoxNjIzOTUyNjcwLCJleHAiOjE2MjM5NTYyNzB9.-fh7ysqiQTAacdB3MVvaXzFE9AmKyfF8TsVmICLJoWI" -d '{"query" : "mutation { addSimpleProductsToCart( input: { cart_id: \"S8dCF7uan1POMy0qY0Hup7tEv1AhFGdY\" cart_items: [ { data: { quantity: 2 sku: \"simple1\" } } ] } ) { cart { items { id product { name sku } quantity } } } }"}' http://magento2.3.local/graphql &
    curl -X POST -H "Content-Type: application/json" -H "Authorization: Bearer eyJraWQiOiIxIiwiYWxnIjoiSFMyNTYifQ.eyJ1aWQiOjEsInV0eXBpZCI6MywiaWF0IjoxNjIzOTUyNjcwLCJleHAiOjE2MjM5NTYyNzB9.-fh7ysqiQTAacdB3MVvaXzFE9AmKyfF8TsVmICLJoWI" -d '{"query" : "mutation { addSimpleProductsToCart( input: { cart_id: \"S8dCF7uan1POMy0qY0Hup7tEv1AhFGdY\" cart_items: [ { data: { quantity: 1 sku: \"simple1\" } } ] } ) { cart { items { id product { name sku } quantity } } } }"}' http://magento2.3.local/graphql
    </code>
    </pre>

1. Esegui lo script.

<u>Risultati previsti</u>:

Nel carrello viene creata una sola linea di prodotti con una quantità totale (tre in questo caso).

<u>Risultati effettivi</u>:

Nel carrello vengono create due righe separate per lo stesso prodotto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti a seconda del tipo di distribuzione:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sulle patch di qualità per Adobe Commerce, consulta:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it).
