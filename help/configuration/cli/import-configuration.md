---
title: Importare dati dai file di configurazione
description: Importa le impostazioni di configurazione di Adobe Commerce dai file di configurazione.
exl-id: 7d9f156c-e8d3-4888-b359-5d9aa8c4ea05
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 0%

---

# Importa impostazioni di configurazione

{{file-system-owner}}

Quando imposti un sistema di produzione utilizzando Commerce 2.2 [modello di distribuzione della pipeline](../deployment/technical-details.md), è necessario _importa_ impostazioni di configurazione da `config.php` e `env.php` nel database.
Queste impostazioni includono percorsi e valori di configurazione, siti web, store, visualizzazioni store e temi.

Dopo aver importato siti Web, store, visualizzazioni di store e temi, puoi creare attributi di prodotto e applicarli a siti Web, store e visualizzazioni di store nel sistema di produzione.

>[!INFO]
>
>Il `bin/magento app:config:import` Il comando non elabora la configurazione archiviata nelle variabili di ambiente.

## Importa, comando

Nel sistema di produzione, eseguire il comando seguente per importare i dati dai file di configurazione (`config.php` e `env.php`) al database:

```bash
bin/magento app:config:import [-n, --no-interaction]
```

Utilizzare l&#39;opzione `[-n, --no-interaction]` flag per importare dati senza alcuna interazione.

Se si immette `bin/magento app:config:import` senza il flag opzionale, è necessario confermare le modifiche.

Ad esempio, se il file di configurazione contiene un nuovo sito Web e un nuovo archivio, viene visualizzato il seguente messaggio:

```terminal
These Websites will be created: New Website
These Groups will be created: New Store
Do you want to continue [yes/no]?
```

Per continuare l&#39;importazione, immetti `yes`.

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

Commerce utilizza direttamente i valori in `system` array in `config.php` o `env.php` anziché importarli nel database perché richiedono alcune azioni di pre e post-elaborazione.

Ad esempio, il valore del percorso di configurazione `web/secure/base_url` deve essere convalidato con modelli di back-end.

#### Modelli di back-end

I modelli di back-end sono il meccanismo per l&#39;elaborazione delle modifiche nella configurazione del sistema.
Puoi definire i moduli back-end in `<module_name>/adminhtml/system.xml`.

Tutti i modelli di back-end devono estendere [`Magento\Framework\App\Config\Value`](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Config/Value.php) classe.

Quando si importano modelli di back-end, i valori di configurazione non vengono salvati.

### Configurazione di siti Web, store e gruppi di store

Importiamo i seguenti tipi di configurazioni.
(Queste configurazioni sono incluse nel `scopes` array in `config.php`.)

- `websites`: configurazione relativa ai siti web
- `groups`: memorizza la configurazione correlata
- `stores`: configurazione correlata alle visualizzazioni archivio

Le configurazioni precedenti possono essere importate nelle seguenti modalità:

- `create`: `config.php` contiene nuove entità (`websites`, `groups`, `stores`) assenti nell&#39;ambiente di produzione
- `update`: `config.php` contiene entità (`websites`, `groups`, `stores`) che sono diversi dall&#39;ambiente di produzione
- `delete`: `config.php` fa _non_ contiene entità (`websites`, `groups`, `stores`) presenti nell&#39;ambiente di produzione

>[!INFO]
>
>Non viene importata la categoria principale associata agli store. È necessario associare una categoria principale a un archivio utilizzando l’amministratore di Commerce.

### Configurazione tema

La configurazione del tema include tutti i temi registrati nel sistema Commerce; i dati provengono direttamente dal `theme` tabella di database. (La configurazione del tema si trova in `themes` array in `config.php`.)

#### Struttura dei dati relativi al tema

La chiave dell’array è il percorso del tema completo: `area` + `theme path`

Ad esempio: `frontend/Magento/luma`.
`frontend` è l’area e `Magento/luma` è il percorso del tema.

Il valore dell’array è dato dal tema: codice, titolo, percorso, ID principale

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
>- _Registrazione tema_. Se i dati di un tema sono definiti in `config.php` ma il codice sorgente del tema non è presente nel file system, il tema viene ignorato (ovvero non registrato).
>- _Rimozione tema_. Se un tema non è presente in `config.php` ma il codice sorgente è presente nel file system, il tema non viene rimosso.

