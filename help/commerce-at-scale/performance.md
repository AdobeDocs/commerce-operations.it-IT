---
title: Ottimizzazione delle prestazioni AEM
description: Ottimizza la configurazione predefinita di Adobe Experience Manager per supportare carichi elevati su Adobe Commerce.
exl-id: 923a709f-9048-4e67-a5b0-ece831d2eb91
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '2248'
ht-degree: 0%

---

# Ottimizzazione delle prestazioni AEM

Il dispatcher AEM è un proxy inverso, che aiuta a fornire un ambiente sia veloce che dinamico. Funziona come parte di un server HTML statico, come Apache HTTP Server, allo scopo di memorizzare (o &quot;memorizzare in cache&quot;) il maggior numero possibile di contenuti del sito, sotto forma di risorse statiche. Questo approccio mira a ridurre al minimo la necessità di accedere il più possibile alla funzionalità di rendering delle pagine di AEM e al servizio Commerce GraphQL di Adobe. Il risultato del serving di gran parte delle pagine come HTML statico, CSS e JS offre agli utenti vantaggi in termini di prestazioni e riduce i requisiti di infrastruttura nell’ambiente. Per la memorizzazione in cache deve essere considerata qualsiasi pagina o query che può essere ripetuta in modo identico da un utente all’altro.

Le sezioni seguenti mostrano ad alto livello l’area di interesse tecnico consigliata da rivedere per abilitare l’effettiva memorizzazione in cache su AEM in un ambiente CIF/Adobe Commerce.

## Memorizzazione in cache basata su TTL su AEM dispatcher

La memorizzazione in cache del maggior numero possibile di siti sui dispatcher è la best practice per qualsiasi progetto AEM. L’utilizzo dell’annullamento della validità della cache basato su tempo memorizzerà nella cache le pagine CIF sottoposte a rendering sul lato server per un periodo di tempo limitato. Una volta scaduto l’orario impostato, la richiesta successiva ricostruirà la pagina dall’editore AEM e da Commerce GraphQL di Adobe e la memorizzerà nuovamente nella cache del dispatcher fino alla successiva invalidazione.

La funzione di caching TTL può essere configurata in AEM utilizzando il componente &quot;Dispatcher TTL&quot; all&#39;interno del pacchetto ACS AEM Commons e impostando /enableTTL &quot;1&quot; nel file di configurazione dispatcher.any.

Se abilitato, il dispatcher valuterà le intestazioni di risposta dal back-end e se contengono una data massima Cache-Control o una data di scadenza, viene creato un file ausiliario vuoto accanto al file di cache, con un&#39;ora di modifica uguale alla data di scadenza. Quando il file memorizzato nella cache viene richiesto oltre il tempo di modifica, viene automaticamente richiesto nuovamente dal backend. Questo offre un meccanismo di caching efficace che non richiede interventi o manutenzione manuali, una volta che il ritardo di aggiornamento del prodotto (TTL) è stato riconosciuto e accettato dalle parti interessate del business.

## Memorizzazione in cache del browser

L’approccio TTL del dispatcher illustrato qui sopra ridurrà notevolmente le richieste e il caricamento sull’editore, tuttavia ci sono alcune risorse che difficilmente cambieranno e quindi anche le richieste al dispatcher possono essere ridotte memorizzando nella cache i file rilevanti localmente sul browser di un utente. Ad esempio, il logo del sito, visualizzato su ogni pagina del sito nel modello di sito, non dovrebbe essere richiesto ogni volta al dispatcher. Questo può essere invece memorizzato nella cache del browser dell’utente. La riduzione dei requisiti di larghezza di banda per ogni caricamento delle pagine avrebbe un grande impatto sulla reattività del sito e sui tempi di caricamento delle pagine.

La memorizzazione in cache a livello di browser viene comunemente eseguita tramite &quot;Cache-Control: max-age=&quot; intestazione di risposta. L&#39;impostazione maxage indica al browser per quanti secondi deve memorizzare in cache il file prima di tentare di &quot;riconvalidare&quot; o richiederlo nuovamente dal sito. Questo concetto di età massima della cache è comunemente noto come &quot;Scadenza cache&quot; o TTL (&quot;Time to Live&quot;). Distribuzione su larga scala di esperienze commerce - Con Adobe Experience Manager, Commerce Integration Framework, Adobe Commerce 7

Alcune aree di un sito Commerce AEM/CIF/Adobe che può essere impostato per essere memorizzato nella cache nel browser del cliente includono:

