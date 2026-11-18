---
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 63e52c8451f368e2d2a36096fc11c7ead62ee94e
workflow-type: tm+mt
source-wordcount: '704'
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

### `whatsnew_consolidated`

Consolida le nuove tabelle pubblicate dai progetti di documentazione di Commerce configurati in `help/_includes/automated/whatsnew/consolidated.md`.

```sh
bundle exec rake whatsnew_consolidated
```

Configurare i progetti in `whatsnew_consolidated.projects` in [`_config.yml`](_config.yml). Ogni voce richiede un nome di repository, un titolo di progetto e un URL assoluto di un sito Web HTTP(S):

```yaml
whatsnew_consolidated:
  projects:
    - repo: commerce-operations.en
      title: Adobe Commerce operational guides
      website: https://experienceleague.adobe.com/en/docs/commerce-operations/operational-guides/home
    - repo: commerce-webapi
      title: Adobe Commerce web APIs
      website: https://developer.adobe.com/commerce/webapi/
    - repo: commerce.en
      title: Adobe Commerce
      website: https://experienceleague.adobe.com/en/docs/commerce
```

Spostare le voci per modificare l&#39;ordine delle sezioni. È possibile inserire liberamente i progetti da entrambe le piattaforme. I nomi dell&#39;archivio che terminano con `.en` utilizzano il percorso di origine ExL, `help/_includes/templated/whats-new.md`. Tutti gli altri archivi utilizzano il percorso di origine DevSite, `src/pages/_includes/templated/whats-new.md`.

L&#39;attività recupera `main` file pubblici dall&#39;organizzazione GitHub `AdobeDocs`. Ogni titolo del progetto viene visualizzato come un titolo di testo normale e ogni tabella viene introdotta con una frase che collega il titolo del progetto alla home page della documentazione configurata in `website` come origine degli aggiornamenti. In vengono utilizzate `Description | Type | Date/source` intestazioni di tabella. Solo per i progetti DevSite, i tag con escape `\<br/\>` diventano `<br/>`. In caso contrario, le righe del corpo, i duplicati, i collegamenti e l’ordine delle righe di origine rimangono invariati. Ogni origine definisce il proprio periodo di tempo.

I progetti con un messaggio di mancato aggiornamento riconosciuto vengono omessi. Se per ogni progetto non è presente alcuna voce, il messaggio di inclusione contiene un messaggio generale di nessun aggiornamento. In caso di errori di configurazione, recupero, analisi o scrittura, l’attività non riesce senza sostituire un’inclusione esistente.

L&#39;attività non pianifica la generazione o l&#39;aggiornamento di pagine che consumano.

La suite di test mirati include test del punto di ingresso Rake che caricano il Rakefile `_jekyll` ed eseguono tramite Bundler. Installa prima il bundle Bundler e `_jekyll`:

```sh
cd _jekyll && bundle install
```

Quindi esegui i test dalla directory principale dell’archivio:

```sh
ruby _jekyll/test/consolidated_whatsnew_test.rb
```

### `whatsnew_feedback`

Crea `help/_includes/automated/whatsnew/consolidated-feedback.md` filtrando l&#39;inclusione locale `help/_includes/automated/whatsnew/consolidated.md` esistente.

```sh
bundle exec rake whatsnew_feedback
```

L&#39;attività corrisponde a `Feedback` come valore Type completo e separato da virgole, ignorando la distinzione tra maiuscole e minuscole e lo spazio vuoto circostante. Sono inclusi tipi combinati come `Feedback, technical`. Le menzioni nelle descrizioni, nei collegamenti di origine o nei nomi dei tipi parziali non sono idonee.

Le righe corrispondenti, i duplicati, le intestazioni di progetto in testo normale, le frasi di origine, se presenti, e l&#39;ordine dei progetti e delle righe rimangono invariati. I progetti senza voci corrispondenti vengono omessi. Se nulla corrisponde, l’output contiene un messaggio generale di nessun feedback.

L&#39;input deve esistere già. Eseguire `bundle exec rake whatsnew_consolidated` separatamente quando si desidera aggiornarlo. L’attività di feedback non recupera il contenuto remoto, non legge la configurazione del progetto e non rigenera il relativo input.

L’input mancante o non valido non riesce l’attività senza sostituire un’inclusione filtrata esistente. Il file di input non viene mai modificato e l’output filtrato viene pubblicato atomicamente.

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
