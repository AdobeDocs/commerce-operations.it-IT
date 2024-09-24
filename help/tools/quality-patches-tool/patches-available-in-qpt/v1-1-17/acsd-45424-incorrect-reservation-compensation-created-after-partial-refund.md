---
title: "ACSD-45424: Compensazione prenotazione errata creata dopo rimborso parziale"
description: La patch ACSD-45424 risolve il problema che comporta la creazione di una compensazione della prenotazione non corretta dopo un rimborso parziale. Questa patch è disponibile quando è installato [Quality Patches Tool (QPT)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17. L’ID della patch è ACSD-45424. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.
feature: Orders
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---

# ACSD-45424: Compensazione prenotazione errata creata dopo rimborso parziale

La patch ACSD-45424 risolve il problema che comporta la creazione di una compensazione della prenotazione non corretta dopo un rimborso parziale. Questa patch è disponibile quando è installato [QPT (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.17. L’ID della patch è ACSD-45424. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.4 - 2.4.4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni dello strumento Patch di qualità. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La compensazione della prenotazione non corretta viene creata dopo un rimborso parziale.

<u>Passaggi da riprodurre</u>:

1. Abilita il metodo di spedizione della consegna in-store.
1. Creare tre origini magazzino e assicurarsi che l&#39;ubicazione di prelievo sia attiva in ciascuna (origine1, origine2, origine3).
1. Create un nuovo materiale e assegnate le tre origini al nuovo materiale.
   * Questo stock deve essere assegnato al sito web principale.
1. Create un prodotto semplice, P3, e assegnate ad esso tutte le sorgenti.
1. Aggiungi le seguenti quantità per le origini del prodotto semplice e abilita ordini inevasi:
   * Origine predefinita - 100
   * source1 - 0
   * source2 - 10
   * source3 - 0
1. Aggiungi il prodotto semplice al carrello dal front-end e procedi al modulo di spedizione.
1. Selezionare &quot;source1&quot; come ubicazione di spedizione.
1. Completa l’ordine ed esegui la seguente query nel database:

   ```sql
   SELECT * FROM inventory_reservation WHERE sku = 'P3';
   ```

   Otterrai il record dell&#39;ordine inserito nella tabella `inventory_reservation`. La quantità è 10, che è corretta.
1. Fattura questo ordine dal backend.
1. Ora crea una nota di credito per un solo prodotto. NON selezionare la casella di controllo *Torna all&#39;archivio*.
1. Esegui la stessa query dal passaggio 8.

<u>Risultati previsti</u>:

Se durante la creazione della nota di credito non è stato selezionato *Torna al magazzino*, la tabella `inventory_reservation` non avrà un record corrispondente alla nota di credito.

<u>Risultati effettivi</u>:

Anche se non hai selezionato *Torna allo Stock* durante la creazione della nota di credito, aggiunge un record alla tabella `inventory_reservation` con tipo di evento `creditmemo_created`. Inoltre, il record della nota di credito aggiunto nella tabella `inventory_reservation` ha una quantità di 10 anche se la nota di credito è stata creata per una sola quantità.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni sullo strumento Patch di qualità, vedere:

* [È stato rilasciato lo strumento di gestione delle patch di qualità: un nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando lo strumento Patch di qualità](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!DNL Quality Patches Tool].

Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
