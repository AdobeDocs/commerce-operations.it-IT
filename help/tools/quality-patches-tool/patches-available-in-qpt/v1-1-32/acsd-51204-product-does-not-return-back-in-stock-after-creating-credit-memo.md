---
title: 'ACSD-51204: Il prodotto non ritorna in magazzino dopo aver creato la nota di credito'
description: Applica la patch ACSD-51204 per risolvere il problema di Adobe Systems Commerce in cui il prodotto non torna in magazzino dopo aver creato la nota di credito.
feature: Orders, Products, Returns
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# ACSD-51204: Il prodotto non ritorna in magazzino dopo aver creato la nota di credito

La patch ACSD-51204 risolve il problema per cui il prodotto non ritorna in magazzino dopo aver creato la nota di credito. Questa patch è disponibile quando è installato 1.1.32 [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) . L&#39;ID della patch è ACSD-51204. Nota: il problema è stato risolto in Adobe Systems Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con nuove [!DNL Quality Patches Tool] versioni. Per verificare se la patch è compatibile con la versione di Adobe Systems Commerce in uso, aggiornare il `magento/quality-patches` pacchetto alla versione più recente e verificare la compatibilità nella [[!DNL Quality Patches Tool]pagina](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) : Search for patches. Utilizzare l&#39;ID patch come parola chiave di ricerca per individuare la patch.

## Questione

Il prodotto esaurito non ritorna in magazzino dopo aver creato la nota di credito.

<u>Passaggi da riprodurre</u>:

1. Installa **[!UICONTROL Adobe Commerce]** e abilita il **[!UICONTROL Inventory Management Module]** solo con origine *predefinita* e *stock*.
1. Aggiungi un **[!UICONTROL new product]** con un quantità di *10*.
1. Assegnare il prodotto a **[!UICONTROL default stock]**.
1. Nella vetrina, aggiungi il prodotto al carrello e ordina per una quantità intera disponibile pari a 10.
1. Nel pannello di amministrazione, genera una *fattura* e una *spedizione* per l&#39;ordine.
1. Crea un **[!UICONTROL Credit Memo]** con la casella di controllo *torna allo stock* selezionata per tutti gli elementi.
1. Controlla che il prodotto sia **[!UICONTROL Salable Quantity]** nel pannello di amministrazione.

<u>Risultati attesi</u>:

La quantità vendibile del prodotto deve tornare a *10*.

<u>Risultati effettivi</u>:

La quantità vendibile del prodotto viene lasciata come *0*.

## Applica la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](</help/tools/quality-patches-tool/usage.md>) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] Rilasciato: una nuova strumento di patch](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) di qualità self-service nel knowledge base di supporto.
* [Controlla se la patch è disponibile per il tuo problema di Adobe Systems Commerce utilizzando [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) la [!UICONTROL Quality Patches Tool] guida.


Per informazioni su altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Search per le](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) patch nella [!DNL Quality Patches Tool] guida.
