---
title: Configurazione cache L2 per l'ottimizzazione delle prestazioni
description: Scopri come configurare la cache L2 in Adobe Commerce per ridurre il traffico di rete e migliorare le prestazioni. Scopri le opzioni di implementazione legacy e Symfony.
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
badgePaas: label="On-Premises" type="Informative" url="https://experienceleague.adobe.com/it/docs/commerce/user-guides/product-solutions" tooltip="Applicabile solo ai progetti Adobe Commerce on Premises."
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
source-git-commit: d9152906a6fbbd765a60e3aeacdbf7cc7527529d
workflow-type: tm+mt
source-wordcount: 1166
ht-degree: 0%

---

# Configurazione della cache L2 per l&#39;ottimizzazione delle prestazioni

La memorizzazione nella cache L2 (a due livelli) riduce il traffico di rete tra lo storage della cache remota (Redis o Valkey) e l&#39;applicazione Commerce aggiungendo un livello di cache locale su ciascun nodo web. Un’istanza Commerce standard trasferisce circa 300 KB per richiesta e in alcune situazioni il traffico può superare rapidamente le 1000 richieste.

Con il caching L2, ogni nodo web memorizza localmente i dati a cui si accede di frequente e utilizza la cache remota per due scopi:

- Verifica della versione dei dati della cache per verificare che la cache più recente sia memorizzata localmente
- Trasferimento dei dati della cache aggiornati dall&#39;archivio remoto al computer locale

Commerce memorizza la versione con hash dei dati nella cache remota, aggiungendo il suffisso `:hash` alla chiave regolare. Quando la cache locale non è aggiornata, i dati vengono recuperati dal computer remoto tramite un adattatore cache.

Sono disponibili due implementazioni di cache L2:

