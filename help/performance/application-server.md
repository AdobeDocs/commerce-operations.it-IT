---
title: API di Application Server per GraphQL
description: Segui queste istruzioni per abilitare le API di Application Server per GraphQL nella tua distribuzione Adobe Commerce.
badgeCoreBeta: label="2.4.7-beta" type="informative"
exl-id: 9b223d92-0040-4196-893b-2cf52245ec33
source-git-commit: b7639e8830b2cab971e3e22285d91105b64e9a6e
workflow-type: tm+mt
source-wordcount: '1768'
ht-degree: 0%

---

# API di Application Server per GraphQL

Il server applicazioni Commerce per le API di GraphQL consente ad Adobe Commerce di mantenere lo stato tra le richieste API di Commerce GraphQL. Application Server, basato sull&#39;estensione Open Cloud, funziona come un processo con thread di lavoro che gestiscono l&#39;elaborazione delle richieste. Mantenendo uno stato di applicazione avviato tra le richieste API di GraphQL, Application Server migliora la gestione delle richieste e le prestazioni complessive del prodotto. Le richieste API diventano notevolmente più efficienti.

Application Server è supportato solo nelle distribuzioni Cloud Starter e on-premise. Non è disponibile per le istanze Cloud Pro durante la versione beta. Non è disponibile per le distribuzioni di Magento Open Source.

## Panoramica dell&#39;architettura di Application Server

Application Server mantiene lo stato tra le richieste API di Commerce GraphQL ed elimina la necessità di bootstrap. La condivisione dello stato dell&#39;applicazione tra i processi rende le richieste GraphQL notevolmente più efficienti e riduce i tempi di risposta fino al 30%.

Il modello di esecuzione PHP senza condivisione rappresenta una sfida dal punto di vista della latenza, in quanto ogni richiesta richiede l’avvio automatico del framework. Questo processo di bootstrap include attività che richiedono tempo, ad esempio la configurazione della lettura, l&#39;impostazione del processo di bootstrap e la creazione di oggetti della classe di servizio.

La transizione della logica di gestione delle richieste a un ciclo di eventi a livello di applicazione sembra rispondere alla sfida di semplificare l’elaborazione delle richieste a livello aziendale. Questo approccio elimina la necessità di bootstrap durante il ciclo di vita di esecuzione delle richieste.

## Vantaggi dell&#39;utilizzo di Application Server

Application Server consente ad Adobe Commerce di mantenere lo stato tra richieste API consecutive di Commerce GraphQL. La condivisione dello stato dell’applicazione tra le richieste migliora l’efficienza delle richieste API riducendo al minimo il sovraccarico di elaborazione e ottimizzando la gestione delle richieste. Di conseguenza, il tempo di risposta alle richieste di GraphQL può essere ridotto fino al 30%.

## Requisiti di sistema

L&#39;esecuzione di Application Server richiede quanto segue:

* PHP 8.2 o superiore
* Aprire Swoole PHP Extension v22+ installato
* RAM e CPU adeguate in base al carico previsto

## Abilita Application Server per Cloud Starter

Il `ApplicationServer` modulo (`Magento/ApplicationServer/`) abilita Application Server per le API di GraphQL. Application Server è supportato solo nelle distribuzioni locali e Cloud Starter. Non è disponibile per le istanze Cloud Pro durante la versione beta.

### Prima di iniziare un’implementazione di Cloud Starter

Prima di distribuire il server applicazioni, completare le attività seguenti:

