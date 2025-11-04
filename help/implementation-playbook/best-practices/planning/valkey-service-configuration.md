---
title: Best practice per la configurazione del servizio Valkey
description: Scopri come migliorare le prestazioni di caching utilizzando l’implementazione estesa della cache Valkey per Adobe Commerce.
role: Developer, Admin
feature: Best Practices, Cache
exl-id: ca1598b0-07c6-4338-aed1-f2ba05375197
source-git-commit: 75dc606da65196619028e99ec44841db3988a73e
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 0%

---

# Best practice per la configurazione del servizio Valkey

Adobe consiglia le seguenti best practice per la configurazione del servizio Valkey:

## Configurare la cache L2 di Valkey

Configurare la cache L2 di Valkey impostando la variabile di distribuzione `VALKEY_BACKEND` nel file di configurazione `.magento.env.yaml`.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Per la configurazione dell&#39;ambiente nell&#39;infrastruttura cloud, vedere [`VALKEY_BACKEND`](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_backend) nella _Guida all&#39;infrastruttura cloud di Commerce_.

Per le installazioni locali, vedere [Configure Valkey page caching](../../../configuration/cache/valkey-pg-cache.md#configure-page-caching) nella _Guida alla configurazione_.

>[!NOTE]
>
>Verificare di utilizzare la versione più recente del pacchetto `ece-tools`. In caso contrario, [aggiorna alla versione più recente](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package). È possibile controllare la versione installata nell&#39;ambiente locale utilizzando il comando CLI `composer show magento/ece-tools`.

### Dimensioni della memoria cache L2 (Adobe Commerce Cloud)

La cache L2 utilizza un [file system temporaneo](https://en.wikipedia.org/wiki/Tmpfs) come meccanismo di archiviazione. Rispetto ai sistemi di database specializzati con valori chiave, un file system temporaneo non dispone di un criterio di rimozione chiave per controllare l&#39;utilizzo della memoria.

La mancanza di controllo dell&#39;utilizzo della memoria può causare un aumento nel tempo dell&#39;utilizzo della memoria cache L2 accumulando la cache non aggiornata.

Per evitare l’esaurimento della memoria per le implementazioni della cache L2, Adobe Commerce cancella l’archiviazione quando viene raggiunta una determinata soglia. Il valore di soglia predefinito è 95%.

È importante regolare l’utilizzo massimo della memoria cache L2 in base ai requisiti del progetto per lo storage della cache. Utilizzare uno dei metodi seguenti per configurare il dimensionamento della cache di memoria:

- Creare un ticket di supporto per richiedere modifiche alle dimensioni del mount `/dev/shm`.
- Regolare la proprietà `cleanup_percentage` a livello di applicazione per limitare la percentuale di riempimento massima dell&#39;archiviazione. La memoria disponibile rimanente può essere utilizzata da altri servizi.
È possibile modificare la configurazione nella configurazione di distribuzione nel gruppo di configurazione della cache `cache/frontend/default/backend_options/cleanup_percentage`.

>[!NOTE]
>
>L&#39;opzione di configurazione `cleanup_percentage` è stata introdotta in Adobe Commerce 2.4.4.

L&#39;esempio seguente mostra un `CACHE_CONFIGURATION` nel file `.magento.env.yaml`:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            cleanup_percentage: 90
```

I requisiti della cache possono variare in base alla configurazione del progetto e al codice personalizzato di terze parti. L&#39;ambito del dimensionamento della memoria cache L2 consente alla cache L2 di funzionare senza inutili hit di soglia.
Idealmente, l&#39;utilizzo della memoria cache L2 dovrebbe stabilizzarsi a un certo livello al di sotto della soglia, per evitare frequenti cancellazioni di memoria.

È possibile controllare l&#39;utilizzo della memoria di archiviazione nella cache L2 in ogni nodo del cluster utilizzando il seguente comando CLI e quindi cercare la riga `/dev/shm`.
L’utilizzo può variare tra nodi diversi, ma deve convergere allo stesso valore.

```bash
df -h
```

## Abilita connessione slave Valkey

Abilitare una connessione slave Valkey nel file di configurazione `.magento.env.yaml` per consentire a un solo nodo di gestire il traffico di lettura/scrittura mentre gli altri nodi gestiscono il traffico di sola lettura.

```yaml
stage:
  deploy:
    VALKEY_USE_SLAVE_CONNECTION: true
```

Per ulteriori dettagli, vedere [VALKEY_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_use_slave_connection) nella _Guida all&#39;infrastruttura cloud di Commerce_.

Per le installazioni locali di Adobe Commerce, configura la nuova implementazione della cache di Valkey utilizzando i comandi `bin/magento:setup`. Per ulteriori informazioni, vedere [Utilizzare Valkey per la cache predefinita](../../../configuration/cache/valkey-pg-cache.md#configure-page-caching) nella _Guida alla configurazione_.

>[!WARNING]
>
>_non_ configurare una connessione slave Valkey per i progetti di infrastruttura cloud con [architettura scalata/divisa](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/architecture/scaled-architecture). Questo causa errori di connessione a Valkey. Per ulteriori informazioni, vedere la [Guida alla configurazione di Valkey](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_use_slave_connection) nella _Guida di Commerce sull&#39;infrastruttura cloud_.

## Precarica chiavi

Per riutilizzare i dati tra pagine, elencare le chiavi per il precaricamento nel file di configurazione `.magento.env.yaml`.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
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

Per le installazioni locali, vedere [Funzionalità di precaricamento Valkey](../../../configuration/cache/valkey-pg-cache.md#valkey-preload-feature) nella _Guida alla configurazione_.

## Abilita cache non aggiornata

Riduci i tempi di attesa di blocco e migliora le prestazioni, soprattutto quando si tratta di numerosi blocchi e chiavi di cache, utilizzando una cache obsoleta durante la generazione in parallelo di una nuova cache. Abilitare la cache non aggiornata e definire i tipi di cache nel file di configurazione `.magento.env.yaml`:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
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
>Nell&#39;esempio precedente, la cache `full_page` non è rilevante per i progetti di infrastruttura cloud di Adobe Commerce, perché utilizza [Fastly](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/cdn/fastly).

Per la configurazione delle installazioni locali, vedere [Opzioni cache non aggiornate](../../../configuration/cache/level-two-cache.md#stale-cache-options) nella _Guida alla configurazione_.

Durante la distribuzione, nel [registro build e distribuzione](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/develop/test/log-locations#build-and-deploy-logs) dovrebbero essere visualizzate le righe seguenti:

```
W:   - Downloading colinmollenhour/credis (1.11.1)
W:   - Downloading colinmollenhour/php-redis-session-abstract (v1.4.5)
...
W:   - Installing colinmollenhour/credis (1.11.1): Extracting archive
W:   - Installing colinmollenhour/php-redis-session-abstract (v1.4.5): Extracting archive
...
[2022-08-17 01:13:40] INFO: Version of service 'valkey' is 8.0
[2022-08-17 01:13:40] INFO: Version of service 'valkey-session' is 8.0
[2022-08-17 01:13:40] INFO: valkey-session will be used for the session if it was not overridden by SESSION_CONFIGURATION.
```

## Compressione cache

Se si utilizzano più di 6 GB di Valkey `maxmemory`, è possibile utilizzare la compressione della cache per ridurre lo spazio utilizzato dalle chiavi. Tieni presente che esiste un compromesso con le prestazioni lato client. Se disponi di CPU di riserva, Adobe consiglia di abilitarle. Vedere [Use Valkey for session storage](../../../configuration/cache/valkey-session.md) nella _Guida alla configurazione_.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true;
      frontend:
        default:
          backend_options:
            compress_data: 4              # 0-9
            compress_tags: 4              # 0-9
            compress_threshold: 20480     # do not compress files smaller than this value
            compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~70%)
```
