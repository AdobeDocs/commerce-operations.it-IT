---
title: Pianificazione degli aggiornamenti dell’amministratore nei siti di produzione
description: Scopri le best practice per la pianificazione di aggiornamenti critici per Adobe Commerce al fine di evitare rallentamenti delle prestazioni e interruzioni.
role: Admin, User
feature: Best Practices
exl-id: 41c0cb87-3371-48a7-9913-264f3eea8d8d
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '135'
ht-degree: 1%

---

# Best practice per la pianificazione degli aggiornamenti amministratore nei siti di produzione

Pianifica aggiornamenti e operazioni critici sui siti Adobe Commerce nelle ore di minore utilizzo per evitare rallentamenti delle prestazioni e interruzioni nei siti di produzione.

Esempi di azioni critiche:

- Modifiche alla configurazione di amministrazione, ad esempio aggiornamento di un attributo di prodotto o spostamento di una sottocategoria di prodotto in un’altra categoria
- Operazioni di importazione o esportazione dei dati

Le azioni critiche portano all’invalidamento della cache e alle operazioni di reindicizzazione che aumentano in modo significativo il tempo di risposta e possono causare interruzioni del sito.

## Prodotti e versioni interessati

[Tutte le versioni supportate](../../../release/versions.md) di:

- Adobe Commerce sull’infrastruttura cloud
- Adobe Commerce on-premise

## Informazioni aggiuntive

- [Procedure consigliate per la memorizzazione nella cache](https://docs.magento.com/user-guide/system/cache-management.html#best-practices-for-caching)
- [Contenuto privato: invalidare il contenuto privato](https://developer.adobe.com/commerce/php/development/cache/page/private-content/#invalidate-private-content)
- [Consigli hardware: cache](../../../performance/hardware.md#caches)
- [Configurazione avanzata: configurazione Redis](../../../performance/advanced-setup.md#set-up-redis)
