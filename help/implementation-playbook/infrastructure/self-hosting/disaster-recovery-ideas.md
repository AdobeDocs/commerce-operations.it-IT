---
title: Recupero di emergenza di Adobe Commerce self-hosting
description: Scopri le idee e i concetti e le best practice per il disaster recovery in hosting autonomo da considerare.
landing-page-description: Scopri alcuni concetti e cose da considerare per l’hosting di Adobe Commerce da solo.
short-description: Scopri strategie e concetti di disaster recovery per l’hosting autonomo di Adobe Commerce.
kt: 11420
doc-type: tutorial
audience: all
last-substantial-update: 2023-04-13T00:00:00Z
source-git-commit: 6e361169889c8fe1c176d3a3283d52699dfa3b85
workflow-type: tm+mt
source-wordcount: '1771'
ht-degree: 0%

---


# Idee di Adobe Commerce Disaster Recovery self-hosting

Il ripristino di emergenza per questo articolo include una distribuzione non riuscita. Anche se l&#39;intero processo potrebbe non essere lo stesso, si applicano principi simili. Un disastro può essere dovuto a un&#39;implementazione di produzione non riuscita, server che non risponde, individuazione di un exploit e molti altri scenari. Se il processo di recupero per un&#39;implementazione non riuscita può richiedere solo due semplici passaggi, un recupero da un&#39;implementazione di exploit può essere molto più impegnativo. A causa della complessità degli ambienti, delle varianti di hosting e di altre complessità questo articolo fornisce idee e concetti, ma è necessario continuare l&#39;indagine da solo. In questo modo è possibile progettare una strategia adatta alle esigenze aziendali.

## Pratica del processo di recupero spesso

Pratica, Pratica, Pratica. C&#39;è un motivo per cui le pratiche appaiono prima nell&#39;elenco di disaster recovery. È molto facile impostare un piano di recupero ma non eseguirlo mai. Se non si pratica abbastanza, si è inclini a errori, passi persi e probabilmente fare un recupero effettivo richiede più tempo. La cadenza per il recupero del tuo esercizio dipende da te e dai tuoi partner commerciali. Rendere il processo di recupero un evento annuale potrebbe essere abbastanza buono, ma una conversazione approfondita con quei decisori nella tua azienda dovrebbe includere diversi argomenti chiave. Questi argomenti li aiutano a capire perché praticare è importante e dovrebbe essere previsto. Di seguito sono riportati alcuni argomenti utili per avviare la conversazione:

* L&#39;utilizzo consente di ridurre i tempi di inattività effettivi quando si verifica un evento reale. Se un&#39;esecuzione a secco di una pratica abbassa il tuo sito per un&#39;ora all&#39;anno, potrebbe ridurre il tempo di inattività effettivo di un evento reale di diverse ore. Non è raro che il recupero di un sito richieda otto ore o più. Praticando questo evento spesso si può ridurre la quantità di tempo che ogni fase richiede e si è in grado di recuperare più velocemente.
* I tempi di inattività pianificati per queste esecuzioni possono coincidere con le patch del server, le regolazioni dell&#39;inventario o qualsiasi altra operazione da eseguire regolarmente.
* Applicare scenari diversi invece dello stesso. Prenditi il tempo occasionalmente, per fare un recupero completo da una data precedente. Ciò include elementi quali la ricerca e l&#39;utilizzo di una copia archiviata del database, il ripristino del codice in modo che corrisponda alla data. Una soluzione più semplice potrebbe essere un ripristino da una distribuzione non riuscita, in cui è sufficiente eseguire il rollback al commit precedente.
* Verificare che il processo di recupero funzioni effettivamente, a volte i database archiviati possono diventare corrotti. In questo modo si garantisce che tutto possa essere recuperato ed è funzionale. Trovare e ripristinare un vecchio DB richiede tempo, dovrebbe essere noto per quanto tempo questa parte del processo può essere.
* Verifica che tutte le modifiche nelle configurazioni siano documentate. In questo modo è necessario garantire il funzionamento di qualsiasi ripristino da un database precedente con nuove modifiche di configurazione. Ad esempio, se la tua chiave API è stata modificata nel processore dei pagamenti negli ultimi giorni. Con un buon processo di gestione delle modifiche, la ricerca di questi aggiornamenti chiave fa sì che il processo vada come pianificato.

