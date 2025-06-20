---
title: 'MDVA-38728: la modifica della visibilità del prodotto crea la riscrittura dell''URL per il sito Web principale'
description: La patch MDVA-38728 risolve il problema relativo alla modifica della visibilità del secondo sito Web in modo da creare un URL riscritto per il sito Web principale. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10. L'ID della patch è MDVA-38728. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
feature: Products
role: Admin
exl-id: c9dfa386-6327-43b6-a977-a29178c64b89
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# MDVA-38728: la modifica della visibilità del prodotto crea la riscrittura dell&#39;URL per il sito Web principale

La patch MDVA-38728 risolve il problema relativo alla modifica della visibilità del secondo sito Web in modo da creare un URL riscritto per il sito Web principale. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10. L&#39;ID della patch è MDVA-38728. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.2 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Modificando la visibilità del prodotto del secondo sito Web, viene creata una riscrittura URL per il sito Web principale.

<u>Passaggi da riprodurre</u>:

1. Crea un ulteriore sito Web, store e storeview.
1. Crea un prodotto semplice.
1. Imposta la visibilità su **Non visibile singolarmente**.
1. Assegna il prodotto solo al secondo sito Web.
1. Compila tutti gli altri campi obbligatori.
1. Salva il prodotto.
1. Avvia code MySQL:

   ```mysql
   bin/magento queue:consumers:start product_action_attribute.update &
   bin/magento queue:consumers:start product_action_attribute.website.update &
   ```

1. Passa a Elenco prodotti.
1. Seleziona il prodotto creato e aggiorna l’attributo di visibilità utilizzando l’aggiornamento di massa a Catalogo e Ricerca.
1. Controlla la riscrittura dell’URL.

<u>Risultati previsti</u>:

La riscrittura viene creata per il secondo sito Web a cui è assegnato il prodotto.

<u>Risultati effettivi</u>:

La riscrittura viene creata per il sito Web principale.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
