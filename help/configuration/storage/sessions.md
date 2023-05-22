---
title: Percorso di archiviazione sessione
description: Scopri dove vengono memorizzati i file della sessione.
feature: Configuration, Storage
exl-id: 43cab98a-5b68-492e-b891-8db4cc99184e
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---

# Percorso di archiviazione sessione

Questo argomento illustra come individuare la posizione in cui sono archiviati i file di sessione. Per memorizzare i file di sessione, il sistema utilizza la logica seguente:

- Se hai configurato memcached, le sessioni vengono memorizzate in RAM; vedi [Usa memcached per l’archiviazione della sessione](memcached.md).
- Se hai configurato Redis, le sessioni vengono memorizzate sul server Redis; vedi [Usa Redis per l’archiviazione della sessione](../cache/redis-session.md).
- Se utilizzi l’archiviazione di sessioni basata su file predefinita, le sessioni vengono memorizzate nelle seguenti posizioni nell’ordine indicato:

   1. Directory definita in [`env.php`](#example-in-envphp)
   1. Directory definita in [`php.ini`](#example-in-phpini)
   1. `<magento_root>/var/session` directory

## Esempio in `env.php`

Un frammento di esempio da `<magento_root>/app/etc/env.php` segue:

```php
 'session' => [
     'save' => 'files',
     'save_path' => '/var/www/session'
 ],
```

L&#39;esempio precedente memorizza i file di sessione in `/var/www/session`

## Esempio in `php.ini`

Come utente con `root` , aprire il `php.ini` e cerca il valore di `session.save_path`. Questo identifica dove vengono memorizzate le sessioni.

## Gestisci dimensioni sessione

Consulta la [Gestione delle sessioni](https://docs.magento.com/user-guide/stores/security-session-management.html) nel _Guida utente_.

## Configurazione della raccolta di oggetti inattivi

Per pulire le sessioni scadute, il sistema chiama il `gc` (_Garbage Collection_) in modo casuale in base a una probabilità calcolata dal gestore `gc_probability / gc_divisor` direttiva. Ad esempio, se imposti queste direttive su `1/100` rispettivamente, indica una probabilità di `1%` (_probabilità di una chiamata di garbage collection per 100 richieste_).

Il gestore di Garbage Collection utilizza `gc_maxlifetime` direttiva: il numero di secondi dopo i quali le sessioni vengono visualizzate come _immondizia_ e potenzialmente puliti.

Su alcuni sistemi operativi (Debian/Ubuntu), il valore predefinito `session.gc_probability` la direttiva è `0`, che impedisce l&#39;esecuzione del gestore di Garbage Collection.

Puoi sovrascrivere il `session.gc_` direttive del `php.ini` file in `<magento_root>/app/etc/env.php` file:

```php
 'session' => [
     'save' => 'db',
     'gc_probability' => 1,
     'gc_divisor' => 1000,
     'gc_maxlifetime' => 1440
 ],
```

La configurazione varia a seconda del traffico e delle esigenze specifiche del sito web del commerciante.
