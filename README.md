---
source-git-commit: 7dd6322370b976d8edea51fd94099e6dc4c082b7
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 3%

---
# Documentazione tecnica di Adobe Commerce

Apprezziamo i contributi della nostra community e dei dipendenti Adobi esterni ai team di documentazione.

## Codice di condotta open source Adobe

Questo progetto ha adottato il [Codice di condotta di Adobe Open Source](code-of-conduct.md) o il [Codice di condotta di .NET Foundation](https://dotnetfoundation.org/code-of-conduct). Per ulteriori informazioni, consulta l’articolo [Contribuzione](contributing.md).

## Informazioni sui contributi ai contenuti Adobe

Consulta la [Guida per i collaboratori Adobe Docs](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html).

Il modo in cui contribuisci dipende da chi sei e dal tipo di modifiche con cui desideri contribuire:

### Modifiche minori

Se stai contribuendo con aggiornamenti minori, visita l’articolo e fai clic sull’area di feedback visualizzata in fondo all’articolo, fai clic su **Opzioni di feedback dettagliate** e quindi fare clic su **Suggerisci una modifica** per passare al file Markdown di origine su GitHub. Utilizza l’interfaccia utente di GitHub per apportare modifiche. Consulta la sezione Generale [Guida per i collaboratori per la documentazione di Adobe](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) per ulteriori informazioni.

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

Per alcuni argomenti, usiamo file di dati e modelli per generare contenuti pubblicati. I casi di utilizzo per questo approccio includono:

* Pubblicazione di grandi set di contenuti generati a livello di programmazione
* Fornire un&#39;unica fonte di verità per i clienti su più sistemi che richiedono formati di file leggibili automaticamente, come YAML, per l&#39;integrazione (ad esempio, Site-Wide Analysis Tool)

Di seguito sono riportati alcuni esempi di contenuti basati su modelli:

* [Riferimento strumenti CLI](https://experienceleague.adobe.com/docs/commerce-operations/reference/commerce-on-premises.html)
* [Tabelle di disponibilità dei prodotti](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html)
* [Tabelle dei requisiti di sistema](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html)

### Generare contenuti basati su modelli

In generale, la maggior parte degli autori deve solo aggiungere una versione alle tabelle dei requisiti di sistema e di disponibilità del prodotto. La manutenzione per tutti gli altri contenuti basati su modelli è automatizzata o gestita da un membro del team dedicato. Queste istruzioni sono destinate alla &quot;maggior parte&quot; degli scrittori.

>**NOTA:**
>
>* La generazione di contenuti basati su modelli richiede l’utilizzo della riga di comando in un terminale.
>* Per eseguire lo script di rendering, è necessario che Ruby sia installato. Consulta [_jekyll/.ruby-version](_jekyll/.ruby-version) per la versione richiesta.

Per una descrizione della struttura di file per il contenuto con modelli, consulta:

* `_jekyll`- Contiene argomenti basati su modelli e risorse richieste
* `_jekyll/_data`- Contiene i formati di file leggibili al computer utilizzati per il rendering dei modelli
* `_jekyll/templated`- Contiene file modello basati su HTML che utilizzano il linguaggio di modellazione Liquid
* `help/_includes/templated`- Contiene l&#39;output generato per il contenuto con modelli in `.md` in modo che possa essere pubblicato negli argomenti di Experience League; lo script di rendering scrive automaticamente l&#39;output generato in questa directory

Per aggiornare il contenuto basato su modelli:

1. Nell’editor di testo, apri un file di dati nel `/jekyll/_data` directory. Ad esempio:

   * [Tabelle di disponibilità dei prodotti](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html): `/jekyll/_data/product-availability.yml`
   * [Tabelle dei requisiti di sistema](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html): `/jekyll/_data/system-requirements.yml`

1. Utilizzare la struttura YAML esistente per creare le voci.

   Ad esempio, per aggiungere una versione di Adobe Commerce alle tabelle di disponibilità del prodotto, aggiungi quanto segue a ciascuna voce della sezione `extensions` e `services` sezioni del `/jekyll/_data/product-availability.yml` file (modificare i numeri di versione secondo necessità):

   ```
   support:
      - core: 1.2.3
        version: 4.5.6
   ```

1. Accedi a `_jekyll` directory.

   ```
   cd _jekyll
   ```

1. Genera contenuti con modelli e scrivi l’output in `help/_includes/templated` directory.

   ```
   rake render
   ```

   >**NOTA:** È necessario eseguire lo script da `_jekyll` directory. Se questa è la prima volta che esegui lo script, devi installare le dipendenze di Ruby prima con `bundle install` comando.

1. Torna a `root` directory.

   ```
   cd ..
   ```

1. Verificare che il valore previsto `help/_includes/templated` i file sono stati modificati.

   ```
   git status
   ```

   Dovresti visualizzare un output simile al seguente:

   ```
   modified:   _data/product-availability.yml
   modified:   help/_includes/templated/product-availability-extensions.md
   ```

1. Invio delle modifiche.

   ```
   git add
   git commit -m "_descriptive message of the intended commit_"
   git push
   ```

Per ulteriori informazioni su, consulta la documentazione di Jekyll. [File di dati](https://jekyllrb.com/docs/datafiles), [Filtri per liquidi](https://jekyllrb.com/docs/liquid/filters/), e altre funzioni.
