---
source-git-commit: 4589c405bab743001e967a9825d578ee1a03c216
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 0%

---
# Panoramica

Questo progetto include diverse attività Rake per automatizzare vari aspetti del flusso di lavoro, ad esempio la generazione di dati per i digesti di notizie, il rendering di file con modelli, l’ottimizzazione delle immagini e la generazione di mappe. Di seguito sono riportate le descrizioni e le linee guida sull’utilizzo per ogni attività Rake definita nel file Rakefile.

## Esegui attività

### `render`

Esegue il rendering dei file modello nella directory `_jekyll/templates` con i dati di `_jekyll/_data/`. Il risultato si troverà nella directory `help/includes/templated`. Questa attività mantiene automaticamente le relazioni di inclusione e i timestamp dopo il rendering.

**Utilizzo:**

```sh
rake render
```

**Funzionamento:**
- Esegue lo script di rendering per generare file con modelli
- Esegue `includes:maintain_all` per aggiornare le relazioni di inclusione e i timestamp
- Assicura che tutti i metadati inclusi siano correnti dopo il rendering

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

### `get_released_versions`

Ottiene le ultime 10 versioni rilasciate dall&#39;archivio `magento/magento2`. Richiede [GitHub CLI](https://cli.github.com/) per essere installato e autenticato.

**Utilizzo:**

```sh
rake get_released_versions
```

**Output:** genera `tmp/core-release.txt` con i nomi e le date dei tag di rilascio.

### `first_merge_date`

Ottiene la data della prima unione in un ramo specificato. Richiede [GitHub CLI](https://cli.github.com/) per essere installato e autenticato.

**Utilizzo:**

```sh
rake first_merge_date base=develop
```

**Argomenti:**

- `base` (obbligatorio): nome del ramo di destinazione da verificare per le unioni.

### `includes:maintain_relationships`

Rileva e aggiorna il file `include-relationships.yml` analizzando tutti i file Markdown nella directory `help` per individuare le istruzioni di inclusione che utilizzano il modello `{{$include /help/_includes/filename.md}}`. Questa attività mantiene automaticamente le relazioni tra i file di contenuto principale e i relativi file inclusi.

**Utilizzo:**

```sh
rake includes:maintain_relationships
```

**Funzionamento:**
- Legge l&#39;elenco dei file di inclusione esistenti dalla directory `help/_includes`
- Esegue la ricerca in tutti i file markdown principali per individuare quelli che fanno riferimento a ciascuno di essi
- Utilizza il pattern `{{$include /help/_includes/filename.md}}` per identificare i riferimenti
- Aggiorna il file `include-relationships.yml` con le relazioni individuate
- Fornisce un riepilogo delle modifiche apportate e identifica gli inclusioni senza riferimenti

### `includes:maintain_timestamps`

Mantiene i timestamp di inclusione aggiungendo i timestamp di modifica del file di inclusione più recenti ai file principali. Questa attività legge il file `include-relationships.yml`, controlla la cronologia Git per ciascun file di inclusione e aggiunge o aggiorna i timestamp alla fine dei file principali.

**Utilizzo:**

```sh
rake includes:maintain_timestamps
```

**Funzionamento:**
- I caricamenti includono relazioni da `include-relationships.yml`
- Per ogni file principale, trova la data di commit Git più recente tra i suoi file di inclusione
- Aggiunge o aggiorna i commenti di HTML con marca temporale alla fine dei file principali
- Utilizza il formato: `<!-- Last updated from includes: YYYY-MM-DD HH:MM:SS -->`
- Fornisce un output dettagliato che mostra quali file di inclusione sono stati controllati e i relativi timestamp

**Output di esempio:**

```console
Processing installation/advanced.md...
  Latest include change: 2024-04-16 09:42:31
  Include files checked: help/_includes/cli-consumers.md (2022-09-12 09:38:25), help/_includes/secure-install.md (2022-09-08 11:33:05), help/_includes/sensitive-data.md (2024-04-16 09:42:31)
  Added new timestamp
```

### `includes:maintain_all`

Un&#39;attività di convenienza che esegue `includes:maintain_relationships` e `includes:maintain_timestamps` in sequenza. Questo è il modo consigliato per mantenere sia le relazioni di inclusione che i timestamp.

**Utilizzo:**

```sh
rake includes:maintain_all
```

### `unused_includes`

Trova i file di inclusione nella directory `help/_includes` a cui non viene fatto riferimento da alcun file markdown. Questo aiuta a identificare i file di inclusione orfani che possono essere rimossi in modo sicuro.

**Utilizzo:**

```sh
rake unused_includes
```

## Elenco delle attività disponibili

Per visualizzare tutte le attività di rastremazione disponibili con le relative descrizioni, utilizzare:

```sh
rake --tasks
```

Per informazioni più dettagliate su un&#39;attività specifica, utilizzare:

```sh
rake -T [task_name]
```

## Includi attività di gestione

Tutte le attività correlate all&#39;inclusione sono organizzate nello spazio dei nomi `includes` per una migliore organizzazione:

```sh
# Discover and maintain include relationships
rake includes:maintain_relationships

# Add/update timestamps based on include file changes
rake includes:maintain_timestamps

# Do both operations in sequence (recommended)
rake includes:maintain_all
```

## Includi formato file relazioni

Il file `include-relationships.yml` tiene traccia delle relazioni tra i file di contenuto principale e i relativi file inclusi. Questo file viene gestito automaticamente dall&#39;attività di rake `maintain_include_relationships`, che rileva le relazioni leggendo i file di inclusione esistenti e individuando i file principali che vi fanno riferimento.

**Struttura file:**

```yaml
---
metadata:
  last_updated: '2025-08-22 14:04:37'
  description: 'Index of main files and their included files for automatic timestamp updates'
  total_relationships: 57
  auto_discovered: true
  discovery_date: '2025-08-22 14:04:37'
relationships:
  configuration/deployment/example-environment-variables.md:
    - "/help/_includes/config-save-config.md"
    - "/help/_includes/config-update-build-system.md"
    - "/help/_includes/config-update-prod-system.md"
  # ... more relationships
```

**Campi:**
- `metadata.last_updated`: Timestamp dell&#39;ultimo aggiornamento
- `metadata.total_relationships`: numero totale di file principali con inclusioni
- `metadata.auto_discovered`: indica che il file è stato generato automaticamente
- `metadata.discovery_date`: data in cui sono state individuate le prime relazioni
- `relationships`: mapping dei file principali ai relativi file inclusi

**Includi formato istruzione:**
Nei file di contenuto principale viene utilizzata la sintassi seguente per includere altri file:

```markdown
{{$include /help/_includes/filename.md}}
```

## Prerequisiti

- Ruby e Bundler installati.
- Gemme obbligatorie specificate nel file Gem (le dipendenze di base sono fornite da `adobe-comdox-exl-rake-tasks`).
- [CLI GitHub](https://cli.github.com/) per le attività `get_released_versions` e `first_merge_date`.
- Python, [PyGMT](https://www.pygmt.org/latest/install.html) e [pdf2svg](https://formulae.brew.sh/formula/pdf2svg) per l&#39;attività `azure_regions`.

## Configurazione

1. Installa le gemme richieste:

   ```sh
   bundle install
   ```

2. Verificare che Python, PyGMT e pdf2svg siano installati per l&#39;attività `azure_regions`. Per ulteriori dettagli sulla configurazione, consulta la documentazione nei commenti all&#39;indirizzo [_scripts/azure_regions.py](_scripts/azure_regions.py).
