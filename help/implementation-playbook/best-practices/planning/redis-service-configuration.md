---
title: Best practice per la configurazione del servizio Redis
description: Scopri come migliorare le prestazioni del caching utilizzando l’implementazione estesa della cache Redis per Adobe Commerce 2.3.5.
role: Developer, Admin
feature-set: Commerce
feature: Best Practices
source-git-commit: 12de523cc7ea1486c894d54efe6944d92d87ded0
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---


# Best practice per la configurazione del servizio Redis

- Per Adobe Commerce 2.3.3 e versioni successive implementato sull&#39;infrastruttura cloud, effettua l&#39;aggiornamento alla versione 5.0 di Redis.
- Per Adobe Commerce versione 2.3.5 o successiva, utilizza l’implementazione estesa della cache Redis. Questa implementazione include le seguenti ottimizzazioni per ridurre al minimo il numero di query Redis eseguite su ogni richiesta da Adobe Commerce:
   - Diminuire le dimensioni dei trasferimenti di dati di rete tra Redis e Adobe Commerce
   - Riduzione del consumo di Redis dei cicli della CPU migliorando la capacità dell&#39;adattatore di determinare automaticamente ciò che deve essere caricato
   - Ridurre le condizioni di gara sulle operazioni di riscrittura

## Prodotti e versioni interessati

Adobe Commerce su infrastruttura cloud con versione 2.3.3 o successiva.
Adobe Commerce (tutti i metodi di distribuzione), versione 2.3.5 e successive

## Aggiorna la versione di Redis per le distribuzioni cloud

Per le implementazioni Adobe Commerce sull&#39;infrastruttura cloud con Adobe Commerce 2.3.3 o versioni successive, aggiorna il servizio Redis alla versione 5.0. Per istruzioni, consulta i seguenti argomenti nella documentazione Adobe Commerce sull&#39;infrastruttura cloud:

- [Configurazione del servizio Redis](https://devdocs.magento.com/cloud/project/services-redis.html)
- [Modificare la versione del servizio](https://devdocs.magento.com/cloud/project/services.html#change-service-version)

## Configurare l’implementazione estesa della cache Redis

Per Adobe Commerce 2.3.5 e versioni successive, aggiorna la configurazione per utilizzare l’implementazione estesa della cache Redis `\Magento\Framework\Cache\Backend\Redis`.

### Configurazione per le distribuzioni cloud

Con `ece-tools` 2002.1.1 o versione successiva, configura la cache Redis avanzata impostando il `REDIS_BACKEND` variabile di distribuzione nel file di configurazione dell’ambiente, `.magento.env.yaml`

```yaml
stage:
  deploy:
    REDIS_BACKEND: '\Magento\Framework\Cache\Backend\Redis'
```

Per maggiori dettagli, vedi [Distribuisci variabili > `REDIS_BACKEND`](https://devdocs.magento.com/cloud/env/variables-deploy.html#redis_backend) nella documentazione per Adobe Commerce sull’infrastruttura cloud.

>[!NOTE]
>
> Controlla la versione di ece-tools installata nel tuo ambiente cloud locale dalla riga di comando utilizzando `composer show magento/ece-tools` comando. Se necessario, [aggiorna la versione di ece-tools](https://devdocs.magento.com/cloud/project/ece-tools-update.html).

>[!WARNING]
>
>Do _not_ configurare una connessione slave Redis per progetti di infrastruttura cloud con un [architettura scalata](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/scaled-architecture.html). Questo causa errori di connessione Redis. Vedi [guida alla configurazione di Redis](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/env/stage/variables-deploy.html#redis_use_slave_connection) in _Commerce sull’infrastruttura cloud_ guida.


### Configurazione per le distribuzioni locali

Per le implementazioni on-premise di Adobe Commerce, configura la nuova implementazione della cache Redis utilizzando il `bin/magento:setup` comandi. Per istruzioni, consulta [Usa Redis per la cache predefinita](../../../configuration/cache/redis-pg-cache.md#configure-redis-page-caching).

## Informazioni aggiuntive

- [Adobe Commerce Release v2.3.5 - Miglioramenti delle prestazioni](https://devdocs.magento.com/guides/v2.3/release-notes/release-notes-2-3-5-commerce.html#performance-boosts)
- [Cache della pagina Redis](../../../configuration/cache/redis-pg-cache.md)


