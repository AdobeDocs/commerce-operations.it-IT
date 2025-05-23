---
source-git-commit: a6086afc0a1f099b62014ad61098a5a1dc9d4675
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 3%

---
# Documentazione tecnica di Adobe Commerce

Apprezziamo i contributi della community e dei dipendenti Adobi esterni ai team di documentazione.

## Codice di condotta di Adobe Open Source

Questo progetto ha adottato il [Codice di condotta di Adobe Open Source](code-of-conduct.md) o il [Codice di condotta di .NET Foundation](https://dotnetfoundation.org/code-of-conduct). Per ulteriori informazioni, consulta l’articolo [Contribuzione](contributing.md).

## Informazioni sui contributi ai contenuti Adobe

Consulta la [Guida collaboratore per i documenti di Adobe](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html?lang=it).

Il modo in cui contribuisci dipende da chi sei e dal tipo di modifiche con cui desideri contribuire:

### Modifiche minori

Se stai apportando aggiornamenti minori, visita l&#39;articolo e fai clic sull&#39;area di feedback visualizzata in fondo all&#39;articolo, fai clic su **Opzioni di feedback dettagliate**, quindi fai clic su **Suggerisci una modifica** per passare al file Markdown di origine su GitHub. Utilizza l’interfaccia utente di GitHub per apportare modifiche. Per ulteriori informazioni, consulta la [Guida per i collaboratori per la documentazione di Adobe](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html?lang=it).

Le correzioni minori o i chiarimenti inviati per la documentazione e gli esempi di codice in questo archivio sono coperti dalle condizioni d’uso di Adobe.

### Modifiche sostanziali o nuovi articoli da parte dei membri della community

Se fai parte della community di Adobi e desideri creare un nuovo articolo o inviare modifiche importanti, utilizza la scheda Issues (Problemi) nell’archivio Git per inviare una segnalazione e avviare una conversazione con il team addetto alla documentazione. Dopo aver concordato un piano, dovrai collaborare con un dipendente per coordinare la pubblicazione dei nuovi contenuti attraverso una combinazione di interventi negli archivi pubblici e privati.

<!--
If you submit a pull request with significant changes to documentation and code examples, you'll see a message in the pull request asking you to submit an online contribution license agreement (CLA). We need you to complete the online form before we can review your pull request.
-->

### Modifiche sostanziali da parte dei dipendenti Adobe

Se sei un autore tecnico, un responsabile di programma o uno sviluppatore del team di prodotto per una soluzione Adobe Experience Cloud ed è tuo compito creare o contribuire ad articoli tecnici, devi utilizzare l&#39;archivio privato all&#39;indirizzo `https://git.corp.adobe.com/AdobeDocs`.

<!--Employees from other parts of the Adobe world should use the public repo for minor updates.-->

## Strumenti e configurazione

I collaboratori della community possono utilizzare l’interfaccia utente di GitHub per apportare modifiche di base o eseguire il fork dell’archivio per apportare contributi principali.

Per informazioni dettagliate, consulta la [Guida per i collaboratori per la documentazione di Adobe](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html?lang=it).

## Come utilizzare markdown per formattare l’argomento

Tutti gli articoli in questo archivio utilizzano il markdown GitHub. Se non conosci Markdown, consulta:

* [Nozioni di base su Markdown](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)
* [Foglio di riferimento per il markdown stampabile](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)

## Modelli

Per alcuni argomenti, usiamo file di dati e modelli per generare contenuti pubblicati. I casi di utilizzo per questo approccio includono:

* Pubblicazione di grandi set di contenuti generati a livello di programmazione
* Fornire un&#39;unica fonte di verità per i clienti su più sistemi che richiedono formati di file leggibili automaticamente, come YAML, per l&#39;integrazione (ad esempio, Site-Wide Analysis Tool)

Di seguito sono riportati alcuni esempi di contenuti basati su modelli:

* [Riferimento strumenti CLI](https://experienceleague.adobe.com/docs/commerce-operations/reference/commerce-on-premises.html)
* [Tabelle di disponibilità del prodotto](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html?lang=it)
* [Tabelle dei requisiti di sistema](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html?lang=it)

### Generare contenuti basati su modelli

In generale, la maggior parte degli autori deve solo aggiungere una versione alle tabelle dei requisiti di sistema e di disponibilità del prodotto. La manutenzione per tutti gli altri contenuti basati su modelli è automatizzata o gestita da un membro del team dedicato. Queste istruzioni sono destinate alla maggior parte degli autori.

>**NOTA:**
>
>* La generazione di contenuti basati su modelli richiede l’utilizzo della riga di comando in un terminale.
>* Per eseguire lo script di rendering, è necessario che Ruby sia installato. Vedere [_jekyll/.ruby-version] (_jekyll/.ruby-version) per la versione richiesta.

Per una descrizione della struttura di file per il contenuto con modelli, consulta:

* `_jekyll` - Contiene gli argomenti con modelli e le risorse richieste
* `_jekyll/_data` - Contiene i formati di file leggibili dal computer utilizzati per il rendering dei modelli
* `_jekyll/templated` - Contiene file di modelli basati su HTML che utilizzano il linguaggio di modelli Liquid
* `help/_includes/templated` - Contiene l&#39;output generato per il contenuto con modelli nel formato di file `.md` in modo che possa essere pubblicato negli argomenti di Experience League. Lo script di rendering scrive automaticamente l&#39;output generato in questa directory

Per aggiornare il contenuto basato su modelli:

1. Nell&#39;editor di testo aprire un file di dati nella directory `/jekyll/_data`. Ad esempio:

   * [Tabelle di disponibilità del prodotto](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html?lang=it): `/jekyll/_data/product-availability.yml`
   * [Tabelle dei requisiti di sistema](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html?lang=it): `/jekyll/_data/system-requirements.yml`

1. Utilizzare la struttura YAML esistente per creare le voci.

   Ad esempio, per aggiungere una versione di Adobe Commerce alle tabelle di disponibilità del prodotto, aggiungere quanto segue a ogni voce nelle sezioni `extensions` e `services` del file `/jekyll/_data/product-availability.yml` (modificare i numeri di versione in base alle esigenze):

   ```
   support:
      - core: 1.2.3
        version: 4.5.6
   ```

1. Passare alla directory `_jekyll`.

   ```
   cd _jekyll
   ```

1. Genera contenuti con modelli e scrive l&#39;output nella directory `help/_includes/templated`.

   ```
   rake render
   ```

   >**NOTA:** è necessario eseguire lo script dalla directory `_jekyll`. Se questa è la prima volta che esegui lo script, devi prima installare le dipendenze Ruby con il comando `bundle install`.

1. Tornare alla directory `root`.

   ```
   cd ..
   ```

1. Verificare che i `help/_includes/templated` file previsti siano stati modificati.

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
   git add .
   git commit -m "descriptive message of the intended commit"
   git push
   ```

Per ulteriori informazioni su [File di dati](https://jekyllrb.com/docs/datafiles), [Filtri liquidi](https://jekyllrb.com/docs/liquid/filters/) e altre funzionalità, vedere la documentazione di Jekyll.
