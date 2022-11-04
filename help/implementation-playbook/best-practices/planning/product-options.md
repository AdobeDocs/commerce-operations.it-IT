---
title: Best practice per la configurazione delle opzioni di prodotto
description: Ottimizza le prestazioni di Adobe Commerce limitando il numero di opzioni di prodotto.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Best practice per le opzioni di prodotto

Per ottenere le migliori prestazioni, configura un massimo di 100 opzioni di prodotto per prodotto.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce su infrastruttura cloud
- Adobe Commerce on-premise

## Riduzione delle opzioni di prodotto

Per migliorare le prestazioni del sito, utilizza le seguenti strategie per ridurre il numero di opzioni di prodotto:

- Configura prodotti complessi e opzioni personalizzate come origine di varianti di prodotto.
- Invece di creare modelli di prodotto globali e contenitori di opzioni applicabili a tutti i prodotti, utilizza i set di attributi per creare modelli di prodotto specifici con attributi e opzioni di destinazione.
- Gestisci le informazioni sui prodotti tramite un sistema di gestione dei prodotti (PMS) esterno.

## Impatto potenziale sulle prestazioni

La configurazione di molte opzioni di prodotto aumenta la quantità di dati recuperati per ogni prodotto su tutte le operazioni di lettura e scrittura, con conseguente:

- Aumento del traffico della query SQL e maggiore carico `JOIN` le operazioni aumentano il throughput del database.
- È stata aumentata la dimensione degli indici Adobe Commerce e dell’indice di ricerca full-text.

Gli aumenti elencati sopra possono influire sulle prestazioni del sito nei seguenti modi:

- Tempo di risposta più lungo per la maggior parte degli scenari di vetrina relativi a prodotti che contengono molte opzioni negli attributi.
- Incremento significativo del tempo necessario per completare le operazioni di gestione dei prodotti in Admin, che può causare timeout, in particolare per gli scenari relativi all’elenco degli attributi e al recupero degli alberi, inclusa la gestione delle regole di promozione.
- Può bloccare azioni in blocco che completano operazioni di massa asincrone come l’importazione e l’esportazione e l’assegnazione di prezzi personalizzati a più prodotti in un catalogo condiviso.

## Informazioni aggiuntive

- [Creare un prodotto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Best practice per la configurazione degli attributi di prodotto](product-attributes-and-options.md)
- [Registro delle azioni in blocco](https://docs.magento.com/user-guide/system/action-log-bulk-actions.html)
- [API per le azioni di massa di inventario](https://developer.adobe.com/commerce/webapi/rest/inventory/bulk-inventory/)
- [Formazione: Gestire cataloghi e prodotti con Adobe Commerce](https://learning.adobe.com/catalog/adobe_commerce/cours000000000098643.html)

