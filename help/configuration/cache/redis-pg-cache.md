---
title: Configurare Redis per Default e Page Cache
description: Scopri come configurare Redis come backend predefinito e cache delle pagine per Adobe Commerce. Scopri i comandi CLI, le impostazioni env.php e la verifica della connessione.
feature: Configuration, Cache
exl-id: 8c097cfc-85d0-4e96-b56e-284fde40d459
badgePaas: label="On-Premises" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Applicabile solo ai progetti locali di Adobe Commerce."
autotag-review: '2026-06-22T21:55:53.227Z'
TQID: 'https://experienceleague.adobe.com/2KjWE19ud32PUdvJQWNWkK338ysaa5vt0mA4EyyP66I'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
feature_v2:
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
source-git-commit: ec95c99d060f3c45095236d41729648abf389dd1
workflow-type: tm+mt
source-wordcount: 1411
ht-degree: 0%

---

# Configurare Redis per cache predefinita e di pagina

{{cloud-cache-config}}

Commerce fornisce opzioni della riga di comando per configurare la pagina Redis e il caching predefinito. Sebbene sia possibile configurare il caching modificando il file `<Commerce-install-dir>app/etc/env.php`, l&#39;utilizzo della riga di comando è il metodo consigliato, in particolare per le configurazioni iniziali. La riga di comando fornisce la convalida, garantendo che la configurazione sia sintatticamente corretta.

**Prerequisito:**

