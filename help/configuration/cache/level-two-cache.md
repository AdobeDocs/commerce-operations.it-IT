---
title: Configurazione cache L2
description: Scopri come configurare la cache L2.
feature: Configuration, Cache
exl-id: 0504c6fd-188e-46eb-be8e-968238571f4e
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# Configurazione cache L2

Il caching consente una riduzione del traffico di rete tra lo storage della cache remota e l’applicazione Commerce. Un’istanza Commerce standard trasferisce circa 300 kb per richiesta e, in alcune situazioni, il traffico può crescere rapidamente fino a oltre ~1000 richieste.

Per ridurre la larghezza di banda di rete a Redis, memorizzare i dati della cache localmente su ciascun nodo web e utilizzare la cache remota per due scopi:

- Controlla la versione dei dati della cache e assicurati che la cache più recente sia memorizzata localmente
- Trasferisci la cache più recente dal computer remoto al computer locale

Commerce memorizza la versione con hash dei dati in Redis, aggiungendo il suffisso &#39;:hash&#39; alla chiave regolare. Se è presente una cache locale obsoleta, i dati vengono trasferiti al computer locale con un adattatore della cache.

>[!INFO]
>
>Per l’infrastruttura cloud di Adobe Commerce, puoi utilizzare [distribuire variabili](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_backend) per configurazione cache L2.

## Esempio di configurazione

Utilizza l’esempio seguente per modificare o sostituire la sezione della cache esistente nel `app/etc/env.php` file.

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
      - `cache_dir` è un&#39;opzione specifica della cache del file per la directory in cui è memorizzata la cache locale.
   - `use_stale_cache` è un flag che abilita o disabilita l’utilizzo di cache non aggiornata.

L’Adobe consiglia di utilizzare Redis per il caching remoto (`\Magento\Framework\Cache\Backend\Redis`) e `Cm_Cache_Backend_File` per il caching locale dei dati nella memoria condivisa, utilizzando: `'local_backend_options' => ['cache_dir' => '/dev/shm/']`

L’Adobe raccomanda l’utilizzo del [`cache preload`](redis-pg-cache.md#redis-preload-feature) in quanto riduce drasticamente la pressione su Redis. Non dimenticare di aggiungere il suffisso &#39;:hash&#39; per i tasti di precaricamento.

## Opzioni cache non aggiornate

A partire da [!DNL Commerce] 2.4, il `use_stale_cache` in alcuni casi specifici.

In genere, il compromesso con l’attesa di blocco è accettabile dal lato delle prestazioni, ma più è grande il numero di Blocchi o Cache di cui dispone il commerciante, maggiore è il tempo impiegato per attendere i blocchi. In alcuni scenari, puoi attendere un **numero di chiavi** \* **timeout ricerca** tempo per il processo. In alcuni rari casi, il commerciante può avere centinaia di chiavi nel `Block/Config` cache, quindi anche un timeout di ricerca ridotto per il blocco può costare secondi.

La cache non aggiornata funziona solo con una cache L2. Con una cache non aggiornata, puoi inviare una cache obsoleta, mentre una nuova viene generata in un processo parallelo. Per abilitare la cache non aggiornata, aggiungere `'use_stale_cache' => true` alla configurazione superiore della cache L2.

L’Adobe consiglia di abilitare `use_stale_cache` solo per i tipi di cache che ne beneficiano maggiormente, tra cui:

- `block_html`
- `config_integration_api`
- `config_integration`
- `full_page`
- `layout`
- `reflection`
- `translate`

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
