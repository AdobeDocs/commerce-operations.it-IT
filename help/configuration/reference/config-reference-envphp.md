---
title: riferimento env.php
description: Consulta un elenco di valori per il file env.php.
exl-id: cf02da8f-e0de-4f0e-bab6-67ae02e9166f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '717'
ht-degree: 0%

---

# riferimento env.php

Il `env.php` Il file contiene le sezioni seguenti:

| Nome | Descrizione |
|-------------------------------|-----------------------------------------------------------------|
| `backend` | Impostazioni per l&#39;area di amministrazione |
| `cache` | Configurare la pagina Redis e la cache predefinita |
| `cache_types` | Impostazioni archiviazione cache |
| `consumers_wait_for_messages` | Configurare il modo in cui i consumatori elaborano i messaggi dalla coda dei messaggi |
| `cron` | Attiva o disattiva i processi cron |
| `crypt` | Chiave di crittografia per le funzioni di crittografia |
| `db` | Impostazioni di connessione al database |
| `default_connection` | Connessione predefinita code di messaggi |
| `directories` | Impostazioni mappatura directory Commerce |
| `downloadable_domains` | Elenco dei domini scaricabili |
| `install` | Data di installazione |
| `lock` | Blocca impostazioni provider |
| `MAGE_MODE` | Il [modalità applicazione](../bootstrap/application-modes.md) |
| `queue` | [Code di messaggi](../queues/manage-message-queues.md) impostazioni |
| `resource` | Mappatura del nome della risorsa su una connessione |
| `session` | Dati archiviazione sessione |
| `system` | Disattiva il campo per la modifica in Admin |
| `x-frame-options` | Impostazione di [x-frame-options][x-frame-options] |

## backend

Configurare **frontName** per l’URL dell’amministratore di Commerce che utilizza `backend` nodo in env.php.

```conf
'backend' => [
  'frontName' => 'admin'
]
```

## cache

Configurare la pagina Redis e il caching predefinito utilizzando `cache` nodo in `env.php` file.

```conf
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
]
```

Ulteriori informazioni in [Configurazione Redis](../cache/redis-pg-cache.md).

## cache_types

Da questo nodo sono disponibili tutte le configurazioni dei tipi di cache.

```conf
'cache_types' => [
  'config' => 1,
  'layout' => 1,
  'block_html' => 1,
  'collections' => 1,
  'reflection' => 1,
  'db_ddl' => 1,
  'compiled_config' => 1,
  'eav' => 1,
  'customer_notification' => 1,
  'config_integration' => 1,
  'config_integration_api' => 1,
  'full_page' => 1,
  'config_webservice' => 1,
  'translate' => 1,
  'vertex' => 1
]
```

Ulteriori informazioni sulle diverse [Tipi di cache](../cli/manage-cache.md).

## consumer_wait_for_messages

Specifica se i consumatori devono continuare a eseguire il polling dei messaggi se il numero di messaggi elaborati è inferiore al `max_messages` valore. Il valore predefinito è `1`.

```conf
'queue' => [
    'consumers_wait_for_messages' => 1
]
```

Sono disponibili le seguenti opzioni:

- `1`: i consumatori continuano a elaborare i messaggi dalla coda dei messaggi fino a quando non raggiungono `max_messages` valore specificato in `env.php` prima di chiudere la connessione TCP e terminare il processo consumer. Se la coda si svuota prima di raggiungere `max_messages` valore, il consumatore attende che arrivino più messaggi.

  Consigliamo questa impostazione per i commercianti di grandi dimensioni, perché è previsto un flusso costante di messaggi e i ritardi di elaborazione non sono auspicabili.

- `0`- I consumatori elaborano i messaggi disponibili nella coda, chiudono la connessione TCP e terminano. I consumatori non attendono messaggi aggiuntivi per entrare nella coda, anche se il numero di messaggi elaborati è inferiore al `max_messages` valore specificato in `env.php` file. Questo può aiutare a prevenire problemi con i processi cron causati da lunghi ritardi nell’elaborazione della coda dei messaggi.

  Consigliamo questa impostazione per i commercianti più piccoli che non si aspettano un flusso di messaggi costante e preferiscono conservare le risorse informatiche in cambio di ritardi di elaborazione minori quando non potrebbero esserci messaggi per giorni.

## cron

Abilita o disabilita i processi cron per l’applicazione Commerce. Per impostazione predefinita, i processi cron sono abilitati. Per disattivarli, aggiungi `cron` alla configurazione `env.php` e imposta il valore su `0`.

```conf
'cron' => [
  'enabled' => 0
]
```

