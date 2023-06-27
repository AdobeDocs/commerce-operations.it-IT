---
title: Suggerimenti per il test delle prestazioni
description: Scopri come impostare i KPI per l’avvio delle soluzioni Adobe Commerce e Adobe Experience Manager.
exl-id: 4b0d9c4f-e611-452d-a80f-27f82705935d
topic: Commerce, Performance
source-git-commit: 76ccc5aa8e5e3358dc52a88222fd0da7c4eb9ccb
workflow-type: tm+mt
source-wordcount: '1147'
ht-degree: 0%

---

# Suggerimenti per il test delle prestazioni

Per valutare l’efficacia di tutte le modifiche di cui sopra, è necessario eseguire test approfonditi delle prestazioni prima del lancio e prima di qualsiasi implementazione futura importante negli ambienti di produzione. Quando pianifichi il test di carico, è importante simulare il più possibile il traffico consumer reale.

Le aree del sito AEM/CIF/Adobe Commerce che richiedono un uso intensivo delle risorse sono quelle che non sono memorizzabili in cache, come la procedura di pagamento e la ricerca del sito. La navigazione nelle pagine statica, e quindi memorizzabile in cache, come ad esempio Produce Detail Pages (PDP) e Product Listing Pages (PLP), costituisce la maggior parte del traffico verso un sito di e-commerce in generale, pertanto gli script e gli scenari nel test dovrebbero rispecchiare questo fatto per misurare i limiti della piattaforma.

Avere un singolo script in esecuzione per il test di carico che naviga attraverso il sito senza tempo di attesa tra i passaggi, e anche sempre completa il processo di pagamento ogni volta non darebbe un&#39;indicazione affidabile dei limiti della piattaforma, in quanto non è quello che sarebbe uno scenario reale.

La definizione dei KPI deve essere il primo passo del piano di test delle prestazioni: definire metriche che possono essere testate durante il test iniziale e poi misurate di nuovo in futuro e in modo ricorrente dopo che il sito è attivo. Questo consente di monitorare le prestazioni del sito nel tempo: prima e dopo il lancio. Esempio di KPI da definire:

- Tempo medio di risposta: tempo al primo o all&#39;ultimo byte
- Latenza
- Byte/s (Througput)
- Percentuale di errori
- Ordini all&#39;ora
- Visualizzazioni pagina all&#39;ora
- Utenti univoci all’ora (acquirenti simultanei)

## Linee guida Jmeter

Le seguenti linee guida di alto livello Jmeter devono essere considerate durante lo sviluppo del test di carico AEM/CIF/Adobe Commerce:

- Suddividi lo script in scenari configurabili, ad esempio:
   - Apri Home Page
   - Apri pagina categorie (PLP)
   - Visualizza prodotti semplici (PDP): 2 cicli all’interno di ogni iterazione
   - Visualizza prodotti configurabili: 2 cicli all’interno di ogni iterazione
      - Ad esempio, imposta i passaggi precedenti al 60% del traffico
   - Ricerca prodotti
      - Ad esempio, imposta la ricerca nel catalogo al 37% del traffico
   - Carrello e pagamento
      - Ad esempio, un utente che completa la parte relativa al carrello e al pagamento dello script deve ottenere per impostazione predefinita un tasso di conversione del sito di e-commerce standard di circa il 3%
      - Poiché il flusso di pagamento non viene memorizzato in cache e in genere richiede un’intensa quantità di risorse, impostare una cifra irrealisticamente elevata per il numero di persone che completano gli ordini rispetto al numero di browser del sito darebbe un risultato inaffidabile per il volume di traffico che il sito potrebbe gestire.
- Pulisci tutte le cache prima di ogni esecuzione del test:
   - È necessario pulire completamente la cache del dispatcher AEM
   - La cache Fastly e interna di Adobe Commerce deve essere completamente svuotata e pulita: questo può essere fatto tramite il controllo della cache nell’amministratore Adobe Commerce.
