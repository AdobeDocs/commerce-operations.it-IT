---
title: Distribuzione di file di visualizzazione statici
description: Scopri come scrivere file statici nel file system Commerce durante la modalità di produzione.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '1135'
ht-degree: 0%

---


# Distribuzione di file di visualizzazione statici

{{file-system-owner}}

Il comando di distribuzione dei file di visualizzazione statica consente di scrivere [file statici](https://glossary.magento.com/static-files) al file system Commerce quando il software Commerce è impostato per [modalità di produzione](../bootstrap/application-modes.md#production-mode).

Il termine _file di visualizzazione statica_ fa riferimento a quanto segue:

- &quot;Statico&quot; significa che può essere memorizzato nella cache per un sito (ovvero, il file non viene generato in modo dinamico). Gli esempi includono immagini e CSS generati da LESS.
- &quot;View&quot; si riferisce al livello di presentazione (da MVC).

I file di visualizzazione statica si trovano in `<magento_root>/pub/static` e alcuni sono memorizzati nella cache `<magento_root>/var/view_preprocessed` anche nella directory.

La distribuzione dei file di visualizzazione statica viene influenzata dalle modalità di applicazione come segue:

- [Predefinito](../bootstrap/application-modes.md#default-mode) e [sviluppatore](../bootstrap/application-modes.md#developer-mode) modalità: Commerce li genera su richiesta, ma gli altri sono memorizzati nella cache in un file per velocizzare l&#39;accesso.
- [Produzione](../bootstrap/application-modes.md#production-mode) modalità: I file statici sono _not_ generato o memorizzato nella cache.

È necessario scrivere manualmente i file di visualizzazione statica nel file system Commerce utilizzando il comando descritto in questo argomento; in seguito, puoi limitare le autorizzazioni per limitare le vulnerabilità e per evitare la sovrascrittura accidentale o dannosa dei file.

>[!WARNING]
>
>_Solo in modalità Sviluppatore_: Quando installi o attivi un nuovo modulo, potrebbe caricare nuovi JavaScript, CSS, layout e così via. Per evitare problemi con i file statici, è necessario pulire i file precedenti per assicurarsi di ottenere tutte le modifiche per il nuovo modulo. È possibile pulire i file di visualizzazione statica generati in diversi modi. Fai riferimento a [Pulisci argomento della cache dei file statici per i dettagli](https://developer.adobe.com/commerce/frontend-core/guide/caching/#clean-static-files-cache) per ulteriori informazioni.

**Per distribuire file di visualizzazione statici**:

1. Accedi al server Commerce come oppure [passa al proprietario del file system](../../installation/prerequisites/file-system/overview.md).
1. Elimina il contenuto di `<magento_root>/pub/static`, ad eccezione del `.htaccess` file. Non eliminare questo file.
1. Esegui lo strumento di distribuzione dei file di visualizzazione statica `<magento_root>/bin/magento setup:static-content:deploy`.

   >[!INFO]
   >
   >Se abiliti l’unione dei file di visualizzazione statica nell’amministrazione, la `pub/static` il sistema di directory deve essere scrivibile.

   Opzioni di comando:

   ```bash
   bin/magento setup:static-content:deploy [<languages>] [-t|--theme[="<theme>"]] [--exclude-theme[="<theme>"]] [-l|--language[="<language>"]] [--exclude-language[="<language>"]] [-a|--area[="<area>"]] [--exclude-area[="<area>"]] [-j|--jobs[="<number>"]]  [--no-javascript] [--no-css] [--no-less] [--no-images] [--no-fonts] [--no-html] [--no-misc] [--no-html-minify] [--no-parent] [-f|--force]
   ```

Nella tabella seguente sono illustrati i parametri e i valori di questo comando.

| Opzione | Descrizione | Obbligatorio |
| ------ | ----------- | --------- |
| `<languages>` | Elenco separato da spazi di [ISO-639](http://www.loc.gov/standards/iso639-2/php/code_list.php) codici di lingua per i quali inviare file di visualizzazione statici. (Il valore predefinito è `en_US`.)<br>Trova l&#39;elenco eseguendo: `bin/magento info:language:list` | No |
| `--language (-l)` | Genera file solo per le lingue specificate. L&#39;impostazione predefinita, senza alcuna opzione specificata, consiste nel generare file per tutti i codici di lingua ISO-639. È possibile specificare il nome di un codice lingua alla volta. Il valore predefinito è **tutto**.<br>Ad esempio: `--language en_US --language es_ES` | No |
| `--exclude-language` | Genera file per i codici di lingua specificati. L’impostazione predefinita, senza alcuna opzione specificata, consiste nell’escludere nulla. È possibile specificare il nome di un codice della lingua o di un elenco di codici della lingua separati da virgole. Il valore predefinito è **nessuno**. | No |
| `--theme <theme>` | emes per cui distribuire contenuto statico. Il valore predefinito è **tutto**.<br>Ad esempio: `--theme Magento/blank --theme Magento/luma` | No |
| `--exclude-theme <theme>` | Temi da escludere durante la distribuzione di contenuto statico. Il valore predefinito è **nessuno**.<br>Ad esempio, `--exclude-theme Magento/blank` | No |
| `--area (-a)` | Genera file solo per le aree specificate. L&#39;impostazione predefinita, senza alcuna opzione specificata, consiste nel generare file per tutte le aree. I valori validi sono `adminhtml` e `frontend`. Il valore predefinito è **tutto**.<br>Ad esempio: `--area adminhtml` | No |
| `--exclude-area` | Non generare file per le aree specificate. L’impostazione predefinita, senza alcuna opzione specificata, consiste nell’escludere nulla. Il valore predefinito è **nessuno**. | No |
| `--jobs (-j)` | Abilita l&#39;elaborazione parallela utilizzando il numero specificato di processi. Il valore predefinito è 0 (non eseguire processi paralleli). Il valore predefinito è **0**. | No |
| `--symlink-locale` | Crea collegamenti simbolici per i file di tali impostazioni internazionali, che vengono passati per la distribuzione ma non dispongono di personalizzazioni. | No |
| `--content-version=CONTENT-VERSION` | La versione personalizzata del contenuto statico può essere utilizzata se si esegue la distribuzione su più nodi per garantire che la versione del contenuto statico sia identica e che il caching funzioni correttamente. | No |
| `--no-javascript` | Non distribuire file JavaScript | No |
| `--no-css` | Non distribuire file CSS. | No |
| `--no-less` | Non distribuire file LESS. | No |
| `--no-images` | Non distribuire immagini. | No |
| `--no-fonts` | Non distribuire i file di font. | No |
| `--no-html` | Non distribuire file HTML. | No |
| `--no-misc` | Non distribuire altri tipi di file: MD, JBF, CSV, JSON, TXT, HTC, SWF | No |
| `--no-html-minify` | Non minimizzare i file HTML. | No |
| `-s <quick\|standard\|compact>` | Definisci la strategia di distribuzione. Utilizzare queste opzioni solo se si dispone di più locali.<ul><li>Utilizza la [strategia rapida](static-view-file-strategy.md#quick-strategy) per ridurre al minimo i tempi di distribuzione. Questa è l&#39;opzione di comando predefinita, se non specificata.</li><li>Utilizza la [strategia standard](static-view-file-strategy.md#standard-strategy) per distribuire tutti i file di visualizzazione statica per tutti i pacchetti.</li><li>Utilizza la [strategia compatta](static-view-file-strategy.md#compact-strategy) per risparmiare spazio su disco sul server.</li></ul> | No |
| `--no-parent` | Non generare file per i temi principali del tema corrente. Si consiglia vivamente di utilizzare questo flag se non si utilizza esplicitamente il tema padre del tema corrente che si sta tentando di distribuire. Ciò aumenta notevolmente la velocità del processo. Questo flag è disponibile in Commerce 2.4.2 | No |
| `--force (-f)` | Distribuisci i file in qualsiasi modalità. Per impostazione predefinita, lo strumento di distribuzione del contenuto statico può essere eseguito solo in modalità di produzione. Utilizzare questa opzione per eseguirla in modalità predefinita o sviluppatore). | No |

>[!INFO]
>
>Se si specificano i valori per entrambi `<languages>` e `--language`, `<languages>` ha la precedenza.

## Esempi

Di seguito sono riportati alcuni comandi di esempio.

### Esclusione di un tema e della minimizzazione di HTML

Il seguente comando distribuisce contenuto statico per l’inglese americano (`en_US`), esclude il tema Luma fornito con Commerce e non minimizza i file HTML.

```bash
bin/magento setup:static-content:deploy en_US --exclude-theme Magento/luma --no-html-minify
```

Output campione:

```terminal
Requested languages: en_US
Requested areas: frontend, adminhtml
Requested themes: Magento/blank, Magento/backend
=== frontend -> Magento/blank -> en_US ===
=== adminhtml -> Magento/backend -> en_US ===
...........................................................
... more ...
Successful: 2055 files; errors: 0
---

New version of deployed files: 1466710645
............
Successful: 1993 files; errors: 0
---
```

Il seguente comando implementa solo JavaScript, con 4 processi, con una strategia di distribuzione standard:

```bash
bin/magento setup:static-content:deploy -s standard --no-misc --no-html --no-fonts --no-images --no-less --no-css -j 4
```

Il seguente comando implementa solo CSS e LESS con 3 processi e una strategia di distribuzione rapida:

```bash
bin/magento setup:static-content:deploy -s quick --no-misc --no-html --no-fonts --no-images --no-javascript -j 3
```

### Generazione di file di visualizzazione statici per un tema e un&#39;area

Il comando seguente genera file di visualizzazione statici per tutte le lingue, solo l’area frontale, solo il tema Commerce Luma, senza generare font:

```bash
bin/magento setup:static-content:deploy --area frontend --no-fonts --theme Magento/luma
```

Output campione:

```terminal
Requested languages: en_US
Requested areas: frontend
Requested themes: Magento/luma
=== frontend -> Magento/luma -> en_US ===
...........................................................
... more ...
........................................................................
Successful: 2092 files; errors: 0
---

New version of deployed files: 1466711110
```

## Distribuire file di visualizzazione statici senza installare Commerce

È possibile eseguire il processo di distribuzione in un ambiente separato, non di produzione, per evitare processi di generazione su computer di produzione sensibili.

A questo scopo, procedi come segue:

1. Esegui [`bin/magento app:config:dump`](../cli/export-configuration.md) per esportare la configurazione dal sistema di produzione.
1. Copia i file esportati nella base di codice non di produzione.
1. Distribuire file di visualizzazione statici: `bin/magento setup:static-content:deploy`

## Risoluzione dei problemi relativi allo strumento di distribuzione dei file di visualizzazione statica

[Installare prima il software Commerce](../../installation/overview.md); in caso contrario, non è possibile eseguire lo strumento di distribuzione dei file di visualizzazione statica.

**Sintomo**: Quando si esegue lo strumento di distribuzione dei file di visualizzazione statica, viene visualizzato il seguente errore:

```terminal
ERROR: You need to install the Commerce application before running this utility.
```

**Soluzione**:

Segui i passaggi seguenti:

1. Installare il software Commerce utilizzando [riga di comando](../../installation/composer.md).
1. Accedi al server dell&#39;applicazione come, o [passa a](../../installation/prerequisites/file-system/overview.md), il proprietario del file system.
1. Elimina il contenuto di `<app_root>/pub/static` ad eccezione della `.htaccess` file. Non eliminare questo file.
1. Distribuire file di visualizzazione statici: `bin/magento setup:static-content:deploy`

## Suggerimento per gli sviluppatori per personalizzare lo strumento di distribuzione dei contenuti statici

Quando crei un’implementazione personalizzata dello strumento di distribuzione del contenuto statico, utilizza solo la scrittura di file atomici per i file che dovrebbero essere disponibili sul client. Se si utilizza la scrittura di file non atomici, questi file potrebbero essere caricati sul client con contenuto parziale.

Una delle opzioni per renderlo atomico è scrivere in file memorizzati in una directory temporanea e copiarli o spostarli nella directory di destinazione (da dove sono caricati al client) dopo la scrittura è finita. Per informazioni dettagliate sulla scrittura in file, consulta [fwrite php](https://www.php.net/manual/en/function.fwrite.php).
