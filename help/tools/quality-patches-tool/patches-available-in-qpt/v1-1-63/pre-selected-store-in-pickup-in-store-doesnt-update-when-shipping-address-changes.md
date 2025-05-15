---
title: Lo store preselezionato in "Ritiro nello Store" non si aggiorna quando cambia l'indirizzo di spedizione
description: Applicare la patch ACSD-64753 per risolvere il problema Adobe Commerce, in cui lo store preselezionato non è stato aggiornato quando è stato immesso un nuovo indirizzo di spedizione al di fuori del raggio di servizio dello store selezionato.
feature: Inventory
role: Admin, Developer
source-git-commit: 9d76014fb86fd92b2fffbf2de35b25a7f6d1cbae
workflow-type: tm+mt
source-wordcount: '438'
ht-degree: 0%

---


# ACSD-64753: lo store preselezionato in &quot;Ritiro in negozio&quot; non si aggiorna quando cambia l’indirizzo di spedizione

La patch ACSD-64753 risolve il problema che impediva l&#39;aggiornamento dello store preselezionato quando veniva immesso un nuovo indirizzo di spedizione al di fuori del raggio di assistenza dello store selezionato. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.63. L’ID della patch è ACSD-64753. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Lo store preselezionato non è stato aggiornato quando è stato immesso un nuovo indirizzo di spedizione al di fuori del raggio di assistenza dello store selezionato.

<u>Passaggi da riprodurre</u>:

1. Abilita **[!UICONTROL In-Store Delivery]** passando a **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]**.
1. Fornire una chiave API [!DNL Google] valida per [!DNL Google Distance Provider]. A tale scopo, passare a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Google Distance Provider]**.
1. Aggiungi una nuova origine (**[!UICONTROL Stores]** > **[!UICONTROL Sources]** > **[!UICONTROL Add New Source]**) e imposta i seguenti valori:
   * **[!UICONTROL Latitude]**: *-41.917344*
   * **[!UICONTROL Longitude]**: *-88.102569*
   * **[!UICONTROL Use as Pickup Location]**: *Sì*
   * **[!UICONTROL Country United]**: *Stati*
   * **[!UICONTROL State]**: *Illinois*
   * **[!UICONTROL City]**: *Flusso Carlo*
   * **[!UICONTROL Postcode]**: *60188*
1. Aggiungi un nuovo titolo (**[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock]** > **[!UICONTROL Add New Stock]**), assegna ad esso la nuova origine e il sito Web principale.
1. Modificare qualsiasi prodotto, assegnare il prodotto al nuovo Source, In Stock e qtà > *0*.
1. Attendi il completamento della reindicizzazione.
1. Nella vetrina, crea un nuovo cliente e quindi aggiungi un indirizzo della California come indirizzo di fatturazione e spedizione predefinito.
1. Aggiungi un altro indirizzo Illinois non predefinito a questo cliente.
1. Aggiungi il prodotto al carrello e procedi al pagamento.
1. Lascia selezionato l&#39;indirizzo di spedizione della California e scegli il metodo di spedizione **[!UICONTROL Pick in Store]**. Fare clic su **[!UICONTROL Next]**.

<u>Risultati previsti</u>:

Poiché l’indirizzo della California non rientra nel raggio di ricerca massimo (200 km), il Source dell’Illinois non deve essere disponibile per il cliente.

<u>Risultati effettivi</u>:

L&#39;origine dell&#39;Illinois può essere prelevata e il cliente può procedere al pagamento.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
