---
title: Disaster recovery Adobe Commerce con hosting autonomo
description: Scopri le idee e i concetti di disaster recovery self-hosting e le best practice da considerare.
landing-page-description: Scopri alcuni concetti e aspetti di disaster recovery da considerare quando ospiti Adobe Commerce.
short-description: Scopri le strategie e i concetti di disaster recovery per l’hosting di Adobe Commerce.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
exl-id: cab6213b-da44-498f-b5c1-e7f89e95038e
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1771'
ht-degree: 0%

---

# Idee di Adobe Commerce per il disaster recovery self-hosting

Il disaster recovery per questo articolo include una distribuzione non riuscita. Anche se l&#39;intero processo può non essere lo stesso, si applicano principi simili. Un guasto può essere dovuto a una mancata distribuzione della produzione, a una mancata risposta del server, all&#39;individuazione di un exploit e a molti altri scenari. Se il processo di ripristino per una distribuzione non riuscita può richiedere solo due semplici passaggi, un ripristino da un exploit potrebbe essere molto più complesso. A causa della complessità degli ambienti, delle varianti di hosting e di altre complessità, questo articolo fornisce idee e concetti, ma è necessario continuare l’indagine da soli. In questo modo, puoi progettare una strategia che soddisfi le tue esigenze aziendali.

## Processo di recupero delle esercitazioni spesso

Pratica, Pratica, Pratica. Esiste un motivo per cui le procedure vengono visualizzate per prime nell&#39;elenco di disaster recovery. L&#39;elaborazione di un piano di risanamento è molto semplice, ma non è mai stata eseguita. Se non si pratica abbastanza, si è inclini a errori, passaggi saltati e probabilmente fare un ripristino effettivo richiedere più tempo. La cadenza per il ripristino dell&#39;esercitazione dipende da voi e dai vostri partner commerciali. Rendere il processo di ripristino un evento annuale potrebbe essere sufficiente, ma una conversazione approfondita con i responsabili decisionali della tua azienda dovrebbe includere diversi argomenti chiave. Questi argomenti li aiutano a capire perché praticare è importante e dovrebbe essere previsto. Di seguito sono riportati alcuni argomenti utili per iniziare la conversazione:

* L’esercitazione riduce i tempi di inattività effettivi quando si verifica un evento reale. Se un&#39;esercitazione di prova provoca il blocco del sito per un&#39;ora all&#39;anno, il downtime effettivo di un evento reale potrebbe essere ridotto di diverse ore. Non è raro che il ripristino di un sito richieda almeno otto ore. Praticando questo evento spesso è possibile ridurre il tempo necessario per ogni fase e ripristinare più rapidamente.
* I tempi di inattività pianificati per queste esecuzioni possono coincidere con le patch del server, le regolazioni di inventario o qualsiasi altra operazione che deve essere eseguita regolarmente.
* Esercitare scenari diversi invece di uno stesso. Occasionalmente, prendere il tempo necessario per eseguire un ripristino completo da una data precedente. Ciò include elementi quali la ricerca e l’utilizzo di una copia archiviata del database, il rollback del codice in modo che corrisponda alla data. Un modo più semplice potrebbe essere il ripristino da una distribuzione non riuscita, in cui è sufficiente eseguire il rollback al commit precedente.
* Verificare che il processo di ripristino funzioni effettivamente, a volte i database archiviati possono danneggiarsi. In questo modo, si assicura che tutto possa essere recuperato e sia funzionale. La ricerca e il ripristino di un vecchio database richiedono tempo, è necessario conoscere la durata di questa parte del processo.
* Verifica che tutte le modifiche nelle configurazioni siano documentate. In questo modo, qualsiasi ripristino da un database precedente che apporti nuove modifiche alla configurazione deve essere funzionante. Ad esempio, se la chiave API è stata modificata nel processore dei pagamenti negli ultimi giorni. Grazie a un buon processo di gestione delle modifiche, la ricerca di questi aggiornamenti chiave fa sì che il processo vada come pianificato.

## Backup del database

