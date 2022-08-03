---
title: Configurazione della cache in CentOS
description: Installa e configura la cache cache su CentOS.
source-git-commit: 65060d067bbbfe139736df3800688ce897cb17be
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---


# Configurazione della cache in CentOS

Questa sezione fornisce istruzioni per installare la cache cache su CentOS. Per ulteriori informazioni, consulta la [wiki memorizzato](https://github.com/memcached/old-wiki).

>[!INFO]
>
>Adobe consiglia di utilizzare l’ultima versione con cache stabile (attualmente 3.1.3 per la cache).

Poiché PHP non dispone di supporto nativo per memcache, è necessario installare un&#39;estensione per PHP per utilizzarla. Sono disponibili due estensioni PHP ed è importante decodificare che utilizzare:

- `memcache` (_no d_) - un&#39;estensione precedente ma popolare che non viene mantenuta regolarmente.
La `memcache` estensione attualmente _non_ lavorare con PHP 7. Vedi [Documentazione PHP per memcache](https://www.php.net/manual/en/book.memcache.php).

   Il nome esatto è `php-pecl-memcache` per CentOS.

- `memcached` (_con`d`_): estensione più recente e mantenuta compatibile con PHP 7. Vedi [Documentazione PHP per cache](https://www.php.net/manual/en/book.memcached.php).

   Il nome esatto è `php-pecl-memcached` per CentOS.

## Installare e configurare la cache in cache su CentOS

Per installare in cache su CentOS, esegui le seguenti attività come utente con `root` privilegi:

1. Installa la cache e le relative dipendenze:

   ```bash
   yum -y update
   ```

   ```bash
   yum install -y libevent libevent-devel
   ```

   ```bash
   yum install -y memcached
   ```

   ```bash
   yum install -y php-pecl-memcache
   ```

   >[!INFO]
   >
   >La sintassi dei comandi precedenti potrebbe dipendere dagli archivi dei pacchetti utilizzati. Ad esempio, se utilizzi webtatic e PHP 5.6, immetti `yum install -y php56w-pecl-memcache`. Utilizzo `yum search memcache|grep php` per trovare il nome del pacchetto appropriato.


1. Modificare l’impostazione di configurazione memorizzata nella cache per `CACHESIZE` e `OPTIONS`:

   1. Apri `/etc/sysconfig/memcached` in un editor di testo.
   1. Individua il valore per `CACHESIZE` e cambiarlo in almeno 1 GB. Ad esempio:

      ```config
      CACHESIZE="1GB"
      ```

   1. Individua il valore per `OPTIONS` e cambiarlo in `localhost` o `127.0.0.1`

1. Salva le modifiche in `memcached` e esci dall’editor di testo.
1. Riavvia la cache in memoria.

   ```bash
   service memcached restart
   ```

1. Riavvia il server web.

   Per Apache:

   ```bash
   service httpd restart
   ```

1. Procedi alla sezione successiva.

## Verificare che la cache in memoria funzioni prima dell’installazione di Commerce

Adobe consiglia di testare la cache in memoria per assicurarsi che funzioni prima di installare Commerce. Questo richiede solo pochi minuti e può semplificare la risoluzione dei problemi in un secondo momento.

### Verifica che la cache memorizzata sia riconosciuta dal server web

Per verificare che la cache memorizzato sia riconosciuta dal server Web:

1. Crea un `phpinfo.php` nel docroot del server web:

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. Vai a quella pagina nel tuo browser web.

   Ad esempio: `http://192.0.2.1/phpinfo.php`

1. Assicurati che la cache memcache venga visualizzata come segue:

![Conferma il riconoscimento della cache memoriale da parte del server web](../../assets/configuration/memcache.png)

Verifica di utilizzare la versione 3.0.5 o successiva della cache.

Se memcache non viene visualizzato, riavviare il server Web e aggiornare la pagina del browser. Se non viene ancora visualizzato, verifica di aver installato il `php-pecl-memcache` estensione.

### Crea un test memcache costituito da un database MySQL e da uno script PHP

Il test utilizza un database, una tabella e dei dati MySQL per verificare che sia possibile recuperare i dati del database e archiviarli in memcache. Uno script PHP cerca prima il [cache](https://glossary.magento.com/cache). Se il risultato non esiste, lo script esegue una query al database. Dopo che la query è stata soddisfatta dal database originale, lo script memorizza il risultato in memcache, utilizzando `set` comando.

[Maggiori dettagli su questo test](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-12-04)

Crea il database MySQL:

```bash
mysql -u root -p
```

Alla `mysql` prompt, immetti i seguenti comandi:

```sql
create database memcache_test;
GRANT ALL ON memcache_test.* TO memcache_test@localhost IDENTIFIED BY 'memcache_test';
use memcache_test;
create table example (id int, name varchar(30));
insert into example values (1, "new_data");
exit
```

Crea `cache-test.php` nel docroot del server web:

```php
$meminstance = new Memcached();

$meminstance->addServer('<memcached hostname or ip>', <memcached port>);

$query = "select id from example where name = 'new_data'";
$querykey = "KEY" . md5($query);

$result = $meminstance->get($querykey);

if (!$result) {
   try {
        $dbh = new PDO('mysql:host=localhost;dbname=memcache_test','memcache_test','memcache_test');
        $dbh->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
        $result = $dbh->query("select id from example where name = 'new_data'")->fetch();
        $meminstance->set($querykey, $result, 0, 600);
        print "got result from mysql\n";
        return 0;
    } catch (PDOException $e) {
        die($e->getMessage());
    }
}
print "got result from memcached\n";
return 0;
```

Dove `<memcached hostname or ip>` è `localhost`, `127.0.0.1`o il nome host o l&#39;indirizzo IP della cache memcache. La `<memcached port>` è la porta di ascolto; per impostazione predefinita, `11211`.

Esegui lo script dalla riga di comando.

```bash
cd <web server docroot>
```

```bash
php cache-test.php
```

Il primo risultato è `got result from mysql`. Ciò significa che la chiave non esiste nella cache in memoria ma è stata recuperata da MySQL.

Il secondo risultato è `got result from memcached`, che verifica che il valore sia memorizzato correttamente nella cache.

Infine, è possibile visualizzare le chiavi memcache utilizzando Telnet:

```bash
telnet localhost <memcache port>
```

Al prompt, immetti

```bash
stats items
```

Il risultato è simile al seguente:

```terminal
STAT items:3:number 1
STAT items:3:age 1075
STAT items:3:evicted 0
STAT items:3:evicted_nonzero 0
STAT items:3:evicted_time 0
STAT items:3:outofmemory 0
STAT items:3:tailrepairs 0
```

Esegui lo scaricamento dell&#39;archivio memcache e chiudi Telnet:

```bash
flush_all
```

```bash
quit
```

[Informazioni aggiuntive sul test Telnet](https://darkcoding.net/software/memcached-list-all-keys/)
