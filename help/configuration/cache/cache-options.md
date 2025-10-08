---
title: Opzioni cache
description: Scopri le opzioni di cache di basso livello e la configurazione dello storage in Adobe Commerce. Scopri la configurazione front-end, back-end e di storage per Redis e database.
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '112'
ht-degree: 0%

---

# Opzioni cache di basso livello

L’applicazione Commerce utilizza una cache di basso livello front-end e back-end per fornire accesso all’archiviazione della cache.

## Cache front-end di basso livello

Commerce estende [Zend_Cache_Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) implementando [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) cache front-end.

## Cache back-end di basso livello

In generale, l&#39;applicazione Commerce funziona con qualsiasi cache back-end supportata da [Zend_Cache Backends](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html). Tuttavia, questa guida tratta solo le seguenti cache di back-end di basso livello:

- [Redis](config-redis.md)
- [Database](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
- File system (predefinito): non è necessaria alcuna configurazione per utilizzare il caching del file system.

[Varnish](config-varnish.md) non richiede la configurazione di un back-end di cache di basso livello.
