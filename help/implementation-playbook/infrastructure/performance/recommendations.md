---
title: Recommendations di ottimizzazione delle prestazioni
description: Ottimizza le prestazioni dell’implementazione Adobe Commerce seguendo questi consigli.
exl-id: c5d62e23-be43-4eea-afdb-bb1b156848f9
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Revisione dell&#39;ottimizzazione delle prestazioni

Anche se l’ottimizzazione delle prestazioni può provenire da molti aspetti, ci sono alcune raccomandazioni generali che dovrebbero essere prese in considerazione per la maggior parte degli scenari. Ciò include l&#39;ottimizzazione della configurazione per gli elementi dell&#39;infrastruttura, la configurazione back-end di Adobe Commerce e la pianificazione della scalabilità dell&#39;architettura.

## Infrastruttura

Le sezioni seguenti descrivono le raccomandazioni per le ottimizzazioni dell’infrastruttura.

### Ricerche DNS

Ricerca DNS è il processo di ricerca dell&#39;indirizzo IP a cui appartiene il nome di dominio. Il browser deve attendere il completamento della ricerca DNS prima di poter scaricare qualsiasi cosa per ogni richiesta. La riduzione delle ricerche DNS è importante per migliorare i tempi di caricamento delle pagine complessive.

### Rete per la distribuzione dei contenuti (CDN)

Utilizza una rete CDN per ottimizzare le prestazioni di download delle risorse. Adobe Commerce utilizza la funzione &quot;Grave&quot;. Se disponi di un’implementazione on-premise di Adobe Commerce, dovresti anche considerare l’aggiunta di un livello CDN.

### Latenza web

La posizione del centro dati influisce sulla latenza web per gli utenti front-end.

### Larghezza di banda della rete

Una larghezza di banda di rete sufficiente è uno dei requisiti chiave per lo scambio di dati tra nodi web, database, server di memorizzazione in cache/sessione e altri servizi.

Poiché Adobe Commerce sfrutta efficacemente la memorizzazione in cache per prestazioni elevate, il sistema può scambiare attivamente i dati con server di caching come Redis. Se Redis si trova su un server remoto, è necessario fornire un canale di rete sufficiente tra i nodi web e il server di caching per evitare i colli di bottiglia nelle operazioni di lettura/scrittura.

### Sistema operativo (OS)

Le configurazioni e le ottimizzazioni del sistema operativo sono simili per Adobe Commerce rispetto ad altre applicazioni web ad alto carico. Con l&#39;aumento del numero di connessioni simultanee gestite dal server, il numero di socket disponibili può essere completamente allocato.

### CPU dei nodi web

Un nucleo della CPU può servire circa 2-4 richieste Adobe Commerce senza cache in modo efficace. Per determinare quanti nodi/core web sono necessari per elaborare tutte le richieste in arrivo senza metterle in coda, utilizza l’equazione:

```
N[Cores] = (N [Expected Requests] / 2) + N [Expected Cron Processes])
```

### Impostazioni PHP-FPM

L’ottimizzazione di queste impostazioni dipende dai risultati dei test delle prestazioni per progetti diversi.

- **ByteCode**—Per ottenere la massima velocità da Adobe Commerce su PHP 7, è necessario attivare il `opcache` e configuralo correttamente.

- **APCU**- Si consiglia di abilitare l’estensione PHP APCu e di configurare Composer per ottimizzare le prestazioni al massimo. Questa estensione memorizza in cache le posizioni dei file per i file aperti, il che aumenta le prestazioni per le chiamate al server Adobe Commerce, incluse pagine, chiamate Ajax e endpoint.

- **Realpath_cacheconfiguration**—Ottimizzazione `realpath_cache` consente ai processi PHP di memorizzare in cache i percorsi dei file invece di cercarli ogni volta che si carica una pagina.

### Server web

