---
title: Raccomandazioni per l’ottimizzazione delle prestazioni
description: Segui queste raccomandazioni per ottimizzare le prestazioni dell’implementazione di Adobe Commerce.
exl-id: c5d62e23-be43-4eea-afdb-bb1b156848f9
feature: Cloud
topic: Performance
source-git-commit: 8b09d734d8ac4490cd88af5673acd0a41b6cdf66
workflow-type: tm+mt
source-wordcount: '1282'
ht-degree: 0%

---


# Valutazione dell’ottimizzazione delle prestazioni

Anche se l’ottimizzazione delle prestazioni può provenire da molti aspetti, ci sono alcune raccomandazioni generali che dovrebbero essere prese in considerazione per la maggior parte degli scenari. I consigli generali includono l’ottimizzazione della configurazione per gli elementi dell’infrastruttura, la configurazione back-end di Adobe Commerce e la pianificazione della scalabilità dell’architettura.

>[!TIP]
>
>Per ulteriori informazioni sull&#39;ottimizzazione delle prestazioni, vedere la [_Guida alle best practice per le prestazioni_](../../../performance/overview.md).

## Infrastruttura

Le sezioni seguenti descrivono i consigli per l’ottimizzazione dell’infrastruttura.

### Ricerche DNS

La ricerca DNS è il processo di ricerca dell’indirizzo IP a cui appartiene il nome di dominio. Il browser deve attendere il completamento della ricerca DNS prima di poter scaricare qualsiasi elemento per ogni richiesta. La riduzione delle ricerche DNS è importante per migliorare i tempi complessivi di caricamento delle pagine.

### Rete per la distribuzione dei contenuti (CDN)

Utilizza una rete CDN per ottimizzare le prestazioni di download delle risorse. Adobe Commerce utilizza Fastly. Se hai implementato Adobe Commerce on-premise, dovresti anche considerare l’aggiunta di un livello CDN.

### Latenza web

La posizione del datacenter influisce sulla latenza web per gli utenti front-end.

### Larghezza di banda di rete

Una larghezza di banda di rete sufficiente è uno dei requisiti chiave per lo scambio di dati tra nodi web, database, server di caching/sessione e altri servizi.

Poiché Adobe Commerce utilizza la memorizzazione nella cache per prestazioni elevate, il sistema può scambiare attivamente i dati con server di memorizzazione nella cache come Redis. Se Redis è installato su un server remoto, è necessario fornire un canale di rete sufficiente tra i nodi web e il server di caching per evitare colli di bottiglia nelle operazioni di lettura/scrittura.

### Sistema operativo (OS)

Le configurazioni e le ottimizzazioni dei sistemi operativi sono simili per Adobe Commerce rispetto ad altre applicazioni web ad alto carico. Con l&#39;aumento del numero di connessioni simultanee gestite dal server, il numero di socket disponibili può essere completamente allocato.

### CPU dei nodi web

Un core CPU può soddisfare circa 2-4 richieste Adobe Commerce senza cache in modo efficace. Per determinare il numero di nodi/core Web necessari per elaborare tutte le richieste in ingresso senza metterle in coda, utilizza l’equazione:

```
N[Cores] = (N [Expected Requests] / 2) + N [Expected Cron Processes])
```

### Impostazioni PHP-FPM

L’ottimizzazione di queste impostazioni dipende dai risultati del test delle prestazioni per i diversi progetti.

- **ByteCode** - Per ottenere la massima velocità da Adobe Commerce su PHP 7, è necessario attivare il modulo `opcache` e configurarlo correttamente.

- **APCU**. L&#39;Adobe consiglia di abilitare l&#39;estensione PHP APCu e di configurare Composer per ottimizzare le prestazioni. Questa estensione memorizza nella cache i percorsi dei file aperti, migliorando le prestazioni per le chiamate al server Adobe Commerce, incluse le pagine, le chiamate AJAX e gli endpoint.

- **Realpath_cacheconfiguration**: l&#39;ottimizzazione di `realpath_cache` consente ai processi PHP di memorizzare nella cache i percorsi dei file anziché cercarli ogni volta che viene caricata una pagina.

### Server web

