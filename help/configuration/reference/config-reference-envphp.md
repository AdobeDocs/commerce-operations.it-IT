---
title: riferimento env.php
description: Scopri i valori e le sezioni di configurazione del file env.php in Adobe Commerce. Scopri le impostazioni dell’ambiente e le opzioni di configurazione.
exl-id: cf02da8f-e0de-4f0e-bab6-67ae02e9166f
source-git-commit: cb89f0c0a576cf6cd8b53a4ade12c21106e2cdf3
workflow-type: tm+mt
source-wordcount: '1033'
ht-degree: 0%

---

# riferimento env.php

Il file `env.php` contiene le sezioni seguenti:

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
| `directories` | Impostazioni di mappatura delle directory Commerce |
| `downloadable_domains` | Elenco dei domini scaricabili |
| `install` | Data di installazione |
| `lock` | Blocca impostazioni provider |
| `MAGE_MODE` | [modalità applicazione](../bootstrap/application-modes.md) |
| `queue` | Impostazioni [Code messaggi](../queues/manage-message-queues.md) |
| `resource` | Mappatura del nome della risorsa su una connessione |
| `session` | Dati archiviazione sessione |
| `system` | Disattiva il campo per la modifica in Admin |
| `x-frame-options` | Impostazione di [x-frame-options][x-frame-options] |

## backend

Configura **frontName** per l&#39;URL amministratore di Commerce utilizzando il nodo `backend` in env.php.

```conf
'backend' => [
  'frontName' => 'admin'
]
```

## cache

Configurare la pagina redis e il caching predefinito utilizzando il nodo `cache` nel file `env.php`.

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

Ulteriori informazioni sui diversi [tipi di cache](../cli/manage-cache.md).

## consumer_wait_for_messages

Specificare se i consumatori devono continuare a eseguire il polling dei messaggi se il numero di messaggi elaborati è inferiore al valore `max_messages`. Il valore predefinito è `1`.

```conf
'queue' => [
    'consumers_wait_for_messages' => 1
]
```

Sono disponibili le seguenti opzioni:

- `1` - I consumatori continuano a elaborare i messaggi dalla coda dei messaggi fino a raggiungere il valore `max_messages` specificato nel file `env.php` prima di chiudere la connessione TCP e terminare il processo consumer. Se la coda si svuota prima di raggiungere il valore `max_messages`, il consumatore attende che arrivino altri messaggi.

  Consigliamo questa impostazione per i commercianti di grandi dimensioni, perché è previsto un flusso costante di messaggi e i ritardi di elaborazione non sono auspicabili.

- `0` - I consumatori elaborano i messaggi disponibili nella coda, chiudono la connessione TCP e terminano. I consumatori non attendono messaggi aggiuntivi per entrare nella coda, anche se il numero di messaggi elaborati è inferiore al valore `max_messages` specificato nel file `env.php`. Questo può aiutare a prevenire problemi con i processi cron causati da lunghi ritardi nell’elaborazione della coda dei messaggi.

  Consigliamo questa impostazione per i commercianti più piccoli che non si aspettano un flusso di messaggi costante e preferiscono conservare le risorse informatiche in cambio di ritardi di elaborazione minori quando non potrebbero esserci messaggi per giorni.

## cron

Attiva o disattiva i processi cron per l&#39;applicazione Commerce. Per impostazione predefinita, i processi cron sono abilitati. Per disattivarle, aggiungere la configurazione `cron` al file `env.php` e impostare il valore su `0`.

```conf
'cron' => [
  'enabled' => 0
]
```

>[!WARNING]
>
>Presta attenzione quando disattivi i processi cron. Quando sono disattivati, i processi essenziali richiesti dall’applicazione Commerce non vengono eseguiti.

Ulteriori informazioni su [Crons](../cli/configure-cron-jobs.md).

## criptare

Commerce utilizza una chiave di crittografia per proteggere le password e altri dati sensibili. Questa chiave viene generata durante il processo di installazione.

```conf
'crypt' => [
  'key' => '63d409380ccb1182bfb27c231b732f05'
]
```

