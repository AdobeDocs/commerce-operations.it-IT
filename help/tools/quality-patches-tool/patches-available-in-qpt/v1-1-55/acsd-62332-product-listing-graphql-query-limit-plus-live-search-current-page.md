---
title: 'ACSD-62332: query GraphQL di elenco prodotti limitata a 10.000 prodotti e  [!DNL Live Search] imposta la pagina corrente su 1'
description: Applica la patch ACSD-62332 per risolvere i problemi di Adobe Commerce in cui la query GraphQL dell’elenco dei prodotti è limitata a un totale di 10.000 prodotti e in cui [!DNL Live Search] imposta la pagina corrente su *1* invece della pagina *2* nei criteri di ricerca quando viene eseguita la query tramite GraphQL.
feature: GraphQL, Products, Search
role: Admin, Developer
exl-id: 3623a337-32e9-468b-a82b-6a7f7fa943c9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---

# ACSD-62332: query GraphQL dell&#39;elenco prodotti limitata a 10.000 prodotti e [!DNL Live Search] imposta la pagina corrente su 1

>[!NOTE]
>
>Questa patch è una versione aggiornata di [ACSD-55100](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-46/acsd-55100-graphql-does-not-return-products-beyond-10k-in-the-search-results.md) e sostituisce [ACSD-52801](/help/tools/quality-patches-tool/patches-available-in-qpt/v1-1-40/acsd-52801-graphql-product-filter-query-not-showing-partial-match-results.md) nelle versioni 2.4.6 - 2.4.6-p8. Per maggiori dettagli, consulta gli articoli corrispondenti.

La patch ACSD-62332 risolve i problemi in cui la query GraphQL dell&#39;elenco prodotti è limitata a `total_count` di 10.000 prodotti e in cui [!DNL Live Search] imposta la pagina corrente su *1* invece della pagina *2* nei criteri di ricerca quando viene eseguita una query tramite GraphQL. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55. L’ID della patch è ACSD-62332. I problemi sono stati risolti in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La query di GraphQL dell&#39;elenco prodotti è limitata a un totale di 10.000 prodotti e dove [!DNL Live Search] imposta la pagina corrente su *1* invece della pagina *2* nei criteri di ricerca quando viene eseguita una query tramite GraphQL.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.


## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
