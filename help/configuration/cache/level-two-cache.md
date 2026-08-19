---
title: Configurazione cache L2 per l'ottimizzazione delle prestazioni
description: Scopri come configurare la cache L2 in Adobe Commerce per ridurre il traffico di rete e migliorare le prestazioni. Scopri le opzioni di implementazione legacy e Symfony.
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
badgePaas: label="On-Premises" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Applicabile solo ai progetti Adobe Commerce on Premises."
TQID: 'https://experienceleague.adobe.com/7vswBqyn9UZLmaeirgPRZ4xEQH5F66XUEtY5hPkz9NY'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
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
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
source-git-commit: 7ebadd26eee51aa2c2f3dfe8a8a2ed3dc20657b9
workflow-type: tm+mt
source-wordcount: 1725
ht-degree: 0%

---

# Configurazione della cache L2 per l&#39;ottimizzazione delle prestazioni

La memorizzazione nella cache L2 (a due livelli) riduce il traffico di rete tra lo storage della cache remota (Redis o Valkey) e l&#39;applicazione Commerce aggiungendo un livello di cache locale su ciascun nodo web. Un’istanza Commerce standard trasferisce circa 300 KB per richiesta e in alcune situazioni il traffico può superare rapidamente le 1000 richieste.

Con il caching L2, ogni nodo web memorizza localmente i dati a cui si accede di frequente e utilizza la cache remota per due scopi:

- Verifica della versione dei dati della cache per verificare che la cache più recente sia memorizzata localmente
- Trasferimento dei dati della cache aggiornati dall&#39;archivio remoto al computer locale

Commerce memorizza la versione con hash dei dati nella cache remota, aggiungendo il suffisso `:hash` alla chiave regolare. Quando la cache locale non è aggiornata, i dati vengono recuperati dal computer remoto tramite un adattatore cache.

In Adobe Commerce sono disponibili due implementazioni di cache L2:

