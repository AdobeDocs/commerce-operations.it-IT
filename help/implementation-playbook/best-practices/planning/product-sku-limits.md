---
title: Best practice sui limiti di prodotto
description: Scopri le best practice per configurare le unità SKU (Stock Keeping Unit) del prodotto per massimizzare le prestazioni del sito.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: e259f9b999566447469200c93db3bc4ba06434c0
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---


# Best practice per la configurazione SKU del prodotto

Per massimizzare le prestazioni, il valore massimo consigliato per unità di conservazione dei prodotti (SKU) efficaci è di 242 milioni. Il valore massimo SKU del prodotto effettivo è calcolato come segue:

```text
Effective SKU = N[SKUs] x N[Stores] x N[Customer groups]
```

Dove:

- N indica il numero di elementi per la categoria
- I gruppi di clienti includono cataloghi condivisi, in quanto crea un gruppo di clienti aggiuntivo.

Una quantità superiore al numero massimo di SKU effettivi rallenta il recupero dei dati di prodotto e aumenta il tempo necessario per completare le operazioni o le indicizzazione del pannello Amministratore.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce su infrastruttura cloud
- Adobe Commerce on-premise

## Riduzione del numero di prodotti

Utilizza le seguenti strategie per ridurre il numero di prodotti (SKU):

- Ridurre al minimo i moltiplicatori
   - Il consolidamento dei siti web riduce il moltiplicatore. Se disponi di 50.000 SKU, dieci siti web e dieci gruppi di clienti, il numero effettivo di SKU è di 5 milioni. La rimozione di cinque gruppi di clienti riduce gli SKU effettivi a 2,5 milioni.
   - Utilizza funzionalità di prodotto alternative per i prezzi personalizzati per sostituire i moltiplicatori di catalogo e gruppi di clienti condivisi.
   - I gruppi di clienti e il catalogo condiviso funzionano come moltiplicatori per il numero di SKU efficaci in un negozio.
- Ristrutturare il catalogo —
   - Ridurre il numero di prodotti assegnati alle categorie.
   - Diminuisce il numero di SKU diminuendo il numero di siti web, gruppi di clienti, cataloghi condivisi, numero di prodotti o numero di opzioni di prodotto configurabili
- Fornisci più varianti di prodotto utilizzando opzioni personalizzate invece di creare prodotti separati.
- Tenendo conto del fatto che una SKU efficace potrebbe includere una serie di potenziali permutazioni dei prezzi, in quanto i prezzi possono essere specificati in modo diverso per ogni negozio o gruppo di clienti.
- Disattivare o rimuovere i componenti di sistema inutilizzati, come i moduli. (Vedi  [Disinstallare i moduli](../../../installation/tutorials/uninstall-modules.md).)
- Gestire i prodotti in un sistema di gestione della piattaforma esterno (PMS).

## Informazioni aggiuntive

- [Creare un prodotto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Assegnazione dei prodotti](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- [Utilizzo dei cataloghi condivisi](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared.html)
- Infrastruttura cloud: [Configurazione di più siti web e negozi](https://devdocs.magento.com/cloud/project/project-multi-sites.html)
- Presso i locali: [Più siti web o negozi](../../../configuration/multi-sites/ms-overview.md)
- [Adobe Commerce sull’infrastruttura cloud: Best practice per la configurazione dell’archivio](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
