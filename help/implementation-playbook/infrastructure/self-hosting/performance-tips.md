---
title: Suggerimenti sulle prestazioni per l’hosting autonomo di Adobe Commerce
description: Scopri ulteriori informazioni su suggerimenti sulle prestazioni di hosting autonomo, idee e concetti e best practice da considerare.
landing-page-description: Scopri alcuni concetti e cose da considerare per l’hosting di Adobe Commerce da solo.
short-description: Scopri strategie e concetti di consigli sulle prestazioni per l’hosting autonomo di Adobe Commerce.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
source-git-commit: 66abe9f234aa44f7e07cc024607eeb6591a99d07
workflow-type: tm+mt
source-wordcount: '1308'
ht-degree: 0%

---


# Suggerimenti sulle prestazioni di Adobe Commerce per l’hosting autonomo

L&#39;utilizzo di una piattaforma di e-commerce flessibile e potente non significa che devi sacrificare le prestazioni. Dall’avvio di Adobe Commerce sono stati apportati numerosi miglioramenti all’applicazione di base. Nella versione 2.5.4, il team tecnico di Adobe Commerce ha eseguito un test impostato per eseguire il benchmark dell’applicazione. I risultati del test hanno dimostrato che Adobe Commerce è in grado di gestire un ampio catalogo di oltre 240 milioni di SKU, i tempi di richiesta API hanno una media eccezionale di 300 ms, e il numero di visualizzazioni di pagina e ordini immessi all’ora sono fenomenali arrivando a 2 milioni di visualizzazioni di pagina e 208.000 ordini all’ora.

Vedi gli ultimi risultati di benchmark per rubrica [Experience League - Adobe Commerce - Playbook di implementazione - Benchmark](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/infrastructure/performance/benchmarks.html){target="_blank"}.

Per ottimizzare il più possibile le operazioni, segui questi standard quando aggiungi personalizzazioni e complessità aggiuntiva al progetto.

Le sezioni seguenti trattano argomenti da considerare e consigliare per come ottimizzare l’implementazione di hosting autonomo.

## Vernice

La vernice è un proxy inversa HTTP con la cache. Per quanto possa sembrare complicato, il risultato sono risposte rapide per garantire che le richieste vengano restituite più rapidamente che se dovesse recuperare l’elemento dall’origine. L’esecuzione di un sito Adobe Commerce senza alcuna versione di Varnish rallenta il caricamento delle pagine e genera altre metriche chiave. Vernish può essere un po &#39;difficile da configurare e gestire se stessi, tuttavia abbiamo questo argomento in Experience League [Configura vernice](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cache/varnish/config-varnish.html){target="_blank"} per comprendere meglio il suo utilizzo con Adobe Commerce. Un’alternativa è quella di utilizzare una soluzione basata su cloud. Sebbene ve ne siano molti da considerare, Flast è stata scelta come soluzione per Adobe Commerce sul cloud. È una versione di Flast, basata su cloud, che utilizza VCL e molti sfaccettature di vernice.

Trovare una soluzione che si adatti al meglio alle tue applicazioni, configurazioni, budget e capacità tecniche è difficile da realizzare. L’utilizzo di un’opzione basata su cloud fa scomparire tutte le parti hardware fino a quando vengono considerati la gestione, la configurazione, i server e altri componenti dell’infrastruttura. È stata scelta da Adobe Commerce sul team cloud come soluzione a causa delle sue prestazioni, della sua scalabilità, del suo throughput e di molte altre metriche chiave.

Scegliendo una buona soluzione per il tuo progetto per quanto riguarda Varnish, ti stai configurando per le migliori prestazioni per i tuoi clienti e salva l&#39;applicazione commerce dal lavorare più duramente del necessario.

## CDN

Insieme a Varnish come risorsa preziosa per il tuo progetto Adobe Commerce, il prossimo in linea è una CDN. Insieme alla versione, una rete CDN può fornire istanze memorizzate nella cache per il CSS, pagine di risorse come le immagini per ridurre la larghezza di banda proveniente dall’applicazione Adobe Commerce. Può memorizzare in cache le risposte di GraphQL che incrementano i vantaggi di un sito Adobe Commerce headless. Alcune CDN forniscono l&#39;ottimizzazione delle immagini, un firewall per applicazioni web e altre funzionalità.

Adobe Commerce su cloud ha scelto di utilizzare Flast per la sua cache Varnish ma anche come CDN. Questa singola soluzione offre una miriade di funzioni per fornire una grande esperienza per Adobe Commerce sui clienti cloud. È possibile leggere la panoramica dei servizi finali in Experience League [Panoramica dei servizi finali](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/fastly.html){target="_blank"}

Una rete CDN fornisce contenuti di consegna ottimizzati e sicuri per il progetto Adobe Commerce. Se questo non è un componente obbligatorio per il progetto, deve essere considerato come il sito matura e il numero di visitatori aumenta. Fornendo una rete CDN, è possibile ritardare l&#39;aggiunta di hardware aggiuntivo all&#39;infrastruttura o il ridimensionamento dell&#39;infrastruttura esistente a causa del carico rimosso da ogni richiesta.

