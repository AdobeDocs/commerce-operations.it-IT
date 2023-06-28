---
title: Strumenti di monitoraggio Adobe Commerce per hosting autonomo
description: Scopri gli strumenti di monitoraggio self-hosting, le idee, i concetti e le best practice da considerare.
landing-page-description: Scopri alcuni concetti e aspetti degli strumenti di monitoraggio da considerare quando ospiti Adobe Commerce da solo.
short-description: Scopri le strategie e i concetti degli strumenti di monitoraggio per l’hosting di Adobe Commerce.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: 728e9439-63d0-4481-b014-7ba2ce97b9d0
feature: Install, Logs, Observability
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '1716'
ht-degree: 0%

---

# Telemetria e strumenti di monitoraggio Adobe Commerce con hosting autonomo

L&#39;utilizzo di strumenti di monitoraggio consente di rilevare i cambiamenti senza dover pagare qualcuno per guardare tutto in continuazione. Con la maggior parte degli strumenti, è possibile aggiungere avvisi e notifiche se viene raggiunta una soglia, ad esempio un disco rigido che esaurisce lo spazio disponibile. Alcuni strumenti forniscono output che devono essere tracciati e calcolati, ad esempio i risultati del test di carico. Indipendentemente dallo strumento, ogni strumento ha uno scopo e, se utilizzato in modo coerente, può aiutarti a gestire l’applicazione. Ci sono opzioni gratuite per ogni strumento, ma ricordarsi di pagare per un servizio spesso garantisce un supporto più veloce e affidabile e può valere la pena l&#39;investimento. New Relic è un esempio di strumento che offre un livello gratuito e una versione a pagamento che sfrutta molta più potenza e funzionalità. Ce ne sono altri come DataDog o Dynatrace. Trova una buona opzione per te e utilizzala in modo coerente.

## Monitoraggio dell’infrastruttura

Il termine infrastruttura è usato piuttosto liberamente in questo contesto. Per questo argomento, si intende qualsiasi server, processo o dispositivo utilizzato per il funzionamento del sito. Ad esempio:

* Dischi rigidi
* Utilizzo CPU
* Utilizzo RAM
* Redis
* Carico medio per server
* traffico di rete

Ricercare soglie per creare avvisi efficaci. Non assegnarne una per gli aspetti importanti, ad esempio la capacità del disco rigido. Imposta alcune per avvisare diversi gruppi quando le cose peggiorano. Ad esempio, ecco un set di regole quando un disco rigido è pieno.

* Notifica di Slack del 70% al canale DevOps
* 80% Notifica il canale DevOps della sala di Slack e una lista di distribuzione via e-mail dei compagni di squadra DevOps
* 90% Notifica canale DevOps di Slack e supporto alla produzione canale di Slack, e-mail DevOps Distribution Group e Engineering Manager
* 95% Notify Slack DevOps e canali di Slack di supporto alla produzione, lista di distribuzione via e-mail di tutti i tecnici e Director of engineering
* 98% Notifica qualsiasi canale di Slack P1 e canali di Slack DevOps e di supporto alla produzione, e-mail di distribuzione dei tecnici e Director of engineering e VP of technology

Ci sono molti modi per notificare un team, quindi assicurati di sceglierne uno che sia affidabile e che non venga inondato da troppi avvisi. È importante riservare gli avvisi quando è importante, altrimenti si corre il rischio di diventare sopraffatti e iniziare a ignorarli.

Esistono spesso buoni modelli da seguire per la maggior parte degli strumenti come New Relic, DataDog e Dynatrace. Prenditi del tempo per trovare buone idee che abbiano più senso per la tua applicazione. Con Adobe Commerce sull’infrastruttura cloud, al momento del provisioning del progetto vengono attivati avvisi e attivatori. Questo consente al team di supporto della produzione Adobe di applicare i propri strumenti per il monitoraggio dei tempi di attività e dell’elevata disponibilità.

