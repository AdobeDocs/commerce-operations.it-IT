---
source-git-commit: d17847a7151c5e88f763b334e1ee659ca3ca6bcf
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 5%

---
# Documentazione utente di Adobe Commerce

Accogliamo con favore i contributi della nostra community e di dipendenti di Adobi provenienti da team esterni alla documentazione.

## Codice di condotta open source di Adobe

Questo progetto ha adottato il [Codice di condotta di Adobe Open Source](code-of-conduct.md) o il [Codice di condotta di .NET Foundation](https://dotnetfoundation.org/code-of-conduct). Per ulteriori informazioni, consulta l’articolo [Contribuzione](contributing.md).

## Informazioni sui contributi al contenuto di Adobe

Consulta la sezione [Guida per i collaboratori per la documentazione di Adobe](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html).

Il tuo contributo dipende da chi sei e dal tipo di modifiche che desideri apportare:

### Modifiche minori

Se stai contribuendo piccoli aggiornamenti per la bontà del tuo cuore, visita l&#39;articolo e fai clic sul **Modifica** nell’articolo che accede all’origine GitHub per l’articolo. Quindi, utilizza l’interfaccia utente GitHub per apportare i tuoi aggiornamenti. Vedi il generale [Guida per i collaboratori per la documentazione di Adobe](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) per ulteriori informazioni.

Le correzioni minori o i chiarimenti inviati per la documentazione e gli esempi di codice in questo repository sono coperti dai termini di utilizzo Adobi.

### Modifiche sostanziali o nuovi articoli dei membri della community

Se fai parte della community Adobe e desideri creare un nuovo articolo o inviare modifiche importanti, utilizza la scheda Issues (Problemi) nell’archivio Git per inviare un problema e avviare una conversazione con il team di documentazione. Una volta concordato un piano, dovrai collaborare con un dipendente per inserire il nuovo contenuto attraverso una combinazione di lavoro negli archivi pubblici e privati.

<!--
If you submit a pull request with significant changes to documentation and code examples, you'll see a message in the pull request asking you to submit an online contribution license agreement (CLA). We need you to complete the online form before we can review your pull request.
-->

### Modifiche di rilievo apportate dai dipendenti Adobi

Se sei un autore tecnico, un responsabile di programma o uno sviluppatore del team di prodotto per una soluzione Adobe Experience Cloud ed è tuo compito creare o contribuire ad articoli tecnici, devi utilizzare l’archivio privato all’indirizzo `https://git.corp.adobe.com/AdobeDocs`.

<!--Employees from other parts of the Adobe world should use the public repo for minor updates.-->

## Strumenti e configurazione

I collaboratori della community possono utilizzare l’interfaccia utente GitHub per effettuare modifiche di base o creare un fork dell’archivio per apportare contributi importanti.

Consulta la sezione [Guida per i collaboratori per la documentazione di Adobe](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) per i dettagli.

## Come utilizzare markdown per formattare l’argomento

Tutti gli articoli in questo archivio utilizzano markdown GitHub. Se non conosci markdown, consulta:

* [Nozioni di base su Markdown](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)
* [Foglio di riferimento per markdown stampabile](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)

## Etichette

Nell’archivio pubblico, alle richieste di pull vengono assegnate etichette automatizzate per aiutarci a gestire il flusso di lavoro delle richieste di pull e per consentirti di sapere cosa sta succedendo:

* **Modifica inviata all&#39;autore**: L&#39;autore è stato informato della richiesta di pull in sospeso.
* **Ready-to-merge**: Pronto per la revisione da parte del team di revisione della richiesta di pull.

## Modelli

La `_jekyll` contiene argomenti templati e risorse richieste.
I modelli che utilizzano il linguaggio di template Liquid risiedono nel `_jekyll/templated` come file HTML.
La `_jekyll/_data` contiene file con i dati utilizzati per eseguire il rendering dei modelli.

Per eseguire il rendering di tutti i modelli:

1. Passa a `_jekyll` directory.

   cd_jekyll

1. Esegui lo script di rendering.

```
_scripts/render
```

> **NOTA:** È necessario eseguire lo script dal `_jekyll` directory.
> **NOTA:** Per eseguire questo script è necessario che Ruby sia installato.

Lo script esegue il rendering e scrive i modelli di cui è stato eseguito il rendering nel `help/_includes/templated` directory.

Vedi la documentazione di Jekyll per maggiori dettagli su [File di dati](https://jekyllrb.com/docs/datafiles) [Filtri liquidi](https://jekyllrb.com/docs/liquid/filters/)e altre funzionalità.
