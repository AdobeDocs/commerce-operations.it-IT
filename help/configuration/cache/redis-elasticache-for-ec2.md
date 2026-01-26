---
title: Configurare Redis con AWS ElastiCache
description: Per le istanze Commerce in hosting su EC2, scopri come utilizzare AWS ElastiCache al posto di un’istanza Redis locale. Scopri la configurazione della riga di comando, le opzioni di configurazione e le tecniche di convalida.
feature: Configuration, Cache
source-git-commit: b66479ee1350d92c1d59212283222e5068c263a6
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---


# Configurare Redis con AWS ElastiCache

A partire dalla versione 2.4.3 di Commerce, le istanze in hosting su Amazon EC2 possono utilizzare un AWS ElastiCache al posto di un’istanza Redis locale.

>[!WARNING]
>
>Questa sezione è applicabile solo alle istanze Commerce in esecuzione su VPC Amazon EC2. Non funziona per gli impianti locali.

## Prerequisiti

- **Creare una cache Redis OSS senza server**. Dalla console di gestione di AWS, creare la cache Redis nella stessa area e VPC dell&#39;istanza EC2. Per istruzioni, consulta la [documentazione di AWS Elasticache](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/GettingStarted.serverless-redis.step1.html).

- **Verifica la connessione all&#39;istanza di Commerce EC2**

   - Aprire una connessione SSH all’istanza EC2
   - Nell’istanza EC2, installa il client Redis:

     ```bash
     sudo apt-get install redis
     ```

   - Aggiungi una regola in entrata al gruppo di sicurezza EC2: tipo `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Aggiungi una regola in entrata al gruppo di sicurezza del cluster ElastiCache: tipo `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
   - Connessione a Redis CLI:

     ```bash
     redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port>
     ```

### Configurare Commerce per l&#39;utilizzo del cluster

Commerce supporta più tipi di configurazioni di caching. In genere, le configurazioni di caching sono suddivise tra front-end e back-end. Il caching front-end è classificato come `default`, utilizzato per qualsiasi tipo di cache. Puoi personalizzare o suddividere in cache di livello inferiore per ottenere prestazioni migliori. Una comune configurazione Redis separa la cache predefinita e la cache delle pagine nel proprio Redis Database (RDB).

Eseguire `setup` comandi per specificare gli endpoint Redis.

Per configurare Commerce per Redis come memorizzazione in cache predefinita:

```bash
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=<ElastiCache Primary Endpoint host> --cache-backend-redis-port=<ElastiCache Primary Endpoint port> --cache-backend-redis-db=0
```

Per configurare Commerce per il caching delle pagine Redis:

```bash
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=<ElastiCache Primary Endpoint host> --page-cache-redis-port=<ElastiCache Primary Endpoint port> --page-cache-redis-db=1
```

Per configurare Commerce per l&#39;utilizzo di Redis per l&#39;archiviazione delle sessioni:

```bash
bin/magento setup:config:set --session-save=redis --session-save-redis-host=<ElastiCache Primary Endpoint host> --session-save-redis-port=<ElastiCache Primary Endpoint port> --session-save-redis-log-level=4 --session-save-redis-db=2
```

## Verificare la connettività

**Per verificare che Commerce stia parlando con ElastiCache**:

1. Apri una connessione SSH all’istanza Commerce EC2.
1. Avviare il monitor Redis.

   ```bash
   redis-cli -h <ElastiCache-Primary-Endpoint-host> -p <ElastiCache-Primary-Endpoint-port> monitor
   ```

1. Apri una pagina nell’interfaccia utente di Commerce.
1. Verifica l&#39;[output della cache](#verify-the-redis-connection) nel terminale.
