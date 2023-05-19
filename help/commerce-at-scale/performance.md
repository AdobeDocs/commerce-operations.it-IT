---
title: Ottimizzazione delle prestazioni AEM
description: Ottimizza la configurazione Adobe Experience Manager predefinita per supportare carichi elevati su Adobe Commerce.
exl-id: 923a709f-9048-4e67-a5b0-ece831d2eb91
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '2248'
ht-degree: 0%

---

# Ottimizzazione delle prestazioni AEM

Il dispatcher per AEM è un proxy inverso che consente di fornire un ambiente veloce e dinamico. Funziona come parte di un server HTML statico, come Apache HTTP Server, con lo scopo di memorizzare (o &quot;memorizzare in cache&quot;) la maggior parte del contenuto del sito sotto forma di risorse statiche. Questo approccio mira a ridurre al minimo la necessità di accedere il più possibile alle funzionalità di rendering delle pagine AEM e al servizio Adobe Commerce GraphQL. Il risultato del fatto di gestire gran parte delle pagine come HTML statico, CSS e JS offre agli utenti vantaggi in termini di prestazioni e riduce i requisiti di infrastruttura per l’ambiente. Qualsiasi pagina o query che potrebbe essere ripetuta in modo identico da utente a utente deve essere considerata per il caching.

Le sezioni seguenti mostrano ad alto livello l’area di focus tecnico consigliata da rivedere per consentire un caching efficace sull’AEM in un ambiente CIF/Adobe Commerce.

## Memorizzazione in cache basata su TTL sui dispatcher AEM

Memorizzare in cache la maggior parte del sito possibile sui dispatcher è una best practice per qualsiasi progetto AEM. Se si utilizza l’annullamento della validità della cache in base al tempo, verranno memorizzate nella cache le pagine CIF sottoposte a rendering lato server, per un periodo di tempo limitato. Una volta scaduto il tempo impostato, la richiesta successiva ricreerà la pagina dall’editore dell’AEM e da Adobe Commerce GraphQL e la memorizzerà nuovamente nella cache del dispatcher fino alla successiva invalidazione.

La funzione di caching TTL può essere configurata in AEM utilizzando il componente &quot;Dispatcher TTL&quot; all’interno del pacchetto ACS AEM Commons e impostando /enableTTL &quot;1&quot; nel file di configurazione dispatcher.any.

Se questa opzione è abilitata, il dispatcher valuterà le intestazioni di risposta provenienti dal backend e, se contengono un’età massima per il controllo della cache o una data di scadenza, viene creato un file ausiliario vuoto accanto al file della cache, con un tempo di modifica uguale alla data di scadenza. Quando il file memorizzato in cache viene richiesto oltre il tempo di modifica, viene automaticamente richiesto nuovamente dal backend. Questo offre un meccanismo di caching efficace che non richiede alcun intervento manuale o manutenzione, una volta che il ritardo di aggiornamento del prodotto (TTL) è stato riconosciuto e accettato dalle parti interessate aziendali.

## Memorizzazione nella cache del browser

L’approccio TTL del dispatcher descritto sopra ridurrà notevolmente le richieste e il caricamento nell’editore. Tuttavia, poiché è molto improbabile che alcune risorse vengano modificate, anche le richieste al dispatcher possono essere ridotte memorizzando nella cache i file rilevanti localmente sul browser di un utente. Ad esempio, il logo del sito, che viene visualizzato in ogni pagina del sito nel modello del sito, non dovrebbe essere richiesto ogni volta a Dispatcher. Può invece essere memorizzato nella cache del browser dell’utente. La riduzione dei requisiti di larghezza di banda per ogni caricamento di pagina avrebbe un impatto notevole sulla reattività del sito e sui tempi di caricamento delle pagine.

La memorizzazione nella cache a livello di browser viene solitamente eseguita tramite l’intestazione di risposta &quot;Cache-Control: max-age=&quot;. L’impostazione massima indica al browser per quanti secondi deve memorizzare in cache il file prima di tentare di &quot;riconvalidare&quot; o richiederlo nuovamente dal sito. Questo concetto di max-age della cache viene comunemente definito &quot;Scadenza cache&quot; o TTL (&quot;Time to Live&quot;). Distribuzione di esperienze e-commerce su larga scala: con Adobe Experience Manager, Commerce Integration Framework, Adobe Commerce 7

Alcune aree di un sito AEM/CIF/Adobe Commerce che possono essere impostate per la memorizzazione nella cache nel browser del client includono:

