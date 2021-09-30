---
title: Performance Optimization Recommendations
description: Ottimizza le prestazioni dell’implementazione Adobe Commerce seguendo questi consigli.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '1287'
ht-degree: 0%

---


# Revisione dell&#39;ottimizzazione delle prestazioni

Anche se l’ottimizzazione delle prestazioni può provenire da molti aspetti, ci sono alcune raccomandazioni generali che dovrebbero essere prese in considerazione per la maggior parte degli scenari. Ciò include l’ottimizzazione della configurazione per gli elementi dell’infrastruttura, la configurazione back-end di Adobe Commerce e la pianificazione della scalabilità dell’architettura.

## Infrastruttura

Le sezioni seguenti descrivono le raccomandazioni per le ottimizzazioni dell’infrastruttura.

### Ricerche DNS

Ricerca DNS è il processo di ricerca dell&#39;indirizzo IP a cui appartiene il nome di dominio. Il browser deve attendere il completamento della ricerca DNS prima di poter scaricare qualsiasi cosa per ogni richiesta. La riduzione delle ricerche DNS è importante per migliorare i tempi di caricamento delle pagine complessive.

### Content delivery network (CDN)

Utilizza una rete CDN per ottimizzare le prestazioni di download delle risorse. Adobe Commerce utilizza Fwide. Se disponi di un’implementazione on-premise di Adobe Commerce, dovresti anche considerare l’aggiunta di un livello CDN.

### Latenza web

La posizione del centro dati influisce sulla latenza web per gli utenti front-end.

### Larghezza di banda della rete

Una larghezza di banda di rete sufficiente è uno dei requisiti chiave per lo scambio di dati tra nodi web, database, server di memorizzazione in cache/sessione e altri servizi.

Poiché Adobe Commerce sfrutta efficacemente la memorizzazione in cache per prestazioni elevate, il sistema può scambiare attivamente i dati con server di caching come Redis. Se Redis si trova su un server remoto, è necessario fornire un canale di rete sufficiente tra i nodi web e il server di caching per evitare i colli di bottiglia nelle operazioni di lettura/scrittura.

### Sistema operativo (OS)

Operating system configurations and optimizations are similar for Adobe Commerce when compared to other high-load web applications. As the number of concurrent connections handled by the server increases, the number of available sockets can become fully allocated.

### CPU dei nodi web

One CPU core can serve around 2-4 Adobe Commerce requests without cache effectively. Per determinare quanti nodi/core web sono necessari per elaborare tutte le richieste in arrivo senza metterle in coda, utilizza l’equazione:

```
N[Cores] = (N [Expected Requests] / 2) + N [Expected Cron Processes])
```

### PHP-FPM settings

Optimizing these settings depends on the performance test results for different projects.

- **ByteCode**—To get maximum speed out of Adobe Commerce on PHP 7, you must activate the `opcache` module and configure it properly.

- **APCU**—We recommend enabling the PHP APCu extension and configuring Composer to optimize for maximum performance. Questa estensione memorizza in cache le posizioni dei file per i file aperti, il che aumenta le prestazioni per le chiamate al server Commerce di Adobe, tra cui pagine, chiamate Ajax e endpoint.

- **Realpath_cacheconfiguration** - L&#39;ottimizzazione  `realpath_cache` consente ai processi PHP di memorizzare in cache i percorsi dei file invece di cercarli ogni volta che viene caricata una pagina.

### Web server

