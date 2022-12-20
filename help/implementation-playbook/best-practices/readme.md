---
source-git-commit: 8013e6339d42108dbefbbafa5db7f9ffc5288c4f
workflow-type: tm+mt
source-wordcount: '639'
ht-degree: 0%

---
# Best practice: Flusso di lavoro per la creazione di contenuti

Questo documento descrive il flusso di lavoro dell&#39;utente per richiedere modifiche o aggiunte al *[Best practice](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html)* nel *Playbook di implementazione Adobe Commerce*.

## Chi può creare una richiesta?

Adobe accetta le richieste delle parti interessate interne ed esterne, compresi, tra l’altro, i soggetti appartenenti ai seguenti gruppi:

- Partner Adobe
- Adobe CTAG (Customer Technical Advisory Group), Assistenza clienti, successo cliente, team tecnici

## Come si crea una richiesta?

**Interessi interni** può inviare richieste aprendo un problema Jira nel progetto COMDOX. **Interessati esterni** può inviare le richieste aprendo una [Problema GitHub](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) in questo archivio.

Puoi inviare i seguenti tipi di richieste:

- Idee per nuovi contenuti
- Aggiornamenti al contenuto già pubblicato
- Pubblicare nuovi contenuti forniti dalle parti interessate o dalla comunità

## Qual è il processo complessivo?


**Crea un biglietto o un problema Jira**- Gli interessati interni creano un ticket Jira nel progetto COMDOX. Le parti interessate esterne inviano un problema GitHub. Includi dettagli completi nella Jira o [Problema GitHub](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) per aiutare il team a comprendere il contesto e dare priorità alla richiesta.

**Il team di progetto di Adobe valuta e dà priorità alla richiesta**- Il team monitora regolarmente le richieste per determinare la priorità e valutare le modifiche richieste per l&#39;inclusione nelle best practice relative all&#39;implementazione per le playlist. Ad esempio, il team potrebbe determinare che invece di creare un nuovo argomento sulle best practice, il contenuto richiesto deve essere aggiunto alla documentazione di prodotto esistente, ad Experience League sul sito Adobe Developer o.

Se in una richiesta non sono fornite informazioni sufficienti, il team richiede informazioni aggiuntive al richiedente. Se il richiedente non risponde entro 14 giorni, il team chiude la richiesta.

**Crea o aggiorna contenuto**- Il lavoro di creazione dei contenuti viene completato dopo il processo documentato in [Guida per i collaboratori di Adobe Experience League](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html). A seconda della richiesta, il lavoro può includere la conversione di nuovo contenuto in markdown, la creazione di un argomento o l’aggiornamento di un argomento esistente.

**Revisione dei contenuti, approvazione e pubblicazione**- Il contenuto viene rivisto e modificato durante la creazione o l&#39;aggiornamento degli argomenti utilizzando [Richieste GitHub pull](https://experienceleague.adobe.com/docs/contributor/contributor-guide/setup/git-fundamentals.html?lang=en#pull-requests). Tutti i contenuti devono essere sottoposti a revisione editoriale. La revisione tecnica è facoltativa e dipende dal contenuto. Se non è necessaria alcuna revisione tecnica, il processo continua solo con una revisione editoriale. Questo processo può richiedere diverse iterazioni fino all’approvazione del contenuto.

Dopo l’approvazione di un articolo, la richiesta di pull può essere unita al ramo di produzione. L&#39;unione deve essere eseguita dall&#39;autore. Dopo l’unione di un argomento, questo può essere pubblicato in produzione immediatamente utilizzando un processo manuale o automaticamente al successivo avvio del processo di pubblicazione. I lavori di pubblicazione vengono in genere eseguiti ogni due ore.

**Nuova notifica del contenuto**-L&#39;Adobe fornirà un *Novità* sezione [Panoramica sulle best practice](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html?lang=en) per informare gli utenti sugli argomenti pubblicati o aggiornati di recente. Adobe promuoverà inoltre nuovi contenuti sulle best practice utilizzando i canali esistenti, come il marketing e le comunicazioni interne.

## Scheda backlog e Kanban

Per evitare duplicazioni, le richieste create e prioritarie saranno visibili nel backlog Jira del progetto COMDOX e [Progetto GitHub Issues](https://github.com/orgs/AdobeDocs/projects/6/views/1). Le parti interessate interne sono incoraggiate ad impegnarsi con il sistema di voto a Jira per respingere le richieste che ritengono necessarie o pertinenti. Il voto aiuta anche il team del progetto Best Practices a comprendere il tipo di contenuti che le parti interessate si aspettano e apprezzano. Le richieste in sospeso per la definizione delle priorità e la revisione vengono visualizzate nel backlog fino a quando non vengono spostate nelle corsie attive nella bacheca Kanban.

Gli utenti interni possono accedere alla bacheca Kanban per visualizzare (e/o monitorare) il contenuto in fase di elaborazione e i progressi compiuti. Su questa bacheca verranno visualizzate solo le richieste attive.
