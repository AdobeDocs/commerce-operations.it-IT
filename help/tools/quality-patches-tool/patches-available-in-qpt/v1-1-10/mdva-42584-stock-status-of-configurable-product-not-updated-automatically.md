---
title: 'MDVA-42584: lo stato del magazzino del prodotto configurabile non viene aggiornato automaticamente'
description: La patch MDVA-42584 risolve il problema se lo stato delle scorte del prodotto configurabile non viene aggiornato automaticamente quando il prodotto semplice viene aggiornato. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10. L'ID della patch è MDVA-42584. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
feature: Configuration, Orders, Products
role: Admin
exl-id: 6311f069-f08f-4d58-9f4b-fa1246c02640
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# MDVA-42584: lo stato del magazzino del prodotto configurabile non viene aggiornato automaticamente

La patch MDVA-42584 risolve il problema se lo stato delle scorte del prodotto configurabile non viene aggiornato automaticamente quando il prodotto semplice viene aggiornato. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10. L&#39;ID della patch è MDVA-42584. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Lo stato Stock del prodotto configurabile nel backend non viene aggiornato automaticamente quando il suo prodotto semplice è impostato su **In Stock** tramite API o importazione.

<u>Prerequisiti</u>:

MSI installato.

<u>Passaggi da riprodurre</u>:

1. Creare un prodotto configurabile, **InvCheck001**, con due opzioni: **InvCheck001-M** e **InvCheck001-L**.
1. Entrambi i prodotti semplici devono avere Quantità e devono essere **In magazzino** in modo che il prodotto configurabile sia anche **In magazzino** nel back-end.
1. Aggiornare i prodotti semplici e impostare Quantità su **0** e Stato scorte su **esaurito**.
1. Aggiorna il prodotto configurabile e verifica che lo stato del magazzino sia aggiornato a **esaurito**.
1. Utilizza il seguente endpoint API e imposta il prodotto semplice **InvCheck001-M** su **In magazzino** con quantità > 0.

   ```JSON
   /rest/V1/inventory/source-items
   
   {
     "sourceItems":
     [
       {
         "sku": "InvCheck001-M",
         "source_code": "default",
         "quantity": 10,
         "status": 1
       }
     ]
   }
   ```

1. Passare al backend e verificare la quantità e lo stato delle scorte del prodotto semplice **InvCheck001-M**. È stato aggiornato a **In magazzino**.
1. Aggiorna il prodotto configurabile e controlla lo stato delle scorte.

<u>Risultati previsti</u>:

Lo stato delle scorte del prodotto configurabile **InvCheck001** nel backend viene aggiornato automaticamente in **In Stock**.

<u>Risultati effettivi</u>:

Lo stato del prodotto configurabile è ancora **esaurito**.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
