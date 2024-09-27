---
source-git-commit: ca9e04d50e69b8a51ec4a6fbcf1d35f0fb363fab
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---
# Panoramica

Questo progetto include diverse attività Rake per automatizzare vari aspetti del flusso di lavoro, ad esempio la generazione di dati per i digesti di notizie, il rendering di file con modelli, l’ottimizzazione delle immagini e la generazione di mappe. Di seguito sono riportate le descrizioni e le linee guida sull’utilizzo per ogni attività Rake definita nel file Rakefile.

## Esegui attività

### `render`

Esegue il rendering dei file modello nella directory `_jekyll/templates` con i dati di `_jekyll/_data/`. Il risultato si troverà nella directory `help/includes/templated`.

**Utilizzo:**

```sh
rake render
```

### `image_optim`

Ottimizza le immagini nei file non salvati modificati. Per altre immagini, utilizzare l&#39;argomento `path` per specificare la directory o il file.

**Utilizzo:**

```sh
rake image_optim
```

**Con `path` argomento:**

```sh
rake image_optim path=../path/to/dir/or/file
```

### `whatsnew`

Genera dati per un riepilogo di notizie. L’intervallo di tempo predefinito è dall’ultimo aggiornamento. È possibile specificare un periodo diverso utilizzando l&#39;argomento `since`.

**Utilizzo:**

```sh
rake whatsnew
```

**Con `since` argomento:**

```sh
rake whatsnew since="jul 4"
```

### `whatsnew_bp`

Genera dati per un riepilogo delle notizie in Best practice. L’intervallo di tempo predefinito è dall’ultimo aggiornamento. È possibile specificare un periodo diverso utilizzando l&#39;argomento `since`.

**Utilizzo:**

```sh
rake whatsnew_bp
```

**Con `since` argomento:**

```sh
rake whatsnew_bp since="jul 4"
```

### `azure_regions`

Genera una mappa delle aree di Azure. Il file di dati di input deve trovarsi in `_jekyll/tmp/azure-regions.json`. Il risultato verrà trovato in `_jekyll/tmp/azure-regions.svg`. È necessario installare Python, [PyGMT](https://www.pygmt.org/latest/install.html) e [pdf2svg](https://formulae.brew.sh/formula/pdf2svg).

**Utilizzo:**

```sh
rake azure_regions
```

## Prerequisiti

- Ruby e Bundler installati.
- Gemme obbligatorie specificate nel file Gem.
- Python, [PyGMT](https://www.pygmt.org/latest/install.html) e [pdf2svg](https://formulae.brew.sh/formula/pdf2svg) per l&#39;attività `azure_regions`.

## Configurazione

1. Installa le gemme richieste:

   ```sh
   bundle install
   ```

2. Verificare che Python, PyGMT e pdf2svg siano installati per l&#39;attività `azure_regions`. Per ulteriori dettagli sulla configurazione, consulta la documentazione nei commenti all&#39;indirizzo [_scripts/azure_regions.py](_scripts/azure_regions.py).
