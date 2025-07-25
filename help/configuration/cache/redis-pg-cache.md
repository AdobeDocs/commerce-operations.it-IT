---
title: Usa Redis per la cache predefinita
description: Scopri come configurare Redis come cache predefinita per Adobe Commerce.
feature: Configuration, Cache
exl-id: 8c097cfc-85d0-4e96-b56e-284fde40d459
source-git-commit: 2c489f2655e6fb067de1730355df6cd3683ea562
workflow-type: tm+mt
source-wordcount: '1126'
ht-degree: 0%

---

# Usa Redis per la cache predefinita

Commerce fornisce opzioni della riga di comando per configurare la pagina Redis e il caching predefinito. Sebbene sia possibile configurare il caching modificando il file `<Commerce-install-dir>app/etc/env.php`, l&#39;utilizzo della riga di comando è il metodo consigliato, in particolare per le configurazioni iniziali. La riga di comando fornisce la convalida, garantendo che la configurazione sia sintatticamente corretta.

È necessario [installare Redis](config-redis.md#install-redis) prima di continuare.

## Configurare il caching predefinito di Redis

Eseguire il comando `setup:config:set` e specificare i parametri specifici del caching predefinito Redis.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-<parameter>=<value>...
```

Con i seguenti parametri:

- `--cache-backend=redis` abilita il caching predefinito di Redis. Se questa funzione è già stata abilitata, ometti questo parametro.

- `--cache-backend-redis-<parameter>=<value>` è un elenco di coppie chiave-valore che configurano il caching predefinito:

| Parametro della riga di comando | Valore | Significato | Valore predefinito |
| ------------------------------ | --------- | ------- | ------------- |
| `cache-backend-redis-server` | server | Nome host completo, indirizzo IP o percorso assoluto di un socket UNIX. Il valore predefinito 127.0.0.1 indica che Redis è installato nel server Commerce. | `127.0.0.1` |
| `cache-backend-redis-port` | porta | Porta di ascolto del server Redis | `6379` |
| `cache-backend-redis-db` | database | Obbligatorio se si utilizza Redis sia per la cache predefinita che per quella a pagina intera. È necessario specificare il numero di database di una delle cache; l&#39;altra cache utilizza 0 per impostazione predefinita.<br><br>**Importante**: se si utilizza Redis per più di un tipo di memorizzazione nella cache, i numeri di database devono essere diversi. È consigliabile assegnare il numero predefinito del database di memorizzazione nella cache a 0, il numero del database di memorizzazione nella cache delle pagine a 1 e il numero del database di memorizzazione nella sessione a 2. | `0` |
| `cache-backend-redis-password` | password | La configurazione di una password Redis abilita una delle funzionalità di protezione incorporate: il comando `auth`, che richiede l&#39;autenticazione dei client per accedere al database. La password è configurata direttamente nel file di configurazione di Redis: `/etc/redis/redis.conf` | |
| `--cache-backend-redis-use-lua` | use_lua | Attiva o disattiva LUA. <br><br>**LUA**: Lua ci consente di eseguire parte della logica dell&#39;applicazione all&#39;interno di Redis, migliorando le prestazioni e garantendo la coerenza dei dati attraverso la sua esecuzione atomica. | `0` |
| `--cache-backend-redis-use-lua-on-gc` | use_lua_on_gc | Attiva o disattiva LUA per la raccolta di oggetti inattivi. <br><br>**LUA**: Lua ci consente di eseguire parte della logica dell&#39;applicazione all&#39;interno di Redis, migliorando le prestazioni e garantendo la coerenza dei dati attraverso la sua esecuzione atomica. | `1` |

### Esempio di comando

Nell&#39;esempio seguente viene attivato il caching predefinito Redis, l&#39;host viene impostato su `127.0.0.1` e il numero del database viene assegnato a 0. Redis utilizza i valori predefiniti per tutti gli altri parametri.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## Configurare il caching delle pagine Redis

Per configurare il caching delle pagine Redis in Commerce, eseguire il comando `setup:config:set` con parametri aggiuntivi.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter>=<value>...
```

Con i seguenti parametri:

- `--page-cache=redis` abilita il caching delle pagine Redis. Se questa funzione è già stata abilitata, ometti questo parametro.

- `--page-cache-redis-<parameter>=<value>` è un elenco di coppie chiave-valore che configurano il caching delle pagine:

| Parametro della riga di comando | Valore | Significato | Valore predefinito |
| ------------------------------ | --------- | ------- | ------------- |
| `page-cache-redis-server` | server | Nome host completo, indirizzo IP o percorso assoluto di un socket UNIX. Il valore predefinito 127.0.0.1 indica che Redis è installato nel server Commerce. | `127.0.0.1` |
| `page-cache-redis-port` | porta | Porta di ascolto del server Redis | `6379` |
| `page-cache-redis-db` | database | Obbligatorio se si utilizza Redis sia per la cache predefinita che per quella a pagina intera. È necessario specificare il numero di database di una delle cache; l&#39;altra cache utilizza 0 per impostazione predefinita.<br/>**Importante**: se si utilizza Redis per più di un tipo di memorizzazione nella cache, i numeri di database devono essere diversi. È consigliabile assegnare il numero predefinito del database di memorizzazione nella cache a 0, il numero del database di memorizzazione nella cache delle pagine a 1 e il numero del database di memorizzazione nella sessione a 2. | `0` |
| `page-cache-redis-password` | password | La configurazione di una password Redis abilita una delle funzionalità di protezione incorporate: il comando `auth`, che richiede l&#39;autenticazione dei client per accedere al database. Configurare la password nel file di configurazione Redis: `/etc/redis/redis.conf` | |

### Esempio di comando

Nell&#39;esempio seguente viene attivato il caching delle pagine Redis, l&#39;host viene impostato su `127.0.0.1` e il numero del database viene assegnato a 1. Tutti gli altri parametri vengono impostati sul valore predefinito.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-redis-db=1
```

## Risultati

Come risultato dei due comandi di esempio, Commerce aggiunge righe simili alle seguenti a `<Commerce-install-dir>app/etc/env.php`:

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

## Utilizzo di AWS ElastiCache con l’istanza EC2

A partire dalla versione 2.4.3 di Commerce, le istanze in hosting su Amazon EC2 possono utilizzare un AWS ElastiCache al posto di un’istanza Redis locale.

>[!WARNING]
>
>Questa sezione funziona solo per le istanze Commerce in esecuzione su VPC Amazon EC2. Non funziona per gli impianti locali.

### Configurare un cluster Redis

Dopo [aver configurato un cluster Redis in AWS](https://aws.amazon.com/getting-started/hands-on/setting-up-a-redis-cluster-with-amazon-elasticache/), configurare l&#39;istanza EC2 per l&#39;utilizzo di ElastiCache.

1. [Creare un cluster ElastiCache](https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/set-up.html) nella stessa area e VPC dell&#39;istanza EC2.
1. Verifica la connessione.

   - Aprire una connessione SSH all’istanza EC2
   - Nell’istanza EC2, installa il client Redis:

     ```bash
     sudo apt-get install redis
     ```

   - Aggiungi una regola in entrata al gruppo di sicurezza EC2: tipo `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Aggiungi una regola in entrata al gruppo di sicurezza del cluster ElastiCache: tipo `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Connessione a Redis CLI:

     ```bash
     redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port>
     ```

### Configurare Commerce per l&#39;utilizzo del cluster

Commerce supporta più tipi di configurazioni di caching. In genere, le configurazioni di caching sono suddivise tra front-end e back-end. Il caching front-end è classificato come `default`, utilizzato per qualsiasi tipo di cache. Puoi personalizzare o suddividere in cache di livello inferiore per ottenere prestazioni migliori. Una comune configurazione Redis separa la cache predefinita e la cache delle pagine nel proprio Redis Database (RDB).

Eseguire `setup` comandi per specificare gli endpoint Redis.

Per configurare Commerce per Redis come memorizzazione in cache predefinita:

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=<ElastiCache Primary Endpoint host> --cache-backend-redis-port=<ElastiCache Primary Endpoint port> --cache-backend-redis-db=0
```

Per configurare Commerce per il caching delle pagine Redis:

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=<ElastiCache Primary Endpoint host> --page-cache-redis-port=<ElastiCache Primary Endpoint port> --page-cache-redis-db=1
```

Per configurare Commerce per l&#39;utilizzo di Redis per l&#39;archiviazione delle sessioni:

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=<ElastiCache Primary Endpoint host> --session-save-redis-port=<ElastiCache Primary Endpoint port> --session-save-redis-log-level=4 --session-save-redis-db=2
```

### Verificare la connettività

**Per verificare che Commerce stia parlando con ElastiCache**:

1. Apri una connessione SSH all’istanza Commerce EC2.
1. Avviare il monitor Redis.

   ```bash
   redis-cli -h <ElastiCache-Primary-Endpoint-host> -p <ElastiCache-Primary-Endpoint-port> monitor
   ```

1. Apri una pagina nell’interfaccia utente di Commerce.
1. Verifica l&#39;[output della cache](#verify-redis-connection) nel terminale.

## Nuova implementazione della cache Redis

A partire dalla versione 2.3.5 di Commerce, si consiglia di utilizzare l&#39;implementazione estesa della cache Redis: `\Magento\Framework\Cache\Backend\Redis`.

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\Redis',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
],
```

## Funzione di precaricamento Redis

Poiché Commerce memorizza i dati di configurazione nella cache Redis, possiamo precaricare i dati riutilizzati tra le pagine. Per trovare le chiavi che devono essere precaricate, analizza i dati trasferiti da Redis a Commerce. Si consiglia di precaricare i dati caricati su ogni pagina, ad esempio `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES`, `DB_IS_UP_TO_DATE`.

Redis utilizza `pipeline` per comporre le richieste di caricamento. Le chiavi devono includere il prefisso del database; ad esempio, se il prefisso del database è `061_`, la chiave di precaricamento sarà simile a: `061_SYSTEM_DEFAULT`

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

Se utilizzi la funzione di precaricamento con la cache L2, non dimenticare di aggiungere il suffisso `:hash` alle chiavi, poiché la cache L2 trasferisce solo l&#39;hash dei dati, non i dati stessi:

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

## Generazione parallela

A partire dalla versione 2.4.0, è stata introdotta l&#39;opzione `allow_parallel_generation` per gli utenti che desiderano eliminare le attese per i blocchi.
È disattivato per impostazione predefinita e si consiglia di disattivarlo fino a quando non si dispone di configurazioni e/o blocchi eccessivi.

**Per abilitare la generazione parallela**:

```bash
bin/magento setup:config:set --allow-parallel-generation
```

Poiché è un flag, non è possibile disattivarlo con un comando. È necessario impostare manualmente il valore di configurazione su `false`:

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

## Verifica connessione Redis

Per verificare che Redis e Commerce funzionino insieme, accedete al server che esegue Redis, aprite un terminale e utilizzate il comando di monitoraggio Redis o il comando ping.

### Comando Redis Monitor

```bash
redis-cli monitor
```

Output di esempio per il caching delle pagine:

```
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
1476826133.883312 [0 127.0.0.1:52369] "hget" "zc:k:ea6_GLOBAL__EVENT_CONFIG_CACHE" "d"
1476826133.898431 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DB_PDO_MYSQL_DDL_STAGING_UPDATE_1" "d"
1476826133.898794 [0 127.0.0.1:52369] "hget" "zc:k:ea6_RESOLVED_STORES_D1BEFA03C79CA0B84ECC488DEA96BC68" "d"
1476826133.905738 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DEFAULT_CONFIG_CACHE_STORE_DEFAULT_10__235__32__1080MAGENTO2" "d"