- Immagini (all&#39;interno del modello di AEM stesso, ad esempio il logo del sito e le immagini di progettazione del modello - le immagini dei prodotti di catalogo saranno chiamate da Adobe Commerce tramite Flast, la memorizzazione in cache di queste immagini sarà discussa più avanti)
- File HTML (per pagine modificate raramente - pagina termini e condizioni, ecc.)
- File CSS
- Tutti i file JavaScript del sito, inclusi i file JavaScript CIF

## Ottimizzazione del periodo di tolleranza per lo statfilelevel e l’ancoraggio del dispatcher

La configurazione predefinita del dispatcher utilizza l’impostazione /statfilelevel &quot;0&quot;, il che significa che un singolo file &quot;.stat&quot; viene posizionato nella directory principale della directory htdocs (directory document root). Se viene apportata una modifica a una pagina o a un file in AEM, l’ora di modifica di questo file di statistica singolo viene aggiornata all’ora della modifica. Se l’ora è più recente rispetto all’ora di modifica della risorsa, il dispatcher considererà che tutte le risorse sono invalidate e qualsiasi richiesta successiva per una risorsa invalidata attiverà una chiamata all’istanza Publish. Quindi essenzialmente, con questa impostazione ogni attivazione invalida l&#39;intera cache.

Per qualsiasi sito, in particolare i siti di e-commerce con carico elevato, questo inserirebbe una quantità inutile di carico sul livello di pubblicazione AEM affinché l’intera struttura del sito venga invalidata con un solo aggiornamento di pagina.

È invece possibile modificare l’impostazione statfilelevel con un valore più alto, corrispondente alla profondità delle sottodirectory nella directory htdocs dalla directory radice del documento in modo che, quando un file posizionato a un determinato livello viene invalidato, vengano aggiornati solo i file a tale livello di directory .stat e seguenti.

Ad esempio: supponiamo che tu disponga di un modello di pagina prodotto in:

```
content/ecommerce/us/en/products/product-page.html
```

Ogni livello di cartella avrebbe un &quot;livello stat&quot;, come mostrato nella tabella precedente.

| contenuto (docroot) | ecommerce | noi | en | products | product-page.tml |
|-------------------|-----------|----|----|----------|------------------|
| 0 | 1 | 2 | 3 | 4 | - |

In questo caso, se hai lasciato la proprietà statfilelevel impostata sul valore predefinito &quot;0&quot; e il modello product-page.html viene aggiornato e attivato attivando un’invalidazione, ogni file .stat da docroot al livello 4 verrà toccato e i file invalidati, causando un’ulteriore richiesta dalle istanze di pubblicazione AEM per tutte le pagine del sito (inclusi altri siti web, paesi e lingue) da tale singola modifica.

Tuttavia, se la proprietà statfilelevel è impostata sul livello 4 e viene apportata una modifica al product-page.html , verrà toccato solo il file .stat nella directory dei prodotti per quel sito web/paese/lingua specifico.

Tieni presente che il livello del file .stat non deve essere impostato su un livello troppo alto - superare i 20 può avere un impatto sulle prestazioni. L’esecuzione di un’attivazione in blocco di file durante l’esecuzione di un test delle prestazioni deve fornire il livello corretto a cui ottimizzare il livello di stato.

Un’altra impostazione del dispatcher da ottimizzare durante la configurazione dello statfilelevel è l’impostazione gracePeriod . Questo definisce il numero di secondi in cui una risorsa obsoleta e auto-invalidata può ancora essere servita dalla cache dopo l’ultima attivazione. Le risorse con annullamento automatico della validità vengono invalidate da qualsiasi attivazione (quando il loro percorso corrisponde alla sezione dispatcher /invalidate e al livello specificato nella proprietà statfileslevel ). L’impostazione di gracePeriod su 2 secondi può essere utilizzata per impedire uno scenario in cui più richieste vengono inviate continuamente all’editore, anche mentre l’editore è ancora in corso di creazione della nuova pagina.

>[!NOTE]
>
> Ulteriori letture più dettagliate su questo argomento sono disponibili nell&#39;archivio [aem-dispatcher-Expercher](https://github.com/adobe/aem-dispatcher-experiments/tree/main/experiments/gracePeriod) GitHub .

## CIF: memorizzazione in cache GraphQL tramite componenti

I singoli componenti all’interno di AEM possono essere impostati in cache, il che significa che la richiesta GraphQL ad Adobe
La chiamata Commerce viene effettuata una volta e successivamente le richieste successive, fino al limite di tempo configurato, vengono recuperate dalla cache AEM e non caricano ulteriormente su Adobe Commerce. Ad esempio, la navigazione nel sito basata su una struttura di categorie mostrata su ogni pagina e le opzioni all’interno di una funzionalità di ricerca sfaccettata. Si tratta solo di due aree che richiedono query ad alta intensità di risorse su Commerce di Adobe per essere create, ma è improbabile che si modifichino regolarmente e quindi rappresentano una buona scelta per il caching. In questo modo, ad esempio, anche quando un PDP o un PLP viene ricostruito dall’editore, la richiesta GraphQL a uso intensivo di risorse per la build di navigazione non raggiungerà Adobe Commerce e potrebbe essere recuperata dalla cache GraphQL su AEM CIF.

Di seguito è riportato un esempio di memorizzazione in cache del componente di navigazione perché invia la stessa query GraphQL su tutte le pagine del sito. La richiesta seguente memorizza in cache le ultime 100 voci per 10 minuti per la struttura di navigazione:

```
venia/components/structure/navigation:true:100:600
```

L’esempio seguente memorizza in cache le ultime 100 opzioni di ricerca sfaccettate in una pagina di ricerca per 1 ora:

```
com.adobe.cq.commerce.core.search.services.SearchFilterService:true:100:3600
```

La richiesta, comprese tutte le intestazioni e le variabili http personalizzate, deve corrispondere esattamente affinché la cache sia &quot;hit&quot; e per evitare una chiamata ripetuta ad Adobe Commerce. Va notato che una volta impostato non c&#39;è un modo facile per annullare manualmente questa cache. Questo potrebbe significare, quindi, che se una nuova categoria viene aggiunta in Adobe Commerce, non inizierebbe a comparire nella navigazione fino a quando il tempo di scadenza impostato nella cache sopra è scaduto e la richiesta GraphQL viene aggiornata. Lo stesso vale per i facet di ricerca. Tuttavia, dati i vantaggi di prestazioni che si possono ottenere con questo caching, questo è di solito un compromesso accettabile.

Le opzioni di memorizzazione in cache di cui sopra possono essere impostate utilizzando la console di configurazione OSGi AEM in &quot;Client GraphQL
Configuration Factory&quot;. È possibile specificare ogni voce di configurazione della cache con il seguente formato:

```
• NAME:ENABLE:MAXSIZE:TIMEOUT like for example mycache:true:1000:60 where each attribute is defined as:
    › NAME (String): name of the cache
    › ENABLE (true|false): enables or disables that cache entry
    › MAXSIZE (Integer): maximum size of the cache (in number of entries)
    › TIMEOUT (Integer): timeout for each cache entry (in seconds)
```

## Memorizzazione in cache ibrida: richieste GraphQL lato client nelle pagine del dispatcher memorizzate nella cache

È anche possibile un approccio ibrido alla memorizzazione in cache delle pagine: una pagina CIF può contenere componenti che richiederebbero sempre le informazioni più recenti da Adobe Commerce direttamente dal browser del cliente. Questo può essere utile per aree specifiche della pagina all’interno di un modello che sono importanti per essere aggiornate con informazioni in tempo reale: Ad esempio, i prezzi dei prodotti all’interno di un PDP. Se i prezzi cambiano frequentemente a causa della corrispondenza dinamica dei prezzi, è possibile configurare tali informazioni in modo che non siano memorizzate nella cache del dispatcher, ma che i prezzi possano essere recuperati lato client nel browser del cliente da Adobe Commerce direttamente tramite API GraphQL con componenti web CIF AEM.

Questo può essere configurato tramite le impostazioni dei componenti AEM. Per informazioni sui prezzi nelle pagine dell’elenco dei prodotti, questo può essere configurato nel modello dell’elenco dei prodotti, selezionando il componente dell’elenco prodotti nelle impostazioni della pagina e selezionando l’opzione &quot;prezzi di caricamento&quot;. Lo stesso approccio funzionerebbe per i livelli delle scorte.

I metodi di cui sopra devono essere utilizzati solo nel caso in cui l&#39;informazione in tempo reale e costantemente aggiornata sia obbligatoria. Nell&#39;esempio precedente con i prezzi, si potrebbe concordare con le parti interessate aziendali di aggiornare i prezzi solo quotidianamente a bassi tempi di traffico e di eseguire il flush della cache in quel momento. Questo eliminerebbe la necessità di richieste di informazioni sui prezzi in tempo reale e il successivo carico aggiuntivo su Adobe Commerce durante la creazione di ogni pagina con informazioni sui prezzi.

## Richieste GraphQL non memorizzabili nella cache

I componenti di dati dinamici specifici all’interno delle pagine non devono essere memorizzati nella cache e richiedono sempre una chiamata GraphQL ad Adobe Commerce, ad esempio per il carrello e le chiamate nelle pagine di pagamento. Queste informazioni sono specifiche per un utente e cambiano costantemente a causa dell’attività del cliente sul sito, ad esempio aggiungendo prodotti al carrello.

I risultati della query GraphQL non devono essere memorizzati nella cache per i clienti connessi se la progettazione del sito fornisce risposte diverse in base al ruolo dell’utente. Ad esempio, puoi creare più gruppi di clienti e impostare prezzi di prodotto diversi o una visibilità diversa per ogni gruppo. I risultati della memorizzazione nella cache come questi possono causare la visualizzazione dei prezzi di un altro gruppo di clienti o la visualizzazione di categorie errate.

## Ignorare i parametri di tracciamento nella cache AEM dispatcher

I siti di e-commerce possono indirizzare il traffico verso il loro sito utilizzando annunci di ricerca PPC o campagne social media.

L’utilizzo di questi media implica l’aggiunta di un ID di tracciamento al collegamento in uscita da tale piattaforma. Ad esempio, Facebook aggiungerà un Facebook Click ID (fbclid) all’URL, Google Adverts aggiungerà un Google Click ID (gclid), in modo che i collegamenti in entrata al tuo fronte di AEM appariranno come il seguente, come esempio:

```
https://www.adobe.com/?gclid=oirhgj34y43yowiahg9u3t
```

Il gclid e fbclid cambieranno con ogni utente che fa clic sull’annuncio, questo è destinato a scopi di tracciamento, ma con le sue impostazioni predefinite, AEM vedrebbe ogni richiesta come una pagina univoca, che bypasserebbe il dispatcher e genererebbe un carico aggiuntivo inutile sull’editore e su Adobe Commerce.

Durante un evento di ondata, gli editori AEM possono anche essere sovraccaricati e non rispondere. Quando un parametro è impostato per essere ignorato per una pagina, la pagina viene memorizzata nella cache la prima volta che viene richiesta la pagina. Le richieste successive per la pagina vengono servite nella cache, indipendentemente dal valore del parametro nella richiesta.

>[!NOTE]
>
>Ulteriori informazioni sull’importanza dell’impostazione `ignoreUrlParams` sono disponibili nell’archivio [aem-dispatcher-expericher](https://github.com/adobe/aem-dispatcher-experiments/tree/main/experiments/ignoreUrlParams) GitHub .

Dovrebbe pertanto essere configurato per ignorare tutti i parametri per impostazione predefinita in &quot;ignoreUrlParams&quot;, a meno che non venga utilizzato un parametro GET che modificherebbe la struttura HTML di una pagina. Un esempio di ciò potrebbe essere con una pagina di ricerca in cui il termine di ricerca è nell&#39;URL come parametro GET - in questo caso dovresti configurare manualmente ignoreUrlParams per ignorare parametri come gclid, fbclid e qualsiasi altro parametro di tracciamento che i canali pubblicitari usano, lasciando inalterati i parametri GET richiesti per le normali operazioni sul sito.

## Limiti per i lavoratori del MPM ai dispatcher

Le impostazioni dei processi di lavoro MPM sono una configurazione avanzata del server Apache HTTP che richiederebbe un test approfondito per ottimizzare in base alla CPU e alla RAM disponibili del Dispatcher. Tuttavia, nell&#39;ambito di questo white paper si consiglia di aumentare ServerLimit e MaxRequestWorkers a un livello che la CPU e la RAM disponibili del server supporterebbero, quindi i MinSpareThreads e MaxSpareThreads siano entrambi aumentati a un livello che corrisponde al MaxRequestWorkers.

Questa configurazione lascerebbe Apache HTTP su una &quot;impostazione di piena disponibilità&quot; che è una configurazione ad alte prestazioni per i server con RAM significativa e più core della CPU. Questa configurazione produrrà i migliori tempi di risposta possibili da Apache HTTP mantenendo le connessioni aperte persistenti pronte per servire le richieste e rimuoverebbe qualsiasi ritardo nella generazione di nuovi processi in risposta a improvvisi ondate di traffico, come durante le vendite flash.
