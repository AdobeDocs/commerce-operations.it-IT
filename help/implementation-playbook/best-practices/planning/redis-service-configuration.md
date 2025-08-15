---
title: Best practice per la configurazione del servizio Redis
description: Scopri come migliorare le prestazioni di caching utilizzando l’implementazione della cache Redis estesa per Adobe Commerce.
role: Developer, Admin
feature: Best Practices, Cache
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: bbebb414ae3b8c255e17b1f3673a6c4b7c6f23b2
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 0%

---

# Best practice per la configurazione del servizio Redis

- Configura cache L2 Redis
- Abilita connessione slave Redis
- Precarica chiavi
- Abilita cache non aggiornata
- Separare la cache Redis dalla sessione Redis
- Comprimi la cache Redis e utilizza `gzip` per una compressione più elevata

## Configura cache L2 Redis

Configurare la cache di Redis L2 impostando la variabile di distribuzione `REDIS_BACKEND` nel file di configurazione `.magento.env.yaml`.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Per la configurazione dell&#39;ambiente nell&#39;infrastruttura cloud, vedere [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=it#redis_backend) nella _Guida all&#39;infrastruttura cloud di Commerce_.

Per le installazioni locali, vedere [Configure Redis page caching](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) nella _Guida alla configurazione_.

>[!NOTE]
>
>Verificare di utilizzare la versione più recente del pacchetto `ece-tools`. In caso contrario, [aggiorna alla versione più recente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html?lang=it). È possibile controllare la versione installata nell&#39;ambiente locale utilizzando il comando CLI `composer show magento/ece-tools`.


### Dimensioni della memoria cache L2 (Adobe Commerce Cloud)

