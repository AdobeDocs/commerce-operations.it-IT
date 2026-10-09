---
title: Best practice per la migrazione dei dati
description: Segui queste best practice per la migrazione dei dati per garantire un aggiornamento corretto da Magento 1 a Magento 2.
exl-id: 0cd51987-a514-434d-b21e-2739ada2ce85
feature: Best Practices, Configuration
topic: Commerce, Migration
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%
---
# Best practice per la migrazione dei dati

Questa sezione fornisce consigli su come accelerare e semplificare la migrazione e indicazioni sul tempo necessario.

* **Utilizzare una copia del database da un&#39;istanza di Magento 1** durante l&#39;esecuzione dei test di migrazione. Non utilizzare l’istanza di produzione del database store di Magento 1.

* **Rimuovere i dati obsoleti e ridondanti** dal database Magento 1 prima della migrazione.

Tali dati possono includere registri, preventivi d’ordine, prodotti visualizzati o confrontati di recente, visitatori, categorie specifiche dell’evento e regole promozionali.

* **Segui le [regole generali per la corretta migrazione](migrate-data/overview.md#migration-overview)**.

* Per migliorare le prestazioni, **abilita l&#39;opzione `direct_document_copy`** nel file `config.xml`:

  ```xml
  <direct_document_copy>1</direct_document_copy>
  ```

>[!NOTE]
>
>I database Magento 1 e Magento 2 devono trovarsi sullo stesso server MySQL e l&#39;account di database deve avere accesso a entrambi i database.

## Stime di benchmarking

Adobe ha testato la migrazione dei dati sul seguente sistema:

* Virtual Box VM, CentOS 6, 2,5 GB di RAM, CPU 1 core a 2,6 GHz
* Database con 177.000 prodotti, 355.000 ordini e 214.000 clienti

## Risultati delle prestazioni

* Tempo di migrazione delle impostazioni: circa 10 minuti
* Tempo di migrazione dei dati: circa 9 ore (tutti i dati tranne le riscritture URL, circa l’85% dei dati totali)
* Stima dei tempi di inattività del sito: alcuni minuti per reindicizzare e modificare le impostazioni DNS. Tempo aggiuntivo necessario per riscaldare la cache delle pagine.
