---
title: 'ACSD-61667: migliora le prestazioni di inventario per la creazione di spedizioni'
description: Applicare la patch ACSD-60584 per migliorare le prestazioni di inventario per la creazione di spedizioni in caso di molte sorgenti con prelievo in-store.
feature: Customers, Shipping/Delivery
role: Admin, Developer
exl-id: 47682daf-9117-45f1-ab09-a66c13132ff3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACSD-61667: migliora le prestazioni di inventario per la creazione di spedizioni

La patch ACSD-61667 risolve il problema che impedisce al commerciante di spedire l&#39;ordine quando l&#39;archivio di prelievo [[!DNL Inventory Management for Commerce]](https://experienceleague.adobe.com/it/docs/commerce-admin/inventory/introduction) (precedentemente MSI) è abilitato con più origini. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.53. L’ID della patch è ACSD-61667. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.6-p5

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Non puoi spedire l&#39;ordine quando l&#39;archivio di prelievo MSI è abilitato, con più origini. Questa patch migliora le prestazioni di inventario per creare la spedizione in caso di molte sorgenti con prelievo in-store.

<u>Prerequisiti:</u>:

I moduli di Adobe Commerce Inventory vengono installati e abilitati.

<u>Passaggi da riprodurre</u>:

1. Crea più di *10* origini e abilita le relative posizioni di prelievo.
1. L&#39;archivio di prelievo è abilitato in **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Delivery Methods]** > **[!UICONTROL In-Store Delivery]**.
1. Crea un grande volume di ordini di prelievo.
1. Vai a **[!UICONTROL Admin login]** e seleziona **[!UICONTROL Sales]** > **[!UICONTROL Orders]** > **[!UICONTROL View]**.
1. Filtra e controlla gli ordini in sospeso.
1. Fai clic su **[!UICONTROL Ship]**.

<u>Risultati previsti</u>:

La pagina di spedizione viene caricata come previsto.

<u>Risultati effettivi</u>:

Si riceve un errore *503 di timeout massimo di esecuzione*.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
