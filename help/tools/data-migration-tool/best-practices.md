---
title: Best practice per la migrazione dei dati
description: Segui queste best practice per la migrazione dei dati per garantire il successo dell’aggiornamento dal Magento 1 al Magento 2.
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---


# Best practice per la migrazione dei dati

Questa sezione fornisce i consigli migliori per accelerare e semplificare la migrazione e indicazioni su quanto tempo potrebbe richiedere.

* **Utilizzare una copia del database da un&#39;istanza del Magento 1** durante l’esecuzione del test di migrazione. Non utilizzare l&#39;istanza di produzione del database dell&#39;archivio Magento 1.

* **Rimuovere i dati obsoleti e ridondanti** dal database di Magento 1 prima della migrazione.

Tali dati possono includere registri, preventivi degli ordini, prodotti visualizzati o confrontati di recente, visitatori, categorie specifiche per gli eventi e regole promozionali.

* **Segui [regole generali per il successo della migrazione](migrate-data/overview.md#migration-overview)**.

* Per migliorare le prestazioni, **abilita `direct_document_copy` opzione** nel tuo `config.xml` file:

   ```xml
   <direct_document_copy>1</direct_document_copy>
   ```

>[!NOTE]
>
>I database di Magento 1 e Magento 2 devono trovarsi sullo stesso server MySQL e l&#39;account di database deve avere accesso a entrambi i database.

## Stime di benchmarking

Adobe ha testato la migrazione dei dati sul seguente sistema:

* VM Virtual Box, CentOS 6, 2,5 GB di RAM, CPU 1 core 2,6 GHz
* Database con 177.000 prodotti, 355.000 ordini e 214.000 clienti

## Risultati delle prestazioni

* Tempo di migrazione delle impostazioni: ~10 minuti
* Tempo di migrazione dei dati: ~9 ore (tutti i dati tranne le riscritture URL, circa l’85% dei dati totali)
* Stima dei tempi di inattività del sito: alcuni minuti per reindicizzare e modificare le impostazioni DNS. Tempo aggiuntivo necessario per riscaldare la cache della pagina.