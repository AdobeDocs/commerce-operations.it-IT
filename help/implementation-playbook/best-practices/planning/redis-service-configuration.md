---
title: Best practice per la configurazione del servizio Redis
description: Scopri come migliorare le prestazioni di caching utilizzando l’implementazione della cache Redis estesa per Adobe Commerce.
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
source-git-commit: e7888688803d86ec342b156da77adc663475fe20
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---


# Best practice per la configurazione del servizio Redis

- Utilizza l’implementazione della cache Redis estesa, che include le seguenti ottimizzazioni per ridurre al minimo il numero di query Redis eseguite su ogni richiesta da Adobe Commerce:
   - Riduce le dimensioni dei trasferimenti di dati di rete tra Redis e Adobe Commerce
   - Riduce il consumo Redis dei cicli della CPU migliorando la capacità della scheda di rete di determinare automaticamente ciò che deve essere caricato
   - Riduce le race condition per le operazioni di scrittura Redis
- Separare la cache Redis dalla sessione Redis
- Comprimere la cache Redis e utilizzare `gzip` per migliorare le prestazioni

## Implementazione della cache Redis estesa

Aggiornare la configurazione per utilizzare l’implementazione della cache Redis estesa `\Magento\Framework\Cache\Backend\Redis`.

### Configurare le distribuzioni cloud

Configurare la cache Redis avanzata impostando `REDIS_BACKEND` variabile di distribuzione in `.magento.env.yaml` file di configurazione.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\Redis'
```

Per ulteriori informazioni, vedere [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) descrizione della variabile in _Guida di Commerce su infrastruttura cloud_.

>[!NOTE]
>
> Controlla la `ece-tools` versione installata nell&#39;ambiente locale dalla riga di comando utilizzando `composer show magento/ece-tools` comando. Se necessario, [aggiornamento alla versione più recente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html).

>[!WARNING]
>
>Esegui _non_ configurare una connessione slave Redis per i progetti di infrastruttura cloud con un [architettura scalata](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html). Questo causa errori di connessione Redis. Consulta [le linee guida per la configurazione di Redis](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) nel _Commerce su infrastruttura cloud_ guida.

### Configurare le distribuzioni locali

Per le distribuzioni locali di Adobe Commerce, configura la nuova implementazione della cache Redis utilizzando `bin/magento:setup` comandi. Per istruzioni, consulta [Usa Redis per la cache predefinita](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching).

## Istanze di sessione e cache separate

La separazione della cache Redis dalla sessione Redis consente di gestire la cache e le sessioni in modo indipendente per evitare che i problemi della cache influiscano sulle sessioni.

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

1. Invia un [Ticket di supporto Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) per modificare la configurazione del servizio Redis negli ambienti Pro Production e Staging. Includi gli aggiornamenti `.magento/services.yaml` e `.magento.app.yaml` file di configurazione.

1. Verifica che la nuova istanza sia in esecuzione e annota il numero di porta.

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. Aggiungere il numero di porta al `.magento.env.yaml` file di configurazione.

   >[!NOTE]
   >`disable_locking` deve essere impostato su `1`.

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

Utilizza la compressione della cache, ma tieni presente che esiste un compromesso con le prestazioni lato client. Se si dispone di CPU di riserva, attivarle. Consulta [Usa Redis per l’archiviazione della sessione](../../../configuration/cache/redis-session.md).

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
