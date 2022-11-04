---
title: Best practice per le dimensioni della memoria OPcache
description: Descrive come evitare il deterioramento delle prestazioni da impostazioni specifiche del consumo di memoria OPcache sui progetti Adobe Commerce.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Procedure consigliate per le dimensioni della memoria OPcache in Adobe Commerce

Per Adobe Commerce sull&#39;infrastruttura cloud Pro, pianifica l&#39;architettura 2.3.x, si consiglia di impostare `opcache.memory_consumption` ad almeno 2 GB, per evitare la degradazione delle prestazioni.

## Prodotti e versioni interessati

* Architettura della pianificazione 2.3.x di Adobe Commerce su infrastruttura cloud Pro
* PHP 7.0 e versioni successive

## Configurare la memoria

Allocare almeno **2 GB** di memoria per [Modulo PHP OPcache](https://www.php.net/manual/en/book.opcache.php). Il modulo OPcache è configurato nel `php.ini` file. Per allocare 2048 MB di memoria, impostare `opcache.memory_consumption = 2048`.

## Informazioni aggiuntive

* [Best practice sulle prestazioni - Impostazioni PHP](../../../performance/software.md#php-settings)
* [Configurare le opzioni PHP](https://devdocs.magento.com/cloud/project/project-conf-files_magento-app.html#customize-phpini-settings)
* [Best practice per il database per Adobe Commerce sull’infrastruttura cloud](database-on-cloud.md)
* [Problemi più comuni relativi al database in Adobe Commerce su infrastruttura cloud](../maintenance/resolve-database-performance-issues.md)
* [Gli indicizzatori &quot;Aggiorna secondo programma&quot; ottimizzano le prestazioni di Adobe Commerce](../maintenance/indexer-configuration.md)