[Installare Redis](config-redis.md#install-redis) prima di continuare.

>[!NOTE]
>
>Per le istanze Commerce in hosting su EC2, puoi utilizzare AWS ElastiCache invece di un’istanza Redis locale. Consulta [Configurare Elasticache per le istanze EC2](redis-elasticache-for-ec2.md).

## Implementazioni della cache Redis

Adobe Commerce ha utilizzato le seguenti implementazioni di back-end della cache Redis:

- **Back-end Redis legacy** (`Cm_Cache_Backend_Redis`) - Implementazione obsoleta utilizzata in configurazioni Redis precedenti.
- **Redis backend** (`Magento\Framework\Cache\Backend\Redis`) - Backend utilizzato dalla configurazione della riga di comando in questo argomento per la cache predefinita e delle pagine.
- **Back-end cache L2** (`Magento\Framework\Cache\Backend\RemoteSynchronizedCache`) - Implementazione della cache a due livelli che utilizza Redis come back-end remoto e archiviazione della cache dei file locale per sincronizzare i dati della cache tra nodi. Vedi [Configurazione della cache a due livelli](level-two-cache.md).

## Configurare il caching predefinito di Redis

Eseguire il comando `setup:config:set` e specificare parametri specifici per il caching predefinito Redis.

```shell
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-<parameter>=<value>...
```

I parametri comuni includono:

- `--cache-backend=redis` abilita il caching predefinito di Redis. Se questa funzione è già stata abilitata, ometti questo parametro.

- `--cache-backend-redis-<parameter>=<value>` è un elenco di coppie chiave-valore che configurano il caching predefinito:

| Parametro della riga di comando | Valore | Significato | Valore predefinito |
| --- | --- | --- | --- |
| `cache-backend-redis-server` | server | Nome host completo, indirizzo IP o percorso assoluto di un socket UNIX. Il valore predefinito 127.0.0.1 indica che Redis è installato nel server Commerce. | `127.0.0.1` |
| `cache-backend-redis-port` | porta | Porta di ascolto del server Redis | `6379` |
| `cache-backend-redis-db` | database | Obbligatorio se si utilizza Redis sia per la cache predefinita che per quella a pagina intera. Specificare il numero di database di una delle cache; l&#39;altra cache utilizza 0 per impostazione predefinita.<br><br>**Importante**: se si utilizza Redis per più di un tipo di memorizzazione nella cache, i numeri di database devono essere diversi. È consigliabile assegnare il numero predefinito del database di memorizzazione nella cache a 0, il numero del database di memorizzazione nella cache delle pagine a 1 e il numero del database di memorizzazione nella sessione a 2. | `0` |
| `cache-backend-redis-password` | password | La configurazione di una password Redis abilita una delle funzionalità di protezione incorporate: il comando `auth`, che richiede l&#39;autenticazione dei client per accedere al database. La password è configurata direttamente nel file di configurazione di Redis: `/etc/redis/redis.conf` | |
| `cache-backend-redis-compress-data` | compress_data | Impostare su `0` per disabilitare la compressione. | `1` |
| `cache-backend-redis-compression-lib` | compression_lib | Libreria di compressione da utilizzare. I valori supportati sono `snappy`, `lzf`, `l4z`, `zstd` e `gzip`. Lascia vuoto per determinare automaticamente. | |
| `cache-backend-redis-use-lua` | use_lua | Attiva o disattiva gli script Lua per tutte le operazioni Redis. <br><br>**Impostazione predefinita: mantieni alle `0`.** La modalità Lua è disabilitata per impostazione predefinita per evitare regressioni delle prestazioni note e problemi di perdita della cache di GraphQL introdotti dalla libreria Redis in bundle (1.17.x) quando Lua è stato abilitato. | `0` |
| `cache-backend-redis-use-lua-on-gc` | use_lua_on_gc | Abilitare o disabilitare gli script Lua per la raccolta di oggetti inattivi (il processo cron `backend_clean_cache`). <br><br>**Impostazione predefinita: mantieni alle `1`.** Abilitato intenzionalmente per garantire la pulizia del set di tag atomici durante la GC. Senza di esso, può verificarsi una situazione di tipo &quot;race condition&quot; quando il cron `backend_clean_cache` viene eseguito contemporaneamente a un&#39;operazione di salvataggio della cache, lasciando le voci della cache senza un record corrispondente nell&#39;indice dei tag della cache. Questo causa un errore improvviso di invalidazione basata su tag: ad esempio, l’aggiornamento del prezzo di un prodotto potrebbe non invalidare la cache del prodotto, richiedendo invece uno scaricamento completo della cache. | `1` |

### Modalità Lua

Se abilitata, la modalità Lua raggruppa più operazioni Redis (scritture cache, aggiornamenti dei tag, Garbage Collection) in un unico script atomico eseguito lato server tramite `EVALSHA`. Questo impedisce l’interfoliazione da richieste simultanee, ad esempio, garantendo che una voce della cache e la relativa appartenenza ai tag siano scritte insieme.

>[!WARNING]
>
>Non modificare i valori predefiniti per `use_lua` e `use_lua_on_gc` senza comprendere le implicazioni per la versione di Adobe Commerce:
>
>- **`use_lua`**: l&#39;abilitazione di questa proprietà in Adobe Commerce 2.4.7 o 2.4.8 (libreria `colinmollenhour/cache-backend-redis` 1.17.1) può causare il danneggiamento della cache e problemi di mancato funzionamento della cache di GraphQL.
>- **`use_lua_on_gc`**: la disabilitazione di questa proprietà in Adobe Commerce 2.4.8 rimuove la protezione atomica durante la raccolta di oggetti inattivi e può causare un errore silenzioso di invalidazione della cache basata su tag, che richiede il ripristino di uno scaricamento completo della cache.

## Esempio di comando (cache predefinita)

Nell&#39;esempio seguente viene attivato il caching predefinito Redis, l&#39;host viene impostato su `127.0.0.1` e il numero del database viene assegnato a 0. Redis utilizza i valori predefiniti per tutti gli altri parametri.

```shell
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## Configurare il caching delle pagine Redis

Per configurare il caching delle pagine Redis in Commerce, eseguire il comando `setup:config:set` con parametri aggiuntivi.

```shell
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter>=<value>...
```

I parametri comuni includono:

- `--page-cache=redis` abilita il caching delle pagine Redis. Se questa funzione è già stata abilitata, ometti questo parametro.

- `--page-cache-redis-<parameter>=<value>` è un elenco di coppie chiave-valore che configurano il caching delle pagine:

| Parametro della riga di comando | Valore | Significato | Valore predefinito |
| --- | --- | --- | --- |
| `page-cache-redis-server` | server | Nome host completo, indirizzo IP o percorso assoluto di un socket UNIX. Il valore predefinito 127.0.0.1 indica che Redis è installato nel server Commerce. | `127.0.0.1` |
| `page-cache-redis-port` | porta | Porta di ascolto del server Redis | `6379` |
| `page-cache-redis-db` | database | Obbligatorio se si utilizza Redis sia per la cache predefinita che per quella a pagina intera. Specificare il numero di database di una delle cache; l&#39;altra cache utilizza 0 per impostazione predefinita.<br/>**Importante**: se si utilizza Redis per più di un tipo di memorizzazione nella cache, i numeri di database devono essere diversi. È consigliabile assegnare il numero predefinito del database di memorizzazione nella cache a 0, il numero del database di memorizzazione nella cache delle pagine a 1 e il numero del database di memorizzazione nella sessione a 2. | `0` |
| `page-cache-redis-password` | password | La configurazione di una password Redis abilita una delle funzionalità di protezione incorporate: il comando `auth`, che richiede l&#39;autenticazione dei client per accedere al database. Configurare la password nel file di configurazione Redis: `/etc/redis/redis.conf` | |
| `page-cache-redis-compress-data` | compress_data | Impostare su `1` per comprimere la cache di pagina intera. Utilizza `0` per disabilitare la compressione. | `0` |
| `page-cache-redis-compression-lib` | compression_lib | Libreria di compressione da utilizzare. I valori supportati sono `snappy`, `lzf`, `l4z`, `zstd` e `gzip`. Lascia vuoto per determinare automaticamente. | |

L&#39;esempio che segue abilita il caching delle pagine Redis, imposta l&#39;host su `127.0.0.1` e assegna il numero di database a `1`. Tutti gli altri parametri vengono impostati sul valore predefinito.

```shell
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-redis-db=1
```

{{valkey-redis-cli-note}}

### Verifica la configurazione dell’ambiente Commerce

L&#39;esecuzione dei comandi per configurare Redis caching aggiorna la configurazione dell&#39;ambiente Commerce (`<Commerce-install-dir>app/etc/env.php`):

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'port' => '6379',
                'database' => '1',
                'compress_data' => '0'
            ]
        ]
    ]
],
```

## Configurare opzioni di caching aggiuntive

### Funzione di precaricamento Redis

Poiché Commerce memorizza i dati di configurazione nella cache Redis, puoi precaricare i dati riutilizzati tra le pagine. Per trovare le chiavi che devono essere precaricate, analizza i dati trasferiti da Redis a Commerce. Adobe consiglia di precaricare i dati caricati su ogni pagina, ad esempio `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES` e `DB_IS_UP_TO_DATE`.

Redis utilizza `pipeline` per comporre le richieste di caricamento. Le chiavi devono includere il prefisso del database; ad esempio, se il prefisso del database è `061_`, la chiave di precaricamento sarà simile alla seguente: `061_SYSTEM_DEFAULT`

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => 'redis',
                'database' => '0',
                'port' => '6379',
                'password' => '',
                'compress_data' => '1',
                'compression_lib' => '',
                'preload_keys' => [
                    '061_EAV_ENTITY_TYPES',
                    '061_GLOBAL_PLUGIN_LIST',
                    '061_DB_IS_UP_TO_DATE',
                    '061_SYSTEM_DEFAULT',
                ],
            ]
        ],
        'page_cache' => [
            'id_prefix' => '061_'
        ]
    ]
]
```

Quando si utilizza la funzione di precaricamento con una cache L2, è necessario aggiungere il suffisso `:hash` alle chiavi. La cache L2 trasferisce solo l’hash dei dati, non i dati effettivi.

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

### Generazione parallela

A partire dalla versione di Commerce 2.4.0, Adobe ha introdotto l&#39;opzione `allow_parallel_generation` per gli utenti che desiderano eliminare l&#39;attesa dei blocchi. È disabilitato per impostazione predefinita e Adobe consiglia di disabilitarlo fino a quando non si dispone di configurazioni e/o blocchi eccessivi.

**Per abilitare la generazione parallela**:

```shell
bin/magento setup:config:set --allow-parallel-generation
```

Poiché è un flag, non è possibile disattivarlo con un comando. Impostare manualmente il valore di configurazione su `false`:

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'Magento\\Framework\\Cache\\Backend\\Redis',
                'backend_options' => [
                    'server' => 'redis',
                    'database' => '0',
                    'port' => '6379',
                    'password' => '',
                    'compress_data' => '1',
                    'compression_lib' => ''
                ]
            ],
            'page_cache' => [
                'id_prefix' => 'b0b_'
            ]
        ],
        'allow_parallel_generation' => false
    ],
```

