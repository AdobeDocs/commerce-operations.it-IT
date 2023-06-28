---
title: Best practice per la configurazione delle varianti di prodotto
description: Scopri come ottimizzare le prestazioni di Adobe Commerce limitando il numero di varianti di prodotto configurate.
role: Admin
feature: Best Practices, Catalogs
exl-id: a19dd8b4-23b8-498f-be51-a0adfcd12a11
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# Best practice per la configurazione delle varianti di prodotto

Per prestazioni ottimali, configura un massimo di 50 varianti per prodotto.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

## Ridurre il numero di varianti di prodotto

Per migliorare le prestazioni del sito, utilizza le seguenti strategie per ridurre il numero di varianti di prodotto:

- Ristruttura il catalogo distribuendo il numero di varianti tra i diversi prodotti.
- Rimuovere le opzioni di attributo configurabili non disponibili.
- Gestisci le varianti tramite funzionalità alternative come opzioni personalizzate, categorie, prodotti correlati, raggruppati e bundle.

## Potenziale impatto sulle prestazioni

Il superamento del numero consigliato di varianti di prodotto può influire sulle prestazioni del sito nei seguenti modi:

- Tempi lunghi di richiesta e rendering dei dettagli di prodotto e delle pagine di categorie contenenti prodotti complessi.
- È stato aumentato il tempo di risposta per completare le operazioni di salvataggio nell’amministratore.
- È stato aumentato il tempo per il rendering del modulo di modifica del prodotto.
- Pagamento lento.

## Informazioni aggiuntive

- [Creare prodotti configurabili](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/types/product-create-configurable.html)
- [Creare un prodotto](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)

- Formazione[Gestire cataloghi e prodotti con Adobe Commerce](https://learning.adobe.com/catalog/adobe_commerce/cours000000000098643.html)
