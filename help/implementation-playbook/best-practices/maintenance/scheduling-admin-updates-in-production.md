---
title: Pianificazione degli aggiornamenti dell'amministratore sui siti di produzione
description: Scopri le best practice per la pianificazione di aggiornamenti critici per Adobe Commerce al fine di evitare prestazioni e interruzioni lente.
role: Admin, User
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Best practice per la pianificazione degli aggiornamenti dell’amministratore sui siti di produzione

Pianifica aggiornamenti e operazioni critiche sui siti Adobe Commerce durante le ore di inattività per evitare prestazioni lente e interruzioni sui siti di produzione.

Esempi di azioni critiche:

- La configurazione dell’amministratore cambia, ad esempio aggiornando un attributo di prodotto o spostando una sottocategoria di prodotto in un’altra categoria
- Operazioni di importazione o esportazione dei dati

Le azioni critiche portano all’invalidazione della cache e alle operazioni di reindicizzazione che aumentano in modo significativo il tempo di risposta che può causare interruzioni del sito.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce su infrastruttura cloud
- Adobe Commerce on-premise

## Informazioni aggiuntive

- [Best practice per la memorizzazione in cache](https://docs.magento.com/user-guide/system/cache-management.html#best-practices-for-caching)
- [Contenuto privato: Annullare la validità del contenuto privato](https://developer.adobe.com/commerce/php/development/cache/page/private-content/#invalidate-private-content)
- [Raccomandazioni hardware: Cache](../../../performance/hardware.md#caches)
- [Configurazione avanzata: Imposta Redis](../../../performance/advanced-setup.md#set-up-redis)

