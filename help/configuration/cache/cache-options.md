---
title: Opzioni di back-end cache e riferimento archiviazione
description: Scopri le opzioni di back-end della cache in Adobe Commerce, tra cui file system, Redis, Valkey e archiviazione del database. Scopri approcci legacy e moderni.
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
source-git-commit: 9cd0f2a84772e2d68fd15a00651216abfa9ec91c
workflow-type: tm+mt
source-wordcount: '300'
ht-degree: 0%

---

# Opzioni di back-end della cache e riferimento archiviazione

L’applicazione Commerce utilizza una cache di basso livello front-end e back-end per fornire accesso allo storage della cache. Commerce supporta diversi back-end e strategie di caching, ciascuno adatto a casi d’uso diversi. Questa pagina descrive i backend disponibili e le loro differenze.

>[!NOTE]
>
>Per informazioni dettagliate sulla configurazione della cache front-end, vedere [Configurare i front-end della cache](cache-types.md).

## Opzioni cache back-end

Nella tabella seguente sono riepilogate le cache back-end disponibili:

| Back-end | Descrizione | Guida alla configurazione |
| ------- | ----------- | ------------------- |
| File system | Impostazione predefinita. Memorizza i dati della cache nei file in `var/cache/`. Nessuna configurazione richiesta. | N/D |
| [Redis](config-redis.md) | Archivio dati in memoria per il caching ad alte prestazioni. | [Usa Redis per la cache predefinita](redis-pg-cache.md) |
| [Chiave Valvola](config-valkey.md) | Alternativa open-source compatibile con Redis. | [Usa Valkey per la cache predefinita](valkey-pg-cache.md) |
| [Database](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/) | Memorizzazione in cache con database. | [Creare motori di cache personalizzati](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/){target="_blank"} (documentazione per gli sviluppatori di Adobe) |

>[!NOTE]
>
>[Varnish](config-varnish.md) gestisce il caching di pagine intere a livello HTTP e non utilizza il backend di cache di basso livello.

## Approcci di implementazione

Commerce supporta due approcci di implementazione back-end. L’approccio scelto dipende dalla versione di Commerce in uso:

>[!BEGINTABS]

>[!TAB Cache legacy basata su Zend (2.4.8 e versioni precedenti)]

Utilizza nomi di classi completi per la configurazione back-end:

| Back-end | Nome classe |
| ------- | ---------- |
| Redis | `Magento\Framework\Cache\Backend\Redis` |
| Valkey | `Magento\Framework\Cache\Backend\Valkey` |

Compatibili con l&#39;interfaccia `Zend_Cache_Backend`.

**Configurazione di esempio:**

```php?start_inline=1
'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
'backend_options' => [
    'server' => '127.0.0.1',
    'database' => '0',
    'port' => '6379',
],
```

>[!TAB Cache Symfony moderna (versione 2.4.9 e successive, consigliata)]

>[!TIP]
>
>La moderna implementazione della cache di Symfony offre prestazioni migliori grazie alla conformità PSR-6, alla serializzazione Igbinary, alla compressione Gzip, agli script Lua e alle connessioni persistenti.

Utilizza i nomi dei tipi di back-end semplificati:

| Back-end | Digita il nome |
| ------- | --------- |
| Redis | `redis` |
| Valkey | `valkey` |
| File system | `file` |

**Configurazione di esempio:**

```php?start_inline=1
'backend' => 'redis',
'backend_options' => [
    'server' => '127.0.0.1',
    'database' => '0',
    'port' => '6379',
    'serializer' => 'igbinary',
    'compression_lib' => 'gzip',
],
```

>[!ENDTABS]

Per le opzioni di configurazione complete, vedi:

- [Usa Redis per la cache predefinita](redis-pg-cache.md)
- [Usa Valkey per la cache predefinita](valkey-pg-cache.md)
- [Configurazione cache L2](level-two-cache.md)

Consulta la [documentazione Laminas](https://docs.laminas.dev/) per informazioni sulle opzioni legacy basate su Zend.
