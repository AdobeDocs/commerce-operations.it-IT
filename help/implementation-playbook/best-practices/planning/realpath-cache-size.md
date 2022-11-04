---
title: Dimensione della cache del percorso reale
description: Scopri come ottimizzare le prestazioni di Adobe Commerce aggiornando la configurazione della cache del percorso di lettura PHP per utilizzare le impostazioni consigliate.
role: Developer
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Best practice per la configurazione della cache del percorso reale

La cache Realpath memorizza in cache i percorsi dei file system reali dei nomi dei file a cui si fa riferimento invece di cercare ogni volta. Ogni volta che varie funzioni di file vengono eseguite o richiedono un file e utilizzano un percorso relativo, PHP deve cercare dove quel file esiste veramente.

Per migliorare le prestazioni di Commerce, utilizza le seguenti impostazioni consigliate per configurare le `realpath_cache` nelle impostazioni `php.ini` file:

- Imposta la dimensione della cache su 10 MB (`realpath cache_size=10M`)
- Imposta il tempo di vita (ttl) a 7200 secondi (`realpath_cache_ttl=7200`)

Per le istruzioni di configurazione, consulta [Come impostare le opzioni PHP](../../../installation/prerequisites/php-settings.md#how-to-set-php-options).

## Prodotti e versioni interessati

- Adobe Commerce on-premise, tutte le versioni 2.3.x e successive
- Adobe Commerce sull’infrastruttura cloud, tutte le versioni 2.3.x e successive

## Impatto potenziale sulle prestazioni

Se i valori di configurazione della cache Realpath sono troppo bassi o troppo alti, aggiunge un sovraccarico aggiuntivo durante la generazione della cache che rallenta le prestazioni.

## Informazioni aggiuntive

- [Presso i locali: Impostazioni PHP](../../../performance/software.md#php-settings)
- Infrastruttura cloud:
   - [Best practice per i database](database-on-cloud.md)
   - [Problemi di database più comuni nel Magento Commerce Cloud](../maintenance/resolve-database-performance-issues.md)
- [Gli indicizzatori &quot;Aggiorna secondo programma&quot; ottimizzano le prestazioni del Magento](../maintenance/indexer-configuration.md)

