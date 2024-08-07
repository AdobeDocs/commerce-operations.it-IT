---
title: Server applicazioni GraphQL
description: Segui queste istruzioni per abilitare il server applicazioni GraphQL nella tua distribuzione Adobe Commerce.
exl-id: 9b223d92-0040-4196-893b-2cf52245ec33
source-git-commit: 620be59a5b66bd4f55997951c59e473ac14a5c21
workflow-type: tm+mt
source-wordcount: '2085'
ht-degree: 0%

---


# Server applicazioni GraphQL

Commerce GraphQL Application Server consente ad Adobe Commerce di mantenere lo stato tra le richieste API di Commerce GraphQL. GraphQL Application Server, basato sull&#39;estensione Swoole, funziona come un processo con thread di lavoro che gestiscono l&#39;elaborazione delle richieste. Mantenendo uno stato di applicazione avviato tra le richieste API di GraphQL, GraphQL Application Server migliora la gestione delle richieste e le prestazioni complessive del prodotto. Le richieste API diventano notevolmente più efficienti.

GraphQL Application Server è disponibile solo per Adobe Commerce. Non è disponibile per il Magento Open Source. Per i progetti Cloud Pro, è necessario [inviare un ticket di supporto Adobe Commerce](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide) per abilitare il server applicazioni GraphQL.

