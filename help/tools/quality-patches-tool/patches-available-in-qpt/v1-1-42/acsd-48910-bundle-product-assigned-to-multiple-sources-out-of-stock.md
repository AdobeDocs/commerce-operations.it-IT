---
title: "ACSD-48910: il prodotto in bundle assegnato a più origini esaurirà le scorte dopo la fatturazione e la spedizione"
description: Applicare la patch ACSD-48910 per risolvere il problema di Adobe Commerce, in cui il prodotto in bundle assegnato a più origini esaurisce le scorte dopo che un ordine è stato fatturato e spedito, anche se presenta ancora una quantità diversa da zero.
feature: Products, Inventory
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# ACSD-48910: il prodotto in bundle assegnato a più origini esaurisce dopo la fatturazione e la spedizione

La patch ACSD-48910 risolve il problema che causa l&#39;esaurimento delle scorte del prodotto in bundle assegnato a più origini dopo la fatturazione e la spedizione di un ordine, anche se la quantità è diversa da zero. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.42. L’ID della patch è ACSD-48910. Il problema è stato risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il prodotto in bundle assegnato a più origini esaurirà le scorte dopo la fatturazione e la spedizione, anche se è ancora disponibile.

<u>Passaggi da riprodurre</u>:

1. Crea due siti Web.
1. Crea due store/viste store (uno per sito web).
1. Creare due prodotti semplici (qtà = 10) e assegnarli sia alle scorte che ai siti Web.
1. Crea un prodotto in bundle e aggiungi questi semplici prodotti. Assegna il prodotto in bundle a entrambi i siti web.
1. Vai alla vetrina e aggiungi il prodotto nel carrello.
1. Estrai e ordina.
1. Dall’amministratore, fatturare e spedire l’ordine.

<u>Risultati previsti</u>:

Il prodotto in bundle rimane in magazzino da quando abbiamo acquistato solo 1 dei 10 articoli.

<u>Risultati effettivi</u>:

Il prodotto nel pacchetto cambia il suo stato in esaurito.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
