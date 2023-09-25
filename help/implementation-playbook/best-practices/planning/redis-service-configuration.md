---
title: Best practice per la configurazione del servizio Redis
description: Scopri come migliorare le prestazioni di caching utilizzando l’implementazione della cache Redis estesa per Adobe Commerce.
role: Developer, Admin
feature: Best Practices, Cache
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: 156e6412b9f94b74bad040b698f466808b0360e3
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 0%

---

# Best practice per la configurazione del servizio Redis

- Configura cache L2 Redis
- Abilita connessione slave Redis
- Precarica chiavi
- Abilita cache non aggiornata
- Separare la cache Redis dalla sessione Redis
- Comprimere la cache Redis e utilizzare `gzip` per una compressione più elevata

## Configura cache L2 Redis

Configurare la cache di Redis L2 impostando `REDIS_BACKEND` variabile di distribuzione in `.magento.env.yaml` file di configurazione.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Per la configurazione dell’ambiente sull’infrastruttura cloud, consulta la sezione [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) nel _Guida di Commerce su infrastruttura cloud_.

Per gli impianti locali, cfr. [Configurare il caching delle pagine Redis](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) nel _Guida alla configurazione_.

>[!NOTE]
>
>Verifica di utilizzare la versione più recente di `ece-tools` pacchetto. In caso contrario, [aggiornamento alla versione più recente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html). Puoi controllare la versione installata nell’ambiente locale utilizzando `composer show magento/ece-tools` CLI.

## Abilita connessione slave Redis

Abilitare una connessione slave Redis in `.magento.env.yaml` file di configurazione per consentire a un solo nodo di gestire il traffico in lettura-scrittura, mentre gli altri nodi gestiscono il traffico in sola lettura.

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

Consulta [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) nel _Guida di Commerce su infrastruttura cloud_.

Per le installazioni Adobe Commerce on-premise, configura la nuova implementazione della cache Redis utilizzando `bin/magento:setup` comandi. Consulta [Usa Redis per la cache predefinita](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) nel _Guida alla configurazione_.

>[!WARNING]
>
>Esegui _non_ configurare una connessione slave Redis per i progetti di infrastruttura cloud con un [architettura scalata/divisa](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html). Questo causa errori di connessione Redis. Consulta [Guida alla configurazione di Redis](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) nel _Commerce su infrastruttura cloud_ guida.

## Precarica chiavi

Per riutilizzare i dati tra pagine, elenca le chiavi per il precaricamento in `.magento.env.yaml` file di configurazione.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '061_'                       # Prefix for keys to be preloaded
          backend_options:
            preload_keys:                         # List the keys to be preloaded
              - '061_EAV_ENTITY_TYPES:hash'
              - '061_GLOBAL_PLUGIN_LIST:hash'
              - '061_DB_IS_UP_TO_DATE:hash'
              - '061_SYSTEM_DEFAULT:hash'
```

Per gli impianti locali, cfr. [Funzione di precaricamento Redis](../../../configuration/cache/redis-pg-cache.md#redis-preload-feature) nel _Guida alla configurazione_.

## Abilita cache non aggiornata

Riduci i tempi di attesa di blocco e migliora le prestazioni, soprattutto quando si tratta di numerosi blocchi e chiavi di cache, utilizzando una cache obsoleta durante la generazione in parallelo di una nuova cache. Abilitare la cache non aggiornata e definire i tipi di cache nella `.magento.env.yaml` file di configurazione:

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      default:
        backend_options:
          use_stale_cache: false
      stale_cache_enabled:
        backend_options:
          use_stale_cache: true
      type:
        default:
          frontend: "default"
        layout:
          frontend: "stale_cache_enabled"
        block_html:
          frontend: "stale_cache_enabled"
        reflection:
          frontend: "stale_cache_enabled"
        config_integration:
          frontend: "stale_cache_enabled"
        config_integration_api:
          frontend: "stale_cache_enabled"
        full_page:
          frontend: "stale_cache_enabled"
        translate:
          frontend: "stale_cache_enabled"
```