- Immagini (all’interno del modello AEM stesso, ad esempio logo del sito e immagini di progettazione del modello - le immagini dei prodotti catalogo verrebbero richiamate da Adobe Commerce tramite Fastly, di cui verrà discusso in seguito nella memorizzazione in cache di queste immagini)
- File HTML (per pagine modificate raramente: pagina termini e condizioni, ecc.)
- File CSS
- Tutti i file JavaScript del sito, inclusi i file JavaScript CIF

## Ottimizzazione del periodo di tolleranza e statfilelevel di Dispatcher

La configurazione del dispatcher predefinita utilizza l’impostazione /statfilelevel &quot;0&quot;; ciò significa che un singolo file &quot;.stat&quot; viene inserito nella directory principale di htdocs (directory principale dei documenti). Se viene apportata una modifica a una pagina o a un file nell’AEM, l’ora di modifica di questo singolo file stat viene aggiornata all’ora della modifica. Se l’ora è successiva all’ora di modifica della risorsa, Dispatcher considererà tutte le risorse invalidate e qualsiasi richiesta successiva di una risorsa invalidata attiverà una chiamata all’istanza Publish. In sostanza, con questa impostazione ogni attivazione invaliderà l’intera cache.

Per qualsiasi sito, in particolare per i siti commerce con carico elevato, ciò comporterebbe un carico superfluo sul livello di pubblicazione AEM, in modo che l’intera struttura del sito venga invalidata con un solo aggiornamento di pagina.

È invece possibile modificare l’impostazione statfilelevel impostando un valore più alto, corrispondente alla profondità delle sottodirectory nella directory htdocs dalla directory principale dei documenti in modo che, quando un file che si trova a un determinato livello viene invalidato, vengano aggiornati solo i file a tale livello di directory .stat e inferiore.

Ad esempio: supponiamo che tu abbia un modello di pagina di prodotto in:

```
content/ecommerce/us/en/products/product-page.html
```

Ogni livello di cartella avrebbe un &quot;livello stat&quot;, come illustrato nella tabella precedente.

| contenuto (directory principale dei documenti) | e-commerce | us | it | products | product-page.tml |
|-------------------|-----------|----|----|----------|------------------|
| 0 | 1 | 2 | 3 | 4 | - |

In questo caso, se hai lasciato la proprietà statfilelevel impostata sul valore predefinito &quot;0&quot; e il modello product-page.html viene aggiornato e attivato attivando un’invalidazione, ogni file .stat dalla directory principale dei documenti al livello 4 viene toccato e i file vengono invalidati, causando un’ulteriore richiesta da parte delle istanze di pubblicazione dell’AEM per tutte le pagine del sito (inclusi altri siti web, paesi e lingue) da quella singola modifica.

Tuttavia, se la proprietà statfilelevel è impostata al livello 4 e viene apportata una modifica al file product-page.html, verrà toccato solo il file .stat nella directory prodotti per quel sito Web/paese/lingua specifico.

Tieni presente che il livello del file .stat non deve essere impostato su un livello troppo alto; un valore superiore a 20 può avere un impatto sulle prestazioni. L&#39;esecuzione dell&#39;attivazione di un file in blocco durante l&#39;esecuzione di un test delle prestazioni dovrebbe fornire il livello corretto su cui regolare il livello stat.

Un’altra impostazione del dispatcher da ottimizzare durante la configurazione dello statfilelevel è l’impostazione gracePeriod. Questo definisce il numero di secondi in cui una risorsa obsoleta e invalidata automaticamente può ancora essere distribuita dalla cache dopo l’ultima attivazione. Le risorse invalidate automaticamente vengono invalidate da qualsiasi attivazione (quando il loro percorso corrisponde alla sezione /invalidate di Dispatcher e al livello specificato nella proprietà statfileslevel). È possibile impostare gracePeriod su 2 secondi per evitare che vengano continuamente inviate più richieste all’editore, anche se questo è ancora in fase di creazione della nuova pagina.

