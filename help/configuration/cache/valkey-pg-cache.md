---
title: Configurare Valkey per Default e Page Cache
description: Scopri come configurare Valkey come backend predefinito e cache delle pagine per Adobe Commerce. Scopri i comandi CLI, le impostazioni env.php e la verifica della connessione.
feature: Configuration, Cache
exl-id: d0baa2a6-8aa8-4f3f-9edf-102d621430e0
badgePaas: label="On-Premises" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Applicabile solo ai progetti locali di Adobe Commerce."
autotag-review: '2026-06-22T22:00:55.389Z'
TQID: 'https://experienceleague.adobe.com/AjJ86dYGRVFuY1T73ct1Gpcf6iDbb4ewP8OiGX8otQs'
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
source-git-commit: 7171e5abfad69ad0f2d3f4c4b5eb57c13d07feb4
workflow-type: tm+mt
source-wordcount: 1315
ht-degree: 0%

---


# Configura Valkey per cache predefinita e di pagina

Commerce fornisce opzioni della riga di comando per configurare l’impostazione predefinita di Valkey e il caching delle pagine. Sebbene sia possibile configurare il caching modificando il file `<Commerce-install-dir>app/etc/env.php`, l&#39;utilizzo della riga di comando è il metodo consigliato, in particolare per le configurazioni iniziali. La riga di comando fornisce la convalida, garantendo che la configurazione sia sintatticamente corretta.

>[!IMPORTANT]
>
>Valkey è richiesto per la configurazione della cache per Adobe Commerce 2.4.9 e le versioni delle patch successive a 2.4.5-p16, 2.4.6-p14, 2.4.7-p9 e 2.4.8-p4. Consulta [Requisiti di sistema](../../installation/system-requirements.md) per i servizi di cache supportati per versione.

{{cloud-cache-config}}

**Prerequisito:**

