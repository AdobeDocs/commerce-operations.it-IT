---
title: 'ACSD-45241: calcolo errato della quantità di scorte del prodotto virtuale'
description: La patch ACSD-45241 risolve il problema relativo al calcolo errato della quantità di scorte del prodotto virtuale dopo la creazione di una nota di credito. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17. L’ID della patch è ACSD-45241. Il problema è stato risolto in Adobe Commerce 2.4.4.
feature: Orders, Products
role: Admin
exl-id: 447a84f0-aab4-4bb1-9f06-c056c006cd69
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---

# ACSD-45241: calcolo errato della quantità di scorte del prodotto virtuale

La patch ACSD-45241 risolve il problema relativo al calcolo errato della quantità di scorte del prodotto virtuale dopo la creazione di una nota di credito. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17. L’ID della patch è ACSD-45241. Il problema è stato risolto in Adobe Commerce 2.4.4.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.5 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La quantità di magazzino per un prodotto virtuale viene calcolata in modo errato dopo la creazione di una nota di credito.

<u>Passaggi da riprodurre</u>:

1. Creare un prodotto configurabile con un prodotto virtuale come prodotto secondario in Commerce Admin.
1. Assicurati che entrambi i prodotti creati nel passaggio 1 siano in magazzino.
1. Contrassegna la quantità per il prodotto virtuale creato nel passaggio 1 come 100 e mantieni la quantità vendibile come 100.
1. Aggiungi il prodotto al carrello.
1. Effettuare un ordine con il prodotto virtuale creato nel primo passaggio.
1. Mantenere lo stato dell&#39;ordine come &quot;In sospeso&quot;. Non è necessario elaborare il pagamento.
1. Record `order_created` creato in `inventory_reservation`. La quantità del prodotto virtuale è pari a 100 con la quantità vendibile pari a 99.
1. Apri l&#39;ordine e passa a **Fattura** > **Invia fattura**.
1. Record `invoice_created` creato in `inventory_reservation`. La quantità di prodotto virtuale è ora 99 e anche la quantità vendibile è 99.
1. Creare una nota di credito senza selezionare **Torna al magazzino**.

<u>Risultati previsti</u>:

Nessun nuovo record creato in `inventory_reservation` e la quantità di scorte per il prodotto virtuale rimane invariata.

<u>Risultati effettivi</u>:

Un record `creditmemo_created` viene creato in `inventory_reservation` e la quantità di scorte di prodotto virtuale viene adeguata a 98 con la quantità vendibile pari a 99.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
