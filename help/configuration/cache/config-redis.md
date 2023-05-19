---
title: Configurare Redis
description: Panoramica delle funzioni di Redis e configurazione di Redis.
exl-id: e037c382-334a-4096-a417-a25fdb61a9ce
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Configurare Redis

Le funzioni di Redis includono:

- Archiviazione sessione PHP
- Pulizia della cache basata su tag senza `foreach` cicli
- Salvataggio su disco e replica master/slave

## Installare Redis

L&#39;installazione e la configurazione del software Redis esulano dall&#39;ambito di questa guida. Consulta risorse quali:

- [Scarica pagina Redis](https://redis.io/download)
- [Guida introduttiva Redis](https://redis.io/docs/getting-started/)
- [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-redis)
- [Pagina della documentazione di Redis](https://redis.io/docs)

## Configurare la configurazione Redis

A seconda dell’installazione, in genere la configurazione Redis è disponibile in uno dei seguenti file: `/etc/redis/redis.conf` o `/etc/redis/<port>.conf`

Per ottimizzare l’istanza Redis in base alle tue esigenze, puoi ottenere risultati migliori utilizzando un’istanza dedicata per ogni sessione, cache Commerce e FPC.

Per le sessioni, l&#39;Adobe consiglia di abilitare la persistenza per copiare i dati Redis su disco utilizzando una delle seguenti opzioni di persistenza: istantanee RDB (Redis Database Backup) regolari o registri di persistenza AOF (Append Only File).

- **Backup Redis Database** (RDB) Le istantanee memorizzano l&#39;intero database in un file di dump dopo un determinato periodo di tempo, quando un numero minimo di chiavi è stato modificato dopo l&#39;ultimo salvataggio. Utilizza il `save` impostazione all&#39;interno del `redis.conf` per configurare questa impostazione.

- **Aggiungi solo file** (AOF) memorizza ogni operazione di scrittura inviata a Redis in un file di diario. Redis legge il file solo al riavvio e lo utilizza per ripristinare il set di dati originale.

È inoltre possibile abilitare contemporaneamente sia le opzioni RDB che AOF. Per ulteriori dettagli, tra cui i vantaggi e gli svantaggi delle opzioni di persistenza, vedi [Documentazione di Redis Persistence](https://redis.io/topics/persistence).

Per l’istanza della cache, imposta l’istanza in modo che sia sufficientemente grande da memorizzare l’intera cache di Commerce. I requisiti di dimensione dipendono da diversi fattori come il numero di prodotti e di visualizzazioni dello store. Come punto di partenza, puoi utilizzare le dimensioni della cartella della cache sul file system. Ad esempio, se `var/cache` sul file system è di 5 GB, configura l’istanza Redis con almeno 5 GB per l’avvio. La persistenza non è necessaria per l’istanza della cache perché è possibile ripristinare la cache di Commerce. Consulta [Guida alla cache Redis](https://redis.io/docs/manual/eviction/).

Per ottimizzare le prestazioni, è possibile attivare le seguenti impostazioni per l&#39;eliminazione asincrona. Queste impostazioni non modificano il comportamento di Redis.

```ini
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
```

In Redis 6.x e versioni successive è inoltre possibile aggiungere il valore seguente:

```ini
lazyfree-lazy-user-del yes
```