La cache L2 utilizza un [file system temporaneo](https://en.wikipedia.org/wiki/Tmpfs) come meccanismo di archiviazione. Rispetto ai sistemi di database specializzati con valori chiave, un file system temporaneo non dispone di criteri di rimozione delle chiavi per controllare l&#39;utilizzo della memoria.

La mancanza di controllo dell&#39;utilizzo della memoria può causare un aumento nel tempo dell&#39;utilizzo della memoria cache L2 accumulando la cache non aggiornata.

Per evitare l’esaurimento della memoria per le implementazioni della cache L2, Adobe Commerce cancella l’archiviazione quando viene raggiunta una determinata soglia. Il valore di soglia predefinito è 95%.

È importante regolare l’utilizzo massimo della memoria cache L2 in base ai requisiti del progetto per lo storage della cache. Utilizzare uno dei metodi seguenti per configurare il dimensionamento della cache di memoria:

- Creare un ticket di supporto per richiedere modifiche alle dimensioni del mount `/dev/shm`.
- Regolare la proprietà `cleanup_percentage` a livello di applicazione per limitare la percentuale di riempimento massima dell&#39;archiviazione. La memoria disponibile rimanente può essere utilizzata da altri servizi.
È possibile modificare la configurazione nella configurazione di distribuzione nel gruppo di configurazione della cache `cache/frontend/default/backend_options/cleanup_percentage`.

>[!NOTE]
>
>L&#39;opzione configurabile `cleanup_percentage` è stata introdotta in Adobe Commerce 2.4.4.

Il codice seguente mostra un esempio di configurazione nel file `.magento.env.yaml`:

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            cleanup_percentage: 90
```

I requisiti della cache possono variare in base alla configurazione del progetto e al codice personalizzato di terze parti. L&#39;ambito del dimensionamento della memoria cache L2 consente alla cache L2 di funzionare senza troppi hit di soglia.
Idealmente, l&#39;utilizzo della memoria cache L2 dovrebbe stabilizzarsi a un certo livello al di sotto della soglia, proprio per evitare frequenti cancellazioni di memoria.

È possibile verificare l&#39;utilizzo della memoria di archiviazione nella cache L2 in ogni nodo del cluster utilizzando il seguente comando CLI e cercando la riga `/dev/shm`.
L’utilizzo può variare tra nodi diversi, ma deve convergere allo stesso valore.

```bash
df -h
```

## Abilita connessione slave Redis

Abilitare una connessione slave Redis nel file di configurazione `.magento.env.yaml` per consentire a un solo nodo di gestire il traffico di lettura/scrittura mentre gli altri nodi gestiscono il traffico di sola lettura.

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

Vedi [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=it#redis_use_slave_connection) nella _Guida di Commerce sull&#39;infrastruttura cloud_.

Per le installazioni Adobe Commerce locali, configurare la nuova implementazione della cache Redis utilizzando i comandi `bin/magento:setup`. Vedere [Utilizzare Redis per la cache predefinita](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) nella _Guida alla configurazione_.

>[!WARNING]
>
>_non_ configurare una connessione slave Redis per i progetti di infrastruttura cloud con [architettura scalata/divisa](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html?lang=it). Questo causa errori di connessione Redis. Consulta la [guida alla configurazione Redis](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=it#redis_use_slave_connection) nella guida _Commerce on Cloud Infrastructure_.

## Precarica chiavi

Per riutilizzare i dati tra pagine, elencare le chiavi per il precaricamento nel file di configurazione `.magento.env.yaml`.

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

Per le installazioni locali, vedere [Funzionalità di precaricamento Redis](../../../configuration/cache/redis-pg-cache.md#redis-preload-feature) nella _Guida alla configurazione_.

## Abilita cache non aggiornata

Riduci i tempi di attesa di blocco e migliora le prestazioni, soprattutto quando si tratta di numerosi blocchi e chiavi di cache, utilizzando una cache obsoleta durante la generazione in parallelo di una nuova cache. Abilitare la cache non aggiornata e definire i tipi di cache nel file di configurazione `.magento.env.yaml`:

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

>[!NOTE]
>
>Nell&#39;esempio precedente, la cache `full_page` non è rilevante per i progetti di infrastruttura cloud di Adobe Commerce, perché utilizza [Fastly](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/cdn/fastly).

Per la configurazione delle installazioni locali, vedere [Opzioni cache non aggiornate](../../../configuration/cache/level-two-cache.md#stale-cache-options) nella _Guida alla configurazione_.

## Cache Redis e istanze di sessione separate

La separazione della cache Redis dalla sessione Redis consente di gestire la cache e le sessioni in modo indipendente. Evita che i problemi di cache influiscano sulle sessioni, il che potrebbe influire sui ricavi. Ogni istanza Redis viene eseguita sul proprio core, migliorando le prestazioni.

1. Aggiornare il file di configurazione `.magento/services.yaml`.

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

1. Aggiornare il file di configurazione `.magento.app.yaml`.

   ```yaml
   relationships:
       database: "mysql:mysql"
       redis: "redis:redis"
       redis-session: "redis-session:redis"   # Relationship of the new Redis instance
       search: "search:elasticsearch"
       rabbitmq: "rabbitmq:rabbitmq"
   ```

1. Invia un [ticket di supporto Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=it#submit-ticket) per richiedere il provisioning di una nuova istanza Redis dedicata alle sessioni negli ambienti di produzione e staging. Includere i file di configurazione `.magento/services.yaml` e `.magento.app.yaml` aggiornati. Questo non causerà tempi di inattività, ma richiede una distribuzione per attivare il nuovo servizio.

1. Verifica che la nuova istanza sia in esecuzione e annota il numero di porta.

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. Aggiungere il numero di porta al file di configurazione `.magento.env.yaml`.

   >[!IMPORTANT]
   >
   >Configurare la porta di sessione Redis solo se `ece-tools` non è in grado di rilevarla automaticamente dalla definizione del servizio di sessione Redis `MAGENTO_CLOUD_RELATIONSHIPS`.

   >[!NOTE]
   >
   >`disable_locking` deve essere impostato su `1`.

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis:
       port: 6374 # check the port in $MAGENTO_CLOUD_RELATIONSHIPS and put it here (by default, you can delete this line!!)
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. Rimuovere le sessioni dal [database predefinito](../../../configuration/cache/redis-pg-cache.md) (`db 0`) nell&#39;istanza della cache Redis.

   ```bash
   redis-cli -h 127.0.0.1 -p 6374 -n 0 FLUSHDB
   ```

Durante la distribuzione, nel [registro build e distribuzione](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/log-locations.html?lang=it#build-and-deploy-logs) dovrebbero essere visualizzate le righe seguenti:

```
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

Se si utilizzano più di 6 GB di Redis `maxmemory`, è possibile utilizzare la compressione della cache per ridurre lo spazio utilizzato dalle chiavi. Tieni presente che esiste un compromesso con le prestazioni lato client. Se si dispone di CPU di riserva, attivarle. Vedere [Utilizzare Redis per l&#39;archiviazione della sessione](../../../configuration/cache/redis-session.md) nella _Guida alla configurazione_.

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
