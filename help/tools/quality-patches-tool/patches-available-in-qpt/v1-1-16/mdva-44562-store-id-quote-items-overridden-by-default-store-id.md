---
title: 'MDVA-44562: ID archivio per gli elementi dell''offerta sostituito dall''ID archivio predefinito'
description: La patch MDVA-44562 risolve il problema per cui l'ID archivio predefinito sostituisce l'ID archivio per gli elementi di preventivo per le richieste GraphQL. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16. L'ID della patch è MDVA-44562. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.
feature: Quotes
role: Admin
exl-id: 007a82f7-4bc9-4a51-8b18-05f6c0867ea7
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---

# MDVA-44562: ID archivio per gli elementi dell&#39;offerta sostituito dall&#39;ID archivio predefinito

La patch MDVA-44562 risolve il problema per cui l&#39;ID archivio predefinito sostituisce l&#39;ID archivio per gli elementi di preventivo per le richieste GraphQL. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.16. L&#39;ID della patch è MDVA-44562. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L’ID archivio per gli elementi dell’offerta viene sostituito dall’ID archivio predefinito per le richieste GraphQL.

<u>Passaggi da riprodurre</u>:

1. Crea una nuova visualizzazione store.
1. Crea un nuovo prodotto semplice con nomi diversi per ogni visualizzazione store.
1. Crea un nuovo cliente.
1. Ottieni il token di autorizzazione del cliente.

   ```GraphQL
    POST /rest/all/V1/integration/customer/token
    {
      "username": "test@example.com",
      "password": "password"
     }
   ```

1. Crea un nuovo preventivo per il cliente utilizzando il token di autorizzazione.

   ```GraphQL
   POST rest/default/V1/carts/mine
   ```

1. Aggiungi un prodotto al carrello.

   ```GraphQL
   POST /rest/default/V1/carts/mine/items
   {
     "cartItem": {
       "sku": "simple1",
       "qty": 1,
       "quote_id": "1"
     }
   }
   ```

1. Ottieni il contenuto del carrello per la visualizzazione predefinita dello store.

   ```GraphQL
   GET rest/default/V1/carts/mine/
   ```

1. Ottieni il contenuto del carrello per la nuova visualizzazione Store.

   ```GraphQL
   GET rest/<store_view_2>/V1/carts/mine/
   ```

<u>Risultati previsti</u>:

La risposta dalla nuova visualizzazione Store mostra il nome del prodotto dalla nuova visualizzazione Store.

<u>Risultati effettivi</u>:

La risposta dalla nuova vista Store mostra l’impostazione del nome del prodotto nella vista Store predefinita.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