Le dashboard consentono di accedere rapidamente agli aspetti frequenti o importanti del sito. Gli elementi del dashboard possono essere costituiti da visualizzazioni di pagina, utilizzo della CPU per host, elenco di tutti i server, tempi di caricamento delle pagine, durate delle transazioni e persino risultati dei test di monitoraggio sintetici per gli ultimi giorni. Queste dashboard devono essere create in modo da consentire una valutazione rapida in caso di errori, oppure dashboard diversi configurati per esperienze utente diverse. Puoi progettare diverse dashboard e vedere il monitoraggio delle applicazioni in tempo reale. È molto soddisfacente, soprattutto quando richiesto dal proprietario del progetto o da un manager come funziona il sito, e si può trovare la risposta in secondi, non ore.

## Aggregazione e rotazione dei registri

I file di registro si trovano nei server applicazioni che elaborano le richieste o nei registri MySQL quando l&#39;esecuzione richiede troppo tempo. Il problema dei registri è che sono separati gli uni dagli altri e li trovano tutti, l’analisi delle informazioni di ciascun registro può essere complicata. Molti anni fa questo problema è stato risolto utilizzando una tecnica chiamata _aggregazione dei registri_. In questo modo i file di registro di tutte le posizioni vengono inviati a una posizione centralizzata. Una volta spostati, un software può leggerli e fornire modi per cercare, filtrare e rivedere le informazioni. Questo può essere un processo difficile per ottenere giusto. Sono disponibili molte opzioni, ma se sei fortunato gli strumenti di monitoraggio possono leggere e aggregare i file di registro, ad esempio New Relic. Trovando un buon strumento, si può risparmiare una quantità incommensurabile di tempo nel futuro. A meno che non si disponga di un solo server che esegue tutte le operazioni necessarie per l&#39;esecuzione e il funzionamento del sito, l&#39;aggregazione dei registri è essenziale. Ciò è particolarmente utile quando si cerca di capire se si è sotto un attacco DDoS o si verifica un picco di traffico legittimo, o quando si cerca il motivo per cui una determinata richiesta non riesce.

Un altro elemento chiave per i registri è garantire che la rotazione avvenga. Questo riguarda storicamente `run-away logs` che possono accidentalmente riempire il disco rigido e causare la caduta del sito. Una versione della rotazione del registro può verificarsi quando un file di registro raggiunge una determinata dimensione, ad esempio 1 GB. Esistono strumenti a livello di server come `logrotate` che possono rimuoverli automaticamente. Ad esempio, è possibile rimuovere i file di registro di dimensioni eccessive quando superano i 1 GB oppure i file di registro più vecchi di 90 giorni. Definisci un criterio di registro, quindi è importante comprendere i limiti delle risorse.

## Scansioni malware

