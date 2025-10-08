---
title: Configura Valkey
description: Scopri come configurare il caching di Valkey per l’ottimizzazione delle prestazioni di Adobe Commerce. Scopri le funzioni, i passaggi di configurazione e le best practice per la configurazione.
feature: Configuration, Cache
exl-id: 12dbc171-3df6-4413-869b-a3450b5647b4
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 0%

---

# Configura Valkey

Le caratteristiche principali includono:

- Archiviazione sessione PHP
- Pulizia della cache basata su tag senza `foreach` cicli
- Salvataggio su disco e replica master/slave

## Installa Valkey

Per installare e configurare il software Valkey, consultare le risorse seguenti:

- [Scarica pagina Valkey](https://valkey.io/download/)
- [Avvio rapido Valkey](https://valkey.io/topics/quickstart/)
- [Pagina documentazione Valkey](https://valkey.io/docs)

## Configurare la configurazione Valkey

A seconda dell&#39;installazione, la configurazione di Valkey è in genere disponibile nel file `/etc/valkey/valkey.conf` o nel file `/etc/valkey/<port>.conf`.

Per ottimizzare l’istanza Valkey in base alle tue esigenze, puoi ottenere risultati ottimali utilizzando un’istanza dedicata per ogni sessione, cache di Commerce e FPC.

Adobe consiglia di abilitare la persistenza per le sessioni per copiare i dati Valkey su disco. È possibile utilizzare snapshot di Backup database Valkey (RDB) o registri di persistenza AOF (Append Only File).

- Gli snapshot di **RDB** (database Valkey) memorizzano il database completo in un file di dump dopo un determinato periodo di tempo, quando è stato modificato un numero minimo di chiavi dall&#39;ultimo salvataggio. Utilizzare l&#39;impostazione `save` nel file `valkey.conf` per configurare questa impostazione.

- **Aggiungi solo file** (AOF) memorizza ogni operazione di scrittura inviata a Valkey in un file journal. Valkey legge questo file solo al riavvio e lo utilizza per ripristinare il set di dati originale.

È inoltre possibile abilitare contemporaneamente sia le opzioni RDB che AOF. Per ulteriori dettagli, inclusi i vantaggi e gli svantaggi delle opzioni di persistenza, vedere la [documentazione sulla persistenza di Valkey](https://valkey.io/topics/persistence/).

Per l’istanza della cache, imposta l’istanza in modo che sia sufficientemente grande da memorizzare l’intera cache di Commerce. I requisiti di dimensione dipendono da diversi fattori come il numero di prodotti e di visualizzazioni dello store. Come punto di partenza, puoi utilizzare le dimensioni della cartella della cache sul file system. Ad esempio, se la cartella `var/cache` nel file system è di 5 GB, impostare l&#39;istanza Valkey con almeno 5 GB per l&#39;avvio. La persistenza non è necessaria per l’istanza della cache perché è possibile ripristinare la cache di Commerce.

Per ottimizzare le prestazioni, è possibile attivare le seguenti impostazioni per l&#39;eliminazione asincrona. Queste impostazioni non modificano il comportamento di Valkey.

```ini
lazyfree-lazy-eviction yes
lazyfree-lazy-expire yes
lazyfree-lazy-server-del yes
replica-lazy-flush yes
lazyfree-lazy-user-del yes
```
