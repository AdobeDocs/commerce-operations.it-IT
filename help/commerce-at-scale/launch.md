---
title: Suggerimenti per il test delle prestazioni
description: Scopri come impostare i KPI per l’avvio della soluzione Adobe Commerce e Adobe Experience Manager.
exl-id: 4b0d9c4f-e611-452d-a80f-27f82705935d
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '1147'
ht-degree: 0%

---

# Suggerimenti per il test delle prestazioni

Per valutare l’efficacia di tutte le modifiche di cui sopra, è necessario eseguire un test completo delle prestazioni prima del lancio e prima di eventuali implementazioni principali future negli ambienti di produzione. Quando pianifichi il tuo test di carico, è importante simulare il più possibile il traffico dei consumatori a vita reale.

Le aree del sito AEM/CIF/Adobe Commerce a uso intensivo di risorse sono quelle che non sono memorizzabili nella cache, ad esempio il processo di pagamento e la ricerca nel sito. La navigazione delle pagine statica e quindi memorizzabile nella cache, ad esempio per le pagine dei dettagli dei prodotti (PDP) e le pagine degli elenchi dei prodotti (PLP), rappresentano in genere la maggior parte del traffico verso un sito di e-commerce, pertanto gli script e gli scenari del test dovrebbero riflettere tale aspetto per misurare i limiti della piattaforma.

Avere un singolo script in esecuzione per il test di carico che naviga attraverso il sito senza tempi di attesa tra i passaggi, e anche completare sempre il processo di pagamento ogni volta, non darebbe un&#39;indicazione affidabile dei limiti della piattaforma, in quanto questo non è ciò che uno scenario reale sarebbe.

La definizione dei KPI deve essere il primo passo del piano di test delle prestazioni: definisci le metriche che puoi sottoporre a test durante il test iniziale, ma che potrai quindi misurare nuovamente in futuro, e su base ricorrente dopo la pubblicazione del sito. Questo consente di monitorare le prestazioni del sito nel tempo, prima e dopo il lancio. Esempio di KPI da definire:

- Tempo medio di risposta: tempo al primo byte o all&#39;ultimo byte
- Latenza
- Byte/s (Througput)
- Frequenza errori
- Ordini all&#39;ora
- Visualizzazioni pagina all&#39;ora
- Utenti univoci all&#39;ora (acquirenti simultanei)

## Linee guida di Jmetro

Quando si sviluppano i test di carico AEM/CIF/Adobe Commerce, è necessario tenere in considerazione le seguenti linee guida di livello elevato di Jmetro:

- Dividi lo script in scenari configurabili, che dovrebbero riguardare, ad esempio:
   - Apri home page
   - Apri pagina categoria (PLP)
   - Visualizza prodotti semplici (PDP) - 2 loop all’interno di ogni iterazione
   - Visualizza prodotti configurabili - 2 loop all’interno di ogni iterazione
      - Ad esempio, imposta i passaggi precedenti al 60% del traffico
   - Ricerca di prodotti
      - Ad esempio, imposta la ricerca nel catalogo al 37% del traffico
   - Carrello e pagamento
      - Ad esempio, per impostazione predefinita, un utente che completa la parte del carrello e il pagamento dello script deve applicare un tasso di conversione del sito e-commerce standard del settore di circa il 3%
      - Poiché il flusso di pagamento viene rimosso dalla cache e solitamente un’operazione ad alta intensità di risorse, l’impostazione di una cifra irrealisticamente elevata per il numero di persone che completano gli ordini rispetto al numero di browser del sito darebbe un risultato inaffidabile per il volume di traffico che il sito potrebbe gestire.
- Pulisci tutte le cache prima di ogni esecuzione del test:
   - La cache del dispatcher AEM deve essere pulita completamente
   - La cache finale e interna di Adobe Commerce deve essere completamente scaricata e pulita - questo può essere fatto tramite il controllo della cache nell’amministratore di Adobe Commerce.
