---
title: Procedure consigliate per la dimensione della memoria OPcache
description: Descrive come evitare il degrado delle prestazioni mediante impostazioni specifiche di consumo di memoria OPcache nei progetti Adobe Commerce.
role: Developer
feature: Best Practices
exl-id: d1e10068-e4e8-4e75-9f30-f3a89a08d791
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '138'
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
* [Configurare le opzioni PHP](https://devdocs.magento.com/cloud/project/project-conf-files_magento-app.html#customize-phpini-settings)
* [Best practice per il database di Adobe Commerce sull’infrastruttura cloud](database-on-cloud.md)
* [Problemi di database più comuni in Adobe Commerce sull’infrastruttura cloud](../maintenance/resolve-database-performance-issues.md)
* [Gli indicizzatori &quot;Update On Schedule&quot; ottimizzano le prestazioni di Adobe Commerce](../maintenance/indexer-configuration.md)
