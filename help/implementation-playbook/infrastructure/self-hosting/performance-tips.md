---
title: Suggerimenti sulle prestazioni di Adobe Commerce con hosting autonomo
description: Scopri i suggerimenti sulle prestazioni di self-hosting, i concetti e le best practice da considerare.
landing-page-description: Scopri alcuni concetti e aspetti relativi alle prestazioni da tenere in considerazione quando ospiti Adobe Commerce da solo.
short-description: Scopri le strategie e i concetti di prestazioni per ospitare Adobe Commerce.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: 95ff0c79-21d0-4514-991c-d88f616db68f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1304'
ht-degree: 0%

---

# Suggerimenti sulle prestazioni di Adobe Commerce con hosting autonomo

L’utilizzo di una piattaforma di e-commerce flessibile e potente non implica necessariamente un sacrificio di prestazioni. Dall’introduzione di Adobe Commerce, l’applicazione core ha subito numerosi miglioramenti. Nella versione 2.5.4, il team di progettazione di Adobe Commerce ha eseguito un set test per eseguire il benchmark dell’applicazione. I risultati del test hanno dimostrato che Adobe Commerce è in grado di gestire un ampio catalogo di oltre 240 milioni di SKU, i tempi di richiesta delle API sono in media eccezionali di 300 ms e il numero di visualizzazioni di pagina e di ordini effettuati all’ora è fenomenale, con 2 milioni di visualizzazioni di pagina e 208.000 ordini all’ora.

Visualizza i risultati più recenti del benchmark andando a [Experience League - Adobe Commerce - Playbook di implementazione - Benchmark](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/infrastructure/performance/benchmarks.html){target="_blank"}.

Per mantenere le cose ottimali, segui questi standard quando aggiungi personalizzazioni e complessità aggiuntiva al progetto.

Le sezioni seguenti trattano argomenti da considerare e consigli su come ottimizzare l’implementazione di self-hosting.

## Vernice

La vernice è un proxy inverso HTTP con cache. Per quanto possa sembrare complicato, il risultato sono risposte rapide per garantire che le richieste vengano restituite più rapidamente che se fosse necessario recuperare l’elemento dalla sorgente. L’esecuzione di un sito Adobe Commerce senza una versione di Vernice rallenterà il caricamento delle pagine e altre metriche chiave. La vernice può essere un po &#39;difficile da impostare e gestire se stessi, tuttavia abbiamo questo argomento in Experience League [Configura vernice](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/varnish/config-varnish.html){target="_blank"} per comprenderne meglio l’utilizzo con Adobe Commerce. In alternativa, puoi utilizzare una soluzione basata su cloud. Se da un lato ce ne sono molti da considerare, Fastly è stato scelto come soluzione per Adobe Commerce sul cloud. Si tratta di una versione di Fastly, basata sul cloud, che utilizza VCL e molte sfaccettature di vernice.

Trovare una soluzione che si adatti al meglio alle applicazioni, alla configurazione, al budget e alle capacità tecniche è difficile. L&#39;utilizzo di un&#39;opzione basata su cloud fa scomparire tutte le parti hardware, in quanto vengono considerati la gestione, la configurazione, i server e altri componenti dell&#39;infrastruttura. È stata scelta dal team Adobe Commerce on cloud come soluzione a causa delle prestazioni, della scalabilità, del throughput e di molte altre metriche chiave.

Scegliendo una buona soluzione per il tuo progetto relativo a Vernice, ti stai impostando per le migliori prestazioni per i tuoi clienti e risparmiando l&#39;applicazione commerce di lavorare più duramente di quanto deve.

## CDN

Oltre a essere una risorsa preziosa per il tuo progetto Adobe Commerce, ora in linea c&#39;è anche una rete CDN. Oltre a Varnish, una CDN può fornire istanze memorizzate nella cache per i file CSS, risorse di pagina come le immagini per ridurre la larghezza di banda che arriva all’applicazione Adobe Commerce. Può memorizzare nella cache le risposte GraphQL per sfruttare ulteriormente i vantaggi di un sito Adobe Commerce headless. Alcune CDN forniscono l’ottimizzazione delle immagini, un firewall per le applicazioni web e altre funzioni.

Adobe Commerce sul cloud ha scelto di utilizzare Fastly per la cache di Vernice ma anche come CDN. Questa singola soluzione fornisce una miriade di funzioni per fornire un’esperienza eccezionale ai clienti Adobe Commerce su cloud. Consulta la panoramica dei servizi Fastly nell’Experience League [Panoramica dei servizi Fastly](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html){target="_blank"}

Una rete CDN fornisce contenuti di consegna ottimizzati e sicuri per il progetto Adobe Commerce. Se questo non è un componente necessario per il progetto, deve essere considerato alla maturazione del sito e all’aumento della quantità di visitatori. Fornendo una rete CDN, è possibile ritardare l&#39;aggiunta di hardware aggiuntivo all&#39;infrastruttura o la scalabilità dell&#39;infrastruttura esistente a causa del carico rimosso da ogni richiesta.

