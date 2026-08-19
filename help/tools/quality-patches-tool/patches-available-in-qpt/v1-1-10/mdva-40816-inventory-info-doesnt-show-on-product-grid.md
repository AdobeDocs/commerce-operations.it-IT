---
title: 'MDVA-40816: dati di inventario non visualizzati nella griglia prodotti'
description: La patch MDVA-40816 risolve il problema che impedisce la visualizzazione delle informazioni di inventario nella griglia del prodotto se uno SKU del prodotto contiene caratteri speciali. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10. L'ID della patch è MDVA-40816. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
feature: Admin Workspace, Inventory, Orders, Products
role: Admin
exl-id: be1dbf75-389d-4bb2-847f-56afb746e4ce
type: Troubleshooting
source-git-commit: 14c28ca8eec3348b2289b0fce2f30b563c7debe0
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# MDVA-40816: dati di inventario non visualizzati nella griglia prodotti

La patch MDVA-40816 risolve il problema che impedisce la visualizzazione delle informazioni di inventario nella griglia del prodotto se uno SKU del prodotto contiene caratteri speciali. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.10. L&#39;ID della patch è MDVA-40816. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Se uno SKU prodotto contiene simboli speciali, i dati di inventario non vengono visualizzati nella griglia del prodotto.

<u>Prerequisiti</u>:

MSI è installato.

<u>Passaggi da riprodurre</u>:

1. Crea un prodotto semplice.
1. Modifica lo SKU di un prodotto in modo che includa simboli speciali come &amp; o &quot;.
1. Apri la griglia del prodotto.

<u>Risultati previsti</u>:

La griglia prodotti visualizza correttamente tutte le informazioni.

<u>Risultati effettivi</u>:

Dati di inventario mancanti.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/upgrade/apply-patches) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
