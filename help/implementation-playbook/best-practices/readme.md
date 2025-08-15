---
source-git-commit: 8013e6339d42108dbefbbafa5db7f9ffc5288c4f
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 0%

---
# Best practice: flusso di lavoro per la creazione di contenuti

Questo documento descrive il flusso di lavoro dell&#39;utente per richiedere modifiche o aggiunte al contenuto delle *[best practice] (https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html* nella *playbook di implementazione di Adobe Commerce*.

## Chi può creare una richiesta?

Adobe accetta le richieste delle parti interessate interne ed esterne, inclusi, a titolo esemplificativo e non esaustivo, i seguenti gruppi:

- Partner Adobe
- Adobe CTAG (Customer Technical Advisory Group), Assistenza clienti, Customer Success, team tecnici

## Come si crea una richiesta?

**Le parti interessate interne** possono inviare richieste aprendo un problema Jira nel progetto COMDOX. **Le parti interessate esterne** possono inviare richieste aprendo [un problema GitHub](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) in questo archivio.

Puoi inviare i seguenti tipi di richieste:

- Idee per nuovi contenuti
- Aggiornamenti a contenuti già pubblicati
- Pubblicare nuovi contenuti forniti dalle parti interessate o dalla community

## Qual è il processo complessivo?


**Crea un ticket Jira o un problema**. Le parti interessate interne creano un ticket Jira nel progetto COMDOX. Le parti interessate esterne presentano un problema GitHub. Includi i dettagli completi nel problema Jira o [GitHub](https://github.com/AdobeDocs/commerce-operations.en/issues/new/choose) per aiutare il team a comprendere il contesto e assegnare la priorità alla richiesta.

**Il team del progetto Adobe valuta e assegna la priorità alla richiesta**. Il team controlla regolarmente le richieste per determinarne la priorità e valutare le modifiche richieste per l&#39;inclusione nelle best practice per l&#39;implementazione del playbook. Ad esempio, il team potrebbe determinare che, invece di creare un nuovo argomento Best Practices, il contenuto richiesto debba essere aggiunto alla documentazione del prodotto esistente su Experience League o sul sito Adobe Developer.

Se una richiesta non contiene informazioni sufficienti, il team richiede ulteriori informazioni al richiedente. Se il richiedente non risponde entro 14 giorni, il team chiude la richiesta.

**Creazione o aggiornamento del contenuto**-Il lavoro di creazione del contenuto è stato completato seguendo il processo documentato nella [Guida per i collaboratori di Adobe Experience League](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html). A seconda della richiesta, il lavoro può includere la conversione di nuovi contenuti in markdown, la creazione di un argomento o l’aggiornamento di un argomento esistente.

**Revisione, approvazione e pubblicazione del contenuto**-Il contenuto viene rivisto e modificato durante la creazione o l&#39;aggiornamento dell&#39;argomento tramite [richieste pull GitHub](https://experienceleague.adobe.com/docs/contributor/contributor-guide/setup/git-fundamentals.html?lang=en#pull-requests). Tutti i contenuti devono essere sottoposti a revisione editoriale. La revisione tecnica è facoltativa e dipende dal contenuto. Se non è necessaria alcuna revisione tecnica, il processo continua solo con una revisione editoriale. Questo processo può richiedere diverse iterazioni fino all’approvazione del contenuto.

Dopo l’approvazione di un articolo, la richiesta di pull può essere unita al ramo di produzione. L’unione deve essere eseguita dall’autore. Dopo l&#39;unione di un argomento, è possibile pubblicarlo immediatamente in produzione utilizzando un processo manuale o automaticamente alla successiva esecuzione del processo di pubblicazione. I processi di pubblicazione vengono in genere eseguiti ogni due ore.

**Notifica per nuovo contenuto**-Adobe fornirà una sezione *Novità* nell&#39;argomento [Panoramica sulle best practice](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/phases.html?lang=en) per informare gli utenti sugli argomenti pubblicati o aggiornati di recente. Adobe promuoverà inoltre nuovi contenuti relativi alle best practice utilizzando i canali esistenti, ad esempio il marketing e le comunicazioni interne.

## Backlog e Kanban Board

Per evitare duplicazioni, le richieste create e con priorità saranno visibili nel backlog Jira del progetto COMDOX e nel [progetto GitHub Issues](https://github.com/orgs/AdobeDocs/projects/6/views/1). Le parti interessate interne sono incoraggiate a impegnarsi con il sistema di voto di Jira per dare un voto favorevole alle richieste che ritengono necessarie o pertinenti. Votare aiuta anche il team del progetto Best Practices a comprendere il tipo di contenuto che le parti interessate si aspettano e che apportano valore. Le richieste in attesa di definizione delle priorità e di revisione vengono visualizzate nel backlog fino a quando non vengono spostate nelle corsie attive nella bacheca Kanban.

Gli utenti interni possono accedere alla bacheca Kanban per visualizzare (e/o monitorare) il contenuto su cui si sta lavorando e i progressi compiuti. Su questa bacheca verranno visualizzate solo le richieste attive.
