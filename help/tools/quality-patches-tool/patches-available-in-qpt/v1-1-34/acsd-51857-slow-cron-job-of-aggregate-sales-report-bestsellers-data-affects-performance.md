---
title: 'ACSD-51857: il processo cron lento di "aggregate_sales_report_bestsellers_data" influisce sulle prestazioni'
description: Applica la patch ACSD-51857 per risolvere il problema di Adobe Commerce dove il processo cron lento "aggregate_sales_report_bestsellers_data" influisce sulle tabelle di database "sales_order" e "sales_order_item" di grandi dimensioni.
exl-id: 48e9852d-2cf6-411c-adf6-f91ac7743338
source-git-commit: 81c78439f7c243437b7b76dc80560c847af95ace
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-51857: il processo cron lento di `aggregate_sales_report_bestsellers_data` influisce sulle prestazioni

La patch ACSD-51857 risolve il problema relativo al processo cron lento `aggregate_sales_report_bestsellers_data` che interessa le tabelle di database `sales_order` e `sales_order_item` di grandi dimensioni. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.34. L’ID della patch è ACSD-51857. Il problema è stato risolto in Adobe Commerce 2.4.7.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.3-p2

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.0 - 2.4.6-p2

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le prestazioni del processo Cron di `aggregate_sales_report_bestsellers_data` sono lente nelle tabelle di database `sales_order` e `sales_order_item`.

Per risolvere questo problema, la query di dati principale che raccoglie i dati per il report è stata riscritta in un modulo più efficiente. Ora utilizza una sottoquery per determinare il sottoinsieme di dati.

Affinché la sottoquery funzioni il più rapidamente possibile, è stato aggiunto un nuovo indice per la tabella del database `sales_order`: `SALES_ORDER_STORE_STATE_CREATED` basato su `store_id`, `state` e `created_at` colonne.

<u>Prerequisiti</u>

Assicurati un numero elevato di ordini al giorno.

<u>Passaggi da riprodurre</u>

1. Eseguire il processo cron `aggregate_sales_report_bestsellers_data`.
1. Controllare i dati da visualizzare nel dashboard di amministrazione, nella scheda **[!UICONTROL Bestsellers]**.

<u>Risultati previsti</u>:

*[!UICONTROL Quantity per source]* nella scheda **[!UICONTROL Configuration]** non deve essere vuoto.

<u>Risultati effettivi</u>:

*[!UICONTROL Quantity per source]* nella scheda **[!UICONTROL Configuration]** è vuoto.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
