---
title: Best practice per la configurazione del servizio Redis
description: Scopri come migliorare le prestazioni del caching utilizzando l’implementazione estesa della cache Redis per Adobe Commerce.
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
source-git-commit: 92faa85b51a1fd5314a5906e8650b03723118ce1
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---


# Best practice per la configurazione del servizio Redis

- Utilizza l’implementazione estesa della cache Redis, che include le seguenti ottimizzazioni per ridurre al minimo il numero di query Redis eseguite su ogni richiesta da Adobe Commerce:
   - Diminuisce le dimensioni dei trasferimenti di dati di rete tra Redis e Adobe Commerce
   - Riduce il consumo di Redis dei cicli della CPU migliorando la capacità dell&#39;adattatore di determinare automaticamente ciò che deve essere caricato
   - Riduce le condizioni di gara sulle operazioni di riscrittura
- Separa la cache Redis dalla sessione Redis
- Comprimi la cache Redis e utilizza `gzip` per migliorare le prestazioni

## Implementazione estesa della cache Redis

Aggiorna la configurazione per utilizzare l&#39;implementazione estesa della cache Redis `\Magento\Framework\Cache\Backend\Redis`.

### Configurare le distribuzioni cloud

Configura la cache Redis migliorata impostando `REDIS_BACKEND` variabile di distribuzione nel `.magento.env.yaml` file di configurazione.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\Redis'
```

Per ulteriori informazioni, consulta la sezione [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) nella descrizione della variabile _Guida a Commerce on Cloud Infrastructure_.

>[!NOTE]
>
> Controlla la `ece-tools` versione installata nell&#39;ambiente locale dalla riga di comando utilizzando `composer show magento/ece-tools` comando. Se necessario, [aggiornamento alla versione più recente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html).

>[!WARNING]
>
>Do _not_ configurare una connessione slave Redis per progetti di infrastruttura cloud con un [architettura scalata](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html). Questo causa errori di connessione Redis. Vedi [guida alla configurazione di Redis](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) in _Commerce sull’infrastruttura cloud_ guida.

### Configurare le distribuzioni locali

Per le implementazioni on-premise di Adobe Commerce, configura la nuova implementazione della cache Redis utilizzando il `bin/magento:setup` comandi. Per istruzioni, consulta [Usa Redis per la cache predefinita](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching).

## Cache e istanze di sessione separate

La separazione della cache Redis dalla sessione Redis consente di gestire la cache e le sessioni in modo indipendente per evitare problemi di cache che influenzano le sessioni.

1. Aggiorna `.magento/services.yaml` file di configurazione.

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

1. Aggiorna `.magento.app.yaml` file di configurazione.

   ```yaml
   relationships:
       database: "mysql:mysql"
       redis: "redis:redis"
       redis-session: "redis-session:redis"   # Relationship of the new Redis instance
       search: "search:elasticsearch"
       rabbitmq: "rabbitmq:rabbitmq"
   ```

1. Invia un [ticket di supporto Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket) per modificare la configurazione del servizio Redis negli ambienti Pro Production e Staging. Includi l’aggiornamento `.magento/services.yaml` e `.magento.app.yaml` file di configurazione.

1. Verifica che la nuova istanza sia in esecuzione e prendi una nota del numero di porta.

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. Aggiungi il numero di porta al `.magento.env.yaml` file di configurazione.

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

1. Rimuovi sessioni da [database predefinito](../../../configuration/cache/redis-pg-cache.md) (`db 0`) sull’istanza della cache Redis.

   ```bash
   redis-cli -h 127.0.0.1 -p 6374 -n 0 FLUSHDB
   ```

Durante la distribuzione, dovresti visualizzare le seguenti righe nel [genera e distribuisci registro](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html#build-and-deploy-logs):

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

Utilizza la compressione cache, ma tieni presente che esiste un compromesso con le prestazioni lato client. Se disponi di CPU di riserva, abilitala. Vedi [Utilizzare Redis per l&#39;archiviazione delle sessioni](../../../configuration/cache/redis-session.md).

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

- [Cache della pagina Redis](../../../configuration/cache/redis-pg-cache.md)
- [Utilizzare Redis per l&#39;archiviazione delle sessioni](../../../configuration/cache/redis-session.md)
