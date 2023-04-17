---
title: Strumenti di monitoraggio di Adobe Commerce self-hosting
description: Scopri gli strumenti di monitoraggio self-hosting idee e concetti e best practice da considerare.
landing-page-description: Scopri alcuni concetti e cose da considerare durante l’hosting di Adobe Commerce da solo.
short-description: Scopri strategie e concetti relativi agli strumenti di monitoraggio per l’hosting autonomo di Adobe Commerce.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
source-git-commit: 63fddb20673399bae397238a8dda866e1d740e6f
workflow-type: tm+mt
source-wordcount: '1716'
ht-degree: 0%

---


# Strumenti e telemetria di monitoraggio Adobe Commerce self-hosting

L&#39;utilizzo di strumenti di monitoraggio consente di rilevare i cambiamenti senza dover pagare qualcuno per guardare tutto il tempo. Con la maggior parte degli strumenti, è possibile aggiungere avvisi e notifiche se viene soddisfatta una soglia, ad esempio un disco rigido che esaurisce lo spazio disponibile. Alcuni strumenti forniscono un output da tracciare e calcolare, ad esempio i risultati del test di carico. Indipendentemente dallo strumento, ogni strumento ha uno scopo e, se utilizzato in modo coerente, può aiutarti a gestire la tua applicazione. Ci sono opzioni gratuite per ogni strumento, ma ricordate che pagare per un servizio spesso assicura un supporto più veloce e affidabile e può essere valsa la pena l&#39;investimento. New Relic è un esempio di uno strumento che offre un livello gratuito e una versione a pagamento che sblocca molta più potenza e capacità. Ci sono altri come DataDog o Dynatrace. Trova una buona opzione per te e utilizzala in modo coerente.

## Monitoraggio dell&#39;infrastruttura

Il termine infrastruttura viene utilizzato piuttosto liberamente per questo contesto. Per questo argomento si intende qualsiasi server, processo o dispositivo utilizzato per il funzionamento del sito. Ad esempio:

* Unità disco rigido
* Utilizzo della CPU
* Utilizzo RAM
* Redis
* Carico medio per server
* traffico di rete

Soglie di ricerca per creare avvisi efficaci. Non assegnarne uno per elementi importanti come la capacità del disco rigido. Imposta alcuni per avvisare i diversi gruppi mentre le cose peggiorano. Ad esempio, ecco un set di regole quando un disco rigido si sta riempiendo.

* Notifica di Slack del 70% al canale DevOps
* 80% Notifica il canale DevOps della stanza di Slack e una lista di distribuzione e-mail dei compagni di squadra DevOps
* 90% Notifica Slack canale DevOps e supporto di produzione canale Slack, e-mail DevOps gruppo di distribuzione e il tecnico manager
* 95% Notifica Slack DevOps e supporto di produzione canali di Slack, lista di distribuzione e-mail di tutti gli ingegneri e Director di ingegneria
* 98% Notifica tutti i canali di Slack P1 e i canali di Slack DevOps e supporto di produzione, la lista di distribuzione e-mail di ingegneri e Director di ingegneria e VP di tecnologia

Ci sono molti modi per avvisare un team, quindi assicuratevi di scegliere uno che è affidabile e non viene inondato con troppi avvisi. È importante riservare gli avvisi quando è importante, altrimenti correte il rischio di essere sopraffatti e iniziare a ignorare gli avvisi.

Ci sono spesso buoni modelli da seguire per la maggior parte degli strumenti come New Relic, DataDog e Dynatrace. Prenditi un po&#39; di tempo per trovare buone idee che hanno più senso per la tua applicazione. Con Adobe Commerce sull’infrastruttura cloud, sono presenti avvisi e attivatori al momento del provisioning del progetto. Questo consente al team di supporto per la produzione di Adobe di applicare i propri strumenti per il monitoraggio dei tempi di attività e dell&#39;elevata disponibilità.

