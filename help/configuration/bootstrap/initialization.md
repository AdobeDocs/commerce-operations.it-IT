---
title: Inizializzazione dell'applicazione e avvio
description: Informazioni sull'inizializzazione e la logica di avvio per l'applicazione Commerce.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '863'
ht-degree: 0%

---


# Panoramica dell&#39;inizializzazione e del bootstrap

Per eseguire l’applicazione Commerce, le azioni seguenti sono implementate in [pub/index.php][index]:

- Includi [app/bootstrap.php][bootinitial], che esegue routine di inizializzazione essenziali, come la gestione degli errori, l’inizializzazione dell’autoloader, l’impostazione delle opzioni di profiling e l’impostazione del fuso orario predefinito.
- Crea un&#39;istanza di [\Magento\Framework\App\Bootstrap.php][bootstrap] <!-- It requires initialization parameters to be specified in constructor. Normally, the $_SERVER super-global variable is supposed to be passed there. -->
- Crea un&#39;istanza di applicazione Commerce: [\Magento\Framework\AppInterface][app-face]
- Esegui Commerce

## Bootstrap logica di esecuzione

[Oggetto bootstrap][bootinitial] utilizza il seguente algoritmo per eseguire l’applicazione Commerce:

1. Inizializza il gestore di errori.
1. Crea la [gestore di oggetti][object] e servizi condivisi di base utilizzati ovunque e colpiti dall&#39;ambiente. I parametri dell’ambiente vengono inseriti correttamente in questi oggetti.
1. Indica che la modalità di manutenzione è _not_ attivato; in caso contrario, termina.
1. afferma che l&#39;applicazione Commerce è installata; in caso contrario, termina.
1. Avvia l&#39;applicazione Commerce.

   Qualsiasi eccezione non rilevata durante l&#39;avvio dell&#39;applicazione viene automaticamente restituita a Commerce nel `catchException()` metodo che è possibile utilizzare per gestire l&#39;eccezione. Quest&#39;ultimo deve restituire `true` o `false`:

   - Se `true`: Eccezione gestita da Commerce. Non c&#39;è bisogno di fare altro.
   - Se `false`: (o qualsiasi altro risultato vuoto) Commerce non ha gestito l&#39;eccezione. L&#39;oggetto bootstrap esegue la subroutine di gestione delle eccezioni predefinita.

1. Invia la risposta fornita dall&#39;oggetto application.

   >[!INFO]
   >
   >Le asserzioni che l’applicazione Commerce è installata e non in modalità di manutenzione sono il comportamento predefinito del `\Magento\Framework\App\Bootstrap` classe. È possibile modificarlo utilizzando uno script del punto di ingresso durante la creazione dell&#39;oggetto bootstrap.

   Esempio di script del punto di ingresso che modifica l&#39;oggetto bootstrap:

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

## Gestione delle eccezioni predefinita

L&#39;oggetto bootstrap specifica come l&#39;applicazione Commerce gestisce le eccezioni non rilevate come segue:

- In [modalità sviluppatore](../bootstrap/application-modes.md#developer-mode), visualizza l&#39;eccezione così com&#39;è.
- In qualsiasi altra modalità, tenta di registrare l&#39;eccezione e visualizzare un messaggio di errore generico.
- Termina Commerce con codice di errore `1`

## Applicazioni punto di ingresso

Abbiamo le seguenti applicazioni punto di ingresso (cioè, applicazioni definite da Commerce che vengono utilizzate dal server web come indice di directory):

### punto di ingresso HTTP

[\Magento\Framework\App\Http][http] funziona come segue:

1. Determina la [area di applicazione](https://developer.adobe.com/commerce/php/architecture/modules/areas/).
1. Avvia il controller anteriore e i sistemi di routing per trovare ed eseguire un&#39;azione del controller.
1. Utilizza un oggetto di risposta HTTP per restituire il risultato ottenuto dall&#39;azione del controller.
1. Gestione degli errori (nell’ordine di priorità seguente):

   1. Se utilizzi [modalità sviluppatore](../bootstrap/application-modes.md#developer-mode):
      - Se l&#39;applicazione Commerce non è installata, reindirizzare a Configurazione guidata.
      - Se l’applicazione Commerce è installata, visualizza un errore e il codice di stato HTTP 500 (Errore interno del server).
   1. Se l’applicazione Commerce è in modalità di manutenzione, visualizza una pagina di destinazione &quot;Servizio non disponibile&quot; di facile utilizzo con codice di stato HTTP 503 (Servizio non disponibile).
   1. Se l’applicazione Commerce è _not_ installato, reindirizzare a Configurazione guidata.
   1. Se la sessione non è valida, reindirizzare alla home page.
   1. Se si verifica un altro errore di inizializzazione dell&#39;applicazione, visualizza una pagina &quot;Pagina non trovata&quot; facile da usare con il codice di stato HTTP 404 (Non trovato).
   1. In caso di altri errori, visualizza una pagina &quot;Servizio non disponibile&quot; facile da usare con risposta HTTP 503 e genera un rapporto di errore e visualizza il relativo ID sulla pagina.

### Punto di ingresso della risorsa statico

[\Magento\Framework\App\StaticResource][static-resource] è un’applicazione per il recupero di risorse statiche (ad esempio CSS, JavaScript e immagini). Rinvia le azioni con una risorsa statica fino a quando la risorsa non viene richiesta.

>[!INFO]
>
>Il punto di ingresso per i file di visualizzazione statica non viene utilizzato in [modalità di produzione](application-modes.md#production-mode) per evitare potenziali utilizzi sul server. In modalità di produzione, l’applicazione Commerce prevede l’esistenza di tutte le risorse necessarie nel `<your Commerce install dir>/pub/static` directory.

In modalità predefinita o sviluppatore, una richiesta di una risorsa statica inesistente viene reindirizzata al punto di ingresso statico in base alle regole di riscrittura specificate dall’appropriata `.htaccess`.
Quando la richiesta viene reindirizzata al punto di ingresso, l’applicazione Commerce analizza l’URL richiesto in base ai parametri recuperati e trova la risorsa richiesta.

- In [sviluppatore](application-modes.md#developer-mode) In modalità , il contenuto del file viene restituito in modo che ogni volta che la risorsa viene richiesta, il contenuto restituito sia aggiornato.
- In [default](application-modes.md#default-mode) la risorsa recuperata viene pubblicata in modo che sia accessibile dall’URL richiesto in precedenza.

   Tutte le richieste future per la risorsa statica vengono elaborate dal server allo stesso modo dei file statici; cioè senza coinvolgere il punto di ingresso. Se è necessario sincronizzare i file pubblicati con quelli originali, il `pub/static` la directory deve essere rimossa; di conseguenza, i file vengono ripubblicati automaticamente con la richiesta successiva.

### Punto di ingresso della risorsa multimediale

[Magento\MediaStorage\App\Media][media] recupera dal database le risorse multimediali (ovvero tutti i file caricati nell&#39;archiviazione multimediale). Viene utilizzato ogni volta che il database viene configurato come archiviazione multimediale.

`\Magento\Core\App\Media` tenta di trovare il file multimediale nell&#39;archivio del database configurato e scriverlo nell&#39;archivio `pub/static` quindi restituirne il contenuto. In caso di errore, restituisce un codice di stato HTTP 404 (Non trovato) nell&#39;intestazione senza contenuto.

<!-- Link Definitions -->

[app-face]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/AppInterface.php
[bootinitial]: https://github.com/magento/magento2/tree/2.4/app/bootstrap.php
[bootstrap]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Bootstrap.php
[http]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/Http
[index]: https://github.com/magento/magento2/tree/2.4/pub/index.php
[media]: https://github.com/magento/magento2/tree/2.4/app/code/Magento/MediaStorage/App/Media.php
[object]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/ObjectManager
[static-resource]: https://github.com/magento/magento2/tree/2.4/lib/internal/Magento/Framework/App/StaticResource.php
