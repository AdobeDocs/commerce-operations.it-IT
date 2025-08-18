---
title: 'ACSD-66404: il processo Cron non riesce a cancellare le tabelle del registro delle modifiche a causa di  [!DNL Galera Cluster]  limiti di dimensione delle transazioni'
description: Applica la patch ACSD-66404 per risolvere il problema di Adobe Commerce che, con il processo cron, non cancella le tabelle del registro delle modifiche e causa  [!DNL Galera Cluster]  problemi in caso di grandi quantità di dati in queste tabelle.
feature: System
role: Admin, Developer
type: Troubleshooting
source-git-commit: 42bd5934782ca65b891a36f61102083356c92e59
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---


# ACSD-66404: il processo Cron non riesce a cancellare le tabelle del registro delle modifiche a causa dei limiti di dimensione delle transazioni [!DNL Galera Cluster]

La patch ACSD-66404 risolve il problema che impediva al processo cron di cancellare le tabelle del registro delle modifiche, causando [!DNL Galera Cluster] problemi durante la gestione di grandi quantità di dati. Questa patch è disponibile quando è installato [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69. L’ID della patch è ACSD-66404. Questo problema è pianificato per la risoluzione in Adobe Commerce 2.4.9.

## Prodotti e versioni interessati

**La patch è stata creata per la versione di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di distribuzione) 2.4.6-p6, 2.4.7-p6

**Compatibile con le versioni di Adobe Commerce:**

* Adobe Commerce (tutti i metodi di implementazione) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>La patch potrebbe diventare applicabile ad altre versioni con le nuove versioni di [!DNL Quality Patches Tool]. Per verificare se la patch è compatibile con la versione di Adobe Commerce in uso, aggiornare il pacchetto `magento/quality-patches` alla versione più recente e verificare la compatibilità nella pagina [[!DNL Quality Patches Tool]: Cerca patch](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Utilizza l’ID patch come parola chiave di ricerca per individuare la patch.

## Problema

Il processo Cron non cancella le tabelle del registro delle modifiche e causa [!DNL Galera Cluster] problemi in caso di grandi quantità di dati in queste tabelle.

<u>Passaggi da riprodurre</u>:

1. Genera molti prodotti utilizzando i profili di prestazioni.
1. Eseguire un aggiornamento in blocco per tutti i prodotti nel sistema, in modo che siano presenti molte voci nella tabella del database `inventory_cl`.
1. Esegui il processo cron `indexer_clean_all_changelogs`.

<u>Risultati previsti</u>:

Il processo cron `indexer_clean_all_changelogs` è in grado di eseguire la pulizia del registro modifiche in un registro modifiche di grandi dimensioni (10+ GB) in più query di eliminazione, senza causare [!DNL Galera Cluster] problemi.

<u>Risultati effettivi</u>:

Il processo cron `indexer_clean_all_changelogs` esegue la pulizia del registro modifiche in un registro modifiche di grandi dimensioni (10+ GB) in una singola query di eliminazione, causando [!DNL Galera Cluster] problemi.

## Applicare la patch

Per applicare singole patch, utilizzare i collegamenti seguenti, a seconda del metodo di distribuzione utilizzato:

* Adobe Commerce o Magento Open Source on-premise: [[!DNL Quality Patches Tool] > Utilizzo](/help/tools/quality-patches-tool/usage.md) nella guida di [!DNL Quality Patches Tool]
* Adobe Commerce su infrastruttura cloud: [Aggiornamenti e patch > Applica patch](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) nella guida Commerce su infrastruttura cloud

## Lettura correlata

Per ulteriori informazioni su [!DNL Quality Patches Tool], vedere:

* [[!DNL Quality Patches Tool]: strumento self-service per patch di qualità](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) nella guida degli strumenti
