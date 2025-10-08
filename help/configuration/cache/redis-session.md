---
title: Usa Redis per l’archiviazione della sessione
description: Scopri come configurare Redis per l’archiviazione delle sessioni in Adobe Commerce. Scopri la configurazione della riga di comando, le opzioni di configurazione e le tecniche di ottimizzazione delle prestazioni.
feature: Configuration, Cache
exl-id: f93f500d-65b0-4788-96ab-f1c3d2d40a38
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '724'
ht-degree: 1%

---

# Usa Redis per l’archiviazione della sessione

>[!IMPORTANT]
>
>È necessario [installare Redis](config-redis.md#install-redis) prima di continuare.


Commerce ora fornisce opzioni della riga di comando per configurare l’archiviazione della sessione Redis. Nelle versioni precedenti, hai modificato il file `<Commerce install dir>app/etc/env.php`. La riga di comando fornisce la convalida ed è il metodo di configurazione consigliato, ma è comunque possibile modificare il file `env.php`.

Eseguire il comando `setup:config:set` e specificare i parametri specifici Redis.

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-<parameter_name>=<parameter_value>...
```

dove

`--session-save=redis` abilita l&#39;archiviazione della sessione Redis. Se questa funzione è già stata abilitata, ometti questo parametro.

`--session-save-redis-<parameter_name>=<parameter_value>` è un elenco di coppie parametro/valore che configurano l&#39;archiviazione della sessione:

| Parametro della riga di comando | Nome parametro | Significato | Valore predefinito |
|--- |--- |--- |--- |
| session-save-redis-host | host | Nome host completo, indirizzo IP o percorso assoluto se si utilizzano socket UNIX. | localhost |
| session-save-redis-port | porta | Porta di ascolto del server Redis. | 6379 |
| session-save-redis-password | password | Specifica una password se il server Redis richiede l&#39;autenticazione. | vuoto |
| session-save-redis-timeout | timeout | Timeout della connessione, in secondi. | 2,5 |
| session-save-redis-persistent-id | persistent_identifier | Stringa univoca per abilitare le connessioni permanenti (ad esempio, sess-db0).<br>[Problemi noti con phpredis e php-fpm](https://github.com/phpredis/phpredis/issues/70). |
| session-save-redis-db | database | Numero univoco del database Redis, che si consiglia di proteggere dalla perdita di dati.<br><br>**Importante**: se si utilizza Redis per più di un tipo di memorizzazione nella cache, i numeri di database devono essere diversi. È consigliabile assegnare il numero predefinito del database di memorizzazione nella cache a 0, il numero del database di memorizzazione nella cache delle pagine a 1 e il numero del database di memorizzazione nella sessione a 2. | 0 |
| session-save-redis-compression-threshold | compression_threshold | Impostare su 0 per disattivare la compressione (consigliato quando `suhosin.session.encrypt = On`).<br>[Problema noto con stringhe superiori a 64 KB](https://github.com/colinmollenhour/Cm_Cache_Backend_Redis/issues/18). | 2048 |
| session-save-redis-compression-lib | library_di_compressione | Opzioni: gzip, lzf, lz4 o snappy. | gzip |
| session-save-redis-log-level | log_level | Impostato su uno dei seguenti, elencati in ordine dal meno dettagliato al più dettagliato:<ul><li>0 (emergenza: solo gli errori più gravi)<li>1 (avviso: è necessaria un&#39;azione immediata)<li>2 (critico: componente applicazione non disponibile)<li>3 (errore: errori di runtime, non critici ma da monitorare)<li>4 (avviso: informazioni aggiuntive, consigliato)<li>5 (nota: condizione normale ma significativa)<li>6 (informazioni: messaggi informativi)<li>7 (debug: la maggior parte delle informazioni solo per lo sviluppo o il testing)</ul> | 1 |
| session-save-redis-max-concurrency | max_concurrency | Numero massimo di processi che possono attendere un blocco in una sessione. Per i cluster di produzione di grandi dimensioni, impostare questo valore su almeno il 10% del numero di processi PHP. | 6 |
| session-save-redis-break-after-frontend | break_after_frontend | Numero di secondi di attesa prima di tentare di interrompere il blocco per la sessione front-end (ovvero, storefront). | 5 |
| session-save-redis-break-after-adminhtml | break_after_adminhtml | Numero di secondi di attesa prima di tentare di interrompere il blocco per una sessione amministratore (ovvero amministratore). | 30 |
| session-save-redis-first-lifetime | first_lifetime | Durata, in secondi, della sessione per i non bot alla prima scrittura o utilizza 0 per disabilitare. | 600 |
| session-save-redis-bot-first-lifetime | bot_first_lifetime | Durata, in secondi, della sessione per i bot alla prima scrittura o utilizza 0 per disabilitare. | 60 |
| session-save-redis-bot-lifetime | bot_lifetime | Durata in secondi della sessione per i bot nelle scritture successive o utilizza 0 per la disattivazione. | 7200 |
| session-save-redis-disable-locking | disable_locking | Disattiva completamente il blocco della sessione. | 0 (false) |
| session-save-redis-min-lifetime | min_lifetime | Durata minima della sessione, in secondi. | 60 |
| session-save-redis-max-lifetime | max_lifetime | Durata massima della sessione, in secondi. | 2592000 (720 ore) |
| session-save-redis-sentinel-master | sentinel_master | Nome master Sentinel Redis | vuoto |
| session-save-redis-sentinel-servers | sentinel_servers | Elenco dei server Redis Sentinel, separati da virgola | vuoto |
| session-save-redis-sentinel-verify-master | sentinel_verify_master | Verifica flag di stato master Redis Sentinel | 0 (false) |
| session-save-redis-sentinel-connect-ries | sentinel_connect_retries | Nuovi tentativi di connessione per le sentinelle | 5 |

## Esempio

L&#39;esempio che segue imposta Redis come archivio dati della sessione, imposta l&#39;host su `127.0.0.1`, imposta il livello di registro su 4 e imposta il numero di database su 2. Tutti gli altri parametri vengono impostati sul valore predefinito.

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=127.0.0.1 --session-save-redis-log-level=4 --session-save-redis-db=2
```

### Risultato

Commerce aggiunge a `<magento_root>app/etc/env.php` righe simili alle seguenti:

```php
'session' => [
    'save' => 'redis',
    'redis' => [
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
        'max_lifetime' => '2592000',
    ],
],
```

>[!INFO]
>
>Il valore TTL per i record di sessione utilizza il valore per Durata cookie, configurato in Amministrazione. Se la durata del cookie è impostata su 0 (il valore predefinito è 3600), le sessioni Redis scadono nel numero di secondi specificato in min_lifetime (il valore predefinito è 60). Questa discrepanza è dovuta alle differenze nel modo in cui Redis e i cookie di sessione interpretano un valore &quot;lifetime&quot; del ciclo di vita pari a 0. Se questo comportamento non è desiderato, aumenta il valore di min_lifetime.

## Verifica connessione Redis

Per verificare che Redis e Commerce funzionino insieme, accedete al server che esegue Redis, aprite un terminale e utilizzate il comando di monitoraggio Redis o il comando ping.

### Comando Redis Monitor

```bash
redis-cli monitor
```

Esempio di output di archiviazione sessione:

```
1476824834.187250 [0 127.0.0.1:52353] "select" "0"
1476824834.187587 [0 127.0.0.1:52353] "hmget" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "writes"
1476824834.187939 [0 127.0.0.1:52353] "expire" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "1200"
1476824834.257226 [0 127.0.0.1:52353] "select" "0"
1476824834.257239 [0 127.0.0.1:52353] "hmset" "sess_sgmeh2k3t7obl2tsot3h2ss0p1" "data" "_session_validator_data|a:4:{s:11:\"remote_addr\";s:12:\"10.235.34.14\";s:8:\"http_via\";s:0:\"\";s:20:\"http_x_forwarded_for\";s:0:\"\";s:15:\"http_user_agent\";s:115:\"Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.143 Safari/537.36\";}_session_hosts|a:1:{s:12:\"10.235.32.10\";b:1;}admin|a:0:{}default|a:2:{s:9:\"_form_key\";s:16:\"e331ugBN7vRjGMgk\";s:12:\"visitor_data\";a:3:{s:13:\"last_visit_at\";s:19:\"2016-10-18 21:06:37\";s:10:\"session_id\";s:26:\"sgmeh2k3t7obl2tsot3h2ss0p1\";s:10:\"visitor_id\";s:1:\"9\";}}adminhtml|a:0:{}customer_base|a:1:{s:20:\"customer_segment_ids\";a:1:{i:1;a:0:{}}}checkout|a:0:{}" "lock" "0"
... more ...
```

### Ridisattiva comando ping

```bash
redis-cli ping
```

`PONG` deve essere la risposta.

Se entrambi i comandi sono riusciti, Redis viene configurato correttamente.

### Analisi dei dati compressi

Per verificare i dati compressi di Session e Page Cache, [RESP.app](https://flathub.org/apps/details/app.resp.RESP) supporta la decompressione automatica di Commerce 2 Session e Page Cache e visualizza i dati di sessione PHP in un formato leggibile.
