---
title: 'ACSD-65331: l''archivio selezionato in [!UICONTROL Pick in Store] è stato cancellato dopo il ritorno all''estrazione'
description: Applicare la patch ACSD-65331 per risolvere il problema di Adobe Commerce in cui l'archivio selezionato nell'opzione [!UICONTROL Pick In Store] viene cancellato quando gli utenti tornano ripetutamente alla pagina di pagamento.
feature: Inventory
role: Admin, Developer
type: Troubleshooting
source-git-commit: a322e822ccf0b584d2385d3f38a3b92ebe3a23d3
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---


# ACSD-65331: l&#39;archivio selezionato in **[!UICONTROL Pick in Store]** è stato cancellato dopo il ritorno all&#39;estrazione

La patch ACSD-65331 risolve il problema che causa la cancellazione dell&#39;archivio selezionato nell&#39;opzione **[!UICONTROL Pick In Store]** quando gli utenti tornano ripetutamente alla pagina di pagamento. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65. L’ID della patch è ACSD-65331. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;archivio selezionato nell&#39;opzione **[!UICONTROL Pick In Store]** viene cancellato quando gli utenti tornano ripetutamente alla pagina di estrazione.

<u>Passaggi da riprodurre</u>:

1. Abilitare **[!UICONTROL In-Store Delivery]** passando a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]**.
1. Configurare una chiave API [!DNL Google] valida per [!UICONTROL Google Distance Provider] passando a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Google Distance Provider]**.
1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Sources]** > **[!UICONTROL Add New Source]** per aggiungere una nuova origine con i seguenti dettagli:

   * **[!UICONTROL Latitude]**: *41,917344*
   * **[!UICONTROL Longitude]**: *-88.102569*
   * **[!UICONTROL Use as Pickup Location]**: *Sì*
   * **[!UICONTROL Country]**: *Stati Uniti*
   * **[!UICONTROL State]**: *Illinois*
   * **[!UICONTROL City]**: *Flusso Carlo*
   * **[!UICONTROL Street]**: *565 E. Fullerton Ave.*
   * **[!UICONTROL Postcode]**: *60188*

1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Stocks]** > **[!UICONTROL Add New Stock]** per creare un nuovo titolo.

   Assegna a questo stock la sorgente appena creata e il sito web principale.
1. Modifica qualsiasi prodotto e:

   1. Assegnalo all’origine appena creata.
   1. Imposta lo stato su *[!UICONTROL In Stock]* e la quantità su un valore maggiore di 0.

1. Esegui i tuoi reindicizzatori.
1. Nella vetrina, crea un nuovo cliente e imposta un indirizzo della California come indirizzo predefinito per la fatturazione e la spedizione.
1. Aggiungi un ulteriore indirizzo Illinois allo stesso cliente (non predefinito).
1. Aggiungere il prodotto configurato al carrello e passare a **[!UICONTROL Checkout]**.
1. Selezionare l&#39;indirizzo dell&#39;Illinois, scegliere **[!UICONTROL Pick In Store]** come metodo di spedizione e fare clic su **[!UICONTROL Next]**.
1. Attendere il caricamento dell&#39;origine e fare clic su **[!UICONTROL Next]**.
1. Torna alla home page.
1. Rivedere la pagina **[!UICONTROL Checkout]**.

<u>Risultati previsti</u>:

L&#39;archivio selezionato dovrebbe rimanere disponibile in **[!UICONTROL Pick In Store]**.

<u>Risultati effettivi</u>:

Il passaggio di spedizione inizia a caricarsi e viene reindirizzato a **[!UICONTROL Pick In Store]**, ma non è visibile alcun archivio.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] **&#x200B; > Utilizzo]**(/help/tools/quality-patches-tool/usage.md) nella guida[!DNL Quality Patches Tool]**.
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch]**(https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool]**, vedere:

* [[!DNL Quality Patches Tool]&#x200B;**: strumento self-service per patch di qualità]**(/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida Strumenti.
