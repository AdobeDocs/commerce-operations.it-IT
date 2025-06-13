---
title: 'MDVA-44505: la query GraphQL per l''applicazione dei punti premio al carrello non aggiorna il totale complessivo'
description: La patch MDVA-44505 risolve il problema per cui la query GraphQL per un carrello che applica punti premio non considera i punti premio e restituisce un totale complessivo errato. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14. L'ID della patch è MDVA-44505. Il problema è stato risolto in Adobe Commerce 2.4.3.
feature: GraphQL, Orders, Rewards, Shopping Cart
role: Admin
exl-id: 543698d8-8963-4bf7-af82-11c2498e882e
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '442'
ht-degree: 0%

---

# MDVA-44505: la query GraphQL per l&#39;applicazione dei punti premio al carrello non aggiorna il totale complessivo

La patch MDVA-44505 risolve il problema per cui la query GraphQL per un carrello che applica punti premio non considera i punti premio e restituisce un totale complessivo errato. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14. L&#39;ID della patch è MDVA-44505. Il problema è stato risolto in Adobe Commerce 2.4.3.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1 - 2.4.2-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La query GraphQL per un carrello che applica punti premio non considera i punti premio e restituisce un totale complessivo errato.

<u>Passaggi da riprodurre</u>:

1. Configurare i punti premio.
1. Crea un carrello e applica alcuni punti premio.
1. Chiama la query `GetCart` dall&#39;endpoint `GraphQL` e recupera il carrello:

   ```GraphQL
   query {
     cart(cart_id: "{CART_ID}") {
       prices {
         discounts {
           amount {
             value
           }
         }
         grand_total {
           value
         }
       }
     }
   }
   ```

1. Controllare la voce totale complessivo.
1. Ora controlla il totale del carrello del cliente utilizzando l&#39;API rest (`/rest/V1/carts/mine/totals`).

<u>Risultati previsti</u>:

La query GraphQL per il carrello restituisce il totale complessivo corretto che considera i punti premio.

<u>Risultati effettivi</u>:

La query GraphQL non considera i punti premio e restituisce un totale complessivo errato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