I backup del database devono essere abbastanza regolari. Non è raro disporre di istantanee orarie, giornaliere, settimanali e mensili. I backup dovrebbero essere trasferiti allo storage a lungo termine. Questo storage a lungo termine può verificarsi quando il team aziendale o tecnologico decide che è trascorso un tempo sufficiente e che probabilmente non è più necessario ripristinarlo rapidamente. Un ripristino da uno storage a lungo termine aggiunge tempo al processo di ripristino, pertanto è necessario prestare attenzione nel decidere quando ciò dovrebbe verificarsi. I backup del database devono essere automatizzati e non dipendere dall’interazione umana. In questo modo è possibile disporre di un numero sufficiente di tali componenti per garantire un processo di ripristino sicuro e prevedibile. Questo aiuta anche in qualsiasi attività forense, se tale attività è necessaria, è fattibile e affidabile. Potresti trovare la necessità di una ricerca forense dopo che un exploit è stato rilevato, o quando si cerca di diagnosticare quando si è verificata un&#39;attività di frode della carta di credito o anche quando qualcuno si è unito al tuo sito web. Non vi è alcun limite al modo in cui si utilizzano questi backup, ma avere una buona cadenza di backup è la vostra grazia di salvataggio quando effettivamente ne avete bisogno.

Di seguito è riportato un esempio di criteri di conservazione dei dati:

* Ogni otto ore. I backup devono essere facilmente accessibili.
* Backup giornalieri degli ultimi sette giorni, facilmente accessibili. Una copia di questi potrebbe essere un candidato per essere spostato fuori sede.
* I backup settimanali delle ultime quattro settimane prendono in considerazione l&#39;eventualità di spostarsi fuori sede.
* i backup mensili degli ultimi tre mesi sono stati trasferiti fuori sede.
* I backup meno recenti vengono spostati fuori sede nello storage a lungo termine.

## Infrastruttura come codice

Grazie a questa metodologia, è possibile disporre di strumenti e codice per la ricostruzione di parti o dell&#39;intera infrastruttura per il progetto. Questo può essere necessario quando si verificano problemi con un server e deve essere rimosso dall’utilizzo. Essere in grado di portare rapidamente online un nuovo server, distribuire il codice, effettuare qualsiasi configurazione PHP, Nginx o Apache, e qualsiasi altra cosa, automaticamente significa meno tempi di inattività. Anche i passaggi ben documentati in un manuale di esecuzione sono più facili da impostare, per eseguire i passaggi richiede molto più tempo. Inoltre, considera l’errore umano che può verificarsi quando si è sotto stress per riportare online un sito che non risponde.

## Database secondario

L&#39;utilizzo di un database secondario può essere utile per alcuni motivi, ad esempio:

* Standby a caldo in caso di guasto dell&#39;unità principale
* Consenti richieste pronte dall’applicazione
* Consenti l&#39;esecuzione di mysqldump e l&#39;esecuzione di transazioni normali senza bloccare il database
* Consente l’accesso ai dati da un’origine dati esterna senza ridurre la capacità dei siti web di negoziare le informazioni per le richieste dei clienti.

Il database secondario può essere utilizzato come `warm standby`. Ciò può verificarsi quando si sta valutando la modalità di ripristino da un errore del database primario. La promozione del database secondario a primario è meno complessa rispetto alla ricostruzione e al ripristino di un database in un&#39;istanza Mysql appena creata. In questo modo si riducono i tempi di inattività effettivi durante un&#39;operazione di ripristino.

È possibile deviare alcune richieste nel database secondario. Se si utilizza questo metodo, si consiglia di rendere il database secondario di sola lettura. Consentendo all’applicazione Adobe Commerce di utilizzare questo database secondario per le operazioni di lettura, è più facile accettare alcune delle richieste di lettura e consentire al database secondario di rispondere. Tuttavia, questa modifica rappresenta solo il 30-50% di tutte le richieste, ma qualsiasi carico che puoi rimuovere dal database primario è una vittoria.

## Creare un piano di distribuzione che includa un rollback

Ogni implementazione deve includere un piano di rollback. Sì, ogni installazione. Se hai intenzione di farlo, non sei mai sorpreso e sei pronto per il brutto evento. A volte gli aggiornamenti di codice più semplici possono avere esito negativo in modo irreversibile per qualsiasi motivo.

