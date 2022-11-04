---
title: Best practice di configurazione per le varianti di prodotto
description: Scopri come ottimizzare le prestazioni di Adobe Commerce limitando il numero di varianti di prodotto configurate.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Procedure consigliate per la configurazione delle varianti di prodotto

Per ottenere le migliori prestazioni, configura un massimo di 50 varianti per prodotto.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce su infrastruttura cloud
- Adobe Commerce on-premise

## Ridurre il numero di varianti di prodotto

Per migliorare le prestazioni del sito, utilizza le seguenti strategie per ridurre il numero di varianti di prodotto:

- Ristrutturare il catalogo distribuendo il numero di varianti tra prodotti diversi.
- Rimuovi le opzioni di attributi configurabili non disponibili.
- Gestisci le varianti tramite funzioni alternative quali opzioni personalizzate, categorie, prodotti correlati, raggruppati e raggruppati.

## Impatto potenziale sulle prestazioni

Il superamento del numero consigliato di varianti di prodotto può influire sulle prestazioni del sito nei seguenti modi:

- Tempi di richiesta e rendering lunghi per i dettagli dei prodotti e le pagine delle categorie contenenti prodotti complessi.
- È stato aumentato il tempo di risposta per completare le operazioni di salvataggio nell’amministratore.
- Maggiore tempo per eseguire il rendering del modulo di modifica del prodotto.
- Pagamento lento.

## Informazioni aggiuntive

- [Creare prodotti configurabili](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-configurable.html)
- [Creare un prodotto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)

- Formazione[Gestire cataloghi e prodotti con Adobe Commerce](https://learning.adobe.com/catalog/adobe_commerce/cours000000000098643.html)
