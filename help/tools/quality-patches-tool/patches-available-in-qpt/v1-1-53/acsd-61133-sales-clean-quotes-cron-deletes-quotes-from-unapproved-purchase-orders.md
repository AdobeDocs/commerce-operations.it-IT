---
title: 'ACSD-61133: cron "sales_clean_quotes" elimina i preventivi da ordini di acquisto non approvati'
description: Applica la patch ACSD-61133 per risolvere il problema Adobe Commerce per cui il cron "sales_clean_quotes" elimina i preventivi da ordini di acquisto non approvati.
feature: B2B, Purchase Orders
role: Admin, Developer
exl-id: 06979d4b-08ea-40fe-a211-3d950c9afb47
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# ACSD-61133: `sales_clean_quotes` cron elimina i preventivi da ordini fornitore non approvati

La patch ACSD-61133 risolve il problema relativo all&#39;eliminazione dei preventivi da ordini di acquisto non approvati da parte del cron `sales_clean_quotes`. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.53. L’ID della patch è ACSD-61133. Il problema è pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.7-p1

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di distribuzione) 2.4.4-p5 - 2.4.4-p11, 2.4.5-p4 - 2.4.5-p10 e 2.4.6-p2 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

`sales_clean_quotes` cron elimina i preventivi da ordini fornitore non approvati. L&#39;ordine di acquisto *[B2B]* non può essere convertito nell&#39;ordine del preventivo associato all&#39;ordine acquistato perché è stato eliminato dal cron.

<u>Prerequisiti</u>:

I moduli Adobe Commerce [!UICONTROL B2B] sono installati e abilitati.

<u>Passaggi da riprodurre</u>:

1. Abilita la funzionalità *[!UICONTROL B2B Purchase Order]*.
1. Crea una società.
1. Crea un *[!UICONTROL Purchase Order]*.
1. Attendi la scadenza del preventivo e viene eliminato dalla cron. Il periodo di scadenza dell&#39;offerta può essere impostato con **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** > **[!UICONTROL General]** > **[!UICONTROL Default Expiration Period configuration]**.
1. Convertire *[!UICONTROL Purchase Order]* nell&#39;ordine tramite *[!UICONTROL My Purchase Order in Customer Dashboard]* o con mutazione [!DNL GraphQL] `placeOrderForPurchaseOrder`.

<u>Risultati previsti</u>:

Il preventivo associato a *[!UICONTROL Purchase Order]* attivo non viene eliminato in quanto scaduto dal cron. L&#39;ordine è stato effettuato correttamente nella vetrina o tramite [!DNL GraphQL].

<u>Risultati effettivi</u>:

L&#39;ordine non viene effettuato e viene visualizzato un errore nella vetrina o restituito nella risposta [!DNL GraphQL].

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
