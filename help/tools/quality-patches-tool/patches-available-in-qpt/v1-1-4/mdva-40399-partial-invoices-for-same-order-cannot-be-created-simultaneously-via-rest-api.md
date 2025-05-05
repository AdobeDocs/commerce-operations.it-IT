---
title: "MDVA-40399: impossibile creare contemporaneamente fatture parziali per lo stesso ordine tramite API"
description: La patch MDVA-40399 risolve il problema che impedisce la creazione simultanea di fatture parziali per lo stesso ordine tramite l'API REST. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4. L'ID della patch è MDVA-40399. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.
feature: REST, Invoices, Orders
role: Admin
source-git-commit: 1fb76b8d648cbbe2a9f602d2b1a0149f1f4f0e46
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# MDVA-40399: impossibile creare contemporaneamente fatture parziali per lo stesso ordine tramite API

La patch MDVA-40399 risolve il problema che impedisce la creazione simultanea di fatture parziali per lo stesso ordine tramite l&#39;API REST. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.4. L&#39;ID della patch è MDVA-40399. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.3-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Non è possibile creare contemporaneamente fatture parziali per gli stessi ordini utilizzando l&#39;API REST.

<u>Prerequisiti</u>:

Un prodotto configurabile con almeno due varianti.

<u>Passaggi da riprodurre</u>:

1. Aggiungi al carrello entrambe le varianti del prodotto configurabile.
1. Effettua l’ordine.
1. Creare due fatture contemporaneamente per l&#39;ordine tramite l&#39;API Rest.

<u>Risultati previsti</u>:

* Entrambe le fatture devono essere create correttamente.
* È necessario aggiornare `qty_invoiced` per entrambe le fatture nella tabella `sales_order_item`.
* Entrambi i prodotti devono avere una quantità fatturata.

<u>Risultati effettivi</u>:

* Entrambe le fatture sono state create correttamente.
* `qty_invoiced` non è aggiornato in base a una delle fatture nella tabella `sales_order_item`.
* Nella pagina **Visualizzazione ordini** dell&#39;amministratore, la quantità delle fatture viene visualizzata solo per un prodotto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, consulta la sezione [Patch disponibili in QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it).