È necessaria solo una piccola riconfigurazione per utilizzare l’nginx come server web. Il server web nginx offre prestazioni migliori ed è facile da configurare utilizzando il file di configurazione di esempio di Adobe Commerce ([`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample)).

- Configurazione corretta di PHP-FPM con TCP

- Abilita HTTP/2 e Gzip

- Ottimizzare le connessioni dei processi di lavoro

### Database

Questo documento non fornisce istruzioni dettagliate di ottimizzazione di MySQL perché ogni archivio e ambiente è diverso, ma possiamo formulare alcune raccomandazioni generali.

Il database di Adobe Commerce (così come qualsiasi altro database) è sensibile alla quantità di memoria disponibile per la memorizzazione di dati e indici. Per sfruttare efficacemente l&#39;indicizzazione dei dati MySQL, la quantità di memoria disponibile dovrebbe essere almeno pari alla metà della dimensione dei dati memorizzati nel database.

Ottimizza `innodb_buffer_pool_instances` impostazione per evitare problemi con più thread che tentano di accedere alla stessa istanza. Il valore del `max_connections` Il parametro deve essere correlato al numero totale di thread PHP configurati nel server dell&#39;applicazione. Utilizza la formula seguente per calcolare il valore migliore per `innodb-thread-concurrency`:

```
innodb-thread-concurrency = 2 * (NumCPUs+NumDisks)
```

### Memorizzazione in cache delle sessioni

La memorizzazione in cache delle sessioni è un buon candidato per la configurazione di un&#39;istanza separata di Redis. La configurazione della memoria per questo tipo di cache dovrebbe considerare la strategia di abbandono del carrello del sito e quanto tempo una sessione dovrebbe aspettarsi di rimanere nella cache.

Redis dovrebbe avere una memoria sufficiente allocata per contenere tutte le altre cache in memoria per ottenere prestazioni ottimali. La cache del blocco sarà il fattore chiave per determinare la quantità di memoria da configurare. La cache del blocco cresce in base al numero di pagine su un sito (numero di SKU x numero di visualizzazioni dello store).

### Memorizzazione in cache delle pagine

Consigliamo vivamente di utilizzare Varnish per la cache a pagina intera sul tuo negozio Adobe Commerce. La `PageCache` Il modulo è ancora presente nel codebase, ma deve essere utilizzato solo a scopo di sviluppo.

Installa Varnish su un server separato davanti al livello web. Deve accettare tutte le richieste in arrivo e fornire copie della pagina memorizzate nella cache. Per consentire a Varnish di funzionare in modo efficace con le pagine protette, un proxy di terminazione SSL può essere posizionato davanti a Varnish. Nginx può essere utilizzato a questo scopo.

Anche se l’annullamento della validità della memoria cache della pagina intera di Varnish è efficace, si consiglia di allocare abbastanza memoria a Varnish per contenere le pagine più popolari in memoria.

### Code di messaggi

MQF (Message Queue Framework) è un sistema che consente a un modulo di pubblicare messaggi nelle code. Definisce anche i consumatori che ricevono i messaggi in modo asincrono. Adobe Commerce supporta RabbitMQ come broker di messaggistica, che fornisce una piattaforma scalabile per l’invio e la ricezione di messaggi.

### Test e monitoraggio delle prestazioni

Prima di ogni versione di produzione, si consiglia sempre di eseguire un test delle prestazioni per ottenere una stima della funzionalità della piattaforma e-commerce. Continuate a monitorare dopo il lancio e disponete di un piano di scalabilità e backup per gestire i tempi di picco.

>[!NOTE]
>
> Adobe Commerce sull&#39;infrastruttura cloud applica già tutte le ottimizzazioni dell&#39;infrastruttura e dell&#39;architettura di cui sopra, ad eccezione della ricerca DNS perché è fuori ambito.

### Ricerca

A partire dalla versione 2.4 di Adobe Commerce è necessario un Elasticsearch, ma è anche consigliabile abilitarlo per le versioni precedenti alla versione 2.4.

## Modelli operativi

Oltre ai consigli di ottimizzazione dell&#39;infrastruttura comune precedentemente menzionati, esistono anche approcci per migliorare le prestazioni per modalità e scale aziendali specifiche. Questo documento non fornisce istruzioni di ottimizzazione approfondite per tutti gli scenari, poiché ogni scenario è diverso, ma possiamo fornire alcune opzioni di alto livello per il vostro riferimento.

### Architettura headless

Abbiamo una sezione separata dedicata al dettaglio di cosa [senza testa](../../architecture/headless/adobe-commerce.md) è e diverse opzioni. In sintesi, separa il livello della vetrina dalla piattaforma stessa. È ancora lo stesso backend, ma Adobe Commerce non elabora più le richieste direttamente e supporta solo vetrine personalizzate tramite l’API GraphQL.

### Mantieni aggiornato Adobe Commerce

Adobe Commerce offre sempre prestazioni migliori quando si esegue la versione più recente. Anche se non è possibile mantenere aggiornato Adobe Commerce dopo il rilascio di ogni nuova versione, si consiglia comunque di [aggiornamento](../../../upgrade/overview.md) quando Adobe Commerce introduce importanti ottimizzazioni delle prestazioni.

Ad esempio, nel 2020, Adobe ha rilasciato un&#39;ottimizzazione al livello Redis, risolvendo molte inefficienze, problemi di connessione e trasferimenti di dati non necessari tra Redis e Adobe Commerce. Le prestazioni complessive tra le 2.3 e le 2.4 sono giorno e notte e abbiamo visto miglioramenti significativi nel carrello, il pagamento, utenti simultanei, proprio a causa dell&#39;ottimizzazione Redis.

### Ottimizzare il modello dati

Molti problemi derivano da dati, inclusi modelli di dati errati, dati non strutturati correttamente e dati mancanti.

Va bene se stai testando alcune connessioni, ma visto in produzione quando il traffico reale colpisce ed è qui che arriva la lentezza. È molto importante che gli integratori di sistemi sappiano come progettare un modello dati (soprattutto per gli attributi del prodotto), evitino di aggiungere attributi non necessari e mantengano attributi obbligatori che influiscono sulla logica di business (come la determinazione dei prezzi, la disponibilità delle azioni e la ricerca).

Per gli attributi che non influiscono sulla logica di business ma che devono ancora essere presenti nella vetrina, combinali in alcuni attributi (ad esempio, il formato JSON).

Per ottimizzare le prestazioni della piattaforma, se sulla vetrina non è necessaria logica di business a partire da dati o attributi provenienti da un PIM o da un ERP, non è necessario aggiungere tale attributo in Adobe Commerce.

### Progettazione per la scalabilità

Questo è importante per le aziende che gestiscono campagne e che devono affrontare spesso i momenti di punta. Affinché l&#39;architettura e la progettazione delle applicazioni siano facili da scalare, questo può aumentare le risorse durante i picchi e ridurle dopo.
