---
title: "ACSD-50813: l’amministratore non è in grado di aggiungere prodotti in bundle contenenti una barra"
description: Applica la patch ACSD-50813 per risolvere il problema di prestazioni di Adobe Commerce, in cui l’amministratore non può aggiungere prodotti in bundle contenenti una barra (`/`) nello SKU con la funzionalità *Add Products by SKU* (Aggiungi prodotti per SKU) all’ordine di amministrazione.
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-50813: l’amministratore non è in grado di aggiungere prodotti in bundle contenenti una barra

La patch ACSD-50813 risolve il problema che impediva all&#39;amministratore di aggiungere prodotti in bundle contenenti un segno di barra (`/`) nello SKU con la funzionalità *[!UICONTROL Add Products by SKU]* all&#39;ordine di amministrazione. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.34. L’ID della patch è ACSD-50813. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

L&#39;amministratore non può aggiungere prodotti in bundle contenenti un segno di barra (`/`) nello SKU con la funzionalità *[!UICONTROL Add Products by SKU]* all&#39;ordine di amministrazione.

<u>Passaggi da riprodurre</u>:

1. Vai a **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Crea un prodotto semplice.
1. Crea un nuovo prodotto incluso.
1. Aggiungere un segno di barra (`/`) al centro dello SKU (esempio: *Bu/ndle*).
1. Aggiungi un&#39;opzione nel bundle con **[!UICONTROL Input Type]** = *[!UICONTROL Dropdown]*.
1. Assegna all’opzione almeno un prodotto semplice.
1. Vai a **[!UICONTROL Sales]** > **[!UICONTROL Orders]** e crea un nuovo ordine.
1. Fai clic su **[!UICONTROL Add Products by SKU]**.
1. Immettere lo SKU e fare clic su **[!UICONTROL Add to Order]**.
1. Apri la console del browser.
1. Fai clic su **[!UICONTROL Configure]**.

<u>Risultati previsti</u>:

Nessun errore.

<u>Risultati effettivi</u>:

Errore JS nella console:

*Errore non rilevato: errore di sintassi, espressione non riconosciuta: div[id=sku_bu/ndle]*

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) nella guida di [!DNL Quality Patches Tool].
