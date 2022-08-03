---
title: riferimento env.php
description: Vedi un elenco di valori per il file env.php.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '629'
ht-degree: 0%

---


# riferimento env.php

La `env.php` il file contiene le sezioni seguenti:

| Nome | Descrizione |
|-------------------------------|-----------------------------------------------------------------|
| `backend` | Impostazioni per l&#39;area Amministratore |
| `cache` | Configura la pagina di redis e la cache predefinita |
| `cache_types` | Impostazioni di archiviazione cache |
| `consumers_wait_for_messages` | Configurare il modo in cui i consumatori elaborano i messaggi dalla coda dei messaggi |
| `cron` | Attiva o disattiva i lavori cron |
| `crypt` | Chiave di crittografia per le funzioni di crittografia |
| `db` | Impostazioni di connessione al database |
| `directories` | Impostazioni di mappatura delle directory Commerce |
| `downloadable_domains` | Elenco dei domini scaricabili |
| `install` | Data di installazione |
| `lock` | Blocca impostazioni provider |
| `MAGE_MODE` | La [modalità applicazione](../bootstrap/application-modes.md) |
| `queue` | [Code di messaggi](../queues/manage-message-queues.md) impostazioni |
| `resource` | Mappatura del nome della risorsa su una connessione |
| `session` | Dati di archiviazione sessione |
| `system` | Disattiva il campo per la modifica nell&#39;amministratore |
| `x-frame-options` | Impostazione per [x-frame-options][x-frame-options] |

## backend

Configura le **frontName** per l’url amministratore Commerce utilizzando `backend` nodo in env.php.

```conf
'backend' => [
  'frontName' => 'admin'
]
```

## cache

Configura la pagina di redis e la memorizzazione in cache predefinita utilizzando `cache` nel nodo `env.php` file.

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

Ulteriori informazioni in [Configurazione di Redis](../cache/redis-pg-cache.md).

## cache_types

Tutte le configurazioni dei tipi di cache sono disponibili da questo nodo.

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

Specifica se i consumatori devono continuare il polling dei messaggi se il numero di messaggi elaborati è inferiore al `max_messages` valore. Il valore predefinito è `1`.

```conf
'queue' => [
    'consumers_wait_for_messages' => 1
]
```

Sono disponibili le seguenti opzioni:

- `1`- I consumatori continuano a elaborare i messaggi dalla coda dei messaggi fino al raggiungimento del `max_messages` il valore specificato nel `env.php` prima di chiudere la connessione TCP e interrompere il processo consumer. Se la coda si svuota prima di raggiungere il `max_messages` il consumatore attende ulteriori messaggi.

   Consigliamo questa impostazione per i grandi merchant perché è previsto un flusso costante di messaggi e non sono auspicabili ritardi nell’elaborazione.

- `0`- I consumatori elaborano i messaggi disponibili nella coda, chiudono la connessione TCP e terminano. I consumatori non attendono che altri messaggi entrino nella coda, anche se il numero di messaggi elaborati è inferiore al `max_messages` il valore specificato nel `env.php` file. Questo può aiutare a evitare problemi con i processi cron causati da lunghi ritardi nell’elaborazione della coda dei messaggi.

   Consigliamo questa impostazione per i commercianti più piccoli che non si aspettano un flusso costante di messaggi e preferiscono conservare le risorse informatiche in cambio di ritardi di elaborazione minori quando non ci potrebbero essere messaggi per giorni.

## cron

Abilitare o disabilitare i lavori cron per l’applicazione Commerce. Per impostazione predefinita, i lavori cron sono abilitati. Per disattivarle, aggiungi la variabile `cron` la configurazione `env.php` e imposta il valore su `0`.

```conf
'cron' => [
  'enabled' => 0
]
```

>[!WARNING]
>
>Presta attenzione quando disattivi i cron job. Quando sono disattivati, i processi essenziali richiesti dall’applicazione Commerce non verranno eseguiti.

Ulteriori informazioni [Crons](../cli/configure-cron-jobs.md).

## cripta

Commerce utilizza una chiave di crittografia per proteggere le password e altri dati sensibili. Questa chiave viene generata durante il processo di installazione.

```conf
'crypt' => [
  'key' => '63d409380ccb1182bfb27c231b732f05'
]
```

Ulteriori informazioni [Chiave di crittografia](https://docs.magento.com/user-guide/system/encryption-key.html) in _Guida utente di Commerce_.

## db

Tutte le configurazioni del database sono disponibili in questo nodo.

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

## directory

Opzioni di mappatura della directory facoltative che devono essere impostate quando il server web è configurato per servire l’app Commerce da `/pub` directory per [maggiore sicurezza][change-docroot-to-pub].

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

## downloadable_domain

Elenco dei domini scaricabili disponibili in questo nodo. È possibile aggiungere, rimuovere o elencare altri domini utilizzando i comandi CLI.

```conf
'downloadable_domains' => [
    'local.vanilla.com'
]
```

Ulteriori informazioni [Domini scaricabili](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#downloadabledomainsadd).

## installare

Data di installazione dell&#39;applicazione Commerce.

```conf
'install' => [
  'date' => 'Tue, 23 Apr 2019 09:31:07 +0000'
]
```

## bloccare

Le impostazioni del provider di blocco sono configurate utilizzando `lock` nodo.

Ulteriori informazioni [Blocca configurazione provider][lock-provider-config].

## MAGE_MODE

La modalità di distribuzione può essere configurata in questo nodo.

```conf
'MAGE_MODE' => 'developer'
```

Ulteriori informazioni [modalità di applicazione](../cli/set-mode.md).

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

Ulteriori informazioni [Coda messaggi][message-queue].

## risorsa

Le impostazioni di configurazione delle risorse sono disponibili in questo nodo.

```conf
'resource' => [
  'default_setup' => [
    'connection' => 'default'
  ]
]
```

## sessione

Le configurazioni della sessione sono memorizzate in `session` nodo.

```conf
'session' => [
  'save' => 'files'
],
```

Ulteriori informazioni [Sessione](../storage/sessions.md).

## x-frame-options

L&#39;intestazione x-frame-options può essere configurata utilizzando questo nodo.

```conf
'x-frame-options' => 'SAMEORIGIN'
```

Ulteriori informazioni [x-frame-options](../security/xframe-options.md).

## sistema

Utilizzando questo nodo, Commerce blocca i valori di configurazione nel `env.php` e quindi disabilita il campo nell&#39;amministratore.

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

[change-docroot-to-pub]: https://devdocs.magento.com/guides/v2.4/install-gde/tutorials/change-docroot-to-pub.html
[encryption-key]: https://docs.magento.com/user-guide/system/encryption-key.html
[lock-provider-config]: https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-lock.html
[message-queue]: https://developer.adobe.com/commerce/php/development/components/message-queues/
