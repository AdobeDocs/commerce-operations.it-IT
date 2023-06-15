---
title: Recommendations software
description: Rivedi un elenco di software consigliati relativi alle prestazioni ottimali di Adobe Commerce e delle distribuzioni di Magento Open Source.
feature: Best Practices, Install
exl-id: b091a733-7655-4e91-a988-93271872c5d5
source-git-commit: 012cba58b336b032b1c911539008c1fb961c2e07
workflow-type: tm+mt
source-wordcount: '1415'
ht-degree: 0%

---

# Consigli software

È necessario il seguente software per le istanze di produzione di [!DNL Commerce]:

* [PHP](../installation/system-requirements.md)
* Nginx e [PHP-FPM](https://php-fpm.org/)
* [[!DNL MySQL]](../installation/prerequisites/database/mysql.md)
* [[!DNL Elasticsearch] o OpenSearch](../installation/prerequisites/search-engine/overview.md)

Per le distribuzioni su più server o per gli esercenti che pianificano la scalabilità della propria attività, consigliamo quanto segue:

* [[!DNL Varnish] cache](../configuration/cache/config-varnish.md)
* [Redis](../configuration/cache/redis-session.md) per sessioni (da 2.0.6+)
* Un’istanza Redis separata come [cache predefinita](../configuration/cache/redis-pg-cache.md) (non utilizzare questa istanza per la cache delle pagine)

Consulta [requisiti di sistema](../installation/system-requirements.md) per informazioni sulle versioni supportate di ciascun tipo di software.

## Sistema operativo

Le configurazioni e le ottimizzazioni del sistema operativo sono simili per [!DNL Commerce] rispetto ad altre applicazioni web ad alto carico. Con l&#39;aumento del numero di connessioni simultanee gestite dal server, il numero di socket disponibili può essere completamente allocato. Il kernel Linux supporta un meccanismo per &quot;riutilizzare&quot; le connessioni TCP. Per attivare questo meccanismo, impostate il seguente valore in `/etc/sysctl.conf`:

>[!INFO]
>
>L&#39;attivazione di net.ipv4.tcp_tw_reuse non ha alcun effetto sulle connessioni in ingresso.

```text
net.ipv4.tcp_tw_reuse = 1
```

Il parametro kernel `net.core.somaxconn` controlla il numero massimo di socket aperti in attesa di connessioni. Questo valore può essere aumentato in modo sicuro a 1024, ma dovrebbe essere correlato alla capacità del server di gestire tale quantità. Per abilitare questo parametro del kernel, impostate il seguente valore in `/etc/sysctl.conf`:

```text
net.core.somaxconn = 1024
```

## PHP

Il Magento supporta pienamente PHP 7.3 e 7.4. Ci sono diversi fattori da tenere in considerazione quando si configura PHP per ottenere la massima velocità ed efficienza nell’elaborazione delle richieste.

### Estensioni PHP

È consigliabile limitare l&#39;elenco delle estensioni PHP attive a quelle necessarie per [!DNL Commerce] funzionalità.

Magento Open Source e Adobe Commerce:

* ext-bcmath
* ext-ctype
* ext-curl
* ext-dom
* ext-fileinfo
* int-gd
* ext-hash
* ext-iconv
* int-est
* ext-json
* ext-libxml
* ext-mbstring
* ext-openssl
* pcre esterno
* ext-pdo_mysql
* ext-simplexml
* ext-soap
* socket di testo
* int-sodio
* ext-tokenizer
* ext-xmlwriter
* ext-xsl
* ext-zip
* lib-libxml
* lib-openssl

Inoltre, Adobe Commerce richiede:

* ext-bcmath
* ext-ctype
* ext-curl
* ext-dom
* ext-fileinfo
* int-gd
* ext-hash
* ext-iconv
* int-est
* ext-json
* ext-libxml
* ext-mbstring
* ext-openssl
* pcre esterno
* ext-pdo_mysql
* ext-simplexml
* ext-soap
* socket di testo
* int-sodio
* ext-spl
* ext-tokenizer
* ext-xmlwriter
* ext-xsl
* ext-zip
* lib-libxml
* lib-openssl

L&#39;aggiunta di più estensioni aumenta i tempi di caricamento della libreria.

>[!INFO]
>
>`php-mcrypt` è stato rimosso da PHP 7.2 e sostituito con il [`sodium` libreria](https://www.php.net/manual/en/book.sodium.php). Assicurati che [sodio](https://www.php.net/manual/en/sodium.installation.php) è abilitato correttamente durante l&#39;aggiornamento di PHP.

>[!INFO]
>
>La presenza di eventuali estensioni di profiling e debug può influire negativamente sul tempo di risposta delle pagine. Ad esempio, un modulo xDebug attivo senza alcuna sessione di debug può aumentare il tempo di risposta della pagina fino al 30%.

### Impostazioni PHP

Garantire la corretta esecuzione di tutte le [!DNL Commerce] istanze senza scaricare dati o codice su disco, impostare il limite di memoria come segue:

```text
memory_limit=1G
```

Per il debug, aumentare questo valore a 2G.

#### Configurazione Realpath_cache

Per migliorare [!DNL Commerce] prestazioni, aggiungi o aggiorna i seguenti elementi consigliati `realpath_cache` impostazioni in `php.ini` file. Questa configurazione consente ai processi PHP di memorizzare nella cache i percorsi dei file invece di cercarli ogni volta che viene caricata una pagina. Consulta [Ottimizzazione delle prestazioni](https://www.php.net/manual/en/ini.core.php) nella documentazione PHP.

```text
realpath_cache_size=10M
realpath_cache_ttl=7200
```

#### ByteCode

Per ottenere la velocità massima da [!DNL Commerce] su PHP 7, è necessario attivare il modulo OpCache e configurarlo correttamente. Queste impostazioni sono consigliate per il modulo:

```text
opcache.memory_consumption=512
opcache.max_accelerated_files=60000
opcache.consistency_checks=0
opcache.validate_timestamps=0
opcache.enable_cli=1
```

Quando ottimizzi l’allocazione di memoria per opcache, tieni conto delle dimensioni della base di codice del Magento e di tutte le estensioni. Il team delle prestazioni del Magento utilizza i valori dell’esempio precedente per il test, perché fornisce spazio sufficiente in opcache per il numero medio di estensioni installate.

Se la memoria del computer è insufficiente e non sono installate molte estensioni o personalizzazioni, utilizzare le impostazioni seguenti per ottenere un risultato simile:

```text
opcache.memory_consumption=64
opcache.max_accelerated_files=60000
```

#### APCU

È consigliabile abilitare [Estensione PHP APCu](https://getcomposer.org/doc/articles/autoloader-optimization.md#optimization-level-2-b-apcu-cache) e [configurazione `composer` per supportarlo](../performance/deployment-flow.md#preprocess-dependency-injection-instructions) per ottimizzare le prestazioni. Questa estensione memorizza nella cache i percorsi dei file aperti, migliorando le prestazioni per [!DNL Commerce] chiamate al server, incluse pagine, chiamate Ajax ed endpoint.

Modifica il `apcu.ini` file per includere quanto segue:

```text
extension=apcu.so
[apcu]
apc.enabled = 1
```

## Server web

Magento supporta completamente i server web Nginx e Apache. [!DNL Commerce] fornisce esempi di file di configurazione consigliati in  `<magento_home>/nginx.conf.sample` (Nginx) e  `<magento_home>.htaccess.sample` (Apache).  L&#39;esempio di Nginx contiene impostazioni per prestazioni migliori ed è progettato in modo che sia richiesta una piccola riconfigurazione. Alcune delle best practice di configurazione principali definite nel file di esempio includono:

* Impostazioni per la memorizzazione nella cache del contenuto statico in un browser
* Impostazioni della memoria e del tempo di esecuzione per PHP
* Impostazioni di compressione del contenuto

Devi anche configurare il numero di thread per l’elaborazione delle richieste di input, come elencato di seguito:

| Server web | Nome attributo | Posizione | Informazioni correlate |
|--- | --- | --- | ---|
| Nginx | `worker_connections` | `/etc/nginx/nginx.conf` (Debian) | [Ottimizzazione di NGINX per le prestazioni](https://www.nginx.com/blog/tuning-nginx/) |
| Apache 2.2 | `MaxClients` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Ottimizzazione delle prestazioni di Apache](https://httpd.apache.org/docs/2.2/misc/perf-tuning.html) |
| Apache 2.4 | `MaxRequestWorkers` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Direttive comuni Apache MPM](https://httpd.apache.org/docs/2.4/mod/mpm_common.html#maxrequestworkers) |

## [!DNL MySQL]

Questo documento non fornisce informazioni approfondite [!DNL MySQL] istruzioni di ottimizzazione perché ogni negozio e ambiente è diverso, ma possiamo fare alcuni consigli generali.

Ci sono stati molti miglioramenti a [!DNL MySQL] 5.7.9 Siamo certi che [!DNL MySQL] viene distribuito con buone impostazioni predefinite. Le impostazioni più critiche sono:

| Parametro | Predefinito | Descrizione |
|--- | --- | ---|
| `innodb_buffer_pool_instances` | 8 | Il valore predefinito è impostato su 8 per evitare problemi con più thread che tentano di accedere alla stessa istanza. |
| `innodb_buffer_pool_size` | 128MB | In combinazione con le istanze di pool multiple descritte in precedenza, ciò significa un&#39;allocazione di memoria predefinita di 1024 MB. La dimensione totale viene divisa tra tutti i pool di buffer. Per una maggiore efficienza, specificare una combinazione di `innodb_buffer_pool_instances` e `innodb_buffer_pool_size` in modo che ogni istanza del pool di buffer sia di almeno 1 GB. |
| `max_connections` | 150 | Il valore della proprietà `max_connections` Il parametro deve essere correlato al numero totale di thread PHP configurati nel server applicazioni. Una raccomandazione generale sarebbe di 300 per un ambiente di piccole dimensioni e di 1000 per un ambiente di medie dimensioni. |
| `innodb_thread_concurrency` | 0 | Il valore migliore per questa configurazione deve essere calcolato con la formula: `innodb_thread_concurrency = 2 * (NumCPUs + NumDisks)` |

## [!DNL Varnish]

Il Magento consiglia vivamente di utilizzare [!DNL Varnish] come server di cache a pagina intera per lo store. Il modulo PageCache è ancora presente nel codebase, ma deve essere utilizzato solo a scopo di sviluppo. Non deve essere usato insieme a o al posto di [!DNL Varnish].

Installa [!DNL Varnish] su un server separato di fronte al livello web. Deve accettare tutte le richieste in arrivo e fornire copie delle pagine memorizzate nella cache. Per consentire [!DNL Varnish] per funzionare in modo efficace con le pagine protette, è possibile inserire un proxy di terminazione SSL davanti a [!DNL Varnish]. Nginx può essere utilizzato per questo scopo.

[!DNL Commerce] distribuisce un file di configurazione di esempio per [!DNL Varnish] (versioni 4 e 5) che contiene tutte le impostazioni consigliate per le prestazioni. Tra questi, i più critici in termini di prestazioni sono:

* **Verifica stato back-end** polling di [!DNL Commerce] per determinare se risponde in modo tempestivo.
* **Modalità di tolleranza** consente di istruire [!DNL Varnish] per mantenere un oggetto nella cache oltre il periodo Time to Live (TTL) e distribuire questo contenuto non aggiornato se [!DNL Commerce] non è integro o se il contenuto fresco non è ancora stato recuperato.
* **Modalità Saint** blacklist non integra [!DNL Commerce] per un periodo di tempo configurabile. Di conseguenza, i backend non integri non possono distribuire il traffico quando si utilizza [!DNL Varnish] come load balancer.

Consulta [Avanzate [!DNL Varnish] configurazione](../configuration/cache/config-varnish-advanced.md) per ulteriori informazioni sull’implementazione di queste funzioni.

### Ottimizzare le prestazioni delle risorse

In generale, consigliamo di memorizzare le risorse (immagini, JS, CSS, ecc.) su una rete CDN per prestazioni ottimali.

Se il sito non richiede l&#39;implementazione di un numero elevato di impostazioni internazionali e i server si trovano nella stessa area della maggior parte dei clienti, è possibile ottenere significativi miglioramenti delle prestazioni a un costo inferiore archiviando le risorse in [!DNL Varnish] invece di utilizzare una rete CDN.

Per memorizzare le risorse in [!DNL Varnish], aggiungi le seguenti voci VCL nel tuo `default.vcl` file generato da [!DNL Commerce] per [!DNL Varnish] 5.

Alla fine del `if` istruzione per le richieste PURGE in `vcl_recv` subroutine, aggiungere:

```javascript
# static files are cacheable. remove SSL flag and cookie

if (req.url ~ "^/(pub/)?(media|static)/.*\.(ico|html|css|js|jpg|jpeg|png|gif|tiff|bmp|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)$") {
  unset req.http.Https;
  unset req.http./* {{ ssl_offloaded_header }} */;
  unset req.http.Cookie;
}
```

In `vcl_backend_response` subroutine, cerca `if` istruzione che annulla l’impostazione del cookie per `GET` o `HEAD` richieste.
Il valore aggiornato `if` Il blocco deve essere simile al seguente:

```javascript
# validate if we need to cache it and prevent from setting cookie
# images, css and js are cacheable by default so we have to remove cookie also

if (beresp.ttl > 0s && (bereq.method == "GET" || bereq.method == "HEAD")) {
  unset beresp.http.set-cookie;
if (bereq.url !~ "\.(ico|css|js|jpg|jpeg|png|gif|tiff|bmp|gz|tgz|bz2|tbz|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)(\?|$)") {
  set beresp.http.Pragma = "no-cache";
  set beresp.http.Expires = "-1";
  set beresp.http.Cache-Control = "no-store, no-cache, must-revalidate, max-age=0";
  }
}
```

Riavvia il [!DNL Varnish] server per svuotare le risorse memorizzate nella cache ogni volta che aggiorni il sito o distribuisci/aggiorni le risorse.

## Memorizzazione in cache e server di sessione

Magento fornisce una serie di opzioni per memorizzare la cache e i dati di sessione, tra cui Redis, Memcache, file system e database. Alcune di queste opzioni sono discusse di seguito.

### Configurazione di un singolo nodo web

Se prevedi di gestire tutto il traffico con un solo nodo web, non avrebbe senso inserire la cache su un server Redis remoto. Utilizzare invece il file system o un server Redis locale. Se si desidera utilizzare il file system, inserire le cartelle della cache in un volume montato su un file system RAM. Se desideri utilizzare un server Redis locale, ti consigliamo vivamente di configurarlo in modo che utilizzi i socket per le connessioni dirette, anziché scambiare dati tramite HTTP.

### Configurazione di più nodi web

Per la configurazione di più nodi web, Redis è l’opzione migliore. Perché [!DNL Commerce] memorizza in cache attivamente molti dati per migliorare le prestazioni, presta attenzione al tuo canale di rete tra i nodi web e il server Redis. Non vuoi che il canale diventi un collo di bottiglia per l’elaborazione delle richieste.

>[!INFO]
>
>Se devi gestire centinaia e migliaia di richieste simultanee, potresti aver bisogno di un canale fino a 1 Gbit (o anche più ampio) per il server Redis.
