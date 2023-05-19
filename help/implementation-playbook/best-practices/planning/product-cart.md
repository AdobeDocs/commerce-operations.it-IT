---
title: Best practice per il carrello dei prodotti
description: Scopri come ottimizzare le prestazioni di Adobe Commerce limitando il numero di prodotti nel carrello.
role: User
feature: Best Practices
feature-set: Commerce
exl-id: 7ea5acc2-f6b2-4244-8c07-c71fd54a18a0
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Best practice per la gestione del carrello dei prodotti

Per ottenere prestazioni ottimali, utilizza le seguenti linee guida per gestire i limiti del carrello per Adobe Commerce e Magenti Open Source:

- Per le versioni 2.3.x - 2.4.2, consenti un massimo di 100 prodotti in un carrello.
- Per le versioni 2.4.3 e successive, il miglioramento delle funzionalità delle regole di vendita ha aumentato il carrello a un massimo di 750.


Per le versioni 2.3.x - 2.4.2, le prestazioni previste in base ai limiti degli articoli del carrello sono:

- Fino a **100** prodotti in un carrello: il prodotto funziona, rispettando gli obiettivi prestazionali per i tempi di risposta.
- Fino a **300** prodotti in un carrello: il prodotto funziona, ma i tempi di risposta aumentano al di sopra degli obiettivi.
- Sopra **500** prodotti in un carrello: il carrello e i flussi di pagamento non sono garantiti

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

## Riduci il numero di elementi nel carrello

Utilizza le seguenti strategie per gestire il numero di articoli del carrello

- Dividi gli ordini in diversi ordini più piccoli con un numero inferiore di righe utilizzando [!UICONTROL Add Item by SKU] funzionalità.
- Aggiungi solo la logica personalizzata e la personalizzazione del carrello richieste per caricare un elenco di elementi.

## Potenziali impatti sulle prestazioni

Avere nel carrello un numero di prodotti superiore al numero massimo consigliato può influire sulle prestazioni del sito nei seguenti modi:

- Tempi di risposta più rapidi per le operazioni di recupero dei dati, convalida degli articoli del carrello, verifica dell&#39;applicazione delle regole di prezzo e calcoli delle imposte e dei totali.
- È stato aumentato il tempo di risposta per il rendering di minicart, incluso il rendering delle visualizzazioni del carrello, il flusso di pagamento e l’esecuzione.
- Tempo di caricamento aumentato per tutte le pagine del sito in cui è presente il minicart.

## Informazioni aggiuntive

- [Configurare le opzioni di prodotto](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-options.html)
- [Gestire un carrello](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/shopping-assisted-cart-manage.html)
