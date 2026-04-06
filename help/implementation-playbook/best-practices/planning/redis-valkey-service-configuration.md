---
title: Best practice per la configurazione del servizio Redis e Valkey
description: Scopri come configurare i servizi Redis e Valkey per Adobe Commerce. Migliora le prestazioni di caching con cache L2, connessioni slave, cache non aggiornata e separazione delle sessioni.
solution: Commerce
role: Developer, Admin
level: Intermediate
feature: Best Practices, Cache
feature-set: Commerce
topic: Performance
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
source-git-commit: aedff83fe473691340f0f254e7c79ef7e632ac0d
workflow-type: tm+mt
source-wordcount: '2139'
ht-degree: 0%

---


# Best practice per la configurazione del servizio Redis e Valkey

Utilizza questi consigli per configurare Redis o Valkey per il caching e le sessioni di Adobe Commerce.

- Configurare la cache L2
- Abilita connessione slave
- Precarica chiavi
- Abilita cache non aggiornata
- Cache e sessione separate
- Comprimi la cache
- Esempi di configurazione

>[!NOTE]
>
>Per gli ambienti dell&#39;infrastruttura Commerce on Cloud, verificare di utilizzare la versione più recente del pacchetto `ece-tools`. In caso contrario, [aggiorna alla versione più recente](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/dev-tools/ece-tools/update-package.html?lang=it). È possibile controllare la versione installata nell&#39;ambiente locale utilizzando il comando CLI `composer show magento/ece-tools`.

## Configurare la cache L2

Configurare la cache L2 impostando la variabile di distribuzione `REDIS_BACKEND` o `VALKEY_BACKEND` nel file di configurazione `.magento.env.yaml`.

>[!BEGINTABS]

>[!TAB Configurazione Redis]

Per Redis, utilizzare:

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Per la configurazione dell&#39;ambiente nell&#39;infrastruttura cloud, vedere il riferimento alla configurazione [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=it#redis_backend) nella _Guida all&#39;infrastruttura cloud di Commerce_.

Per le installazioni locali, vedere [Configure Redis page caching](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) nella _Guida alla configurazione_.

>[!TAB Configurazione Valkey]

Per Valkey, utilizzare:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Per la configurazione dell&#39;ambiente nell&#39;infrastruttura cloud, vedere il riferimento alla configurazione [`VALKEY_BACKEND`](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_backend) nella _Guida all&#39;infrastruttura cloud di Commerce_.

Per le installazioni locali, vedere [Configure Valkey](../../../configuration/cache/config-valkey.md) in _Configuration Guide_.

>[!ENDTABS]


### Dimensioni della memoria cache L2 per Adobe Commerce Cloud

