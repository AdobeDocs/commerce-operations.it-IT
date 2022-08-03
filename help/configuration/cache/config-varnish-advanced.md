---
title: Configurazione avanzata della vernice
description: Configura le funzioni avanzate della vernice, incluse le modalità di controllo dello stato, grazia e saint.
source-git-commit: bda758381d8d1b9209110adb168c36e1d504c4fa
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 0%

---


# Configurazione avanzata della vernice

Varnish offre diverse funzioni che impediscono ai clienti di riscontrare ritardi e timeout lunghi quando il server Commerce non funziona correttamente. Queste funzioni possono essere configurate nel `default.vcl` file. Questo argomento descrive le aggiunte fornite da Commerce nel file VCL (Varnish Configuration Language) scaricato dall’amministratore.

Consulta la sezione [Manuale di riferimento vernice](https://varnish-cache.org/docs/6.3/reference/index.html) per informazioni dettagliate sull&#39;utilizzo di Varnish Configuration Language.

## Verifica dello stato

La funzione di controllo dello stato di vernice controlla il server Commerce per determinare se sta rispondendo in modo tempestivo. Se risponde normalmente, il contenuto fresco viene rigenerato dopo la scadenza del periodo Time to Live (TTL). In caso contrario, Varnish indica sempre il contenuto non aggiornato.

Commerce definisce il seguente controllo di integrità predefinito:

```conf
.probe = {
    .url = "/pub/health_check.php";
    .timeout = 2s;
    .interval = 5s;
    .window = 10;
    .threshold = 5;
    }
```

Ogni 5 secondi, questo controllo dello stato di salute chiama il `pub/health_check.php` script. Questo script controlla la disponibilità del server, di ciascun database e di Redis (se installato). Lo script deve restituire una risposta entro 2 secondi. Se lo script determina che una di queste risorse è inattiva, restituisce un codice di errore HTTP 500. Se questo codice di errore viene ricevuto in sei tentativi su dieci, la [backend](https://glossary.magento.com/backend) è considerato malsano.

La `health_check.php` lo script si trova nel `pub` directory. Se la directory principale Commerce è `pub`, quindi assicurati di modificare il percorso nel `url` parametro da `/pub/health_check.php` a `health_check.php`.

Per ulteriori informazioni, consulta la sezione [Controlli sanitari in vernice](https://varnish-cache.org/docs/6.3/users-guide/vcl-backends.html?highlight=health%20check#health-checks) documentazione.

## Modalità Grace

La modalità Grace consente a Varnish di mantenere un oggetto [cache](https://glossary.magento.com/cache) oltre il valore TTL. Varnish può quindi servire il contenuto scaduto (obsoleto) mentre recupera una nuova versione. Ciò migliora il flusso di traffico e diminuisce i tempi di caricamento. Viene utilizzato nelle situazioni seguenti:

- Quando il backend Commerce è integro, ma una richiesta richiede più tempo del normale
- Quando il back-end Commerce non è integro.

La `vcl_hit` la subroutine definisce il modo in cui Varnish risponde a una richiesta di oggetti che sono stati memorizzati nella cache.

### Quando il back-end Commerce è sano

Quando i controlli di integrità determinano che il backend Commerce è sano, Varnish controlla se il tempo rimane nel periodo di tolleranza. Il periodo di tolleranza predefinito è di 300 secondi, ma un esercente può impostare il valore dal [Amministratore](https://glossary.magento.com/admin) come descritto in [Configurare Commerce per utilizzare Varnish](config-varnish-magento.md). Se il periodo di tolleranza non è scaduto, Varnish consegna il contenuto non aggiornato e aggiorna l’oggetto in modo asincrono dal server Commerce. Se il periodo di tolleranza è scaduto, Varnish utilizza il contenuto non aggiornato e aggiorna in modo sincrono l’oggetto dal back-end Commerce.

La quantità massima di tempo utilizzata da Varnish per un oggetto obsoleto è la somma del periodo di tolleranza (300 secondi per impostazione predefinita) e del valore TTL (86400 secondi per impostazione predefinita).

Per modificare il periodo di tolleranza predefinito da `default.vcl` modifica la riga seguente nel `vcl_hit` subroutine:

```conf
if (obj.ttl + 300s > 0s) {
```

### Quando il backend Commerce non è integro

Se il back-end Commerce non è reattivo, Varnish utilizza il contenuto non aggiornato dalla cache per tre giorni (o come definito in `beresp.grace`) più il TTL rimanente (che per impostazione predefinita è un giorno), a meno che il contenuto nella cache non venga eliminato manualmente.

## Modalità Saint

La modalità Saint esclude i backend non integri per un periodo di tempo configurabile. Di conseguenza, i backend non integri non possono servire il traffico quando si utilizza Varnish come load balancer. La modalità Saint può essere utilizzata con la modalità di tolleranza per consentire la gestione complessa di server back-end non integri. Ad esempio, se un server di backend non è integro, è possibile indirizzare i nuovi tentativi a un altro server. Se tutti gli altri server sono inattivi, vengono utilizzati oggetti non aggiornati nella cache. Gli host di backend e i periodi di blackout in modalità saint sono definiti nella `default.vcl` file.

La modalità Saint può essere utilizzata anche quando le istanze Commerce vengono portate offline singolarmente per eseguire attività di manutenzione e aggiornamento senza influire sulla disponibilità del sito Commerce.

### Prerequisiti per la modalità Saint

Designare una macchina come installazione primaria. In questo computer, installare l&#39;istanza principale di Commerce, il database mySQL e Varnish.

Su tutti gli altri computer, l&#39;istanza Commerce deve avere accesso al database mySQL del computer primario. I computer secondari devono avere accesso anche ai file dell&#39;istanza Commerce principale.

In alternativa, [file statici](https://glossary.magento.com/static-files) il controllo delle versioni può essere disattivato su tutte le macchine. È accessibile dall’amministratore in **Negozi** > Impostazioni > **Configurazione** > **Avanzate** > **Sviluppatore** > **Impostazioni dei file statici** > **Firma di file statici** = **No**.

Infine, tutte le istanze Commerce devono essere in modalità di produzione. Prima che Varnish inizi, cancella la cache su ogni istanza. Nell&#39;Admin, vai a **Sistema** > Strumenti > **Gestione cache** e fai clic su **Svuotare la cache del Magento**. Puoi anche eseguire il seguente comando per cancellare la cache:

```bash
bin/magento cache:flush
```

### Installazione

La modalità Saint non fa parte del pacchetto principale Varnish. È una versione separata `vmod` deve essere scaricato e installato. Di conseguenza, è necessario ricompilare Varnish dalla fonte, come descritto nei seguenti articoli:

- [Installazione di Varnish 6.4](https://varnish-cache.org/docs/6.4/installation/install.html)
- [Installazione di Varnish 6.0](https://varnish-cache.org/docs/6.0/installation/install.html) (LTS)

Dopo la ricompilazione, è possibile installare la modalità Saint [modulo](https://glossary.magento.com/module). In generale, segui questi passaggi:

1. Ottieni il codice sorgente da [Moduli di vernice](https://github.com/varnish/varnish-modules). Clona la versione Git (versione master) poiché le versioni 0.9.x contengono un errore del codice sorgente.
1. Crea il codice sorgente con gli strumenti automatici:

   ```bash
   sudo apt-get install libvarnishapi-dev || sudo yum install varnish-libs-devel
   ./bootstrap   # If running from git.
   ./configure
   make
   make check   # optional
   sudo make install
   ```

Vedi [Raccolta moduli vernici](https://github.com/varnish/varnish-modules) per informazioni sull&#39;installazione del modulo di modalità Saint.

### File VCL di esempio

L&#39;esempio di codice seguente mostra il codice che deve essere aggiunto al file VCL per abilitare la modalità saint. Posiziona il `import` dichiarazioni `backend` definizioni nella parte superiore del file.

```cpp
import saintmode;
import directors;

backend default1 {
    .host = "192.168.0.1";
    .port = "8080";
    .first_byte_timeout = 600s;
    .probe = {
        .url = "/pub/health_check.php";
        .timeout = 2s;
        .interval = 5s;
        .window = 10;
        .threshold = 5;
    }
}

backend default2 {
    .host = "192.168.0.2";
    .port = "8080";
    .first_byte_timeout = 600s;
    .probe = {
        .url = "/pub/health_check.php";
        .timeout = 2s;
        .interval = 5s;
        .window = 10;
        .threshold = 5;
    }
}

sub vcl_init {
    # Instantiate sm1, sm2 for backends tile1, tile2
    # with 10 blacklisted objects as the threshold for marking the
    # whole backend sick.
    new sm1 = saintmode.saintmode(default1, 10);
    new sm2 = saintmode.saintmode(default2, 10);

    # Add both to a director. Use sm0, sm1 in place of tile1, tile2.
    # Other director types can be used in place of random.
    new magedirector = directors.random();
    magedirector.add_backend(sm1.backend(), 1);
    magedirector.add_backend(sm2.backend(), 1);
}

sub vcl_backend_fetch {
    # Get a backend from the director.
    # When returning a backend, the director will only return backends
    # saintmode says are healthy.
    set bereq.backend = magedirector.backend();
}

sub vcl_backend_response {
    if (beresp.status >= 500) {
        # This marks the backend as sick for this specific
        # object for the next 20s.
        saintmode.blacklist(20s);
        # Retry the request. This will result in a different backend
        # being used.
        return (retry);
    }
}
```
