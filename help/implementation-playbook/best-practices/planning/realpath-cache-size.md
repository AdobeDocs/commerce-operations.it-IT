---
title: Dimensioni cache realpath
description: Scopri come ottimizzare le prestazioni di Adobe Commerce aggiornando la configurazione della cache readpath di PHP per utilizzare le impostazioni consigliate.
role: Developer
feature: Best Practices, Cache
exl-id: 1cd48155-5d60-48b2-b07b-9b5784b81681
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: cdfd3bc1-dc23-5cf0-b965-d3c0c55cde67
    internal-label: Best Practices
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '187'
ht-degree: 1%
---
# Best practice per la configurazione della cache Realpath

La cache Realpath memorizza nella cache i percorsi effettivi dei file system dei nomi di file a cui si fa riferimento, invece di cercarli ogni volta. Ogni volta che vengono eseguite varie funzioni di file o che richiedono un file e utilizzano un percorso relativo, PHP deve cercare dove esiste realmente quel file.

Per migliorare le prestazioni di Commerce, utilizzare le seguenti impostazioni consigliate per configurare le impostazioni `realpath_cache` nel file `php.ini`:

- Imposta la dimensione della cache su 10 MB (`realpath_cache_size=10M`)
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
  - [Problemi più comuni relativi al database in Magento Commerce Cloud](../maintenance/resolve-database-performance-issues.md)
- [Gli indicizzatori &quot;Update On Schedule&quot; ottimizzano le prestazioni di Magento](../maintenance/indexer-configuration.md)
