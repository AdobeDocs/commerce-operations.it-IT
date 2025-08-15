---
title: 'ACSD-64137: la ricerca di posizioni di prelievo in base al codice postale non funziona correttamente per la localizzazione olandese'
description: Applica la patch ACSD-64137 per risolvere il problema per cui la ricerca di posizioni di prelievo per codice postale non funziona correttamente per la localizzazione in olandese.
feature: Shipping/Delivery
role: Admin, Developer
exl-id: 86c28b6d-6584-4caf-bd35-13e0c1bdcf1d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-64137: la ricerca di posizioni di prelievo in base al codice postale non funziona correttamente per la localizzazione in olandese

La patch ACSD-64137 risolve il problema per cui la ricerca di posizioni di prelievo per codice postale non funziona correttamente per la localizzazione olandese. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60. L’ID della patch è ACSD-64137. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La ricerca del codice postale per i Paesi Bassi non mostra i risultati nella pagina di pagamento front-end. Tuttavia, funziona per città e visualizza l’indirizzo corrispondente senza effettuare ricerche.

<u>Passaggi da riprodurre</u>:

1. Installa un’istanza pulita con i moduli inventario.
1. Crea un titolo personalizzato.
1. Creare due origini con indirizzi olandesi e assegnarle al magazzino (codici postali 7311ER e 7311AE).
1. Crea un prodotto semplice e aggiungi l’inventario.
1. Abilitare **[!UICONTROL In-Store Delivery]** passando a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]**.
1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Distance Provider for Distance Based SSA]**. Imposta **[!UICONTROL Provider]** su *Calcolo offline*.
1. Esegui il comando seguente per importare i nomi geografici per il paese NL.

   ```bash
   bin/magento inventory-geonames:import NL
   ```

1. Aggiungi il prodotto al carrello e passa alla fase di spedizione.
1. Selezionare **[!UICONTROL Pick In Store]**. Quindi fare clic su **[!UICONTROL Select Other]** per selezionare altri archivi.
1. Digitare *7311* o *7311AE* nel modulo di ricerca **[!UICONTROL Select Store]**.


**Risultati previsti**:

* Gli archivi corrispondenti devono essere compilati.

**Risultati effettivi**:

* Nessun risultato trovato.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.


## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
