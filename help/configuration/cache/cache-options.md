---
title: Opzioni cache
description: Configurare l'accesso allo storage della cache di basso livello.
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# Opzioni cache di basso livello

L’applicazione Commerce utilizza una cache di basso livello front-end e back-end per fornire accesso all’archiviazione della cache.

## Cache front-end di basso livello

Estensioni Commerce [Zend_Cache_Core](https://framework.zend.com/manual/1.12/en/zend.cache.frontends.html) implementando [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) cache front-end.

## Cache back-end di basso livello

In generale, l’applicazione Commerce funziona con qualsiasi cache back-end che [Backend Zend_Cache](https://framework.zend.com/manual/1.12/en/zend.cache.backends.html) supporta. Tuttavia, questa guida tratta solo le seguenti cache di back-end di basso livello:

- [Redis](config-redis.md)
- [Database](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/)
- File system (predefinito): non è necessaria alcuna configurazione per utilizzare il caching del file system.

[Vernice](config-varnish.md) non richiede la configurazione di un back-end della cache di basso livello.