>[!NOTE]
>
> Ulteriori informazioni più dettagliate su questo argomento sono disponibili nel [aem-dispatcher-experiment](https://github.com/adobe/aem-dispatcher-experiments/tree/main/experiments/gracePeriod) Archivio GitHub.

## CIF - Memorizzazione in cache di GraphQL tramite componenti

I singoli componenti all’interno dell’AEM possono essere impostati per essere memorizzati in cache, il che significa che la richiesta di GraphQL ad Adobe Commerce viene chiamata una volta e che le richieste successive, fino al limite di tempo configurato, vengono recuperate dalla cache AEM e non caricano ulteriormente su Adobe Commerce. Ad esempio, una navigazione del sito basata su una struttura di categorie mostrata su ogni pagina e opzioni all’interno di una funzionalità di ricerca con facet: si tratta solo di due aree che richiedono query a uso intensivo di risorse su Adobe Commerce da generare, ma che probabilmente non cambieranno regolarmente e quindi sarebbero buone scelte per il caching. In questo modo, ad esempio, anche quando un PDP o PLP viene ricreato dall’editore, la richiesta di GraphQL a uso intensivo di risorse per la build di navigazione non raggiungerebbe Adobe Commerce e potrebbe essere recuperata dalla cache di GraphQL su AEM CIF.

Di seguito è riportato un esempio per il componente Navigazione da memorizzare in cache, perché invia la stessa query GraphQL su tutte le pagine del sito. La richiesta seguente memorizza in cache le ultime 100 voci per 10 minuti per la struttura di navigazione:

```
venia/components/structure/navigation:true:100:600
```

L’esempio seguente memorizza in cache le ultime 100 opzioni di ricerca con facet in una pagina di ricerca per 1 ora:

```
com.adobe.cq.commerce.core.search.services.SearchFilterService:true:100:3600
```

La richiesta, comprese tutte le intestazioni e le variabili http personalizzate, deve corrispondere esattamente affinché la cache possa essere &quot;hit&quot; e per evitare una chiamata ripetuta ad Adobe Commerce. Una volta impostata, è importante notare che non è possibile annullare manualmente la validità della cache. Questo potrebbe significare, quindi, che se una nuova categoria viene aggiunta in Adobe Commerce, non inizierà a essere visualizzata nella navigazione finché il tempo di scadenza impostato nella cache precedente non è scaduto e la richiesta GraphQL non viene aggiornata. Lo stesso vale per i facet di ricerca. Tuttavia, dati i vantaggi in termini di prestazioni che questa memorizzazione in cache offre, in genere si tratta di un compromesso accettabile.

Le opzioni di caching di cui sopra possono essere impostate utilizzando la console di configurazione AEM OSGi in &quot;GraphQL Client Configuration Factory&quot;. Ogni voce di configurazione della cache può essere specificata con il seguente formato:

```
• NAME:ENABLE:MAXSIZE:TIMEOUT like for example mycache:true:1000:60 where each attribute is defined as:
    › NAME (String): name of the cache
    › ENABLE (true|false): enables or disables that cache entry
    › MAXSIZE (Integer): maximum size of the cache (in number of entries)
    › TIMEOUT (Integer): timeout for each cache entry (in seconds)
```

## Memorizzazione in cache ibrida: richieste GraphQL lato client all’interno delle pagine del dispatcher memorizzate nella cache

È anche possibile un approccio ibrido alla memorizzazione in cache delle pagine: una pagina CIF può contenere componenti che richiederebbero sempre le informazioni più recenti da Adobe Commerce direttamente dal browser del cliente. Questo può essere utile per specifiche aree della pagina all’interno di un modello che sono importanti per essere tenuti aggiornati con informazioni in tempo reale: prezzi dei prodotti all’interno di un PDP, ad esempio. Se i prezzi cambiano frequentemente a causa della corrispondenza dinamica dei prezzi, tali informazioni possono essere configurate in modo da non essere memorizzate nella cache del dispatcher, ma possono essere recuperate lato client nel browser del cliente da Adobe Commerce direttamente tramite API GraphQL con componenti web AEM CIF.

Questo può essere configurato tramite le impostazioni dei componenti AEM: per informazioni sui prezzi nelle pagine dell’elenco dei prodotti, puoi configurarlo nel modello dell’elenco dei prodotti, selezionando il componente dell’elenco dei prodotti nelle impostazioni della pagina e selezionando l’opzione &quot;carica prezzi&quot;. Lo stesso approccio funzionerebbe per i livelli delle scorte.

I metodi di cui sopra devono essere utilizzati solo nel caso in cui sia necessario disporre di informazioni costantemente aggiornate e in tempo reale. Nell’esempio precedente con i prezzi, si potrebbe concordare con le parti interessate all’attività di aggiornare i prezzi solo ogni giorno in momenti di traffico ridotto ed eseguire quindi l’operazione di scaricamento della cache. In questo modo, quando si crea una pagina contenente informazioni sui prezzi, non è più necessario richiedere informazioni sui prezzi in tempo reale e caricare ulteriormente Adobe Commerce.

## Richieste GraphQL non memorizzabili nella cache

Componenti dati dinamici specifici all’interno delle pagine non devono essere memorizzati in cache e richiederanno sempre una chiamata GraphQL ad Adobe Commerce, ad esempio per il carrello e chiamate attraverso le pagine di pagamento. Queste informazioni sono specifiche per un utente e cambiano costantemente a causa dell’attività del cliente sul sito, ad esempio aggiungendo prodotti al carrello.

I risultati delle query GraphQL non devono essere memorizzati nella cache per i clienti connessi se la progettazione del sito darebbe risposte diverse in base al ruolo dell’utente. Ad esempio, puoi creare più gruppi di clienti e impostare prezzi di prodotto diversi o una visibilità della categoria di prodotto diversa per ciascun gruppo. La memorizzazione nella cache dei risultati di questo tipo può causare la visualizzazione dei prezzi di un altro gruppo di clienti o la visualizzazione di categorie non corrette da parte dei clienti.

## I parametri di tracciamento nella cache del dispatcher AEM verranno ignorati

I siti di e-commerce possono indirizzare il traffico verso il loro sito utilizzando annunci di ricerca PPC o campagne sui social media.

L’utilizzo di questi supporti comporta l’aggiunta di un ID di tracciamento al collegamento in uscita da tale piattaforma. Ad esempio, Facebook aggiungerà un Facebook Click ID (fbclid) all’URL, Google Adverts aggiungerà un Google Click ID (gclid), in modo che i collegamenti in ingresso al front-end dell’AEM vengano visualizzati come segue, ad esempio:

```
https://www.adobe.com/?gclid=oirhgj34y43yowiahg9u3t
```

Il gclid e il fbclid cambiano con ogni utente che fa clic sull’annuncio, per scopi di tracciamento, ma con le sue impostazioni predefinite, l’AEM vede ogni richiesta come una pagina univoca, che bypassa il dispatcher e genera un inutile carico aggiuntivo sull’editore e su Adobe Commerce.

Durante un evento di picco, questo può anche causare il sovraccarico e la mancata risposta degli editori dell’AEM. Quando un parametro è impostato per essere ignorato per una pagina, la pagina viene memorizzata in cache la prima volta che viene richiesta. Alle successive richieste per la pagina viene distribuita la pagina memorizzata in cache, indipendentemente dal valore del parametro nella richiesta.

>[!NOTE]
>
>Ulteriori letture sull&#39;importanza della fissazione `ignoreUrlParams` è disponibile in [aem-dispatcher-experiment](https://github.com/adobe/aem-dispatcher-experiments/tree/main/experiments/ignoreUrlParams) Archivio GitHub.

Dovrebbe quindi essere configurato in modo da ignorare tutti i parametri per impostazione predefinita in &quot;ignoreUrlParams&quot;, a meno che non venga utilizzato un parametro di GET che modificherebbe la struttura HTML di una pagina. GET Ad esempio, puoi usare una pagina di ricerca in cui il termine di ricerca si trova nell’URL come parametro. In questo caso devi configurare manualmente ignoreUrlParams in modo da ignorare parametri come gclid, fbclid e qualsiasi altro parametro di tracciamento utilizzato dai canali pubblicitari, lasciando invariati i parametri di GET necessari per le normali operazioni del sito.

## Limiti dei lavoratori MPM sui dispatcher

Le impostazioni dei processi di lavoro MPM rappresentano una configurazione avanzata del server HTTP Apache che richiederebbe test approfonditi per ottimizzare la CPU e la RAM disponibili nel Dispatcher. Tuttavia, nell’ambito di questo white paper si suggerisce di aumentare ServerLimit e MaxRequestWorkers a un livello supportato dalla CPU e dalla RAM disponibili nel server, quindi di aumentare MinSpareThreads e MaxSpareThreads a un livello corrispondente a MaxRequestWorkers.

Questa configurazione lascerebbe Apache HTTP su un’&quot;impostazione di fattibilità completa&quot;, ovvero una configurazione ad alte prestazioni per server con RAM significativa e più core CPU. Questa configurazione produrrà i migliori tempi di risposta possibili da Apache HTTP mantenendo le connessioni aperte persistenti pronte per servire le richieste e rimuoverà qualsiasi ritardo nella generazione di nuovi processi in risposta a improvvisi picchi di traffico, come durante le vendite flash.
