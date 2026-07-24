---
title: Opzioni di back-end cache e riferimento archiviazione
description: Scopri le opzioni di back-end della cache in Adobe Commerce, tra cui file system, Redis, Valkey e archiviazione del database. Scopri approcci legacy e moderni.
feature: Configuration, Cache
exl-id: e0330108-5c55-4a33-9f93-63fbb71af761
badgePaas: label="On-Premises" type="Informative" url="https://experienceleague.adobe.com/it/docs/commerce/user-guides/product-solutions" tooltip="Applicabile solo ai progetti locali di Adobe Commerce."
autotag-review: '2026-06-22T18:37:32.504Z'
TQID: 'https://experienceleague.adobe.com/m7eUBNrt8UF43iJq9Tpl0Y1WcmR-dlt7Z4PoHvXVNnA'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: d9152906a6fbbd765a60e3aeacdbf7cc7527529d
workflow-type: tm+mt
source-wordcount: 331
ht-degree: 0%

---

# Opzioni di back-end della cache e riferimento archiviazione

{{cloud-cache-config}}

L’applicazione Commerce utilizza una cache di basso livello front-end e back-end per fornire accesso allo storage della cache. Commerce supporta diversi back-end e strategie di caching, ciascuno adatto a casi d’uso diversi. Questa pagina descrive i backend disponibili e le loro differenze.

>[!NOTE]
>
>[Varnish](config-varnish.md) gestisce il caching di pagine intere a livello HTTP e non utilizza il backend di cache di basso livello.

## Opzioni cache back-end

Nella tabella seguente sono riepilogate le cache back-end disponibili:

| Back-end | Descrizione | Guida alla configurazione |
| ------- | ----------- | ------------------- |
| File system | Impostazione predefinita. Memorizza i dati della cache nei file in `var/cache/`. Nessuna configurazione richiesta. | N/D |
| [Redis](config-redis.md) | Archivio dati in memoria per il caching ad alte prestazioni. | [Usa Redis per la cache predefinita](redis-pg-cache.md) |
| [Chiave Valvola](config-valkey.md) | Alternativa open-source compatibile con Redis. | [Usa Valkey per la cache predefinita](valkey-pg-cache.md) |
| [Database](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/) | Memorizzazione in cache con database. | [Creare motori di cache personalizzati](https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/){target="_blank"} (documentazione per gli sviluppatori di Adobe) |

>[!IMPORTANT]
>
>{{redis-cache-support}}

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
| Valkey | `valkey` |
| File system | `file` |

>[!NOTE]
>
>Anche il nome del tipo `redis` è accettato, ma Redis non è un servizio cache ufficialmente supportato per Adobe Commerce 2.4.9 e versioni successive. Utilizza invece `valkey`.

**Configurazione di esempio:**

```php?start_inline=1
'backend' => 'valkey',
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

