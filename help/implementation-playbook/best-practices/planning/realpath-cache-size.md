---
title: Dimensioni cache realpath
description: Scopri come ottimizzare le prestazioni di Adobe Commerce aggiornando la configurazione della cache readpath di PHP per utilizzare le impostazioni consigliate.
role: Developer
feature: Best Practices, Cache
exl-id: 1cd48155-5d60-48b2-b07b-9b5784b81681
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '182'
ht-degree: 1%

---

# Best practice per la configurazione della cache Realpath

La cache Realpath memorizza nella cache i percorsi effettivi dei file system dei nomi di file a cui si fa riferimento, invece di cercarli ogni volta. Ogni volta che vengono eseguite varie funzioni di file o che richiedono un file e utilizzano un percorso relativo, PHP deve cercare dove esiste realmente quel file.

Per migliorare le prestazioni di Commerce, utilizzare le seguenti impostazioni consigliate per configurare le impostazioni `realpath_cache` nel file `php.ini`:

- Imposta la dimensione della cache su 10 MB (`realpath cache_size=10M`)
- Imposta durata (ttl) su 7200 secondi (`realpath_cache_ttl=7200`)

Per istruzioni di configurazione, vedere [Come impostare le opzioni PHP](../../../installation/prerequisites/php-settings.md#how-to-set-php-options).

## Prodotti e versioni interessati

- Adobe Commerce on-premise, tutte le versioni 2.3.x e successive
- Adobe Commerce su infrastruttura cloud, tutte le versioni 2.3.x e successive

## Potenziale impatto sulle prestazioni

Se i valori di configurazione della cache Realpath sono troppo bassi o troppo alti, viene aggiunto un sovraccarico aggiuntivo durante la generazione della cache che rallenta le prestazioni.

## Informazioni aggiuntive

- [On-premise: impostazioni PHP](../../../performance/software.md#php-settings)
- Infrastruttura cloud:
   - [Best practice per il database](database-on-cloud.md)
   - [Problemi di database più comuni nel Magento Commerce Cloud](../maintenance/resolve-database-performance-issues.md)
- [Gli indicizzatori &quot;Update On Schedule&quot; ottimizzano le prestazioni del Magento](../maintenance/indexer-configuration.md)
