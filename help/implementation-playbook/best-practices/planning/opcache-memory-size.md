---
title: Procedure consigliate per la dimensione della memoria OPcache
description: Descrive come evitare il degrado delle prestazioni mediante impostazioni specifiche di consumo di memoria OPcache nei progetti Adobe Commerce.
role: Developer
feature: Best Practices
exl-id: d1e10068-e4e8-4e75-9f30-f3a89a08d791
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '159'
ht-degree: 1%
---
# Procedure consigliate per la dimensione della memoria OPcache in Adobe Commerce

Per Adobe Commerce on Cloud Infrastructure Pro plan Architecture 2.3.x, si consiglia di impostare `opcache.memory_consumption` su almeno 2 GB, per evitare il degrado delle prestazioni.

## Prodotti e versioni interessati

* Adobe Commerce su infrastruttura cloud Architettura del piano Pro 2.3.x
* PHP 7.0 e versioni successive

## Configurare la memoria

Allocare almeno **2 GB** di memoria per il modulo PHP [OPcache](https://www.php.net/manual/en/book.opcache.php). Modulo OPcache configurato nel file `php.ini`. Per allocare 2048 MB di memoria, impostare `opcache.memory_consumption = 2048`.

## Informazioni aggiuntive

* [Best practice per le prestazioni - Impostazioni PHP](../../../performance/software.md#php-settings)
* [Configurare le opzioni PHP](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/configure/app/configure-app-yaml)
* [Best practice per il database di Adobe Commerce sull’infrastruttura cloud](database-on-cloud.md)
* [Problemi di database più comuni in Adobe Commerce sull’infrastruttura cloud](../maintenance/resolve-database-performance-issues.md)
* [Gli indicizzatori &quot;Update On Schedule&quot; ottimizzano le prestazioni di Adobe Commerce](../maintenance/indexer-configuration.md)