- Includi un periodo di rampa nel test Jmetro: Non impostare alcun periodo di rampa significa che non vi è un aumento graduale del traffico e non è possibile che il sito memorizzi nella cache una qualsiasi delle pagine e dei componenti visitati di frequente nella pagina. Nella vita reale, sarebbe insolito che tutto il traffico di picco arrivasse su un sito completamente non memorizzato nella cache esattamente allo stesso tempo, quindi dovrebbe essere incluso un periodo di rampa negli script di test Jmetro per consentire alla cache di accumularsi come accadrebbe su un sito di e-commerce reale.
- Dovrebbe essere utilizzato un &quot;Tempo di attesa&quot; tra ogni passaggio all’interno di un’iterazione, in realtà un utente non passa immediatamente alla pagina successiva del sito durante il percorso, ma ci sarà un tempo di attesa mentre l’utente legge la pagina e decide la propria azione successiva.
- L&#39;impostazione dei gruppi di thread su loop infinitamente, ma per un periodo di tempo impostato di x (ad esempio 60 minuti), darà una prova ripetibile, con tempi di risposta mediani confrontabili con le prove precedenti. Ciò significa che dopo il periodo di aggiornamento impostato, ci sarà il numero di destinazione di Utenti virtuali in esecuzione contemporaneamente e questo continuerà per il tempo di ciclo impostato.
- Il tempo medio dovrebbe essere utilizzato per fornire un miglioramento/diminuzione del tempo medio di risposta, non della media. Se ci sono diversi risultati edge che richiedono molto più tempo rispetto agli altri risultati, questo potrebbe distorcere questo risultato medio, ma ciò a cui siamo interessati nel tempo di risposta dell&#39;utente finale per la maggior parte degli utenti, che è più adatto alla misura media.
- Le risorse incorporate non vengono raccolte per impostazione predefinita in jmetro (ad esempio, JS, CSS e altre risorse scaricate quando un utente reale visita la pagina). Può essere abilitato, ma solo per il dominio di cui stai eseguendo il test: le chiamate a risorse esterne devono ancora essere escluse (ad esempio, non vogliamo includere i tempi di risposta dai servizi in hosting esterni, ad esempio codice di google analytics, in quanto non abbiamo controllo su di loro).
- È necessario abilitare HTTP Cache Manager, che consente a Jmetro di memorizzare nella cache gli elementi di pagina durante un percorso come farebbe un vero percorso di utenti durante la navigazione del sito web sul proprio browser. Durante il percorso in cui si trovava il sito, il browser dell’utente scaricava le risorse incorporate correlate una sola volta e queste venivano memorizzate nella cache dal browser dell’utente. Inoltre, se lo stesso utente ritorna al sito qualche volta dopo la visita originale, potrebbe comunque essere la cache in cui tali risorse vengono memorizzate nella cache.
- Gli ascoltatori devono essere tenuti all’interno delle esecuzioni effettive del test di carico (ad esempio &quot;Visualizza albero risultati&quot; e &quot;Rapporto aggregato&quot;). Includere questo nell&#39;esecuzione del test di carico reale non-GUI può influenzare i risultati delle prestazioni segnalati da Jmetro, in quanto le risorse vengono utilizzate durante l&#39;esecuzione del test reale per generare i rapporti. Questi ascoltatori sono stati rimossi dallo script di test per essere sostituiti con un file di risultati JTL, che può quindi essere elaborato utilizzando la funzionalità Dashboard dei report di Jmetro.
- Un tempo di risposta di destinazione per valutato in modo che il &quot;Punteggio dell’Apdex&quot; del rapporto del dashboard possa essere utilizzato rapidamente per misurare l’effetto dei cambiamenti sulle prestazioni tra le esecuzioni dei test. Il punteggio Apdex si basa su una certa quantità di persone in grado di accedere al sito in un tempo tollerabile . Se il tempo di risposta supera una certa quantità &quot;frustrante&quot;, questo riduce il punteggio. I tempi possono essere impostati utilizzando i parametri &quot;apdex_purchased_ soglia&quot; e &quot;apdex_Allowated_soglia&quot;.
- Imposta una metrica di destinazione &quot;Ordini all’ora&quot; da presentare agli utenti aziendali, non un conteggio di utenti virtuali. Gli &quot;utenti virtuali&quot; possono essere un argomento complesso per comprendere cosa in tempo reale sta misurando il test. Calcolando il tasso di conversione del sito, gli ordini all&#39;ora, il tempo medio trascorso da un utente sul sito e il tempo impiegato tra ciascun caricamento di pagina, è possibile utilizzare i calcoli standard del settore per presentare diversi scenari di test di carico basati su ordini all&#39;ora da raggiungere.
- Infine, il server di test Jmetro deve essere eseguito su un server geograficamente vicino a dove proviene la maggior parte del traffico degli utenti e da dove è ospitata l&#39;infrastruttura cloud - si spera che sia lo stesso.