La cache L2 utilizza un [file system temporaneo](https://en.wikipedia.org/wiki/Tmpfs) (`/dev/shm`) come meccanismo di archiviazione. A differenza degli archivi specializzati di valori chiave, i tmpfs non dispongono di criteri di rimozione delle chiavi, pertanto l&#39;utilizzo della memoria può crescere senza limiti. Per evitare l’esaurimento, Adobe Commerce cancella automaticamente lo storage L2 quando l’utilizzo raggiunge una soglia configurabile (95% per impostazione predefinita). È possibile controllare il consumo di memoria richiedendo un montaggio `/dev/shm` più grande o abbassando la soglia di pulizia.

Regola l’utilizzo massimo della memoria cache L2 in base ai requisiti del progetto. Utilizza uno dei seguenti metodi:

- Creare un ticket di supporto per regolare la dimensione di montaggio `/dev/shm`. Per questo scenario, Adobe consiglia di impostare la dimensione di montaggio `/dev/shm` su 15 GB.
- Regolare la proprietà `cleanup_percentage` a livello di applicazione per limitare l&#39;utilizzo dello spazio di archiviazione e della memoria disponibile per altri servizi.
È possibile modificare la configurazione nella configurazione di distribuzione nel gruppo di configurazione della cache `cache/frontend/default/backend_options/cleanup_percentage`.

>[!NOTE]
>
>L&#39;opzione configurabile `cleanup_percentage` è stata introdotta in Adobe Commerce 2.4.4.

Gli esempi seguenti mostrano il codice di configurazione nel file `.magento.env.yaml`:

>[!BEGINTABS]

>[!TAB Configurazione Redis]

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

>[!TAB Configurazione Valkey]

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

>[!ENDTABS]

I requisiti della cache dipendono dalla configurazione del progetto e dal codice personalizzato di terze parti. Dimensione della memoria cache L2 in modo che la cache possa funzionare senza frequenti hit di soglia.

Idealmente, l&#39;utilizzo della memoria cache L2 si stabilizza al di sotto della soglia per evitare frequenti cancellazioni dello storage.

È possibile verificare l&#39;utilizzo della memoria di archiviazione nella cache L2 in ogni nodo del cluster eseguendo il seguente comando CLI e rivedendo la riga `/dev/shm`.

```bash
df -h /dev/shm
```

L’utilizzo può variare tra i nodi, ma deve convergere in un valore simile.

## Configurare directory personalizzate per la cache L2

Quando si ottimizzano le prestazioni della cache L2, è possibile scegliere di memorizzare i file della cache locale in una directory personalizzata ad alte prestazioni, ad esempio un disco RAM (`/dev/shm/`).

Per garantire la coerenza a livello di applicazione ed evitare la frammentazione dell&#39;archiviazione della cache, configurare sia le opzioni specifiche del back-end L2 che il Registro di sistema della directory globale nel file `app/etc/env.php`.

**Best practice:** Definisci sia `local_backend_options['cache_dir']` che il `directories['cache']['path']` globale.

- **`local_backend_options['cache_dir']`**: indirizza l&#39;adattatore cache back-end (ad esempio, `Cm_Cache_Backend_File`) a memorizzare i file della cache L2 sincronizzati nel percorso specificato.
- **`directories['cache']['path']`**: aggiorna il Registro di sistema di Adobe Commerce `DirectoryList`, stabilendo il percorso personalizzato come directory definitiva della cache di sistema per l&#39;intera applicazione.

### Impedisci la suddivisione delle directory della cache e errori di segmentazione GlusterFS

Se si definisce il percorso personalizzato esclusivamente in `local_backend_options`, il motore di cache L2 funziona correttamente, ma il Registro di sistema globale dell&#39;applicazione continua a riconoscere `var/cache` come percorso di cache predefinito.

Questa mancata corrispondenza di configurazione determina uno scenario &quot;split-brain&quot; in cui estensioni di terze parti o processi di fallback di base scrivono file temporanei nella directory predefinita `var/cache`.

**Impatto critico su Adobe Commerce Cloud:** Nelle architetture Pro, la directory `var/` è montata su un file system distribuito condiviso. L&#39;imposizione dell&#39;I/O della cache ad alta velocità su questo montaggio di rete sovraccarica il client ed è un trigger primario per **errori di segmentazione GlusterFS e interruzioni a livello di cluster**. La configurazione di entrambe le impostazioni garantisce che tutti gli I/O della cache rimangano rigorosamente sul disco locale ad alte prestazioni.

### Esempio di configurazione

Per applicare un&#39;unica directory cache unificata, aggiornare il file `env.php` in modo da includere entrambe le configurazioni:

```php
return [
    // 1. Override the global directory registry
    'directories' => [
        'cache' => [
            'path' => '/dev/shm/magento_cache'
        ]
    ],
    // 2. Configure the L2 cache engine
    'cache' => [
        'frontend' => [
            'default' => [
                'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
                'backend_options' => [
                    'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                    'server' => '127.0.0.1',
                    'port' => '6379',
                    'database' => '1',
                    // ... other redis configurations ...
                    'local_backend' => 'Cm_Cache_Backend_File',
                    'local_backend_options' => [
                        'cache_dir' => '/dev/shm/magento_cache' 
                    ]
                ]
            ]
        ]
    ],
    // ...
];
```

## Abilita connessione slave

Abilitare la connessione slave nel file `.magento.env.yaml` per consentire ad Adobe Commerce di utilizzare una connessione cache di sola lettura aggiuntiva per le operazioni di lettura mentre si continua a utilizzare l&#39;endpoint primario per le operazioni di scrittura. Questa configurazione può ridurre il carico di lettura sul servizio di cache principale e distribuire il traffico di lettura in modo più efficace.

>[!BEGINTABS]

>[!TAB Configurazione Redis]

Per Redis, utilizzare:

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

Per la configurazione dell&#39;ambiente nell&#39;infrastruttura Commerce Cloud, vedere [REDIS_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=it#redis_use_slave_connection) nella _Guida di Commerce sull&#39;infrastruttura cloud_.

Per le installazioni Adobe Commerce locali, configurare la nuova implementazione della cache Redis utilizzando i comandi `bin/magento setup`. Vedere [Utilizzare Redis per la cache predefinita](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching) nella _Guida alla configurazione_.

>[!TAB Configurazione Valkey]

Per Valkey, utilizzare:

```yaml
stage:
  deploy:
    VALKEY_USE_SLAVE_CONNECTION: true
```

Per la configurazione dell&#39;ambiente nell&#39;infrastruttura Commerce Cloud, vedere [VALKEY_USE_SLAVE_CONNECTION](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=it#valkey_use_slave_connection) nella _Guida di Commerce sull&#39;infrastruttura cloud_.

Per le installazioni locali di Adobe Commerce, configura la nuova implementazione della cache di Valkey utilizzando i comandi `bin/magento setup`. Vedi [Configurazione di Valkey](../../../configuration/cache/config-valkey.md) nella _Guida alla configurazione_.

>[!ENDTABS]

## Precarica chiavi

Magento in genere carica le voci della cache da Redis o Valkey una chiave alla volta. La funzione di precaricamento ti consente di fornire un elenco di chiavi utilizzate di frequente che Magento recupera in una singola pipeline al primo accesso durante una richiesta. Magento mantiene quindi i valori recuperati nella memoria PHP per il resto di tale richiesta, riducendo i round trip ripetuti a Redis o Valkey e migliorando le prestazioni di bootstrap delle richieste per tali chiavi.

Puoi identificare le chiavi utilizzate di frequente monitorando i comandi attivi su Redis o Valkey:

>[!BEGINTABS]

>[!TAB Redis configurazione chiave di precaricamento]

Le chiavi di precaricamento sono configurate nel file di configurazione `.magento.env.yaml`.

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '061_' # Prefix for keys to be preloaded, it can be any random string
          backend_options:
            preload_keys: # List the keys to be preloaded
              - '061_EAV_ENTITY_TYPES:hash' # The key name must start with the id_prefix set above
              - '061_GLOBAL_PLUGIN_LIST:hash'
              - '061_DB_IS_UP_TO_DATE:hash'
              - '061_SYSTEM_DEFAULT:hash'
```

Per elencare le chiavi, eseguire il comando seguente:

```terminal
redis-cli -p 6370 -n 1 MONITOR > /tmp/list.keys
```

Dopo 10 secondi, premere **[!UICONTROL Ctrl+C]**. Quindi esegui il seguente comando:

```terminal
cat /tmp/list.keys | grep "HGET" | awk '{print $5}' | sort | uniq -c | sort -nr | head -n 50
```

In questo registro sono elencate le chiavi che è possibile precaricare. Per visualizzare il contenuto di una chiave, eseguire il comando seguente:

```terminal
redis-cli -p 6370 -n 1 hgetall "<key_name>"
```

Per le installazioni locali, vedere [Funzionalità di precaricamento Redis](../../../configuration/cache/redis-pg-cache.md#redis-preload-feature) nella _Guida alla configurazione_.

>[!TAB Configurazione chiave di precaricamento Valkey]

Le chiavi di precaricamento sono configurate nel file di configurazione `.magento.env.yaml`.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '061_' # Prefix for keys to be preloaded, it can be any random string
          backend_options:
            preload_keys: # List the keys to be preloaded
              - '061_EAV_ENTITY_TYPES:hash' # The key name must start with the id_prefix set above
              - '061_GLOBAL_PLUGIN_LIST:hash'
              - '061_DB_IS_UP_TO_DATE:hash'
              - '061_SYSTEM_DEFAULT:hash'
```

Per elencare le chiavi, eseguire il comando seguente:

```terminal
valkey-cli -p 6370 -n 1 MONITOR > /tmp/list.keys
```

Dopo 10 secondi, premere **[!UICONTROL Ctrl+C]**. Quindi esegui il seguente comando:

```terminal
cat /tmp/list.keys | grep "HGET" | awk '{print $5}' | sort | uniq -c | sort -nr | head -n 50
```

In questo registro sono elencate le chiavi che è possibile precaricare. Per visualizzare il contenuto di una chiave, eseguire il comando seguente:

```terminal
valkey-cli -p 6370 -n 1 hgetall "<key_name>"
```

Per le installazioni locali, vedere [Funzionalità di precaricamento Valkey](../../../configuration/cache/valkey-pg-cache.md#valkey-preload-feature) nella _Guida alla configurazione_.

>[!ENDTABS]

## Abilita cache non aggiornata

La cache non aggiornata è una funzionalità della cache L2 di `RemoteSynchronizedCache`. Se abilitata, Adobe Commerce può distribuire un valore della cache locale esistente da `/dev/shm` mentre un&#39;altra richiesta sta già rigenerando la stessa voce, invece di fare attendere ogni richiesta concorrente. Questo riduce gli stamp della cache e i conflitti di blocco durante la rigenerazione di voci costose della cache.

### Come funziona

Con `RemoteSynchronizedCache`, Magento mantiene due copie di ogni voce della cache: una copia locale in `/dev/shm` e una copia remota in Redis o Valkey. Quando la copia remota non è disponibile ed esiste già un blocco di rigenerazione per tale chiave, le richieste simultanee possono ricevere il valore locale precedente invece di attendere che venga scritto il nuovo valore.

Per abilitare la cache non aggiornata, configurarla nel file `.magento.env.yaml`.

>[!BEGINTABS]

>[!TAB Configura cache non aggiornata per Redis]

Per Redis:

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            use_stale_cache: true
```

>[!TAB Configura cache non aggiornata per Valkey]

Per Valkey:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            use_stale_cache: true
```

>[!ENDTABS]

>[!NOTE]
>
>Il tipo di cache `full_page` non è rilevante per i progetti di infrastruttura Adobe Commerce on Cloud perché utilizza [Fastly](https://experienceleague.adobe.com/it/docs/commerce-cloud-service/user-guide/cdn/fastly).

Per le installazioni locali, vedere [Opzioni cache non aggiornate](../../../configuration/cache/level-two-cache.md#stale-cache-options) nella _Guida alla configurazione_.

>[!WARNING]
>
>La configurazione precedente abilita la cache non aggiornata nel front-end della cache `default`, che applica il comportamento di cache non aggiornata a tutte le voci della cache che utilizzano tale front-end. I tipi di cache di base di Magento generalmente funzionano come previsto con questa impostazione. Tuttavia, se il progetto include codice personalizzato o estensioni che scrivono nella cache tramite l&#39;API generica `\Magento\Framework\App\Cache` (ad esempio `$this->cache->save()`) senza una cache front-end dedicata, tali voci possono anche fornire valori non aggiornati durante la rigenerazione.
>
>
>Se si verifica un comportamento imprevisto nelle personalizzazioni, lasciare disabilitata la cache non aggiornata nel front-end `default` e abilitarla solo per i tipi di cache selezionati, come avviene di solito [in locale](../../../configuration/cache/level-two-cache.md#stale-cache-options).

### Abilitazione di una cache non aggiornata singolarmente per tipo di cache

È possibile abilitare una cache non aggiornata solo per i tipi di cache selezionati definendo una cache front-end dedicata in `.magento.env.yaml` e mappando i tipi di cache selezionati.

Per funzionare correttamente, il front-end personalizzato deve essere definito come front-end completo in `CACHE_CONFIGURATION.frontend`. Non è sufficiente definire solo `use_stale_cache: true` per un nuovo nome front-end.

**Configurazioni di esempio**

>[!BEGINTABS]

>[!TAB Configura cache non aggiornata per Redis]

Per Redis:

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # In this frontend, we keep stale cache set to false.
          id_prefix: '001_'
          backend_options:
            use_stale_cache: false

        # Now, create a new frontend called 'stale_cache_enabled'.
        # It must contain the same backend connection settings as the frontend 'default':

        stale_cache_enabled:
          id_prefix: '001_'
          backend: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
          backend_options:
            remote_backend: '\Magento\Framework\Cache\Backend\Redis'
            remote_backend_options:
              server: localhost
              port: 6370 # Use the same port used by the frontend 'default' in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same port used by the frontend 'default' in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: 'Cm_Cache_Backend_File'
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true # stale cache here is enabled

      # Now select which cache types you want to enable (stale_cache_enabled), or disable (default)

      type:
        default:
          frontend: default
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...
```

>[!TAB Configura cache non aggiornata per Valkey]

Per Valkey:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # In this frontend, we keep stale cache set to false.
          id_prefix: '001_'
          backend_options:
            use_stale_cache: false

        # Now, create a new frontend called 'stale_cache_enabled'.
        # It must contain the same backend connection settings as the frontend 'default':
 
        stale_cache_enabled:
          id_prefix: '001_'
          backend: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
          backend_options:
            remote_backend: '\Magento\Framework\Cache\Backend\Redis'
            remote_backend_options:
              server: localhost
              port: 6370 # Use the same port used by the frontend 'default' in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same port used by the frontend 'default' in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: 'Cm_Cache_Backend_File'
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true # stale cache here is enabled

      # Now select which cache types you want to enable (stale_cache_enabled), or disable (default)

      type:
        default:
          frontend: default
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...
```

>[!ENDTABS]

>[!NOTE]
>
>Se il front-end di origine è configurato con opzioni di back-end aggiuntive, ad esempio compressione, nuovi tentativi, chiavi di precaricamento o altri valori di tuning, copiare tali opzioni in `stale_cache_enabled` in modo che il nuovo front-end mantenga lo stesso comportamento.


## Istanze di sessione e cache separate

La separazione della cache dalle sessioni consente di gestirle in modo indipendente. Riduce il conflitto tra la cache e il traffico di sessione, evita che la pressione relativa alla cache influisca sulle sessioni e consente di ridimensionare e regolare ogni istanza Redis o Valkey per il proprio carico di lavoro.

Segui i passaggi seguenti per effettuare il provisioning di un’istanza dedicata per le sessioni:

>[!BEGINTABS]

>[!TAB Redis]

1. Aggiornare il file di configurazione `.magento/services.yaml`.

   ```yaml
   mysql:
     type: mysql:10.4
     disk: 35000
   
   redis:
     type: redis:6.0
   
   redis-session: # This is for the new Redis instance
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

1. Richiedi una nuova istanza Redis dedicata alle sessioni sugli ambienti di produzione e staging.

   Invia un [ticket di supporto Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=it#submit-ticket). Includere i file di configurazione `.magento/services.yaml` e `.magento.app.yaml` aggiornati.

   Questo aggiornamento non causa tempi di inattività, ma richiede una distribuzione per attivare il nuovo servizio.

1. Verifica che la nuova istanza sia in esecuzione e annota il numero della porta.

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. Aggiungere il numero di porta al file di configurazione `.magento.env.yaml`.

   >[!IMPORTANT]
   >
   >Configurare la porta di sessione Redis solo se `ece-tools` non è in grado di rilevarla automaticamente dalla definizione del servizio di sessione Redis `MAGENTO_CLOUD_RELATIONSHIPS`.

   >[!NOTE]
   >
   >Impostare `disable_locking` su `1` per ottenere prestazioni ottimali. Nei rari casi in cui si verificano condizioni di tipo &quot;race condition&quot; a causa di un&#39;elevata attività della sessione simultanea, impostarla su `0` per abilitare il blocco.

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis:
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. Rimuovere le sessioni dal [database predefinito](../../../configuration/cache/redis-pg-cache.md) (`db 0`) nell&#39;istanza della cache Redis.

   ```terminal
   redis-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!TAB Chiave Valvola]

1. Aggiornare il file di configurazione `.magento/services.yaml`.

   ```yaml
   mysql:
     type: mysql:10.4
     disk: 35000
   
   valkey:
     type: valkey:8.0
   
   valkey-session: # This is for the new Valkey instance
     type: valkey:8.0
   
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
     valkey: "valkey:valkey"
     valkey-session: "valkey-session:valkey"   # Relationship of the new Valkey instance
     search: "search:elasticsearch"
     rabbitmq: "rabbitmq:rabbitmq"
   ```

1. Richiedi una nuova istanza di Valkey dedicata alle sessioni sugli ambienti di produzione e staging.

   Invia un [ticket di supporto Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=it#submit-ticket). Includere i file di configurazione `.magento/services.yaml` e `.magento.app.yaml` aggiornati.

   Questo aggiornamento non causa tempi di inattività, ma richiede una distribuzione per attivare il nuovo servizio.

1. Verifica che la nuova istanza sia in esecuzione e annota il numero della porta.

   ```bash
   echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp
   ```

1. Aggiungere il numero di porta al file di configurazione `.magento.env.yaml`.

   >[!IMPORTANT]
   >
   >Configurare la porta di sessione Valkey solo se `ece-tools` non è in grado di rilevarla automaticamente dalla definizione del servizio di sessione Valkey `MAGENTO_CLOUD_RELATIONSHIPS`.

   >[!NOTE]
   >
   >Impostare `disable_locking` su `1` per ottenere prestazioni ottimali. Nei rari casi in cui si verificano condizioni di tipo &quot;race condition&quot; a causa di un&#39;elevata attività della sessione simultanea, impostarla su `0` per abilitare il blocco.

   ```yaml
   SESSION_CONFIGURATION:
     _merge: true
     redis: # keep 'redis' even if you are using Valkey.
       timeout: 5
       disable_locking: 1
       bot_first_lifetime: 60
       bot_lifetime: 7200
       max_lifetime: 2592000
       min_lifetime: 60
   ```

1. Rimuovere le sessioni dal [database predefinito](../../../configuration/cache/redis-pg-cache.md) (`db 0`) nell&#39;istanza della cache di Valkey.

   ```terminal
   valkey-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!ENDTABS]

## Compressione cache

Se si utilizzano più di 6 GB di Redis o Valkey `maxmemory`, è possibile abilitare la compressione della cache per ridurre lo spazio utilizzato dalle chiavi. Tieni presente che questa impostazione consente di risparmiare memoria grazie alle prestazioni lato client. Se disponi di una capacità CPU di riserva, puoi attivarla. Vedere [Utilizzare Redis per l&#39;archiviazione della sessione](../../../configuration/cache/redis-session.md) o [Utilizzare Valkey per l&#39;archiviazione della sessione](../../../configuration/cache/valkey-session.md) nella _Guida alla configurazione_.

```yaml
stage:
  deploy:
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            compress_data: 4              # 0-9
            compress_tags: 4              # 0-9
            compress_threshold: 20480     # don't compress files smaller than this value
            compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)
```

## Abilita liberazione asincrona

Per abilitare `lazyfree` su Adobe Commerce nell&#39;infrastruttura cloud, invia un [ticket di supporto Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=it#submit-ticket) richiedendo che la seguente configurazione Redis o Valkey venga applicata agli ambienti:

```text
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
lazyfree-lazy-user-del yes
```

Quando `lazyfree` è abilitato, Redis o Valkey scarica il recupero della memoria in thread in background per eliminazioni, scadenze, eliminazioni avviate dal server, eliminazioni da parte dell&#39;utente e scaricamenti del set di dati di replica. Questo riduce il blocco del thread principale e può ridurre la latenza della richiesta.

>[!NOTE]
>
>Con l&#39;opzione `lazyfree-lazy-user-del yes` il comando `DEL` si comporta come `UNLINK`, che scollega immediatamente le chiavi e libera la memoria in modo asincrono.

>[!WARNING]
>
>Poiché la liberazione si verifica in background, la memoria utilizzata dalle chiavi eliminate, scadute o eliminate rimane allocata fino al completamento del lavoro da parte dei thread in background. Se l’istanza Redis o Valkey è già soggetta a una forte pressione di memoria, esegui il test con cautela e valuta prima di tutto la riduzione della pressione di memoria. Ad esempio, disattiva la cache di blocco per casi specifici e istanze Redis di cache e sessione separate come descritto sopra.

## Abilita I/O multithread

Per abilitare il threading di I/O Redis su Adobe Commerce nell&#39;infrastruttura cloud, invia un [ticket di supporto Adobe Commerce](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html?lang=it#submit-ticket) richiedendo la configurazione del threading di I/O seguente. Questa configurazione può migliorare il throughput scaricando le letture e le scritture del socket e l&#39;analisi dei comandi dal thread principale, al costo di un maggiore utilizzo di CPU. Convalida sotto carico e monitora gli host.

>[!BEGINTABS]

>[!TAB Configurare i thread di I/O per Redis]

Per Redis:

```text
io-threads-do-reads yes
io-threads 8 # Choose a value lower than the number of CPU cores (check with nproc), and then tune under load.
```

>[!TAB Configurazione thread di I/O per Valkey]

Per Valkey:

```text
io-threads-do-reads yes
io-threads 8 # choose a value lower than the number of CPU cores (check with nproc), then tune under load
events-per-io-thread 2
```

>[!ENDTABS]


>[!NOTE]
>
>I thread di I/O sono paralleli solo all&#39;I/O client e all&#39;analisi. L’esecuzione del comando Redis rimane a thread singolo.

>[!WARNING]
>
>L&#39;abilitazione dei thread di I/O può aumentare l&#39;utilizzo di CPU e non giovare a tutti i carichi di lavoro. Inizia con un valore e un benchmark prudenti. Se la latenza aumenta o CPU satura, ridurre `io-threads` o disabilitare le letture nei thread di I/O.


## Aumentare i timeout e i tentativi client

Aumentare la tolleranza del client cache Redis o Valkey a brevi periodi di saturazione regolando le opzioni di back-end in `.magento.env.yaml`.

```yaml
stage:
  deploy:
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            connect_retries: 3 # Number of connection retries
            remote_backend_options:
              read_timeout: 10 # Timeout
```

Queste impostazioni possono ridurre gli errori di connessione intermittente e di timeout di lettura durante picchi brevi, ritentando la configurazione della connessione e lasciando più tempo per le risposte da Redis o Valkey.

>[!NOTE]
>
>Queste impostazioni possono essere utili in caso di breve congestione, ma non correggono il sovraccarico persistente.

## Esempi di configurazione

Utilizza gli esempi seguenti come punto di partenza per le configurazioni del servizio Redis o Valkey.


### Applica tutte le raccomandazioni sulle best practice

>[!BEGINTABS]

>[!TAB Redis]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    REDIS_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '001_' # Any prefix is fine, but keep it consistent.
          backend_options:
            use_stale_cache: true             # Enables stale cache feature for all cache types
            connect_retries: 3                # Number of connection retries
            preload_keys:                     # Preload keys at backend_options level (official Adobe placement)
              - '001_EAV_ENTITY_TYPES:hash'   # Bootstrap: entity types
              - '001_GLOBAL_PLUGIN_LIST:hash' # Bootstrap: DI plugin list
              - '001_DB_IS_UP_TO_DATE:hash'   # Bootstrap: schema version
              - '001_SYSTEM_DEFAULT:hash'     # Config: system defaults
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1        # Required for split architecture
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4              # 0-9
            # compress_tags: 4              # 0-9
            # compress_threshold: 20480     # don't compress files smaller than this value
            # compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)

    SESSION_CONFIGURATION:
      _merge: true
      redis:

        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.

        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!TAB Esempio di configurazione Valkey]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    VALKEY_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '001_' # any prefix is fine, but keep it consistent.
          backend_options:
            use_stale_cache: true             # Enables stale cache feature for all cache types
            connect_retries: 3                # Number of connection retries
            preload_keys:                     # Preload keys at backend_options level (official Adobe placement)
              - '001_EAV_ENTITY_TYPES:hash'   # Bootstrap: entity types
              - '001_GLOBAL_PLUGIN_LIST:hash' # Bootstrap: DI plugin list
              - '001_DB_IS_UP_TO_DATE:hash'   # Bootstrap: schema version
              - '001_SYSTEM_DEFAULT:hash'     # Config: system defaults
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1        # Required for split architecture
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4              # 0-9
            # compress_tags: 4              # 0-9
            # compress_threshold: 20480     # don't compress files smaller than this value
            # compression_lib: 'gzip'       # snappy and lzf for performance, gzip for high compression (~69%)

    SESSION_CONFIGURATION:
      _merge: true
      redis:
        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.
        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!ENDTABS]

### Applicare tutte le raccomandazioni sulle best practice e separare la cache non aggiornata per tipo di cache

>[!BEGINTABS]

>[!TAB Redis]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    REDIS_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # Keep stale cache disabled on the broad default frontend.
          id_prefix: '001_' # Keep this prefix consistent with the frontend configuration generated in env.php
          backend_options:
            use_stale_cache: false # stale cache false here
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

        stale_cache_enabled: # New frontend with stale cache enabled only for selected cache types.
          id_prefix: '001_' # Use the same id_prefix used by the source frontend in env.php
          backend: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
          backend_options:
            remote_backend: \Magento\Framework\Cache\Backend\Redis
            remote_backend_options:
              server: localhost
              port: 6370   # Use the same port used by the source frontend in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same slave connection/read port used by the source frontend in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: Cm_Cache_Backend_File
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

      type:
        default:
          frontend: default # Keeps stale cache disabled on the broad default frontend, including generic cache writes that use \Magento\Framework\App\Cache, such as $this->cache->save().
        block_html:
          frontend: stale_cache_enabled # This is often one of the cache types that benefits the most from stale cache, because it is heavily used and can contribute significantly to lock contention during regeneration. In most cases, it can remain enabled. Exclude it only if the project has customization-specific issues caused by stale block output.
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...

    SESSION_CONFIGURATION:
      _merge: true
      redis:
        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.
        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!TAB Chiave Valvola]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables the slave connection logic in Magento. It also works in a split architecture
    VALKEY_BACKEND: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # Keep stale cache disabled on the broad default frontend.
          id_prefix: '001_' # Keep this prefix consistent with the frontend configuration generated in env.php
          backend_options:
            use_stale_cache: false # stale cache false here
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            remote_backend_options:
              read_timeout: 10
              retry_reads_on_master: 1
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

        stale_cache_enabled: # New frontend with stale cache enabled only for selected cache types.
          id_prefix: '001_' # Use the same id_prefix used by the source frontend in env.php
          backend: \Magento\Framework\Cache\Backend\RemoteSynchronizedCache
          backend_options:
            remote_backend: \Magento\Framework\Cache\Backend\Redis
            remote_backend_options:
              server: localhost
              port: 6370   # Use the same port used by the source frontend in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same slave connection/read port used by the source frontend in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: Cm_Cache_Backend_File
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true
            connect_retries: 3
            preload_keys:
              - '001_EAV_ENTITY_TYPES:hash'
              - '001_GLOBAL_PLUGIN_LIST:hash'
              - '001_DB_IS_UP_TO_DATE:hash'
              - '001_SYSTEM_DEFAULT:hash'
              - '001_EXTENSION_ATTRIBUTES_CONFIG:hash'
            # Keep compression disabled for maximum performance. Only enable it if the cache usage is approaching the limit defined in maxmemory:
            # compress_data: 4
            # compress_tags: 4
            # compress_threshold: 20480
            # compression_lib: 'gzip'

      type:
        default:
          frontend: default # Keeps stale cache disabled on the broad default frontend, including generic cache writes that use \Magento\Framework\App\Cache, such as $this->cache->save().
        block_html:
          frontend: stale_cache_enabled # This is often one of the cache types that benefits the most from stale cache, because it is heavily used and can contribute significantly to lock contention during regeneration. In most cases, it can remain enabled. Exclude it only if the project has customization-specific issues caused by stale block output.
        layout:
          frontend: stale_cache_enabled
        reflection:
          frontend: stale_cache_enabled
        config_integration:
          frontend: stale_cache_enabled
        config_integration_api:
          frontend: stale_cache_enabled
        translate:
          frontend: stale_cache_enabled
        # add other cache types as needed...

    SESSION_CONFIGURATION:
      _merge: true
      redis: # keep 'redis' even if you are using Valkey.
        # port: 6372 # ece-tools should detect the port automatically, but if not, set here.
        timeout: 5
        disable_locking: 1 # true for max performance. If racing conditions happen when the server has an excessively high number of simultaneous session activities, set it to false.
        bot_first_lifetime: 60
        bot_lifetime: 7200
        max_lifetime: 2592000
        min_lifetime: 60
```

>[!ENDTABS]

## Informazioni aggiuntive

Consulta i seguenti argomenti correlati:

- [Cache pagine Redis](../../../configuration/cache/redis-pg-cache.md)
- [Usa Redis per l’archiviazione della sessione](../../../configuration/cache/redis-session.md)
- [Usa Valkey per la cache predefinita](../../../configuration/cache/valkey-pg-cache.md)
- [Usa Valkey per l&#39;archiviazione della sessione](../../../configuration/cache/valkey-session.md)
