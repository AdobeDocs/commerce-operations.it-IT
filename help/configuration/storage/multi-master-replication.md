---
title: Replica del database
description: Scopri i vantaggi della configurazione della replica del database.
source-git-commit: 52f92ef79586d618fd4ac51c00eaa1446a2dc98f
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 0%

---


# Replica del database

{{ee-only}}

{{deprecate-split-db}}

L&#39;impostazione della replica del database offre i seguenti vantaggi:

- Fornisce il backup dei dati
- Abilita l’analisi dei dati senza influire sul database master
- Scalabilità

I database MySQL vengono replicati in modo asincrono, il che significa che gli slave non devono essere connessi in modo permanente per ricevere gli aggiornamenti dal master.

## Configurare la replica del database

Una discussione approfondita sulla replica dei database va oltre l&#39;ambito di questa guida. Per configurarlo, puoi consultare una risorsa come:

- [Documentazione di MySQL](https://dev.mysql.com/doc/refman/5.6/en/replication.html)
- [Come impostare la replica principale secondario in MySQL (digitaloceani)](https://www.digitalocean.com/community/tutorials/how-to-set-up-replication-in-mysql)

Commerce fornisce configurazioni MySQL di esempio per i database slave. Viene fornita una configurazione semplice con l’ `ResourceConnections` Classe `README.md`.

Di seguito è riportato un livello più avanzato ed è fornito solo per informazioni:

```php
   return array (
      //...
      'db' =>
         array (
            'connection' =>
               array (
                  'indexer' =>
                     array (
                        'host' => 'default-master-host',
                        'dbname' => 'magento',
                        'username' => 'magento',
                        'password' => 'magento',
                        'active' => '1',
                        'persistent' => NULL,
                     ),
                  'default' =>
                     array (
                        'host' => 'default-master-host',
                        'dbname' => 'magento',
                        'username' => 'magento',
                        'password' => 'magento',
                        'active' => '1',
                     ),
                  'checkout' =>
                     array (
                        'host' => 'checkout-master-host',
                        'dbname' => 'checkout',
                        'username' => 'magento',
                        'password' => 'magento',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
                  'sales' =>
                     array (
                        'host' => 'sales-master-host',
                        'dbname' => 'sales',
                        'username' => 'magento',
                        'password' => 'magento',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
               ),
            'slave_connection' =>
               array (
                  'default' =>
                     array (
                        'host' => 'default-slave-host',
                        'dbname' => 'magento',
                        'username' => 'read_only',
                        'password' => 'password',
                        'active' => '1',
                     ),
                  'checkout' =>
                     array (
                        'host' => 'checkout-slave-host',
                        'dbname' => 'checkout',
                        'username' => 'read_only',
                        'password' => 'password',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
                  'sales' =>
                     array (
                        'host' => 'sales-slave-host',
                        'dbname' => 'sales',
                        'username' => 'read_only',
                        'password' => 'password',
                        'model' => 'mysql4',
                        'engine' => 'innodb',
                        'initStatements' => 'SET NAMES utf8;',
                        'active' => '1',
                     ),
                  ),
               'table_prefix' => '',
   ),
   //.......
```

## Miglioramento delle prestazioni

Per migliorare le prestazioni della replica master-slave, è possibile filtrare alcune tabelle sulle istanze slave. È consigliabile filtrare tutte le tabelle temporanee con pattern di nome `search\_tmp\_%` utilizzati per [catalogo](https://glossary.magento.com/catalog) ricerca.

A questo scopo, aggiungi la seguente riga al tuo `my.cnf` file sulle istanze slave:

```conf
replicate-wild-ignore-table=%.search\_tmp\_%
```
