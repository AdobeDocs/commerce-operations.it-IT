---
title: Opzioni cache
description: Configura l'accesso allo storage cache di basso livello.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# Opzioni cache a basso livello

L’applicazione Commerce utilizza un front-end cache e un backend a basso livello per fornire accesso allo storage della cache.

## Cache front-end a basso livello

Estensione Commerce [Zend_Cache_Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) mediante [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) cache front-end.

## Cache back-end a basso livello

In generale, l’applicazione Commerce funziona con qualsiasi cache di backend che [Backend Zend_Cache](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html) supporta. Tuttavia, questa guida copre solo le seguenti cache back-end di basso livello:

- [Redis](config-redis.md)
- [Database](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
- File system (predefinito): Non è necessaria alcuna configurazione per utilizzare la memorizzazione in cache del file system.

[Vernice](config-varnish.md) non richiede la configurazione di un back-end cache di basso livello.
