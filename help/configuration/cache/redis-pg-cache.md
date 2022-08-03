---
title: Usa Redis per la cache predefinita
description: Scopri come configurare Redis come cache predefinita per Adobe Commerce e Magenti Open Source.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '1088'
ht-degree: 0%

---


# Usa Redis per la cache predefinita

Commerce fornisce opzioni della riga di comando per configurare la pagina Redis e il caching predefinito. Anche se è possibile configurare la memorizzazione in cache modificando il `<Commerce install dir>app/etc/env.php` file, l&#39;utilizzo della riga di comando è il metodo consigliato, in particolare per le configurazioni iniziali. La riga di comando fornisce la convalida, assicurando che la configurazione sia sincronicamente corretta.

Devi [installare Redis](config-redis.md#install-redis) prima di continuare.

## Configurare la memorizzazione in cache predefinita di Redis

Esegui il `setup:config:set` e specificare i parametri specifici della memorizzazione in cache predefinita di Redis.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-<parameter_name>=<parameter_value>...
```

dove

`--cache-backend=redis` abilita il caching predefinito Redis. Se questa funzione è già stata abilitata, ometti questo parametro.

`--cache-backend-redis-<parameter_name>=<parameter_value>` è un elenco di coppie chiave-valore che configurano il caching predefinito:

| Parametro della riga di comando | Parametro | Significato | Valore predefinito |
|--- |--- |--- |--- |
| cache-backend-redis-server | server | Nome host completo, indirizzo IP o percorso assoluto di un socket UNIX. Il valore predefinito 127.0.0.1 indica che Redis è installato sul server Commerce. | 127.0.0.1 |
| cache-backend-redis-port | porta | Porta di ascolto del server Redis | 6379 |
| cache-backend-redis-db | database | Obbligatorio se si utilizza Redis sia per la cache predefinita che per quella a pagina intera. È necessario specificare il numero del database di una delle cache; l’altra cache utilizza 0 per impostazione predefinita.<br><br>Importante: Se si utilizza Redis per più tipi di caching, i numeri del database devono essere diversi. Si consiglia di assegnare il numero di database di memorizzazione in cache predefinito a 0, il numero di database di memorizzazione in cache della pagina a 1 e il numero di database di archiviazione della sessione a 2. | 0 |
| cache-backend-redis-password | password | La configurazione di una password Redis abilita una delle funzioni di sicurezza integrate: la `auth` , che richiede l&#39;autenticazione dei client per accedere al database. La password è configurata direttamente nel file di configurazione di Redis, `/etc/redis/redis.conf`. |  |

### Esempio, comando

L&#39;esempio seguente abilita il caching predefinito Redis, imposta l&#39;host su `127.0.0.1` e assegna il numero del database a 0. Redis utilizza i valori predefiniti per tutti gli altri parametri.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## Configurare la memorizzazione in cache delle pagine Redis

Per configurare la memorizzazione in cache delle pagine Redis su Commerce, esegui la `setup:config:set` con parametri aggiuntivi.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter_name>=<parameter_value>...
```

dove

`--page-cache=redis` abilita il caching delle pagine di Redis. Se questa funzione è già stata abilitata, ometti questo parametro.

`--page-cache-redis-<parameter_name>=<parameter_value>` è un elenco di coppie di parametri/valori che configurano la memorizzazione in cache delle pagine:

| Parametro della riga di comando | Parametro | Significato | Valore predefinito |
|--- |--- |--- |--- |
| page-cache-redis-server | server | Nome host completo, indirizzo IP o percorso assoluto di un socket UNIX. Il valore predefinito 127.0.0.1 indica che Redis è installato sul server Commerce. | 127.0.0.1 |
| page-cache-redis-port | porta | Porta di ascolto del server Redis | 6379 |
| page-cache-redis-db | database | Obbligatorio se si utilizza Redis sia per la cache predefinita che per quella a pagina intera. È necessario specificare il numero del database di una delle cache; l’altra cache utilizza 0 per impostazione predefinita.<br/>Importante: Se si utilizza Redis per più tipi di caching, i numeri del database devono essere diversi. Si consiglia di assegnare il numero di database di memorizzazione in cache predefinito a 0, il numero di database di memorizzazione in cache della pagina a 1 e il numero di database di archiviazione della sessione a 2. | 0 |
| page-cache-redis-password | password | La configurazione di una password Redis abilita una delle funzioni di sicurezza integrate: la `auth` , che richiede l&#39;autenticazione dei client per accedere al database. Configura la password all&#39;interno del file di configurazione Redis, /etc/redis/redis.conf. |  |

### Esempio, comando

L&#39;esempio seguente abilita il caching delle pagine Redis, imposta l&#39;host su `127.0.0.1` e assegna il numero del database a 1. Tutti gli altri parametri sono impostati sul valore predefinito.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-redis-db=1
```

## Risultati

A seguito dei due comandi di esempio, Commerce aggiunge linee simili alle seguenti `<Commerce install dir>app/etc/env.php`:

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

## Utilizzo di AWS ElastiCache con l&#39;istanza EC2

A partire da Commerce 2.4.3, le istanze ospitate su Amazon EC2 possono utilizzare un AWS ElastiCache al posto di un&#39;istanza Redis locale.

>[!WARNING]
>
>Questa sezione funziona solo per le istanze Commerce in esecuzione su VPC Amazon EC2. Non funziona per installazioni locali.

### Configurare un cluster Redis

Dopo [configurazione di un cluster Redis su AWS](https://aws.amazon.com/getting-started/hands-on/setting-up-a-redis-cluster-with-amazon-elasticache/), configura l’istanza EC2 per utilizzare ElastiCache.

1. [Crea un cluster ElastiCache](https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/set-up.html) nella stessa regione e VPC dell’istanza EC2.
1. Verifica la connessione.

   - Apri una connessione SSH alla tua istanza EC2
   - Nell’istanza EC2, installa il client Redis:

      ```bash
      sudo apt-get install redis
      ```

   - Aggiungi una regola in entrata al gruppo di sicurezza EC2: Tipo `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Aggiungi una regola in entrata al gruppo di sicurezza del cluster ElastiCache: Tipo `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Connettiti alla CLI di Redis:

      ```bash
      redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port>
      ```

### Configurare Commerce per utilizzare il cluster

Commerce supporta più tipi di configurazioni di caching. Generalmente, le configurazioni di memorizzazione in cache sono suddivise tra front-end e backend. Il caching frontale è classificato come &quot;predefinito&quot;, utilizzato per qualsiasi tipo di cache. Puoi personalizzare o dividere in cache di livello inferiore per ottenere prestazioni migliori. Una configurazione comune di Redis sta separando la cache predefinita e la cache della pagina nel proprio database Redis (RDB).

Esegui `setup` comandi per specificare gli endpoint Redis.

Configurazione di Commerce per Redis come memorizzazione in cache predefinita:

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=<ElastiCache Primary Endpoint host> --cache-backend-redis-port=<ElastiCache Primary Endpoint port> --cache-backend-redis-db=0
```

Configurare Commerce per la memorizzazione in cache delle pagine Redis:

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=<ElastiCache Primary Endpoint host> --page-cache-redis-port=<ElastiCache Primary Endpoint port> --page-cache-redis-db=1
```

Configura Commerce per utilizzare Redis per l&#39;archiviazione delle sessioni:

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=<ElastiCache Primary Endpoint host> --session-save-redis-port=<ElastiCache Primary Endpoint port> --session-save-redis-log-level=4 --session-save-redis-db=2
```

### Verificare la connettività

Per verificare che Commerce stia parlando con ElasiCache:

1. Apri una connessione SSH all’istanza Commerce EC2.
1. Avviare il monitor Redis.

   ```bash
   redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port> monitor
   ```

1. Apri una pagina nell’interfaccia utente Commerce.
1. Verifica la [uscita cache](#verify-redis-connection) nel terminale.

## Nuova implementazione della cache Redis

A partire da Commerce 2.3.5, si consiglia di utilizzare l’implementazione estesa della cache Redis: `\Magento\Framework\Cache\Backend\Redis`.

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

## Funzione di precaricamento di Redis

Poiché Commerce memorizza molti dati di configurazione nella cache Redis, possiamo precaricare i dati riutilizzati tra le pagine.
Per trovare le chiavi che devono essere precaricate, devi analizzare i dati trasferiti da Redis a Commerce. Si consiglia di precaricare i dati caricati su ogni pagina, di seguito sono riportati alcuni esempi comuni `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES`, `DB_IS_UP_TO_DATE`.
Redis utilizza il `pipeline` per comporre le richieste di caricamento.
Tieni presente che le chiavi devono includere il prefisso del database, ad esempio se il prefisso del database è `061_`, il tasto di precaricamento è simile a `061_SYSTEM_DEFAULT`.

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

Se utilizzi la funzione di precaricamento con la cache L2, non dimenticare di aggiungere il suffisso &#39;:hash&#39; alle chiavi, poiché la cache L2 trasferisce solo l&#39;hash dei dati, non i dati stessi:

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

## Generazione parallela

A partire dalla versione 2.4.0, abbiamo introdotto la `allow_parallel_generation` opzione per gli utenti che desiderano eliminare le attese per i blocchi.
È disabilitata per impostazione predefinita e consigliamo di disattivarla finché non si dispone di configurazioni e/o blocchi eccessivi.

**Per abilitare la generazione parallela**:

```bash
bin/magento setup:config:set --allow-parallel-generation
```

Poiché si tratta di un flag, non è possibile disattivarlo con un comando. È necessario impostare manualmente il valore di configurazione su `false`:

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

## Verifica la connessione Redis

Per verificare che Redis e Commerce stiano lavorando insieme, accedi al server che esegue Redis, apri un terminale e utilizza il comando Monitor Redis o il comando ping.

### Comando Redis monitor

```bash
redis-cli monitor
```

Esempio di output di memorizzazione in cache delle pagine:

```terminal
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

### Ripristina, comando

```bash
redis-cli ping
```

`PONG` dovrebbe essere la risposta.

Se entrambi i comandi sono riusciti, Redis è configurato correttamente.

### Ispezione dei dati compressi

Per esaminare i dati compressi della sessione e della cache della pagina, la [RESP.app](https://flathub.org/apps/details/app.resp.RESP) supporta la decompressione automatica della cache di sessioni e pagine Commerce 2 e visualizza i dati di sessione PHP in un formato leggibile dall&#39;utente.
