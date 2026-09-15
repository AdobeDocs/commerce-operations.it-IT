---
title: Configurazione cache L2 per l'ottimizzazione delle prestazioni
description: Scopri come configurare la cache L2 in Adobe Commerce on-premise per ridurre il traffico di rete e migliorare le prestazioni. Confronta l’implementazione legacy di RemoteSynchronizedCache con la moderna implementazione di Symfony L2.
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
badgePaas: label="On-Premises" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Applicabile solo ai progetti Adobe Commerce on Premises."
TQID: 'https://experienceleague.adobe.com/7vswBqyn9UZLmaeirgPRZ4xEQH5F66XUEtY5hPkz9NY'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
    internal-label: Commerce on Prem
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: b5f00040-57a0-4a6d-a39e-383b1936c2c9
    internal-label: Compliance
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: e8818fe6-9c8b-4bc0-9ef8-377a10b7bc75
    internal-label: Architecture
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
    internal-label: Implementation
  - id: cdd65e7e-8839-44a2-bc21-0e03623b5dd1
    internal-label: Optimization
source-git-commit: ea07c4a7e42988b2ede3511273261fa7d560b652
workflow-type: tm+mt
source-wordcount: '1686'
ht-degree: 0%
---
# Configurazione della cache L2 per l&#39;ottimizzazione delle prestazioni

Il caching L2 (a due livelli) riduce il traffico di rete tra il servizio di cache remota e l’applicazione Commerce aggiungendo un livello di cache locale su ciascun nodo web. Un’istanza Commerce standard può trasferire circa 300 KB per richiesta. Con volumi di richiesta elevati, il traffico di rete risultante può essere considerevole.

Con il caching L2, ogni nodo web memorizza localmente i dati a cui si accede di frequente e utilizza la cache remota per due scopi:

- Verifica della versione dei dati della cache per verificare che la cache più recente sia memorizzata localmente
- Trasferimento dei dati della cache aggiornati dal servizio cache remota al computer locale

Commerce memorizza la versione con hash dei dati nella cache remota, aggiungendo il suffisso `:hash` alla chiave regolare. Quando la cache locale è obsoleta, i dati vengono recuperati dal servizio cache remota tramite un adattatore cache.

L’implementazione della cache L2 disponibile dipende dalla versione e dal livello di patch di Commerce:

| Implementazione | Versione Commerce | Servizio cache remota | Descrizione |
| -------------- | ---------------- | -------------------- | ----------- |
| [`RemoteSynchronizedCache`](#remotesynchronizedcache-l2-cache-configuration) | Prima della versione 2.4.9, se supportato | Redis o Valkey, a seconda della versione e del livello di patch | Cache a due livelli basata su Zend con `Cm_Cache_Backend_File` per l&#39;archiviazione locale |
| [Symfony L2 (`symfony_l2`)](#symfony-l2-cache-implementation) | 2.4.9 e versioni successive | Valkey | Implementazione L2 moderna basata su Symfony Cache con conformità PSR-6 |

## Configurazione cache L2 RemoteSynchronizedCache


>[!NOTE]
>
>Questa sezione descrive la configurazione L2 di `RemoteSynchronizedCache` per le versioni locali di Adobe Commerce precedenti alla 2.4.9, supportata dalla matrice di supporto a livello di patch e versione di Commerce esatta.
>
>Per Adobe Commerce 2.4.9 e versioni successive, utilizzare Valkey con [cache L2 Symfony](#symfony-l2-cache-implementation).
>
>Per l&#39;infrastruttura Adobe Commerce on Cloud, configurare la cache L2 tramite le variabili di distribuzione in `.magento.env.yaml`. Non modificare `app/etc/env.php` direttamente. Vedere [Configurare la cache L2](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-l2-cache).

Le istruzioni di configurazione della cache dipendono dalla versione di Commerce in uso:

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
  - `remote_backend` è l&#39;implementazione della cache remota: Redis o Valkey, a seconda della versione di Commerce e del supporto a livello di patch.
  - `remote_backend_options` è la configurazione della cache remota.
  - `local_backend` è l&#39;implementazione della cache locale: `Cm_Cache_Backend_File`.
  - `local_backend_options` è la configurazione della cache locale.
  - `cache_dir` è un&#39;opzione specifica per la cache dei file che definisce la directory in cui è memorizzata la cache locale.

Per le versioni di Adobe Commerce precedenti alla 2.4.9 che supportano Redis o Valkey, Adobe consiglia di utilizzare Redis o Valkey per il caching remoto, come supportato dalla versione esatta, e `Cm_Cache_Backend_File` per il caching locale. La cache locale viene comunemente archiviata in un file system temporaneo, ad esempio `/dev/shm/`:

```php
'local_backend_options' => [
    'cache_dir' => '/dev/shm/'
]
```

Adobe consiglia di utilizzare la funzione `[cache preload](redis-pg-cache.md#redis-preload-feature)`, in quanto riduce il carico su Redis. Assicurarsi di aggiungere il suffisso `:hash` per le chiavi di precaricamento.

## Opzioni cache non aggiornate

A partire da Commerce 2.4, l&#39;opzione `use_stale_cache` può migliorare le prestazioni in casi specifici fornendo i dati precedentemente memorizzati nella cache mentre i nuovi dati della cache vengono generati in un processo parallelo. I tipi di cache consigliati e i compromessi descritti in questa sezione si applicano sia alle implementazioni `RemoteSynchronizedCache` che a quelle `symfony_l2`. Per un esempio di configurazione di `symfony_l2`, vedere [Cache L2 Symfony con cache non aggiornata](#symfony-l2-cache-with-stale-cache).

In genere, il compromesso con l’attesa di blocco è accettabile dal punto di vista delle prestazioni. Tuttavia, con l’aumento del numero di blocchi o voci della cache, le attese dei blocchi richiedono più tempo. In alcuni scenari, l&#39;attesa può essere pari a **il numero di chiavi** x **timeout ricerca** per il processo. In rari casi, un utente può avere centinaia di chiavi nella cache `Block/Config`, quindi anche un piccolo timeout di ricerca per un blocco può costare secondi.

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

Il codice seguente mostra un esempio di configurazione per il backend `RemoteSynchronizedCache`. Per un esempio di `symfony_l2`, vedere [Cache L2 Symfony con cache non aggiornata](#symfony-l2-cache-with-stale-cache).

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

## Implementazione della cache L2 di Symfony

Nelle versioni di Commerce 2.4.9+, utilizza l&#39;implementazione della cache L2 di Symfony (`symfony_l2` backend) invece di `RemoteSynchronizedCache`. La cache L2 di Symfony fornisce un’implementazione di caching conforme a PSR-6 utilizzando Valkey.

>[!IMPORTANT]
>
>Redis non è supportato per la configurazione della cache nelle seguenti versioni di Adobe Commerce:
>
>- Adobe Commerce 2.4.9 e versioni successive
>- Adobe Commerce 2.4.8-p4 e versioni successive
>- Adobe Commerce 2.4.7-p9 e versioni successive
>- Adobe Commerce 2.4.6-p14 e versioni successive
>- Adobe Commerce 2.4.5-p16 e versioni successive
>
>Per queste versioni, configura Valkey.
>
>Se si configura `symfony_l2` per il caching L2 in Adobe Commerce 2.4.9 o versione successiva, è necessario utilizzare Valkey per il servizio di cache remota. Vedere [configurare Valkey](config-valkey.md).

### Migrazione da RemoteSynchronizedCache a Symfony L2

Se si sta aggiornando un&#39;installazione locale dal backend `RemoteSynchronizedCache` a `symfony_l2`, controllare quanto segue prima di aggiornare `app/etc/env.php`. La modifica solo del valore `backend` non è sufficiente. La struttura della configurazione, i nomi delle chiavi e alcuni comportamenti predefiniti sono diversi.

- **La struttura della configurazione cambia.** `remote_backend`, `remote_backend_options` e `local_backend` utilizzano valori diversi in `symfony_l2`. Ad esempio, `remote_backend` diventa `'valkey'` invece del nome completo della classe. Utilizza l&#39;[esempio di configurazione](#configuration-example-with-symfony-l2-cache) di seguito come punto di partenza, anziché modificare la configurazione di `RemoteSynchronizedCache` esistente.

- **`preload_keys`non è consigliato con `symfony_l2`.** Se la configurazione di `RemoteSynchronizedCache` include `preload_keys`, rimuoverlo come parte della migrazione. Il precaricamento delle chiavi non migliora le prestazioni in `symfony_l2` e può aumentare il carico su Valkey attivando ulteriori ricerche di chiavi non necessarie.

- **La compressione richiede un flag esplicito.** L&#39;impostazione di `compression_lib` da sola non abilita la compressione in `symfony_l2`. Vedere [Opzioni di back-end per la cache L2 di Symfony](#backend-options-for-symfony-l2-cache) per l&#39;impostazione `compress_data` richiesta.

- **Le distribuzioni locali configurate manualmente non abilitano la cache non aggiornata per impostazione predefinita.** `use_stale_cache` utilizza `false` come impostazione predefinita in `symfony_l2` (vedi la [tabella delle opzioni di back-end](#backend-options-for-symfony-l2-cache)). Se la configurazione di `RemoteSynchronizedCache` ha utilizzato il front-end `stale_cache_enabled`, è necessario ricrearlo in modo esplicito utilizzando il pattern nella cache di [Symfony L2 con cache non aggiornata](#symfony-l2-cache-with-stale-cache).

>[!NOTE]
>
>Adobe Commerce sugli ambienti cloud che impostano la variabile di distribuzione `VALKEY_BACKEND: symfony_l2` dispongono di una configurazione L2 completa, incluso il front-end `stale_cache_enabled`, generata automaticamente da `ece-tools`. Consulta [Configurare la cache L2 di Symfony](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-symfony-l2-cache) per il comportamento specifico di Cloud.

- **Redis non è un back-end remoto supportato per `symfony_l2`.** Esegui la migrazione a Valkey come parte di questa modifica. Vedere [configurare Valkey](config-valkey.md).

### Esempio di configurazione con cache L2 Symfony

>[!IMPORTANT]
>
>Questo esempio di `app/etc/env.php` si applica solo alle installazioni locali. Per l&#39;infrastruttura Adobe Commerce on Cloud, non modificare direttamente `app/etc/env.php`. Imposta `VALKEY_BACKEND: symfony_l2` in `.magento.env.yaml`. `ece-tools` genera e gestisce la configurazione della cache L2 durante la distribuzione. Vedere [Configurare la cache L2 di Symfony](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-symfony-l2-cache).

Nel file `app/etc/env.php`, utilizzare il tipo di back-end `symfony_l2` semplificato per la cache L2. Questo esempio non include la configurazione `preload_keys`, che non è consigliata con `symfony_l2`. Per ulteriori dettagli, vedere [Migrazione da RemoteSynchronizedCache a Symfony L2](#migrating-from-remotesynchronizedcache-to-symfony-l2).

L&#39;esempio imposta `cleanup_percentage` su `90`. Il valore predefinito è `95`. Regola questo valore in base allo storage della cache locale disponibile e ai requisiti della distribuzione Commerce.

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
| -------- | ------ | --------- | ----------- |
| `remote_backend` | stringa | `'valkey'` | Back-end della cache remota. Utilizza `valkey` con Symfony L2. Redis non è ufficialmente supportato. |
| `remote_backend_options` | array | `[]` | Configurazione back-end Valkey remota |
| `local_backend` | stringa | `'file'` | Tipo di back-end locale: `file` o `apcu` |
| `local_backend_options` | array | `[]` | Configurazione back-end locale |
| `cleanup_percentage` | numero intero | `95` | Soglia di pulizia della cache L1, espressa come percentuale da 1 a 100 |
| `use_stale_cache` | booleano | `false` | Abilita la cache non aggiornata per il front-end |
| `compress_data` | booleano | `false` | Abilita la compressione se combinata con `compression_lib`. Imposta questa opzione nelle opzioni di back-end remote di Valkey. |
| `persistent` | booleano | `true` | Controlla le connessioni permanenti al backend remoto. Impostato su `false` (`'0'`) per corrispondere al comportamento della cache Zend, che viene impostato automaticamente su connessioni non persistenti. |

>[!NOTE]
>
>L&#39;opzione `frontend_options.write_control` si applica alla configurazione di `RemoteSynchronizedCache` e non a `symfony_l2`.

### Prestazioni e affidabilità migliorate della cache L2 di Symfony

>[!NOTE]
>
>Questi miglioramenti si applicano alle distribuzioni di Adobe Commerce 2.4.9 che utilizzano `symfony_l2` e sono disponibili nella patch ACP2E-5132.
>
>Per Adobe Commerce on-premise, applichi questa patch utilizzando lo strumento Quality Patches (QPT). Per l&#39;infrastruttura Adobe Commerce on Cloud, la patch è inclusa nel pacchetto Patch cloud per Commerce, che è una dipendenza di `ece-tools`. Aggiornare alla versione più recente di `ece-tools` per ricevere le ultime patch di Cloud durante la distribuzione.

Gli aggiornamenti più recenti migliorano la scalabilità della cache di Symfony L2, riducono gli I/O inutili dei file system e migliorano la coerenza e l’affidabilità della cache.

#### Memorizzazione tag cache L2 ottimizzata di Symfony

Per le distribuzioni della cache Symfony L2 con supporto Valkey, i tag della cache sono memorizzati esclusivamente in Valkey. In questo modo si eliminano le scritture ridondanti dell&#39;indice dei tag del file system, si riducono le operazioni di I/O del disco e si evita la crescita inutile della directory `var/cache/symfony/tags/`.

#### Miglioramento del comportamento della cache basata su file

Per le distribuzioni che utilizzano la cache basata su file (senza Valkey), l’indice dei tag locali continua a essere mantenuto per supportare l’invalidamento della cache. L&#39;indice dei tag viene ora scritto nel percorso `cache_dir` configurato anziché nel percorso `var/cache` codificato in precedenza, garantendo un utilizzo coerente della directory della cache e un supporto migliorato per le configurazioni della cache personalizzata.

#### Correzione dell’appartenenza ai tag obsoleti dopo il retagging

Il retagging di una voce della cache può lasciarla associata a tag a cui non appartiene più. Le appartenenze ai tag non aggiornate vengono ora cancellate al momento del retag, pertanto le voci della cache vengono invalidate solo dai tag attualmente assegnati.

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
- Riduce gli stamp di rigenerazione per `use_stale_cache` voci selezionando un singolo generatore per chiave anziché ogni richiesta concorrente di rigenerazione della voce.

Per opzioni di configurazione dettagliate, vedi:

- [Configurazione della cache di Valkey con Symfony Cache](valkey-pg-cache.md)