Le dashboard consentono di accedere rapidamente agli aspetti frequenti o importanti del sito. Gli elementi del dashboard possono consistere in visualizzazioni di pagina, utilizzo della CPU per host, elenco di tutti i server, tempi di caricamento delle pagine, durate delle transazioni e persino risultati di test di monitoraggio sintetico negli ultimi giorni. Queste dashboard devono essere create per consentire una rapida valutazione in caso di problemi o se sono configurate dashboard diverse per diverse esperienze utente. Si spera di poter progettare diverse dashboard e godere di vedere il monitoraggio delle applicazioni in tempo reale. È molto soddisfacente, soprattutto quando richiesto dal proprietario del progetto o da un responsabile come funziona il sito, e si può trovare la risposta in secondi, non ore.

## Aggregazione e rotazione del registro

I file di registro si trovano sui server applicazioni che elaborano le richieste o i registri MySQL quando l&#39;esecuzione richiede troppo tempo. La cosa difficile dei log è che sono separati l&#39;uno dall&#39;altro e trovarli tutti, analizzare le informazioni di ogni log può essere ingombrante. Molti anni fa questo problema è stato risolto utilizzando una tecnica chiamata _aggregazione log_. In questo modo i file di registro vengono recuperati da tutte le posizioni di log e inviati a una posizione centralizzata. Una volta spostati, un software può leggerli e fornire modi per cercare, filtrare e rivedere le informazioni. Questo può essere un processo difficile da risolvere. Ci sono molte opzioni, ma se siete fortunati i vostri strumenti di monitoraggio possono leggere e aggregare i vostri file di log, come New Relic. Trovando un buon strumento, si può risparmiare un incommensurabile quantità di tempo in futuro. A meno che non si disponga di un solo server che esegua tutte le operazioni necessarie per l&#39;esecuzione e il funzionamento del sito, l&#39;aggregazione dei log è essenziale. Questo è particolarmente utile quando si cerca di capire se sei sotto un attacco DDoS o si verifica un picco di traffico legittimo, o quando si cerca il motivo per cui una determinata richiesta sta fallendo.

Un altro elemento chiave per i registri è garantire che la rotazione avvenga. Questo riguarda storicamente `run-away logs` che può accidentalmente riempire il tuo disco rigido e causare la caduta del sito. Una versione della rotazione del registro può verificarsi quando un file di registro raggiunge una certa dimensione, ad esempio 1 GB. Esistono strumenti a livello di server come `logrotate` che può rimuoverli automaticamente. Ad esempio, può rimuovere file di log eccessivamente grandi una volta che diventano più grandi di 1 GB o rimuovere file di log più vecchi di 90 giorni. Definisci un criterio di registro, quindi è importante comprendere le limitazioni delle risorse.

## Scansioni malware

