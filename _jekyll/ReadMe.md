---
source-git-commit: 90e3f9cb6033c91be67947e84520d3e2537ca5d9
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---
# Panoramica

Questo progetto utilizza le attività Rake per automatizzare parti del flusso di lavoro della documentazione. La maggior parte delle attività sono condivise tra gli archivi documenti di ExL Commerce e provengono dal gem [`adobe-comdox-exl-rake-tasks`](https://github.com/commerce-docs/adobe-comdox-exl-rake-tasks). Di seguito sono riportate alcune attività specifiche di questo archivio.

**Per le attività comuni (rendering dei modelli, gestione delle inclusioni, ottimizzazione/controllo delle immagini, generazione del riepilogo Novità), vedi il file README delle [attività adobe-comdox-exl-rake](https://github.com/commerce-docs/adobe-comdox-exl-rake-tasks/blob/main/README.md).**

> Tutti i comandi `bundle exec rake` seguenti devono essere eseguiti dall&#39;interno della directory `_jekyll/`, in quanto è qui che risiedono il file Gemfile e il file Rakefile.

## Attività Rake specifiche per l’archivio

### `whatsnew_bp`

Genera dati per un riepilogo delle notizie in Best practice. L’intervallo di tempo predefinito è dall’ultimo aggiornamento. È possibile specificare un periodo diverso utilizzando l&#39;argomento `since`.

**Utilizzo:**

```sh
bundle exec rake whatsnew_bp
```

**Con `since` argomento:**

```sh
bundle exec rake whatsnew_bp since="jul 4"
```

### `get_released_versions`

Ottiene le ultime 10 versioni rilasciate dall&#39;archivio `magento/magento2`. Richiede [GitHub CLI](https://cli.github.com/) per essere installato e autenticato.

**Utilizzo:**

```sh
bundle exec rake get_released_versions
```

**Output:** genera `tmp/core-release.txt` con i nomi e le date dei tag di rilascio.

### `first_merge_date`

Ottiene la data della prima unione in un ramo specificato. Richiede [GitHub CLI](https://cli.github.com/) per essere installato e autenticato.

**Utilizzo:**

```sh
bundle exec rake first_merge_date base=develop
```

**Argomenti:**

- `base` (obbligatorio): nome del ramo di destinazione da verificare per le unioni.

## Elenco delle attività disponibili

Per visualizzare tutte le attività di rastremazione disponibili con le relative descrizioni, utilizzare:

```sh
bundle exec rake --tasks
```

Per informazioni più dettagliate su un&#39;attività specifica, utilizzare:

```sh
bundle exec rake -T [task_name]
```

## Includi formato file relazioni

Il file `include-relationships.yml` tiene traccia delle relazioni tra i file di contenuto principale e i relativi file inclusi. Questo file viene gestito automaticamente dall&#39;attività `includes:maintain_relationships` (vedi il file README[&#128279;](https://github.com/commerce-docs/adobe-comdox-exl-rake-tasks/blob/main/README.md) di adobe-comdox-exl-rake-tasks per informazioni sull&#39;utilizzo delle attività), che rileva le relazioni leggendo i file di inclusione esistenti e trovando i file principali che vi fanno riferimento.

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

**Includi formato rendiconto:**
Nei file di contenuto principale viene utilizzata la sintassi seguente per includere altri file:

```markdown
{{$include /help/_includes/filename.md}}
```

## Prerequisiti

- Ruby e Bundler installati.
- Elementi gems richiesti specificati nel file Gem (le attività comuni sono fornite da `adobe-comdox-exl-rake-tasks`; l&#39;attività `whatsnew` richiede inoltre `whatsup_github`).
- [CLI GitHub](https://cli.github.com/) per le attività `get_released_versions` e `first_merge_date`.

## Configurazione

Installa le gemme richieste:

```sh
bundle install
```
