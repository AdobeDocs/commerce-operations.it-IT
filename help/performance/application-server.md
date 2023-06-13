---
title: API di Application Server per GraphQL
description: Segui queste istruzioni per abilitare le API di Application Server per GraphQL nella tua distribuzione Adobe Commerce.
badgeCoreBeta: label="2.4.7-beta1" type="informative"
source-git-commit: 28bfc54e0f15ba4f4f941acc7d1fb4825702cdf3
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 0%

---

# API di Application Server per GraphQL

Il server applicazioni Commerce per le API di GraphQL consente ad Adobe Commerce di mantenere lo stato tra le richieste API di Commerce GraphQL e riduce il tempo di avvio per ogni richiesta. Condividendo lo stato dell’applicazione tra i processi, le richieste API diventano notevolmente più efficienti.

Questa versione beta di Application Server è disponibile solo per le distribuzioni locali che eseguono PHP 8.1 o 8.2. Non supporta le distribuzioni basate su cloud. Non supporta ancora la funzionalità GraphQL B2B. Le richieste GraphQL potrebbero non funzionare come previsto nelle distribuzioni locali quando è configurata questa versione del server applicazioni PHP.

## Chi può utilizzare Application Server?

Application Server è disponibile solo per le distribuzioni Commerce locali.

## Abilita Application Server per le API di GraphQL

Il `ApplicationServer` modulo (`Magento/ApplicationServer/`) abilita Application Server per le API di GraphQL.

Per eseguire il server applicazioni in locale, è necessario installare l&#39;estensione Open Swoole e apportare una modifica minore al file di configurazione Nginx della distribuzione.

### Prima di iniziare

Completa queste due attività prima di abilitare `ApplicationServer` modulo:

* Configurare Nginx

* Installare e configurare l’estensione Open Swoole v22

### Configurare Nginx

La tua specifica implementazione di Commerce determina come configurare Nginx. In generale, il file di configurazione di Nginx è denominato per impostazione predefinita `nginx.conf` e si trova in una delle seguenti directory: `/usr/local/nginx/conf`, `/etc/nginx`, o `/usr/local/etc/nginx`. Consulta [Guida per principianti](http://nginx.org/en/docs/beginners_guide.html) per ulteriori informazioni sulla configurazione di Nginx.

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

È possibile installare sia l&#39;estensione Open Swoole per PHP (v22) che i pacchetti Composer necessari a questa estensione con un solo comando.

### Installa Open Swoole

Immetti:

```bash
pecl install openswoole-22.0.0 | composer require openswoole/core:22.1.1
```

Durante l’installazione, Adobe Commerce visualizza le richieste per abilitare il supporto per `openssl`, `mysqlnd`, `sockets`, `http2`, e `postgres`. Invio `yes` per tutte le opzioni eccetto `postgres`.

### Conferma l’installazione di Open Swoole

Esegui `php -m | grep openswoole` per verificare che l’estensione sia stata abilitata correttamente.

### Errori comuni con l’installazione di Open Swoole

Eventuali errori che si verificano durante l&#39;installazione di Open Swoole si verificano in genere durante `pecl` fase di installazione. Gli errori tipici includono mancanti `openssl.h` e `pcre2.h` file. Per risolvere questi errori, accertati che questi due pacchetti siano installati nel sistema locale.

* Controlla posizione di `openssl` eseguendo:

```bash
openssl version -d
```

Questo comando mostra il percorso in cui `openssl` è installato.

* Controlla posizione di `pcre2` eseguendo:

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

