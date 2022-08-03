---
title: Utilizzare la cache per l'archiviazione delle sessioni
description: Scopri come utilizzare la cache per l’archiviazione delle sessioni Commerce.
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---


# Utilizzare la cache per l&#39;archiviazione delle sessioni

Memcache è un sistema di memorizzazione in cache della memoria distribuita a scopo generale. Viene spesso utilizzato per velocizzare i siti web dinamici basati su database memorizzando nella cache dati e oggetti in RAM per ridurre il numero di volte in cui è necessario leggere un&#39;origine dati esterna (ad esempio un database o un&#39;API).

Memcache fornisce una tabella hash di grandi dimensioni che può essere distribuita su più computer. Quando la tabella è piena, gli inserimenti successivi fanno sì che i dati meno recenti vengano eliminati nell’ordine meno recente utilizzato (LRU). La dimensione di questa tabella hash è spesso molto grande. (Origine: [memcached.org](http://memcached.org/))

Commerce utilizza memcache per l’archiviazione delle sessioni ma non per il caching delle pagine. Per la memorizzazione in cache delle pagine, si consiglia di [Redis](../cache/redis-pg-cache.md) o [Vernice](../cache/config-varnish.md).

**Per configurare Commerce per l’utilizzo della cache in memoria**:

1. Apri `<your install dir>/app/etc/env.php` in un editor di testo.
1. Individua quanto segue:

   ```php
   'session' =>
       array (
       'save' => 'files',
   ),
   ```

1. Modificalo come segue:

   ```php
   'session' =>
       array (
         'save' => 'memcached',
         'save_path' => '<memcache ip or host>:<memcache port>'
   ),
   ```

   Memcache dispone di parametri di avvio facoltativi che esulano dall’ambito di questa guida. Puoi trovare ulteriori informazioni su di esse nella sezione [memorizzato](https://php.net/manual/en/memcached.sessions.php) documentazione, codice sorgente e registri delle modifiche.

1. Procedi alla sezione successiva.

**Per verificare i lavori in cache con Commerce**:

1. Elimina il contenuto delle seguenti directory nella directory di installazione Commerce:

   ```bash
   rm -rf var/cache/* var/page_cache/* var/session/*
   ```

1. Vai a qualsiasi pagina nella vetrina.

1. Accedi all’amministratore e naviga su diverse pagine.

   Se non vengono visualizzati errori, congratulazioni! Memcache funziona! Facoltativamente, puoi esaminare l’archiviazione memorizzata nella cache come descritto nel passaggio successivo.

   Se vengono visualizzati degli errori (ad esempio HTTP 500 (Errore interno del server)), abilita la modalità sviluppatore e analizza il problema. Assicurati che la cache sia in esecuzione, configurata correttamente e che `env.php` non ha errori di sintassi.

1. (Facoltativo.) Utilizzare Telnet per esaminare l&#39;archiviazione memorizzata nella cache.

   ```bash
   telnet <memcached host or ip> <memcached port>
   ```

   ```bash
   stats items
   ```

   I risultati vengono visualizzati in modo simile ai seguenti:

   ```terminal
   STAT items:3:number 1
   STAT items:3:age 7714
   STAT items:3:evicted 0
   STAT items:3:evicted_nonzero 0
   STAT items:3:evicted_time 0
   STAT items:3:outofmemory 0
   STAT items:3:tailrepairs 0
   
   [Look at the keys in more detail](http://www.darkcoding.net/software/memcached-list-all-keys/)
   ```