>[!NOTE]
>
>GraphQL Application Server non è attualmente compatibile con [[!DNL Amazon Simple Storage Service (AWS S3)]](https://aws.amazon.com/s3/). I clienti di Adobe Commerce sull&#39;infrastruttura cloud che attualmente utilizzano [!DNL AWS S3] per l&#39;[archiviazione remota](../configuration/remote-storage/cloud-support.md) non possono utilizzare GraphQL Application Server fino a quando Adobe non rilascerà un hotfix più tardi nel 2024.

## Architettura

GraphQL Application Server mantiene lo stato tra le richieste API di Commerce GraphQL ed elimina la necessità di avviare il sistema. La condivisione dello stato dell&#39;applicazione tra i processi rende le richieste GraphQL notevolmente più efficienti e riduce i tempi di risposta fino al 30%.

Il modello di esecuzione PHP senza condivisione rappresenta una sfida dal punto di vista della latenza, in quanto ogni richiesta richiede l’avvio automatico del framework. Questo processo di bootstrap include attività che richiedono tempo, ad esempio la configurazione della lettura, l&#39;impostazione del processo di bootstrap e la creazione di oggetti della classe di servizio.

La transizione della logica di gestione delle richieste a un ciclo di eventi a livello di applicazione sembra rispondere alla sfida di semplificare l’elaborazione delle richieste a livello aziendale. Questo approccio elimina la necessità di bootstrap durante il ciclo di vita di esecuzione delle richieste.

## Vantaggi

GraphQL Application Server consente ad Adobe Commerce di mantenere lo stato tra richieste consecutive di API Commerce GraphQL. La condivisione dello stato dell’applicazione tra le richieste migliora l’efficienza delle richieste API riducendo al minimo il sovraccarico di elaborazione e ottimizzando la gestione delle richieste. Di conseguenza, il tempo di risposta alle richieste di GraphQL può essere ridotto fino al 30%.

## Requisiti di sistema

L&#39;esecuzione di GraphQL Application Server richiede quanto segue:

* Commerce versione 2.4.7+
* PHP 8.2 o superiore
* Estensione PHP Swoole v5+ installata
* RAM e CPU adeguate in base al carico previsto

## Abilitare e distribuire su infrastruttura cloud

Il modulo `ApplicationServer` (`Magento/ApplicationServer/`) abilita GraphQL Application Server.

### Abilita progetti Pro

>[!NOTE]
>
>Il server applicazioni è una funzione di consenso nelle istanze di Cloud Pro. Per abilitarlo, invia una richiesta di supporto.

Dopo aver attivato la funzionalità Application Server nel progetto Pro, completare i passaggi seguenti prima di distribuire GraphQL Application Server:

1. Distribuisci Adobe Commerce sull&#39;infrastruttura cloud utilizzando il modello cloud del ramo [2.4.7-appserver](https://github.com/magento/magento-cloud/tree/2.4.7-appserver).
1. Assicurati che tutte le personalizzazioni ed estensioni di Commerce siano [compatibili](https://developer.adobe.com/commerce/php/development/components/app-server/) con GraphQL Application Server.
1. Clona il progetto Commerce Cloud.
1. Se necessario, regola le impostazioni nel file application-server/nginx.conf.sample.
1. Aggiungere un commento alla sezione &#39;web&#39; attiva nel file `project_root/.magento.app.yaml`.
1. Rimuovere il commento dalla seguente configurazione di sezione &#39;web&#39; nel file `project_root/.magento.app.yaml` che include il comando di GraphQL Application Server `start`.

   ```yaml
   web:
       upstream:
           socket_family: tcp
           protocol: http
       commands:
           start: ./application-server/start.sh > var/log/application-server-status.log 2>&1
   ```

1. Verificare che `/application-server/start.sh` sia eseguibile eseguendo il comando seguente:

   ```bash
   chmod +x application-server/start.sh
   ```

1. Aggiungi i file aggiornati all’indice Git con questo comando:

   ```bash
   git add -f .magento.app.yaml application-server/*
   ```

1. Esegui il commit delle modifiche con questo comando:

   ```bash
   git commit -m "AppServer Enabled"
   ```

### Distribuire progetti Pro

Dopo aver completato i passaggi di abilitazione, invia le modifiche all’archivio Git per distribuire GraphQL Application Server:

```bash
git push
```

### Abilita progetti iniziali

Prima di distribuire GraphQL Application Server su progetti iniziali, effettuare le operazioni riportate di seguito.

1. Distribuisci Adobe Commerce sull&#39;infrastruttura cloud utilizzando il modello cloud del ramo [2.4.7-appserver](https://github.com/magento/magento-cloud/tree/2.4.7-appserver).
1. Verificare che tutte le personalizzazioni e le estensioni di Commerce siano compatibili con GraphQL Application Server.
1. Verificare che la variabile di ambiente `CRYPT_KEY` sia impostata per l&#39;istanza. Puoi controllare lo stato di questa variabile sul Cloud Project Portal (Interfaccia utente di onboarding).
1. Clona il progetto Commerce Cloud.
1. Rinomina `application-server/.magento/.magento.app.yaml.sample` in `application-server/.magento/.magento.app.yaml` e, se necessario, regola le impostazioni in .magento.app.yaml.
1. Rimuovere il commento dalla configurazione della route seguente nel file `project_root/.magento/routes.yaml` per reindirizzare il traffico `/graphql` a GraphQL Application Server.

   ```yaml
   "http://{all}/graphql":
       type: upstream
       upstream: "application-server:http"
   ```

1. Aggiungi file aggiornati all’indice Git:

   ```bash
   git add -f .magento/routes.yaml application-server/.magento/*
   ```

1. Eseguire il commit delle modifiche:

   ```bash
   git commit -m "AppServer Enabled"
   ```

>[!NOTE]
>
>Assicurarsi che tutte le impostazioni personalizzate nel file radice `.magento.app.yaml` siano migrate in modo appropriato nel file `application-server/.magento/.magento.app.yaml`. Dopo aver aggiunto il file `application-server/.magento/.magento.app.yaml` al progetto, è necessario mantenerlo in aggiunta al file radice `.magento.app.yaml`. Se ad esempio è necessario [configurare il servizio RabbitMQ](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/service/rabbitmq) o [gestire le proprietà Web](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure/app/properties/web-property), aggiungere la stessa configurazione anche a `application-server/.magento/.magento.app.yaml`.

### Distribuire progetti iniziali

Dopo aver completato i [passaggi](#before-you-begin-a-cloud-starter-deployment) per l&#39;abilitazione, invia le modifiche all&#39;archivio Git per distribuire GraphQL Application Server:

```bash
git push
```

### Verificare l’abilitazione nei progetti cloud

1. Eseguire una query GraphQL o una mutazione sull&#39;istanza per confermare che l&#39;endpoint `graphql` è accessibile. Ad esempio:

   ```
   mutation {  
    createEmptyCart
   }
   ```

   La risposta prevista dovrebbe essere simile a questo esempio:

   ```json
   {    
    "data": {        
        "createEmptyCart": "HLATPzcLw5ylDf76IC92nxdO2hXSXOrv"    
        }
    }
   ```

1. Utilizza SSH per accedere alla tua istanza cloud. `project_root/var/log/application-server.log` deve contenere un nuovo record di registro per ogni richiesta GraphQL.

1. È inoltre possibile verificare se GraphQL Application Server è in esecuzione eseguendo il comando seguente:

   ```bash
   ps aux|grep php
   ```

   Dovresti visualizzare un processo `bin/magento server:run` con più thread.

Se questi passaggi di verifica hanno esito positivo, GraphQL Application Server è in esecuzione e fornisce `/graphql` richieste.

## Abilita progetti locali

Il modulo `ApplicationServer` (`Magento/ApplicationServer/`) abilita le API di GraphQL Application Server per GraphQL.

L&#39;esecuzione locale di GraphQL Application Server richiede l&#39;installazione dell&#39;estensione Swoole e una modifica minore al file di configurazione Nginx della distribuzione.

### Prerequisiti

Completare i passaggi seguenti prima di abilitare il modulo `ApplicationServer`:

* Configurare Nginx
* Installare e configurare l’estensione Swoole v5+

#### Configurare Nginx

La distribuzione specifica di Commerce determina come configurare Nginx. In generale, il file di configurazione Nginx è denominato `nginx.conf` per impostazione predefinita e si trova in una delle seguenti directory: `/usr/local/nginx/conf`, `/etc/nginx` o `/usr/local/etc/nginx`. Per ulteriori informazioni sulla configurazione di Nginx, vedere la _[Guida per principianti](https://nginx.org/en/docs/beginners_guide.html)_.

Esempio di configurazione di Nginx:

```conf
location /graphql {
    proxy_set_header Host $http_host;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;

    proxy_pass http://127.0.0.1:9501/graphql;
}
```

#### Installare e configurare Swoole

Per eseguire GraphQL Application Server localmente, installare l&#39;estensione Swoole (v5.0 o successiva). Esistono diversi modi per installare questa estensione.

La procedura seguente descrive come installare l’estensione Swoole per PHP 8.2 su sistemi basati su OSX. Si tratta di uno dei diversi modi per installare l’estensione Swoole.

```bash
pecl install swoole
```

Durante l&#39;installazione, Adobe Commerce visualizza le richieste per abilitare il supporto per `openssl`, `mysqlnd`, `sockets`, `http2` e `postgres`. Immettere `yes` per tutte le opzioni eccetto `postgres`.

### Verifica installazione Swoole

Conferma che l&#39;estensione sia stata abilitata correttamente:

```bash
php -m | grep swoole
```

### Errori comuni con l’installazione di Swoole

Eventuali errori che si verificano durante l&#39;installazione di Swoole si verificano in genere durante la fase di installazione di `pecl`. Gli errori tipici includono i file mancanti `openssl.h` e `pcre2.h`. Per risolvere questi errori, accertati che questi due pacchetti siano installati nel sistema locale.

* Controllare il percorso di `openssl` eseguendo:

```bash
openssl version -d
```

Questo comando mostra il percorso in cui è installato `openssl`.

* Controllare il percorso di `pcre2` eseguendo:

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

Per risolvere i problemi relativi a `openssl`, eseguire:

```bash
export LDFLAGS="-L/opt/homebrew/etc/openssl@3/lib" export CPPFLAGS="-I/opt/homebrew/etc/openssl@3/include"
```

Verificare di utilizzare il percorso dell&#39;ambiente `dev` locale.

#### Conferma la risoluzione dei problemi correlati a openssl

È possibile eseguire nuovamente il comando seguente per verificare se i problemi correlati a openssl sono stati risolti:

```bash
pecl install swoole
```

#### Risolvere i problemi relativi a pcre2.h

Per risolvere i problemi relativi a `pcre2.h`, collegare il percorso `pcre2.h` alla directory dell&#39;estensione PHP installata. La versione installata specifica di PHP e `pcr2.h` determina la versione specifica del comando da utilizzare.

### Esegui server applicazioni GraphQL

Avvia GraphQL Application Server:

```bash
bin/magento server:run
```

Questo comando avvia una porta HTTP su 9501. Dopo l&#39;avvio di GraphQL Application Server, la porta 9501 diventa un server proxy HTTP per tutte le query GraphQL.

Per verificare che GraphQL Application Server sia in esecuzione nella distribuzione:

```bash
ps aux | grep php
```

Altri metodi per verificare che GraphQL Application Server sia in esecuzione includono:

* Verificare nel file `/var/log/application-server.log` la presenza di voci correlate alle richieste GraphQL elaborate.
* Provare a connettersi alla porta HTTP su cui viene eseguito GraphQL Application Server. Esempio: `curl -g 'http://localhost:9501/graph`.

### Conferma l’elaborazione delle richieste GraphQL

GraphQL Application Server aggiunge l&#39;intestazione di risposta `X-Backend` con il valore `graphql_server` a ogni richiesta elaborata. Per verificare se GraphQL Application Server ha gestito una richiesta, verificare questa intestazione di risposta.

### Conferma compatibilità di estensione e personalizzazione

Gli sviluppatori e i commercianti delle estensioni devono verificare innanzitutto che il codice di estensione e personalizzazione sia conforme alle linee guida descritte in _[Linee guida tecniche](https://developer.adobe.com/commerce/php/coding-standards/technical-guidelines/)_.

Considera queste linee guida durante la valutazione del codice:

* Le classi del servizio (ovvero le classi che forniscono il comportamento ma non i dati, ad esempio `EventManager`) non devono avere uno stato mutabile.
* Evitare l&#39;accoppiamento temporale.

## Disabilita server applicazioni GraphQL

Le procedure per la disattivazione di GraphQL Application Server variano a seconda che il server sia in esecuzione in una distribuzione locale o cloud.

### Disabilita server applicazioni GraphQL (cloud)

1. Rimuovere tutti i nuovi file ed eventuali altre modifiche al codice inclusi nel commit `AppServer Enabled` durante i preparativi per la distribuzione.

1. Eseguire il commit delle modifiche utilizzando questo comando:

   ```bash
   git commit -m "AppServer Disabled"
   ```

1. Distribuisci le modifiche utilizzando questo comando:

   ```bash
   git push
   ```

### Disabilita GraphQL Application Server (locale)

1. Aggiungere un commento alla sezione `/graphql` del file `nginx.conf` aggiunto quando si abilita GraphQL Application Server.
1. Riavvia indice.

Questo metodo di disattivazione di GraphQL Application Server può essere utile per testare o confrontare rapidamente le prestazioni.

### Verificare che GraphQL Application Server sia disabilitato

Per confermare che `php-fpm` sta elaborando le richieste di GraphQL al posto di GraphQL Application Server, immettere il comando seguente: `ps aux | grep php`.

Dopo aver disabilitato GraphQL Application Server:

* `bin/magento server:run` è inattivo.
* `var/log/application-server.log` non contiene voci dopo le richieste di GraphQL.

## Integrazione e test funzionali per GraphQL Application Server

Gli sviluppatori di estensioni possono eseguire due integration test per verificare la compatibilità dell&#39;estensione con GraphQL Application Server: `GraphQlStateTest` e `ResetAfterRequestTest`.

### GraphQlStateTest

`GraphQlStateTest` rileva lo stato negli oggetti condivisi che non deve essere riutilizzato per più richieste.

Questo test è progettato per rilevare le modifiche dello stato negli oggetti del servizio generati da `ObjectManager`. Il test esegue due volte query GraphQL identiche e confronta lo stato dell&#39;oggetto servizio prima e dopo la seconda query.

#### Errori GraphQlStateTest e potenziale correzione

* **Impossibile aggiungere, saltare o filtrare un elenco**. Se si verifica un errore durante l&#39;aggiunta, il salto o il filtraggio di un elenco, valutare se è possibile eseguire il refactoring della classe in modo compatibile con le versioni precedenti per utilizzare le factory delle classi di servizio con stato mutabile.

* **La classe presenta uno stato modificabile**. Se la classe stessa presenta uno stato mutabile, prova a riscrivere il codice per aggirare questo stato. Se lo stato mutabile è necessario per motivi di prestazioni, implementare `ResetAfterRequestInterface` e utilizzare `_resetState()` per ripristinare lo stato costruito iniziale dell&#39;oggetto.

* **Impossibile accedere alla proprietà digitata $x prima del messaggio di inizializzazione**. Errori con questo tipo di messaggio indicano che la proprietà specificata non è stata inizializzata dal costruttore. Si tratta di una forma di accoppiamento temporale che si verifica perché l&#39;oggetto non può essere utilizzato dopo che è stato inizialmente costruito. Questo accoppiamento si verifica anche se la proprietà è privata perché l’agente di raccolta che recupera i dati dalle proprietà utilizza la funzione di riflessione PHP. In questo caso, provare a rieseguire il factoring della classe per evitare l&#39;accoppiamento temporale e lo stato mutabile. Se il refactoring non risolve l&#39;errore, è possibile modificare il tipo di proprietà in un tipo nullable in modo che possa essere inizializzato in null.  Se la proprietà è un array, provare a inizializzarla come array vuoto.

Eseguire `GraphQlStateTest` eseguendo `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/GraphQl/App/GraphQlStateTest.php`.

### ResetAfterRequestTest

`ResetAfterRequestTest` cerca tutte le classi che implementano `ResetAfterRequestInterface` e verifica che il metodo `_resetState()` restituisca lo stato di un oggetto allo stesso stato che aveva dopo essere stato costruito da `ObjectManager`.  Questo test crea un oggetto servizio con `ObjectManager`, quindi clona l&#39;oggetto, chiama `_resetState()` e confronta entrambi gli oggetti. Il test non chiama alcun metodo tra la creazione dell&#39;istanza dell&#39;oggetto e `_resetState()`, pertanto non conferma la reimpostazione di alcuno stato mutabile. Sono stati rilevati problemi in cui un bug o un errore di battitura in `_resetState()` può impostare lo stato su un valore diverso da quello originale.

#### Errori ResetAfterRequestTest e potenziale correzione

* **La classe contiene valori di proprietà incoerenti**. Se il test non riesce, verificare se una classe è stata modificata con il risultato che l&#39;oggetto dopo la costruzione ha valori di proprietà diversi rispetto a quelli che ha dopo la chiamata al metodo `_resetState()`. Se la classe su cui si sta lavorando non contiene il metodo `_resetState()` stesso, controllare la gerarchia di classi per individuare una superclasse che lo implementa.

* **Impossibile accedere alla proprietà digitata $x prima del messaggio di inizializzazione**. Questo problema si verifica anche con `GraphQlStateTest`.

  Eseguire `ResetAfterRequestTest` eseguendo: `vendor/bin/phpunit -c $(pwd)/dev/tests/integration/phpunit.xml dev/tests/integration/testsuite/Magento/Framework/ObjectManager/ResetAfterRequestTest.php`.

### Test funzionali

durante la distribuzione di GraphQL Application Server, gli sviluppatori di estensioni devono eseguire test funzionali WebAPI ed eventuali test funzionali personalizzati automatizzati o manuali per GraphQL. Questi test funzionali aiutano gli sviluppatori a identificare potenziali errori o problemi di compatibilità.

#### Modalità di monitoraggio stato

Durante l&#39;esecuzione di test funzionali o manuali, GraphQL Application Server può essere eseguito con `--state-monitor mode` abilitato per consentire la ricerca di classi in cui lo stato viene riutilizzato involontariamente. Avviare l&#39;Application Server normalmente, tranne aggiungere il parametro `--state-monitor`.

```
bin/magento server:run --state-monitor
```

Dopo l&#39;elaborazione di ogni richiesta, viene aggiunto un nuovo file alla directory `tmp`, ad esempio: `var/tmp/StateMonitor-thread-output-50-6nmxiK`. Al termine del test, questi file possono essere uniti con il comando `bin/magento server:state-monitor:aggregate-output`, che crea due file uniti, uno in `XML` e uno in `JSON`.

Esempi:

```
/var/workspace/var/tmp/StateMonitor-json-2024-04-10T18:50:39Z-hW0ucN.json
/var/workspace/var/tmp/StateMonitor-junit-2024-04-10T18:50:39Z-oreUco.xml
```

Questi file possono essere esaminati con qualsiasi strumento utilizzato per visualizzare XML o JSON che mostra le proprietà modificate degli oggetti del servizio come `GraphQlStateTest`. La modalità `--state-monitor` utilizza lo stesso elenco di salto e lo stesso elenco di filtri di GraphQlStateTest.

>[!NOTE]
>
>Non utilizzare la modalità `--state-monitor` in produzione. È progettato solo per lo sviluppo e il testing. Crea molti file di output ed è più lento del normale.

>[!NOTE]
>
>`--state-monitor` non è compatibile con le versioni PHP `8.3.0` - `8.3.4` a causa di un bug nel Garbage Collector PHP. Se si utilizza PHP 8.3, è necessario eseguire l&#39;aggiornamento a `8.3.5` o versione successiva per utilizzare questa funzionalità.
