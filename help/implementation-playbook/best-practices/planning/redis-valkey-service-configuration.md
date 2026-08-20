---
title: Best practice per la configurazione del servizio Valkey e Redis
description: Scopri come configurare il caching Redis e Valkey per Adobe Commerce su Cloud, incluse le connessioni di replica, la cache L2, la cache non aggiornata e l’archiviazione delle sessioni.
solution: Commerce
role: Developer, Admin
level: Intermediate
feature: Best Practices, Cache
feature-set: Commerce
topic: Performance
exl-id: 8b3c9167-d2fa-4894-af45-6924eb983487
badgePaas: label="Commerce su Cloud" type="Informative" url="https://experienceleague.adobe.com/it/docs/commerce/user-guides/product-solutions" tooltip="Applicabile solo ai progetti Adobe Commerce on Cloud."
nudge: true
autotag-review: '2026-08-18T23:34:12.845Z'
TQID: 'https://experienceleague.adobe.com/kYuQylZb2r7ElWP1oRJbyIt9jsZMhoO9yFpBMDlf1tw'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
  - id: cdf0c6dd-1717-4e20-9530-a24eee57088b
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: 4266dbeca837bc62e5a76b2ef22b065a3452e088
workflow-type: tm+mt
source-wordcount: 3304
ht-degree: 0%

---


# Best practice per la configurazione del servizio Valkey e Redis

Segui questi consigli durante la configurazione di Redis o Valkey per la cache dell’applicazione Adobe Commerce, l’archiviazione della sessione e la cache L2 per le distribuzioni Adobe Commerce on Cloud.

