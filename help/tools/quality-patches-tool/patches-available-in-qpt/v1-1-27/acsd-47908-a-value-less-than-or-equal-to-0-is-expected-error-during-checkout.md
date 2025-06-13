---
title: 'ACSD-47908: *È previsto un valore minore o uguale a 0* errore durante il check-out'
description: Applicare la patch ACSD-47908 per correggere l'errore Adobe Commerce *È previsto un valore minore o uguale a 0* quando si selezionano l'origine e la quantità nella fase di spedizione durante il pagamento.
feature: Admin Workspace, Checkout, Orders
role: Admin
exl-id: f1429bd9-652d-43c0-af52-b2258e2a7643
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '472'
ht-degree: 0%

---

# ACSD-47908: *È previsto un valore minore o uguale a 0* errore durante l&#39;estrazione

La patch ACSD-47908 corregge l&#39;errore *È previsto un valore minore o uguale a 0* durante la selezione dell&#39;origine e della quantità nella fase di spedizione durante l&#39;estrazione. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27. L’ID della patch è ACSD-47908. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Viene generato il seguente errore durante la selezione dell&#39;origine e della quantità nella fase di spedizione durante l&#39;estrazione: *È previsto un valore minore o uguale a 0*.

<u>Prerequisiti</u>:

Installa i moduli Adobe Commerce Inventory management (MSI).

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Sources]** e configura più origini.
1. Vai a **[!UICONTROL Stores]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock]** e crea un nuovo titolo.
   * Ora assegna le origini al nuovo stock.
1. Vai a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** e modifica almeno un prodotto.
   * Assicurati che i prodotti siano assegnati alle nuove origini e specifica la quantità disponibile.
1. Vai a **[!UICONTROL Sales]** > **[!UICONTROL Orders]** e crea un nuovo ordine.
1. Aggiungi questi prodotti all’ordine e inseriscili.
1. Fare clic su **[!UICONTROL Ship]**.
1. Selezionare l&#39;origine da cui spedire.
1. Specifica la quantità di ciascun articolo da spedire.
1. Ricarica la pagina.
1. Fai clic su **[!UICONTROL Proceed to Shipment]**.

<u>Risultati previsti</u>:

La nuova pagina di spedizione viene visualizzata senza errori.

<u>Risultati effettivi</u>:

* Impossibile convalidare la quantità immessa.
* Viene generato il seguente errore: *Immettere un valore minore o uguale a 0*.

  L’errore è, tuttavia, incoerente e potrebbe non apparire sempre.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
