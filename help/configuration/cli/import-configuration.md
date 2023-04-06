---
title: Importare dati dai file di configurazione
description: Importa le impostazioni di configurazione di Adobe Commerce dai file di configurazione.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---


# Importa impostazioni di configurazione

{{file-system-owner}}

Quando si imposta un sistema di produzione utilizzando Commerce 2.2 [modello di distribuzione della pipeline](../deployment/technical-details.md), devi _importare_ impostazioni di configurazione da `config.php` e `env.php` nel database.
Queste impostazioni includono percorsi e valori di configurazione, siti web, store, viste store e temi.

Dopo aver importato siti web, store, viste store e temi, puoi creare attributi di prodotto e applicarli a siti web, negozi e viste store sul sistema di produzione.

>[!INFO]
>
>La `bin/magento app:config:import` Il comando non elabora la configurazione memorizzata nelle variabili di ambiente.

## Importa, comando

Sul sistema di produzione, esegui il seguente comando per importare dati dai file di configurazione (`config.php` e `env.php`) nel database:

```bash
bin/magento app:config:import [-n, --no-interaction]
```

Utilizza l’opzione `[-n, --no-interaction]` contrassegna per importare i dati senza alcuna interazione.

Se immetti `bin/magento app:config:import` senza il flag opzionale, è necessario confermare le modifiche.

Ad esempio, se il file di configurazione contiene un nuovo sito web e un nuovo archivio, viene visualizzato il seguente messaggio:

```terminal
These Websites will be created: New Website
These Groups will be created: New Store
Do you want to continue [yes/no]?
```

Per continuare l’importazione, immetti `yes`.

Se i file di configurazione della distribuzione contengono alcuni dati da importare, viene visualizzato un messaggio simile al seguente:

```terminal
Start import:
Some information about importing
```

Se i file di configurazione della distribuzione non contengono dati da importare, viene visualizzato un messaggio simile al seguente:

```terminal
Start import:
Nothing to import
```

## Cosa importiamo

Nelle sezioni seguenti vengono descritti in dettaglio i dati importati.

### Configurazione del sistema

Commerce utilizza direttamente i valori in `system` nella `config.php` o `env.php` anziché importarli nel database perché richiedono alcune azioni di pre e post-elaborazione.

Ad esempio, il valore del percorso di configurazione `web/secure/base_url` deve essere convalidato con modelli di backend.

#### Modelli back-end

I modelli back-end sono il meccanismo per l&#39;elaborazione delle modifiche nella configurazione del sistema.
Definisci i moduli di backend in `<module_name>/adminhtml/system.xml`.

Tutti i modelli di backend devono estendere [`Magento\Framework\App\Config\Value`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config/Value.php) classe.

Quando importiamo modelli di back-end, non vengono salvati i valori di configurazione.

### Configurazione di siti web, archivi e gruppi di archivi

Importiamo i seguenti tipi di configurazioni.
(Queste configurazioni si trovano nella sezione `scopes` in matrice `config.php`.)

- `websites`: configurazione dei siti web
- `groups`: memorizza la configurazione correlata
- `stores`: configurazione correlata alle viste store

Le configurazioni precedenti possono essere importate nelle seguenti modalità:

- `create`: `config.php` contiene nuove entità (`websites`, `groups`, `stores`) assenti nell&#39;ambiente di produzione
- `update`: `config.php` contiene entità (`websites`, `groups`, `stores`) diverse dall’ambiente di produzione
- `delete`: `config.php` does _not_ contiene entità (`websites`, `groups`, `stores`) presenti nell&#39;ambiente di produzione

>[!INFO]
>
>Non importiamo la categoria principale associata agli archivi. È necessario associare una categoria principale a un archivio utilizzando Commerce Admin.

### Configurazione del tema

La configurazione dei temi include tutti i temi registrati nel tuo sistema Commerce; i dati provengono direttamente dal `theme` tabella del database. (La configurazione del tema si trova nel `themes` in matrice `config.php`.)

#### Struttura dei dati del tema

La chiave dell&#39;array è il percorso a tema completo: `area` + `theme path`

Ad esempio: `frontend/Magento/luma`.
`frontend` è area e `Magento/luma` è il percorso del tema.

Il valore dell&#39;array è dato sul tema: codice, titolo, percorso, id padre

Esempio completo:

```php?start_inline=1
'frontend/Magento/luma' =>
   array (
      'parent_id' => 'Magento/blank',
      'theme_path' => 'Magento/luma',
      'theme_title' => 'Magento Luma',
      'is_featured' => '0',
      'area' => 'frontend',
      'type' => '0',
      'code' => 'Magento/luma',
),
```

>[!INFO]
>
>- _Registrazione del tema_. Se i dati di un tema sono definiti in `config.php` ma il codice sorgente del tema non è presente nel file system, il tema viene ignorato (cioè, non registrato).
>- _Rimozione del tema_. Se un tema non è presente in `config.php` ma il codice sorgente è presente nel file system, il tema non viene rimosso.

