---
source-git-commit: aaf174e5d895ebc60d4937b0214e23a559532942
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---
# Best practice: Flusso di lavoro per la creazione di contenuti

Lo scopo di questo documento è quello di fornire dettagli al flusso di lavoro che gli utenti devono seguire per richiedere il contenuto Best practice.

## Chi può creare una richiesta?

Esistono due gruppi di soggetti interessati che possono presentare una richiesta, tra cui, a titolo esemplificativo:

- Esterno: Partner
- Interno: CTAG (Customer Technical Advisory Group), Assistenza clienti, successo cliente, team tecnici

## Come si crea una richiesta?

Le parti interessate interne devono presentare richieste aprendo un problema Jira nel progetto COMDOX. Le parti interessate esterne devono effettuare richieste aprendo un problema GitHub in questo archivio. Le parti interessate possono presentare le seguenti richieste:

- Richiedi l’aggiunta di nuovi contenuti
- Richiedi modifiche per il contenuto già pubblicato
- Condividere il proprio contenuto da pubblicare

## Qual è il processo complessivo?

Le parti interessate interne devono aprire un ticket Jira nel progetto Commerce Documentation (COMDOX) e fornire dettagli completi, incluso il completamento di un modello. Questi dettagli aiutano il team a dare priorità alle richieste di contenuto.

Il team monitora regolarmente le richieste nel backlog per determinare la priorità e se il Playbook di implementazione è il posto migliore per la richiesta. Il team può stabilire che invece di creare un nuovo argomento, il contenuto richiesto deve essere aggiunto alla documentazione di prodotto esistente, ad Experience League sul sito Adobe Developer.

Se in una richiesta non sono fornite informazioni sufficienti, il team chiederà al richiedente di completare tutti i campi corrispondenti. Se il richiedente non risponde entro X giorni, il team chiude la richiesta.
Dopo che il team convalida e dà priorità alla richiesta, il passaggio successivo consiste nel creare l’argomento. Ciò può significare l’adattamento dei contenuti al formato .md o la creazione dell’articolo da zero.

Il contenuto viene rivisto e modificato durante la creazione dell’argomento. Il processo di revisione avviene tramite richieste pull GitHub. Tutti i contenuti devono essere sottoposti a revisione editoriale. La revisione tecnica è facoltativa e dipende dal contenuto. Se non è necessaria alcuna revisione tecnica, il processo continua solo con una revisione editoriale. Questo processo può richiedere diverse iterazioni fino all’approvazione del contenuto.

Dopo l’approvazione di un articolo, il passaggio successivo consiste nell’unirlo al ramo di produzione. L&#39;unione deve essere eseguita dall&#39;autore. L’argomento può essere pubblicato immediatamente o attendere l’esecuzione del successivo processo di pubblicazione, che pubblica tutti gli argomenti approvati e uniti.

Verrà visualizzata una nuova sezione sull’Experience League Home page Best practice per aiutare gli utenti a rimanere aggiornati sugli argomenti pubblicati di recente, pertanto non dovranno navigare tra pagine e portali diversi per trovare informazioni rilevanti di interesse. Promuoveremo anche i contenuti nei canali esistenti, come il marketing e le comunicazioni interne.

## Scheda backlog e Kanban

Per evitare duplicazioni, le richieste create e prioritarie devono essere visibili nel backlog. Gli utenti sono incoraggiati ad impegnarsi con il sistema di voto a Jira per ribaltare le richieste che ritengono necessarie o pertinenti. Questo sarà anche un buon indicatore per il team di quale tipo di contenuto ci si aspetta dai soggetti interessati. Le richieste in attesa di definizione delle priorità e revisione verranno visualizzate nel backlog fino a quando non vengono spostate nelle corsie attive nella bacheca Kanban.

Gli utenti interni possono accedere alla bacheca Kanban per visualizzare (e/o monitorare) il contenuto in fase di elaborazione e i progressi compiuti. Su questa bacheca verranno visualizzate solo le richieste attive.
