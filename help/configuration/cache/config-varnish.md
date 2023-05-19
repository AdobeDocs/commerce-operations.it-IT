---
title: Configurare e utilizzare vernice
description: Scopri in che modo Vernice memorizza i file e migliora il traffico HTTP.
exl-id: 57614878-e349-43bb-b22b-1aa321907be1
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 0%

---

# Configura vernice

[Cache vernice] è un acceleratore di applicazioni web open-source (noto anche come _Acceleratore HTTP_ o _caching proxy inverso HTTP_). La vernice memorizza (o memorizza in cache) file o frammenti di file in memoria, il che consente a Vernice di ridurre il tempo di risposta e il consumo di larghezza di banda della rete su richieste equivalenti future. A differenza dei server web come Apache e Nginx, Varnish è stato progettato per essere usato esclusivamente con il protocollo HTTP.

Commerce 2.4.2 è testato con vernice 6.4. Commerce 2.4.x è compatibile con Vernice 6.x

>[!WARNING]
>
>Noi _consiglia vivamente_ usa vernice per la produzione. Il caching a pagina intera incorporato, al file system o [database]- è molto più lento di Varnish, ed è progettato per accelerare il traffico HTTP.

Per ulteriori informazioni sulla vernice, consulta:

- [Il quadro vernice grande]
- [Opzioni di avvio vernice]
- [Vernice e prestazioni del sito web]

## Diagramma topologico della vernice

La figura seguente mostra una vista di base della vernice nella topologia Commerce.

![Diagramma di vernice di base](../../assets/configuration/varnish-basic.png)

Nella figura precedente, le richieste HTTP degli utenti su Internet generano numerose richieste di CSS, HTML, JavaScript e immagini (collettivamente denominate _risorse_). Varnish siede davanti al server web e invia queste richieste al server web.

Quando il server web restituisce le risorse, le risorse memorizzabili in cache vengono memorizzate in vernice. Eventuali richieste successive per tali risorse vengono soddisfatte da Varish (ovvero, le richieste non raggiungono il server web). La vernice restituisce il contenuto memorizzato nella cache in modo estremamente rapido. I risultati sono tempi di risposta più rapidi per restituire il contenuto agli utenti e un numero ridotto di richieste che devono essere soddisfatte da Commerce.

