---
title: Recommendations software
description: Rivedi un elenco di software consigliati relativi alle prestazioni ottimali delle distribuzioni Adobe Commerce e Magenti Open Source.
source-git-commit: 8572cc8702d6f7e9c40b64110a9ba18aa5784f44
workflow-type: tm+mt
source-wordcount: '1415'
ht-degree: 0%

---


# Raccomandazioni software

È necessario il software seguente per le istanze di produzione di [!DNL Commerce]:

* [PHP](../installation/system-requirements.md)
* Nginx e [PHP-FPM](https://php-fpm.org/)
* [[!DNL MySQL]](../installation/prerequisites/database/mysql.md)
* [[!DNL Elasticsearch] o OpenSearch](../installation/prerequisites/search-engine/overview.md)

Per le implementazioni multi-server o per i commercianti che pianificano l’scalabilità della propria attività, si consiglia di:

* [[!DNL Varnish] cache](../configuration/cache/config-varnish.md)
* [Redis](../configuration/cache/redis-session.md) per le sessioni (da 2.0.6+)
* Un&#39;istanza Redis separata come tua [cache predefinita](../configuration/cache/redis-pg-cache.md) (non utilizzare questa istanza per la cache della pagina)

Vedi [requisiti di sistema](../installation/system-requirements.md) per informazioni sulle versioni supportate di ciascun tipo di software.

## Sistema operativo

Le configurazioni e le ottimizzazioni del sistema operativo sono simili per [!DNL Commerce] rispetto ad altre applicazioni web ad alto carico. Con l&#39;aumento del numero di connessioni simultanee gestite dal server, il numero di socket disponibili può essere completamente allocato. Il kernel Linux supporta un meccanismo per &quot;riutilizzare&quot; le connessioni TCP. Per abilitare questo meccanismo, imposta il seguente valore in `/etc/sysctl.conf`:

>[!INFO]
>
>L&#39;abilitazione di net.ipv4.tcp_tw_riutilizzo non ha alcun effetto sulle connessioni in ingresso.

```text
net.ipv4.tcp_tw_reuse = 1
```

Parametro del kernel `net.core.somaxconn` controlla il numero massimo di prese aperte in attesa di connessioni. Questo valore può essere aumentato in modo sicuro a 1024, ma dovrebbe essere correlato alla capacità del server di gestire questa quantità. Per abilitare questo parametro del kernel, imposta il seguente valore in `/etc/sysctl.conf`:

```text
net.core.somaxconn = 1024
```

## PHP

Il Magento supporta completamente PHP 7.3 e 7.4. Ci sono diversi fattori da tenere in considerazione quando si configura PHP per ottenere la massima velocità ed efficienza nell&#39;elaborazione delle richieste.

### Estensioni PHP

È consigliabile limitare l’elenco delle estensioni PHP attive a quelle necessarie per [!DNL Commerce] funzionalità.

Magento Open Source e Adobe Commerce:

* ext-bcmath
* ext-ctype
* curl di testo
* dom
* ext-fileinfo
* ext-gd
* hash di testo
* ext-iconv
* ext-intl
* ext-json
* ext-libxml
* ext-mbstring
* ext-openssl
* ext-pcre
* ext-pdo_mysql
* ext-simplexml
* ext-soap
* socket di testo
* ext-sodico
* ext-tokenizer
* ext-xmlwriter
* ext-xsl
* zip di testo
* lib-libxml
* lib-openssl

Inoltre, Adobe Commerce richiede:

* ext-bcmath
* ext-ctype
* curl di testo
* dom
* ext-fileinfo
* ext-gd
* hash di testo
* ext-iconv
* ext-intl
* ext-json
* ext-libxml
* ext-mbstring
* ext-openssl
* ext-pcre
* ext-pdo_mysql
* ext-simplexml
* ext-soap
* socket di testo
* ext-sodico
* ext-spl
* ext-tokenizer
* ext-xmlwriter
* ext-xsl
* zip di testo
* lib-libxml
* lib-openssl

L&#39;aggiunta di più estensioni aumenta i tempi di caricamento della libreria.

>[!INFO]
>
>`php-mcrypt` è stato rimosso da PHP 7.2 e sostituito con [`sodium` libreria](https://www.php.net/manual/en/book.sodium.php). Assicurati che [sodio](https://www.php.net/manual/en/sodium.installation.php) è abilitato correttamente durante l&#39;aggiornamento di PHP.

>[!INFO]
>
>La presenza di eventuali estensioni di profiling e debug può influire negativamente sul tempo di risposta delle pagine. Ad esempio, un modulo xDebug attivo senza alcuna sessione di debug può aumentare il tempo di risposta della pagina fino al 30%.

### Impostazioni PHP

Garantire il successo dell&#39;esecuzione di tutti [!DNL Commerce] istanze senza scaricare dati o codice su disco, impostare il limite di memoria come segue:

```text
memory_limit=1G
```

Per il debug, aumenta questo valore a 2G.

#### Configurazione di Realpath_cache

Per migliorare [!DNL Commerce] prestazioni, aggiungere o aggiornare quanto segue consigliato `realpath_cache` nelle impostazioni `php.ini` file. Questa configurazione consente ai processi PHP di memorizzare in cache i percorsi dei file invece di cercarli ogni volta che una pagina viene caricata. Vedi [Ottimizzazione delle prestazioni](https://www.php.net/manual/en/ini.core.php) nella documentazione PHP.

```text
realpath_cache_size=10M
realpath_cache_ttl=7200
```

#### ByteCode

Per ottenere la massima velocità [!DNL Commerce] su PHP 7, è necessario attivare il modulo OpCache e configurarlo correttamente. Queste impostazioni sono consigliate per il modulo:

```text
opcache.memory_consumption=512
opcache.max_accelerated_files=60000
opcache.consistency_checks=0
opcache.validate_timestamps=0
opcache.enable_cli=1
```

Quando ottimizza l’allocazione della memoria per opcache, prendi in considerazione le dimensioni della base del codice del Magento e tutte le tue estensioni. Il team delle prestazioni del Magento utilizza i valori nell&#39;esempio precedente per il test, perché fornisce spazio sufficiente in opcache per il numero medio di estensioni installate.

Se si dispone di una macchina a memoria insufficiente e non sono installate molte estensioni o personalizzazioni, utilizzare le seguenti impostazioni per ottenere un risultato simile:

```text
opcache.memory_consumption=64
opcache.max_accelerated_files=60000
```

#### APCU

Si consiglia di abilitare [Estensione PHP APCu](https://getcomposer.org/doc/articles/autoloader-optimization.md#optimization-level-2-b-apcu-cache) e [configurazione `composer` per sostenerlo](../performance/deployment-flow.md#preprocess-dependency-injection-instructions) per ottimizzare le massime prestazioni. Questa estensione memorizza in cache le posizioni dei file per i file aperti, il che aumenta le prestazioni per [!DNL Commerce] chiamate al server che includono pagine, chiamate Ajax e endpoint.

Modifica il `apcu.ini` per includere quanto segue:

```text
extension=apcu.so
[apcu]
apc.enabled = 1
```

## Server web

Il Magento supporta completamente i server web Nginx e Apache. [!DNL Commerce] fornisce file di configurazione consigliati di esempio in  `<magento_home>/nginx.conf.sample` e  `<magento_home>.htaccess.sample` (Apache) file.  L&#39;esempio Nginx contiene le impostazioni per migliorare le prestazioni ed è progettato in modo da richiedere una piccola riconfigurazione. Alcune delle best practice di configurazione principali definite nel file di esempio includono:

* Impostazioni per la memorizzazione in cache di contenuto statico in un browser
* Impostazioni della memoria e dei tempi di esecuzione per PHP
* Impostazioni di compressione del contenuto

È inoltre necessario configurare il numero di thread per l’elaborazione della richiesta di input, come illustrato di seguito:

| Server web | Nome attributo | Posizione | Informazioni correlate |
|--- | --- | --- | ---|
| Nginx | `worker_connections` | `/etc/nginx/nginx.conf` (Debian) | [Ottimizzazione di NGINX per le prestazioni](https://www.nginx.com/blog/tuning-nginx/) |
| Apache 2.2 | `MaxClients` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Ottimizzazione delle prestazioni di Apache](https://httpd.apache.org/docs/2.2/misc/perf-tuning.html) |
| Apache 2.4 | `MaxRequestWorkers` | `/etc/httpd/conf/httpd.conf` (CentOS) | [Direttive comuni Apache MPM](https://httpd.apache.org/docs/2.4/mod/mpm_common.html#maxrequestworkers) |

## [!DNL MySQL]

Questo documento non fornisce informazioni approfondite [!DNL MySQL] istruzioni di ottimizzazione perché ogni negozio e ambiente è diverso, ma possiamo formulare alcuni consigli generali.

Sono stati apportati numerosi miglioramenti [!DNL MySQL] 5.7.9 Confidiamo che [!DNL MySQL] è distribuito con impostazioni predefinite corrette. Le impostazioni più importanti sono:

| Parametro | Predefinito | Descrizione |
|--- | --- | ---|
| `innodb_buffer_pool_instances` | 8 | Il valore predefinito è impostato su 8 per evitare problemi con più thread che tentano di accedere alla stessa istanza. |
| `innodb_buffer_pool_size` | 128 MB | Combinato con le istanze di pool multipli descritte in precedenza, significa un&#39;allocazione di memoria predefinita di 1024 MB. La dimensione totale è divisa tra tutti i pool di buffer. Per una migliore efficienza, specifica una combinazione di `innodb_buffer_pool_instances` e `innodb_buffer_pool_size` in modo che ogni istanza del pool di buffer sia di almeno 1 GB. |
| `max_connections` | 150 | Il valore del `max_connections` Il parametro deve essere correlato al numero totale di thread PHP configurati nel server dell&#39;applicazione. Una raccomandazione generale sarebbe di 300 per un piccolo e di 1000 per un ambiente medio. |
| `innodb_thread_concurrency` | 0 | Il valore migliore per questa configurazione deve essere calcolato dalla formula: `innodb_thread_concurrency = 2 * (NumCPUs + NumDisks)` |

## [!DNL Varnish]

Magento consiglia vivamente di utilizzare [!DNL Varnish] come server di cache a pagina intera per il tuo archivio. Il modulo PageCache è ancora presente nel codebase, ma deve essere utilizzato solo a scopo di sviluppo. Non deve essere utilizzato insieme o al posto di [!DNL Varnish].

Installa [!DNL Varnish] su un server separato di fronte al livello web. Deve accettare tutte le richieste in arrivo e fornire copie della pagina memorizzate nella cache. Consentire [!DNL Varnish] per lavorare in modo efficace con le pagine protette, un proxy di terminazione SSL può essere posizionato davanti a [!DNL Varnish]. Nginx può essere utilizzato a questo scopo.

[!DNL Commerce] distribuisce un file di configurazione di esempio per [!DNL Varnish] (versioni 4 e 5) che contiene tutte le impostazioni consigliate per le prestazioni. Tra questi, i più critici in termini di prestazioni sono:

* **Verifica dello stato di salute del backend** sondaggi [!DNL Commerce] server per determinare se risponde in modo tempestivo.
* **Modalità Grace** consente di istruire [!DNL Varnish] per mantenere un oggetto nella cache oltre il periodo TTL (Time to Live) e servire questo contenuto non aggiornato se [!DNL Commerce] non è in buona salute o se non è ancora stato recuperato contenuto fresco.
* **Modalità Saint** blacklist non integri [!DNL Commerce] server per un periodo di tempo configurabile. Di conseguenza, i backend non integri non possono servire il traffico quando si utilizza [!DNL Varnish] come load balancer.

Vedi [Avanzate [!DNL Varnish] configurazione](../configuration/cache/config-varnish-advanced.md) per ulteriori informazioni sull’implementazione di queste funzioni.

### Ottimizzare le prestazioni delle risorse

In generale, consigliamo di memorizzare le risorse (immagini, JS, CSS, ecc.) su un CDN per ottenere prestazioni ottimali.

Se il sito non richiede l’implementazione di un numero elevato di impostazioni internazionali e i server si trovano nella stessa area della maggior parte dei clienti, è possibile che si registrino notevoli miglioramenti delle prestazioni a un costo inferiore memorizzando le risorse in [!DNL Varnish] invece di utilizzare una CDN.

Per memorizzare le risorse in [!DNL Varnish], aggiungi le seguenti voci VCL nel tuo `default.vcl` file generato da [!DNL Commerce] per [!DNL Varnish] 5.

Alla fine del `if` istruzione per le richieste PURGE nel `vcl_recv` subroutine, aggiungere:

```javascript
# static files are cacheable. remove SSL flag and cookie

if (req.url ~ "^/(pub/)?(media|static)/.*\.(ico|html|css|js|jpg|jpeg|png|gif|tiff|bmp|mp3|ogg|svg|swf|woff|woff2|eot|ttf|otf)$") {
  unset req.http.Https;
  unset req.http./* {{ ssl_offloaded_header }} */;
  unset req.http.Cookie;
}
```

In `vcl_backend_response` subroutine, cerca `if` istruzione che annulla l&#39;impostazione del cookie per `GET` o `HEAD` richieste.
Il `if` Il blocco deve essere simile al seguente:

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

Riavvia [!DNL Varnish] server per svuotare le risorse memorizzate nella cache ogni volta che si aggiorna il sito o si distribuiscono/aggiornano le risorse.

## Memorizzazione in cache e server di sessione

Il Magento fornisce una serie di opzioni per memorizzare la cache e i dati di sessione, tra cui Redis, Memcache, filesystem e database. Alcune di queste opzioni sono discusse di seguito.

### Configurazione di un singolo nodo web

Se prevedi di gestire tutto il traffico con un solo nodo web, non ha senso mettere la cache su un server Redis remoto. Utilizza invece il filesystem o un server Redis locale. Se si desidera utilizzare il filesystem, mettere le cartelle della cache su un volume montato su un filesystem RAM. Se desideri utilizzare un server Redis locale, si consiglia vivamente di configurare Redis in modo che utilizzi socket per connessioni dirette, anziché scambiare dati tramite HTTP.

### Configurazione di più nodi web

Per una configurazione di più nodi web, Redis è l&#39;opzione migliore. Perché [!DNL Commerce] memorizza attivamente nella cache molti dati per migliorare le prestazioni, presta attenzione al canale di rete tra i nodi web e il server Redis. Non vuoi che il canale diventi un collo di bottiglia per l&#39;elaborazione della richiesta.

>[!INFO]
>
>Se hai bisogno di soddisfare centinaia e migliaia di richieste simultanee, potresti aver bisogno di un canale fino a 1 Gbit (o anche più ampio) per il tuo server Redis.
