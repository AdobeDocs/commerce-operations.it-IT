---
title: Best practice per la configurazione delle categorie
description: Scopri le best practice per massimizzare le prestazioni del sito limitando il numero di categorie nel catalogo.
role: Admin
feature: Best Practices
feature-set: Commerce
exl-id: c6834b32-9ee8-4a4a-932c-9726f3feee3f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---

# Best practice per la configurazione delle categorie

Per prestazioni ottimali, non configurare più del numero massimo di categorie consigliato per i siti Adobe Commerce.

- Per Adobe Commerce versione 2.4.2 e successive, configura un massimo di 6000 categorie
- Per Adobe Commerce versione 2.3.x e da 2.4.0 a 2.4.1-p1, configura un massimo di 3000 categorie

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

## Ridurre il numero di prodotti

Utilizza le seguenti strategie per ridurre il numero di categorie:

- Gestire funzioni univoche del prodotto tramite attributi e opzioni personalizzate
- Rimuovi categorie inattive
- Ottimizzare la profondità del catalogo nella navigazione

## Potenziali impatti sulle prestazioni

Un numero di categorie superiore al numero massimo consigliato può influire sulle prestazioni del sito nei seguenti modi:

- Aumento tangibile del tempo di risposta per le pagine di catalogo non memorizzate nella cache
- Esecuzione lunga e timeout durante la gestione delle categorie dall’amministratore
- Aumento delle dimensioni delle tabelle di database corrispondenti
- Tabelle indice più grandi aumentano il tempo necessario per completare le operazioni di indicizzazione per `[category/product relation index\]`
- Aumento del tempo di elaborazione per completare le operazioni di creazione della struttura delle categorie, recupero dei menu e gestione delle regole di categoria

## Informazioni aggiuntive

- [Panoramica sulle categorie](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/categories.html)
- [Panoramica sulla navigazione](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation.html)
- [Assegnazioni prodotti](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- [Adobe Commerce sull’infrastruttura cloud: best practice per la configurazione dello store](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