Ulteriori informazioni sulla [chiave di crittografia](https://experienceleague.adobe.com/it/docs/commerce-admin/systems/security/encryption-key) nella _Guida utente di Commerce_.

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

Definisce la connessione predefinita per le code di messaggi. Il valore può essere `db`, `amqp`, `stomp` o un sistema di code personalizzato come `redismq`. Se si specifica un valore diverso da `db`, è necessario installare e configurare prima il software della coda messaggi. In caso contrario, i messaggi non verranno elaborati correttamente.

```conf
'queue' => [
    'default_connection' => 'amqp'
]
```

Per STOMP (ActiveMQ Artemis):

```conf
'queue' => [
    'default_connection' => 'stomp'
]
```

Se `queue/default_connection` è specificato nel file di sistema `env.php`, questa connessione viene utilizzata per tutte le code di messaggi nel sistema, a meno che non sia definita una connessione specifica in un file `queue_topology.xml`, `queue_publisher.xml` o `queue_consumer.xml`.
Ad esempio, se `queue/default_connection` è `amqp` in `env.php` ma è specificata una connessione `db` nei file XML di configurazione della coda di un modulo, il modulo utilizzerà MySQL come gestore di messaggi.

## directory

Opzioni di mappatura della directory facoltative che devono essere impostate quando il server Web è configurato per servire l&#39;app Commerce dalla directory `/pub` per [sicurezza migliorata](../../installation/tutorials/docroot.md).

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

Ulteriori informazioni su [Domini scaricabili](https://experienceleague.adobe.com/it/docs/commerce-operations/tools/cli-reference/commerce-on-premises#downloadabledomainsadd).

## installare

Data di installazione dell&#39;applicazione Commerce.

```conf
'install' => [
  'date' => 'Tue, 23 Apr 2019 09:31:07 +0000'
]
```

## blocca

Le impostazioni del provider di blocco sono configurate utilizzando il nodo `lock`.

Ulteriori informazioni su [Blocca configurazione provider](../../installation/tutorials/lock-provider.md).

## MODALITÀ_IMMAGINE

La modalità di distribuzione può essere configurata in questo nodo.

```conf
'MAGE_MODE' => 'developer'
```

Ulteriori informazioni sulle [modalità applicazione](../cli/set-mode.md).

## coda

Le configurazioni della coda messaggi sono disponibili in questo nodo. Puoi configurare RabbitMQ (AMQP) o ActiveMQ Artemis (STOMP) come broker di messaggi.

```conf
'queue' => [
  'topics' => [
    'customer.created' => [publisher="default-broker"],
    'order.created' => [publisher="default-broker"],
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

Le configurazioni di sessione sono archiviate nel nodo `session`.

```conf
'session' => [
  'save' => 'files'
],
```

Ulteriori informazioni sulla [sessione](../storage/sessions.md).

## x-frame-options

l’intestazione x-frame-options può essere configurata utilizzando questo nodo.

```conf
'x-frame-options' => 'SAMEORIGIN'
```

Ulteriori informazioni su [x-frame-options](../security/xframe-options.md).

## sistema

Utilizzando questo nodo, Commerce blocca i valori di configurazione nel file `env.php` e quindi disabilita il campo nell&#39;amministratore.

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


## Aggiungi variabili alla configurazione del file

È possibile impostare o sostituire ogni opzione di configurazione (variabile con valore) con le variabili di ambiente a livello di sistema operativo.

La configurazione `env.php` è archiviata in un array con livelli nidificati. Per convertire un percorso array nidificato in una stringa per le variabili di ambiente del sistema operativo, concatenare ogni chiave nel percorso con caratteri di sottolineatura doppia `__`, in maiuscolo e con prefisso `MAGENTO_DC_`.

Si supponga ad esempio di convertire il gestore di salvataggio della sessione dalla configurazione `env.php` in una variabile di ambiente del sistema operativo.

```conf
'session' => [
  'save' => 'files'
],
```

Concatenato con `__` e chiavi in maiuscolo diventerà `SESSION__SAVE`.

Viene quindi aggiunto il prefisso `MAGENTO_DC_` per ottenere il nome della variabile di ambiente del sistema operativo risultante `MAGENTO_DC_SESSION__SAVE`.

```shell
export MAGENTO_DC_SESSION__SAVE=files
```

Come altro esempio, convertiamo un percorso dell&#39;opzione di configurazione `env.php` scalare.

```conf
'x-frame-options' => 'SAMEORIGIN'
```

>[!INFO]
>
>Il nome della variabile deve essere in maiuscolo, ma il valore fa distinzione tra maiuscole e minuscole e deve essere mantenuto come documentato.

Per ricevere il nome finale della variabile di ambiente del sistema operativo `MAGENTO_DC_`, è sufficiente utilizzare la maiuscola e il prefisso `MAGENTO_DC_X-FRAME-OPTIONS`.

```shell
export MAGENTO_DC_X-FRAME-OPTIONS=SAMEORIGIN
```

>[!INFO]
>
>Il contenuto `env.php` avrà priorità rispetto alle variabili di ambiente del sistema operativo.

## Sovrascrivi configurazione file con variabili

Per sostituire le opzioni di configurazione di `env.php` esistenti con una variabile di ambiente del sistema operativo, l&#39;elemento array della configurazione deve essere codificato in JSON e impostato come valore della variabile del sistema operativo `MAGENTO_DC__OVERRIDE`.

Quando `MAGENTO_DC__OVERRIDE` è impostato, il framework Commerce ignora i valori corrispondenti nel file `env.php` e legge la configurazione direttamente dalla variabile di ambiente. I valori nel file `env.php` rimangono invariati ma vengono ignorati per le sezioni di configurazione sostituite.

>[!IMPORTANT]
>
>La variabile `MAGENTO_DC__OVERRIDE` ignora completamente le sezioni di configurazione specificate nel file `env.php`. Questo comportamento è diverso dalle singole variabili `MAGENTO_DC_`, che hanno priorità inferiore rispetto ai valori nel file `env.php`.

Se devi ignorare più opzioni di configurazione, assemblatele tutte in un singolo array prima della codifica JSON.

Sostituiamo ad esempio le seguenti `env.php` configurazioni:

```conf
'session' => [
  'save' => 'files'
],
'x-frame-options' => 'SAMEORIGIN'
```

Il testo codificato JSON dell’array precedente sarebbe
`{"session":{"save":"files"},"x-frame-options":"SAMEORIGIN"}`.

Ora impostarlo come valore della variabile del sistema operativo `MAGENTO_DC__OVERRIDE`.

```shell
export MAGENTO_DC__OVERRIDE='{"session":{"save":"files"},"x-frame-options":"SAMEORIGIN"}'
```

>[!INFO]
>
>Assicurati che l’array con codifica JSON sia correttamente citato e/o con escape, se necessario, per evitare che il sistema operativo corrompa la stringa codificata.