## Backup database

I backup del database devono essere abbastanza regolari. Non è raro avere istantanee orarie, giornaliere, settimanali e mensili. I backup dovrebbero essere spostati in un sistema di storage a lungo termine. Questo storage a lungo termine può essere realizzato ogni volta che il team aziendale o tecnologico decide che il tempo necessario è sufficiente e che probabilmente non è più necessario un rapido ripristino. Un ripristino da uno storage a lungo termine aggiunge tempo al processo di ripristino, pertanto è necessario prestare attenzione nel decidere quando ciò debba verificarsi. I backup del database devono essere automatizzati e non basarsi sull&#39;interazione umana. In questo modo è possibile disporre di un numero sufficiente di elementi per garantire un processo di ripristino sicuro e prevedibile. Questo aiuta anche in qualsiasi attività forense, se tale attività è necessaria, è fattibile e affidabile. Si potrebbe trovare la necessità di ricerca scientifica dopo che un exploit è stato rilevato, o quando si cerca di diagnosticare quando un&#39;attività di frode di carta di credito si è verificato o anche quando qualcuno è entrato nel tuo sito web. Non vi è alcun limite alla modalità di utilizzo di questi backup, ma avere una buona frequenza di backup è la vostra grazia di risparmio quando ne avete effettivamente bisogno.

Esempio di criteri di conservazione dei dati:

* Ogni otto ore. I backup dovrebbero essere facilmente accessibili.
* I backup giornalieri degli ultimi sette giorni devono essere facilmente accessibili. Una copia potrebbe essere un candidato per essere stato spostato fuori sede.
* I backup settimanali delle ultime quattro settimane considerano lo spostamento fuori sede.
* backup mensili per gli ultimi tre mesi spostati fuori sede.
* I backup precedenti vengono spostati in uno storage fuori sede a lungo termine.

## Infrastruttura come codice

Questa metodologia consente di disporre di strumenti e codice per la ricostruzione di parti o dell&#39;intera infrastruttura del progetto. Questo può essere necessario quando un server riscontra problemi e deve essere eliminato dall’uso. Essendo in grado di portare rapidamente online un nuovo server, implementare il codice, fare qualsiasi configurazione PHP, Nginx o Apache, e qualsiasi altra cosa, automaticamente significa meno tempi di inattività. Anche i passaggi ben documentati in un run book sono più facili da configurare, per eseguire i passaggi richiede molto più tempo. Inoltre, considerare l&#39;errore umano che può verificarsi durante lo stress per portare un sito non reattivo di nuovo online.

## Database secondario

L&#39;utilizzo di un database secondario può essere utile per alcuni motivi:

* Standby a caldo se si verifica un guasto dell&#39;unità primaria
* Consenti richieste pronte dall&#39;applicazione
* Consenti il verificarsi di mysqldump e consente che le transazioni normali avvengano senza bloccare il database
* Consente l’accesso ai dati da un’origine dati esterna senza ridurre la possibilità per i siti web di negoziare informazioni per le richieste dei clienti.

Il database secondario può essere utilizzato come `warm standby`. Questo può entrare in gioco quando si sta considerando come recuperare da un errore di database primario. La promozione del database secondario sul database primario è meno complessa rispetto alla ricostruzione e al ripristino di un database in un&#39;istanza Mysql appena creata. Questo riduce i tempi di inattività durante un&#39;operazione di ripristino.

C&#39;è l&#39;opportunità di deviare alcune delle richieste al database secondario. Se si utilizza questo metodo, si consiglia di rendere il database secondario di sola lettura. Consentendo all&#39;applicazione Adobe Commerce di utilizzare questo database secondario per le operazioni di lettura, è utile prendendo alcune delle richieste di lettura e consentendo al database secondario di rispondere. Tuttavia, questa modifica rappresenta solo il 30-50% di tutte le richieste, ma qualsiasi carico che puoi portare via dal database primario è una vittoria.

## Creare un piano di distribuzione che include un rollback

Ogni distribuzione deve includere un piano di rollback. Sì, ogni distribuzione. Se lo pianifichi, non sei mai sorpreso e sei pronto per il cattivo evento. A volte gli aggiornamenti di codice più semplici possono avere un esito negativo catastrofico per qualsiasi motivo.