| Implementazione | Versione | Descrizione |
| -------------- | ------- | ----------- |
| [Legacy (`RemoteSynchronizedCache`)](#legacy-l2-cache-configuration-remotesynchronizedcache) | &lt;2.4.9 | Cache a due livelli basata su Zend con `Cm_Cache_Backend_File` per l&#39;archiviazione locale |
| [Moderno (`symfony_l2`)](#modern-symfony-l2-cache-implementation) | 2.4.9+ | L2 basato su Symfony Cache con conformità PSR-6 e prestazioni migliorate. Supporta Valkey. |

La cache L2 di Symfony è l’implementazione consigliata per Adobe Commerce 2.4.9 e versioni successive. Fornisce un&#39;implementazione di caching moderna e conforme a PSR-6 con miglioramenti significativi delle prestazioni rispetto al tradizionale `RemoteSynchronizedCache`.

## Configurazione cache L2 legacy (RemoteSynchronizedCache)

Le istruzioni di configurazione della cache L2 legacy si applicano alle versioni precedenti di Adobe Commerce. Se utilizzi Adobe Commerce versione 2.4.9 o successiva, utilizza Valkey con [implementazione della cache L2 Modern Symfony](#modern-symfony-l2-cache-implementation).

>[!NOTE]
>
>Questa pagina tratta solo la configurazione locale. Per Adobe Commerce on Cloud, consulta [Configurare la cache L2](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-l2-cache).

Per le versioni locali di Adobe Commerce che supportano Redis, utilizzare l&#39;esempio seguente per modificare o sostituire la sezione cache esistente nel file `app/etc/env.php`.

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
            'backend_options' => [
                'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                'remote_backend_options' => [
                    'persistent' => 0,
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                ],
                'local_backend' => 'Cm_Cache_Backend_File',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/'
                ]
            ],
            'frontend_options' => [
                'write_control' => false,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
    ],
]
```

Dove:

- `backend` è l&#39;implementazione della cache L2.
- `backend_options` è la configurazione della cache L2.
  - `remote_backend` è l&#39;implementazione della cache remota: Redis o MySQL.
  - `remote_backend_options` è la configurazione della cache remota.
  - `local_backend` è l&#39;implementazione della cache locale: `Cm_Cache_Backend_File`.
  - `local_backend_options` è la configurazione della cache locale.
  - `cache_dir` è un&#39;opzione specifica della cache del file per la directory in cui è memorizzata la cache locale.

Per le versioni di Adobe Commerce precedenti alla 2.4.9 che supportano Redis, Adobe consiglia di utilizzare Redis per il caching remoto (`\Magento\Framework\Cache\Backend\Redis`) e `Cm_Cache_Backend_File` per il caching locale dei dati nella memoria condivisa, utilizzando: `'local_backend_options' => ['cache_dir' => '/dev/shm/']`.

Adobe consiglia di utilizzare la funzionalità [`cache preload`](redis-pg-cache.md#redis-preload-feature), in quanto riduce drasticamente la pressione su Redis. Non dimenticare di aggiungere il suffisso `:hash` per le chiavi di precaricamento.

## Opzioni cache non aggiornate

A partire da Commerce 2.4, l&#39;opzione `use_stale_cache` può migliorare le prestazioni in casi specifici fornendo i dati precedentemente memorizzati nella cache mentre i nuovi dati della cache vengono generati in un processo parallelo. I tipi di cache consigliati e i compromessi descritti in questa sezione si applicano sia alle implementazioni legacy `RemoteSynchronizedCache` che a quelle legacy `symfony_l2`. Per un esempio di configurazione di `symfony_l2`, vedere [Cache L2 Symfony con cache non aggiornata](#symfony-l2-cache-with-stale-cache).

In genere, il compromesso con l’attesa di blocco è accettabile dal punto di vista delle prestazioni. Tuttavia, con l’aumento del numero di blocchi o voci della cache, le attese dei blocchi richiedono più tempo. In alcuni scenari, l&#39;attesa può essere pari a **il numero di chiavi** x **timeout ricerca** per il processo. In rari casi, un commerciante può avere centinaia di chiavi nella cache `Block/Config`, quindi anche un piccolo timeout di ricerca per un blocco può costare secondi.

>[!IMPORTANT]
>
>La cache non aggiornata funziona solo con la cache L2. Per abilitarlo, aggiungere `'use_stale_cache' => true` alla configurazione di livello superiore del front-end della cache L2.

Adobe consiglia di abilitare l&#39;opzione `use_stale_cache` solo per i tipi di cache che ne beneficiano maggiormente, tra cui:

- `block_html`
- `config_integration_api`
- `config_integration`
- `full_page`
- `layout`
- `reflection`
- `translate`

Adobe sconsiglia di abilitare l&#39;opzione `use_stale_cache` per il tipo di cache `default`.

Il codice seguente mostra un esempio di configurazione per il backend legacy `RemoteSynchronizedCache`. Per un esempio di `symfony_l2`, vedere [Cache L2 Symfony con cache non aggiornata](#symfony-l2-cache-with-stale-cache).

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
            'backend_options' => [
                'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                'remote_backend_options' => [
                    'persistent' => 0,
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                ],
                'local_backend' => 'Cm_Cache_Backend_File',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/'
                ]
            ],
            'frontend_options' => [
                'write_control' => false,
            ],
        ],
         'stale_cache_enabled' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\RemoteSynchronizedCache',
            'backend_options' => [
                'remote_backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
                'remote_backend_options' => [
                    'persistent' => 0,
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                ],
                'local_backend' => 'Cm_Cache_Backend_File',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/'
                ],
                'use_stale_cache' => true,
            ],
            'frontend_options' => [
                'write_control' => false,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
        'layout' => ['frontend' => 'stale_cache_enabled'],
        'block_html' => ['frontend' => 'stale_cache_enabled'],
        'reflection' => ['frontend' => 'stale_cache_enabled'],
        'config_integration' => ['frontend' => 'stale_cache_enabled'],
        'config_integration_api' => ['frontend' => 'stale_cache_enabled'],
        'full_page' => ['frontend' => 'stale_cache_enabled'],
        'translate' => ['frontend' => 'stale_cache_enabled']
    ],
],
```

## Implementazione moderna della cache L2 di Symfony

Nelle versioni di Commerce 2.4.9+, utilizzare l&#39;implementazione della cache L2 basata su Symfony Cache (`symfony_l2` backend) invece della cache L2 legacy. La cache L2 di Symfony fornisce un&#39;implementazione di caching moderna e conforme a PSR-6 con miglioramenti significativi delle prestazioni rispetto alla tradizionale `RemoteSynchronizedCache`.

