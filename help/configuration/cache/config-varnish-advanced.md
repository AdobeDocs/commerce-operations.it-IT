---
title: Configurazione vernice avanzata
description: Configura le funzioni avanzate di vernice, tra cui le modalità di controllo dello stato di salute, grazia e santo.
feature: Configuration, Cache
exl-id: 178bd675-6ed0-40cc-9455-08a11b32c054
source-git-commit: ec3ab7e3c6c3835e73653b0d4f74aadc861016d3
workflow-type: tm+mt
source-wordcount: '871'
ht-degree: 0%

---

# Configurazione vernice avanzata

Vernice offre diverse funzioni che impediscono ai clienti di riscontrare lunghi ritardi e timeout quando il server Commerce non funziona correttamente. Queste funzionalità possono essere configurate nel file `default.vcl`. In questo argomento vengono descritte le aggiunte fornite da Commerce nel file VCL (Vernice Configuration Language) scaricato dall&#39;amministratore.

Per informazioni dettagliate sull&#39;utilizzo del linguaggio di configurazione vernice, vedere il [manuale di riferimento vernice](https://varnish-cache.org/docs/index.html).

## Verifica stato

La funzione di controllo dello stato di vernice esegue un polling nel server Commerce per determinare se sta rispondendo in modo tempestivo. Se risponde normalmente, il contenuto fresco viene rigenerato dopo la scadenza del periodo Time to Live (TTL). In caso contrario, vernice fornisce sempre contenuti non aggiornati.

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

Ogni 5 secondi, questo controllo di integrità chiama lo script `pub/health_check.php`. Questo script controlla la disponibilità del server, di ogni database e di Redis (se installato). Lo script deve restituire una risposta entro 2 secondi. Se lo script determina che una di queste risorse non è disponibile, restituisce un codice di errore HTTP 500. Se questo codice di errore viene ricevuto in sei tentativi su dieci, il backend viene considerato non integro.

Lo script `health_check.php` si trova nella directory `pub`. Se la directory principale di Commerce è `pub`, assicurarsi di cambiare il percorso nel parametro `url` da `/pub/health_check.php` a `health_check.php`.

Per ulteriori informazioni, consulta la documentazione sui [controlli di integrità della vernice](https://varnish-cache.org/docs/7.4/users-guide/vcl-backends.html#health-checks).

## Modalità di tolleranza

La modalità di tolleranza consente a Varnish di mantenere un oggetto nella cache oltre il suo valore TTL. La vernice può quindi fornire il contenuto scaduto (non aggiornato) mentre recupera una nuova versione. Questo migliora il flusso del traffico e riduce i tempi di caricamento. Viene utilizzato nelle seguenti situazioni:

- Quando il backend Commerce è integro, ma una richiesta richiede più tempo del normale
- Quando il backend Commerce non è integro.

La subroutine `vcl_hit` definisce il modo in cui Vernice risponde a una richiesta per gli oggetti che sono stati memorizzati nella cache.

### Quando il backend Commerce è integro

Quando i controlli di integrità determinano che il backend di Commerce è integro, Vernice controlla se il tempo rimane nel periodo di tolleranza. Il periodo di tolleranza predefinito è di 300 secondi, ma un commerciante può impostare il valore dall&#39;amministratore come descritto in [Configurare Commerce per l&#39;utilizzo di vernice](configure-varnish-commerce.md). Se il periodo di tolleranza non è scaduto, Vernice distribuisce il contenuto non aggiornato e aggiorna l&#39;oggetto in modo asincrono dal server Commerce. Se il periodo di tolleranza è scaduto, Vernice fornisce il contenuto non aggiornato e aggiorna in modo sincrono l&#39;oggetto dal backend di Commerce.

Il periodo di tempo massimo per il quale Vernice fornisce un oggetto non aggiornato è la somma del periodo di tolleranza (300 secondi per impostazione predefinita) e del valore TTL (86400 secondi per impostazione predefinita).

Per modificare il periodo di tolleranza predefinito dall&#39;interno del file `default.vcl`, modificare la riga seguente nella subroutine `vcl_hit`:

```conf
if (obj.ttl + 300s > 0s) {
```

### Quando il backend Commerce non è integro

Se il backend di Commerce non risponde, Vernice fornisce contenuto non aggiornato dalla cache per tre giorni (o come definito in `beresp.grace`) più il TTL rimanente (che per impostazione predefinita è di un giorno), a meno che il contenuto memorizzato nella cache non venga eliminato manualmente.

## Modalità Saint

La modalità Saint esclude i backend non integri per un periodo di tempo configurabile. Di conseguenza, i backend non integri non possono servire il traffico quando si utilizza Vernice come load balancer. La modalità Saint può essere utilizzata con la modalità grace per consentire una gestione complessa di server back-end non integri. Ad esempio, se un server back-end non è integro, i nuovi tentativi possono essere instradati a un altro server. Se tutti gli altri server non sono attivi, distribuire oggetti memorizzati nella cache non aggiornati. Gli host back-end in modalità saint e i periodi di sospensione attività sono definiti nel file `default.vcl`.

La modalità Saint può essere utilizzata anche quando le istanze di Commerce vengono portate offline singolarmente per eseguire attività di manutenzione e aggiornamento senza influire sulla disponibilità del sito Commerce.

### Prerequisiti per la modalità Saint

Designare un computer come installazione principale. Su questo computer installare l&#39;istanza principale di Commerce, del database mySQL e di Vernice.

Su tutti gli altri computer, l&#39;istanza di Commerce deve avere accesso al database mySQL del computer primario. Anche i computer secondari devono avere accesso ai file dell&#39;istanza Commerce primaria.

In alternativa, il controllo delle versioni dei file statici può essere disattivato su tutti i computer. È possibile accedervi dall&#39;amministratore in **Archivi** > Impostazioni > **Configurazione** > **Avanzate** > **Sviluppo** > **Impostazioni file statici** > **Firma file statici** = **No**.

Infine, tutte le istanze di Commerce devono essere in modalità di produzione. Prima dell&#39;avvio di Vernice, cancellare la cache su ogni istanza. In Amministrazione, vai a **Sistema** > Strumenti > **Gestione cache** e fai clic su **Svuota cache Magento**. Per cancellare la cache, puoi anche eseguire il seguente comando:

```bash
bin/magento cache:flush
```

### Installazione

La modalità Saint non fa parte del pacchetto principale di vernice. Si tratta di un `vmod` con versione separata che deve essere scaricato e installato. Di conseguenza, è necessario ricompilare la vernice dall&#39;origine, come descritto nelle [istruzioni di installazione](https://varnish-cache.org/docs/index.html) per la versione di Vernice in uso.

Dopo la ricompilazione, è possibile installare il modulo modalità Saint. In generale, segui questi passaggi:

1. Ottieni il codice sorgente da [moduli vernice](https://github.com/varnish/varnish-modules). Clona la versione Git (versione master) poiché le versioni 0.9.x contengono un errore del codice sorgente.
1. Crea il codice sorgente con gli strumenti automatici:

   ```bash
   sudo apt-get install libvarnishapi-dev || sudo yum install varnish-libs-devel
   ./bootstrap   # If running from git.
   ./configure
   make
   make check   # optional
   sudo make install
   ```

Per informazioni sull&#39;installazione del modulo Saint mode, vedere [Raccolta moduli di vernice](https://github.com/varnish/varnish-modules).

### File VCL di esempio

Nell&#39;esempio di codice riportato di seguito viene illustrato il codice che deve essere aggiunto al file VCL per attivare la modalità saint. Posiziona le istruzioni `import` e le definizioni `backend` nella parte superiore del file.

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