Considera questa storia vera di un team che ha eseguito una piccola e semplice richiesta di pull per eseguire una modifica dello schema nel database. Mentre il dispiegamento andava da 1 minuto, a 5, poi 10, e il team si preoccupava sempre di più. Ciò che non sono riusciti a verificare e considerare fino a questo punto era una discrepanza dal database di produzione rispetto al database di staging. Avevano una pratica comune di rimuovere tutti i dati dei clienti durante l’aggiornamento dell’ambiente di staging con una copia della produzione. Ciò significa che il completamento di tutti i test e il controllo qualità precedenti all’implementazione avrebbe richiesto solo alcuni minuti. In realtà, avevano più di 20 milioni di clienti e questo piccolo cambiamento di schema richiedeva un tempo eccezionalmente lungo per essere completato. Poiché non avevano idea di quanto tempo ci sarebbe voluto, sono stati costretti a interrompere il processo mysql e a ripristinare l&#39;implementazione.

La preparazione di un processo di rollback per una distribuzione richiede solo pochi minuti perché il processo complessivo sarà simile. Tuttavia, dovresti prendere il tempo di documentare esattamente in quale commit reimposteresti il HEAD dell’archivio Git. È necessario documentare esattamente quale snapshot del database utilizzare o dove trovare quello corrente, se sempre nello stesso punto. Hanno definito i tempi in cui lo stato della distribuzione deve essere discusso e quando le cose diventano automaticamente effettive. Ad esempio, se una distribuzione richiede più di 15 minuti, chiedi al project manager e agli altri azionisti se le cose devono continuare. Tuttavia, esegui automaticamente il processo di rollback e avvisa tutte le parti interessate se il processo richiede 45 minuti, indipendentemente dall’eventuale esitazione da parte del project manager e dell’architetto per il progetto.

Assicurati che più persone siano coinvolte nell&#39;intero processo e in ogni fase. La possibilità per gli sviluppatori di livello intermedio di rivedere il processo di distribuzione, la procedura di rollback e la posizione dei file è un ottimo modo per coinvolgerli. Alla fine eseguiranno i passaggi necessari per far capire loro che l&#39;intero processo è fondamentale per il successo a lungo termine. Assicurati che tutti abbiano il potere di annullare un&#39;implementazione. Dare al tuo team questa quantità di voce è dare potere e gratificante. Se uno sviluppatore giovane sente veramente che qualcosa manca, dovrebbe sentirsi costretto a parlare e lasciare che la loro cautela sia ascoltata. Lasciate che l&#39;architetto e i project manager confermino o attenuino la loro paura. È importante disporre di un team forte che si occupi del progetto e che mantenga la propria esperienza in materia di implementazioni impeccabili.

## Verifica l&#39;accesso alla gestione dei nomi di dominio, DMS, SSL, WAF

Poiché i nomi di dominio scadono, i record DNS possono essere modificati accidentalmente, i certificati SSL possono scadere e molto altro ancora; verificare di disporre della capacità di accedere e verificare che la connettività avvenga spesso. Facendo questo semplice controllo ogni trimestre ti mantiene sicuro che sai esattamente dove si trovano le cose, soprattutto in caso di emergenza. Non presumere che il DNS sia gestito nel Registro di sistema solo per scoprire che è gestito in Amazon. Questi record non vengono utilizzati frequentemente, quindi dimenticare dove si trovano è una probabilità elevata. Non considerare attendibile solo la documentazione scritta relativa ai nomi utente e alle password. Accedi a ciascuno di essi e verifica che le configurazioni che stai cercando siano effettivamente gestite lì. Troppo spesso le cose cambiano durante il fatturato di gestione o l&#39;acquisizione di un&#39;azienda e solo una persona sa cosa è successo, perché sono loro che hanno fatto l&#39;aggiornamento. Non erano a conoscenza del fatto che si faceva affidamento su un documento di testo condiviso che cos&#39;è la posizione, il nome utente e la password. Trova un processo di verifica che abbia senso per te e per la tua organizzazione, ma farlo ogni tre o sei mesi è un buon punto di partenza.

{{$include /help/_includes/hosting-related-links.md}}
