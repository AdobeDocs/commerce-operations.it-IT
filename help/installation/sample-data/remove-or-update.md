---
title: Rimuovi o aggiorna i moduli dati di esempio
description: Per gestire i moduli dati di esempio di Adobe Commerce, segui la procedura riportata di seguito.
exl-id: d23f999f-18bf-449b-be23-bdf392dda539
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '107'
ht-degree: 0%

---

# Rimuovi o aggiorna i moduli dati di esempio

In questo argomento viene illustrato come:

* [Rimuovere i moduli dati di esempio](#remove-sample-data-modules) da un&#39;installazione di Adobe Commerce `composer.json`. Questa opzione *non* rimuove i dati di esempio dal database.

* [Preparare l&#39;aggiornamento dei dati di esempio](#prepare-to-update-sample-data) (ad esempio, prima di aggiornare l&#39;applicazione Magento).

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

Questo comando consente di aggiornare i dati di esempio prima di aggiornare Adobe Commerce.

Per preparare i dati di esempio per l&#39;aggiornamento, immettere il comando seguente:

```bash
bin/magento sampledata:reset
```

Dopodiché, [aggiorna l&#39;applicazione](../tutorials/uninstall.md#update-the-application).
