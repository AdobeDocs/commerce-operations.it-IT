---
title: 'ACSD-59083: errori di tabella o visualizzazione di base non trovati durante gli aggiornamenti simultanei di visualizzazione'
description: Applicare la patch ACSD-59083 per risolvere il problema di Adobe Commerce, se alcune operazioni di aggiornamento del database non riescono e viene visualizzato l'errore "Tabella o vista di base non trovata".
feature: System
role: Admin, Developer
source-git-commit: 7f091ff8db7973c4290e0412d19e9088f1220cef
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---

# ACSD-59083: *Tabella o vista di base non trovata* errori durante `mview` aggiornamenti simultanei

La patch di ACSD-59083 risolve il problema relativo al mancato funzionamento di alcune operazioni di aggiornamento del database con l&#39;errore &quot;Tabella o vista di base non trovata&quot; quando `mview` aggiornamenti vengono eseguiti contemporaneamente. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57. L’ID della patch è ACSD-59083. Il problema è stato risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.5-p5

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Alcune operazioni di aggiornamento del database generano errori di tipo &quot;Tabella di base o vista non trovata&quot; quando `mview` aggiornamenti vengono eseguiti contemporaneamente.

<u>Passaggi da riprodurre</u>:

1. Imposta la modalità indicizzatore su **[!UICONTROL Update on Schedule]**.
1. Inserire record nelle tabelle `cl` utilizzando i seguenti comandi SQL:

   ```
   INSERT INTO catalogrule_product_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalogrule_rule_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalogsearch_fulltext_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalog_category_product_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalog_product_attribute_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalog_product_category_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO catalog_product_price_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO customer_dummy_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO design_config_dummy_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO salesrule_rule_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO targetrule_product_rule_cl SELECT NULL, entity_id FROM catalog_product_entity;
   INSERT INTO targetrule_rule_product_cl SELECT NULL, entity_id FROM catalog_product_entity;
   ```

1. Installa il profilo `setup/performance-toolkit/profiles/ce/small.xml`.
1. Aggiungere un punto di interruzione nel file `magento2ee/lib/internal/Magento/Framework/ForeignKey/Config/DbReader.php` alla riga 72.
1. Cancella la cache.
1. Fai clic su **[!UICONTROL Add to Cart]** per qualsiasi prodotto.
1. Avvia il processo cron quando l’esecuzione raggiunge il punto di interruzione.
1. Riprendi il processo dopo l’avvio del processo cron.

<u>Risultati previsti</u>:

Le operazioni del database vengono eseguite senza errori.

<u>Risultati effettivi</u>:

Si è verificato un errore durante l&#39;esecuzione:

```
SQLSTATE[42S02]: Base table or view not found: 1146 Table 'magento24.design_config_dummy_cl__tmp663bb682960345_17794892' doesn't exist in /www/magento24/lib/internal/Magento/Framework/DB/Statement/Pdo/Mysql.php:90
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source locale: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=it) nella guida Commerce su infrastruttura cloud.


## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
