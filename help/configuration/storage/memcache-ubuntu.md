---
title: Imposta la cache su Ubuntu
description: Installa e configura la cache in memoria su Ubuntu.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 0%

---


# Imposta la cache su Ubuntu

Questa sezione fornisce istruzioni per installare la cache di memoria su Ubuntu.

>[!INFO]
>
>Adobe consiglia di utilizzare la versione 3.0.5 o successiva della cache.

Poiché PHP non dispone di supporto nativo per memcache, è necessario installare un&#39;estensione per PHP per utilizzarla. Sono disponibili due estensioni PHP ed è importante decodificare che utilizzare:

- `memcache` (_no d_) - un&#39;estensione precedente ma popolare che non viene mantenuta regolarmente.
La `memcache` estensione attualmente _non_ lavorare con PHP 7. Vedi [Documentazione PHP per memcache](https://www.php.net/manual/en/book.memcache.php).

   Il nome esatto è `php5-memcache` per Ubuntu.

- `memcached` (_con`d`_): estensione più recente e mantenuta compatibile con PHP 7. Vedi [Documentazione PHP per cache](https://www.php.net/manual/en/book.memcached.php).

   Il nome esatto è `php5-memcached` per Ubuntu.

## Installa e configura la cache in memoria su Ubuntu

**Per installare e configurare la memorizzazione in cache su Ubuntu**:

1. Come utente con `root` Privilegi, immetti il comando seguente:

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-get -y install php5-memcached memcached
   ```

1. Modificare l’impostazione di configurazione memorizzata nella cache per `CACHESIZE` e `-l`:

   1. Apri `/etc/memcached.conf` in un editor di testo.
   1. Individua il `-m` parametro .
   1. Cambia almeno il suo valore in `1GB`
   1. Individua il `-l` parametro .
   1. Cambia il valore in `127.0.0.1` o `localhost`
   1. Salva le modifiche in `memcached.conf` e esci dall’editor di testo.
   1. Riavvia la cache in memoria.

      ```bash
      service memcached restart
      ```

1. Riavvia il server web.

   Per Apache, `service apache2 restart`

1. Procedi alla sezione successiva.

## Verificare che la cache in memoria funzioni prima di installare il Magento

Adobe consiglia di testare la cache in memoria per assicurarsi che funzioni prima di installare Commerce. Questo richiede solo pochi minuti e può semplificare la risoluzione dei problemi in un secondo momento.

### Verifica che la cache memorizzata sia riconosciuta dal server web

Per verificare che la cache memorizzato sia riconosciuta dal server Web:

1. Crea un `phpinfo.php` nel docroot del server web:

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. Vai a quella pagina nel tuo browser web. Ad esempio:

   ```http
   http://192.0.2.1/phpinfo.php
   ```

1. Assicurati che la cache sia visualizzata come segue:

   ![Conferma che la cache della memoria è riconosciuta dal server web](../../assets/configuration/memcache.png)

   Verifica di utilizzare la versione 3.0.5 o successiva della cache.

   Se la cache memcache non viene visualizzata, riavviare il server Web e aggiornare la pagina del browser. Se non viene ancora visualizzato, verifica di aver installato il `php-pecl-memcached` estensione.

### Verifica che i dati della cache possano essere memorizzati nella cache

Questo test utilizza uno script PHP per verificare che la cache possa archiviare e recuperare [cache](https://glossary.magento.com/cache) dati.

Per ulteriori informazioni su questo test, vedi [Esercitazione su come installare e utilizzare Memcache su Ubuntu](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-14-04).

Crea `cache-test.php` nel docroot del server web con i seguenti contenuti:

```php
$meminstance = new Memcached();

$meminstance->addServer("<memcached hostname or ip>", <memcached port>);

$result = $meminstance->get("test");

if ($result) {
    echo $result;
} else {
    echo "No matching key found. Refresh the browser to add it!";
    $meminstance->set("test", "Successfully retrieved the data!") or die("Could not save anything to memcached...");
}
```

Dove `<memcached hostname or ip>` è `localhost`, `127.0.0.1`o il nome host o l&#39;indirizzo IP della cache memcache. La `<memcached port>` è la porta di ascolto; per impostazione predefinita, `11211`.

Vai a quella pagina in un browser web. Ad esempio

```http
http://192.0.2.1/cache-test.php
```

Al primo accesso alla pagina, viene visualizzato quanto segue: `No matching key found. Refresh the browser to add it!`

Aggiorna il browser. Il messaggio viene modificato in `Successfully retrieved the data!`

Infine, è possibile visualizzare le chiavi memcache utilizzando Telnet:

```bash
telnet localhost <memcache port>
```

Al prompt, immetti

```shell
stats items
```

Il risultato è simile al seguente:

```terminal
STAT items:2:number 1
STAT items:2:age 106
STAT items:2:evicted 0
STAT items:2:evicted_nonzero 0
STAT items:2:evicted_time 0
STAT items:2:outofmemory 0
STAT items:2:tailrepairs 0
STAT items:2:reclaimed 0
STAT items:2:expired_unfetched 0
STAT items:2:evicted_unfetched 0
```

Svuotare l&#39;archiviazione in cache e chiudere Telnet:

```shell
flush_all
```

```shell
quit
```

[Informazioni aggiuntive sul test Telnet](https://darkcoding.net/software/memcached-list-all-keys/)
