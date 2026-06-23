---
title: Installazione e configurazione di Valkey
description: Scopri come installare e configurare Valkey per il caching e l’archiviazione delle sessioni con Adobe Commerce. Scopri le opzioni per l’ottimizzazione e l’ottimizzazione delle prestazioni.
feature: Configuration, Cache
exl-id: 12dbc171-3df6-4413-869b-a3450b5647b4
badgePaas: label="On-Premises" type="Informative" url="https://experienceleague.adobe.com/it/docs/commerce/user-guides/product-solutions" tooltip="Applicabile solo ai progetti locali di Adobe Commerce."
TQID: 'https://experienceleague.adobe.com/Ef4WREy0eq0ChsrI5-0FtrjMZWNjwr7l71Pm-RHD1GI'
product_v2:
  - id: b974b164-8a4e-43b8-a9e2-8e67ec131677
  - id: eadea719-cf89-469b-a6fd-a236a7138047
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
source-wordcount: 414
ht-degree: 0%

---

# Installare e configurare Valkey

Valkey è un archivio dati in memoria open source compatibile con Redis che può essere utilizzato come back-end della cache e per l’archiviazione della sessione. Le caratteristiche principali includono:

- Archiviazione sessione PHP
- Pulizia della cache basata su tag senza `foreach` cicli
- Salvataggio su disco e replica master/slave

{{cloud-cache-config}}

## Installa Valkey

Per installare e configurare il software Valkey, consultare le risorse seguenti:

- [Scarica pagina Valkey](https://valkey.io/download/){target="_blank"}
- [Guida introduttiva di Valkey](https://valkey.io/topics/quickstart/){target="_blank"}
- [Pagina della documentazione di Valkey](https://valkey.io/docs){target="_blank"}

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