Per utilizzare nginx come server web è necessaria solo una leggera riconfigurazione. Il server Web Nginx offre prestazioni migliori ed è facile da configurare utilizzando il file di configurazione di esempio di Adobe Commerce ([`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample)).

- Configurare PHP-FPM con TCP in modo corretto

- Abilita HTTP/2 e Gzip

- Ottimizza connessioni lavoratore

### Database

Questo documento non fornisce istruzioni di tuning MySQL approfondite perché ogni archivio e ambiente è diverso, ma Adobe può fornire consigli generali.

Il database di Adobe Commerce (e qualsiasi altro database) è sensibile alla quantità di memoria disponibile per l’archiviazione di dati e indici. Per utilizzare in modo efficace l&#39;indicizzazione dei dati MySQL, la quantità di memoria disponibile deve essere, come minimo, quasi la metà della dimensione dei dati memorizzati nel database.

Ottimizzare l&#39;impostazione `innodb_buffer_pool_instances` per evitare problemi con più thread che tentano di accedere alla stessa istanza. Il valore del parametro `max_connections` deve essere correlato al numero totale di thread PHP configurati nel server applicazioni. Utilizzare la formula seguente per calcolare il valore ottimale per `innodb-thread-concurrency`:

```
innodb-thread-concurrency = 2 * (NumCPUs+NumDisks)
```

### Memorizzazione in cache della sessione

Il caching delle sessioni è un buon candidato per la configurazione per un’istanza separata di Redis. La configurazione della memoria per questo tipo di cache deve tenere conto della strategia di abbandono del carrello del sito e di quanto tempo una sessione deve aspettarsi di rimanere nella cache.

I Redis devono avere una quantità di memoria sufficiente per contenere tutte le altre cache in memoria per ottenere prestazioni ottimali. La cache di blocco è il fattore chiave per determinare la quantità di memoria da configurare. La cache dei blocchi cresce in relazione al numero di pagine su un sito (numero di SKU x numero di visualizzazioni dello store).

### Memorizzazione in cache delle pagine

L’Adobe consiglia vivamente di utilizzare Vernice per la cache a pagina intera nel tuo store Adobe Commerce. Il modulo `PageCache` è ancora presente nel codebase, ma deve essere utilizzato solo a scopo di sviluppo.

Installa Vernice su un server separato di fronte al livello web. Deve accettare tutte le richieste in arrivo e fornire copie delle pagine memorizzate nella cache. Per consentire a Varish di funzionare in modo efficace con pagine protette, è possibile inserire un proxy di terminazione SSL davanti a Varnish. Nginx può essere utilizzato per questo scopo.

Mentre l&#39;annullamento della validità della memoria cache a pagina intera di Varnish è efficace, Adobe consiglia di allocare una quantità di memoria sufficiente per mantenere le pagine più popolari in memoria.

### Code di messaggi

MQF (Message Queue Framework) è un sistema che consente a un modulo di pubblicare messaggi nelle code. Definisce inoltre i consumatori che ricevono i messaggi in modo asincrono. Adobe Commerce supporta [!DNL RabbitMQ] come broker di messaggistica, che fornisce una piattaforma scalabile per l&#39;invio e la ricezione di messaggi.

### Test e monitoraggio delle prestazioni

Per ottenere una stima delle funzionalità della piattaforma e-commerce, è sempre consigliabile eseguire un test delle prestazioni prima di ogni versione di produzione. Monitoraggio continuo dopo l&#39;avvio e pianificazione di scalabilità e backup per gestire i periodi di picco.

>[!NOTE]
>
> Adobe Commerce sull’infrastruttura cloud applica già le ottimizzazioni dell’infrastruttura e dell’architettura di cui sopra, ad eccezione della ricerca DNS perché fuori ambito.

### Ricerca {#search-heading}

Elasticsearch (o OpenSearch) è obbligatorio a partire dalla versione 2.4 di Adobe Commerce, ma è anche una best practice abilitarlo per le versioni precedenti alla 2.4.

## Modelli operativi

Oltre alle raccomandazioni comuni per l&#39;ottimizzazione dell&#39;infrastruttura precedentemente menzionate, esistono anche approcci per migliorare le prestazioni per modalità e scale di business specifiche. Questo documento non fornisce istruzioni di ottimizzazione approfondite per tutti gli scenari, in quanto ogni scenario è diverso, ma Adobe può fornire alcune opzioni di alto livello per riferimento.

### Architettura headless

Esiste una sezione separata dedicata a [headless](../../architecture/enterprise-blueprint.md#headless-storefront). In sintesi, separa il livello vetrina dalla piattaforma stessa. È ancora lo stesso backend, ma Adobe Commerce non elabora più le richieste direttamente e supporta solo storefront personalizzati tramite l’API GraphQL.

### Mantieni Adobe Commerce aggiornato

Adobe Commerce offre sempre prestazioni migliori quando si esegue la versione più recente. Anche se non è possibile mantenere Adobe Commerce aggiornato dopo il rilascio di ogni nuova versione, si consiglia comunque di [eseguire l&#39;aggiornamento](../../../upgrade/overview.md) quando Adobe Commerce introduce significative ottimizzazioni delle prestazioni.

Ad esempio, nel 2020, Adobe ha rilasciato un’ottimizzazione per il livello Redis, risolvendo molte inefficienze, problemi di connessione e trasferimenti di dati non necessari tra Redis e Adobe Commerce. Le prestazioni complessive tra 2.3 e 2.4 sono notturne e diurne e hanno fornito miglioramenti significativi in termini di carrello, pagamento e utenti simultanei, grazie all’ottimizzazione Redis.

### Ottimizza modello dati

Molti problemi derivano dai dati, inclusi modelli di dati non validi, dati non strutturati correttamente e dati senza indice.

Sembra che vada bene se stai testando alcune connessioni, ma dopo la distribuzione in produzione potresti notare un grave deterioramento delle prestazioni. È importante che gli integratori di sistemi sappiano come progettare un modello di dati (in particolare per gli attributi del prodotto), evitare di aggiungere attributi non necessari e mantenere attributi obbligatori che influiscono sulla logica di business (come prezzi, disponibilità di stock e ricerca).

Per gli attributi che non influiscono sulla logica di business ma che devono essere ancora presenti nella vetrina, combinali in alcuni attributi (ad esempio, il formato JSON).

Per ottimizzare le prestazioni della piattaforma, se la logica di business non è richiesta nella vetrina da dati o attributi rilevati da un PIM o un ERP, non è necessario aggiungere tale attributo in Adobe Commerce.

### Progettazione per la scalabilità

La scalabilità è importante per le aziende che eseguono campagne e che si trovano spesso ad affrontare i picchi di traffico. Un&#39;architettura scalabile e una progettazione delle applicazioni possono aumentare le risorse durante i periodi di picco e ridurle successivamente.
