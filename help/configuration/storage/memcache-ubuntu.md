---
title: Configurare memcached su Ubuntu
description: Installa e configura memcached su Ubuntu.
exl-id: 831193d2-3e81-472c-9b87-78a8d52959b4
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# Configurare memcached su Ubuntu

Questa sezione fornisce istruzioni per installare memcached su Ubuntu.

>[!INFO]
>
>L’Adobe consiglia di utilizzare memcached versione 3.0.5 o successiva.

Poiché PHP non dispone di supporto nativo per memcache, è necessario installare un&#39;estensione affinché PHP possa utilizzarla. Sono disponibili due estensioni PHP ed è importante decodificare quali utilizzare:

- `memcache` (_d non disponibile_) - un&#39;estensione precedente ma popolare che non viene mantenuta regolarmente.
Il `memcache` estensione attualmente _non_ lavorare con PHP 7. Consulta [Documentazione PHP per memcache](https://www.php.net/manual/en/book.memcache.php).

   Il nome esatto è `php5-memcache` per Ubuntu.

- `memcached` (_con un`d`_) - un&#39;estensione più recente e mantenuta compatibile con PHP 7. Consulta [Documentazione PHP per memcached](https://www.php.net/manual/en/book.memcached.php).

   Il nome esatto è `php5-memcached` per Ubuntu.

## Installare e configurare memcached su Ubuntu

**Per installare e configurare memcached su Ubuntu**:

1. Come utente con `root` , immetti il seguente comando:

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-get -y install php5-memcached memcached
   ```

1. Modificare l’impostazione di configurazione memcached per `CACHESIZE` e `-l`:

   1. Apri `/etc/memcached.conf` in un editor di testo.
   1. Individua il `-m` parametro.
   1. Modifica il valore in almeno `1GB`
   1. Individua il `-l` parametro.
   1. Modifica il valore in `127.0.0.1` o `localhost`
   1. Salva le modifiche apportate a `memcached.conf` ed esci dall’editor di testo.
   1. Riavvia memcached.

      ```bash
      service memcached restart
      ```

1. Riavvia il server web.

   Per Apache, `service apache2 restart`

1. Procedi alla sezione successiva.

## Verifica del funzionamento di memcached prima di installare il Magento

L’Adobe consiglia di testare memcached per verificare che funzioni prima di installare Commerce. Questa operazione richiede solo pochi minuti e può semplificare la risoluzione dei problemi in un secondo momento.

### Verificare che memcached sia riconosciuto dal server web

Per verificare che memcached sia riconosciuto dal server web:

1. Creare un `phpinfo.php` file nella directory principale dei documenti del server web:

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. Vai a quella pagina nel browser web. Ad esempio:

   ```http
   http://192.0.2.1/phpinfo.php
   ```

1. Assicurati che vengano visualizzati i seguenti display memcached:

   ![Conferma che memcached sia riconosciuto dal server web](../../assets/configuration/memcache.png)

   Verifica di utilizzare memcached versione 3.0.5 o successiva.

   Se memcached non viene visualizzato, riavviare il server web e aggiornare la pagina del browser. Se ancora non viene visualizzato, verificare di aver installato `php-pecl-memcached` estensione.

### Verificare che memcached possa memorizzare i dati nella cache

Questo test utilizza uno script PHP per verificare che memcached possa memorizzare e recuperare i dati della cache.

Per ulteriori informazioni su questo test, consulta [Esercitazione su come installare e utilizzare Memcache su Ubuntu](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-14-04).

Crea `cache-test.php` nella directory principale dei documenti del server web con i seguenti contenuti:

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

Dove `<memcached hostname or ip>` è `localhost`, `127.0.0.1`o il nome host o l’indirizzo IP memcache. Il `<memcached port>` è la porta di ascolto; per impostazione predefinita, `11211`.

Vai a quella pagina in un browser web. Ad esempio

```http
http://192.0.2.1/cache-test.php
```

La prima volta che accedi alla pagina, viene visualizzato quanto segue: `No matching key found. Refresh the browser to add it!`

Aggiorna il browser. Il messaggio diventa `Successfully retrieved the data!`

Infine, puoi visualizzare le chiavi memcache utilizzando Telnet:

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

Scaricare lo storage memorizzato nella cache di memoria e uscire da Telnet:

```shell
flush_all
```

```shell
quit
```

[Informazioni aggiuntive sul test Telnet](https://darkcoding.net/software/memcached-list-all-keys/)
