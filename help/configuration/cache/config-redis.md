---
title: Configura Redis
description: Ottieni una panoramica delle funzioni di Redis e avvia la tua configurazione di Redis.
source-git-commit: 0d106b36f479ecf2eda3fecf6740b28d4b6793eb
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Configura Redis

Le funzioni Redis includono:

- Archiviazione sessione PHP
- Pulizia della cache basata su tag senza `foreach` loop
- Salvataggio su disco e replica master/slave

## Installa Redis

L&#39;installazione e la configurazione del software Redis va oltre l&#39;ambito di questa guida. Consulta le risorse come:

- [Scarica la pagina Redis](https://redis.io/download)
- [Avvio rapido di Redis](https://redis.io/docs/getting-started/)
- [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-redis)
- [Pagina della documentazione di Redis](https://redis.io/docs)

## Configurare la configurazione Redis

A seconda dell’installazione, in genere è possibile trovare la configurazione Redis in uno dei file seguenti: `/etc/redis/redis.conf` o `/etc/redis/<port>.conf`

Per ottimizzare l’istanza di Redis per le tue esigenze, ottieni i migliori risultati utilizzando un’istanza dedicata per ogni sessione, la cache Commerce e FPC.

Per le sessioni, Adobe consiglia di abilitare la persistenza per copiare i dati Redis su disco utilizzando una delle seguenti opzioni di persistenza: istantanee normali di backup del database (RDB) o registri di persistenza di Aggiungi solo file (AOF).

- **Backup database Redis** (RDB) le istantanee memorizzano l&#39;intero database in un file di dump dopo un determinato periodo di tempo, quando un numero minimo di chiavi è cambiato dall&#39;ultimo salvataggio. Utilizza la `save` impostazione all&#39;interno del `redis.conf` per configurare questa impostazione.

- **Aggiungi solo file** (AOF) memorizza ogni operazione di scrittura inviata a Redis in un file giornale di registrazione. Redis legge questo file solo al riavvio e lo utilizza per ripristinare il set di dati originale.

Puoi anche abilitare contemporaneamente sia le opzioni RDB che AOF. Per ulteriori dettagli, compresi i vantaggi e gli svantaggi delle opzioni di persistenza, consulta la sezione [Documentazione sulla persistenza di Redis](https://redis.io/topics/persistence).

Per l’istanza di cache, imposta l’istanza in modo che sia sufficientemente grande per memorizzare l’intera cache Commerce. I requisiti di dimensione dipendono da fattori diversi, come il numero di prodotti e le visualizzazioni del negozio. Come punto di partenza, è possibile utilizzare la dimensione della cartella cache sul file system. Ad esempio, se `var/cache` la cartella sul tuo file system è di 5 GB, imposta l&#39;istanza Redis con almeno 5 GB per avviarla. La persistenza non è necessaria per l’istanza di cache perché è possibile ripristinare la cache Commerce. Vedi [Guida alla cache di Redis](https://redis.io/docs/manual/eviction/).

Per ottimizzare le prestazioni, puoi abilitare le seguenti impostazioni per l’eliminazione asincrona. Queste impostazioni non modificano il comportamento di Redis.

```ini
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
```

Su Redis 6.x e versioni successive, puoi anche aggiungere il seguente valore:

```ini
lazyfree-lazy-user-del yes
```
