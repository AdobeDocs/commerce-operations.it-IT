---
title: Configurare memcached su CentOS
description: Installa e configura memcached su CentOS.
feature: Configuration, Cache, Storage
exl-id: fc4ad18b-7e99-496e-aebc-1d7640d8716c
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '550'
ht-degree: 0%

---

# Configurare memcached su CentOS

Questa sezione fornisce istruzioni per installare memcached su CentOS. Per ulteriori informazioni, consultare il [wiki memcached](https://github.com/memcached/old-wiki).

>[!INFO]
>
>L’Adobe consiglia di utilizzare l’ultima versione stabile di memcached (attualmente 3.1.3 per memcached).

Poiché PHP non dispone di supporto nativo per memcache, è necessario installare un&#39;estensione affinché PHP possa utilizzarla. Sono disponibili due estensioni PHP ed è importante decodificare quali utilizzare:

- `memcache` (_no d_), un&#39;estensione precedente ma popolare che non viene mantenuta regolarmente.
L&#39;estensione `memcache` attualmente _non funziona con PHP 7_. Consulta la [documentazione PHP per memcache](https://www.php.net/manual/en/book.memcache.php).

  Il nome esatto è `php-pecl-memcache` per CentOS.

- `memcached` (_con un`d`_)—un&#39;estensione più recente e mantenuta compatibile con PHP 7. Consulta la [documentazione PHP per memcached](https://www.php.net/manual/en/book.memcached.php).

  Il nome esatto è `php-pecl-memcached` per CentOS.

## Installare e configurare memcached su CentOS

Per installare memcached su CentOS, eseguire le attività seguenti come utente con privilegi `root`:

1. Installare memcached e le relative dipendenze:

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
   >La sintassi dei comandi precedenti potrebbe dipendere dagli archivi di pacchetti utilizzati. Ad esempio, se si utilizza webtatic e PHP 5.6, immettere `yum install -y php56w-pecl-memcache`. Utilizzare `yum search memcache|grep php` per trovare il nome del pacchetto appropriato.


1. Modificare l&#39;impostazione di configurazione memcached per `CACHESIZE` e `OPTIONS`:

   1. Apri `/etc/sysconfig/memcached` in un editor di testo.
   1. Individuare il valore per `CACHESIZE` e modificarlo in almeno 1 GB. Ad esempio:

      ```config
      CACHESIZE="1GB"
      ```

   1. Individuare il valore per `OPTIONS` e modificarlo in `localhost` o `127.0.0.1`

1. Salvare le modifiche apportate a `memcached` e uscire dall&#39;editor di testo.
1. Riavvia memcached.

   ```bash
   service memcached restart
   ```

1. Riavvia il server web.

   Per Apache:

   ```bash
   service httpd restart
   ```

1. Procedi alla sezione successiva.

## Verifica del funzionamento di memcached prima di installare Commerce

L’Adobe consiglia di testare memcached per assicurarsi che funzioni prima di installare Commerce. Questa operazione richiede solo pochi minuti e può semplificare la risoluzione dei problemi in un secondo momento.

### Verificare che memcached sia riconosciuto dal server web

Per verificare che memcached sia riconosciuto dal server web:

1. Creare un file `phpinfo.php` nella directory principale dei documenti del server Web:

   ```php
   <?php
   // Show all information, defaults to INFO_ALL
   phpinfo();
   ```

1. Vai a quella pagina nel browser web.

   Ad esempio: `http://192.0.2.1/phpinfo.php`

1. Accertati che memcache venga visualizzato come segue:

![Conferma memcache riconosciuta dal server Web](../../assets/configuration/memcache.png)

Verifica di utilizzare memcached versione 3.0.5 o successiva.

Se memcache non viene visualizzata, riavviare il server Web e aggiornare la pagina del browser. Se ancora non viene visualizzata, verificare di aver installato l&#39;estensione `php-pecl-memcache`.

### Creare un test memcache costituito da un database MySQL e da uno script PHP

Il test utilizza un database, una tabella e dati MySQL per verificare che sia possibile recuperare i dati del database e memorizzarli in memcache. Uno script PHP esegue prima la ricerca nella cache. Se il risultato non esiste, lo script esegue una query sul database. Dopo che la query è stata soddisfatta dal database originale, lo script memorizza il risultato in memcache, utilizzando il comando `set`.

[Ulteriori dettagli su questo test](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-memcache-on-ubuntu-12-04)

Creare il database MySQL:

```bash
mysql -u root -p
```

Al prompt `mysql`, immettere i comandi seguenti:

```sql
create database memcache_test;
GRANT ALL ON memcache_test.* TO memcache_test@localhost IDENTIFIED BY 'memcache_test';
use memcache_test;
create table example (id int, name varchar(30));
insert into example values (1, "new_data");
exit
```

Crea `cache-test.php` nella directory principale dei documenti del server Web:

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

Dove `<memcached hostname or ip>` è `localhost`, `127.0.0.1` o il nome host o l&#39;indirizzo IP memcache. `<memcached port>` è la porta di ascolto; per impostazione predefinita, `11211`.

Esegui lo script dalla riga di comando.

```bash
cd <web server docroot>
```

```bash
php cache-test.php
```

Il primo risultato è `got result from mysql`. Ciò significa che la chiave non esiste in memcached ma è stata recuperata da MySQL.

Il secondo risultato è `got result from memcached`, che verifica che il valore sia archiviato correttamente in memcached.

Infine, puoi visualizzare le chiavi memcache utilizzando Telnet:

```bash
telnet localhost <memcache port>
```

Al prompt, immetti

```bash
stats items
```

Il risultato è simile al seguente:

```
STAT items:3:number 1
STAT items:3:age 1075
STAT items:3:evicted 0
STAT items:3:evicted_nonzero 0
STAT items:3:evicted_time 0
STAT items:3:outofmemory 0
STAT items:3:tailrepairs 0
```

Scaricare la memoria cache e uscire da Telnet:

```bash
flush_all
```

```bash
quit
```

[Ulteriori informazioni sul test Telnet](https://darkcoding.net/software/memcached-list-all-keys/)