Molte società di hosting di siti web che sono dedicate ad Adobe Commerce avrebbero una libreria di exploit noti e malware. Devono offrire una scansione automaticamente o su richiesta. Laddove sono efficaci, sono reazionari e funzionano solo quando viene rilevato nuovo malware. Potrebbe essere una buona idea avere uno strumento proattivo che possa esaminare il codice e il database per il malware noto. Sono disponibili alcune opzioni, ad esempio [ReportImmagine](https://www.magereport.com){target="_blank"}, [Sansec](https://sansec.io){target="_blank"}, or [Magento Malware Scanner](https://github.com/gwillem/magento-malware-scanner){target="_blank"}. Possono eseguire una scansione remota dall&#39;esterno o essere installati e aggiornare/eseguire la scansione/monitorare in modo proattivo dopo essere stati configurati sui server. Si tratta di un&#39;ottima opzione, in quanto la libreria viene costantemente aggiornata in quanto vengono installati e monitorati migliaia di siti se si sceglie una soluzione specifica, ad esempio Sansec. Quando viene rilevato un nuovo malware, ogni progetto monitorato beneficia delle informazioni e viene ora avvisato se viene rilevato.

Ci sono alcune versioni gratuite da prendere in considerazione, ma per il malware, si dovrebbe davvero considerare una soluzione a pagamento. Questa potrebbe essere la differenza tra il fatto che il sito sia stato infettato per alcuni minuti e per alcuni mesi. Avere un exploit sul tuo sito causa enormi mal di testa, questa è un&#39;area che si dovrebbe considerare il pagamento per un servizio.

## Adobe di strumento di analisi a livello di sito

Site-Wide Analysis Tool è uno strumento proattivo self-service e un archivio centrale che include informazioni dettagliate sul sistema e raccomandazioni per garantire la sicurezza e l’operabilità dell’installazione di Adobe Commerce. Fornisce monitoraggio delle prestazioni in tempo reale, report e consigli 24 ore su 24, 7 giorni su 7 per identificare potenziali problemi e migliorare la visibilità delle configurazioni di salute, sicurezza e applicazioni del sito. Consente di ridurre i tempi di risoluzione e di migliorare la stabilità e le prestazioni del sito.

Nella pagina Recommendations dello strumento di analisi a livello di sito sono elencati i consigli basati sulle best practice per risolvere i problemi rilevati sul sito. Le raccomandazioni sono ordinate in base alla priorità da PO a P4, dove PO è critico e P4 è basso. I risultati includono descrizione, consigli, impatto sul sito, causa principale, scenari/precondizioni, risultato previsto e strumenti utilizzati.

Scopri le best practice per migliorare le prestazioni del sito. Monitora e implementa i consigli elencati in base alla priorità.

Per ulteriori informazioni su come installarlo nel progetto, visita [Guida all’installazione di Site-Wide Analysis Tool](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/installation.html){target="_blank"}.

## Monitoraggio SSL

Uno degli elementi dimenticati di un progetto è il certificato SSL. Hanno bisogno di attenzione solo una volta all&#39;anno, quindi dimenticarli è molto facile. La scadenza del certificato di sicurezza potrebbe causare un avviso o un rifiuto da parte dei browser moderni di visualizzare le pagine del sito. Se si verifica un problema di questo tipo, i clienti possono iniziare a inviare e-mail o a chiamare il supporto e l’utente potrebbe non essere in grado di utilizzarlo finché il problema non viene risolto. Ogni minuto conta, quindi riconoscere la scadenza sta arrivando prima del tempo e assicurarsi che le cose siano rinnovate è fondamentale per mantenere il sito in funzione. Esistono molti modi per eseguire il monitoraggio SSL. Prendi in considerazione l’utilizzo di strumenti di monitoraggio sintetico per il tuo sito, utilizzando strumenti gratuiti o a basso costo come PKingdom, Keychest o Sucuri e persino abbonati a un servizio che offre avvisi di scadenza dei certificati SSL. Questi semplici strumenti possono garantire la validità dei certificati del sito e ridurre il rischio di tempi di inattività per i clienti.

## Test automatizzati

L’esecuzione di test automatizzati, come test funzionali o unit test, spesso consente di rilevare i problemi derivanti dal codice appena introdotto. Questi test potrebbero non rilevare tutto, in quanto Adobe Commerce e gli unit test hanno in genere una copertura inferiore al 50%. Ciò non significa che dovresti evitare di scriverli e di testarli. Questi strumenti servono ad aggiungere un altro livello di sicurezza che garantisca che tutto ciò che viene eseguito non influisca negativamente sull’utilizzo preconfigurato e su eventuali test personalizzati creati dal team di sviluppo. Eseguendo questi test in ogni distribuzione, eventuali problemi principali vengono rilevati in anticipo ed evitano di consentire agli elementi di passare alla produzione.

I test di carico possono essere difficili da eseguire per ottenere il risultato corretto. Gran parte della complessità deriva da come il front-end viene utilizzato e implementato. Se il sito dispone di un front-end headless, potrebbe essere utile caricare il test delle API GraphQL e REST. Sta a te e al team DevOps decidere come terminare il test di carico. Ogni test di carico, eseguito il prima possibile, fornisce informazioni approfondite sullo stato del progetto. Fornisce inoltre parametri di riferimento per le prove future al fine di verificare eventuali modifiche drastiche nei risultati delle prove di carico. In caso affermativo, e sono negativi, questa è una buona opportunità per rivedere le ultime modifiche al codice e cercare sezioni che influiscono sulle prestazioni da migliorare.

Adobe Commerce dispone di utili indicazioni per comprendere come eseguire gli unit test, vedi [Test dell&#39;unità PHP](https://developer.adobe.com/commerce/testing/guide/unit/){target="_blank"} nel _Guida al test delle applicazioni_ nel sito della documentazione di Adobe Developer.

Per ulteriori informazioni sui test funzionali, visita [Introduzione al Functional Testing Framework](https://developer.adobe.com/commerce/testing/functional-testing-framework/){target="_blank"}.


{{$include /help/_includes/hosting-related-links.md}}
