---
title: 'ACSD-45257: GraphQL non visualizza correttamente lo sconto sul carrello'
description: La patch ACSD-45257 risolve il problema se GraphQL non visualizza correttamente lo sconto sul carrello. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18. L’ID della patch è ACSD-45257. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.
feature: GraphQL, Marketing Tools, Orders, Personalization, Shopping Cart
role: Admin
exl-id: 3d546768-7f7e-4724-a6d7-c88ca6b67e8c
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# ACSD-45257: GraphQL non visualizza correttamente lo sconto sul carrello

La patch ACSD-45257 risolve il problema se GraphQL non visualizza correttamente lo sconto sul carrello. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18. L’ID della patch è ACSD-45257. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.4 - 2.4.3-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

GraphQL non visualizza correttamente lo sconto sul carrello.

<u>Passaggi da riprodurre</u>:

1. Vai a **Amministratore** > **Marketing** > **Promozioni** > **Regola prezzo carrello**.
1. Aggiungi una nuova regola e applicala all’importo della spedizione.
1. Aggiungi un prodotto al carrello utilizzando GraphQL.
1. Controlla le informazioni del carrello con una query GraphQL.

<u>Risultati previsti</u>:

Lo sconto totale include lo sconto applicato all&#39;importo di spedizione nella risposta di GraphQL.

<u>Risultati effettivi</u>:

Lo sconto totale non riflette lo sconto applicato sull’importo della spedizione nella risposta di GraphQL.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
