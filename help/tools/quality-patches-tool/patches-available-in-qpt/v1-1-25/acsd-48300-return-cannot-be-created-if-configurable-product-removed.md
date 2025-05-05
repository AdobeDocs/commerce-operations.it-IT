---
title: "ACSD-48300: impossibile creare il reso se il prodotto configurabile viene rimosso"
description: Applica la patch ACSD-48300 per risolvere il problema di Adobe Commerce, per il quale non è possibile creare una restituzione se il prodotto configurabile viene rimosso.
feature: Admin Workspace, Configuration, Orders, Products, Returns
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-48300: impossibile creare la restituzione se il prodotto configurabile viene rimosso

La patch ACSD-48300 risolve il problema che impediva la creazione di un reso in caso di rimozione del prodotto configurabile. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.25. L’ID della patch è ACSD-48300. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Non è possibile creare una restituzione se il prodotto configurabile viene rimosso.

<u>Passaggi da riprodurre</u>:

1. Abilitare RMA nella vetrina in **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Sales]** > **[!UICONTROL RMA Settings]**.
1. Crea un prodotto configurabile.
1. Nella vetrina, crea un account (e/o accedi).
1. Aggiungi un prodotto configurabile al carrello come primo elemento.
1. Aggiungi successivamente qualsiasi prodotto semplice.
1. Effettua l’ordine.
1. Spedisci l&#39;ordine.
1. Ora elimina solo il prodotto configurabile (non eliminare i relativi prodotti secondari).
1. Nella vetrina, vai a **[!UICONTROL My Orders]** e visualizza l&#39;ordine.
1. Fai clic su **[!UICONTROL Return]**.

<u>Risultati previsti</u>:

L’amministratore è in grado di restituire gli elementi anche se il prodotto configurabile viene eliminato.

<u>Risultati effettivi</u>:

Si verifica un errore quando si restituiscono elementi.

```
report.CRITICAL: Error: Call to a member function getShipmentType() on null in magento2ee/app/code/Magento/Rma/view/frontend/templates/return/create.phtml:52
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
