---
title: 'ACSD-50817: Ottimizza l’esecuzione più rapida del processo cron sales_clean_quotes'
description: Applica la patch ACSD-50817 per ottimizzare il processo cron "sales_clean_quote" in modo che venga eseguito più rapidamente aggiungendo un indice composito nelle colonne "store_id" e "updated_at" della tabella delle quotazioni.
feature: Quotes
role: Admin
exl-id: b6cd412f-2f37-438b-9abc-d45de6ed54d6
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '354'
ht-degree: 0%

---

# ACSD-50817: Ottimizza l&#39;esecuzione più veloce del processo cron `sales_clean_quotes`

La patch ACSD-50817 ottimizza l&#39;esecuzione più rapida del processo cron `sales_clean_quotes` aggiungendo un indice composito nelle colonne `store_id` e `updated_at` della tabella delle virgolette. Questa patch è disponibile quando è installato [!DNL Quality Patches Tool (QPT)] 1.1.31. L’ID della patch è ACSD-50817.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p1

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.3.7 - 2.4.6

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il processo cron `sales_clean_quotes` è troppo lento. Con questa patch è stato ottimizzato per essere eseguito più rapidamente aggiungendo un indice composito nelle colonne `store_id` e `updated_at` della tabella delle virgolette.

<u>Passaggi da riprodurre</u>:

1. Genera 50-80M di preventivi con `updated_at` impostato come periodo &lt; 30 giorni.
1. Eseguire il processo cron `sales_clean_quotes` o la query seguente nella tabella dei preventivi:

   ```cron
   SELECT COUNT(*) FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0')
   
   SELECT * FROM `quote` AS `main_table` WHERE (`store_id` = '1') AND (`updated_at` <= '2023-02-25') AND (`is_persistent` = '0') LIMIT 50
   ```

<u>Risultati previsti</u>

Il processo Cron `sales_clean_quotes` è ottimizzato per essere eseguito più rapidamente aggiungendo un indice composito nelle colonne `store_id` e `updated_at` nella tabella delle virgolette.

<u>Risultati effettivi</u>

Query troppo lenta.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool] rilasciato: nuovo strumento per la gestione automatica delle patch di qualità](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) nella Knowledge Base di supporto.
* [Verifica se la patch è disponibile per il problema di Adobe Commerce utilizzando  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) nella guida di [!UICONTROL Quality Patches Tool].


Per informazioni sulle altre patch disponibili in QPT, fare riferimento a [[!DNL Quality Patches Tool]: Cercare le patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it) nella guida di [!DNL Quality Patches Tool].
