---
title: Dettagli tecnici
description: Scopri i dettagli tecnici della distribuzione della pipeline, i tipi di configurazioni e i flussi di lavoro consigliati.
exl-id: a396d241-f895-4414-92af-3abf3511e62a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '1254'
ht-degree: 0%

---

# Dettagli tecnici

Questo argomento illustra i dettagli tecnici dell’implementazione della pipeline in Commerce 2.2 e versioni successive. I miglioramenti possono essere suddivisi nelle seguenti aree:

- [Gestione della configurazione](#configuration-management)
- [Modifiche in Admin](#changes-in-the-admin)
- [Installare e rimuovere cron](#install-and-remove-cron)

In questo argomento viene inoltre illustrato il [flusso di lavoro consigliato](#recommended-workflow) per la distribuzione della pipeline e vengono forniti alcuni esempi per comprendere il funzionamento.

Prima di iniziare, controlla i [Prerequisiti per i sistemi di sviluppo, generazione e produzione](../deployment/prerequisites.md).

## Gestione della configurazione

Per consentire la sincronizzazione e la gestione della configurazione dei sistemi di sviluppo e produzione, utilizzare il seguente schema di sostituzione.

![Determinazione dei valori delle variabili di configurazione](../../assets/configuration/override-flow-diagram.png)

Come illustrato nel diagramma, i valori di configurazione vengono utilizzati nell&#39;ordine seguente:

1. Le variabili di ambiente, se esistenti, sostituiscono tutti gli altri valori.
1. Dai file di configurazione condivisi `env.php` e `config.php`. I valori in `env.php` sostituiscono i valori in `config.php`.
1. Da valori memorizzati nel database.
1. Se in una di queste origini non esiste alcun valore, viene utilizzato il valore predefinito o NULL.

### Gestire la configurazione condivisa

La configurazione condivisa è archiviata in `app/etc/config.php`, che deve trovarsi nel controllo del codice sorgente.

Imposta la configurazione condivisa nell&#39;Admin nel tuo sistema di sviluppo (o Adobe Commerce sull&#39;infrastruttura cloud _integrazione_) e scrivi la configurazione in `config.php` utilizzando il comando [`magento app:config:dump`](../cli/export-configuration.md).

### Gestire la configurazione specifica del sistema

La configurazione specifica del sistema è archiviata in `app/etc/env.php`, che dovrebbe _non_ essere nel controllo del codice sorgente.

Imposta la configurazione specifica del sistema nell&#39;Admin nel tuo sistema di sviluppo (o Adobe Commerce sull&#39;integrazione dell&#39;infrastruttura cloud) e scrivi la configurazione su `env.php` utilizzando il comando [`magento app:config:dump`](../cli/export-configuration.md).

Questo comando scrive anche le impostazioni sensibili in `env.php`.

### Gestire la configurazione sensibile

La configurazione sensibile è archiviata anche in `app/etc/env.php`.

Puoi gestire la configurazione sensibile in uno dei seguenti modi:

- Variabili di ambiente
- Salva la configurazione sensibile in `env.php` nel sistema di produzione utilizzando il comando [`magento config:set:sensitive`](../cli/set-configuration-values.md)

### Impostazioni di configurazione bloccate in Amministrazione

Tutte le impostazioni di configurazione in `config.php` o `env.php` sono bloccate nell&#39;amministratore, ovvero non possono essere modificate nell&#39;amministratore.
Utilizzare il comando [`magento config:set` o `magento config:set --lock`](../cli/export-configuration.md#config-cli-config-set) per modificare le impostazioni nei file `config.php` o `env.php`.

## L’Amministratore Commerce

Durante la modalità di produzione, l’amministratore mostra il seguente comportamento:

- Non è possibile abilitare o disabilitare i tipi di cache nell’amministratore
- Le impostazioni per gli sviluppatori non sono disponibili (**Archivi** > Impostazioni > **Configurazione** > Avanzate > **Sviluppatore**), tra cui:

   - Minimizzare CSS, JavaScript e HTML
   - Unisci CSS e JavaScript
   - Compilazione LESS lato server o lato client
   - Traduzioni in linea
   - Come descritto in precedenza, qualsiasi impostazione di configurazione in `config.php` o `env.php` è bloccata e non può essere modificata nell&#39;amministratore.
   - È possibile modificare le impostazioni locali dell&#39;amministratore solo nelle lingue utilizzate dai temi distribuiti

     Nella figura seguente viene illustrato un esempio dell&#39;elenco **Impostazioni account** > **Impostazioni internazionali interfaccia** dell&#39;amministratore che mostra solo due impostazioni internazionali distribuite:

     ![È possibile modificare le impostazioni locali dell&#39;amministratore solo nelle impostazioni locali distribuite](../../assets/configuration/split-deploy-admin-locale.png)

- Non è possibile modificare le configurazioni locali per alcun ambito utilizzando Admin.

  È consigliabile apportare queste modifiche prima di passare alla modalità di produzione.

  È comunque possibile configurare le impostazioni locali utilizzando le variabili di ambiente o il comando CLI `config:set` con il percorso `general/locale/code`.

## Installare e rimuovere cron

Nella versione 2.2, per la prima volta, ti aiutiamo a configurare il processo cron fornendo il comando [`magento cron:install`](../cli/configure-cron-jobs.md). Questo comando imposta una scheda cronologica come utente che esegue il comando.

È inoltre possibile rimuovere la scheda cronologica utilizzando il comando `magento cron:remove`.

## Flusso di lavoro di distribuzione della pipeline consigliato

Il diagramma seguente mostra come si consiglia di utilizzare la distribuzione della pipeline per gestire la configurazione.

![Flusso di lavoro di distribuzione pipeline consigliato](../../assets/configuration/split-deploy-workflow.png)

### Sistema di sviluppo

Nel sistema di sviluppo, è possibile apportare modifiche alla configurazione nell&#39;amministratore e generare la configurazione condivisa, `app/etc/config.php` e la configurazione specifica del sistema, `app/etc/env.php`. Controlla il codice Commerce e la configurazione condivisa nel controllo del codice sorgente e inviala al server di build.

Devi anche installare le estensioni e personalizzare il codice Commerce sul sistema di sviluppo.

Sul sistema di sviluppo:

1. Imposta la configurazione in Admin.

1. Utilizzare il comando `magento app:config:dump` per scrivere la configurazione nel file system.

   - `app/etc/config.php` è la configurazione condivisa, che contiene tutte le impostazioni _eccetto_ impostazioni sensibili e specifiche del sistema. Il file deve trovarsi nel controllo del codice sorgente.
   - `app/etc/env.php` è la configurazione specifica del sistema, che contiene impostazioni univoche per un sistema specifico (ad esempio, nomi host e numeri di porta). Il file _non_ deve essere incluso nel controllo del codice sorgente.

1. Aggiungere il codice modificato e la configurazione condivisa al controllo del codice sorgente.

1. Per rimuovere il codice php generato e i file di risorse statiche durante lo sviluppo, esegui i seguenti comandi:

   ```bash
   rm -r var/view_preprocessed/*
   rm -r pub/static/*/*
   rm -r generated/*/*
   ```

Dopo aver eseguito i comandi per cancellare le risorse, Commerce genera i file di lavoro.

>[!WARNING]
>
>Fai attenzione con l’approccio di cui sopra. L&#39;eliminazione del file `.htacces` nella cartella `generated` o `pub` può causare problemi.

### Genera sistema

Il sistema di build compila il codice e genera file di visualizzazione statica per i temi registrati in Commerce. Non è necessaria una connessione al database di Commerce, ma solo la base di codice Commerce.

Sul sistema di build:

1. Estrarre il file di configurazione condiviso dal controllo del codice sorgente.
1. Utilizzare il comando `magento setup:di:compile` per compilare il codice.
1. Utilizzare il comando `magento setup:static-content:deploy -f` per aggiornare i file di visualizzazione dei file statici.
1. Controllare gli aggiornamenti nel controllo del codice sorgente.

>[!INFO]
>
>Vedere [Strategie di distribuzione per i file di visualizzazione statica](../cli/static-view-file-strategy.md).

### Sistema di produzione

Nel sistema di produzione (ovvero nel tuo archivio live), puoi estrarre le risorse generate e gli aggiornamenti del codice dal controllo del codice sorgente e impostare impostazioni di configurazione specifiche del sistema e sensibili utilizzando la riga di comando o le variabili di ambiente.

Sul sistema di produzione:

1. Avvia la modalità di manutenzione.
1. Recupera gli aggiornamenti del codice e della configurazione dal controllo del codice sorgente.
1. Se si utilizza Adobe Commerce, arrestare i processi di lavoro in coda.
1. Utilizzare il comando `magento app:config:import` per importare le modifiche alla configurazione nel sistema di produzione.
1. Se sono stati installati componenti che hanno modificato lo schema del database, eseguire `magento setup:upgrade --keep-generated` per aggiornare lo schema e i dati del database, mantenendo i file statici generati.
1. Per impostare le impostazioni specifiche del sistema, utilizzare il comando `magento config:set` o le variabili di ambiente.
1. Per impostare le impostazioni sensibili, utilizzare il comando `magento config:sensitive:set` o le variabili di ambiente.
1. Pulire (indicato anche come _svuotare_) la cache.
1. Termina modalità di manutenzione.

## Comandi di gestione della configurazione

Per facilitare la gestione della configurazione, vengono forniti i seguenti comandi:

- [`magento app:config:dump`](../cli/export-configuration.md) per scrivere le impostazioni di configurazione amministratore in `config.php` e `env.php` (tranne le impostazioni sensibili)
- [`magento config:set`](../cli/set-configuration-values.md) per impostare i valori delle impostazioni specifiche del sistema nel sistema di produzione.

  Utilizzare l&#39;opzione facoltativa `--lock` per bloccare l&#39;opzione in Admin (ovvero, rendere l&#39;impostazione non modificabile). Se un&#39;impostazione è già bloccata, utilizzare l&#39;opzione `--lock` per modificarla.

- [`magento config:sensitive:set`](../cli/set-configuration-values.md) per impostare i valori delle impostazioni sensibili nel sistema di produzione.
- [`magento app:config:import`](../cli/import-configuration.md) per importare le modifiche di configurazione da `config.php` e `env.php` nel sistema di produzione.

## Esempi di gestione della configurazione

In questa sezione vengono illustrati alcuni esempi di gestione della configurazione che consentono di visualizzare le modifiche apportate a `config.php` e `env.php`.

### Modificare le impostazioni internazionali predefinite

In questa sezione viene illustrata la modifica apportata a `config.php` quando si modifica l&#39;unità di misura predefinita utilizzando l&#39;Admin (**Stores** > Settings > **Configuration** > General > **General** > **Locale Options**).

Dopo aver apportato la modifica in Admin, eseguire `bin/magento app:config:dump` per scrivere il valore in `config.php`. Il valore viene scritto nell&#39;array `general` in `locale`, come mostra il seguente snippet da `config.php`:

```php
'general' =>
    array (
        'locale' =>
        array (
            'code' => 'en_US',
            'timezone' => 'America/Chicago',
            'weight_unit' => 'kgs'
        )
    )
```

### Modificare diverse impostazioni di configurazione

Questa sezione descrive come apportare le seguenti modifiche alla configurazione:

- Aggiunta di una visualizzazione sito Web, archivio e archivio (**Archivi** > Impostazioni > **Tutti gli archivi**)
- Modifica del dominio e-mail predefinito (**Archivi** > Impostazioni > **Configurazione** > Clienti > **Configurazione cliente**)
- Impostazione del nome utente e della password API di PayPal (**Archivi** > Impostazioni > **Configurazione** > Vendite > **Metodi di pagamento** > **PayPal** > **Impostazioni PayPal richieste**)

Dopo aver apportato la modifica in Admin, esegui `bin/magento app:config:dump` sul tuo sistema di sviluppo. Questa volta non tutte le modifiche sono state scritte in `config.php`. In effetti, solo le visualizzazioni del sito Web, dello store e dello store vengono scritte nel file come mostrato nei frammenti seguenti.

### config.php

`config.php` contiene:

- Modifiche alla visualizzazione del sito Web, dello store e dello store.
- Impostazioni del motore di ricerca non specifiche del sistema
- Impostazioni PayPal non sensibili
- Commenti che ti informano sulle impostazioni sensibili omesse da `config.php`

Array `websites`:

```php
      'new' =>
      array (
        'website_id' => '2',
        'code' => 'new',
        'name' => 'New website',
        'sort_order' => '0',
        'default_group_id' => '2',
        'is_default' => '0',
      ),
```

Array `groups`:

```php
      2 =>
      array (
        'group_id' => '2',
        'website_id' => '2',
        'code' => 'newstore',
        'name' => 'New store',
        'root_category_id' => '2',
        'default_store_id' => '2',
      ),
```

Array `stores`:

```php
     'newview' =>
      array (
        'store_id' => '2',
        'code' => 'newview',
        'website_id' => '2',
        'group_id' => '2',
        'name' => 'New store view',
        'sort_order' => '0',
        'is_active' => '1',
      ),
```

Array `payment`:

```php
      'payment' =>
      array (
        'paypal_express' =>
        array (
          'active' => '0',
          'in_context' => '0',
          'title' => 'PayPal Express Checkout',
          'sort_order' => NULL,
          'payment_action' => 'Authorization',
          'visible_on_product' => '1',
          'visible_on_cart' => '1',
          'allowspecific' => '0',
          'verify_peer' => '1',
          'line_items_enabled' => '1',
          'transfer_shipping_options' => '0',
          'solution_type' => 'Mark',
          'require_billing_address' => '0',
          'allow_ba_signup' => 'never',
          'skip_order_review_step' => '1',
        ),
```

### env.php

L&#39;impostazione di configurazione predefinita specifica per il sistema del dominio e-mail è scritta in `app/etc/env.php`.

Le impostazioni PayPal non vengono scritte in nessun file perché il comando `bin/magento app:config:dump` non scrive impostazioni sensibili. È necessario impostare le impostazioni PayPal sul sistema di produzione utilizzando i seguenti comandi:

```bash
bin/magento config:sensitive:set paypal/wpp/api_username <username>
```

```bash
bin/magento config:sensitive:set paypal/wpp/api_password <password>
```