>[!IMPORTANT]
>
>Redis non è supportato come back-end di cache remota che inizia con:
>
>- Adobe Commerce 2.4.9 e versioni successive
>- 2.4.8-p4 e versioni successive
>- 2.4.7-p9 e versioni successive
>- 2.4.6-p14 e versioni successive
>- 2.4.5-p16 e versioni successive
>
>Se stai eseguendo l&#39;aggiornamento oltre queste versioni, configura Valkey e aggiorna la configurazione della cache per utilizzare `symfony_l2`. Vedere [configurazione di Valkey](config-valkey.md) e [Requisiti di sistema](../../installation/system-requirements.md).

### Vantaggi della cache L2 di Symfony

- **Architettura moderna:** basata sui componenti della cache di Symfony (conforme a PSR-6)
- **Prestazioni migliori:** supporto nativo per la serializzazione Igbinary, la compressione Gzip e gli script Lua
- **Connessioni persistenti:** riduce il sovraccarico della connessione Valkey con il connection pooling
- **Chiavi di precaricamento:** supporta il precaricamento della chiave della cache per i dati critici
- **Supporto cache non aggiornata:** piena compatibilità con l&#39;opzione `use_stale_cache`
- **Configurazione semplificata:** nomi dei tipi di back-end di pulizia (`valkey`, `file`)

### Migrazione da RemoteSynchronizedCache a Symfony L2

Se si sta aggiornando un&#39;installazione locale dal back-end legacy `RemoteSynchronizedCache` a `symfony_l2`, controllare quanto segue prima di aggiornare `app/etc/env.php`. La modifica solo del valore `backend` non è sufficiente. La struttura della configurazione, i nomi delle chiavi e alcuni comportamenti predefiniti sono diversi.

- **La struttura della configurazione cambia.** `remote_backend`, `remote_backend_options` e `local_backend` utilizzano valori diversi in `symfony_l2`. Ad esempio, `remote_backend` diventa `'valkey'` invece del nome completo della classe. Utilizza l&#39;[esempio di configurazione](#configuration-example-with-symfony-l2-cache) di seguito come punto di partenza, anziché modificare la configurazione legacy esistente.

- **`preload_keys`non è consigliato con `symfony_l2`.** Se la configurazione legacy include `preload_keys`, rimuoverlo come parte della migrazione. Il precaricamento delle chiavi non migliora le prestazioni in `symfony_l2` e può aumentare il carico su Valkey attivando ulteriori ricerche di chiavi non necessarie.

- **La compressione richiede un flag esplicito.** L&#39;impostazione di `compression_lib` da sola non abilita la compressione in `symfony_l2`. Vedere [Opzioni di back-end per la cache L2 di Symfony](#backend-options-for-symfony-l2-cache) per l&#39;impostazione `compress_data` richiesta.

