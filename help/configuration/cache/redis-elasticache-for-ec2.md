---
title: Configurare Redis con AWS ElastiCache
description: Scopri come utilizzare AWS ElastiCache come back-end Redis per Adobe Commerce su EC2. Individua l'installazione, la configurazione e la convalida della riga di comando.
feature: Configuration, Cache
autotag-review: '2026-06-22T21:54:39.355Z'
TQID: 'https://experienceleague.adobe.com/p4-Pyc3yWwokyFOAyAjN3r1Ic26brx83bPf-GZQNSN8'
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: e7dae43f-215c-4cdf-90d3-c5a461a6e669
    internal-label: Admin tools and workspace
subfeature_v2:
  - id: b673188e-f9fa-492a-b470-c8f949bf7827
    internal-label: Cache
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: b5a62a22-46f7-4f0d-b151-3fc640bef588
    internal-label: Intermediate
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
topic_v2:
  - id: d095671a-1355-40aa-8b5f-06c33c68080b
    internal-label: Security
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 0%
---

# Configurare Redis con AWS ElastiCache

A partire dalla versione 2.4.3 di Commerce, le istanze in hosting su Amazon EC2 possono utilizzare un AWS ElastiCache al posto di un’istanza Redis locale.

>[!WARNING]
>
>Questa sezione è applicabile solo alle istanze Commerce in esecuzione su VPC Amazon EC2.

## Prerequisiti

- **Creare una cache Redis OSS senza server**. Dalla console di gestione di AWS, creare la cache Redis nella stessa area e VPC dell&#39;istanza EC2. Per istruzioni, consulta la [documentazione di AWS Elasticache](https://docs.aws.amazon.com/AmazonElastiCache/latest/dg/GettingStarted.serverless-redis.step1.html).

- **Verifica la connessione all&#39;istanza di Commerce EC2**

  - Aprire una connessione SSH all’istanza EC2
  - Nell’istanza EC2, installa il client Redis:

    ```shell
    sudo apt-get install redis
    ```

  - Aggiungi una regola in entrata al gruppo di sicurezza EC2: tipo `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
  - Aggiungi una regola in entrata al gruppo di sicurezza del cluster ElastiCache: tipo `- Custom TCP, port - 6379, Source - 0.0.0.0/0`
  - Connessione a Redis CLI:

    ```shell
    redis-cli -h <ElastiCache Primary Endpoint host> -p <ElastiCache Primary Endpoint port>
    ```

### Configurare Commerce per l&#39;utilizzo del cluster

Commerce supporta più tipi di configurazioni di caching. In genere, le configurazioni di caching sono suddivise tra front-end e back-end. Il caching front-end è classificato come `default`, utilizzato per qualsiasi tipo di cache. Puoi personalizzare o suddividere in cache di livello inferiore per ottenere prestazioni migliori. Una comune configurazione Redis separa la cache predefinita e la cache delle pagine nel proprio Redis Database (RDB).

Eseguire `setup` comandi per specificare gli endpoint Redis.

Per configurare Commerce per Redis come memorizzazione in cache predefinita:

```shell
bin/magento setup:config:set --cache-backend=redis --cache-backend-redis-server=<ElastiCache Primary Endpoint host> --cache-backend-redis-port=<ElastiCache Primary Endpoint port> --cache-backend-redis-db=0
```

Per configurare Commerce per il caching delle pagine Redis:

```shell
bin/magento setup:config:set --page-cache=redis --page-cache-redis-server=<ElastiCache Primary Endpoint host> --page-cache-redis-port=<ElastiCache Primary Endpoint port> --page-cache-redis-db=1
```

Per configurare Commerce per l&#39;utilizzo di Redis per l&#39;archiviazione delle sessioni:

```shell
bin/magento setup:config:set --session-save=redis --session-save-redis-host=<ElastiCache Primary Endpoint host> --session-save-redis-port=<ElastiCache Primary Endpoint port> --session-save-redis-log-level=4 --session-save-redis-db=2
```

## Verificare la connettività

**Per verificare che Commerce stia parlando con ElastiCache**:

1. Apri una connessione SSH all’istanza Commerce EC2.
1. Avviare il monitor Redis.

   ```shell
   redis-cli -h <ElastiCache-Primary-Endpoint-host> -p <ElastiCache-Primary-Endpoint-port> monitor
   ```

1. Apri una pagina nell’interfaccia utente di Commerce.
1. Verifica l&#39;[output della cache](#verify-connectivity) nel terminale.
