---
title: Installazione e configurazione di Redis
description: Scopri come installare e configurare Redis per il caching e l’archiviazione delle sessioni con Adobe Commerce. Scopri le opzioni per l’ottimizzazione e l’ottimizzazione delle prestazioni.
feature: Configuration, Cache
exl-id: e037c382-334a-4096-a417-a25fdb61a9ce
badgePaas: label="On-Premises" type="Informative" url="https://experienceleague.adobe.com/it/docs/commerce/user-guides/product-solutions" tooltip="Applicabile solo ai progetti locali di Adobe Commerce."
autotag-review: '2026-06-22T20:26:29.348Z'
TQID: 'https://experienceleague.adobe.com/N61AAy4ihSIlhEjdvpji2XVOdZuHWhytp9zgoAU41K4'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
topic_v2:
  - id: b5ce8718-c3af-4fdb-a1a9-fca32f83a87c
source-git-commit: ab2a9ef6d4c3ed692f4a6a66323ab5e3d5c6673a
workflow-type: tm+mt
source-wordcount: 456
ht-degree: 0%

---

# Installare e configurare Redis

Redis è un archivio dati in memoria che può essere utilizzato come back-end della cache e per l’archiviazione della sessione. Le caratteristiche principali includono:

- Archiviazione sessione PHP
- Pulizia della cache basata su tag senza `foreach` cicli
- Salvataggio su disco e replica master/slave

{{cloud-cache-config}}

## Installare Redis

L&#39;installazione e la configurazione del software Redis esulano dall&#39;ambito di questa guida. Consulta risorse quali:

- [Scarica pagina Redis](https://redis.io/download)
- [Guida introduttiva Redis](https://redis.io/docs/latest/)
- [DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-redis)
- [Pagina della documentazione di Redis](https://redis.io/docs)

## Configurare la configurazione Redis

A seconda dell&#39;installazione, la configurazione Redis è in genere disponibile in uno dei seguenti file: `/etc/redis/redis.conf` o `/etc/redis/<port>.conf`

Per ottimizzare l’istanza Redis in base alle tue esigenze, ottieni risultati ottimali utilizzando un’istanza dedicata per ogni sessione, cache Commerce e FPC.

Per le sessioni, Adobe consiglia di abilitare la persistenza per copiare i dati Redis su disco utilizzando una delle seguenti opzioni di persistenza: istantanee RDB (Redis Database Backup) regolari o registri di persistenza AOF (Append Only File).

- **Redis Database Backup** (RDB) gli snapshot memorizzano il database completo in un file di dump dopo un determinato periodo di tempo, quando è stato modificato un numero minimo di chiavi dall&#39;ultimo salvataggio. Utilizzare l&#39;impostazione `save` nel file `redis.conf` per configurare questa impostazione.

- **Aggiungi solo file** (AOF) memorizza ogni operazione di scrittura inviata a Redis in un file di diario. Redis legge il file solo al riavvio e lo utilizza per ripristinare il set di dati originale.

È inoltre possibile abilitare contemporaneamente sia le opzioni RDB che AOF. Per ulteriori dettagli, inclusi i vantaggi e gli svantaggi delle opzioni di persistenza, vedere la [documentazione sulla persistenza Redis](https://redis.io/topics/persistence).

Per l’istanza della cache, imposta l’istanza in modo che sia sufficientemente grande da memorizzare l’intera cache di Commerce. I requisiti di dimensione dipendono da diversi fattori come il numero di prodotti e di visualizzazioni dello store. Come punto di partenza, puoi utilizzare le dimensioni della cartella della cache sul file system. Ad esempio, se la cartella `var/cache` nel file system è di 5 GB, impostare l&#39;istanza Redis con almeno 5 GB per l&#39;avvio. La persistenza non è necessaria per l’istanza della cache perché è possibile ripristinare la cache di Commerce. Consulta la [Guida alla cache Redis](https://redis.io/docs/latest/develop/use/).

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
