---
title: 'ACSD-47803: campioni di prodotto configurabili esauriti visualizzati come disponibili'
description: Applica la patch ACSD-47803 per risolvere il problema di Adobe Commerce, se i campioni di prodotto configurabili esauriti vengono visualizzati come disponibili.
feature: Configuration, Orders, Products
role: Admin
exl-id: c1b80949-65ed-4a44-8be4-25decda32142
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-47803: campioni di prodotto configurabili esauriti visualizzati come disponibili

La patch ACSD-47803 risolve il problema relativo alla disponibilità di campioni di prodotto configurabili esauriti. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24. L’ID della patch è ACSD-47803. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.6.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

I campioni di prodotto configurabili esauriti vengono visualizzati in base alla disponibilità.

<u>Passaggi da riprodurre</u>:

>[!NOTE]
>
>I passaggi seguenti si riferiscono a dati di esempio.

1. Nell&#39;amministratore [!UICONTROL Commerce], passare a **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** e impostare **[!UICONTROL Display Out of Stock Products]** su *Sì*.
1. Dall&#39;amministratore, passare a **[!UICONTROL Catalog]** > **[!UICONTROL Products]** e modificare un prodotto configurabile nella pagina di modifica del prodotto (ad esempio, SKU &quot;WB04&quot;, se si utilizzano dati di esempio):
   * Per una delle varianti di configurazione, impostare la quantità su *0* (ad esempio, per &quot;WB04-M-Purple&quot;).
1. Ora apri il prodotto configurabile sulla vetrina.
1. Seleziona la dimensione del prodotto per la variante configurabile con zero azioni (cioè &quot;M&quot;).

<u>Risultati previsti</u>:

Le opzioni esaurite sono disabilitate e contrassegnate come [!UICONTROL Out of Stock].

<u>Risultati effettivi</u>:

Tutti i campioni colore sono abilitati, anche quello che è [!UICONTROL Out of Stock].

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
