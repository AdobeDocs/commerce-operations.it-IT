---
title: Rimuovi o aggiorna i moduli dati di esempio
description: Per gestire i moduli dati di esempio di Adobe Commerce, segui la procedura riportata di seguito.
exl-id: d23f999f-18bf-449b-be23-bdf392dda539
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---

# Rimuovi o aggiorna i moduli dati di esempio

In questo argomento viene illustrato come:

* [Rimuovi moduli dati di esempio](#remove-sample-data-modules) da un’installazione di Adobe Commerce o di Magento Open Source `composer.json`. Questa opzione funziona *non* rimuovere i dati di esempio dal database.

* [Preparare l’aggiornamento dei dati di esempio](#prepare-to-update-sample-data) (ad esempio, prima di aggiornare l’applicazione di Magento).

## Rimuovi moduli dati di esempio

Immetti il comando seguente:

```bash
bin/magento sampledata:remove
```

L’elenco completo dei moduli di dati di esempio è il seguente:

* `magento/module-bundle-sample-data`
* `magento/module-catalog-rule-sample-data`
* `magento/module-catalog-sample-data`
* `magento/module-cms-sample-data`
* `magento/module-configurable-sample-data`
* `magento/module-customer-sample-data`
* `magento/module-downloadable-sample-data`
* `magento/module-grouped-product-sample-data`
* `magento/module-msrp-sample-data`
* `magento/module-offline-shipping-sample-data`
* `magento/module-product-links-sample-data`
* `magento/module-review-sample-data`
* `magento/module-sales-rule-sample-data`
* `magento/module-sales-sample-data`
* `magento/module-sample-data`
* `magento/module-swatches-sample-data`
* `magento/module-tax-sample-data`
* `magento/module-theme-sample-data`
* `magento/module-widget-sample-data`
* `magento/module-wishlist-sample-data`
* `magento/sample-data-media`

## Preparare l’aggiornamento dei dati di esempio

Questo comando consente di aggiornare i dati di esempio prima di aggiornare Adobe Commerce o Magento Open Source.

Per preparare i dati di esempio per l&#39;aggiornamento, immettere il comando seguente:

```bash
bin/magento sampledata:reset
```

Dopo, [aggiornare l’applicazione](../tutorials/uninstall.md#update-the-application).
