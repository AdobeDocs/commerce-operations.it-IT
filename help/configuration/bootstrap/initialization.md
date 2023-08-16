---
title: Inizializzazione e avvio dell'applicazione
description: Informazioni sull’inizializzazione e la logica di avvio per l’applicazione Commerce.
feature: Configuration, Install, Media
exl-id: 46d1ffc0-7870-4dd1-beec-0a9ff858ab62
source-git-commit: 403a5937561d82b02fd126c95af3f70b0ded0747
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---

# Panoramica dell&#39;inizializzazione e dell&#39;avvio

Per eseguire l’applicazione Commerce, in sono implementate le seguenti azioni [pub/index.php][index]:

- Includi [app/bootstrap.php][bootinitial], che esegue routine di inizializzazione essenziali come la gestione degli errori, l&#39;inizializzazione dell&#39;autoloader, l&#39;impostazione delle opzioni di profilatura e l&#39;impostazione del fuso orario predefinito.
- Crea un&#39;istanza di [\Magento\Framework\App\Bootstrap.php][bootstrap] <!-- It requires initialization parameters to be specified in constructor. Normally, the $_SERVER super-global variable is supposed to be passed there. -->
- Creare un’istanza dell’applicazione Commerce: [\Magento\Framework\AppInterface][app-face]
- Eseguire Commerce

## Bootstrap logica di esecuzione

[Oggetto bootstrap][bootinitial] utilizza il seguente algoritmo per eseguire l’applicazione Commerce:

1. Inizializza il gestore degli errori.
1. Crea il [gestione oggetti][object] e servizi condivisi di base utilizzati ovunque e influenzati dall&#39;ambiente. I parametri dell’ambiente vengono inseriti correttamente in questi oggetti.
1. Asserisce che la modalità di manutenzione è _non_ abilitato; in caso contrario, termina.
1. Asserisce che l’applicazione Commerce è installata; in caso contrario, termina.
1. Avvia l’applicazione Commerce.

   Eventuali eccezioni non rilevate durante l’avvio dell’applicazione vengono trasmesse automaticamente a Commerce in `catchException()` metodo che è possibile utilizzare per gestire l&#39;eccezione. Quest&#39;ultimo deve restituire: `true` o `false`:

   - Se `true`: eccezione gestita correttamente da Commerce. Non c&#39;è bisogno di fare altro.
   - Se `false`: (o qualsiasi altro risultato vuoto) Commerce non ha gestito l’eccezione. L&#39;oggetto bootstrap esegue la subroutine predefinita per la gestione delle eccezioni.

1. Invia la risposta fornita dall&#39;oggetto applicativo.

   >[!INFO]
   >
   >L’asserzione che l’applicazione Commerce è installata e non in modalità di manutenzione è il comportamento predefinito del `\Magento\Framework\App\Bootstrap` classe. È possibile modificarlo utilizzando uno script del punto di ingresso durante la creazione dell&#39;oggetto bootstrap.

   Script di esempio del punto di ingresso che modifica l&#39;oggetto bootstrap:

   ```php
   <?php
   use Magento\Framework\App\Bootstrap;
   require __DIR__ . '/app/bootstrap.php';
   
   $params = $_SERVER;
   $params[Bootstrap::PARAM_REQUIRE_MAINTENANCE] = true; // default false
   $params[Bootstrap::PARAM_REQUIRE_IS_INSTALLED] = false; // default true
   $bootstrap = Bootstrap::create(BP, $params);
   
   /** @var \Magento\Framework\App\Http $app */
   $app = $bootstrap->createApplication('Magento\Framework\App\Http');
   $bootstrap->run($app);
   ```

## Gestione eccezioni predefinita

L&#39;oggetto bootstrap specifica il modo in cui l&#39;applicazione Commerce gestisce le eccezioni non rilevate nel modo seguente:

- In entrata [modalità sviluppatore](../bootstrap/application-modes.md#developer-mode), visualizza l&#39;eccezione così com&#39;è.
- In qualsiasi altra modalità, tenta di registrare un’eccezione e di visualizzare un messaggio di errore generico.
- Termina Commerce con codice di errore `1`

## Applicazioni entry-point

Abbiamo le seguenti applicazioni del punto di ingresso (ovvero, applicazioni definite da Commerce e utilizzate dal server web come indice di directory):

### Punto di ingresso HTTP

[\Magento\Framework\App\Http][http] funziona come segue:

1. Determina la [area di applicazione](https://developer.adobe.com/commerce/php/architecture/modules/areas/).
1. Avvia il controller anteriore e i sistemi di routing per individuare ed eseguire un&#39;azione del controller.
1. Utilizza un oggetto di risposta HTTP per restituire il risultato ottenuto dall’azione del controller.
1. Gestione degli errori (nell’ordine di priorità seguente):

   1. Se sta usando [modalità sviluppatore](../bootstrap/application-modes.md#developer-mode):
      - Se l&#39;applicazione Commerce non è installata, reindirizzare all&#39;Installazione guidata.
      - Se l’applicazione Commerce è installata, visualizza un errore e il codice di stato HTTP 500 (Errore interno del server).
   1. Se l’applicazione Commerce è in modalità manutenzione, visualizza una pagina di destinazione intuitiva &quot;Servizio non disponibile&quot; con codice di stato HTTP 503 (Servizio non disponibile).
   1. Se l’applicazione Commerce è _non_ installato, reindirizzare all&#39;Installazione guidata.
   1. Se la sessione non è valida, reindirizzare alla home page.
   1. In caso di altri errori di inizializzazione dell&#39;applicazione, visualizzare una pagina intuitiva denominata &quot;Pagina non trovata&quot; con codice di stato HTTP 404 (non trovato).
   1. In caso di altri errori, visualizza una pagina semplice di &quot;Servizio non disponibile&quot; con la risposta HTTP 503, genera un rapporto di errore e visualizza il relativo ID sulla pagina.

### Punto di ingresso risorsa statica

[\Magento\Framework\App\StaticResource][static-resource] è un’applicazione per il recupero di risorse statiche (ad esempio, CSS, JavaScript e immagini). Posticipa qualsiasi azione con una risorsa statica fino a quando la risorsa non viene richiesta.

>[!INFO]
>
>Il punto di ingresso per i file di visualizzazione statica non viene utilizzato in [modalità di produzione](application-modes.md#production-mode) per evitare potenziali exploit sul server. In modalità di produzione, l’applicazione Commerce si aspetta che siano presenti tutte le risorse necessarie nel `<your Commerce install dir>/pub/static` directory.

In modalità predefinita o sviluppatore, una richiesta per una risorsa statica inesistente viene reindirizzata al punto di ingresso statico in base alle regole di riscrittura specificate dalla `.htaccess`.
Quando la richiesta viene reindirizzata al punto di ingresso, l’applicazione Commerce analizza l’URL richiesto in base ai parametri recuperati e trova la risorsa richiesta.

- In entrata [sviluppatore](application-modes.md#developer-mode) in modo che, ogni volta che la risorsa viene richiesta, il contenuto restituito sia aggiornato.
- In entrata [predefinito](application-modes.md#default-mode) In questa modalità, la risorsa recuperata viene pubblicata in modo che sia accessibile dall’URL richiesto in precedenza.

  Tutte le richieste future per la risorsa statica vengono elaborate dal server allo stesso modo dei file statici, ovvero senza coinvolgere il punto di ingresso. Se è necessario sincronizzare i file pubblicati con quelli originali, il `pub/static` La directory deve essere rimossa; di conseguenza, i file vengono ripubblicati automaticamente con la richiesta successiva.

### Punto di ingresso risorse multimediali

[Magento\MediaStorage\App\Media][media] recupera dal database le risorse multimediali, ovvero tutti i file caricati nell&#39;archivio multimediale. Viene utilizzato ogni volta che il database viene configurato come archivio multimediale.

`\Magento\Core\App\Media` tenta di trovare il file multimediale nell’archivio del database configurato e di scriverlo nell’archivio `pub/static` , quindi restituirne il contenuto. In caso di errore, restituisce un codice di stato HTTP 404 (Non trovato) nell’intestazione senza contenuto.

<!-- Link Definitions -->

[app-face]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/AppInterface.php
[bootinitial]: https://github.com/magento/magento2/tree/2.4/app/bootstrap.php
[bootstrap]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Bootstrap.php
[http]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Http
[index]: https://github.com/magento/magento2/tree/2.4/pub/index.php
[media]: https://github.com/magento/magento2/tree/2.4/app/code/Magento/MediaStorage/App/Media.php
[object]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/ObjectManager
[static-resource]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/StaticResource.php
