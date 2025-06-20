---
title: 'MDVA-43102: quantità di vendita non aggiornata correttamente'
description: La patch MDVA-43102 risolve il problema che causa l'aggiornamento non corretto della quantità vendibile quando viene effettuato un rimborso tramite API REST. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14. L'ID della patch è MDVA-43102. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.
feature: Variables
role: Admin
exl-id: 6a10f586-bbde-4252-9b8e-9b2b712f0fb3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# MDVA-43102: quantità di vendita non aggiornata correttamente

La patch MDVA-43102 risolve il problema che causa l&#39;aggiornamento non corretto della quantità vendibile quando viene effettuato un rimborso tramite API REST. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14. L&#39;ID della patch è MDVA-43102. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.5.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.1 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La quantità vendibile non viene aggiornata correttamente quando viene effettuato un rimborso utilizzando l’API REST.

<u>Passaggi da riprodurre</u>:

1. Aggiungi un articolo al carrello.
1. Controllare la Qtà magazzino e la Qtà vendibile.
1. Crea un ordine.
1. Creare una fattura, se necessario.
1. Sottomettere una richiesta REST per rimborsare la fattura utilizzando il seguente payload:

   * metodo/ordine non in linea/`<order_id>`/rimborso
   * metodo online/fattura/`<invoice_id>`/rimborso

   ```rest
   {
     "items": [
     {
       "order_item_id": <order_item_id>,
       "qty": 1
     }
     ],
     "notify": true,
     "arguments": {
       "shipping_amount": 5,
       "extension_attributes": {
         "return_to_stock_items": [
         <order_item_id>
         ]
       }
     }
   }
   ```

1. Non spedire gli articoli.
1. Confrontare la Qtà magazzino e la Qtà vendibile da prima. Entrambi devono essere aggiornati dello stesso importo.

<u>Risultati previsti</u>:

La quantità vendibile viene aggiornata correttamente quando viene emesso un rimborso prima della spedizione dell&#39;ordine e il prodotto viene restituito alle scorte.

<u>Risultati effettivi</u>:

La quantità vendibile non viene aggiornata quando viene emesso un rimborso prima della spedizione dell&#39;ordine e il prodotto viene restituito alle scorte.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
