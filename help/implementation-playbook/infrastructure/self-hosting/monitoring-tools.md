---
title: Strumenti di monitoraggio Adobe Commerce per hosting autonomo
description: Scopri informazioni sugli strumenti di monitoraggio self-hosting, idee, concetti e best practice da considerare.
landing-page-description: Scopri alcuni concetti relativi agli strumenti di monitoraggio e cose da considerare quando si ospita Adobe Systems Commerce da soli.
short-description: Scopri strategie e concetti di strumenti di monitoraggio per l'hosting Adobe Systems Commerce.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: 5aa03f91-1240-47f6-8d06-b06e64973266
feature: Install, Logs, Observability
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '1710'
ht-degree: 0%

---

# Hosting autonomo Adobe Systems strumenti e telemetria per il monitoraggio del commercio

L&#39;utilizzo di strumenti di monitoraggio offre l&#39;opportunità di rilevare i cambiamenti senza dover pagare qualcuno per guardare tutto il tempo. Con la maggior parte degli strumenti, è possibile aggiungere avvisi e notifiche se viene soddisfatto un soglia, ad esempio un dare impulso a difficile che sta esaurendo lo spazio. Alcuni strumenti forniscono output che deve essere tracciato e calcolato, ad esempio i risultati dei test di carico. Non importa il strumento, ogni strumento ha uno scopo e, se usato in modo coerente, può aiutarti a gestire la tua applicazione. Ci sono gratuito opzioni per ogni strumento, ma ricorda che pagare per un servizio spesso garantisce un supporto più veloce e affidabile e può valere l&#39;investimento. Nuovo Relic è un esempio di strumento che offre un livello gratuito e una versione a pagamento che sblocca molta più potenza e capacità. Ce ne sono altri come DataDog o Dynatrace. Trova una buona opzione per te e utilizzala in modo coerente.

## Monitoraggio dell&#39;infrastruttura

Il termine infrastruttura è usato in modo piuttosto vago per questo contesto. Per questo argomento, si intende qualsiasi server, processo o dispositivo utilizzato per far funzionare il sito. Ad esempio:

* Dischi rigidi
* Utilizzo della CPU
* Utilizzo della RAM
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

I file di registro si trovano nei server applicazioni che elaborano le richieste o nei registri MySQL quando l&#39;esecuzione richiede troppo tempo. Il problema dei registri è che sono separati gli uni dagli altri e li trovano tutti, l’analisi delle informazioni di ciascun registro può essere complicata. Molti anni fa questo problema è stato risolto utilizzando una tecnica denominata _aggregazione del registro_. In questo modo i file di registro di tutte le posizioni vengono inviati a una posizione centralizzata. Una volta spostati, un software può leggerli e fornire modi per cercare, filtrare e rivedere le informazioni. Questo può essere un processo difficile per ottenere giusto. Ci sono molte opzioni, ma se sei fortunato i tuoi strumenti di monitoraggio possono leggere e aggregato i tuoi file di registro, come Nuovo Relic. Trovando una buona strumento, puoi risparmiare una quantità incommensurabile di tempo in futuro. A meno che tu non abbia un solo server che fa di tutto per far funzionare e funzionare il tuo sito, avere l&#39;aggregazione dei log è essenziale. Ciò è particolarmente utile quando si cerca di capire se si è sotto un attacco DDoS o si verifica un picco di traffico legittimo, o quando si cerca perché un determinato richiesta sta fallendo.

Un altro elemento chiave per i tronchi è garantire che la rotazione avvenga. Questo storicamente riguarda `run-away logs` il fatto che può riempire accidentalmente il tuo dare impulso a duro e causare l&#39;arresto del sito. Una versione della rotazione del registro può verificarsi quando un file di registro raggiunge una certa dimensione, ad esempio 1 GB. Esistono strumenti a livello di server in `logrotate` grado di rimuoverli automaticamente. Ad esempio, può rimuovere file di registro eccessivamente grandi quando diventano più grandi di 1 GB o rimuovere file di registro più vecchi di 90 giorni. Si definisce un regola di log, quindi è importante comprendere i limiti delle risorse.

## Scansioni malware

