---
title: Best practice sui limiti di prodotto
description: Scopri le best practice per configurare le unità SKU (Stock Keeping Unit) del prodotto per massimizzare le prestazioni del sito.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Best practice per la configurazione SKU del prodotto

Per massimizzare le prestazioni, il valore massimo consigliato per unità di conservazione dei prodotti (SKU) efficaci è di 10 milioni. Il valore massimo effettivo del prodotto è calcolato come segue:

`Effective SKU = N\[SKUs\] * Stores/Websites * Customer Groups`

Una quantità superiore al numero massimo di SKU effettivi rallenta il recupero dei dati di prodotto e aumenta il tempo necessario per completare le operazioni di amministrazione.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce su infrastruttura cloud
- Adobe Commerce on-premise

## Riduzione del numero di prodotti

Utilizza le seguenti strategie per ridurre il numero di prodotti (SKU):

- Ridurre al minimo i moltiplicatori
   - Lo spostamento di negozi o siti web riduce il moltiplicatore. Se disponi di 50.000 SKU, dieci siti web e dieci gruppi di clienti, il numero effettivo di SKU è di 5 milioni. La rimozione di cinque gruppi di clienti riduce gli SKU effettivi a 2,5 milioni.
   - Utilizza funzionalità di prodotto alternative per i prezzi personalizzati per sostituire i moltiplicatori di catalogo e gruppi di clienti condivisi.
- Ristrutturare il catalogo —
   - Ridurre il numero di prodotti assegnati alle categorie.
   - Diminuisce il numero di SKU diminuendo il numero di negozi, siti web, gruppi di clienti o il numero di prodotti.
- Fornisci più varianti di prodotto utilizzando opzioni personalizzate invece di creare prodotti separati.
- Disattivare o rimuovere i componenti di sistema inutilizzati, come i moduli. (Vedi  [Disinstallare i moduli](../../../installation/tutorials/uninstall-modules.md).)
- Gestire i prodotti in un sistema di gestione della piattaforma esterno (PMS).

## Informazioni aggiuntive

- [Creare un prodotto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Assegnazione dei prodotti](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- Infrastruttura cloud: [Configurazione di più siti web e negozi](https://devdocs.magento.com/cloud/project/project-multi-sites.html)
- Presso i locali: [Più siti web o negozi](../../../configuration/multi-sites/ms-overview.md)
- [Adobe Commerce sull’infrastruttura cloud: Best practice per la configurazione dell’archivio](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