- **Per impostazione predefinita, la cache non aggiornata non è abilitata per le distribuzioni locali configurate manualmente.** `use_stale_cache` utilizza `false` come impostazione predefinita in `symfony_l2` (vedi la [tabella delle opzioni di back-end](#backend-options-for-symfony-l2-cache)). Se la configurazione precedente ha utilizzato il front-end `stale_cache_enabled`, è necessario ricrearlo in modo esplicito utilizzando il modello nella cache L2 di [Symfony con cache non aggiornata](#symfony-l2-cache-with-stale-cache).

>[!NOTE]
>
>Adobe Commerce sugli ambienti cloud che impostano la variabile di distribuzione `VALKEY_BACKEND: symfony_l2` dispongono di una configurazione L2 completa, incluso il front-end `stale_cache_enabled`, generata automaticamente da `ece-tools`. Consulta [Configurare la cache L2 di Symfony](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-symfony-l2-cache) per il comportamento specifico di Cloud.

- **Redis non è un back-end remoto supportato per `symfony_l2`.** Esegui la migrazione a Valkey come parte di questa modifica. Vedere [configurare Valkey](config-valkey.md).

### Esempio di configurazione con cache L2 Symfony

>[!NOTE]
>
>Questo esempio è per la configurazione locale di `app/etc/env.php`. Per Adobe Commerce on Cloud, la configurazione della cache viene gestita automaticamente da `ece-tools`. Invece di modificare direttamente `env.php`, consulta [Configurare la cache L2 di Symfony](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-symfony-l2-cache).

Nel file `app/etc/env.php`, utilizzare il tipo di back-end `symfony_l2` semplificato per la cache L2. Questo esempio non include la configurazione `preload_keys`, che non è consigliata con `symfony_l2`. Per ulteriori dettagli, vedere [Migrazione da RemoteSynchronizedCache a Symfony L2](#migrating-from-remotesynchronizedcache-to-symfony-l2).

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                // L2 (Remote): Valkey with Symfony Cache
                'remote_backend' => 'valkey',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'compress_data' => '1',
                    'persistent_id' => 'magento_l2_default',
                    'timeout' => '2.5',
                    'read_timeout' => '2.0',
                    'use_lua' => '1',
                ],
                // L1 (Local): File cache
                'local_backend' => 'file',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/magento_l1'
                ],
                'cleanup_percentage' => 90,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
    ],
],
```

### Cache Symfony L2 con cache non aggiornata

Vedi [Opzioni cache non aggiornata](#stale-cache-options) per le quali i tipi di cache beneficiano di una cache non aggiornata e perché.

Utilizzare l&#39;esempio seguente per configurare front-end separati per il supporto cache non aggiornata `symfony_l2`:

```php
'cache' => [
    'frontend' => [
        // Default frontend: NO stale cache
        'default' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                'remote_backend' => 'valkey',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'compress_data' => '1',
                    'persistent_id' => 'magento_l2_default',
                ],
                'local_backend' => 'file',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/magento_l1'
                ],
            ],
        ],
        // Stale cache enabled frontend
        'stale_cache_enabled' => [
            'backend' => 'symfony_l2',
            'backend_options' => [
                'remote_backend' => 'valkey',
                'remote_backend_options' => [
                    'server' => 'localhost',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compression_lib' => 'gzip',
                    'compress_data' => '1',
                    'persistent_id' => 'magento_l2_stale',
                ],
                'local_backend' => 'file',
                'local_backend_options' => [
                    'cache_dir' => '/dev/shm/magento_l1_stale'
                ],
                'use_stale_cache' => true,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
        'layout' => ['frontend' => 'stale_cache_enabled'],
        'block_html' => ['frontend' => 'stale_cache_enabled'],
        'reflection' => ['frontend' => 'stale_cache_enabled'],
        'config_integration' => ['frontend' => 'stale_cache_enabled'],
        'config_integration_api' => ['frontend' => 'stale_cache_enabled'],
        'full_page' => ['frontend' => 'stale_cache_enabled'],
        'translate' => ['frontend' => 'stale_cache_enabled'],
    ],
],
```

### Opzioni di back-end per la cache L2 di Symfony

| Opzione | Tipo | Predefinito | Descrizione |
| -------- | ------ | --------- | --------------------------------------------------------------------- |
| `remote_backend` | stringa | `'valkey'` | Tipo di back-end remoto: `valkey` o `file`. Usa `valkey` per la cache L2. |
| `remote_backend_options` | array | `[]` | Configurazione back-end remota (consulta la documentazione di Valkey) |
| `local_backend` | stringa | `'file'` | Tipo di back-end locale: `file` o `apcu` |
| `local_backend_options` | array | `[]` | Configurazione back-end locale |
| `cleanup_percentage` | numero intero | `95` | Soglia pulizia cache L1 (1-100) |
| `use_stale_cache` | booleano | `false` | Abilita cache non aggiornata per un&#39;elevata disponibilità |
| `compress_data` | booleano | `false` | Abilita la compressione se combinata con `compression_lib`. L&#39;impostazione di `compression_lib` da sola non abilita la compressione. |
| `persistent` | booleano | `true` | Controlla le connessioni permanenti al backend remoto. Impostato su `false` (`'0'`) per corrispondere al comportamento della cache Zend legacy, che viene impostato automaticamente su connessioni non persistenti. |


>[!NOTE]
>
>- Anche l&#39;opzione `remote_backend` accetta un valore di `redis`, ma Redis non è ufficialmente supportato (vedi la nota precedente in [Implementazione della cache L2 di Modern Symfony](#modern-symfony-l2-cache-implementation)).
>
>- `frontend_options.write_control`, utilizzato nella configurazione legacy di `RemoteSynchronizedCache`, non si applica a `symfony_l2`.

### Prestazioni e affidabilità migliorate della cache L2 di Symfony

>[!NOTE]
>
>Questi miglioramenti si applicano alle distribuzioni di Adobe Commerce 2.4.9 che utilizzano `symfony_l2` e sono disponibili nella patch ACP2E-5132. Per Adobe Commerce on-premise, applichi questa patch utilizzando lo strumento Quality Patches (QPT). Per Adobe Commerce on Cloud, questa patch viene distribuita automaticamente tramite [Patch cloud per Commerce](https://experienceleague.adobe.com/en/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches#latest).

Gli aggiornamenti più recenti migliorano la scalabilità della cache di Symfony L2, riducono gli I/O inutili dei file system e migliorano la coerenza e l’affidabilità della cache.

#### Memorizzazione tag cache L2 ottimizzata di Symfony

È stato ottimizzato il comportamento della cache L2 di Symfony per le distribuzioni con supporto Valkey, eliminando le scritture ridondanti dell’indice dei tag del file system. I tag cache sono ora memorizzati esclusivamente in Valkey, allineando il comportamento della cache di Symfony L2 con l’implementazione della cache legacy. In questo modo si riduce l&#39;I/O del disco non necessario, si migliorano le prestazioni di scrittura della cache e si impedisce la crescita della directory `var/cache/symfony/tags/`.

#### Miglioramento del comportamento della cache basata su file

Per le distribuzioni che utilizzano la cache basata su file (senza Valkey), l’indice dei tag locali continua a essere mantenuto per supportare l’invalidamento della cache. L&#39;indice dei tag viene ora scritto nel percorso `cache_dir` configurato anziché nel percorso `var/cache` codificato in precedenza, garantendo un utilizzo coerente della directory della cache e un supporto migliorato per le configurazioni della cache personalizzata.

#### Correzione dell’appartenenza ai tag obsoleti dopo il retagging

Il retagging di una voce della cache poteva lasciarla associata a tag a cui non apparteneva più. Le appartenenze ai tag non aggiornate vengono ora cancellate al momento del retag, pertanto le voci della cache vengono invalidate solo dai tag attualmente assegnati.

#### Correzione di scrittura remota ridondante per salvataggi invariati

Il salvataggio di una voce della cache con contenuto invariato attivava ancora una scrittura sul backend remoto (Valkey). I salvataggi ora vengono ignorati quando il contenuto non viene modificato, riducendo le scritture remote non necessarie.

#### Correzione sfratto basata sulle dimensioni L1 (cleanup_percentage)

La soglia `cleanup_percentage` utilizzata per l&#39;eliminazione basata sulle dimensioni L1 non ha attivato in modo coerente la pulizia. L&#39;eliminazione della cache L1 ora rispetta correttamente `cleanup_percentage` configurato.

#### Blocco di rigenerazione per cache non aggiornata

Quando `use_stale_cache` è abilitato e la copia remota di una voce non è temporaneamente disponibile, solo un processo acquisisce un blocco di breve durata per rigenerare la voce. Altre richieste simultanee per la stessa voce continuano a fornire il valore locale esistente invece di rigenerarlo personalmente, riducendo gli stamp di rigenerazione e il carico di back-end ridondante.

#### Impatto

- Elimina le scritture ridondanti dell&#39;indice dei tag del file system per le distribuzioni della cache Symfony L2 con supporto Valkey, riducendo l&#39;I/O del disco e impedendo la crescita inutile della directory `var/cache/symfony/tags/`.
- Garantisce che le distribuzioni della cache basate su file utilizzino in modo coerente `cache_dir` configurato per l&#39;indice di tag locale, mantenendo al contempo il comportamento di invalidamento della cache.
- Impedisce l’invalidazione errata della cache a causa di appartenenze di tag non aggiornati lasciate dopo il retagging.
- Riduce le scritture remote non necessarie per il salvataggio della cache invariata, riducendo il carico di rete e di back-end.
- Assicura che l&#39;eliminazione della cache L1 venga attivata in modo affidabile alla soglia configurata di `cleanup_percentage`.
- Riduce gli stamp di rigenerazione per `use_stale_cache` voci selezionando un singolo rigeneratore per chiave anziché ogni richiesta concorrente che lo ricrea.

Per opzioni di configurazione dettagliate, vedi:

- [Configurazione della cache di Valkey con Symfony Cache](valkey-pg-cache.md)

>[!MORELIKETHIS]
>
>- [Panoramica sulla memorizzazione nella cache e opzioni di configurazione](caching-overview.md)
>- [Opzioni di back-end cache e riferimento archiviazione](cache-options.md)
>- [Configura tipi e front-end della cache](cache-types.md)
>- [Configura Redis per la cache predefinita e delle pagine](redis-pg-cache.md)
