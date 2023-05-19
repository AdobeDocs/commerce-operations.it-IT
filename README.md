---
source-git-commit: 4b767014f325bef7e07cea11d01089206bf44caf
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---
# Documentazione tecnica di Adobe Commerce

Apprezziamo i contributi della nostra community e dei dipendenti Adobi esterni ai team di documentazione.

## Codice di condotta open source Adobe

Questo progetto ha adottato [Codice di condotta open source Adobe](code-of-conduct.md) o [Codice di condotta .NET Foundation](https://dotnetfoundation.org/code-of-conduct). Per ulteriori informazioni, vedere [Contribuire](contributing.md) articolo.

## Informazioni sui contributi ai contenuti Adobe

Consulta la [Guida per i collaboratori Adobe Docs](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html).

Il modo in cui contribuisci dipende da chi sei e dal tipo di modifiche con cui desideri contribuire:

### Modifiche minori

Se contribuisci con piccoli aggiornamenti per bontà d’animo, visita l’articolo e fai clic su **Modifica** nell’articolo, che passa alla sorgente dell’articolo su GitHub. Quindi, utilizza l’interfaccia utente di GitHub per apportare gli aggiornamenti. Consulta la sezione Generale [Guida per i collaboratori per la documentazione di Adobe](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) per ulteriori informazioni.

Le correzioni minori o i chiarimenti inviati per la documentazione e gli esempi di codice in questo archivio sono coperti dalle condizioni d’uso di Adobe.

### Modifiche sostanziali o nuovi articoli da parte dei membri della community

Se fai parte della community di Adobi e desideri creare un nuovo articolo o inviare modifiche importanti, utilizza la scheda Issues (Problemi) nell’archivio Git per inviare una segnalazione e avviare una conversazione con il team addetto alla documentazione. Dopo aver concordato un piano, dovrai collaborare con un dipendente per coordinare la pubblicazione dei nuovi contenuti attraverso una combinazione di interventi negli archivi pubblici e privati.

<!--
If you submit a pull request with significant changes to documentation and code examples, you'll see a message in the pull request asking you to submit an online contribution license agreement (CLA). We need you to complete the online form before we can review your pull request.
-->

### Modifiche sostanziali da parte dei dipendenti Adobe

Se sei un autore tecnico, un responsabile di programma o uno sviluppatore del team addetto ai prodotti di una soluzione Adobe Experience Cloud ed è tuo compito creare o contribuire ad articoli tecnici, devi utilizzare l’archivio privato all’indirizzo `https://git.corp.adobe.com/AdobeDocs`.

<!--Employees from other parts of the Adobe world should use the public repo for minor updates.-->

## Strumenti e configurazione

I collaboratori della community possono utilizzare l’interfaccia utente di GitHub per apportare modifiche di base o eseguire il fork dell’archivio per apportare contributi principali.

Consulta la [Guida per i collaboratori Adobe Docs](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) per i dettagli.

## Come utilizzare markdown per formattare l’argomento

Tutti gli articoli in questo archivio utilizzano il markdown GitHub. Se non conosci Markdown, consulta:

* [Nozioni di base su Markdown](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)
* [Foglio di riferimento per markdown stampabile](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)

## Modelli

Il `_jekyll` La directory contiene argomenti basati su modelli e risorse richieste.
I modelli che utilizzano il linguaggio di modellazione Liquid risiedono nel `_jekyll/templated` come file HTML.
Il `_jekyll/_data` La directory contiene file con i dati utilizzati per il rendering dei modelli.

Per eseguire il rendering di tutti i modelli:

1. Accedi a `_jekyll` directory.

   cd_jekyll

1. Esegui lo script di rendering.

```
_scripts/render
```

> **NOTA:** È necessario eseguire lo script da `_jekyll` directory.
> **NOTA:** Per eseguire lo script è necessario che Ruby sia installato.

Lo script esegue il rendering e scrive i modelli sottoposti a rendering in `help/_includes/templated` directory.

Per ulteriori informazioni su, consulta la documentazione di Jekyll. [File di dati](https://jekyllrb.com/docs/datafiles [Filtri per liquidi](https://jekyllrb.com/docs/liquid/filters/), e altre funzioni.
