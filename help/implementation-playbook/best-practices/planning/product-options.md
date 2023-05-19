---
title: Best practice per la configurazione delle opzioni di prodotto
description: Ottimizza le prestazioni di Adobe Commerce limitando il numero di opzioni di prodotto.
role: Admin
feature: Best Practices
feature-set: Commerce
exl-id: 7571a163-798a-40be-b26f-4a184bceb809
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Best practice per le opzioni di prodotto

Per ottenere le migliori prestazioni, configura un massimo di 100 opzioni prodotto per prodotto.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

## Ridurre le opzioni di prodotto

Per ottenere le migliori prestazioni del sito, utilizza le seguenti strategie per ridurre il numero di opzioni di prodotto:

- Configura prodotti complessi e opzioni personalizzate come origine di varianti di prodotto.
- Invece di creare modelli di prodotto globali e contenitori di opzioni applicabili a tutti i prodotti, utilizza i set di attributi per creare modelli di prodotto specifici con attributi e opzioni di destinazione.
- Gestire le informazioni sui prodotti tramite un sistema di gestione dei prodotti (PMS) esterno.

## Potenziale impatto sulle prestazioni

La configurazione di molte opzioni di prodotto aumenta la quantità di dati recuperati per ciascun prodotto su tutte le operazioni di lettura e scrittura, con conseguente:

- Traffico di query SQL aumentato e maggiore `JOIN` le operazioni aumentano la velocità effettiva del database.
- Sono state aumentate le dimensioni per gli indici Adobe Commerce e l’indice di ricerca full-text.

Gli aumenti elencati sopra possono influire sulle prestazioni del sito nei seguenti modi:

- Tempi di risposta più lunghi per la maggior parte degli scenari di vetrina relativi a prodotti contenenti molte opzioni negli attributi.
- Aumenti significativi del tempo necessario per completare le operazioni di gestione dei prodotti in Admin che possono causare timeout, in particolare per scenari relativi all’elenco degli attributi e al recupero della struttura, inclusa la gestione delle regole di promozione.
- Può bloccare azioni in blocco che completano operazioni di massa asincrone come l’importazione e l’esportazione e assegnare prezzi personalizzati a più prodotti in un catalogo condiviso.

## Informazioni aggiuntive

- [Creare un prodotto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Best practice per la configurazione dell’attributo di prodotto](product-attributes-and-options.md)
- [Registro azioni in blocco](https://docs.magento.com/user-guide/system/action-log-bulk-actions.html)
- [API Azioni di massa inventario](https://developer.adobe.com/commerce/webapi/rest/inventory/bulk-inventory/)
- [Formazione: gestire cataloghi e prodotti tramite Adobe Commerce](https://learning.adobe.com/catalog/adobe_commerce/cours000000000098643.html)
