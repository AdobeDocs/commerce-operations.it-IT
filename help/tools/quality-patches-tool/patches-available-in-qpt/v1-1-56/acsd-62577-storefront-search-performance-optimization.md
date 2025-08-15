---
title: 'ACSD-62577: Ottimizzazione delle prestazioni di ricerca in vetrina'
description: Applica la patch ACSD-62577 per risolvere il problema di Adobe Commerce in cui le prestazioni di ricerca della vetrina si riducono a causa di una lenta esecuzione delle query causata da una grande tabella "search_query".
feature: Search
role: Admin, Developer
exl-id: 211c1e3c-0739-4ff6-a25c-b27d335920d1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# ACSD-62577: Ottimizzazione delle prestazioni di ricerca in vetrina

La patch ACSD-62577 risolve il problema con le prestazioni lente delle query di ricerca in vetrina ottimizzando sia gli indici di query che di tabella. Questa patch è disponibile con [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56. L’ID della patch è ACSD-62577. Il problema era pianificato per essere risolto in Adobe Commerce 2.4.8.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.6, 2.4.7-p2

**Compatibile con le versioni di Adobe Commerce:**

Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Le tabelle `search_query` di grandi dimensioni rallentano notevolmente le ricerche nella vetrina, aumentando i tempi di risposta front-end a causa di query inefficienti e della mancanza di indici di tabella ottimizzati.

<u>Passaggi da riprodurre</u>:

1. Configurare Adobe Commerce Develop utilizzando il toolkit delle prestazioni `small.xml`.
1. Accedere alla riga di comando SQL ed eliminare la tabella `search_query` utilizzando i comandi seguenti:

   ```
   SET FOREIGN_KEY_CHECKS = 0;  
   DROP TABLE search_query;  
   SET FOREIGN_KEY_CHECKS = 1;  
   ```

1. Popolare la tabella `search_query` con un numero elevato di record, ad esempio 4 milioni di record.
1. Attiva la reindicizzazione e svuota le cache.

   ```
   bin/magento indexer:reindex  
   bin/magento c:c  
   bin/magento c:f  
   ```

1. Abilita registri di debug del database:

   ```
   bin/magento dev:query-log:enable  
   ```

1. Cerca un termine nella barra di ricerca della vetrina, ad esempio,
   `http://your_magento_instance/default/catalogsearch/result/?q=test.`
1. Controllare `db.log` per il tempo di esecuzione della query per le istruzioni SQL seguenti:

   ```
   SELECT COUNT(*) FROM (  
   SELECT DISTINCT `main_table`.`query_text`  
   FROM `search_query` AS `main_table`  
   WHERE (main_table.store_id IN (1))  
   AND (main_table.num_results > 0)  
   ORDER BY `main_table`.`popularity` DESC  
   LIMIT 100  ) AS `result` WHERE (result.query_text = 'test')  
   ```

<u>Risultati previsti</u>:

Il tempo di esecuzione della query è ottimizzato, con conseguente aumento meno significativo del tempo di risposta durante l&#39;elaborazione di `search_query` tabelle di grandi dimensioni.

<u>Risultati effettivi</u>:

Il tempo di esecuzione della query aumenta in modo significativo a causa della gestione inefficiente della tabella `search_query` di grandi dimensioni:

```
TIME: 10.8520 seconds  
```

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool].
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud.

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti.
