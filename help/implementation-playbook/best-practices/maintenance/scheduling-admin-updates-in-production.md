---
title: Pianificazione degli aggiornamenti dell’amministratore nei siti di produzione
description: Scopri le best practice per la pianificazione di aggiornamenti critici per Adobe Commerce al fine di evitare rallentamenti delle prestazioni e interruzioni.
role: Admin, User
feature: Best Practices
exl-id: 41c0cb87-3371-48a7-9913-264f3eea8d8d
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: b69b2659-1057-424e-8fc5-ed9e016dc554
    internal-label: User
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '161'
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

- [Best practice per il caching](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/cache-management#best-practices-for-caching)
- [Contenuto privato: annullare la validità del contenuto privato](https://developer.adobe.com/commerce/php/development/cache/page/private-content#invalidate-private-content)
- [Consigli hardware: cache](../../../performance/hardware.md#caches)
- [Configurazione avanzata: configurazione Redis](../../../performance/advanced-setup.md#set-up-redis)
