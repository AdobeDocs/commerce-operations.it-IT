---
title: Eseguire un aggiornamento
description: Segui questi passaggi per aggiornare un progetto Adobe Commerce o Magenti Open Source.
source-git-commit: 3c3966a904b0568e0255020d8880d348c357ea95
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Eseguire un aggiornamento

È possibile aggiornare l&#39;applicazione Adobe Commerce o Magenti Open Source dalla riga di comando se il software è stato installato da:

- Download di [metapackage](https://glossary.magento.com/metapackage) utilizzando `composer create-project` comando.
- Installazione dell&#39;archivio compresso.

>[!NOTE]
>
>Non utilizzare questo metodo per l’aggiornamento se hai clonato l’archivio GitHub. Invece, vedi [Aggiornare un’installazione basata su Git](../developer/git-installs.md) per istruzioni sull’aggiornamento.

Le istruzioni seguenti mostrano come effettuare l’aggiornamento utilizzando Composer. Adobe Commerce 2.4.2 ha introdotto il supporto per Composer 2. Se stai tentando di eseguire l&#39;aggiornamento da &lt;2.4.1, devi prima eseguire l&#39;aggiornamento a una versione compatibile con il Compositore 2 (ad esempio, 2.4.2) utilizzando il Compositore 1 _prima_ aggiornamento a Composer 2 per gli aggiornamenti a >2.4.2. Inoltre, devi eseguire un [versione supportata](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) di PHP.

>[!WARNING]
>
>La procedura per l’aggiornamento di Adobe Commerce e Magenti Open Source è cambiata. È necessario installare una nuova versione di `magento/composer-root-update-plugin` (vedi [prerequisiti](../prepare/prerequisites.md)). Inoltre, i comandi per l&#39;aggiornamento sono cambiati da `composer require magento/<package_name>` a `composer require-commerce magento/<package_name>`.

## Prima di iniziare

Devi completare la [prerequisiti per l’aggiornamento](../prepare/prerequisites.md) per preparare l’ambiente prima di avviare il processo di aggiornamento.

## Gestire i pacchetti

>[!NOTE]
>
>Per informazioni su come specificare diversi livelli di versione, consulta gli esempi alla fine di questa sezione . Ad esempio, rilascio minore, patch di qualità e patch di sicurezza. I clienti Adobe Commerce possono accedere alle patch due settimane prima della data di disponibilità generale (GA, General Availability). I pacchetti pre-release sono disponibili solo tramite Composer. Non è possibile trovarli sul portale dei download o su GitHub fino a quando non è disponibile in versione GA. Se non riesci a trovare questi pacchetti in Compositore, contatta il supporto Adobe Commerce.

1. Passa alla modalità di manutenzione per impedire l&#39;accesso allo store durante il processo di aggiornamento.

   ```bash
   bin/magento maintenance:enable
   ```

   Vedi [Attiva o disattiva la modalità di manutenzione](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html) per ulteriori opzioni. Facoltativamente, puoi creare un [pagina della modalità di manutenzione personalizzata](https://devdocs.magento.com/guides/v2.4/comp-mgr/trouble/cman/maint-mode.html).

1. L’avvio del processo di aggiornamento mentre i processi asincroni, come i consumatori della coda dei messaggi, sono in esecuzione, può causare il danneggiamento dei dati. Per evitare il danneggiamento dei dati, disattiva tutti i lavori cron.

   _Adobe Commerce sull’infrastruttura cloud:_

   ```bash
   ./vendor/bin/ece-tools cron:disable
   ```

   _Magento Open Source:_

   ```bash
   bin/magento cron:remove
   ```

1. Avvia manualmente tutti i consumatori della coda messaggi per assicurarsi che tutti i messaggi siano utilizzati.

   ```bash
   bin/magento cron:run --group=consumers
   ```

   Attendi il completamento del lavoro del cron. Puoi monitorare lo stato del processo con un visualizzatore di processi o eseguendo il `ps aux | grep 'bin/magento queue'` comando più volte fino al completamento di tutti i processi.

1. Crea un backup del `composer.json` file.

   ```bash
   cp composer.json composer.json.bak
   ```

1. Aggiungi o rimuovi pacchetti specifici in base alle tue esigenze.

   Ad esempio, se stai effettuando l’aggiornamento da Magenti Open Source ad Adobe Commerce, rimuovi il pacchetto di Magento Open Source.

   ```bash
   composer remove magento/product-community-edition --no-update
   ```

   Puoi anche aggiornare dati di esempio.

   ```bash
   composer require <sample data module-1>:<version> ... <sample data module-n>:<version> --no-update
   ```

   - _Adobe Commerce:_

      ```bash
      composer require magento/module-bundle-sample-data:100.4.* magento/module-widget-sample-data:100.4.* magento/module-theme-sample-data:100.4.* magento/module-catalog-sample-data:100.4.* magento/module-customer-sample-data:100.4.* magento/module-cms-sample-data:100.4.*  magento/module-catalog-rule-sample-data:100.4.* magento/module-sales-rule-sample-data:100.4.* magento/module-review-sample-data:100.4.* magento/module-tax-sample-data:100.4.* magento/module-sales-sample-data:100.4.* magento/module-grouped-product-sample-data:100.4.* magento/module-downloadable-sample-data:100.4.* magento/module-msrp-sample-data:100.4.* magento/module-configurable-sample-data:100.4.* magento/module-product-links-sample-data:100.4.* magento/module-wishlist-sample-data:100.4.* magento/module-swatches-sample-data:100.4.* magento/sample-data-media:100.4.* magento/module-offline-shipping-sample-data:100.4.* magento/module-gift-card-sample-data:100.4.* magento/module-customer-balance-sample-data:100.4.* magento/module-target-rule-sample-data:100.4.* magento/module-gift-registry-sample-data:100.4.* magento/module-multiple-wishlist-sample-data:100.4.* --no-update
      ```

   - _Magento Open Source:_

      ```bash
      composer require magento/module-bundle-sample-data:100.4.* magento/module-widget-sample-data:100.4.* magento/module-theme-sample-data:100.4.* magento/module-catalog-sample-data:100.4.* magento/module-customer-sample-data:100.4.* magento/module-cms-sample-data:100.4.*  magento/module-catalog-rule-sample-data:100.4.* magento/module-sales-rule-sample-data:100.4.* magento/module-review-sample-data:100.4.* magento/module-tax-sample-data:100.4.* magento/module-sales-sample-data:100.4.* magento/module-grouped-product-sample-data:100.4.* magento/module-downloadable-sample-data:100.4.* magento/module-msrp-sample-data:100.4.* magento/module-configurable-sample-data:100.4.* magento/module-product-links-sample-data:100.4.* magento/module-wishlist-sample-data:100.4.* magento/module-swatches-sample-data:100.4.* magento/sample-data-media:100.4.* magento/module-offline-shipping-sample-data:100.4.* --no-update
      ```

1. Aggiorna l’istanza utilizzando quanto segue `composer require-commerce` sintassi comando:

   ```bash
   composer require-commerce magento/<product> <version> --no-update [--interactive-root-conflicts] [--force-root-updates] [--help]
   ```

   Le opzioni di comando includono:

   - `<product>` —(Obbligatorio) Il pacchetto da aggiornare. Per gli impianti locali, tale valore deve essere `product-community-edition` o `product-enterprise-edition`.

   - `<version>` —(Obbligatorio) Versione di Adobe Commerce o Magento Open Source a cui si sta effettuando l&#39;aggiornamento. Ad esempio, `2.4.3`.

   - `--no-update` —(Obbligatorio) Disattiva l&#39;aggiornamento automatico delle dipendenze.

   - `--interactive-root-conflicts` —(Facoltativo) Ti consente di visualizzare e aggiornare in modo interattivo i valori obsoleti delle versioni precedenti o i valori personalizzati che non corrispondono alla versione a cui stai eseguendo l’aggiornamento.

   - `--force-root-updates` —(Facoltativo) Ignora tutti i valori personalizzati in conflitto con i valori Magenti previsti.

   - `--help` —(Facoltativo) Fornisce dettagli sull&#39;utilizzo del plug-in.
   Se non `--interactive-root-conflicts` né `--force-root-updates` vengono specificati, il comando mantiene i valori esistenti in conflitto e visualizza un messaggio di avviso. Per ulteriori informazioni sul plug-in, consulta la [README utilizzo plug-in](https://github.com/magento/composer-root-update-plugin/blob/develop/src/Magento/ComposerRootUpdatePlugin/README.md).

1. Aggiorna le dipendenze.

   ```bash
   composer update
   ```

### Esempio: elenco delle versioni disponibili

Per visualizzare l’elenco completo delle versioni 2.4.x disponibili:

_Magento Open Source_:

```bash
composer show magento/product-community-edition 2.4.* --available | grep -m 1 versions
```

_Adobe Commerce_:

```bash
composer show magento/product-enterprise-edition 2.4.* --available | grep -m 1 versions
```

### Esempio - Versione secondaria

Le versioni secondarie contengono nuove funzioni, correzioni di qualità e correzioni di sicurezza. Utilizza Compositore per specificare una versione secondaria. Ad esempio, per specificare il metapackage Magenti Open Source 2.4.3:

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.0 --no-update
```

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.0 --no-update
```

### Esempio - Patch di qualità

Le patch di qualità contengono principalmente elementi funzionali _e_ correzioni di sicurezza. Tuttavia, a volte possono contenere nuove funzioni compatibili con le versioni precedenti. Utilizza Compositore per scaricare una patch di qualità. Ad esempio, per specificare il metapackage Magenti Open Source 2.4.1:

```bash
composer require-commerce magento/product-community-edition 2.4.3 --no-update
```

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.3 --no-update
```

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.3 --no-update
```

### Esempio: patch di sicurezza

Le patch di sicurezza contengono solo correzioni di sicurezza. Sono progettati per rendere il processo di aggiornamento più rapido e semplice.

Le patch di sicurezza utilizzano la convenzione di denominazione del Compositore `2.4.x-px`. Utilizza Compositore per specificare una patch.

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.3-p1 --no-update
```

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.3-p1 --no-update
```

## Aggiornare i metadati

1. Aggiorna `"name"`, `"version"`e `"description"` nei campi `composer.json` se necessario.

   >[!NOTE]
   >
   >Aggiornamento dei metadati nel `composer.json` il file è del tutto superficiale, non funzionale.

1. Applica aggiornamenti.

   ```bash
   composer update
   ```

1. Elimina `var/` e `generated/` sottodirectory:

   ```bash
   rm -rf var/cache/*
   ```

   ```bash
   rm -rf var/page_cache/*
   ```

   ```bash
   rm -rf generated/code/*
   ```

   >[!NOTE]
   >
   >Se utilizzi un archivio cache diverso dal file system, ad esempio Redis o Memcache, devi cancellare manualmente anche la cache.

1. Aggiornare lo schema e i dati del database.

   ```bash
   bin/magento setup:upgrade
   ```

1. Disattiva la modalità di manutenzione.

   ```bash
   bin/magento maintenance:disable
   ```

1. _(Facoltativo)_ Riavvia Varnish.

   Se utilizzi Varnish per la memorizzazione in cache delle pagine, riavvialo:

   ```bash
   service varnish restart
   ```

## Controlla il tuo lavoro

Apri l’URL della vetrina in un browser web per verificare se l’aggiornamento è stato eseguito correttamente. Se l&#39;aggiornamento non è andato a buon fine, la vetrina non verrà caricata correttamente.

Se l’applicazione non riesce con un  `We're sorry, an error has occurred while generating this email.` errore:

1. Reimposta [proprietà e autorizzazioni del file system](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-system-perms.html) come utente con `root` privilegi.
1. Cancella le seguenti directory:
   - `var/cache/`
   - `var/page_cache/`
   - `generated/code/`
1. Controlla di nuovo la vetrina nel browser web.
