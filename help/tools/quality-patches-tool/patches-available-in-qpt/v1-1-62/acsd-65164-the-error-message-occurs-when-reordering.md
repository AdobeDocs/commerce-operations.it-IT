---
title: 'ACSD-65164: messaggio di errore durante il riordinamento di un prodotto configurabile con una singola opzione di selezione personalizzata selezionata'
description: Applica la patch ACSD-65164 per risolvere il problema di Adobe Commerce, in cui viene visualizzato il messaggio di errore *Alcune delle opzioni selezionate per l’elemento non sono attualmente disponibili* quando si riordina un prodotto configurabile con una singola opzione personalizzata selezionata per la casella di controllo.
feature: Products, Orders
role: Admin, Developer
exl-id: 22b72d24-4852-45ba-ac98-df9565f94539
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-65164: messaggio di errore durante il riordinamento di un prodotto configurabile con una singola opzione di selezione personalizzata selezionata

La patch ACSD-65164 risolve il problema che causa il messaggio di errore *Alcune delle opzioni selezionate per l&#39;elemento non sono attualmente disponibili* quando si riordina un prodotto configurabile con una singola opzione selezionata per la casella di controllo personalizzata. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62. L’ID della patch è ACSD-65164. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di distribuzione) 2.4.6-p8

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6 - 2.4.7-p4

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Quando si riordina un prodotto configurabile con una singola opzione personalizzata selezionata, il sistema restituisce un messaggio di errore: *Alcune delle opzioni selezionate per l&#39;elemento non sono attualmente disponibili*.

### Passaggi da replicare:

1. Nel pannello di amministrazione, vai a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]** > **[!UICONTROL Simple Product]**.
1. In **[!UICONTROL Customizable Options]**, aggiungere un&#39;opzione *Casella di controllo*.
   * Imposta l&#39;opzione della casella di controllo come *Obbligatorio*.
   * Aggiungi due valori di opzione.
1. Accedi allo Storefront e accedi come cliente registrato.
1. Aggiungi il prodotto al carrello selezionando una casella di controllo.
1. Vai a **[!UICONTROL Cart]** > **[!UICONTROL Proceed to Checkout]** > **[!UICONTROL Place an Order]**.
1. Vai a **[!UICONTROL My Account]** > **[!UICONTROL Orders]** > **[!UICONTROL Reorder]** per aggiungere lo stesso prodotto.

**Risultati previsti:**

Il prodotto deve essere aggiunto correttamente al carrello.

**Risultati effettivi:**

Viene visualizzato un messaggio di errore:

*Impossibile aggiungere il prodotto con SKU &quot;24-MB01&quot; al carrello: alcune delle opzioni selezionate per l&#39;elemento non sono attualmente disponibili.*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
