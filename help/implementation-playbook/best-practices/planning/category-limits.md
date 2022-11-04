---
title: Best practice per la configurazione delle categorie
description: Scopri le best practice per massimizzare le prestazioni del sito limitando il numero di categorie nel catalogo.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: e156fcafc5792036b37d9b199b870f1888c3f1ff
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Best practice per la configurazione delle categorie

Per ottenere le migliori prestazioni, non configurare più del numero massimo consigliato di categorie per i siti Adobe Commerce.

- Per Adobe Commerce versione 2.4.2 e successive, configura un massimo di 6000 categorie
- Per Adobe Commerce versione 2.3.x e da 2.4.0 a 2.4.1-p1, configura un massimo di 3000 categorie

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce su infrastruttura cloud
- Adobe Commerce on-premise

## Riduzione del numero di prodotti

Utilizza le seguenti strategie per ridurre il numero di categorie:

- Gestione di funzionalità di prodotto uniche tramite attributi e opzioni personalizzate
- Rimuovere le categorie inattive
- Ottimizzare la profondità del catalogo nella navigazione

## Effetti potenziali sulle prestazioni

Avere più del numero massimo consigliato di categorie può influenzare le prestazioni del sito nei seguenti modi:

- Incremento tangibile del tempo di risposta per le pagine di catalogo non memorizzate nella cache
- Esecuzione e timeout lunghi durante la gestione delle categorie dall&#39;amministratore
- Aumento delle dimensioni delle tabelle di database corrispondenti
- Tabelle indice più grandi aumentano il tempo necessario per completare le operazioni di indicizzazione per `[category/product relation index\]`
- Maggiore tempo di elaborazione per completare le operazioni di creazione albero delle categorie, recupero menu e gestione delle regole di categoria

## Informazioni aggiuntive

- [Panoramica sulle categorie](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/categories.html)
- [Panoramica sulla navigazione](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/navigation/navigation.html)
- [Assegnazione dei prodotti](https://experienceleague.adobe.com/docs/commerce-admin/catalog/categories/products-in-category/categories-product-assignments.html)
- [Adobe Commerce sull’infrastruttura cloud: Best practice per la configurazione dell’archivio](https://devdocs.magento.com/cloud/configure/configure-best-practices.html)
