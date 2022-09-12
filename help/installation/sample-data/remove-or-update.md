---
title: Rimuovere o aggiornare moduli di dati di esempio
description: Segui questi passaggi per gestire moduli di dati di esempio Adobe Commerce e Magenti Open Source.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---


# Rimuovere o aggiornare moduli di dati di esempio

Questo argomento illustra come:

* [Rimuovere i moduli di dati di esempio](#remove-sample-data-modules) da un’installazione Adobe Commerce o Magenti Open Source `composer.json`. Questa opzione *not* rimuovere dati di esempio dal database.

* [Preparare l’aggiornamento dei dati di esempio](#prepare-to-update-sample-data) (ad esempio, prima di aggiornare l&#39;applicazione Magento).

## Rimuovere i moduli di dati di esempio

Immetti il seguente comando:

```bash
bin/magento sampledata:remove
```

L’elenco completo dei moduli di dati campione è il seguente:

Adobe Commerce e Magento Open Source:

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

Solo Adobe Commerce:

* `magento/module-customer-balance-sample-data`
* `magento/module-gift-card-sample-data`
* `magento/module-gift-registry-sample-data`
* `magento/module-multiple-wishlist-sample-data`
* `magento/module-target-rule-sample-data`

## Preparare l’aggiornamento dei dati di esempio

Questo comando consente di aggiornare i dati di esempio prima di aggiornare Adobe Commerce o Magenti Open Source.

Per preparare i dati di esempio da aggiornare, immettere il comando seguente:

```bash
bin/magento sampledata:reset
```

Dopo questo, [aggiornare l&#39;applicazione](../tutorials/uninstall.md#update-the-application).