Molte aziende di hosting di siti web dedicate ad Adobe Commerce avrebbero una libreria di sfruttare e malware noti. Essi dovrebbero offrire una scansione automaticamente o su richiesta. Se sono efficaci, sono reazionari e funzionano solo quando viene rilevato un nuovo malware. Può essere una buona idea avere uno strumento proattivo che può guardare il codice e il database per malware noto. Sono disponibili alcune opzioni, ad esempio [ReportImmagine](https://www.magereport.com){target="_blank"}, [Sansec](https://sansec.io){target="_blank"}, or [Magento Malware Scanner](https://github.com/gwillem/magento-malware-scanner){target="_blank"}. Possono eseguire una scansione remota dall&#39;esterno oppure essere installati e aggiornare/scansionare/monitorare in modo proattivo dopo essere stati impostati sui server. Queste possono essere una grande opzione in quanto la loro libreria viene costantemente aggiornata perché sono installati e monitorano migliaia di siti se si sceglie una soluzione fornita come Sansec. Quando viene rilevato un nuovo malware, ogni progetto che monitorano beneficia delle informazioni e ora viene avvisato se viene rilevato.

Ci sono alcune versioni gratuite da considerare, ma per il malware, si dovrebbe davvero prendere in considerazione una soluzione a pagamento. Questa può essere una differenza tra il sito infettato per alcuni minuti rispetto a pochi mesi. Avere un sfruttare sul tuo sito causa enormi mal di testa, questo è un&#39;area che dovresti considerare di pagare per un servizio.

## Adobe dello strumento di analisi a livello di sito

Lo strumento di analisi a livello di sito è uno strumento proattivo self-service e un archivio centrale che include informazioni dettagliate sul sistema e raccomandazioni per garantire la sicurezza e l’operabilità dell’installazione di Adobe Commerce. Fornisce monitoraggio delle prestazioni in tempo reale, report e consigli 24 ore su 24 per identificare potenziali problemi e migliorare la visibilità sulle configurazioni di sicurezza, salute e applicazioni del sito. Consente di ridurre i tempi di risoluzione e migliorare la stabilità e le prestazioni del sito.

Nella pagina Recommendations dello strumento di analisi a livello di sito sono elencate le raccomandazioni basate sulle best practice per risolvere i problemi rilevati sul sito. Le raccomandazioni sono ordinate per priorità da PO a P4, dove PO è critico e P4 è basso. I risultati includono descrizione, raccomandazione, impatto del sito, causa principale, scenari/condizioni preliminari, risultato previsto e strumenti utilizzati.

Scopri le best practice per migliorare le prestazioni del sito. Tenere traccia e implementare le raccomandazioni elencate in base alla priorità.

Per ulteriori informazioni su come installarlo nel progetto, visita [Guida all’installazione di uno strumento di analisi a livello di sito](https://experienceleague.adobe.com/docs/commerce-operations/tools/site-wide-analysis-tool/installation.html){target="_blank"}.

## Monitoraggio SSL

Uno degli elementi più dimenticati per un progetto è il certificato SSL. Hanno bisogno di attenzione solo una volta all&#39;anno, quindi dimenticarli è molto facile. La scadenza del certificato di sicurezza potrebbe comportare l’avviso o il rifiuto da parte dei browser di visualizzare le pagine del sito. Se si verifica un problema di questo tipo, i clienti possono iniziare a inviare e-mail o a chiamare il supporto e potresti non riuscire a farlo finché non viene risolto. Ogni minuto conta, quindi riconoscere la scadenza sta arrivando in anticipo e assicurarsi che le cose siano rinnovate è fondamentale per mantenere il sito in funzione e in esecuzione. Esistono molti modi per eseguire il monitoraggio SSL. Prendi in considerazione l’utilizzo di strumenti di monitoraggio sintetico per il tuo sito, utilizzando strumenti gratuiti o a basso costo come Pingdom, Keypetto o Sucuri e iscriviti a un servizio che offre avvisi sulla scadenza del certificato SSL. Questi semplici strumenti possono garantire la validità dei certificati del sito e ridurre il rischio di tempi di inattività dei clienti.

## Test automatizzato

L’esecuzione di test automatizzati, come test funzionali o unit test, spesso aiuta a rilevare i problemi derivanti dal codice appena introdotto. Questi test potrebbero non funzionare, in quanto Adobe Commerce e i test di unità di misura in genere hanno una copertura inferiore al 50%. Non significa che devi evitare di scriverli e di testarli. Questi strumenti sono qui per aggiungere un altro livello di sicurezza che tutto ciò che viene commesso non influenza negativamente il pronto all’uso e qualsiasi test personalizzato creato dal tuo team di sviluppo. L&#39;esecuzione di questi test su ogni implementazione consente di rilevare rapidamente tutti i problemi principali ed evita di consentire agli elementi di passare alla produzione.

I test di carico possono essere difficili da ottenere correttamente. Gran parte della complessità deriva dal modo in cui il frontend viene utilizzato e implementato. Se il tuo sito ha una front-end headless, puoi caricare le API GraphQL e REST di prova. Il modo in cui si concludono i test di carico dipende da te e dal team DevOps. Ogni test di carico, eseguito il prima possibile, fornisce informazioni sullo stato del progetto. Fornisce inoltre parametri di riferimento per le prove future per verificare se vi sono cambiamenti drastici nei risultati delle prove di carico. In tal caso, e sono negativi, questa è una buona opportunità per rivedere le ultime modifiche del codice e cercare sezioni che abbiano un impatto sulle prestazioni per migliorare.

Adobe Commerce offre indicazioni utili per comprendere come eseguire i test di unità, consulta [Test dell&#39;unità PHP](https://developer.adobe.com/commerce/testing/guide/unit/){target="_blank"} in _Guida al test delle applicazioni_ nel sito della documentazione di Adobe Developer.

Per ulteriori informazioni sui test funzionali, visita [Introduzione al framework dei test funzionali](https://developer.adobe.com/commerce/testing/functional-testing-framework/){target="_blank"}.


{{$include /help/_includes/hosting-related-links.md}}
