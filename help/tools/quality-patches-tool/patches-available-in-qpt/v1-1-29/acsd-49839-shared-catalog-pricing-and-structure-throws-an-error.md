---
title: 'ACSD-49839: la struttura e i prezzi del catalogo condiviso genera un errore'
description: Applica la patch ACSD-49839 per risolvere il problema di Adobe Commerce, a causa del quale la struttura e i prezzi del catalogo condiviso generano un errore nell’amministratore quando i prodotti presentano virgolette singole o doppie in SKU.
feature: Admin Workspace, Catalog Management, Categories
role: Admin
exl-id: b74e3926-16c8-4222-b642-ed1b7095dea4
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-49839: la struttura e i prezzi del catalogo condiviso genera un errore

La patch ACSD-49839 risolve il problema relativo alla struttura e ai prezzi del catalogo condiviso genera un errore nell’amministratore quando i prodotti presentano virgolette singole o doppie in SKU. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.29. L’ID della patch è ACSD-49839. Il problema è pianificato per la risoluzione in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

La struttura e il prezzo del catalogo condiviso genera un errore nell’amministratore quando i prodotti presentano virgolette singole o doppie in SKU.

<u>Passaggi da riprodurre</u>:

1. Imposta alcuni SKU del prodotto con un carattere speciale, ad esempio virgolette doppie come:
   *[Prodotto&quot;12, Prodotto&quot;14, Prodotto&quot;15]*.
1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalog]** > **[!UICONTROL Add Shared Catalog]** (ad esempio,*[Test catalogo condiviso]*).
1. Assegna tutti i **[!UICONTROL Products and Categories]** > **[!UICONTROL Generate Catalog]** > **[!UICONTROL Save]**.
1. Vai a **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalog]** > **[!UICONTROL Test Shared Catalog]** > **[!UICONTROL Action]** > **[!UICONTROL Set Pricing and Structure]**.
1. Contrassegna *[!UICONTROL Root Catalog]* per selezionare tutte le categorie e i prodotti.
1. Osserva le richieste dell’AJAX nel pannello di rete.

<u>Risultati previsti</u>:

La struttura e il prezzo del catalogo condiviso non genera un errore nell’amministratore quando i prodotti presentano virgolette singole o doppie in SKU.

<u>Risultati effettivi</u>:

La struttura e i prezzi del catalogo condiviso generano un errore nell’amministratore quando i prodotti presentano virgolette singole o doppie in SKU.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
