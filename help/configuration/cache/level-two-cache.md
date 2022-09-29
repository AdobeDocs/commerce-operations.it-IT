---
title: Configurazione della cache L2
description: Scopri come configurare la cache L2.
source-git-commit: e5e4cf0b3979a457e706823dd16c88508ec4abd8
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Configurazione della cache L2

La memorizzazione in cache consente di ridurre il traffico di rete tra l’archiviazione della cache remota e l’applicazione Commerce. Un’istanza Commerce standard trasferisce circa 300 kb per richiesta e il traffico potrebbe rapidamente aumentare fino a oltre circa 1000 richieste in alcune situazioni.

Per ridurre la larghezza di banda della rete a Redis, memorizza i dati della cache localmente su ogni nodo web e utilizza la cache remota per due scopi:

- Controlla la versione dei dati della cache e assicurati che la cache più recente sia memorizzata localmente
- Trasferisci la cache più recente dal computer remoto al computer locale

Commerce memorizza la versione dei dati con hash in Redis, con il suffisso &#39;:hash&#39; aggiunto alla chiave regolare. Se è presente una cache locale obsoleta, i dati vengono trasferiti al computer locale con una scheda di cache.

>[!INFO]
>
>Per Adobe Commerce sull’infrastruttura cloud, considera le best practice in [Implementazione estesa della cache Redis](https://support.magento.com/hc/en-us/articles/360049292532) articolo di supporto.

## Esempio di configurazione

Utilizza l’esempio seguente per modificare o sostituire la sezione di cache esistente nel `app/etc/env.php` file.

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
                ],
                'use_stale_cache' => false,
            ],
            'frontend_options' => [
                'write_control' => false,
            ],
        ]
    ],
    'type' => [
        'default' => ['frontend' => 'default'],
    ],
],
```

Dove:

- `backend` è l’implementazione della cache L2.
- `backend_options` è la configurazione della cache L2.
   - `remote_backend` è l’implementazione della cache remota: Redis o MySQL.
   - `remote_backend_options` è la configurazione della cache remota.
   - `local_backend` è l’implementazione della cache locale: `Cm_Cache_Backend_File`
   - `local_backend_options` è la configurazione della cache locale.
      - `cache_dir` è un’opzione specifica della cache del file per la directory in cui è memorizzata la cache locale.
   - `use_stale_cache` è un flag che abilita o disabilita l’utilizzo di cache obsoleta.

Adobe consiglia di utilizzare Redis per la memorizzazione in cache remota (`\Magento\Framework\Cache\Backend\Redis`) e `Cm_Cache_Backend_File` per il caching locale dei dati nella memoria condivisa, utilizzando: `'local_backend_options' => ['cache_dir' => '/dev/shm/']`

L&#39;Adobe raccomanda l&#39;uso del [`cache preload`](redis-pg-cache.md#redis-preload-feature) in quanto riduce drasticamente la pressione su Redis. Non dimenticare di aggiungere il suffisso &#39;:hash&#39; per le chiavi di precaricamento.

## Opzioni cache obsolete

Inizia con [!DNL Commerce] 2.4 `use_stale_cache` in alcuni casi specifici, le prestazioni possono essere migliorate.

Generalmente, il compromesso con blocco in attesa è accettabile dal lato delle prestazioni, ma più grande è il numero di blocchi o cache che il commerciante ha, più tempo è speso in attesa di blocchi. In alcuni scenari, puoi aspettare un **numero di chiavi** \* **timeout ricerca** quantità di tempo per il processo. In alcuni rari casi, il commerciante può avere centinaia di chiavi `Block/Config` cache, quindi anche un piccolo timeout di ricerca per il blocco può costare secondi.

La cache obsoleta funziona solo con una cache L2. Con una cache obsoleta, puoi inviare una cache obsoleta, mentre una nuova viene generata in un processo parallelo. Per abilitare la cache obsoleta, aggiungi `'use_stale_cache' => true` alla configurazione superiore della cache L2.

L&#39;Adobe consiglia di abilitare il `use_stale_cache` solo per i tipi di cache che ne beneficiano di più, tra cui:

- `block_html`
- `config_integration_api`
- `config_integration`
- `full_page`
- `layout`
- `reflection`
- `translate`

Il codice seguente mostra una configurazione di esempio:

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
                ],
                'use_stale_cache' => false,
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
