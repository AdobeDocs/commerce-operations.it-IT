---
title: Inizializzazione e avvio dell'applicazione
description: Informazioni sull'inizializzazione e la logica di avvio per l'applicazione Commerce.
feature: Configuration, Install, Media
exl-id: 46d1ffc0-7870-4dd1-beec-0a9ff858ab62
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '804'
ht-degree: 0%

---

# Panoramica dell&#39;inizializzazione e dell&#39;avvio

Per eseguire l&#39;applicazione Commerce, le azioni seguenti sono implementate in [pub/index.php](https://github.com/magento/magento2/tree/2.4.8/pub/index.php):

- Includi il file [app/bootstrap.php](https://github.com/magento/magento2/blob/2.4.8/app/bootstrap.php) per la versione di Commerce distribuita nell&#39;ambiente. Questo file esegue routine di inizializzazione essenziali, ad esempio la gestione degli errori, l&#39;inizializzazione del caricatore automatico, l&#39;impostazione delle opzioni di profilatura e l&#39;impostazione del fuso orario predefinito.
- Crea un&#39;istanza di [\Magento\Framework\App\Bootstrap.php](https://github.com/magento/magento2/tree/2.4.8/lib/internal/Magento/Framework/App/Bootstrap.php) <!-- It requires initialization parameters to be specified in constructor. Normally, the $_SERVER super-global variable is supposed to be passed there. -->
- Crea un&#39;istanza dell&#39;applicazione Commerce: [\Magento\Framework\AppInterface](https://github.com/magento/magento2/tree/2.4.8/lib/internal/Magento/Framework/AppInterface.php)
- Esegui Commerce

## Logica di esecuzione Bootstrap

[L&#39;oggetto bootstrap](https://github.com/magento/magento2/tree/2.4.8/app/bootstrap.php) utilizza il seguente algoritmo per eseguire l&#39;applicazione Commerce:

1. Inizializza il gestore degli errori.
1. Crea [object manager](https://github.com/magento/magento2/tree/2.4.8/lib/internal/Magento/Framework/ObjectManager) e servizi condivisi di base utilizzati ovunque e interessati dall&#39;ambiente. I parametri dell’ambiente vengono inseriti correttamente in questi oggetti.
1. Asserisce che la modalità di manutenzione è _non_ abilitata; in caso contrario, termina.
1. Asserisce che l&#39;applicazione Commerce è installata; in caso contrario, termina.
1. Avvia l&#39;applicazione Commerce.

   Qualsiasi eccezione non rilevata durante l&#39;avvio dell&#39;applicazione viene automaticamente restituita a Commerce nel metodo `catchException()` che è possibile utilizzare per gestire l&#39;eccezione. Quest&#39;ultimo deve restituire `true` o `false`:

   - Se `true`: Commerce ha gestito l&#39;eccezione correttamente. Non c&#39;è bisogno di fare altro.
   - Se `false`: (o qualsiasi altro risultato vuoto) Commerce non ha gestito l&#39;eccezione. L&#39;oggetto bootstrap esegue la subroutine predefinita per la gestione delle eccezioni.

1. Invia la risposta fornita dall&#39;oggetto applicativo.

   >[!INFO]
   >
   >Il comportamento predefinito della classe `\Magento\Framework\App\Bootstrap` è costituito dalle asserzioni che indicano che l&#39;applicazione Commerce è installata e non in modalità di manutenzione. È possibile modificarlo utilizzando uno script del punto di ingresso durante la creazione dell&#39;oggetto bootstrap.

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

- In [modalità sviluppatore](../bootstrap/application-modes.md#developer-mode), visualizza l&#39;eccezione così com&#39;è.
- In qualsiasi altra modalità, tenta di registrare un’eccezione e di visualizzare un messaggio di errore generico.
- Termina Commerce con codice di errore `1`

## Applicazioni entry-point

Abbiamo le seguenti applicazioni del punto di ingresso (ovvero, applicazioni definite da Commerce che vengono utilizzate dal server web come indice di directory):

### Punto di ingresso HTTP

[\Magento\Framework\App\Http](https://github.com/magento/magento2/tree/2.4.8/lib/internal/Magento/Framework/App/Http) funziona come segue:

1. Determina l&#39;[area applicazione](https://developer.adobe.com/commerce/php/architecture/modules/areas/).
1. Avvia il controller anteriore e i sistemi di routing per individuare ed eseguire un&#39;azione del controller.
1. Utilizza un oggetto di risposta HTTP per restituire il risultato ottenuto dall’azione del controller.
1. Gestione degli errori (nell’ordine di priorità seguente):

   1. Se si utilizza la [modalità sviluppatore](../bootstrap/application-modes.md#developer-mode):
      - Se l&#39;applicazione Commerce non è installata, reindirizzare all&#39;Installazione guidata.
      - Se l&#39;applicazione Commerce è installata, visualizzare un errore e il codice di stato HTTP 500 (Errore interno del server).
   1. Se l’applicazione Commerce è in modalità manutenzione, visualizza una pagina di destinazione intuitiva &quot;Servizio non disponibile&quot; con codice di stato HTTP 503 (Servizio non disponibile).
   1. Se l&#39;applicazione Commerce è installata _not_, reindirizzare all&#39;Installazione guidata.
   1. Se la sessione non è valida, reindirizzare alla home page.
   1. In caso di altri errori di inizializzazione dell&#39;applicazione, visualizzare una pagina intuitiva denominata &quot;Pagina non trovata&quot; con codice di stato HTTP 404 (non trovato).
   1. In caso di altri errori, visualizza una pagina semplice di &quot;Servizio non disponibile&quot; con la risposta HTTP 503, genera un rapporto di errore e visualizza il relativo ID sulla pagina.

### Punto di ingresso risorsa statica

[\Magento\Framework\App\StaticResource](https://github.com/magento/magento2/tree/2.4.8/lib/internal/Magento/Framework/App/StaticResource.php) è un&#39;applicazione per il recupero di risorse statiche, ad esempio CSS, JavaScript e immagini. Posticipa qualsiasi azione con una risorsa statica fino a quando la risorsa non viene richiesta.

>[!INFO]
>
>Il punto di ingresso per i file di visualizzazione statica non viene utilizzato in [modalità di produzione](application-modes.md#production-mode) per evitare potenziali attacchi sul server. In modalità di produzione, l&#39;applicazione Commerce prevede che tutte le risorse necessarie siano presenti nella directory `<your Commerce install dir>/pub/static`.

In modalità predefinita o sviluppatore, una richiesta per una risorsa statica inesistente viene reindirizzata al punto di ingresso statico in base alle regole di riscrittura specificate da `.htaccess` appropriato.
Quando la richiesta viene reindirizzata al punto di ingresso, l’applicazione Commerce analizza l’URL richiesto in base ai parametri recuperati e trova la risorsa richiesta.

- In modalità [sviluppatore](application-modes.md#developer-mode), il contenuto del file viene restituito in modo che ogni volta che viene richiesta la risorsa, il contenuto restituito sia aggiornato.
- In modalità [default](application-modes.md#default-mode), la risorsa recuperata viene pubblicata in modo che sia accessibile dall&#39;URL richiesto in precedenza.

  Tutte le richieste future per la risorsa statica vengono elaborate dal server allo stesso modo dei file statici, ovvero senza coinvolgere il punto di ingresso. Se è necessario sincronizzare i file pubblicati con quelli originali, è necessario rimuovere la directory `pub/static`. Di conseguenza, i file vengono ripubblicati automaticamente con la richiesta successiva.

### Punto di ingresso risorse multimediali

[Magento\MediaStorage\App\Media](https://github.com/magento/magento2/tree/2.4.8/app/code/Magento/MediaStorage/App/Media.php) recupera le risorse multimediali (ovvero tutti i file caricati nell&#39;archivio multimediale) dal database. Viene utilizzato ogni volta che il database viene configurato come archivio multimediale.

`\Magento\Core\App\Media` tenta di trovare il file multimediale nell&#39;archivio del database configurato e di scriverlo nella directory `pub/static`, quindi di restituirne il contenuto. In caso di errore, restituisce un codice di stato HTTP 404 (Non trovato) nell’intestazione senza contenuto.