## Disattiva moduli

La disattivazione di un modulo non utilizzato deve essere presa in considerazione, ma non deve essere presa alla leggera. Questa tecnica riduce alcuni sovraccarichi e tempi di elaborazione per alcune richieste, ma ci sono effetti collaterali che devono essere considerati. In alcuni casi, quando uno sviluppatore assume che un modulo è disponibile durante la creazione di funzionalità, Questo spesso è sicuro, a meno che non abbiano scelto di utilizzare alcune classi presenti in un modulo disabilitato.

La disattivazione di un modulo come la &quot;newsletter&quot; nativa è un evento abbastanza comune. Questo vale soprattutto quando il proprietario del negozio ha una società di terze parti che gestisce la newsletter. Questo può essere un problema quando viene installato un modulo di terze parti e per qualche motivo hanno deciso di utilizzare una classe dalla newsletter. Questa dipendenza accidentale verrà probabilmente rilevata durante alcune installazioni e test iniziali, ma poi si è costretti a decidere se si desidera mantenere questo modulo di terze parti, abilitare newsletter e quindi testare la regressione del sito alla ricerca di qualsiasi comportamento dispari che viene introdotto. Oppure trovi una sostituzione per quel modulo di terze parti. Entrambe le decisioni comportano rischi, tempo e forse errori.

Prima di disattivare i moduli inutilizzati, assicurarsi di non disporre di test quali l&#39;unità, [MFTF](https://developer.adobe.com/commerce/cloud-tools/docker/test/application-testing/){target="_blank"}, [Codeception testing](https://developer.adobe.com/commerce/cloud-tools/docker/test/code-testing/){targe="_blank"} test di caricamento o richieste API che potrebbero essere interessate.

## Richiedi che siano rispettati gli standard di codifica Adobe Commerce e PHP per ogni richiesta di pull

Adobe Commerce ha un set di [Standard di codifica](https://developer.adobe.com/commerce/php/coding-standards/){target="_blank"}. Questi consentono di garantire che venga seguito un modello, uno stile e una progettazione simili, indipendentemente dal tipo di sviluppo software. Se si tratta di un requisito fondamentale da seguire è quando si contribuisce alla base di codice di Adobe Commerce. Tuttavia, il rispetto di questa metodologia per lo sviluppo personalizzato crea anche una solida pietra miliare per tutti gli sviluppatori, attuali e future. Quando richiedi a tutte le richieste di pull di passare uno standard di codice, assicurati che tutti possano comprendere e attendersi gli stessi pattern di sviluppo coerenti.

Per accompagnare gli standard di codifica Adobe Commerce, l&#39;altra base utilizzata è gli standard di codifica di base PHP. Deve essere chiaramente definito nelle guide per gli sviluppatori quali standard sono necessari per seguire ed eventuali deviazioni accettabili. Tuttavia, un fallback dovrebbe essere alla guida gestita pubblicamente disponibile all&#39;indirizzo [PHP-FIG](https://www.php-fig.org){target="_blank"}.

Una posizione ferma sul seguito dei modelli PSR-1 e PSR-12. Garantire che gli sviluppatori che contribuiscono al progetto seguano questi passaggi aiuta a garantire che non ci siano file e pattern stranamente strutturati. Questo aiuta anche a garantire che i futuri sviluppatori possano leggere e comprendere rapidamente il codice che stanno revisionando. Più si seguono questi modelli e gli standard di codifica, più le iniziative future di sviluppo dovrebbero essere più facili da leggere e più veloci da implementare.

## Esegui test di carico dopo ogni distribuzione

L&#39;esecuzione di un test di carico dopo ogni distribuzione può sembrare eccessiva. Tuttavia, se si segue questa metodologia, è possibile tenere traccia e attenuare l’opportunità di nuove funzioni che causano una diminuzione delle prestazioni.

Oltre a rilevare il peggioramento delle prestazioni dal nuovo codice, l&#39;utilizzo di un riferimento storico delle metriche chiave dal sito può fornire indicazioni su quando è abilitato un nuovo strumento o una nuova infrastruttura di modifica. Ad esempio, prima di pagare la società di hosting per aumentare le dimensioni dell&#39;ambiente e sperare di ottenere l&#39;aumento delle prestazioni previsto, puoi impostare un ambiente di staging con le nuove configurazioni ed eseguire un test di carico per vedere quale sarebbe il risultato effettivo.

Questi test possono essere automatizzati e fanno parte della pipeline CI/CD. A causa di questo, è anche possibile avere regole che prendono i risultati e potenzialmente bloccano l&#39;unione di feature se si verifica troppa deviazione dalla norma. Il numero di casi d&#39;uso per questi dati è illimitato, ma senza avviare questo processo si potrebbe mai realizzare il suo potenziale.

Adobe Commerce ha una buona scrittura su questo argomento trovato in Experience League [Suggerimenti per il test delle prestazioni](https://experienceleague.adobe.com/docs/commerce-operations/deliver-commerce-at-scale/launch.html){target="_blank"} and in [Testing guidance](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/guidance.html){target="_blank"}.

{{$include /help/_includes/hosting-related-links.md}}