Per la configurazione della cache locale di Adobe Commerce, vedere [Configurazione della cache L2 per l&#39;ottimizzazione delle prestazioni](/help/configuration/cache/level-two-cache.md).

>[!NOTE]
>
>Questo argomento tratta la cache dell’applicazione Commerce e i backend di sessione. Il caching HTTP a pagina intera, come Fastly o Varnish, è un livello di caching separato e viene configurato in modo indipendente. Le modifiche al back-end della cache dell’applicazione non sostituiscono o configurano la cache a pagina intera HTTP.

Tali raccomandazioni riguardano i seguenti aspetti:

- Seleziona un servizio di cache supportato
- Abilita connessione di replica
- Istanze di sessione e cache separate
- Configurare la compressione cache
- Abilita liberazione asincrona
- Abilita I/O multithread
- Aumentare i timeout e i tentativi client
- Configura la cache L2, incluse le chiavi di precaricamento, la cache non aggiornata e la cache L2 [!DNL Symfony]
- Esaminare gli esempi di configurazione

## Seleziona un servizio di cache supportato

| Versione Adobe Commerce | Servizio cache consigliato | Implementazione della cache L2 |
| ---------------------- | -------------------------- | ------------------------ |
| 2.4.8 e versioni precedenti, se supportate dalla versione esatta | Redis o Valkey | CacheSincronizzataRemota |
| 2.4.9 e versioni successive | Valkey | symfony_l2 |

Redis non è supportato per la configurazione della cache in Adobe Commerce 2.4.9 e nelle versioni patch in cui i requisiti di sistema specificano Valkey. Verifica sempre la versione esatta di Commerce, il livello di patch e la versione del servizio nelle [Opzioni di back-end cache e riferimento archiviazione](/help/configuration/cache/cache-options.md) e [Requisiti di sistema](/help/installation/system-requirements.md).

>[!NOTE]
>
>Verificare di utilizzare la versione più recente del pacchetto `ece-tools`. In caso contrario, [aggiorna alla versione più recente](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package). È possibile controllare la versione installata nell&#39;ambiente locale utilizzando il comando CLI `composer show magento/ece-tools`.

## Abilita connessione di replica

Abilitare la connessione di replica nel file `.magento.env.yaml`. Questa modifica consente ad Adobe Commerce di utilizzare una connessione cache aggiuntiva per le letture mentre si continua a utilizzare l’endpoint primario per le scritture. Questa configurazione può ridurre il carico di lettura sul servizio di cache principale e distribuire il traffico di lettura in modo più efficace.

>[!NOTE]
>
>La disponibilità di una connessione di replica dipende dalla topologia del progetto (ad esempio, nodo singolo o architettura split o HA) e dalla versione `ece-tools`. Prima di utilizzare questa impostazione, verificare che esista una relazione di replica per il servizio eseguendo `echo $MAGENTO_CLOUD_RELATIONSHIPS | base64 -d | json_pp` e verificando la presenza di una voce `USE_SLAVE_CONNECTION`. Per confermare se la topologia esegue il provisioning di un endpoint di replica, aggiornare `ece-tools` e ridistribuire oppure contattare il supporto Adobe Commerce se non è presente alcuna voce `USE_SLAVE_CONNECTION`.
>
>Per `symfony_l2`, il supporto della connessione di replica viene fornito tramite un aggiornamento di `ece-tools` e delle patch cloud. Non è richiesta alcuna configurazione della cache aggiuntiva oltre alla modifica di `VALKEY_USE_SLAVE_CONNECTION: true`. Aggiornare alla versione `ece-tools` più recente per ricevere la correzione.

>[!BEGINTABS]

>[!TAB Configurazione Valkey]

Per Valkey, utilizzare:

```yaml
stage:
  deploy:
    VALKEY_USE_SLAVE_CONNECTION: true
```

Per informazioni dettagliate sulla configurazione delle variabili di ambiente, vedere [VALKEY _USE_ SLAVE_CONNECTION](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_use_slave_connection) nella _Guida all&#39;infrastruttura cloud di Commerce_.

>[!TAB Configurazione Redis]

Per Redis, utilizzare:

```yaml
stage:
  deploy:
    REDIS_USE_SLAVE_CONNECTION: true
```

Per informazioni dettagliate sulla configurazione delle variabili di ambiente, vedere [REDIS _USE_ SLAVE_CONNECTION](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#redis_use_slave_connection) nella _Guida all&#39;infrastruttura cloud di Commerce_.

>[!ENDTABS]

## Istanze di sessione e cache separate

La configurazione della cache e della sessione è indipendente. `SESSION_CONFIGURATION` non influisce sul comportamento della cache, indipendentemente dal back-end della cache o dall&#39;implementazione della cache L2 utilizzata. La separazione della cache dalle sessioni consente di gestirle in modo indipendente. Riduce il conflitto tra la cache e il traffico di sessione, evita che la pressione relativa alla cache influisca sulle sessioni e consente di ridimensionare e regolare ogni istanza Redis o Valkey per il proprio carico di lavoro.

>[!IMPORTANT]
>
>Il provisioning di un’istanza di sessione dedicata in Produzione e Staging non è self-service. Richiede l&#39;invio di un [ticket di supporto Adobe Commerce](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) con i file `.magento/services.yaml` e `.magento.app.yaml` aggiornati, come descritto nel passaggio 3 seguente.

Per eseguire il provisioning di un’istanza dedicata per le sessioni, segui i passaggi seguenti:

>[!BEGINTABS]

>[!TAB Chiave Valvola]

1. Aggiornare il file di configurazione `.magento/services.yaml`, sostituendo `<version>` con le versioni del servizio in uso. Consulta [Requisiti di sistema](/help/installation/system-requirements.md) per le versioni dei servizi supportate in base alla versione.

   ```yaml
   mysql:
     type: mysql:<version>
     disk: 35000
   
   valkey:
     type: valkey:<version>
   
   valkey-session: # This is for the new Valkey instance
     type: valkey:<version>
   
   search:
     type: elasticsearch:<version>
     disk: 5000
   
   rabbitmq:
     type: rabbitmq:<version>
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

   Invia un [ticket di supporto Adobe Commerce](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket). Includere i file di configurazione `.magento/services.yaml` e `.magento.app.yaml` aggiornati.

   Questo aggiornamento non causa tempi di inattività, ma richiede una distribuzione per attivare il nuovo servizio.

1. Verifica che la nuova istanza sia in esecuzione e annota il numero della porta.

   ```shell
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

1. Rimuovere le sessioni dal [database predefinito](/help/configuration/cache/redis-pg-cache.md) (`db 0`) nell&#39;istanza della cache di Valkey.

   ```terminal
   valkey-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!TAB Redis]

1. Aggiornare il file di configurazione `.magento/services.yaml`, sostituendo `<version>` con le versioni del servizio in uso.

   ```yaml
   mysql:
     type: mysql:<version>
     disk: 35000
   
   redis:
     type: redis:<version>
   
   redis-session: # This is for the new Redis instance
     type: redis:<version>
   
   search:
     type: elasticsearch:<version>
     disk: 5000
   
   rabbitmq:
     type: rabbitmq:<version>
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

   Invia un [ticket di supporto Adobe Commerce](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket). Includere i file di configurazione `.magento/services.yaml` e `.magento.app.yaml` aggiornati.

   Questo aggiornamento non causa tempi di inattività, ma richiede una distribuzione per attivare il nuovo servizio.

1. Verifica che la nuova istanza sia in esecuzione e annota il numero della porta.

   ```shell
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

1. Rimuovere le sessioni dal [database predefinito](/help/configuration/cache/redis-pg-cache.md) (`db 0`) nell&#39;istanza della cache Redis.

   ```terminal
   redis-cli -h 127.0.0.1 -p 6370 -n 0 FLUSHDB
   ```

>[!ENDTABS]

## Compressione cache

Se si utilizzano più di 6 GB di Redis o Valkey `maxmemory`, è possibile abilitare la compressione della cache per ridurre lo spazio utilizzato dalle chiavi. Tieni presente che questa impostazione consente di valutare le prestazioni lato client per risparmiare memoria. Se disponi di una capacità CPU di riserva, puoi attivarla. Vedere [Utilizzare Redis per l&#39;archiviazione della sessione](/help/configuration/cache/redis-session.md) o [Utilizzare Valkey per l&#39;archiviazione della sessione](/help/configuration/cache/valkey-session.md) nella _Guida alla configurazione_.

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

Per abilitare `lazyfree` nell&#39;infrastruttura cloud Adobe Commerce, invia un [ticket di supporto Adobe Commerce](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) richiedendo che la seguente configurazione Redis o Valkey venga applicata agli ambienti:

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

Per abilitare il threading di I/O Redis sull&#39;infrastruttura cloud Adobe Commerce, invia un [ticket di supporto Adobe Commerce](https://experienceleague.adobe.com/it/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide#submit-ticket) richiedendo la configurazione del threading di I/O seguente. Questa configurazione può migliorare il throughput scaricando le letture, le scritture e l&#39;analisi dei comandi del socket dal thread principale, al costo di un maggiore utilizzo di CPU. Convalida sotto carico e monitora gli host.

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

## Configurare la cache L2

Configurare la cache L2 impostando la variabile di distribuzione `VALKEY_BACKEND` o `REDIS_BACKEND` nel file di configurazione `.magento.env.yaml`.

Sono disponibili due implementazioni di cache L2 per Adobe Commerce sull’infrastruttura cloud.

- L&#39;implementazione legacy utilizza `RemoteSynchronizedCache` con `Cm_Cache_Backend_File` per l&#39;archiviazione locale
- L&#39;implementazione moderna utilizza `symfony_l2` con conformità PSR-6 e prestazioni migliorate. L’implementazione moderna supporta solo Valkey.

| Versione Commerce | RemoteSynchronizedCache con Valkey | Configurazione consigliata |
| -------------- | ----------------------------------- | ------------------------- |
| 2.4.8 e versioni precedenti<br>(se Valkey è supportato) | Percorso L2 legacy supportato | `VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'` |
| 2.4.9 e versioni successive | Non supportato | `VALKEY_BACKEND: 'symfony_l2'` |

>[!IMPORTANT]
>
>La cache Redis non è supportata per Adobe Commerce 2.4.9 o per versioni patch successive a 2.4.5-p16, 2.4.6-p14, 2.4.7-p9 e 2.4.8-p4. Utilizza Valkey per la configurazione della cache quando Redis non è supportato. Consulta [Requisiti di sistema](/help/installation/system-requirements.md) per i servizi di cache supportati per versione.

>[!BEGINTABS]

>[!TAB Configurazione Valkey]

In Commerce 2.4.8 e versioni precedenti che supportano Valkey, utilizza questa configurazione:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

In Commerce 2.4.9 e versioni successive, utilizzare la seguente configurazione con l&#39;implementazione L2 di [!DNL Symfony]:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: 'symfony_l2'
```

>[!TAB Configurazione Redis]

Nella versione 2.4.8 e nelle versioni precedenti di Commerce che supportano Redis, utilizza:

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\RemoteSynchronizedCache'
```

Per informazioni dettagliate sulla configurazione dell&#39;ambiente, vedere [`REDIS_BACKEND`](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#redis_backend) nella _Guida di Commerce sull&#39;infrastruttura cloud_.

>[!ENDTABS]

### Esegui migrazione a Valkey con cache L2 [!DNL Symfony]

Se stai eseguendo la migrazione di un progetto Adobe Commerce on Cloud esistente da `RemoteSynchronizedCache` (Redis o Valkey) a `symfony_l2`, controlla quanto segue prima di aggiornare `.magento.env.yaml`.

- **La modifica della variabile di distribuzione è sufficiente per abilitare `symfony_l2`.** Se si imposta `VALKEY_BACKEND: symfony_l2` da solo, viene automaticamente generata la configurazione completa della cache L2. Non è necessario ricreare manualmente la struttura `backend_options` utilizzata nella configurazione `RemoteSynchronizedCache` precedente. Vedi [Configura [!DNL Symfony] cache L2](#configure-symfony-l2-cache).

- **Rimuovi `preload_keys` dalla configurazione esistente.** Se la configurazione di `RemoteSynchronizedCache` include `preload_keys` in `CACHE_CONFIGURATION`, rimuoverla come parte della migrazione. Per ulteriori dettagli, vedere [Chiavi di precaricamento](#preload-keys).

- **Il comportamento della cache non aggiornata viene modificato automaticamente.** In `symfony_l2`, `ece-tools` abilita automaticamente la cache non aggiornata per i tipi di cache comuni (ad esempio `layout`, `block_html`, `full_page` e `translate`) senza richiedere la configurazione front-end manuale necessaria per `RemoteSynchronizedCache`. Se in precedenza era stata configurata manualmente una cache non aggiornata e si desidera mantenere il comportamento precedente esatto, rivedere [Abilita cache non aggiornata](#enable-stale-cache) prima di eseguire la migrazione.

- **La compressione richiede un flag esplicito.** Se si personalizza la compressione `symfony_l2` tramite `CACHE_CONFIGURATION`, la sola impostazione di `compression_lib` non consente la compressione. È necessario impostare anche `compress_data`. Vedere [Compressione cache](#cache-compression).

- **Redis non è un back-end remoto supportato per `symfony_l2`.** Esegui la migrazione a Valkey come parte di questa modifica. Vedere [Configurazione del servizio Valkey](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/configure/service/valkey).

- **La configurazione della sessione non è interessata da questa migrazione.** `SESSION_CONFIGURATION` è indipendente dal backend della cache e non deve essere modificato quando si passa a `symfony_l2`. Vedi [Istanze di sessione e cache separate](#separate-cache-and-session-instances).

>[!IMPORTANT]
>
>Non configurare `symfony_l2` manualmente in `app/etc/env.php`. Configurarlo tramite `.magento.env.yaml` in modo che `ece-tools` applichi e mantenga l&#39;impostazione durante la distribuzione. Vedi [Configura [!DNL Symfony] cache L2](#configure-symfony-l2-cache).

### Precarica chiavi

Le chiavi di precaricamento possono essere applicate a una configurazione `symfony_l2` se si utilizza il posizionamento corretto (in `backend_options` o `remote_backend_options`). Tuttavia, Adobe sconsiglia di utilizzare le chiavi di precaricamento con `symfony_l2`. L&#39;implementazione di precaricamento di `symfony_l2` recupera le chiavi una alla volta, quindi non riduce i round trip come avviene per `RemoteSynchronizedCache` e può aumentare il carico su Valkey senza un vantaggio di prestazioni.

La funzione di precaricamento ti consente di fornire un elenco di chiavi utilizzate di frequente che Magento recupera in una singola pipeline al primo accesso durante una richiesta. Magento mantiene quindi i valori recuperati nella memoria PHP per il resto di tale richiesta, riducendo i round trip ripetuti a Redis o Valkey e migliorando le prestazioni di bootstrap delle richieste per tali chiavi.

Puoi identificare le chiavi utilizzate di frequente monitorando i comandi attivi su Redis o Valkey:

Le chiavi di precaricamento sono configurate nel file di configurazione `.magento.env.yaml`. Questo esempio mostra la configurazione per Adobe Commerce 2.4.8 e versioni precedenti che supportano `RemoteSynchronizedCache`.

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

Dopo 10 secondi, premere **Ctrl+C**. Quindi esegui il seguente comando:

```terminal
cat /tmp/list.keys | grep "HGET" | awk '{print $5}' | sort | uniq -c | sort -nr | head -n 50
```

In questo registro sono elencate le chiavi che è possibile precaricare. Per visualizzare il contenuto di una chiave, eseguire il comando seguente:

```terminal
redis-cli -p 6370 -n 1 hgetall "<key_name>"
```

### Abilita cache non aggiornata

La cache non aggiornata è una funzione della cache L2 che consente ad Adobe Commerce di distribuire un valore della cache locale esistente da `/dev/shm` mentre un&#39;altra richiesta sta già rigenerando la stessa voce. Questo impedisce l’attesa di richieste simultanee. Questo riduce gli stamp della cache e i conflitti di blocco durante la rigenerazione di voci costose della cache.

Per Adobe Commerce 2.4.9 e versioni successive, impostare `VALKEY_BACKEND: symfony_l2` nel file `.magento.env.yaml`:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: symfony_l2
```

`ece-tools` genera automaticamente sia un front-end `default` che un front-end `stale_cache_enabled` e mappa i seguenti tipi di cache al front-end non aggiornato: `layout`, `block_html`, `reflection`, `config_integration`, `config_integration_api`, `full_page` e `translate`. Per questi tipi non è richiesta alcuna configurazione manuale `use_stale_cache` o front-end. Questa mappatura automatica è di per sé un esempio di abilitazione selettiva della cache non aggiornata. Solo tipi di cache specifici utilizzano il front-end abilitato non aggiornato, non tutti. Per personalizzare i tipi mappati a `stale_cache_enabled` o per aggiungere tipi oltre i valori predefiniti, vedere [Personalizzare la [!DNL Symfony] configurazione cache L2](#customize-the-symfony-l2-cache-configuration).

>[!NOTE]
>
>Il tipo di cache `full_page` non è rilevante per i progetti di infrastruttura Adobe Commerce on Cloud perché utilizza Fastly per il caching a pagina intera. Gli esempi di configurazione manuale in questa sezione omettono `full_page` per questo motivo, anche se `ece-tools` lo include nel mapping predefinito di `symfony_l2`.

La seguente configurazione legacy si applica ad Adobe Commerce 2.4.8 e versioni precedenti, che utilizzano `RemoteSynchronizedCache` e richiedono una configurazione manuale di cache non aggiornata e front-end. In questo caso si applica la stessa raccomandazione selettiva rispetto a quella globale.

#### Funzionamento del back-end legacy RemoteSynchronizedCache

Con `RemoteSynchronizedCache`, Magento mantiene due copie di ogni voce della cache: una copia locale in `/dev/shm` e una copia remota in Redis o Valkey. Quando la copia remota non è disponibile ed esiste già un blocco di rigenerazione per tale chiave, le richieste simultanee possono ricevere il valore locale precedente invece di attendere che venga scritto il nuovo valore.

Per abilitare la cache non aggiornata per le versioni 2.4.8 e precedenti, configurarla nel file `.magento.env.yaml`.

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

>[!WARNING]
>
>La configurazione precedente abilita la cache non aggiornata nel front-end della cache `default`, che applica il comportamento di cache non aggiornata a tutte le voci della cache che utilizzano tale front-end. I tipi di cache di base di Magento funzionano come previsto con questa impostazione. Tuttavia, se il progetto include codice personalizzato o estensioni che scrivono nella cache tramite l&#39;API generica `\Magento\Framework\App\Cache` (ad esempio `$this->cache->save()`) senza una cache front-end dedicata, tali voci possono anche fornire valori non aggiornati durante la rigenerazione.
>
>
>Se si verifica un comportamento imprevisto nelle personalizzazioni, lasciare disabilitata la cache non aggiornata sul front-end `default` e abilitarla solo per i tipi di cache selezionati, come illustrato di seguito.

#### Abilita cache non aggiornata singolarmente per tipo di cache (legacy)

È possibile abilitare una cache non aggiornata solo per i tipi di cache selezionati definendo una cache front-end dedicata in `.magento.env.yaml` e mappando i tipi di cache selezionati. Questo approccio manuale si applica al backend legacy `RemoteSynchronizedCache`; `symfony_l2` esegue automaticamente questa mappatura, come descritto in precedenza.

Per funzionare correttamente, il front-end personalizzato deve essere definito come front-end completo in `CACHE_CONFIGURATION.frontend`. Non è sufficiente definire solo `use_stale_cache: true` per un nuovo nome front-end.

**Configurazioni di esempio**

Per Redis nelle versioni 2.4.8 e precedenti, la seguente configurazione abilita una cache non aggiornata per i tipi di cache `layout`, `reflection`, `config_integration`, `config_integration_api` e `translate`, lasciando ad altri utenti l&#39;utilizzo del front-end predefinito con cache non aggiornata disabilitata:

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

>[!NOTE]
>
>Se il front-end di origine è configurato con opzioni di back-end aggiuntive, copiarle in `stale_cache_enabled` in modo che il nuovo front-end mantenga lo stesso comportamento.

### Configura cache L2 di [!DNL Symfony]

Adobe Commerce 2.4.9 e versioni successive supportano il back-end della cache `symfony_l2`. Il backend `symfony_l2` è l&#39;implementazione della cache che Adobe Commerce utilizza per gestire il comportamento della cache L1 e L2. **Non sostituisce Redis o Valkey come servizio cache remota.**

>[!IMPORTANT]
>
>Configura `symfony_l2` tramite la variabile di distribuzione `.magento.env.yaml` in modo che `ece-tools` applichi e mantenga l&#39;impostazione durante la distribuzione. Non configurare `symfony_l2` manualmente in `app/etc/env.php`, perché la distribuzione può sovrascrivere le `env.php` modifiche manuali. Se `ece-tools` non applica `symfony_l2`, Commerce può eseguire il fallback alla cache basata su file, il che può aumentare l&#39;I/O del disco, aggiungere il sovraccarico di replica del file system in ambienti a più nodi e ridurre le prestazioni.

Per utilizzare la cache `symfony_l2` per Adobe Commerce 2.4.9, completare i passaggi seguenti:

- Verificare che il progetto cloud utilizzi il pacchetto [`ece-tools` v2002.2.12](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/dev-tools/ece-tools/update-package) o versione successiva.

- Impostare la variabile di distribuzione nel file `.magento.env.yaml`: `VALKEY_BACKEND`=`symfony_l2`.

  ```yaml
  stage:
    deploy:
      VALKEY_BACKEND: symfony_l2
  ```

L&#39;impostazione della variabile di distribuzione `VALKEY_BACKEND` su `symfony_l2` genera automaticamente la configurazione completa della cache L2 dai dettagli di connessione al servizio Valkey, inclusi i front-end `default` e `stale_cache_enabled`, con tipi di cache comuni già mappati. La definizione di `CACHE_CONFIGURATION` è facoltativa e necessaria solo se si desidera personalizzare opzioni di back-end specifiche.

>[!NOTE]
>
>La patch ACP2E-5132 per Adobe Commerce 2.4.9 migliora le prestazioni e l&#39;affidabilità della cache L2 di [!DNL Symfony] ottimizzando l&#39;archiviazione dei tag, aggiungendo un blocco di rigenerazione della cache non aggiornata e risolvendo i problemi relativi alle appartenenze ai tag non aggiornati, alle scritture remote ridondanti e all&#39;eliminazione basata sulle dimensioni L1 (`cleanup_percentage`). Ciò riduce l&#39;I/O del disco e il carico di back-end, migliorando la coerenza della cache. Consulta [Prestazioni e affidabilità migliorate della cache L2 di Symfony](/help/configuration/cache/level-two-cache.md#enhanced-symfony-l2-cache-performance-and-reliability) nella _Guida alla configurazione di Adobe Commerce_.
>
>La patch è inclusa nel pacchetto [Patch cloud per Commerce](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches) (una dipendenza di `ece-tools`) e viene applicata automaticamente durante la distribuzione quando si esegue l&#39;aggiornamento alla versione `ece-tools` più recente. Aggiornare alla versione più recente di `ece-tools` per ricevere la patch.

#### Personalizza la configurazione della cache L2 di [!DNL Symfony]

`ece-tools` deriva automaticamente i dettagli della connessione Valkey (`server`, `port`, `database`, `serializer`, `compression_lib`, `persistent_id`) per i front-end `default` e `stale_cache_enabled`. Per personalizzare altre opzioni di back-end, ad esempio la directory della cache locale, definire `CACHE_CONFIGURATION` con `_merge: true` insieme a `VALKEY_BACKEND: symfony_l2`. I valori definiti in questo campo sostituiscono i valori predefiniti generati automaticamente corrispondenti. Qualsiasi opzione omessa continua a utilizzare i valori derivati automaticamente da `ece-tools`.

```yaml
stage:
  deploy:
    VALKEY_BACKEND: symfony_l2
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            remote_backend: valkey
            local_backend: file
            local_backend_options:
              cache_dir: /dev/shm/magento_l1
        stale_cache_enabled:
          backend: symfony_l2
          backend_options:
            remote_backend: valkey
            local_backend: file
            local_backend_options:
              cache_dir: /dev/shm/magento_l1_stale
            use_stale_cache: true
```

>[!CAUTION]
>
>Durante la definizione di `CACHE_CONFIGURATION` per `symfony_l2`, eseguire l&#39;override di `server` o `port` solo se si punta intenzionalmente a un endpoint della cache diverso dal servizio Valkey del progetto. Il pacchetto `ece-tools` deriva automaticamente questi valori dalla relazione del servizio Valkey.
>
>Se si esegue l&#39;override di `server`, il relativo valore deve essere `localhost` durante la connessione al servizio Valkey del progetto. Se si specifica un valore `server` o `port` non corretto, la distribuzione non riesce e viene generato un errore di connessione alla cache.

### Dimensioni della memoria cache L2 per Adobe Commerce Cloud

La cache L2 utilizza un [file system temporaneo](https://en.wikipedia.org/wiki/Tmpfs) (`/dev/shm`) come meccanismo di archiviazione. A differenza degli archivi specializzati di valori chiave, i tmpfs non dispongono di criteri di rimozione delle chiavi, pertanto l&#39;utilizzo della memoria può crescere senza limiti. Per evitare l’esaurimento, Adobe Commerce cancella automaticamente lo storage L2 quando l’utilizzo raggiunge una soglia configurabile (95% per impostazione predefinita). È possibile controllare il consumo di memoria richiedendo un montaggio `/dev/shm` più grande o abbassando la soglia di pulizia.

Regola l’utilizzo massimo della memoria cache L2 in base ai requisiti del progetto. Utilizza uno dei seguenti metodi:

- Per regolare la dimensione di montaggio `/dev/shm`, creare un ticket di supporto. Per questo scenario, Adobe consiglia di impostare la dimensione di montaggio `/dev/shm` su 15 GB.
- Regolare la proprietà `cleanup_percentage` a livello di applicazione per limitare l&#39;utilizzo dello spazio di archiviazione e della memoria disponibile per altri servizi.
È possibile modificare la configurazione nella configurazione di distribuzione nel gruppo di configurazione della cache `cache/frontend/default/backend_options/cleanup_percentage`.

>[!NOTE]
>
>L&#39;opzione configurabile `cleanup_percentage` è stata introdotta in Adobe Commerce 2.4.4.

Gli esempi seguenti mostrano il codice di configurazione nel file `.magento.env.yaml`:

>[!BEGINTABS]

>[!TAB Configurazione Valkey]

Per Commerce 2.4.9 e versioni successive, utilizza la seguente configurazione per impostare la soglia di pulizia su 90%:

```yaml
stage:
  deploy:
    VALKEY_BACKEND: symfony_l2
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          backend_options:
            cleanup_percentage: 90
```

>[!TAB Configurazione Redis]

Per Commerce 2.4.8 e versioni precedenti, utilizza la seguente configurazione per impostare la soglia di pulizia su 90%:

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

>[!ENDTABS]

I requisiti della cache dipendono dalla configurazione del progetto e dal codice personalizzato di terze parti. Dimensione della memoria cache L2 in modo che la cache possa funzionare senza frequenti hit di soglia.

Idealmente, l&#39;utilizzo della memoria cache L2 si stabilizza al di sotto della soglia per evitare frequenti cancellazioni dello storage.

È possibile verificare l&#39;utilizzo della memoria di archiviazione nella cache L2 in ogni nodo del cluster eseguendo il seguente comando CLI e rivedendo la riga `/dev/shm`.

```shell
df -h /dev/shm
```

L’utilizzo varia tra i nodi, ma converge in un valore simile.

## Esempi di configurazione

Utilizza gli esempi seguenti come punto di partenza per le configurazioni del servizio Redis o Valkey.


### Applica tutte le raccomandazioni sulle best practice

>[!BEGINTABS]

>[!TAB Esempio di configurazione Valkey]

Per `VALKEY_BACKEND: symfony_l2`, lasciare che `ece-tools` generi i front-end `default` e `stale_cache_enabled` e i relativi mapping di tipo cache. Non impostare `use_stale_cache` sul front-end `default` esteso. Il blocco `CACHE_CONFIGURATION` di seguito contiene solo sostituzioni esplicite dell&#39;opzione di back-end.

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables read-only replica connection logic in Magento. It also works in a split architecture.
    VALKEY_BACKEND: symfony_l2 # Use symfony_l2 for Adobe Commerce 2.4.9 and later
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default:
          id_prefix: '001_' # any prefix is fine, but keep it consistent.
          backend_options:
            connect_retries: 3                # Number of connection retries
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

>[!TAB Esempio di configurazione Redis]

Utilizza la seguente configurazione per Redis su Adobe Commerce 2.4.8 e versioni precedenti:

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables read-only replica connection logic in Magento. It also works in a split architecture
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

>[!ENDTABS]

### Separa cache non aggiornata per tipo di cache

>[!BEGINTABS]

>[!TAB Chiave Valvola]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    VALKEY_USE_SLAVE_CONNECTION: true # Enables read-only replica connection logic in Magento. It also works in a split architecture
    VALKEY_BACKEND: symfony_l2 # Use symfony_l2 for Adobe Commerce 2.4.9 and later
    CACHE_CONFIGURATION:
      _merge: true
      frontend:
        default: # Keep stale cache disabled on the broad default frontend.
          id_prefix: '001_' # Keep this prefix consistent with the frontend configuration generated in env.php
          backend_options:
            connect_retries: 3
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
          backend: symfony_l2
          backend_options:
            remote_backend: valkey
            remote_backend_options:
              server: localhost
              port: 6370   # Use the same port used by the source frontend in env.php
              database: 1
              load_from_slave:
                server: localhost
                port: 26370 # Use the same read-only replica connection/read port used by the source frontend in env.php
              retry_reads_on_master: 1
              read_timeout: 10
            local_backend: file
            local_backend_options:
              cache_dir: /dev/shm/
            use_stale_cache: true
            connect_retries: 3
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

>[!TAB Redis]

```yaml
stage:
  deploy:
    MYSQL_USE_SLAVE_CONNECTION: true
    REDIS_USE_SLAVE_CONNECTION: true # Enables read-only replica connection logic in Magento. It also works in a split architecture
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
                port: 26370 # Use the same read-only replica connection/read port used by the source frontend in env.php
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

>[!ENDTABS]

>[!MORELIKETHIS]
>
>- [Configura servizio Valkey](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/configure/service/valkey)
>- [Configurazione del servizio Redis](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/configure/service/redis)
>- [Distribuisci variabili](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy)