## Ottimizzazione delle prestazioni

Se si utilizza Symfony Cache, è possibile ottimizzare ulteriormente le prestazioni configurando il serializzatore Igbinary, installando l&#39;estensione PHP e phpredis e abilitando connessioni persistenti.

### Serializzatore igbinario

Il serializzatore Igbinary migliora notevolmente le prestazioni rispetto alla serializzazione predefinita di PHP. Deve essere configurato manualmente in `app/etc/env.php`:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend_options' => [
                'server' => 'redis',
                'database' => '0',
                'port' => '6379',
                'serializer' => 'igbinary',  // Enable Igbinary serialization
            ]
        ],
        'page_cache' => [
            'backend_options' => [
                'server' => 'redis',
                'database' => '1',
                'port' => '6379',
                'serializer' => 'igbinary',  // Enable Igbinary for page cache too
            ]
        ]
    ]
]
```

### Installare l&#39;estensione PHP Igbinary

Per utilizzare la serializzazione binaria, è necessario installare l&#39;estensione PHP Igbinary.

**Utilizzo di apt (consigliato per Debian/Ubuntu)**:

```bash
sudo apt-get install php-igbinary
sudo systemctl restart php-fpm
php -m | grep igbinary
```

**Utilizzo di pecl (metodo alternativo)**:

```bash
sudo pecl install igbinary
echo "extension=igbinary.so" | sudo tee /etc/php/8.3/mods-available/igbinary.ini
sudo phpenmod igbinary
sudo systemctl restart php-fpm
php -m | grep igbinary
```

### Estensione PHP Redis

Utilizzare l&#39;estensione PHP Redis nativa (`phpredis`) quando supportata dall&#39;ambiente:

#### Usa apt

Per Debian o Ubuntu, usa `apt`:

```bash
sudo apt-get install php-redis
sudo systemctl restart php-fpm
php -m | grep redis
```

#### Usa pecl

In alternativa, utilizzare `pecl`:

```bash
sudo pecl install redis
echo "extension=redis.so" | sudo tee /etc/php/<version>/mods-available/redis.ini
sudo phpenmod redis
sudo systemctl restart php-fpm
php -m | grep redis
```

**Confronto delle prestazioni**:

| Operazione | Predis | phpredis | Miglioramento |
|-----------|--------|----------|-------------|
| Cache GET | 1-5 ms | 0,5-2 ms | 2-3 volte più veloce |
| Cache SET | 2-6 ms | 0,8-2,5 ms | 2-3 volte più veloce |
| Operazioni sui tag | 10-30 ms | 3-10 ms | 3-4 volte più veloce |

### Connessioni persistenti

Le connessioni persistenti riutilizzano le connessioni Redis esistenti tra le richieste, fornendo operazioni della cache più veloci del 5-15%. Configura in `app/etc/env.php`:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend_options' => [
                'server' => 'redis',
                'database' => '0',
                'port' => '6379',
                'persistent' => '1',
                'persistent_id' => 'cache_default',
                'timeout' => '2.5',
                'read_timeout' => '2.0',
            ]
        ],
        'page_cache' => [
            'backend_options' => [
                'server' => 'redis',
                'database' => '1',
                'port' => '6379',
                'persistent' => '1',
                'persistent_id' => 'cache_fpc',
            ]
        ]
    ]
]
```

