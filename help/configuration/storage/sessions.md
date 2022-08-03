---
title: Percorso di archiviazione sessione
description: Scopri dove sono memorizzati i file di sessione.
source-git-commit: 27c3914540a0574fa4ff58df50d5cd2c71fb6670
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 0%

---


# Percorso di archiviazione sessione

Questo argomento illustra come individuare la posizione in cui vengono archiviati i file di sessione. Il sistema utilizza la logica seguente per memorizzare i file di sessione:

- Se hai configurato la memorizzazione in cache, le sessioni vengono memorizzate in RAM; vedere [Utilizzare la cache per l&#39;archiviazione delle sessioni](memcached.md).
- Se hai configurato Redis, le sessioni vengono memorizzate sul server Redis; vedere [Utilizzare Redis per l&#39;archiviazione delle sessioni](../cache/redis-session.md).
- Se utilizzi l’archiviazione predefinita delle sessioni basata su file, le sessioni vengono memorizzate nelle seguenti posizioni nell’ordine mostrato:

   1. Directory definita in [`env.php`](#example-in-envphp)
   1. Directory definita in [`php.ini`](#example-in-phpini)
   1. `<magento_root>/var/session` directory

## Esempio in `env.php`

Frammento di esempio da `<magento_root>/app/etc/env.php` seguente:

```php
 'session' => [
     'save' => 'files',
     'save_path' => '/var/www/session'
 ],
```

Nell&#39;esempio precedente vengono memorizzati i file di sessione in `/var/www/session`

## Esempio in `php.ini`

Come utente con `root` privilegi, apri `php.ini` e cerca il valore di `session.save_path`. Questo identifica dove vengono memorizzate le sessioni.

## Gestione delle dimensioni della sessione

Consulta la sezione [Gestione delle sessioni](https://docs.magento.com/user-guide/stores/security-session-management.html) in _Guida utente_.

## Configurazione della raccolta rifiuti

Per pulire le sessioni scadute, il sistema chiama `gc` (_raccolta dei rifiuti_) in modo casuale in base a una probabilità calcolata dal `gc_probability / gc_divisor` direttiva. Ad esempio, se si impostano queste direttive su `1/100` rispettivamente, significa una probabilità di `1%` (_probabilità di una chiamata di raccolta oggetti inattivi per 100 richieste_).

Il gestore della raccolta degli oggetti inattivi utilizza `gc_maxlifetime` direttiva: il numero di secondi dopo i quali le sessioni vengono visualizzate come _immondizia_ e potenzialmente ripulito.

Su alcuni sistemi operativi (Debian/Ubuntu), il valore predefinito `session.gc_probability` direttiva `0`, che impedisce l’esecuzione del gestore di raccolta oggetti inattivi.

È possibile sovrascrivere `session.gc_` le direttive `php.ini` nel `<magento_root>/app/etc/env.php` file:

```php
 'session' => [
     'save' => 'db',
     'gc_probability' => 1,
     'gc_divisor' => 1000,
     'gc_maxlifetime' => 1440
 ],
```

La configurazione varia a seconda del traffico e delle esigenze specifiche del sito web del commerciante.