Considera questa storia vera di un team che ha eseguito una piccola, semplice richiesta di pull per eseguire una modifica dello schema nel database. Con il passare da 1 minuto, a 5, poi a 10, il team si preoccupò sempre di più. Ciò che fino a questo momento non è stato verificato e considerato è stata una discrepanza dal database di produzione rispetto al database dell&#39;area di gestione temporanea. Avevano una pratica comune per rimuovere tutti i dati dei clienti durante l&#39;aggiornamento dell&#39;ambiente di staging con una copia della produzione. Questo significava che il completamento di tutti i test e il QA precedenti rispecchiavano l’implementazione in pochi minuti. In realtà, avevano oltre 20 milioni di clienti e il completamento di questa piccola modifica dello schema impiegava un tempo eccezionalmente lungo. Poiché non avevano idea di quanto tempo ci sarebbe voluto, sono stati costretti a terminare il processo mysql e a ripristinare la distribuzione.

La preparazione di un processo di rollback per una distribuzione richiede solo pochi minuti perché il processo complessivo sarà simile. Tuttavia, dovresti prenderti il tempo necessario per documentare esattamente a quale impegno ripristineresti le HEAD dell’archivio Git. È necessario documentare esattamente quale snapshot di database utilizzare o dove trovare quello corrente, se questo si trova sempre nello stesso punto. Definire i momenti in cui è necessario discutere lo stato della distribuzione e quando le cose diventano automaticamente effettive. Ad esempio, se una distribuzione richiede più di 15 minuti, chiedi al project manager e alle altre parti interessate se le cose devono continuare. Tuttavia, esegui automaticamente il processo di rollback e avvisa tutte le parti interessate se il processo richiede 45 minuti, indipendentemente da eventuali esitazioni da parte del project manager e dell’architetto del progetto.

Assicurati che diverse persone siano coinvolte nell’intero processo e in ogni fase. La possibilità per gli sviluppatori di livello intermedio di esaminare il processo di distribuzione, la procedura di rollback e la posizione dei file è un ottimo modo per coinvolgerli. Alla fine eseguiranno i passaggi necessari, in modo che comprendano l’intero processo sia fondamentale per il successo a lungo termine. Assicurati che tutti abbiano la possibilità di annullare una distribuzione. Dare al tuo team tutta questa voce in capitolo significa dare più potere e ricompensare. Se uno sviluppatore giovane sente davvero che qualcosa manca, dovrebbe sentirsi obbligato a parlare più forte e lasciare che la sua cautela sia ascoltata. Lasciate che l&#39;architetto e i project manager confermino o attenuino la loro paura. È importante avere un team forte che sia alla ricerca del progetto e mantenga traccia delle implementazioni impeccabili.

## Verificare l&#39;accesso alla gestione dei nomi di dominio, DMS, SSL, WAF

Poiché i nomi di dominio scadono, i record DNS possono essere modificati accidentalmente, i certificati SSL possono scadere e molto altro ancora; assicurati di avere la possibilità di accedere e verificare che la connettività sia attiva spesso. Facendo questo semplice controllo ogni trimestre si è sicuri di sapere esattamente dove si trovano le cose, soprattutto in un&#39;emergenza. Non presumere che il DNS sia gestito nel programma di registrazione solo per scoprire di averlo gestito in Amazon. Questi record non vengono utilizzati frequentemente, quindi è molto probabile che si dimentichi dove si trovano. Non considerare attendibile la documentazione scritta solo per nomi utente e password. Accedi a ciascuno di essi e verifica che le configurazioni che stai cercando siano effettivamente gestite lì. Troppo spesso le cose cambiano durante il turnover della direzione o l&#39;acquisizione di un&#39;azienda e solo una persona sa cosa è successo, perché sono loro che hanno fatto l&#39;aggiornamento. Non sapevano che ci si affidasse a un documento di Word condiviso per determinare la posizione, il nome utente e la password. Trovare un processo di controllo appropriato per te e per la tua organizzazione, ma farlo ogni tre o sei mesi è un buon punto di partenza.

{{$include /help/_includes/hosting-related-links.md}}