Molte società di hosting di siti web che sono dedicate ad Adobe Commerce avrebbero una libreria di exploit noti e malware. Devono offrire una scansione automaticamente o su richiesta. Laddove sono efficaci, sono reazionari e funzionano solo quando viene rilevato nuovo malware. Potrebbe essere una buona idea avere uno strumento proattivo che possa esaminare il codice e il database per il malware noto. Sono disponibili alcune opzioni, ad esempio [MageReport](https://www.magereport.com){target="_blank"}, [Sansec](https://sansec.io){target="_blank"} o [Scanner malware Magento](https://github.com/gwillem/magento-malware-scanner){target="_blank"}. Possono eseguire una scansione remota dall&#39;esterno o essere installati e aggiornare/eseguire la scansione/monitorare in modo proattivo dopo essere stati configurati sui server. Si tratta di un&#39;ottima opzione, in quanto la libreria viene costantemente aggiornata in quanto vengono installati e monitorati migliaia di siti se si sceglie una soluzione specifica, ad esempio Sansec. Quando viene rilevato un nuovo malware, ogni progetto monitorato beneficia delle informazioni e viene ora avvisato se viene rilevato.

Ci sono alcune versioni gratuite da prendere in considerazione, ma per il malware, si dovrebbe davvero considerare una soluzione a pagamento. Questa potrebbe essere la differenza tra il fatto che il sito sia stato infettato per alcuni minuti e per alcuni mesi. Avere un exploit sul tuo sito causa enormi mal di testa, questa è un&#39;area che si dovrebbe considerare il pagamento per un servizio.

## Adobe di strumento di analisi a livello di sito

Site-Wide Analysis Tool è uno strumento proattivo self-service e un archivio centrale che include informazioni dettagliate sul sistema e raccomandazioni per garantire la sicurezza e l’operabilità dell’installazione di Adobe Commerce. Fornisce monitoraggio delle prestazioni in tempo reale, report e consigli 24 ore su 24, 7 giorni su 7 per identificare potenziali problemi e migliorare la visibilità delle configurazioni di salute, sicurezza e applicazioni del sito. Consente di ridurre i tempi di risoluzione e di migliorare la stabilità e le prestazioni del sito.

La pagina Raccomandazioni dello strumento di analisi a livello di sito elenca i consigli basati sulle best practice per risolvere i problemi rilevati sul sito. Le raccomandazioni sono ordinate per priorità da PO a P4, dove PO è critico e P4 è basso. I risultati includono descrizione, consiglio, impatto sul sito, causa principale, scenari / precondizioni, risultato atteso e strumenti utilizzati.

Scopri le best practice per migliorare la tua prestazioni del sito. Tenere traccia e implementare i consigli elencati in base alla priorità.

Per ulteriori informazioni su come installarlo nel progetto, visita [Guida all&#39;installazione](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/installation.html){target="_blank"} dello strumento di analisi a livello di sito.

## Monitoraggio SSL

Uno degli elementi dimenticati di un progetto è il certificato SSL. Hanno bisogno di attenzione solo una volta all&#39;anno, quindi dimenticarli è molto facile. La scadenza del certificato di sicurezza potrebbe comportare un avviso o un rifiuto da parte dei browser moderni di visualizzare le pagine del tuo sito. Se si verifica un problema di questo tipo, i clienti possono iniziare a inviare e-mail o a chiamare il supporto e l’utente potrebbe non essere in grado di utilizzarlo finché il problema non viene risolto. Ogni minuto conta, quindi riconoscere che la scadenza sta arrivando in anticipo e assicurarsi che le cose vengano rinnovate è fondamentale per mantenere il sito attivo e funzionante. Esistono molti modi per eseguire il monitoraggio SSL. Prendi in considerazione l&#39;utilizzo di strumenti di monitoraggio sintetici per il tuo sito, utilizzando strumenti gratuito o a basso costo like Pingdom, Keychest o Sucuri e lineare abbonati a un servizio che offre avvisi di scadenza del certificato SSL. Questi semplici strumenti possono garantire che i certificati del tuo sito siano validi e ridurre il rischio di tempi di inattività per i tuoi clienti.

## Test automatizzati

L&#39;esecuzione di test automatizzati, ad esempio test funzionali o unit test, consente spesso di rilevare i problemi derivanti dal codice appena introdotto. Questi test potrebbero non rilevare tutto, poiché Adobe Systems Commerce e gli unit test hanno in genere una copertura inferiore al 50%. Ciò non significa che dovresti evitare di scriverli e testarli. Questi strumenti sono qui per aggiungere un ulteriore livello di sicurezza e protezione che tutto ciò che viene impegnato non influisce negativamente sul test out of the box e su eventuali test personalizzati creati dal tuo team di sviluppo. Eseguendo questi test su ogni distribuzione, eventuali problemi importanti vengono rilevati in anticipo ed evitano che le cose si facciano strada verso la produzione.

I test di carico possono essere difficili da eseguire correttamente. Gran parte della complessità deriva da come il front-end viene utilizzato e implementato. Se il sito dispone di un front-end headless, potrebbe essere utile caricare il test delle API GraphQL e REST. Sta a te e al team DevOps decidere come terminare il test di carico. Ogni test di carico, eseguito il prima possibile, fornisce informazioni approfondite sullo stato del progetto. Fornisce inoltre parametri di riferimento per i test futuri per vedere se ci sono cambiamenti drastici nei risultati dei test di carico. Se è così, e sono negativi, questo è un buon opportunità per esaminare le ultime modifiche al codice e cercare sezioni che influiscono sulle prestazioni da migliorare.

Adobe Systems Commerce dispone di buone indicazioni per aiutare a capire come eseguire unit test, vedere [unit testing](https://developer.adobe.com/commerce/testing/guide/unit/){target="_blank"} PHP nella _Guida_ al test delle applicazioni nel sito della documentazione di Adobe Systems Developer.

Per ulteriori informazioni sui test funzionali, visita [Introduzione a Functional Testing Framework](https://developer.adobe.com/commerce/testing/functional-testing-framework/){target="_blank"}.


{{$include /help/_includes/hosting-related-links.md}}