- Includi un periodo di rampa nel test Jmeter: se non è impostato alcun periodo di rampa, non si verifica un aumento graduale del traffico e non si ha la possibilità che il sito memorizzi in cache le pagine e i componenti della pagina visitati di frequente. In uno scenario reale, sarebbe insolito che tutto il traffico di picco arrivasse su un sito completamente non memorizzato in cache esattamente nello stesso momento, quindi dovrebbe essere incluso un periodo di rampa negli script di test Jmeter per consentire alla cache di accumularsi come accadrebbe su un sito di e-commerce reale.
- Dovrebbe essere utilizzato un &quot;Tempo di attesa&quot; tra ogni passaggio all’interno di un’iterazione; in realtà, un utente non passerebbe immediatamente alla pagina successiva del sito durante il percorso; si verificherebbe un tempo di attesa durante la lettura della pagina da parte dell’utente, che deciderebbe quindi in merito all’azione successiva.
- Impostando i gruppi di filettature su loop infinito, ma per un tempo impostato di x (ad esempio 60 minuti), si otterrà un test ripetibile, con tempi di risposta mediani comparabili a quelli delle esecuzioni precedenti. Ciò significa che dopo il periodo di avvio impostato, sarà presente il numero target di utenti virtuali in esecuzione simultanea e questo continuerà per il tempo di loop impostato.
- Il tempo mediano deve essere utilizzato per fornire un miglioramento/declino del tempo medio di risposta, non del tempo medio. Se ci sono diversi risultati edge che richiedono molto più tempo degli altri risultati, questo distorcerebbe il risultato medio, ma ci interessa il tempo di risposta dell’utente finale per la maggior parte degli utenti, che è più adatto alla misura mediana.
- Le risorse incorporate non vengono raccolte per impostazione predefinita in jmeter (ad esempio JS, CSS e altre risorse scaricate quando un utente reale visita la pagina). Questa può essere abilitata, ma solo per il dominio che stai testando, le chiamate a risorse esterne devono comunque essere escluse (ad esempio, non vogliamo includere i tempi di risposta da servizi ospitati esternamente, ad es. google analytics (codice google analytics, poiché non abbiamo alcun controllo su di essi).
- Se è necessario abilitare HTTP Cache Manager, questo consente a Jmeter di memorizzare nella cache gli elementi di una pagina durante un percorso, come farebbe il percorso di un utente reale durante la navigazione del sito web sul proprio browser. Durante il percorso attraverso il sito, il browser dell’utente scarica le relative risorse incorporate una sola volta e poi queste vengono memorizzate nella cache dal browser dell’utente. Inoltre, se lo stesso utente ritorna sul sito qualche tempo dopo la visita originale, allora potrebbe ancora essere la cache che quelle risorse vengono memorizzate in cache.
- I listener devono essere mantenuti all’interno delle esecuzioni effettive del test di carico (ad esempio &quot;Visualizza struttura risultati&quot; e &quot;Rapporto aggregato&quot;). L’inclusione di questo valore nell’esecuzione dei test di carico reale senza interfaccia grafica utente grafica può influire sui risultati delle prestazioni riportati da Jmeter, in quanto le risorse vengono utilizzate durante l’esecuzione dei test reali per generare i rapporti. Questi listener sono stati rimossi dallo script di test per essere sostituiti con un file di risultati JTL, che può quindi essere elaborato utilizzando la funzionalità Report Dashboard di Jmeter.
- Un tempo di risposta target per valutato in modo che il &quot;Punteggio approssimativo&quot; del rapporto del dashboard possa essere utilizzato come modo rapido per misurare l’effetto delle modifiche sulle prestazioni tra le esecuzioni dei test. Il punteggio Apdex si basa sulla capacità di una certa quantità di persone di accedere al sito in un tempo tollerabile . Se il tempo di risposta supera un certo importo &quot;frustrante&quot;, il punteggio si abbassa. I tempi possono essere impostati utilizzando i parametri &quot;apdex_satisfaction_ threshold&quot; e &quot;apdex_tolerated_threshold&quot;.
- Imposta una metrica target &quot;Ordini per ora&quot; da presentare agli utenti aziendali, non un conteggio di utenti virtuali. &quot;Utenti virtuali&quot; può essere un argomento complesso per capire cosa viene misurato nella vita reale del test. Calcolando il tasso di conversione del sito, gli ordini all’ora, il tempo medio trascorso da un utente sul sito e il tempo di riflessione tra ciascun caricamento di pagina, è possibile utilizzare i calcoli standard di settore per presentare diversi scenari di test di carico in base agli ordini all’ora da raggiungere.
- Infine, il server di test Jmeter deve essere eseguito su un server geograficamente vicino a dove proviene la maggior parte del traffico utente e dove è ospitata l’infrastruttura cloud, si spera che sia lo stesso.