Per la configurazione delle installazioni locali, consulta [Opzioni cache non aggiornate](../../../configuration/cache/level-two-cache.md#stale-cache-options) nel _Guida alla configurazione_.

## Cache Redis e istanze di sessione separate

La separazione della cache Redis dalla sessione Redis consente di gestire la cache e le sessioni in modo indipendente. Evita che i problemi di cache influiscano sulle sessioni, il che potrebbe influire sui ricavi. Ogni istanza Redis viene eseguita sul proprio core, migliorando le prestazioni.

1. Aggiornare il `.magento/services.yaml` file di configurazione.

   ```yaml
   mysql:
       type: mysql:10.4
       disk: 35000
   
   redis:
      type: redis:6.0
   
   redis-session:              # This is for the new Redis instance
      type: redis:6.0
   
   search:
      type: elasticsearch:7.9
      disk: 5000
   
   rabbitmq:
      type: rabbitmq:3.8
      disk: 2048
   ```

1. Aggiornare il `.magento.app.yaml` file di configurazione.

   ```yaml
   relationships:
       database: "mysql:mysql"
       redis: "redis:redis"
       redis-session: "redis-session:redis"   # Relationship of the new Redis instance
       search: "search:elasticsearch"
       rabbitmq: "rabbitmq:rabbitmq"
   ```

1. Invia un [Ticket di supporto Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) per richiedere il provisioning di una nuova istanza Redis dedicata alle sessioni sugli ambienti di produzione e staging. Includi gli aggiornamenti `.magento/services.yaml` e `.magento.app.yaml` file di configurazione. Questo non causerà tempi di inattività, ma richiede una distribuzione per attivare il nuovo servizio.

1. Verifica che la nuova istanza sia in esecuzione e annota il numero di porta.

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. Aggiungere il numero di porta al `.magento.env.yaml` file di configurazione.

   >[!NOTE]
   >`disable_locking` deve essere impostato su `1`.
   >   

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis:
       port: 6374       # check the port in $MAGENTO_CLOUD_RELATIONSHIPS
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. Rimuovi sessioni da [database predefinito](../../../configuration/cache/redis-pg-cache.md) (`db 0`) sull&#39;istanza della cache Redis.

   ```bash
   redis-cli -h 127.0.0.1 -p 6374 -n 0 FLUSHDB
   ```

Durante la distribuzione, dovresti vedere le seguenti righe nella sezione [genera e distribuisci registro](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html#build-and-deploy-logs):

```terminal
W:   - Downloading colinmollenhour/credis (1.11.1)
W:   - Downloading colinmollenhour/php-redis-session-abstract (v1.4.5)
...
W:   - Installing colinmollenhour/credis (1.11.1): Extracting archive
W:   - Installing colinmollenhour/php-redis-session-abstract (v1.4.5): Extracting archive
...
[2022-08-17 01:13:40] INFO: Version of service 'redis' is 6.0
[2022-08-17 01:13:40] INFO: Version of service 'redis-session' is 6.0
[2022-08-17 01:13:40] INFO: redis-session will be used for session if it was not override by SESSION_CONFIGURATION
```

## Compressione cache

Se utilizzi più di 6 GB di Redis `maxmemory`, è possibile utilizzare la compressione della cache per ridurre lo spazio utilizzato dalle chiavi. Tieni presente che esiste un compromesso con le prestazioni lato client. Se si dispone di CPU di riserva, attivarle. Consulta [Usa Redis per l’archiviazione della sessione](../../../configuration/cache/redis-session.md) nel _Guida alla configurazione_.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true;
      frontend:
        default:
          backend_options:
            compress_data: 4              # 0-9
            compress_tags: 4              # 0-9
            compress_threshold: 20480     # don't compress files smaller than this value
            compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)
```

## Informazioni aggiuntive

- [Cache pagine Redis](../../../configuration/cache/redis-pg-cache.md)
- [Usa Redis per l’archiviazione della sessione](../../../configuration/cache/redis-session.md)