## Disabilita moduli

La disabilitazione di un modulo non utilizzato deve essere presa in considerazione, ma non presa alla leggera. Questa tecnica riduce alcune spese generali e il tempo di elaborazione per alcune richieste, ma ci sono effetti collaterali che devono essere considerati. Spesso, quando uno sviluppatore assume che un modulo sia disponibile durante la creazione di funzionalità, si verificano dei casi in cui Questo è spesso sicuro, a meno che non scelgano di utilizzare alcune classi presenti in un modulo disabilitato.

La disattivazione di un modulo come la &quot;newsletter&quot; nativa è un evento abbastanza comune. Ciò si verifica in particolare quando il proprietario del negozio ha una società di terze parti che gestisce la newsletter. Questo può essere un problema quando viene installato un modulo di terze parti e, per qualche motivo, hanno deciso di utilizzare una classe della newsletter. Questa dipendenza accidentale probabilmente verrà rilevata durante l’installazione iniziale e i test, ma in seguito sei costretto a decidere se mantenere questo modulo di terze parti, abilitare la newsletter e quindi testare la regressione del sito alla ricerca di eventuali comportamenti strani introdotti. Oppure trovi un sostituto per il modulo di terze parti? Entrambe le decisioni comportano rischi, tempo e possibili bug.

Prima di disabilitare i moduli non utilizzati, accertati di non disporre di test quali unit, [MFTF](https://developer.adobe.com/commerce/cloud-tools/docker/test/application-testing/){target="_blank"}, [Codeception testing](https://developer.adobe.com/commerce/cloud-tools/docker/test/code-testing/){targe="_blank"} test di caricamento o richieste API che potrebbero essere interessate.

## Richiedi il rispetto degli standard di codifica Adobe Commerce e PHP per ogni richiesta pull

Adobe Commerce dispone di un set di [Standard di codifica](https://developer.adobe.com/commerce/php/coding-standards/){target="_blank"}. In questo modo è possibile garantire che il modello, lo stile e la progettazione previsti siano simili, indipendentemente dal tipo di sviluppo software. Questo è un requisito quando contribuisci alla base di codice di Adobe Commerce. Tuttavia, se scegli di seguire questa metodologia per lo sviluppo personalizzato, stabilisce un solido fondamento per tutti gli sviluppatori, sia attuali che futuri. Quando si richiede a tutte le richieste pull di passare uno standard di codice, è importante assicurarsi che tutti possano capire e aspettarsi gli stessi modelli di sviluppo coerenti.

Per accompagnare gli standard di codifica Adobe Commerce, l&#39;altra base utilizzata è costituita dagli standard di codifica PHP di base. Dovrebbe essere chiaramente definito nelle guide per sviluppatori quali standard devi seguire e quali deviazioni sono accettabili. Tuttavia, un fallback dovrebbe essere alla guida gestita pubblicamente che si trova all&#39;indirizzo [PHP-FIG](https://www.php-fig.org){target="_blank"}.

Una posizione ferma nei confronti del PSR-1 e del PSR-12. Assicurati che gli sviluppatori che contribuiscono al progetto seguano questi fattori aiuta a garantire che non vi siano file e modelli stranamente strutturati. Questo consente anche ai futuri sviluppatori di leggere e comprendere rapidamente il codice che stanno esaminando. Più si seguono questi modelli e standard di codifica, più le attività di sviluppo future dovrebbero essere più facili da leggere e più veloci da implementare.

## Eseguire test di carico dopo ogni distribuzione

L&#39;esecuzione di un test di carico dopo ogni distribuzione può sembrare eccessiva. Tuttavia, se si segue questa metodologia, è possibile tenere traccia e attenuare l’opportunità di nuove funzioni introdotte che causano una diminuzione delle prestazioni.

Oltre a rilevare il deterioramento delle prestazioni dal nuovo codice, avere un riferimento storico delle metriche chiave dal sito può aiutare a fornire informazioni approfondite su quando è abilitato un nuovo strumento o una nuova infrastruttura di modifica. Ad esempio, prima di pagare la società di hosting per ridimensionare l&#39;ambiente e sperare di ottenere l&#39;aumento delle prestazioni previsto, puoi impostare un ambiente di staging con le nuove configurazioni ed eseguire un test di carico per vedere quale sarebbe il risultato effettivo.

Questi test possono essere automatizzati e far parte della pipeline CI/CD. Per questo motivo, è anche possibile disporre di regole che accettano i risultati e potenzialmente bloccano l&#39;unione di feature in caso di eccessiva deviazione dalla norma. Il numero di casi d’uso per questi dati è illimitato, ma senza avviare questo processo potresti non realizzare mai il suo potenziale.

Adobe Commerce ha una buona scrittura su questo argomento, che si trova in Experience League [Suggerimenti per il test delle prestazioni](https://experienceleague.adobe.com/docs/commerce-operations/deliver-commerce-at-scale/launch.html){target="_blank"} and in [Testing guidance](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html){target="_blank"}.

{{$include /help/_includes/hosting-related-links.md}}