Le risorse memorizzate nella cache da Varish scadono a un intervallo configurabile o vengono sostituite da versioni più recenti delle stesse risorse. È inoltre possibile cancellare la cache manualmente utilizzando Admin o [`magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types) comando.

## Panoramica del processo

In questo argomento viene illustrato come installare inizialmente Vernice con un set minimo di parametri e verificare che funzioni. Esportare quindi una configurazione Vernice dall&#39;amministratore Commerce e testarla nuovamente.

Il processo può essere riassunto come segue:

1. Installa Vernice e testa accedendo a qualsiasi pagina di Commerce per vedere se ricevi intestazioni di risposta HTTP che indicano che Vernice funziona.
1. Installa il software Commerce e utilizza l’Amministratore per creare un file di configurazione per Vernice.
1. Sostituisci il file di configurazione vernice esistente con quello generato dall&#39;amministratore.
1. Prova di nuovo tutto.

   Se non c’è nulla nel tuo `<magento_root>/var/page_cache` directory, la configurazione di Varnish con Commerce è stata completata.

>[!NOTE]
- Ad eccezione dei casi indicati, è necessario immettere tutti i comandi descritti in questo argomento come utente con `root` privilegi.
- Questo argomento è stato scritto per Varnish su CentOS e Apache 2.4. Se si imposta Vernice in un ambiente diverso, alcuni comandi potrebbero essere diversi. Per ulteriori informazioni, consulta la documentazione sulle vernici.


## Problemi noti

Conosciamo i seguenti problemi di vernice:

- [La vernice non supporta SSL]

   In alternativa, utilizza la terminazione SSL o un proxy di terminazione SSL.

- Se si elimina manualmente il contenuto del `<magento_root>/var/cache` directory, è necessario riavviare Varnish.

- Possibile errore durante l’installazione di Commerce:

   ```terminal
   Error 503 Service Unavailable
   Service Unavailable
   XID: 303394517
   Varnish cache server
   ```

   Se si verifica questo errore, modificare `default.vcl` e aggiungi un timeout al `backend` strofa come segue:

   ```conf
   backend default {
       .host = "127.0.0.1";
       .port = "8080";
       .first_byte_timeout = 600s;
   }
   ```

## Panoramica del caching di Varnish

Il caching delle vernici funziona con Commerce utilizzando:

- [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) dall’archivio GitHub Magento 2
- `.htaccess` file di configurazione distribuito per Apache fornito con Commerce
- `default.vcl` per la vernice generata utilizzando [Amministratore](../cache/configure-varnish-commerce.md)

>[!INFO]
In questo argomento vengono illustrate solo le opzioni predefinite dell&#39;elenco precedente. Esistono molti altri modi per configurare il caching in scenari complessi (ad esempio, utilizzando una rete per la distribuzione di contenuti); tali metodi vanno oltre l’ambito di questa guida.

Alla prima richiesta del browser, le risorse memorizzabili in cache vengono consegnate al browser client da Microsoft e memorizzate nella cache del browser.

Inoltre, per le risorse statiche viene utilizzato un tag di entità (ETag). ETag consente di determinare quando i file statici cambiano sul server. Di conseguenza, le risorse statiche vengono inviate al client quando cambiano sul server, su nuova richiesta di un browser o quando il client aggiorna la cache del browser, in genere premendo F5 o Ctrl+F5.

Ulteriori dettagli sono forniti nelle sezioni seguenti.

## Memorizzazione in cache per richiesta browser

Questa sezione utilizza un controllo browser per mostrare come le risorse vengono consegnate al browser nella prima richiesta e successivamente caricate dalla cache locale del browser.

### Prima richiesta browser

`nginx.conf.sample` e `.htaccess` fornisce opzioni per il caching client. Quando la prima richiesta viene effettuata da un browser per un oggetto memorizzabile in cache, vernice lo consegna al client.

Nella figura seguente viene illustrato un esempio relativo all&#39;utilizzo di un controllo browser:

![La prima volta che viene effettuata una richiesta per un oggetto memorizzabile in cache, Varnish lo consegna al browser](../../assets/configuration/varnish-apache-first-visit.png)

L&#39;esempio precedente mostra una richiesta per la pagina principale storefront (`m2_ce_my`). Le risorse CSS e JavaScript sono memorizzate nella cache del browser client.

>[!NOTE]
La maggior parte delle risorse statiche ha un codice di stato HTTP 200 (OK), che indica che la risorsa è stata recuperata dal server.

### Seconda richiesta browser

Se lo stesso browser richiede nuovamente la stessa pagina, queste risorse vengono distribuite dalla cache del browser locale, come illustrato nella figura seguente.

![Alla successiva richiesta dello stesso oggetto, le risorse vengono caricate dalla cache del browser locale](../../assets/configuration/varnish-apache-second-visit.png)

Nota la differenza di tempo di risposta tra la prima e la seconda richiesta. Anche in questo caso, le risorse statiche hanno un codice di risposta 200 (OK) perché vengono consegnate dalla cache locale per la prima volta.

## Utilizzo di Etag in Commerce

L’esempio seguente mostra le intestazioni di risposta per una particolare risorsa statica.

![ETag consente di determinare più facilmente se una risorsa statica è stata modificata o meno](../../assets/configuration/varnish-etag.png)

`calendar.css` dispone di un’intestazione di risposta ETag, il che significa che il file CSS sul browser client può essere confrontato con quello sul server.

Inoltre, le risorse statiche vengono restituite con un codice di stato HTTP 304 (Non modificato), come illustrato nella figura seguente.

![Il codice di risposta HTTP 304 (Non modificato) indica che la risorsa statica nella cache locale è la stessa del server](../../assets/configuration/varnish-304.png)

Il codice di stato 304 si verifica perché l’utente ha invalidato la cache locale e il contenuto sul server non è cambiato. A causa del codice di stato 304, la risorsa statica _contenuto_ non viene trasferito; solo le intestazioni HTTP vengono scaricate nel browser.

Se il contenuto cambia sul server, il client scarica la risorsa statica con un codice di stato HTTP 200 (OK) e un nuovo ETag.

<!-- Link Definitions -->

[database]: https://developer.adobe.com/commerce/php/development/cache/partial/database-caching/
[Il quadro vernice grande]: https://www.varnish-cache.org/docs/trunk/users-guide/intro.html
[Cache vernice]: https://varnish-cache.org
[Opzioni di avvio vernice]: https://www.varnish-cache.org/docs/trunk/reference/varnishd.html#ref-varnishd-options
[Vernice e prestazioni del sito web]: https://www.varnish-cache.org/docs/trunk/users-guide/performance.html#users-performance
[La vernice non supporta SSL]: https://www.varnish-cache.org/docs/3.0/phk/ssl.html
