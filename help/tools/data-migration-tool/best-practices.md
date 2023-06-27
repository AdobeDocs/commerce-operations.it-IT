---
title: Best practice per la migrazione dei dati
description: Segui queste best practice per la migrazione dei dati per garantire un aggiornamento corretto dal Magento 1 al Magento 2.
exl-id: 0cd51987-a514-434d-b21e-2739ada2ce85
feature: Best Practices, Configuration
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '201'
ht-degree: 0%

---

# Best practice per la migrazione dei dati

Questa sezione fornisce consigli su come accelerare e semplificare la migrazione e indicazioni sul tempo necessario.

* **Utilizzare una copia del database da un&#39;istanza del Magento 1** durante l’esecuzione dei test di migrazione. Non utilizzare l&#39;istanza di produzione del database dell&#39;archivio di Magento 1.

* **Rimuovere i dati obsoleti e ridondanti** dal database del Magento 1 prima della migrazione.

Tali dati possono includere registri, preventivi d’ordine, prodotti visualizzati o confrontati di recente, visitatori, categorie specifiche dell’evento e regole promozionali.

* **Segui le [regole generali per una migrazione corretta](migrate-data/overview.md#migration-overview)**.

* Per migliorare le prestazioni, **abilita `direct_document_copy` opzione** nel tuo `config.xml` file:

  ```xml
  <direct_document_copy>1</direct_document_copy>
  ```

>[!NOTE]
>
>I database del Magento 1 e del Magento 2 devono trovarsi sullo stesso server MySQL e l&#39;account del database deve avere accesso a entrambi i database.

## Stime di benchmarking

Adobe ha testato la migrazione dei dati sul seguente sistema:

* Virtual Box VM, CentOS 6, 2,5 GB di RAM, CPU 1 core 2,6 GHz
* Database con 177.000 prodotti, 355.000 ordini e 214.000 clienti

## Risultati delle prestazioni

* Tempo di migrazione delle impostazioni: circa 10 minuti
* Tempo di migrazione dei dati: circa 9 ore (tutti i dati tranne le riscritture URL, circa l’85% dei dati totali)
* Stima dei tempi di inattività del sito: alcuni minuti per reindicizzare e modificare le impostazioni DNS. Tempo aggiuntivo necessario per riscaldare la cache delle pagine.