>[!WARNING]
>
>Presta attenzione quando disattivi i processi cron. Quando sono disabilitati, i processi essenziali richiesti dall’applicazione Commerce non vengono eseguiti.

Ulteriori informazioni su [Cron](../cli/configure-cron-jobs.md).

## criptare

Commerce utilizza una chiave di crittografia per proteggere le password e altri dati sensibili. Questa chiave viene generata durante il processo di installazione.

```conf
'crypt' => [
  'key' => '63d409380ccb1182bfb27c231b732f05'
]
```

Ulteriori informazioni su [Chiave di crittografia](https://docs.magento.com/user-guide/system/encryption-key.html) nel _Guida utente di Commerce_.

## db

Tutte le configurazioni di database sono disponibili in questo nodo.

```conf
'db' => [
  'table_prefix' => '',
  'connection' => [
    'default' => [
      'host' => 'localhost',
      'dbname' => 'magento_db',
      'username' => 'root',
      'password' => 'admin123',
      'model' => 'mysql4',
      'engine' => 'innodb',
      'initStatements' => 'SET NAMES utf8;',
      'active' => '1'
    ]
  ]
]
```

## default_connection

Definisce la connessione predefinita per le code di messaggi. Il valore può essere `db`, `amqp`o un sistema di code personalizzato come `redismq`. Se specifichi un valore diverso da `db`, il software della coda di messaggi deve essere installato e configurato per primo. In caso contrario, i messaggi non verranno elaborati correttamente.

```conf
'queue' => [
    'default_connection' => 'amqp'
]
```

Se `queue/default_connection` è specificato nel sistema `env.php` file, questa connessione viene utilizzata per tutte le code di messaggi nel sistema, a meno che non venga definita una connessione specifica in un `queue_topology.xml`, `queue_publisher.xml` o `queue_consumer.xml` file.
Ad esempio, se `queue/default_connection` è `amqp` in `env.php` ma un `db` connessione specificata nei file XML di configurazione della coda di un modulo, il modulo utilizzerà MySQL come gestore di messaggi.

## directory

Opzioni di mappatura directory opzionali che devono essere impostate quando il server web è configurato per servire l’app Commerce dal `/pub` directory per [maggiore sicurezza](../../installation/tutorials/docroot.md).

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

## downloadable_domain

Elenco dei domini scaricabili disponibili in questo nodo. È possibile aggiungere, rimuovere o elencare domini aggiuntivi utilizzando i comandi CLI.

```conf
'downloadable_domains' => [
    'local.vanilla.com'
]
```

Ulteriori informazioni su [Domini scaricabili](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#downloadabledomainsadd).

## installare

Data di installazione dell’applicazione Commerce.

```conf
'install' => [
  'date' => 'Tue, 23 Apr 2019 09:31:07 +0000'
]
```

## blocca

Le impostazioni del provider di blocco sono configurate utilizzando `lock` nodo.

Ulteriori informazioni su [Blocca configurazione provider](../../installation/tutorials/lock-provider.md).

## MODALITÀ_IMMAGINE

La modalità di distribuzione può essere configurata in questo nodo.

```conf
'MAGE_MODE' => 'developer'
```

Ulteriori informazioni su [Modalità di applicazione](../cli/set-mode.md).

## coda

Le configurazioni della coda messaggi sono disponibili in questo nodo.

```conf
'queue' => [
  'topics' => [
    'customer.created' => [publisher="default-rabitmq"],
    'order.created' => [publisher="default-rabitmq"],
  ]
]
```

Ulteriori informazioni su [Coda messaggi][message-queue].

## resource

Le impostazioni di configurazione delle risorse sono disponibili in questo nodo.

```conf
'resource' => [
  'default_setup' => [
    'connection' => 'default'
  ]
]
```

## sessione

Le configurazioni delle sessioni sono memorizzate in `session` nodo.

```conf
'session' => [
  'save' => 'files'
],
```

Ulteriori informazioni su [Sessione](../storage/sessions.md).

## x-frame-options

l’intestazione x-frame-options può essere configurata utilizzando questo nodo.

```conf
'x-frame-options' => 'SAMEORIGIN'
```

Ulteriori informazioni su [x-frame-options](../security/xframe-options.md).

## sistema

Utilizzando questo nodo, Commerce blocca i valori di configurazione in `env.php` e quindi disabilita il campo nell&#39;amministratore.

```conf
'system' => [
  'default' => [
    'web' => [
      'secure' => [
          'base_url' => 'https://magento.test/'
      ]
    ]
  ]
```

Ulteriori informazioni in [env-php-config-set](../cli/set-configuration-values.md).

<!-- Link definitions -->

[message-queue]: https://developer.adobe.com/commerce/php/development/components/message-queues/
