---
title: '[!DNL Upgrade Compatibility Tool] report'
description: Per eseguire il comando [!DNL Upgrade Compatibility Tool] sul progetto Adobe Commerce.
exl-id: a2272339-46d6-443b-bd53-286b72f13d4e
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 0%

---

# Rapporti

{{commerce-only}}

In seguito all&#39;analisi, [!DNL Upgrade Compatibility Tool] può esportare un report contenente un elenco di problemi per ciascun file specificandone la gravità, il codice di errore e la descrizione dell’errore. Il [!DNL Upgrade Compatibility Tool] esporta il rapporto in due formati diversi:

- A [File JSON](reports.md#json-file).
- Un [Rapporto HTML](reports.md#html-report).

Vedi il seguente esempio di interfaccia della riga di comando di un rapporto:

```terminal
File: /app/code/Custom/CatalogExtension/Controller/Index/Index.php
------------------------------------------------------------------
 * [WARNING][1131] Line 10: Extending from class 'Magento\Framework\App\Action\Action' that is @deprecated on version '2.4.4'
 * [ERROR][1328] Line 10: Implemented interface 'Magento\Framework\App\Action\HttpGetActionInterface' that is non API on version '2.4.4'
```

Controlla la [Riferimento messaggio di errore](../upgrade-compatibility-tool/error-messages.md) per ulteriori informazioni sui diversi errori che questo report può generare.

Questo rapporto include anche un riepilogo dettagliato che mostra:

- *Versione corrente*: versione attualmente installata.
- *Versione di destinazione*: la versione a cui desideri effettuare l’aggiornamento.
- *Tempo di esecuzione*: tempo impiegato dall’analisi per generare il rapporto (mm:ss).
- *Moduli che richiedono aggiornamento*: la percentuale di moduli che contengono problemi di compatibilità e richiedono un aggiornamento.
- *File che richiedono aggiornamento*: percentuale di file che contengono problemi di compatibilità e richiedono l’aggiornamento.
- *Totale errori critici*: numero di errori critici rilevati.
- *Totale errori*: numero di errori trovati.
- *Totale avvisi*: numero di avvisi trovati.
- *Utilizzo massimo della memoria*: la quantità massima di memoria [!DNL Upgrade Compatibility Tool] raggiunto durante l&#39;esecuzione.

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

È possibile ottenere l’output del file JSON durante l’esecuzione del comando [!DNL Upgrade Compatibility Tool] su un&#39;interfaccia della riga di comando. Il `JSON` il file contiene esattamente le stesse informazioni visualizzate nel [!DNL Upgrade Compatibility Tool] output:

- Elenco dei problemi identificati.
- Riepilogo dell’analisi.

Per ogni problema riscontrato, il rapporto fornisce informazioni dettagliate come la gravità e la descrizione del problema.

Per esportare questo `JSON` in una cartella di output diversa:

```bash
bin/uct upgrade:check <dir> --json-output-path[=JSON-OUTPUT-PATH]
```

Dove gli argomenti sono i seguenti:

- `<dir>`: directory di installazione di Adobe Commerce.
- `[=JSON-OUTPUT-PATH]`: directory del percorso per esportare `JSON` file di output.

>[!NOTE]
>
> Il percorso predefinito per la cartella di output è `var/output/[TIME]-results.json`.

## Rapporto HTML

È possibile ottenere il report HTML durante l&#39;esecuzione dello strumento tramite un&#39;interfaccia della riga di comando o tramite [!DNL Site-Wide Analysis Tool]. La relazione HTML contiene inoltre:

- Elenco dei problemi identificati.
- Riepilogo dell’analisi.

![Rapporto HTML - Riepilogo](../../assets/upgrade-guide/uct-html-summary.png)

Puoi navigare facilmente tra i problemi identificati durante il [!DNL Upgrade Compatibility Tool] analisi.

Puoi filtrare i problemi visualizzati nel rapporto in base al livello di problema minimo (il valore predefinito è `WARNING`).

Nell’angolo in alto a destra è presente un elenco a discesa che consente di selezionare un livello diverso. L’elenco dei problemi identificati viene filtrato di conseguenza.

![Rapporto HTML - Utilizzo elenco a discesa](../../assets/upgrade-guide/uct-html-filtered-issues-list.png)

>[!NOTE]
>
> I problemi con il livello di problema inferiore vengono eliminati, ma si riceve una notifica in modo da essere sempre a conoscenza dei problemi identificati per modulo.

Il rapporto HTML include anche quattro grafici diversi:

- **Moduli per gravità del problema**: mostra la distribuzione della gravità per moduli.
- **File in base alla gravità del problema**: mostra la distribuzione della gravità per file.
- **Moduli ordinati per numero totale di problemi**: mostra i 10 moduli più compromessi tenendo conto di avvisi, errori ed errori critici.
- **Moduli con dimensioni e problemi relativi**: più file contiene un modulo, più grande è il suo cerchio. Più problemi ha un modulo, più il suo cerchio appare rosso.

Questi grafici consentono di identificare i moduli più compromessi e quelli che richiedono più lavoro per eseguire un aggiornamento.

![Rapporto HTML - Diagrammi](../../assets/upgrade-guide/uct-html-diagrams.png)

Anche i diagrammi del rapporto di HTML vengono aggiornati di conseguenza, con l’unica eccezione del `Modules with relative sizes and issues`, generato con `min-issue-level` questo è stato originariamente configurato.

Se desideri visualizzare risultati diversi per `Modules with relative sizes and issues` è necessario eseguire nuovamente il comando fornendo un altro valore per il `--min-issue-level` opzione.

![Rapporto HTML - Diagramma grafico a bolle](../../assets/upgrade-guide/uct-html-filtered-diagrams.png)

Per esportare il report HTML in una cartella di output diversa:

```bash
bin/uct upgrade:check <dir> --html-output-path[=HTML-OUTPUT-PATH]
```

Dove gli argomenti sono i seguenti:

- `<dir>`: directory di installazione di Adobe Commerce.
- `[=HTML-OUTPUT-PATH]`: directory del percorso per esportare `.html` file di output.

>[!NOTE]
>
> Il percorso predefinito per la cartella di output è `var/output/[TIME]-results.html`.
