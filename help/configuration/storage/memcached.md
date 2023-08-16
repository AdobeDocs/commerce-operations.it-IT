---
title: Usa memcached per l’archiviazione della sessione
description: Scopri come utilizzare memcache per l’archiviazione delle sessioni di Commerce.
feature: Configuration, Cache, Storage
exl-id: 24077929-e732-4579-8d7d-717a4902fc64
source-git-commit: af45ac46afffeef5cd613628b2a98864fd7da69b
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Usa memcached per l’archiviazione della sessione

Memcached è un sistema di caching di memoria distribuito per scopi generici. Viene spesso utilizzato per velocizzare i siti web dinamici basati su database memorizzando nella cache dati e oggetti nella RAM per ridurre il numero di volte in cui è necessario leggere un’origine dati esterna (ad esempio un database o un’API).

Memcached fornisce una tabella hash di grandi dimensioni che può essere distribuita su più computer. Quando la tabella è piena, gli inserimenti successivi causano l&#39;eliminazione dei dati meno recenti in base all&#39;ordine LRU utilizzato di recente. La dimensione di questa tabella hash è spesso molto grande. (Origine: [memcached.org](https://www.memcached.org/))

Commerce utilizza memcached per l’archiviazione della sessione ma non per il caching delle pagine. Per il caching delle pagine, consigliamo [Redis](../cache/redis-pg-cache.md) o [Vernice](../cache/config-varnish.md).

**Per configurare Commerce per l’utilizzo di memcached**:

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

   memcached dispone di parametri di avvio facoltativi che vanno oltre l’ambito di questa guida. Per ulteriori informazioni, consulta la sezione [memcached](https://www.php.net/manual/en/memcached.sessions.php) documentazione, codice sorgente e registri delle modifiche.

1. Procedi alla sezione successiva.

**Verificare il funzionamento di memcached con Commerce**:

1. Elimina il contenuto delle seguenti directory nella directory di installazione di Commerce:

   ```bash
   rm -rf var/cache/* var/page_cache/* var/session/*
   ```

1. Vai a qualsiasi pagina della vetrina.

1. Accedi all’amministratore e individua diverse pagine.

   Se non vengono visualizzati errori, congratulazioni! memcached funziona. Facoltativamente, puoi esaminare l’archiviazione memcached come descritto nel passaggio successivo.

   Se vengono visualizzati degli errori (ad esempio, HTTP 500 (Errore interno del server)), abilita la modalità sviluppatore e diagnostica il problema. Assicurati che memcached sia in esecuzione, configurato correttamente e che `env.php` non presenta errori di sintassi.

1. (Facoltativo.) Utilizza Telnet per esaminare l’archiviazione memorizzata in memcache.

   ```bash
   telnet <memcached host or ip> <memcached port>
   ```

   ```bash
   stats items
   ```

   I risultati vengono visualizzati in modo simile al seguente:

   ```terminal
   STAT items:3:number 1
   STAT items:3:age 7714
   STAT items:3:evicted 0
   STAT items:3:evicted_nonzero 0
   STAT items:3:evicted_time 0
   STAT items:3:outofmemory 0
   STAT items:3:tailrepairs 0
   
   [Look at the keys in more detail](https://darkcoding.net/software/memcached-list-all-keys/)
   ```