[Installare Valkey](config-valkey.md#install-valkey) prima di continuare.

## Framework supportati

>[!BEGINTABS]

>[!TAB Cache Zend (2.4.8 e versioni precedenti)]

- **Cache Zend (2.4.8 e versioni precedenti)** — Backend Valkey legacy per Commerce 2.4.8 e versioni precedenti:
   - **Backend Valkey legacy** - Utilizza il percorso completo della classe (`Magento\Framework\Cache\Backend\Valkey`)
   - **Chiavi di precaricamento** - Supporta il precaricamento delle chiavi della cache utilizzate di frequente
   - **Script Lua** — Lua per la raccolta di oggetti inattivi
   - **Compressione** - Supporta la compressione dei dati

>[!TAB Cache Symfony (2.4.9+)]

- **Cache Symfony (2.4.9+)** — A partire da Commerce 2.4.9, la cache Symfony fornisce un&#39;implementazione di caching moderna e conforme a PSR-6 per Valkey, con miglioramenti significativi delle prestazioni:
   - **Piping automatico di Valkey**: batch di più operazioni in singole richieste, riduzione della latenza
   - **TagAwareAdapter** PSR-6: invalidazione efficiente della cache basata su tag con operazioni atomiche
   - **Serializzazione ignorata**: la serializzazione binaria riduce la dimensione della voce della cache del 45% e migliora la velocità del 5-10%
   - **Connessioni permanenti migliorate** — Pool di connessioni più stabili con una migliore gestione dei processi fork
   - **Script Lua ottimizzati** — Esecuzione lato server combinata con pipeline per la massima efficienza

>[!ENDTABS]

## Configurare la memorizzazione in cache predefinita di Valkey

Eseguire il comando `setup:config:set` e specificare i parametri per il caching predefinito di Valkey.

```shell
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-<parameter>=<value>...
```

- `--cache-backend=valkey` abilita il caching predefinito di Valkey. Se questa funzione è già stata abilitata, ometti questo parametro.

- `--cache-backend-valkey-<parameter>=<value>` è un elenco di coppie chiave-valore che configurano il caching predefinito:

{{valkey-redis-cli-note}}

| Parametro della riga di comando | Valore | Significato | Valore predefinito |
|---------------------------------| --------- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `cache-backend-valkey-server` | server | Nome host completo, indirizzo IP o percorso assoluto di un socket UNIX. Il valore predefinito `127.0.0.1` indica che Valkey è installato nel server Commerce. | `127.0.0.1` |
| `cache-backend-valkey-port` | porta | Porta di ascolto server Valkey | `6379` |
| `cache-backend-valkey-db` | database | Obbligatorio se si utilizza Valkey sia per la cache predefinita che per quella a pagina intera. Specificare il numero di database di una delle cache; l&#39;altra cache utilizza `0` per impostazione predefinita.<br><br>**Importante**: se si utilizza Valkey per più di un tipo di memorizzazione nella cache, i numeri di database devono essere diversi. Adobe consiglia di assegnare il numero predefinito del database di memorizzazione nella cache a `0`, il numero del database di memorizzazione nella cache delle pagine a `1` e il numero del database di archiviazione della sessione a `2`. | `0` |
| `cache-backend-valkey-password` | password | La configurazione di una password Valkey abilita una delle funzionalità di protezione incorporate: il comando `auth`, che richiede l&#39;autenticazione dei client per accedere al database. La password è configurata direttamente nel file di configurazione di Valkey: `/etc/valkey/valkey.conf` | |
| `cache-backend-valkey-use-lua` | use_lua | Attiva o disattiva LUA. <br><br>**LUA**: Lua consente di eseguire parte della logica dell&#39;applicazione all&#39;interno di Valkey, migliorando le prestazioni e garantendo la coerenza dei dati tramite l&#39;esecuzione atomica. | `0` |
| `cache-backend-valkey-use-lua-on-gc` | use_lua_on_gc | Attiva o disattiva LUA per la raccolta di oggetti inattivi. <br><br>**LUA**: Lua consente di eseguire parte della logica dell&#39;applicazione all&#39;interno di Valkey, migliorando le prestazioni e garantendo la coerenza dei dati tramite l&#39;esecuzione atomica. | `1` |

## Esempio di comando (cache predefinita)

Nell&#39;esempio seguente viene attivato il caching predefinito di Valkey, l&#39;host viene impostato su `127.0.0.1` e il numero del database viene assegnato a `0`. Valkey utilizza i valori predefiniti per tutti gli altri parametri.

```shell
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-server=127.0.0.1 --cache-backend-valkey-db=0
```

{{valkey-redis-cli-note}}

## Configurare il caching delle pagine Valkey

Per configurare il caching delle pagine Valkey in Commerce, eseguire il comando `setup:config:set` con parametri aggiuntivi.

```shell
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-<parameter>=<value>...
```

Con i seguenti parametri:

- `--page-cache=valkey` abilita il caching delle pagine Valkey. Se questa funzione è già stata abilitata, ometti questo parametro.

- `--page-cache-valkey-<parameter>=<value>` è un elenco di coppie chiave-valore che configurano il caching delle pagine:

| Parametro della riga di comando | Valore | Significato | Valore predefinito |
|----------------------------------------| --------- |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `page-cache-valkey-server` | server | Nome host completo, indirizzo IP o percorso assoluto di un socket UNIX. Il valore predefinito `127.0.0.1` indica che Valkey è installato nel server Commerce. | `127.0.0.1` |
| `page-cache-valkey-port` | porta | Porta di ascolto del server Valkey. | `6379` |
| `page-cache-valkey-db` | database | Obbligatorio se si utilizza Valkey sia per la cache predefinita che per quella a pagina intera. Specificare il numero di database di una delle cache; l&#39;altra cache utilizza `0` per impostazione predefinita.<br/>**Importante**: se si utilizza Valkey per più di un tipo di memorizzazione nella cache, i numeri di database devono essere diversi. È consigliabile assegnare il numero predefinito del database di memorizzazione nella cache a `0`, il numero del database di memorizzazione nella cache delle pagine a `1` e il numero del database di archiviazione sessione a `2`. | `0` |
| `page-cache-valkey-password` | password | La configurazione di una password Valkey abilita una delle funzionalità di protezione incorporate: il comando `auth`, che richiede l&#39;autenticazione dei client per accedere al database. Configurare la password nel file di configurazione Valkey: `/etc/valkey/valkey.conf` | |

### Esempio di comando (cache delle pagine)

L&#39;esempio seguente abilita il caching delle pagine Valkey, imposta l&#39;host su `127.0.0.1` e assegna il numero di database a `1`. Tutti gli altri parametri vengono impostati sul valore predefinito.

```shell
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-server=127.0.0.1 --page-cache-valkey-db=1
```

{{valkey-redis-cli-note}}

### Verifica la configurazione dell’ambiente Commerce

L&#39;esecuzione dei comandi per configurare Valkey caching aggiorna la configurazione dell&#39;ambiente Commerce (`<Commerce-install-dir>app/etc/env.php`):

>[!BEGINTABS]

>[!TAB Cache Zend (2.4.8 e versioni precedenti)]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
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

>[!TAB Cache Symfony (2.4.9+)]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => 'valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
        'page_cache' => [
            'backend' => 'valkey',
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

>[!NOTE]
>
>A partire da Commerce 2.4.9, utilizza il tipo di back-end semplificato `'backend' => 'valkey'` invece del percorso completo della classe. La cache di Symfony viene utilizzata automaticamente quando si specifica il nome semplificato.

>[!ENDTABS]

## Configurare opzioni di caching aggiuntive

### Funzione di precaricamento Valkey

Poiché Commerce memorizza i dati di configurazione nella cache di Valkey, puoi precaricare i dati riutilizzati tra le pagine. Per trovare le chiavi che devono essere precaricate, analizza i dati trasferiti da Valkey a Commerce. Adobe consiglia di precaricare i dati caricati su ogni pagina, ad esempio `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES` e `DB_IS_UP_TO_DATE`.

Valkey utilizza `pipeline` per comporre le richieste di caricamento. Le chiavi devono includere il prefisso del database; ad esempio, se il prefisso del database è `061_`, la chiave di precaricamento sarà simile alla seguente: `061_SYSTEM_DEFAULT`

>[!BEGINTABS]

>[!TAB Cache Zend]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => 'valkey',
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

>[!TAB Cache Symfony]

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => '061_',
            'backend' => 'valkey',
            'backend_options' => [
                'server' => 'valkey',
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

>[!ENDTABS]

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

>[!BEGINTABS]

>[!TAB Cache Zend]

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
                'backend_options' => [
                    'server' => 'valkey',
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

>[!TAB Cache Symfony]

```php
    'cache' => [
        'frontend' => [
            'default' => [
                'id_prefix' => 'b0b_',
                'backend' => 'valkey',
                'backend_options' => [
                    'server' => 'valkey',
                    'database' => '0',
                    'port' => '6379',
                    'serializer' => 'igbinary',
                    'compress_data' => '1',
                    'compression_lib' => 'gzip'
                ]
            ],
            'page_cache' => [
                'id_prefix' => 'b0b_'
            ]
        ],
        'allow_parallel_generation' => false
    ],
```

>[!ENDTABS]

## Ottimizzazione delle prestazioni della cache di Symfony

Se si utilizza Symfony Cache, è possibile ottimizzare ulteriormente le prestazioni configurando il serializzatore Igbinary, installando l&#39;estensione PHP e phpredis e abilitando connessioni persistenti.

### Serializzatore igbinario

Il serializzatore Igbinary migliora notevolmente le prestazioni rispetto alla serializzazione predefinita di PHP. Deve essere configurato manualmente in `app/etc/env.php`:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend_options' => [
                'server' => 'valkey',
                'database' => '0',
                'port' => '6379',
                'serializer' => 'igbinary',  // Enable Igbinary serialization
            ]
        ],
        'page_cache' => [
            'backend_options' => [
                'server' => 'valkey',
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

### Estensioni PHP Redis: phpredis vs predis

Commerce 2.4.9+ include il fallback automatico tra phpredis (estensione C nativa) e Predis (libreria PHP pura). Per ottenere prestazioni ottimali, installare phpredis:

**Utilizzo di apt (consigliato per Debian/Ubuntu)**:

```bash
sudo apt-get install php-redis
sudo systemctl restart php-fpm
php -m | grep redis
```

**Utilizzo di pecl (metodo alternativo)**:

```bash
sudo pecl install redis
echo "extension=redis.so" | sudo tee /etc/php/8.3/mods-available/redis.ini
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

Le connessioni persistenti riutilizzano le connessioni Valkey esistenti tra le richieste, fornendo operazioni della cache più veloci del 5-15%. Configura in `app/etc/env.php`:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend_options' => [
                'server' => 'valkey',
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
                'server' => 'valkey',
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

Ecco una configurazione pronta per la produzione che combina tutte le ottimizzazioni delle prestazioni:

```php
'cache' => [
    'frontend' => [
        'default' => [
            'id_prefix' => 'b0b_',
            'backend' => 'valkey',
            'backend_options' => [
                'server' => 'valkey',
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
            'backend' => 'valkey',
            'backend_options' => [
                'server' => 'valkey',
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

## Verifica connessione Valkey

Per verificare che Valkey e Commerce funzionino correttamente:

1. Accedi al server che esegue Valkey e Commerce.
1. Apri un terminale.
1. Controllare la connessione utilizzando il comando `valkey-cli monitor` o il comando `valkey-cli ping`.

Se i comandi vengono eseguiti correttamente, Valkey è in esecuzione e può comunicare con l&#39;applicazione Commerce. In caso di esito negativo, è necessario risolvere un problema di connessione tra Valkey e Commerce.

### Comando di monitoraggio Valkey

```shell
valkey-cli monitor
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
1476826133.883312 [0 127.0.0.1:52369] "hget" "zc:k:ea6_GLOBAL__EVENT_CONFIG_CACHE" "d"
1476826133.898431 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DB_PDO_MYSQL_DDL_STAGING_UPDATE_1" "d"
1476826133.898794 [0 127.0.0.1:52369] "hget" "zc:k:ea6_RESOLVED_STORES_D1BEFA03C79CA0B84ECC488DEA96BC68" "d"
1476826133.905738 [0 127.0.0.1:52369] "hget" "zc:k:ea6_DEFAULT_CONFIG_CACHE_STORE_DEFAULT_10__235__32__1080MAGENTO2" "d"

... more ...

1476826210.634998 [0 127.0.0.1:52439] "hmset" "zc:k:ea6_MVIEW_CONFIG" "d" "a:18:{s:19:\"design_config_dummy\";a:4:{s:7:\"view_id\";s:19:\"design_config_dummy\";s:12:\"action_class\";s:39:\"Magento\\Theme\\Model\\Indexer\\Mview\\Dummy\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:0:{}}s:14:\"customer_dummy\";a:4:{s:7:\"view_id\";s:14:\"customer_dummy\";s:12:\"action_class\";s:42:\"Magento\\Customer\\Model\\Indexer\\Mview\\Dummy\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:0:{}}s:13:\"cms_page_grid\";a:4:{s:7:\"view_id\";s:13:\"cms_page_grid\";s:12:\"action_class\";s:43:\"Magento\\Catalog\\Model\\Indexer\\Category\\Flat\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:1:{s:8:\"cms_page\";a:3:{s:4:\"name\";s:8:\"cms_page\";s:6:\"column\";s:7:\"page_id\";s:18:\"subscription_model\";N;}}}s:21:\"catalog_category_flat\";a:4:{s:7:\"view_id\";s:21:\"catalog_category_flat\";s:12:\"action_class\";s:43:\"Magento\\Catalog\\Model\\Indexer\\Category\\Flat\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:6:{s:23:\"catalog_category_entity\";a:3:{s:4:\"name\";s:23:\"catalog_category_entity\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";N;}s:31:\"catalog_category_entity_decimal\";a:3:{s:4:\"name\";s:31:\"catalog_category_entity_decimal\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:27:\"catalog_category_entity_int\";a:3:{s:4:\"name\";s:27:\"catalog_category_entity_int\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:28:\"catalog_category_entity_text\";a:3:{s:4:\"name\";s:28:\"catalog_category_entity_text\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:31:\"catalog_category_entity_varchar\";a:3:{s:4:\"name\";s:31:\"catalog_category_entity_varchar\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}s:32:\"catalog_category_entity_datetime\";a:3:{s:4:\"name\";s:32:\"catalog_category_entity_datetime\";s:6:\"column\";s:9:\"entity_id\";s:18:\"subscription_model\";s:71:\"Magento\\CatalogStaging\\Model\\Mview\\View\\Category\\Attribute\\Subscription\";}}}s:24:\"catalog_category_product\";a:4:{s:7:\"view_id\";s:24:\"catalog_category_product\";s:12:\"action_class\";s:46:\"Magento\\Catalog\\Model\\Indexer\\Category\\Product\";s:5:\"group\";s:7:\"indexer\";s:13:\"subscriptions\";a:2:{s:23:\"catalog_category_entity\";a:3:{s:4:\"name\";s:23:\"catalog_category_entity\";s:6:\"column\"

... more ...
```

### Comando ping Valkey

```shell
valkey-cli ping
```

Risposta prevista: `PONG`

Se entrambi i comandi sono riusciti, Valkey viene configurato correttamente.

### Controllare i dati compressi

Per verificare i dati di sessione compressi e la cache delle pagine, utilizzare lo strumento [RESP.app](https://flathub.org/apps/app.resp.RESP). Supporta la decompressione automatica dei dati della cache di pagina e della sessione di Commerce 2 e visualizza i dati della sessione PHP in un formato leggibile.

