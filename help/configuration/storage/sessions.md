---
title: Percorso di archiviazione sessione
description: Scopri dove vengono memorizzati i file della sessione.
feature: Configuration, Storage
exl-id: 43cab98a-5b68-492e-b891-8db4cc99184e
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '257'
ht-degree: 0%

---

# Percorso di archiviazione sessione

Questo argomento illustra come individuare la posizione in cui sono archiviati i file di sessione. Per memorizzare i file di sessione, il sistema utilizza la logica seguente:

- Se hai configurato Memcached, le sessioni sono archiviate in RAM; vedi [Usa Memcached per l&#39;archiviazione delle sessioni](memcached.md).
- Se hai configurato Redis, le sessioni sono archiviate sul server Redis; vedi [Utilizzare Redis per l&#39;archiviazione delle sessioni](../cache/redis-session.md).
- Se utilizzi l’archiviazione di sessioni basata su file predefinita, le sessioni vengono memorizzate nelle seguenti posizioni nell’ordine indicato:

   1. Directory definita in [`env.php`](#example-in-envphp)
   1. Directory definita in [`php.ini`](#example-in-phpini)
   1. Directory `<magento_root>/var/session`

## Esempio in `env.php`

Di seguito è riportato uno snippet di esempio da `<magento_root>/app/etc/env.php`:

```php
 'session' => [
     'save' => 'files',
     'save_path' => '/var/www/session'
 ],
```

Nell&#39;esempio precedente i file di sessione vengono archiviati in `/var/www/session`

## Esempio in `php.ini`

Come utente con privilegi di `root`, apri il file `php.ini` e cerca il valore di `session.save_path`. Questo identifica dove vengono memorizzate le sessioni.

## Gestisci dimensioni sessione

Consulta la [Gestione delle sessioni](https://experienceleague.adobe.com/it/docs/commerce-admin/systems/security/security-session-management) nella _Guida utente_.

## Configurazione della raccolta di oggetti inattivi

Per pulire le sessioni scadute, il sistema chiama il gestore `gc` (_garbage collection_) in modo casuale in base a una probabilità calcolata dalla direttiva `gc_probability / gc_divisor`. Ad esempio, se imposti queste direttive rispettivamente su `1/100`, ciò significa una probabilità di `1%` (_probabilità di una chiamata di Garbage Collection per 100 richieste_).

Il gestore di Garbage Collection utilizza la direttiva `gc_maxlifetime`, ovvero il numero di secondi dopo i quali le sessioni vengono visualizzate come _garbage_ e potenzialmente pulite.

In alcuni sistemi operativi (Debian/Ubuntu), la direttiva `session.gc_probability` predefinita è `0`, che impedisce l&#39;esecuzione del gestore di Garbage Collection.

È possibile sovrascrivere le direttive `session.gc_` dal file `php.ini` nel file `<magento_root>/app/etc/env.php`:

```php
 'session' => [
     'save' => 'db',
     'gc_probability' => 1,
     'gc_divisor' => 1000,
     'gc_maxlifetime' => 1440
 ],
```

La configurazione varia a seconda del traffico e delle esigenze specifiche del sito web del commerciante.
