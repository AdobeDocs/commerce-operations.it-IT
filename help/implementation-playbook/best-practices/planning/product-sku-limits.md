---
title: Best practice per i limiti di prodotto
description: Scopri le best practice per configurare le SKU (Stock Keeping Unit) del prodotto per massimizzare le prestazioni del sito.
role: Admin
feature: Best Practices, Catalogs
exl-id: 37af7b92-05ac-4a4f-9009-11e8d9f95c2f
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 0%

---

# Best practice per la configurazione SKU del prodotto

Per massimizzare le prestazioni, il valore massimo consigliato per le SKU (Stock Keeping Unit) del prodotto è 242 milioni. Questo SKU prodotto effettivo massimo è calcolato come:

```text
Effective SKU = N[SKUs] x N[Stores] x N[Customer groups]
```

Dove:

- N sta per il numero di elementi per quella categoria
- I gruppi di clienti includono cataloghi condivisi, in quanto creano un gruppo di clienti aggiuntivo.

Avere un numero di SKU superiore al massimo consentito rallenta il recupero dei dati dei prodotti e aumenta il tempo necessario per completare le operazioni o le indicizzazioni del pannello di amministrazione.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

## Ridurre il numero di prodotti

Per ridurre il numero di prodotti (SKU), utilizza le seguenti strategie:

- Riduci al minimo i moltiplicatori:
   - Il consolidamento dei siti web riduce il moltiplicatore. Se disponi di 50.000 SKU, dieci siti Web e dieci gruppi di clienti, il numero effettivo di SKU è 5 milioni. La rimozione di cinque gruppi di clienti riduce le SKU effettive a 2,5 milioni.
   - Utilizza funzioni di prodotto alternative per i prezzi personalizzati al posto dei moltiplicatori di cataloghi e gruppi di clienti condivisi.
   - Sia i gruppi di clienti che il catalogo condiviso fungono da moltiplicatori per il numero di SKU effettivi in un negozio.
- Ristrutturare il catalogo:
   - Riduci il numero di prodotti assegnati alle categorie.
   - Diminuisci il numero di SKU diminuendo il numero di siti web, gruppi di clienti, cataloghi condivisi, numero di prodotti o numero di opzioni di prodotto configurabili
- Puoi fornire più varianti di prodotto utilizzando opzioni personalizzate anziché creare prodotti separati.
- Tenendo conto del fatto che una SKU effettiva potrebbe includere una serie di potenziali permutazioni dei prezzi, poiché i prezzi possono essere specificati in modo diverso per ogni negozio o gruppo di clienti.
- Disattiva o rimuovi i componenti di sistema inutilizzati come i moduli. (vedere  [Disinstalla moduli](../../../installation/tutorials/uninstall-modules.md).)
- Gestione dei prodotti in un sistema di gestione della piattaforma (PMS) esterno.

## Informazioni aggiuntive

- [Creare un prodotto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Assegnazioni prodotti](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- [Utilizzo dei cataloghi condivisi](https://experienceleague.adobe.com/docs/commerce-admin/b2b/shared-catalogs/catalog-shared.html)
- Infrastruttura cloud: [Configurare più siti Web e store](https://devdocs.magento.com/cloud/project/project-multi-sites.html)
- Locale: [Più siti Web o store](../../../configuration/multi-sites/ms-overview.md)
- [Adobe Commerce sull’infrastruttura cloud: best practice per la configurazione dello store](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