| Implementazione | Versione | Descrizione |
| -------------- | ------- | ----------- |
| [Legacy (`RemoteSynchronizedCache`)](#legacy-l2-cache-configuration-remotesynchronizedcache) | &lt;2.4.9 | Cache a due livelli basata su Zend con `Cm_Cache_Backend_File` per l&#39;archiviazione locale |
| [Moderno (`symfony_l2`)](#modern-symfony-l2-cache-implementation) | 2.4.9+ | L2 basato su Symfony Cache con conformità PSR-6 e prestazioni migliorate. Supporta solo Valkey. |

## Configurazione cache L2 legacy (RemoteSynchronizedCache)

>[!NOTE]
>
>Le istruzioni di configurazione della cache L2 legacy si applicano alle versioni precedenti di Adobe Commerce. Se utilizzi Adobe Commerce versione 2.4.9 o successiva, usa Valkey con [Symfony 2 per cache L2](#modern-symfony-l2-cache-implementation).

Le istruzioni di configurazione della cache dipendono dal tipo di distribuzione:

- **Per Adobe Commerce su Cloud**, configurare la cache L2 impostando la variabile di distribuzione [`REDIS_BACKEND`](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html?lang=it#redis_backend) o [`VALKEY_BACKEND`](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/configure/env/stage/variables-deploy#valkey_backend) in `.magento.env.yaml`. Per esempi di configurazione, vedere [Configurare la cache L2](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-l2-cache).

- **Per le versioni locali di Adobe Commerce che supportano Redis**, utilizzare l&#39;esempio seguente per modificare o sostituire la sezione della cache esistente nel file `app/etc/env.php`.

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
  - `local_backend` è l&#39;implementazione della cache locale: `Cm_Cache_Backend_File`
  - `local_backend_options` è la configurazione della cache locale.
  - `cache_dir` è un&#39;opzione specifica della cache del file per la directory in cui è memorizzata la cache locale.

Per Adobe Commerce, Adobe consiglia di utilizzare Redis per il caching remoto (`\Magento\Framework\Cache\Backend\Redis`) e `Cm_Cache_Backend_File` per il caching locale dei dati nella memoria condivisa, utilizzando: `'local_backend_options' => ['cache_dir' => '/dev/shm/']`

Adobe consiglia di utilizzare la funzionalità [`cache preload`](redis-pg-cache.md#redis-preload-feature), in quanto riduce drasticamente la pressione su Redis. Non dimenticare di aggiungere il suffisso &#39;:hash&#39; per le chiavi di precaricamento.

## Opzioni cache non aggiornate

A partire da Commerce 2.4, l&#39;opzione `use_stale_cache` può migliorare le prestazioni in casi specifici fornendo i dati precedentemente memorizzati nella cache mentre i nuovi dati della cache vengono generati in un processo parallelo.

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

Il codice seguente mostra un esempio di configurazione:

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

>[!NOTE]
>
>Per Adobe Commerce on Cloud, il pacchetto di strumenti ECE (`ece-tools`) gestisce automaticamente questa configurazione. Non modificare direttamente `app/etc/env.php`. La distribuzione sovrascrive le modifiche manuali. Per la configurazione cloud, vedi [Configurare la cache L2 di Symfony](../../implementation-playbook/best-practices/planning/redis-valkey-service-configuration.md#configure-symfony-l2-cache).

>[!IMPORTANT]
>
>{{redis-cache-support}}
>
>Poiché `symfony_l2` è disponibile solo in Adobe Commerce 2.4.9 e versioni successive, configurarlo con Valkey come back-end remoto. Redis non è un back-end remoto ufficialmente supportato per `symfony_l2`. Consulta [Requisiti di sistema](../../installation/system-requirements.md) per i servizi di cache supportati per versione.

### Vantaggi della cache L2 di Symfony

- **Architettura moderna**: basata sui componenti della cache di Symfony (conforme a PSR-6)
- **Prestazioni migliori**: supporto nativo per la serializzazione Igbinary, la compressione Gzip e gli script Lua
- **Connessioni persistenti**: riduce il sovraccarico della connessione Valkey con il connection pooling
- **Chiavi di precaricamento**: supporta il precaricamento della chiave della cache per i dati critici
- **Supporto cache non aggiornata**: piena compatibilità con l&#39;opzione `use_stale_cache`
- **Configurazione semplificata**: nomi dei tipi di back-end di pulizia (`valkey`, `file`)

### Esempio di configurazione con cache L2 Symfony

Utilizza il tipo di back-end `symfony_l2` semplificato per la cache L2:

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
                    'persistent_id' => 'magento_l2_default',
                    'timeout' => '2.5',
                    'read_timeout' => '2.0',
                    'use_lua' => '1',
                    'preload_keys' => [
                        'prefix_EAV_ENTITY_TYPES:hash',
                        'prefix_GLOBAL_PLUGIN_LIST:hash',
                        'prefix_DB_IS_UP_TO_DATE:hash',
                        'prefix_SYSTEM_DEFAULT:hash',
                    ],
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

Configurare front-end separati per il supporto della cache non aggiornata:

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
|--------|------|---------|-------------------------------------------------------------------|
| `remote_backend` | stringa | `'valkey'` | Tipo di back-end remoto: `valkey` o `file`. Usa `valkey` per la cache L2. |
| `remote_backend_options` | array | `[]` | Configurazione back-end remota (consulta la documentazione di Valkey) |
| `local_backend` | stringa | `'file'` | Tipo di back-end locale: `file` o `apcu` |
| `local_backend_options` | array | `[]` | Configurazione back-end locale |
| `cleanup_percentage` | numero intero | `95` | Soglia pulizia cache L1 (1-100) |
| `use_stale_cache` | booleano | `false` | Abilita cache non aggiornata per un&#39;elevata disponibilità |

>[!NOTE]
>
>L&#39;opzione `remote_backend` accetta anche un valore di `redis`. Tuttavia, Redis non è un servizio di cache ufficialmente supportato per Adobe Commerce 2.4.9 e versioni successive. Adobe consiglia di configurare `symfony_l2` solo con `valkey`. Consulta [Requisiti di sistema](../../installation/system-requirements.md) per i servizi di cache supportati per versione.

### Prestazioni e affidabilità migliorate della cache L2 di Symfony

>[!NOTE]
>
>Questi miglioramenti si applicano alle distribuzioni di Adobe Commerce 2.4.9 che utilizzano `symfony_l2` e sono disponibili con la patch ACP2E-5132. Per le ultime note sulla versione della patch, consulta [Patch cloud per Commerce](https://experienceleague.adobe.com/it/docs/commerce-on-cloud/user-guide/release-notes/cloud-patches#latest).

#### Memorizzazione tag cache L2 ottimizzata di Symfony

È stato ottimizzato il comportamento della cache L2 di Symfony per le distribuzioni con supporto Valkey, eliminando le scritture ridondanti dell’indice dei tag del file system. I tag cache sono ora memorizzati esclusivamente in Valkey, allineando il comportamento della cache di Symfony L2 con l’implementazione della cache legacy. In questo modo si riduce l&#39;I/O del disco non necessario, si migliorano le prestazioni di scrittura della cache e si impedisce la crescita della directory `var/cache/symfony/tags/`.

#### Miglioramento del comportamento della cache basata su file

Per le distribuzioni che utilizzano la cache basata su file (senza Valkey), l’indice dei tag locali continua a essere mantenuto per supportare l’invalidamento della cache. L&#39;indice dei tag viene ora scritto nel percorso `cache_dir` configurato anziché nel percorso `var/cache` codificato in precedenza, garantendo un utilizzo coerente della directory della cache e un supporto migliorato per le configurazioni della cache personalizzata.

#### Annullamento della validità della cache migliorato

L’annullamento della validità della cache ora utilizza blocchi di rigenerazione basati su TTL con la pulizia corretta dei tag L1, eliminando le voci della cache non aggiornate che in precedenza potevano persistere dopo l’annullamento della validità dei tag.

#### Compressione attivata per impostazione predefinita

La compressione Redis/Valkey (`compress_data`) è ora attivata per impostazione predefinita per la cache L2 di Symfony, riducendo il consumo di memoria e il traffico di rete e allineandola al comportamento predefinito dell&#39;implementazione della cache legacy.

#### Impatto

- Elimina le scritture ridondanti dell&#39;indice dei tag del file system per le distribuzioni della cache Symfony L2 con supporto Valkey.
- Riduce l&#39;I/O del disco e migliora le prestazioni di scrittura della cache.
- Impedisce la crescita non necessaria della directory `var/cache/symfony/tags/`.
- Garantisce che le distribuzioni della cache basate su file utilizzino in modo coerente `cache_dir` configurato, mantenendo al contempo il comportamento di invalidamento della cache.
- Elimina le voci di cache non aggiornate tramite blocchi di rigenerazione basati su TTL e la pulizia corretta dei tag L1.
- Riduce il consumo di memoria e il traffico di rete con `compress_data` abilitato per impostazione predefinita.

Per opzioni di configurazione dettagliate, vedi:
- [Configurazione della cache di Valkey con Symfony Cache](valkey-pg-cache.md)

