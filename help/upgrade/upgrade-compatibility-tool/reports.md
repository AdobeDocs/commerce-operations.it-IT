---
title: '"[!DNL Upgrade Compatibility Tool] reports"'
description: Segui questi passaggi per eseguire il [!DNL Upgrade Compatibility Tool] sul progetto Adobe Commerce.
source-git-commit: 1ce02c3215b01f64e86383938a257514f0e4257c
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---


# Rapporti

{{commerce-only}}

A seguito dell&#39;analisi, il [!DNL Upgrade Compatibility Tool] può esportare un rapporto che contiene un elenco di problemi per ogni file, specificandone la gravità, il codice di errore e la descrizione dell’errore. La [!DNL Upgrade Compatibility Tool] esporta il rapporto in due formati diversi:

- A [File JSON](reports.md#json-file).
- Un [Rapporto HTML](reports.md#html-report).

Vedi il seguente esempio di interfaccia a riga di comando di un report:

```terminal
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 10: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.4'
 * [ERROR][1328] Line 10: Implemented interface 'Magento\Framework\App\Action\HttpGetActionInterface' that is non API on version '2.4.4'
```

Controlla la [Riferimento al messaggio di errore](../upgrade-compatibility-tool/error-messages.md) argomento per ulteriori informazioni sui diversi errori generati dal rapporto.

Questo rapporto include anche un riepilogo dettagliato che mostra:

- *Versione corrente*: versione attualmente installata.
- *Versione di destinazione*: la versione a cui desideri eseguire l’aggiornamento.
- *Tempo di esecuzione*: il tempo impiegato dall&#39;analisi per costruire il rapporto (mm:ss).
- *Moduli che richiedono aggiornamento*: la percentuale di moduli che contengono problemi di compatibilità e richiedono l’aggiornamento.
- *File che richiedono l’aggiornamento*: la percentuale di file che contengono problemi di compatibilità e richiedono l’aggiornamento.
- *Errori critici totali*: numero di errori critici rilevati.
- *Errori totali*: numero di errori rilevati.
- *Avvisi totali*: numero di avvisi rilevati.
- *Utilizzo di picco della memoria*: la quantità massima di memoria [!DNL Upgrade Compatibility Tool] ha raggiunto durante l&#39;esecuzione.

Vedi il seguente esempio di interfaccia della riga di comando:

```terminal
 ----------------------------- ----------------- 
  Current version               2.4.1            
  Target version                2.4.4            
  Execution time                1m:8s            
  Modules that require update   71.67% (43/60)   
  Files that require update     18.05% (96/532)  
  Total critical issues         24               
  Total errors                  159              
  Total warnings                53               
  Memory peak usage             902.00 MB        
 ----------------------------- ----------------- 
```

## File JSON

Puoi ottenere l’output del file JSON durante l’esecuzione del [!DNL Upgrade Compatibility Tool] su un&#39;interfaccia a riga di comando. La `JSON` il file contiene esattamente le stesse informazioni visualizzate nel [!DNL Upgrade Compatibility Tool] output:

- Elenco dei problemi identificati.
- Sintesi dell&#39;analisi.

Per ogni problema riscontrato, il rapporto fornisce informazioni dettagliate, ad esempio la gravità e la descrizione del problema.

Per esportare questo `JSON` in una cartella di output diversa:

```bash
bin/uct upgrade:check <dir> --json-output-path[=JSON-OUTPUT-PATH]
```

Se gli argomenti sono i seguenti:

- `<dir>`: Directory di installazione di Adobe Commerce.
- `[=JSON-OUTPUT-PATH]`: Directory del percorso per esportare `JSON` file di output.

>[!NOTE]
>
> Il percorso predefinito per la cartella di output è `var/output/[TIME]-results.json`.

## Rapporto HTML

È possibile ottenere il rapporto di HTML durante l&#39;esecuzione dello strumento su un&#39;interfaccia a riga di comando o tramite [!DNL Site-Wide Analysis Tool]. Il rapporto HTML contiene anche:

- Elenco dei problemi identificati.
- Sintesi dell&#39;analisi.

![Rapporto HTML - Riepilogo](../../assets/upgrade-guide/uct-html-summary.png)

Puoi navigare facilmente tra i problemi identificati durante il [!DNL Upgrade Compatibility Tool] analisi.

Puoi filtrare i problemi visualizzati nel rapporto in base al livello di problema minimo (il valore predefinito è `WARNING`).

Nell’angolo in alto a destra è disponibile un menu a discesa che consente di selezionare un livello diverso. L&#39;elenco dei problemi identificati viene filtrato di conseguenza.

![Rapporto HTML - Utilizzo a discesa](../../assets/upgrade-guide/uct-html-filtered-issues-list.png)

>[!NOTE]
>
> I problemi a livello di problema inferiore vengono eliminati ma ottieni una notifica in modo da essere sempre a conoscenza dei problemi identificati per modulo.

Il rapporto HTML include anche quattro diversi grafici:

- **Moduli per gravità del problema**: Mostra la distribuzione della gravità per moduli.
- **File per gravità del problema**: Mostra la distribuzione della gravità per file.
- **Moduli ordinati per numero totale di problemi**: Mostra i 10 moduli più compromessi tenendo conto di avvisi, errori ed errori critici.
- **Moduli con dimensioni e problemi relativi**: Più file contiene un modulo, più grande è il suo cerchio. Più problemi ha un modulo, più rosso appare il suo cerchio.

Questi grafici ti consentono di identificare i moduli più compromessi e quelli che richiedono più lavoro per eseguire un aggiornamento.

![Rapporto HTML - Diagrammi](../../assets/upgrade-guide/uct-html-diagrams.png)

Anche i diagrammi dei report di HTML vengono aggiornati di conseguenza, con l&#39;unica eccezione del `Modules with relative sizes and issues`, generato con il `min-issue-level` è stato creato originariamente.

Se desideri visualizzare risultati diversi per il `Modules with relative sizes and issues` è necessario eseguire nuovamente il comando specificando un altro valore per il `--min-issue-level` opzione .

![Rapporto HTML - Diagramma a bolle](../../assets/upgrade-guide/uct-html-filtered-diagrams.png)

Per esportare il rapporto HTML in una cartella di output diversa:

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

Se gli argomenti sono i seguenti:

- `<dir>`: {{site.data.var.ee}} directory di installazione.
- `[=HTML-OUTPUT-PATH]`: Directory del percorso per esportare `.html` file di output.

>[!NOTE]
>
> Il percorso predefinito per la cartella di output è `var/output/[TIME]-results.html`.