1. Verifica che Adobe Commerce sia installato su Commerce Cloud.
1. Confermare che `CRYPT_KEY` la variabile di ambiente è impostata per l’istanza. Puoi controllare lo stato di questa variabile sul Cloud Project Portal (Interfaccia utente di onboarding).
1. Clona il progetto Commerce Cloud.
1. Creare un `graphql` cartella nel tuo `project_root` cartella.
1. Aggiungi il componente personalizzato aggiuntivo `.magento.app.yaml` file incluso nel [contenuto del file magento.app.yaml](#magento.app.yaml-file-content) nell&#39;oggetto `project_root/graphql` cartella.
1. Modifica il `project_root/.magento/routes.yaml` file per includere le direttive seguenti:

   ```yaml
   # The routes of the project.
   #
   # Each route describes how an incoming URL is going to be processed.
   
   "http://{default}/":
     type: upstream
     upstream: "mymagento:http"
   
   "http://{default}/graphql":
     type: upstream
     upstream: "graphql:http"
   ```

1. Aggiungi i file aggiornati all’indice Git con questo comando:

   ```bash
   git add -f php.ini graphql/.magento.app.yaml .magento/routes.yaml swoole.so
   ```

1. Esegui il commit delle modifiche con questo comando:

   ```bash
   git commit -m "AppServer Enabled"
   ```

### Distribuire il server applicazioni su Cloud Starter

Dopo aver eseguito le attività preliminari, distribuire Application Server utilizzando il comando seguente:

```bash
git push
```

### Verifica abilitazione del server applicazioni in Cloud Starter

1. Apri l’interfaccia utente del progetto Cloud. Dovresti trovare un punto di accesso SSH aggiuntivo per `graphql` applicazione.

1. Utilizza SSH per accedere alla tua istanza Cloud utilizzando il punto di accesso all’applicazione graphql, quindi esegui il seguente comando:

   ```bash
   ps aux|grep php
   ```

1. Esegui una query GraphQL o una mutazione rispetto all’istanza per confermare che `graphql` endpoint accessibile. Ad esempio:

   ```
   mutation {  
    createEmptyCart
   }
   ```

   La risposta prevista dovrebbe essere simile a questo esempio:

   ```terminal
   {    
    "data": {        
        "createEmptyCart": "HLATPzcLw5ylDf76IC92nxdO2hXSXOrv"    
        }
    }
   ```

1. Utilizza SSH per accedere alla tua istanza Cloud tramite il punto di accesso all’applicazione GraphQL. Il `project_root/var/log/magento-server.log` deve contenere un nuovo record di registro per ogni richiesta GraphQL.

Se questi passaggi di verifica hanno esito positivo, puoi procedere con l’esecuzione del ciclo di test.


## Abilita server applicazioni in implementazioni locali

Il `ApplicationServer` modulo (`Magento/ApplicationServer/`) abilita Application Server per le API di GraphQL.

Per eseguire il server applicazioni in locale, è necessario installare l&#39;estensione Open Swoole e apportare una modifica minore al file di configurazione Nginx della distribuzione.

### Prima di iniziare un’implementazione on-premise

Completa queste due attività prima di abilitare `ApplicationServer` modulo:

* Configurare Nginx

* Installare e configurare l’estensione Open Swoole v22

### Configurare Nginx

La tua specifica implementazione di Commerce determina come configurare Nginx. In generale, il file di configurazione di Nginx è denominato per impostazione predefinita `nginx.conf` e si trova in una delle seguenti directory: `/usr/local/nginx/conf`, `/etc/nginx`, o `/usr/local/etc/nginx`. Consulta [Guida per principianti](https://nginx.org/en/docs/beginners_guide.html) per ulteriori informazioni sulla configurazione di Nginx.

Esempio di configurazione di Nginx:

```conf
location /graphql {
    proxy_set_header Host $http_host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    proxy_pass http://127.0.0.1:9501/graphql;
}
```

### Installare e configurare Open Cloud

Per eseguire il server applicazioni in locale, installare l&#39;estensione Open Swoole v22. Esistono diversi modi per installare questa estensione.

## Esegui server applicazioni

Avviare il server applicazioni:

```bash
bin/magento server:run
```

Questo comando avvia una porta HTTP su 9501. Una volta avviato Application Server, la porta 9501 diventa un server proxy HTTP per tutte le query GraphQL.

## Esempio: installazione di Open Swoole (OSX)

Questa procedura illustra come installare l’estensione Open Swoole su PHP 8.2 per sistemi basati su OSX. Si tratta di uno dei diversi modi per installare l’estensione Open Swoole.

### Installa Open Swoole

Immetti:

```bash
pecl install openswoole-22.0.0
composer require openswoole/core:22.1.1
```

Durante l’installazione, Adobe Commerce visualizza le richieste per abilitare il supporto per `openssl`, `mysqlnd`, `sockets`, `http2`, e `postgres`. Invio `yes` per tutte le opzioni eccetto `postgres`.

### Conferma l’installazione di Open Swoole

Esegui `php -m | grep openswoole` per verificare che l’estensione sia stata abilitata correttamente.

### Errori comuni con l’installazione di Open Swoole

Eventuali errori che si verificano durante l&#39;installazione di Open Swoole si verificano in genere durante `pecl` fase di installazione. Gli errori tipici includono mancanti `openssl.h` e `pcre2.h` file. Per risolvere questi errori, accertati che questi due pacchetti siano installati nel sistema locale.

* Controlla la posizione di `openssl` eseguendo:

```bash
openssl version -d
```

Questo comando mostra il percorso in cui `openssl` è installato.

* Controlla la posizione di `pcre2` eseguendo:

```bash
pcre2-config --prefix 
```

Utilizzare Homebrew per installare i pacchetti mancanti se l&#39;output del comando indica che mancano file:

```bash
brew install openssl
```

```bash
brew install pcre2
```

#### Risolvere i problemi con openssl

Per risolvere i problemi relativi a `openssl`, esegui:

```bash
export LDFLAGS="-L/opt/homebrew/etc/openssl@3/lib" export CPPFLAGS="-I/opt/homebrew/etc/openssl@3/include"
```

Conferma di utilizzare il percorso dal tuo `dev` ambiente.

#### Conferma la risoluzione dei problemi correlati a openssl

È possibile eseguire nuovamente il comando seguente per verificare se i problemi correlati a openssl sono stati risolti:

```bash
pecl install openswoole-22.0.0
```

#### Risolvere i problemi relativi a pcre2.h

Per risolvere i problemi relativi a `pcre2.h`, collegano simbolicamente il `pcre2.h` percorso della directory dell&#39;estensione PHP installata. La versione specifica installata di PHP e `pcr2.h` determina la versione specifica del comando da utilizzare.

### Verificare che il server applicazioni sia in esecuzione

Per verificare che il server applicazioni sia in esecuzione nella distribuzione, eseguire il comando seguente:

```bash
ps aux | grep php
```

Altri metodi per verificare che Application Server sia in esecuzione includono:

* Controlla la `/var/log/magento-server.log` file per le voci correlate alle richieste GraphQL elaborate.
* Provare a connettersi alla porta HTTP su cui viene eseguito Application Server. Ad esempio: `curl -g 'http://localhost:9501/graph`.

### Conferma che le richieste GraphQL vengano elaborate dal server applicazioni

Application Server aggiunge `X-Backend` intestazione di risposta con il valore `graphql_server` a ogni richiesta elaborata. Per verificare se una richiesta è stata gestita da Application Server, controllare questa intestazione di risposta.

### Conferma della compatibilità di estensione e personalizzazione con Application Server

Gli sviluppatori e i commercianti di estensioni devono prima verificare che il loro codice di estensione e personalizzazione sia conforme alle linee guida tecniche descritte in [Linee guida tecniche](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/).

Considera queste linee guida durante la valutazione del codice:

* Classi di servizio (ovvero classi che forniscono il comportamento ma non i dati, ad esempio `EventManager`) non deve avere uno stato mutabile.
* Evitare l&#39;accoppiamento temporale.

## Disabilita server applicazioni

Le procedure per la disattivazione di Application Server variano a seconda che il server sia in esecuzione in una distribuzione locale o cloud.

### Disabilita server applicazioni su Cloud Starter

1. Rimuovi eventuali nuovi file e altre modifiche al codice inclusi nel `AppServer Enabled` esegui il commit durante i preparativi per l’implementazione.

1. Eseguire il commit delle modifiche utilizzando questo comando:

   ```bash
   git commit -m "AppServer Disabled"
   ```

1. Distribuisci le modifiche utilizzando questo comando:

   ```bash
   git push
   ```

### Disabilita server applicazioni

1. Commenta il `/graphql` sezione di `nginx.conf` file aggiunto durante l&#39;abilitazione di Application Server.
1. Riavvia indice.

Questo metodo di disattivazione di Application Server può essere utile per testare o confrontare rapidamente le prestazioni.

### Conferma che Application Server è disabilitato

Per confermare che le richieste GraphQL vengono elaborate da `php-fpm` anziché Application Server, immettere il comando seguente: `ps aux | grep php`.

Dopo la disabilitazione di Application Server:

* `bin/magento server:run` è inattivo.
* `var/log/magento-server.log` non contiene voci dopo le richieste di GraphQL.

## Integrazione e test funzionali per il server applicazioni PHP

Gli sviluppatori di estensioni possono eseguire due integration test per verificare la compatibilità dell’estensione con il server applicazioni: `GraphQlStateTest` e `ResetAfterRequestTest`.

### GraphQlStateTest

`GraphQlStateTest` rileva lo stato negli oggetti condivisi che non devono essere riutilizzati per più richieste.

Questo test è progettato per rilevare le modifiche dello stato negli oggetti del servizio prodotti da `ObjectManager`. Il test esegue due volte query GraphQL identiche e confronta lo stato dell&#39;oggetto servizio prima e dopo la seconda query. 

#### Errori GraphQlStateTest e potenziale correzione

* **Impossibile aggiungere, saltare o filtrare un elenco**. Se si verifica un errore che indica che non è sicuro aggiungere, saltare o filtrare un elenco, valutare se è possibile eseguire il refactoring della classe in modo compatibile con le versioni precedenti per utilizzare le factory delle classi di servizio con stato mutabile.

* **La classe presenta uno stato mutabile**. Se la classe stessa presenta uno stato mutabile, prova a riscrivere il codice per aggirare questo stato. Se per motivi di prestazioni è necessario lo stato mutabile, implementa `ResetAfterRequestInterface` e utilizzare `_resetState()` per ripristinare lo stato di costruzione iniziale dell&#39;oggetto.

* **Impossibile accedere alla proprietà digitata $x prima del messaggio di inizializzazione**. Errori con questo tipo di messaggio indicano che la proprietà specificata non è stata inizializzata dal costruttore. Si tratta di una forma di accoppiamento temporale che si verifica perché l&#39;oggetto non può essere utilizzato dopo che è stato inizialmente costruito. Questo accoppiamento si verifica anche se la proprietà è privata perché l’agente di raccolta che recupera i dati dalle proprietà utilizza la funzione di riflessione PHP. In questo caso, provare a rieseguire il factoring della classe per evitare l&#39;accoppiamento temporale e lo stato mutabile. Se il refactoring non risolve l&#39;errore, è possibile modificare il tipo di proprietà in un tipo nullable in modo che possa essere inizializzato in null.  Se la proprietà è un array, provare a inizializzarla come array vuoto.

Esegui `GraphQlStateTest` eseguendo `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/GraphQl/App/GraphQlStateTest.php`.

### ResetAfterRequestTest

`ResetAfterRequestTest` cerca tutte le classi che implementano `ResetAfterRequestInterface` e verifica che `_resetState()` il metodo restituisce lo stato di un oggetto allo stesso stato che aveva dopo essere stato costruito da `ObjectManager`.  Questo test crea un oggetto servizio con `ObjectManager`, quindi clona tale oggetto, chiama `_resetState()`e quindi confronta entrambi gli oggetti. Il test non chiama alcun metodo tra la creazione di istanze di oggetti e `_resetState()`, pertanto non conferma il ripristino di alcuno stato mutabile. Trova problemi quando un bug o un errore di battitura in `_resetState()` può impostare lo stato su un valore diverso da quello originale.

#### Errori ResetAfterRequestTest e potenziale correzione

* **La classe presenta valori di proprietà incoerenti**. Se il test ha esito negativo, verificare se una classe è stata modificata con il risultato che l&#39;oggetto dopo la costruzione ha valori di proprietà diversi rispetto a quelli dopo la `_resetState()` viene chiamato il metodo. Se la classe su cui stai lavorando non contiene `_resetState()` nella gerarchia di classi per individuare una superclasse che la implementa.

* **Impossibile accedere alla proprietà digitata $x prima del messaggio di inizializzazione**. Questo problema si verifica anche con `GraphQlStateTest`.
 
Esegui `ResetAfterRequestTest` eseguendo: `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/Framework/ObjectManager/ResetAfterRequestTest.php`.

### Test funzionali

Durante la distribuzione del server applicazioni, gli sviluppatori delle estensioni devono eseguire test funzionali WebAPI per GraphQL, nonché eventuali test funzionali personalizzati automatizzati o manuali per GraphQL. Questi test funzionali aiutano gli sviluppatori a identificare potenziali errori o problemi di compatibilità.

## contenuto del file magento.app.yaml

Consulta [Prima di iniziare un’implementazione di Cloud Starter](#Before-you-begin-a-Cloud-Starter-deployment) per istruzioni sull&#39;aggiunta del codice seguente al `project_root/graphql` cartella.

```yaml
name: graphql
# The toolstack used to build the application.
type: php:8.2
build:
    flavor: none
 
source:
    root: /
dependencies:
    php:
        composer/composer: '2.5.5'
 
# Enable extensions required by Magento 2
runtime:
    extensions:
        - xsl
        - sodium
 
# The relationships of the application with services or other applications.
# The left-hand side is the name of the relationship as it will be exposed
# to the application in the environment variable. The right-hand
# side is in the form `<service name>:<endpoint name>`.
relationships:
    database: "mysql:mysql"
    redis: "redis:redis"
    opensearch: "opensearch:opensearch"
 
# The configuration of app when it is exposed to the web.
web:
    commands:
        start: "php -dopcache.enable_cli=1 -dopcache.validate_timestamps=0 bin/magento server:run -vvv  --port=${PORT:-80} > ${MAGENTO_CLOUD_APP_DIR}/var/log/magento-server.log 2>&1"
    upstream:
        socket_family: tcp
        protocol: http
    locations:
        '/':
            root: "pub"
            passthru: true
 
# The size of the persistent disk of the application (in MB).
disk: 5120
 
# The mounts that will be performed when the package is deployed.
mounts:
    "var": "shared:files/var"
    "app/etc": "shared:files/etc"
    "pub/media": "shared:files/media"
    "pub/static": "shared:files/static"
 
hooks:
    # We run build hooks before your application has been packaged.
    build: |
        set -e
        composer install
        php ./vendor/bin/ece-tools run scenario/build/generate.xml
        php ./vendor/bin/ece-tools run scenario/build/transfer.xml
    # We run deploy hook after your application has been deployed and started.
    deploy: |
        php ./vendor/bin/ece-tools run scenario/deploy.xml
    # We run post deploy hook to clean and warm the cache. Available with ECE-Tools 2002.0.10.
    post_deploy: |
        php ./vendor/bin/ece-tools run scenario/post-deploy.xml
```
