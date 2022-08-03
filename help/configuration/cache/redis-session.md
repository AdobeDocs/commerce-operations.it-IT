---
title: Utilizzare Redis per l'archiviazione delle sessioni
description: Scopri come configurare Redis per l’archiviazione delle sessioni.
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '730'
ht-degree: 1%

---


# Utilizzare Redis per l&#39;archiviazione delle sessioni

>[!IMPORTANT]
>
>Devi [installare Redis](config-redis.md#install-redis) prima di continuare.


Commerce fornisce ora opzioni della riga di comando per configurare l’archiviazione della sessione Redis. Nelle versioni precedenti è stata modificata la `<Commerce install dir>app/etc/env.php` file. La riga di comando fornisce la convalida ed è il metodo di configurazione consigliato, ma è comunque possibile modificare il `env.php` file.

Esegui il `setup:config:set` e specificare i parametri specifici di Redis.

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-<parameter_name>=<parameter_value>...
```

dove

`--session-save=redis` abilita l&#39;archiviazione della sessione di Redis. Se questa funzione è già stata abilitata, ometti questo parametro.

`--session-save-redis-<parameter_name>=<parameter_value>` è un elenco di coppie di parametri/valori che configurano l’archiviazione della sessione:

| Parametro della riga di comando | Nome parametro | Significato | Valore predefinito |
|--- |--- |--- |--- |
| session-save-redis-host | host | Nome host completo, indirizzo IP o percorso assoluto se si utilizzano socket UNIX. | localhost |
| session-save-redis-port | porta | Porta di ascolto del server Redis. | 6379 |
| session-save-redis-password | password | Specifica una password se il server Redis richiede l&#39;autenticazione. | vuoto |
| session-save-redis-timeout | timeout | Timeout connessione, in secondi. | 2,5 |
| session-save-redis-persistente-id | persistente_identifier | Stringa univoca per abilitare le connessioni persistenti (ad esempio, sess-db0).<br>[Problemi noti con phpredis e php-fpm](https://github.com/phpredis/phpredis/issues/70). |
| session-save-redis-db | database | Numero di database Redis univoco, consigliato per la protezione dalla perdita di dati.<br><br>**Importante**: Se si utilizza Redis per più tipi di caching, i numeri del database devono essere diversi. Si consiglia di assegnare il numero di database di memorizzazione in cache predefinito a 0, il numero di database di memorizzazione in cache della pagina a 1 e il numero di database di archiviazione della sessione a 2. | 0 |
| session-save-redis-compressione-soglia | compressione_soglia | Imposta su 0 per disabilitare la compressione (consigliato quando [suhosin.session.encrypt = On](https://suhosin.org/stories/howtos.html)).<br>[Problema noto con stringhe di dimensioni superiori a 64 KB](https://github.com/colinmollenhour/Cm_Cache_Backend_Redis/issues/18). | 2048 |
| session-save-redis-compressione-lib | compressione_library | Opzioni: gzip, lzf, lz4 o snappy. | gzip |
| livello session-save-redis-log | livello_log | Impostate su uno dei seguenti elementi, elencati in ordine dal più dettagliato al più dettagliato:<ul><li>0 (emergenza: solo gli errori più gravi)<li>1 (avviso: necessaria un&#39;azione immediata)<li>2 (critico: componente dell&#39;applicazione non disponibile)<li>3 (errore: errori di runtime, non critici ma da monitorare)<li>4 (avviso: informazioni aggiuntive, consigliato)<li>5 (avviso: condizioni normali ma significative)<li>6 (informazioni: messaggi informativi)<li>7 (debug: la maggior parte delle informazioni solo per lo sviluppo o il testing)</ul> | 1 |
| session-save-redis-max-concurrency | max_concurrency | Numero massimo di processi che possono attendere un blocco in una sessione. Per i grandi cluster di produzione, impostare questo valore ad almeno il 10% del numero di processi PHP. | 6 |
| session-save-redis-break-after-frontend | break_after_frontend | Numero di secondi di attesa prima di tentare di interrompere il blocco per la sessione front-end (ovvero storefront). | 5 |
| session-save-redis-break-after-adminhtml | break_after_adminhtml | Numero di secondi di attesa prima di tentare di interrompere il blocco per una sessione amministratore (cioè amministratore). | 30 |
| session-save-redis-first lifetime | first_lifetime | Ciclo di vita, in secondi, della sessione per i non-robot nella prima scrittura, o utilizzare 0 per disabilitare. | 600 |
| session-save-redis-bot-first lifetime | bot_first_lifetime | Ciclo di vita, in secondi, della sessione per i bot nella prima scrittura, o utilizzare 0 per disabilitare. | 60 |
| session-save-redis-bot-lifetime | bot_lifetime | Ciclo di vita, in secondi, della sessione per i bot nelle scritture successive, o utilizzare 0 per disabilitare. | 7200 |
| session-save-redis-disable-locking | disable_locking | Disattiva completamente il blocco della sessione. | 0 (false) |
| session-save-redis-min-lifetime | min_lifetime | Durata minima della sessione, in secondi. | 60 |
| session-save-redis-max-lifetime | max_lifetime | Durata massima della sessione, in secondi. | 2592000 (720 ore) |
| session-save-redis-sentinel-master | sentinel_master | Nome principale di Redis Sentinel | vuoto |
| session-save-redis-sentinel-server | sentinel_servers | Elenco dei server Sentinel Redis, separati da virgole | vuoto |
| session-save-redis-sentinel-verify-master | sentinel_verify_master | Verifica il flag di stato principale sentinella Redis | 0 (false) |
| session-save-redis-sentinel-connect-retry | sentinel_connect_retry | Tentativi di connessione per sentinels | 5 |

## Esempio

L&#39;esempio seguente imposta Redis come archivio dati della sessione, imposta l&#39;host su `127.0.0.1`, imposta il livello di log su 4 e imposta il numero del database su 2. Tutti gli altri parametri sono impostati sul valore predefinito.

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=127.0.0.1 --session-save-redis-log-level=4 --session-save-redis-db=2
```

### Risultato

Commerce aggiunge linee simili alle seguenti `<magento_root>app/etc/env.php`:

```php
    'session' =>
    array (
      'save' => 'redis',
      'redis' =>
      array (
        'host' => '127.0.0.1',
        'port' => '6379',
        'password' => '',
        'timeout' => '2.5',
        'persistent_identifier' => '',
        'database' => '2',
        'compression_threshold' => '2048',
        'compression_library' => 'gzip',
        'log_level' => '4',
        'max_concurrency' => '6',
        'break_after_frontend' => '5',
        'break_after_adminhtml' => '30',
        'first_lifetime' => '600',
        'bot_first_lifetime' => '60',
        'bot_lifetime' => '7200',
        'disable_locking' => '0',
        'min_lifetime' => '60',
        'max_lifetime' => '2592000'
      )
    ),
```

>[!INFO]
>
>Il TTL per i record di sessione utilizza il valore per Durata cookie, configurato nell’amministratore. Se il valore di Durata cookie è impostato su 0 (il valore predefinito è 3600), le sessioni Redis scadono nel numero di secondi specificato in min_lifetime (il valore predefinito è 60). Questa discrepanza è dovuta alle differenze nel modo in cui Redis e i cookie di sessione interpretano un valore del ciclo di vita di 0. Se tale comportamento non è desiderato, aumenta il valore di min_lifetime.

## Verifica la connessione Redis

Per verificare che Redis e Commerce stiano lavorando insieme, accedi al server che esegue Redis, apri un terminale e utilizza il comando Monitor Redis o il comando ping.

### Comando Redis monitor

```bash
redis-cli monitor
```

Esempio di output di archiviazione sessione:

```terminal
1476824834.187250 [0 127.0.0.1:52353] "select" "0"
1476824834.187587 [0 127.0.0.1:52353] "hmget" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "writes"
1476824834.187939 [0 127.0.0.1:52353] "expire" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "1200"
1476824834.257226 [0 127.0.0.1:52353] "select" "0"
1476824834.257239 [0 127.0.0.1:52353] "hmset" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "_session_validator_data|a:4:{s:11:\"remote_addr\";s:12:\"10.235.34.14\";s:8:\"http_via\";s:0:\"\";s:20:\"http_x_forwarded_for\";s:0:\"\";s:15:\"http_user_agent\";s:115:\"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.143 Safari/537.36\";}_session_hosts|a:1:{s:12:\"10.235.32.10\";b:1;}admin|a:0:{}default|a:2:{s:9:\"_form_key\";s:16:\"e331ugBN7vRjGMgk\";s:12:\"visitor_data\";a:3:{s:13:\"last_visit_at\";s:19:\"2016-10-18 21:06:37\";s:10:\"session_id\";s:26:\"sgmeh2k3t7obl2tsot3h2ss0p1\";s:10:\"visitor_id\";s:1:\"9\";}}adminhtml|a:0:{}customer_base|a:1:{s:20:\"customer_segment_ids\";a:1:{i:1;a:0:{}}}checkout|a:0:{}" "lock" "0"
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

