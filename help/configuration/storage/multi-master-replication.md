---
title: Replica del database
description: Vedere i vantaggi della configurazione della replica del database.
exl-id: 0e41dca0-5a23-4d12-96fe-241c511ae366
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '175'
ht-degree: 0%

---

# Replica del database

{{ee-only}}

{{deprecate-split-db}}

L&#39;impostazione della replica del database offre i seguenti vantaggi:

- Backup dei dati
- Abilita l&#39;analisi dei dati senza influire sul database principale
- Scalabilità

I database MySQL vengono replicati in modo asincrono, il che significa che non è necessario che gli slave siano connessi in modo permanente per ricevere gli aggiornamenti dal master.

## Configurare la replica del database

Una discussione approfondita sulla replica del database esula dall&#39;ambito di questa guida. Per configurarlo, puoi consultare una risorsa come:

- [Documentazione di MySQL](https://dev.mysql.com/doc/refman/5.6/en/replication.html)
- [Come impostare la replica master slave in MySQL (digitalocean)](https://www.digitalocean.com/community/tutorials/how-to-set-up-replication-in-mysql)

Commerce fornisce configurazioni MySQL di esempio per i database slave. Una configurazione semplice viene fornita con `ResourceConnections` classe `README.md`.

Di seguito sono riportate alcune informazioni più avanzate fornite esclusivamente a scopo informativo:

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

Per migliorare le prestazioni della replica master-slave, è possibile filtrare alcune tabelle in base alle istanze slave. È consigliabile filtrare tutte le tabelle temporanee con il pattern dei nomi `search\_tmp\_%` utilizzati per la ricerca nel catalogo.

A questo scopo, aggiungi la seguente riga al tuo `my.cnf` file nelle istanze slave:

```conf
replicate-wild-ignore-table=%.search\_tmp\_%
```