... more ...

1476826210.634998 [0 127.0.0.1:52439] "hmset" "zc:k:ea6_MVIEW_CONFIG" "d" "a:18:{s:19:\"design_config_dummy\";a:4:{s:7:\"view_id\";s:19:\"design_config_dummy\";s:12:\"action_class\";s:39:\"Magento\\Theme\\Model\\Indexer\\Mview\\Dummy\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:0:{}}s:14:\"customer_dummy\";a:4:{s:7:\"view_id\";s:14:\"customer_dummy\";s:12:\"action_class\";s:42:\"Magento\\Customer\\Model\\Indexer\\Mview\\Dummy\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:0:{}}s:13:\"cms_page_grid\";a:4:{s:7:\"view_id\";s:13:\"cms_page_grid\";s:12:\"action_class\";s:43:\"Magento\\Catalog\\Model\\Indexer\\Category\\Flat\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:1:{s:8:\"cms_page\";a:3:{s:4:\"name\";s:8:\"cms_page\";s:6:\"column\";s:7:\"page_id\";s:18:\"subscription_model\";N;}}}s:21:\"catalog_category_flat\";a:4:{s:7:\"view_id\";s:21:\"catalog_category_flat\";s:12:\"action_class\";s:43:\"Magento\\Catalog\\Model\\Indexer\\Category\\Flat\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:6:{s:23:\"catalog_category_entity\";a:3:{s:4:\"name\";s:23:\"catalog_category_entity\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";N;}s:31:\"catalog_category_entity_decimal\";a:3:{s:4:\"name\";s:31:\"catalog_category_entity_decimal\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:27:\"catalog_category_entity_int\";a:3:{s:4:\"name\";s:27:\"catalog_category_entity_int\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:28:\"catalog_category_entity_text\";a:3:{s:4:\"name\";s:28:\"catalog_category_entity_text\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:31:\"catalog_category_entity_varchar\";a:3:{s:4:\"name\";s:31:\"catalog_category_entity_varchar\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:32:\"catalog_category_entity_datetime\";a:3:{s:4:\"name\";s:32:\"catalog_category_entity_datetime\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}}}s:24:\"catalog_category_product\";a:4:{s:7:\"view_id\";s:24:\"catalog_category_product\";s:12:\"action_class\";s:46:\"Magento\\Catalog\\Model\\Indexer\\Category\\Product\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:2:{s:23:\"catalog_category_entity\";a:3:{s:4:\"name\";s:23:\"catalog_category_entity\";s:6:\"column\"

... more ...
```

### Ridisattiva comando ping

```bash
redis-cli ping
```

Risposta prevista: `PONG`

Se entrambi i comandi sono riusciti, Redis viene configurato correttamente.

### Analisi dei dati compressi

Per verificare i dati compressi di Session e Page Cache, [RESP.app](https://flathub.org/apps/details/app.resp.RESP) supporta la decompressione automatica di Commerce 2 Session e Page Cache e visualizza i dati di sessione PHP in un formato leggibile.