>[!IMPORTANT]
>
>Utilizzare un `persistent_id` univoco per ogni tipo di cache per evitare conflitti di connessione.

### Configurazione ottimizzata completa

Ecco una configurazione Redis pronta per la produzione che combina tutte le ottimizzazioni delle prestazioni:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => 'b0b_',
            'backend' => 'redis',
            'backend_options' => [
                'server' => 'redis',
                'database' => '0',
                'port' => '6379',
                'serializer' => 'igbinary',
                'compress_data' => '1',
                'compression_lib' => 'gzip',
                'persistent' => '1',
                'persistent_id' => 'cache_default',
                'timeout' => '2.5',
                'read_timeout' => '2.0',
                'use_lua' => '1',
                'use_lua_on_gc' => '1',
                'preload_keys' => [
                    'b0b_EAV_ENTITY_TYPES',
                    'b0b_GLOBAL_PLUGIN_LIST',
                    'b0b_DB_IS_UP_TO_DATE',
                    'b0b_SYSTEM_DEFAULT',
                ],
            ]
        ],
        'page_cache' => [
            'id_prefix' => 'b0b_',
            'backend' => 'redis',
            'backend_options' => [
                'server' => 'redis',
                'database' => '1',
                'port' => '6379',
                'serializer' => 'igbinary',
                'compress_data' => '0',
                'persistent' => '1',
                'persistent_id' => 'cache_fpc',
            ]
        ]
    ],
    'allow_parallel_generation' => false
]
```

## Verificare la connessione Redis

Per verificare che Redis e Commerce funzionino correttamente:

1. Accedere al server che esegue Redis e Commerce.
1. Apri un terminale.
1. Controllare la connessione utilizzando il comando `redis-cli monitor` o il comando `redis-cli ping`.

Se i comandi vengono eseguiti correttamente, Redis è in esecuzione e può comunicare con l&#39;applicazione Commerce. In caso di esito negativo, è necessario risolvere un problema di connessione tra Redis e Commerce.

### Comando Redis Monitor

```shell
redis-cli monitor
```

Output di esempio per il caching delle pagine:

```text
1476826133.810090 [0 127.0.0.1:52366] "select" "1"
1476826133.816293 [0 127.0.0.1:52367] "select" "0"
1476826133.817461 [0 127.0.0.1:52367] "hget" "zc:k:ea6_GLOBAL__DICONFIG" "d"
1476826133.829666 [0 127.0.0.1:52367] "hget" "zc:k:ea6_DICONFIG049005964B465901F774DB9751971818" "d"
1476826133.837854 [0 127.0.0.1:52367] "hget" "zc:k:ea6_INTERCEPTION" "d"
1476826133.868374 [0 127.0.0.1:52368] "select" "1"
1476826133.869011 [0 127.0.0.1:52369] "select" "0"
1476826133.869601 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DEFAULT_CONFIG_CACHE_DEFAULT__10__235__32__1080MAGENTO2" "d"
1476826133.872317 [0 127.0.0.1:52369] "hget" "zc:k:ea6_INITIAL_CONFIG" "d"
1476826133.879267 [0 127.0.0.1:52369] "hget" "zc:k:ea6_GLOBAL_PRIMARY_PLUGIN_LIST" "d"
...
```

Se entrambi i comandi vengono eseguiti, Redis viene configurato correttamente.

### Controllare i dati compressi

Per verificare i dati di sessione compressi e la cache delle pagine, utilizzare lo strumento [RESP.app](https://flathub.org/apps/details/app.resp.RESP). Supporta la decompressione automatica dei dati della cache di pagina e della sessione di Commerce 2 e visualizza i dati della sessione PHP in un formato leggibile.
