---
title: 'MDVA-40435: lo sconto sul prodotto bundle non viene applicato correttamente tramite GraphQL'
description: La patch MDVA-40435 risolve il problema della mancata applicazione dello sconto su un prodotto in bundle tramite GraphQL. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4. L'ID della patch è MDVA-40435. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
feature: GraphQL, Orders, Personalization, Products
role: Admin
exl-id: 001be138-5d09-455d-a597-57115cd21a25
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# MDVA-40435: lo sconto sul prodotto bundle non viene applicato correttamente tramite GraphQL

La patch MDVA-40435 risolve il problema della mancata applicazione dello sconto su un prodotto in bundle tramite GraphQL. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.4. L&#39;ID della patch è MDVA-40435. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.4 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Lo sconto su un prodotto in bundle non viene applicato correttamente tramite GraphQL.

<u>Passaggi da riprodurre</u>:

1. Crea una regola di prezzo del carrello con un codice coupon per uno sconto fisso di $5.
1. Crea un carrello vuoto tramite GraphQL.
1. Aggiungi al carrello un prodotto in bundle tramite GraphQL.
1. Applica il codice coupon all&#39;importo fisso (5$) tramite GraphQL.
1. Ottieni le informazioni sul carrello tramite GraphQL.

<u>Risultati previsti</u>:

&quot;sconti&quot; è di $5.

<u>Risultati effettivi</u>:

&quot;discounts&quot; è NULL.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
