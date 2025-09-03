---
title: Usa Valkey per la cache predefinita
description: Scopri come configurare Valkey come cache predefinita per Adobe Commerce.
feature: Configuration, Cache
exl-id: d0baa2a6-8aa8-4f3f-9edf-102d621430e0
source-git-commit: dea0ad57a8c4525be9bc442708bdd2495f28d72d
workflow-type: tm+mt
source-wordcount: '1047'
ht-degree: 0%

---


# Usa Valkey per la cache predefinita

Commerce fornisce opzioni della riga di comando per configurare la pagina Valkey e il caching predefinito. Sebbene sia possibile configurare il caching modificando il file `<Commerce-install-dir>app/etc/env.php`, l&#39;utilizzo della riga di comando è il metodo consigliato, in particolare per le configurazioni iniziali. La riga di comando fornisce la convalida, garantendo che la configurazione sia sintatticamente corretta.

È necessario [installare Valkey](config-redis.md#install-redis) prima di continuare.

## Configurare la memorizzazione in cache predefinita di Valkey

Eseguire il comando `setup:config:set` e specificare i parametri per il caching predefinito di Valkey.

```bash
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-<parameter>=<value>...
```

- `--cache-backend=valkey` abilita il caching predefinito di valkey. Se questa funzione è già stata abilitata, ometti questo parametro.

- `--cache-backend-valkey-<parameter>=<value>` è un elenco di coppie chiave-valore che configurano il caching predefinito:

>[!NOTE]
>
>A partire da **Adobe Commerce 2.4.9-alpha2**, **Valkey** ha ufficialmente sostituito Redis negli strumenti CLI a causa di modifiche nelle licenze. Valkey è un fork di Redis e mantiene funzionalità quasi identiche. Per **versioni 2.4.8 e precedenti**, i comandi CLI utilizzati per configurare Valkey rimangono gli stessi di quelli utilizzati per Redis, garantendo una perfetta compatibilità con le versioni precedenti e semplificando la migrazione o il supporto di ambienti doppi. Nell&#39;esempio seguente viene illustrato il comando specifico di Valkey.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-valkey-<parameter>=<value>...
```

| Parametro della riga di comando | Valore | Significato | Valore predefinito |
|---------------------------------| --------- |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `cache-backend-valkey-server` | server | Nome host completo, indirizzo IP o percorso assoluto di un socket UNIX. Il valore predefinito `127.0.0.1` indica che Valkey è installato nel server Commerce. | `127.0.0.1` |
| `cache-backend-valkey-port` | porta | Porta di ascolto server Valkey | `6379` |
| `cache-backend-valkey-db` | database | Obbligatorio se si utilizza Valkey sia per la cache predefinita che per quella a pagina intera. Specificare il numero di database di una delle cache; l&#39;altra cache utilizza `0` per impostazione predefinita.<br><br>**Importante**: se si utilizza Valkey per più di un tipo di memorizzazione nella cache, i numeri di database devono essere diversi. Adobe consiglia di assegnare il numero predefinito del database di memorizzazione nella cache a `0`, il numero del database di memorizzazione nella cache delle pagine a `1` e il numero del database di archiviazione della sessione a `2`. | `0` |
| `cache-backend-valkey-password` | password | La configurazione di una password Valkey abilita una delle funzionalità di protezione incorporate: il comando `auth`, che richiede l&#39;autenticazione dei client per accedere al database. La password è configurata direttamente nel file di configurazione di Valkey: `/etc/valkey/valkey.conf` | |

### Esempio di comando

Nell&#39;esempio seguente viene attivato il caching predefinito di Valkey, l&#39;host viene impostato su `127.0.0.1` e il numero del database viene assegnato a `0`. Valkey utilizza i valori predefiniti per tutti gli altri parametri.

```bash
bin/magento setup:config:set --cache-backend=valkey --cache-backend-valkey-server=127.0.0.1 --cache-backend-valkey-db=0
```

>[!NOTE]
>
>A partire da **Adobe Commerce 2.4.9-alpha2**, **Valkey** ha ufficialmente sostituito Redis negli strumenti CLI a causa di modifiche nelle licenze. Valkey è un fork di Redis e mantiene funzionalità quasi identiche. Per **versioni 2.4.8 e precedenti**, i comandi CLI utilizzati per configurare Valkey rimangono gli stessi di quelli utilizzati per Redis, garantendo una perfetta compatibilità con le versioni precedenti e semplificando la migrazione o il supporto di ambienti doppi. Nell&#39;esempio seguente viene illustrato il comando specifico di Valkey.

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=127.0.0.1 --cache-backend-redis-db=0
```

## Configurare il caching delle pagine

Per configurare il caching delle pagine Valkey in Commerce, eseguire il comando `setup:config:set` con parametri aggiuntivi.

```bash
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-<parameter>=<value>...
```

Con i seguenti parametri:

- `--page-cache=valkey` abilita il caching delle pagine Valkey. Se questa funzione è già stata abilitata, ometti questo parametro.

- `--page-cache-valkey-<parameter>=<value>` è un elenco di coppie chiave-valore che configurano il caching delle pagine:

>[!NOTE]
>
>A partire da **Adobe Commerce 2.4.9-alpha2**, **Valkey** ha ufficialmente sostituito Redis negli strumenti CLI a causa di modifiche nelle licenze. Valkey è un fork di Redis e mantiene funzionalità quasi identiche. Per **versioni 2.4.8 e precedenti**, i comandi CLI utilizzati per configurare Valkey rimangono gli stessi di quelli utilizzati per Redis, garantendo una perfetta compatibilità con le versioni precedenti e semplificando la migrazione o il supporto di ambienti doppi. Nell&#39;esempio seguente viene illustrato il comando specifico di Valkey.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-<parameter>=<value>...
```

| Parametro della riga di comando | Valore | Significato | Valore predefinito |
|------------------------------| --------- |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------| ------------- |
| `page-cache-valkey-server` | server | Nome host completo, indirizzo IP o percorso assoluto di un socket UNIX. Il valore predefinito `127.0.0.1` indica che Valkey è installato nel server Commerce. | `127.0.0.1` |
| `page-cache-valkey-port` | porta | Porta di ascolto del server Valkey. | `6379` |
| `page-cache-valkey-db` | database | Obbligatorio se si utilizza Valkey sia per la cache predefinita che per quella a pagina intera. Specificare il numero di database di una delle cache; l&#39;altra cache utilizza `0` per impostazione predefinita.<br/>**Importante**: se si utilizza Valkey per più di un tipo di memorizzazione nella cache, i numeri di database devono essere diversi. È consigliabile assegnare il numero predefinito del database di memorizzazione nella cache a `0`, il numero del database di memorizzazione nella cache delle pagine a `1` e il numero del database di archiviazione sessione a `2`. | `0` |
| `page-cache-valkey-password` | password | La configurazione di una password Valkey abilita una delle funzionalità di protezione incorporate: il comando `auth`, che richiede l&#39;autenticazione dei client per accedere al database. Configurare la password nel file di configurazione Valkey: `/etc/valkey/valkey.conf` | |

### Esempio di comando

L&#39;esempio seguente abilita il caching delle pagine Valkey, imposta l&#39;host su `127.0.0.1` e assegna il numero di database a `1`. Tutti gli altri parametri vengono impostati sul valore predefinito.

```bash
bin/magento setup:config:set --page-cache=valkey --page-cache-valkey-server=127.0.0.1 --page-cache-valkey-db=1
```

>[!NOTE]
>
>A partire da **Adobe Commerce 2.4.9-alpha2**, **Valkey** ha ufficialmente sostituito Redis negli strumenti CLI a causa di modifiche nelle licenze. Valkey è un fork di Redis e mantiene funzionalità quasi identiche. Per **versioni 2.4.8 e precedenti**, i comandi CLI utilizzati per configurare Valkey rimangono gli stessi di quelli utilizzati per Redis, garantendo una perfetta compatibilità con le versioni precedenti e semplificando la migrazione o il supporto di ambienti doppi. Nell&#39;esempio seguente viene illustrato il comando specifico di Valkey.

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=127.0.0.1 --page-cache-valkey-db=1
```

## Risultati

Come risultato dei due comandi di esempio, Commerce aggiunge righe simili alle seguenti a `<Commerce-install-dir>app/etc/env.php`:

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

## Nuova implementazione cache Valkey

[!BADGE 2.4.9-alfa]{type=Negative tooltip="Disponibile solo in 2.4.9-alfa."}

A partire dalla versione Adobe Commerce 2.4.9, Adobe consiglia di utilizzare l&#39;implementazione della cache Valkey: `\Magento\Framework\Cache\Backend\Valkey`.

```php
'cache' => [
    'frontend' => [
        'default' => [
            'backend' => '\\Magento\\Framework\\Cache\\Backend\\Valkey',
            'backend_options' => [
                'server' => '127.0.0.1',
                'database' => '0',
                'port' => '6379'
            ],
        ],
],
```

## Funzione di precaricamento Valkey

Poiché Commerce memorizza i dati di configurazione nella cache di Valkey, puoi precaricare i dati riutilizzati tra le pagine. Per trovare le chiavi che devono essere precaricate, analizza i dati trasferiti da Valkey a Commerce. Adobe consiglia di precaricare i dati caricati su ogni pagina, ad esempio `SYSTEM_DEFAULT`, `EAV_ENTITY_TYPES` e `DB_IS_UP_TO_DATE`.

Valkey utilizza `pipeline` per comporre le richieste di caricamento. Le chiavi devono includere il prefisso del database; ad esempio, se il prefisso del database è `061_`, la chiave di precaricamento sarà simile alla seguente: `061_SYSTEM_DEFAULT`

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

Quando si utilizza la funzione di precaricamento con una cache L2, è necessario aggiungere il suffisso `:hash` alle chiavi. La cache L2 trasferisce solo l’hash dei dati, non i dati effettivi.

```php
'preload_keys' => [
    '061_EAV_ENTITY_TYPES:hash',
    '061_GLOBAL_PLUGIN_LIST:hash',
    '061_DB_IS_UP_TO_DATE:hash',
    '061_SYSTEM_DEFAULT:hash',
],
```

## Generazione parallela

A partire dalla versione di Commerce 2.4.0, Adobe ha introdotto l&#39;opzione `allow_parallel_generation` per gli utenti che desiderano eliminare le attese per i blocchi.
È disabilitato per impostazione predefinita e Adobe consiglia di disabilitarlo fino a quando non si dispone di configurazioni e/o blocchi eccessivi.

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
                'backend' => 'Magento\\Framework\\Cache\\Backend\\Valkey',
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

## Verifica connessione Valkey

Per verificare che Valkey e Commerce funzionino correttamente, accedere al server che esegue Valkey, aprire un terminale e utilizzare il comando `valkey-cli monitor` o il comando `redis-cli ping`.

### Comando di monitoraggio Valkey

```bash
valkey-cli monitor
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

### Comando ping Valkey

```bash
redis-cli ping
```

Risposta prevista: `PONG`

Se entrambi i comandi sono riusciti, Valkey viene configurato correttamente.

### Analisi dei dati compressi

Per verificare i dati di sessione compressi e la cache delle pagine, [RESP.app](https://flathub.org/apps/app.resp.RESP) supporta la decompressione automatica della cache delle pagine e delle sessioni di Commerce 2 e visualizza i dati di sessione PHP in un formato leggibile dall&#39;utente.
