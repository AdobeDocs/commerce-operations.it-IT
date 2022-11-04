---
title: Best practice per il carrello dei prodotti
description: Scopri come ottimizzare le prestazioni di Adobe Commerce limitando il numero di prodotti nel carrello.
role: User
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Best practice per la gestione del carrello dei prodotti

Per ottenere le migliori prestazioni, utilizza le seguenti linee guida per gestire i limiti del carrello per Adobe Commerce e Magenti Open Source:

- Per le versioni 2.3.x - 2.4.2, consenti un massimo di 100 prodotti in un carrello.
- Per le versioni 2.4.3 e successive, il miglioramento delle funzionalità delle regole di vendita ha aumentato il massimo del carrello a 750.


Per le versioni da 2.3.x a 2.4.2, le prestazioni previste in base ai limiti degli articoli del carrello sono le seguenti:

- Fino a **100** prodotti in un carrello: il prodotto funziona e soddisfa gli obiettivi prestazionali per il tempo di risposta.
- Fino a **300** prodotti in un carrello: il prodotto funziona, ma il tempo di risposta aumenta al di sopra degli obiettivi.
- Sopra **500** prodotti in un carrello: i flussi del carrello e dei pagamenti non sono garantiti per funzionare

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce su infrastruttura cloud
- Adobe Commerce on-premise

## Riduzione del numero di elementi del carrello

Utilizza le seguenti strategie per gestire il numero di elementi del carrello

- Dividi gli ordini in più ordini più piccoli con un numero inferiore di righe utilizzando il [!UICONTROL Add Item by SKU] funzionalità.
- Aggiungi solo la logica personalizzata e la personalizzazione del carrello necessaria per caricare un elenco di elementi.

## Effetti potenziali sulle prestazioni

Avere più del numero massimo consigliato di prodotti nel carrello può influenzare le prestazioni del sito nei seguenti modi:

- Maggiore tempo di risposta per le operazioni di recupero dati, convalida degli articoli del carrello, controlli per l&#39;applicazione delle regole di prezzo e calcoli delle imposte e dei totali.
- Maggiore tempo di risposta per il rendering minicart, tra cui il rendering di viste del carrello, il flusso di cassa e l’esecuzione.
- Tempo di caricamento aumentato per tutte le pagine del sito in cui è presente il minicart.

## Informazioni aggiuntive

- [Configurare le opzioni di prodotto](https://experienceleague.adobe.com/docs/commerce-admin/inventory/configuration/product-options.html)
- [Gestire un carrello](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/point-of-purchase/assist/shopping-assisted-cart-manage.html)