Only slight reconfiguration is needed to use nginx as a web server. Il server web nginx offre prestazioni migliori ed è facile da configurare utilizzando il file di configurazione di esempio di Adobe Commerce ([`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample)).

- Configurazione corretta di PHP-FPM con TCP

- Abilita HTTP/2 e Gzip

- Ottimizzare le connessioni dei processi di lavoro

### Database

This document does not provide in-depth MySQL tuning instructions because each store and environment is different, but we can make some general recommendations.

Il database di Adobe Commerce (nonché qualsiasi altro database) è sensibile alla quantità di memoria disponibile per la memorizzazione di dati e indici. To effectively leverage MySQL data indexation, the amount of memory available should be, at minimum, close to half the size of the data stored in the database.

Optimize the `innodb_buffer_pool_instances` setting to avoid issues with multiple threads attempting to access the same instance. The value of the `max_connections` parameter should correlate with the total number of PHP threads configured in the application server. Utilizza la formula seguente per calcolare il valore migliore per `innodb-thread-concurrency`:

```
innodb-thread-concurrency = 2 * (NumCPUs+NumDisks)
```

### Memorizzazione in cache delle sessioni

La memorizzazione in cache delle sessioni è un buon candidato per la configurazione di un&#39;istanza separata di Redis. La configurazione della memoria per questo tipo di cache dovrebbe considerare la strategia di abbandono del carrello del sito e quanto tempo una sessione dovrebbe aspettarsi di rimanere nella cache.

Redis should have enough memory allocated to hold all other caches in memory for optimal performance. La cache del blocco sarà il fattore chiave per determinare la quantità di memoria da configurare. La cache del blocco cresce in base al numero di pagine su un sito (numero di SKU x numero di visualizzazioni dello store).

### Page caching

We highly recommend using Varnish for full page cache on your Adobe Commerce store. The `PageCache` module is still present in the codebase, but it should be used for development purposes only.

Installa Varnish su un server separato davanti al livello web. Deve accettare tutte le richieste in arrivo e fornire copie della pagina memorizzate nella cache. Per consentire a Varnish di funzionare in modo efficace con le pagine protette, un proxy di terminazione SSL può essere posizionato davanti a Varnish. Nginx può essere utilizzato a questo scopo.

Anche se l’annullamento della validità della memoria cache della pagina intera di Varnish è efficace, si consiglia di allocare abbastanza memoria a Varnish per contenere le pagine più popolari in memoria.

### Code di messaggi

MQF (Message Queue Framework) è un sistema che consente a un modulo di pubblicare messaggi nelle code. Definisce anche i consumatori che ricevono i messaggi in modo asincrono. Adobe Commerce supporta RabbitMQ come broker di messaggistica, che fornisce una piattaforma scalabile per l’invio e la ricezione di messaggi.

### Test e monitoraggio delle prestazioni

Performance testing before each production release is always recommend to get an estimation of the capability of your ecommerce platform. Continuate a monitorare dopo il lancio e disponete di un piano di scalabilità e backup per gestire i tempi di picco.

>[!NOTE]
>
> Adobe Commerce on cloud infrastrucrure already applies all of the above infrastructure and architecture optimizations, except for the DNS lookup because it&#39;s out of scope.

### Ricerca

Elasticsearch is required as of Adobe Commerce version 2.4, but it’s also a best practice to enable it for versions prior to 2.4.

## Modelli operativi

Apart from the previoiusly mentioend common infrastructure optimization recommendations, there are also approaches to enhance the performance for specific business modes and scales. This document does not provide in-depth tuning instructions for all of them because each scenario is different, but we can provide a few high-level options for your reference.

### Architettura headless

Abbiamo una sezione separata dedicata al dettaglio di ciò che è [headless](../../architecture/headless/adobe-commerce.md) e di diverse opzioni. In summary, it separates the storefront layer from the platform itself. It is still the same backend, but Adobe Commerce no longer processes requests directly and instead only supports custom storefronts through the GraphQL API.

### Mantieni aggiornato Adobe Commerce

Adobe Commerce always has better performance when running the newest version. Even if it’s not possible to keep Adobe Commerce up-to-date after each new version is released, it’s still recommended to upgrade when Adobe Commerce introduces significant performance optimizations.

Ad esempio, nel 2020, Adobe ha rilasciato un&#39;ottimizzazione al livello Redis, risolvendo molte inefficienze, problemi di connessione e trasferimenti di dati non necessari tra Redis e Adobe Commerce. Le prestazioni complessive tra le 2.3 e le 2.4 sono giorno e notte e abbiamo visto miglioramenti significativi nel carrello, il pagamento, utenti simultanei, proprio a causa dell&#39;ottimizzazione Redis.

### Ottimizzare il modello dati

Molti problemi derivano da dati, inclusi modelli di dati errati, dati non strutturati correttamente e dati mancanti.

It looks fine if you&#39;re testing a few connections, but seen in production when the real traffic hits and this is where slowness comes in. It’s very important that systems integrators know how to design a data model (especially for product attributes), avoid adding unnecessary attributes, and keep mandatory attributes that affect business logic (such as pricing, stock availability, and search).

For those attributes that do not affect business logic but still need to be present on the storefront, combine them into a few attributes (for example, JSON format).

To optimize platform performance, if business logic is not required on the storefront from data or attributes taken from a PIM or an ERP, there is no need to add that attribute into Adobe Commerce.

### Progettazione per la scalabilità

Questo è importante per le aziende che gestiscono campagne e che devono affrontare spesso i momenti di punta. Affinché l&#39;architettura e la progettazione delle applicazioni siano facili da scalare, questo può aumentare le risorse durante i picchi e ridurle dopo.
