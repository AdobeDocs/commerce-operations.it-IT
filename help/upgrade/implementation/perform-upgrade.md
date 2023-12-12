---
title: Eseguire un aggiornamento
description: Per aggiornare le distribuzioni locali di Adobe Commerce, segui la procedura riportata di seguito.
exl-id: 9183f1d2-a8dd-4232-bdee-7c431e0133df
source-git-commit: 0cee0ab36274758b583c04dbee8251ce3b78e559
workflow-type: tm+mt
source-wordcount: '742'
ht-degree: 0%

---


# Eseguire un aggiornamento

È possibile eseguire l&#39;aggiornamento _on-premise_ distribuzioni dell’applicazione Adobe Commerce o di Magento Open Source dalla riga di comando se il software è stato installato:

- Scaricare il metapacchetto del Compositore utilizzando `composer create-project` comando.
- Installazione dell&#39;archivio compresso.

>[!NOTE]
>
>- Per i progetti Adobe Commerce su infrastrutture cloud, consulta [Aggiorna versione Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/commerce-version.html) nella Guida al cloud.
>- Non utilizzare questo metodo per eseguire l’aggiornamento se hai clonato l’archivio GitHub. Consulta [Aggiornare un’installazione basata su Git](../developer/git-installs.md).

Le istruzioni seguenti spiegano come eseguire l’aggiornamento utilizzando Gestione pacchetti Compositore. Adobe Commerce 2.4.2 ha introdotto il supporto per Composer 2. Se si sta tentando di eseguire l&#39;aggiornamento da &lt;2.4.1, è innanzitutto necessario eseguire l&#39;aggiornamento a una versione compatibile con Composer 2 (ad esempio, 2.4.2) utilizzando Composer 1 _prima di_ aggiornamento a Composer 2 per gli aggiornamenti >2.4.2. Inoltre, devi eseguire una [versione supportata](../../installation/system-requirements.md) del PHP.

>[!WARNING]
>
>La procedura per l’aggiornamento di Adobe Commerce e Magento Open Source è stata modificata. È necessario installare una nuova versione di `magento/composer-root-update-plugin` pacchetto (vedere [prerequisiti](../prepare/prerequisites.md)). Inoltre, i comandi per l&#39;aggiornamento sono stati modificati da `composer require magento/<package_name>` a `composer require-commerce magento/<package_name>`.

## Prima di iniziare

È necessario completare [prerequisiti per l’aggiornamento](../prepare/prerequisites.md) per preparare l’ambiente prima di avviare il processo di aggiornamento.

## Gestire i pacchetti

>[!NOTE]
>
>Consulta gli esempi alla fine di questa sezione per informazioni su come specificare diversi livelli di rilascio. Ad esempio, patch di qualità e di sicurezza. Se non riesci a trovare questi pacchetti nel Compositore, contatta il supporto Adobe Commerce.

1. Passa alla modalità di manutenzione per impedire l’accesso allo store durante il processo di aggiornamento.

   ```bash
   bin/magento maintenance:enable
   ```

   Consulta [Attiva o disattiva la modalità di manutenzione](../../installation/tutorials/maintenance-mode.md) per ulteriori opzioni. Facoltativamente, puoi creare una [pagina modalità di manutenzione personalizzata](../troubleshooting/maintenance-mode-options.md).

1. L’avvio del processo di aggiornamento durante l’esecuzione di processi asincroni, come ad esempio i consumer della coda di messaggi, può causare il danneggiamento dei dati. Per evitare il danneggiamento dei dati, disabilita tutti i processi cron.

   _Adobe Commerce sull’infrastruttura cloud:_

   ```bash
   ./vendor/bin/ece-tools cron:disable
   ```

   _Magento Open Source:_

   ```bash
   bin/magento cron:remove
   ```

1. Avvia manualmente tutti i consumer della coda di messaggi per garantire che tutti i messaggi vengano utilizzati.

   ```bash
   bin/magento cron:run --group=consumers
   ```

   Attendere il completamento del processo cron. È possibile monitorare lo stato del processo con un visualizzatore di processi o eseguendo il comando `ps aux | grep 'bin/magento queue'` fino al completamento di tutti i processi.

1. Crea un backup del `composer.json` file.

   ```bash
   cp composer.json composer.json.bak
   ```

1. Aggiungi o rimuovi pacchetti specifici in base alle tue esigenze.

   Se ad esempio si esegue l&#39;aggiornamento da Magento Open Source ad Adobe Commerce, rimuovere il pacchetto di Magento Open Source.

   ```bash
   composer remove magento/product-community-edition --no-update
   ```

   Puoi anche aggiornare i dati di esempio.

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

   - `<version>` —(Obbligatorio) La versione di Adobe Commerce o del Magento Open Source a cui si sta effettuando l&#39;aggiornamento. Ad esempio: `2.4.3`.

   - `--no-update` —(Obbligatorio) Disattiva l&#39;aggiornamento automatico delle dipendenze.

   - `--interactive-root-conflicts` —(Facoltativo) Consente di visualizzare e aggiornare in modo interattivo tutti i valori obsoleti delle versioni precedenti o qualsiasi valore personalizzato che non corrisponde alla versione a cui si sta eseguendo l&#39;aggiornamento.

   - `--force-root-updates` —(Facoltativo) Sostituisce tutti i valori personalizzati in conflitto con i valori Commerce previsti.

   - `--help` —(Facoltativo) Fornisce dettagli sull&#39;utilizzo del plug-in.

   Se nessuno dei due `--interactive-root-conflicts` né `--force-root-updates` vengono specificati, il comando mantiene i valori esistenti in conflitto e visualizza un messaggio di avviso. Per ulteriori informazioni sul plug-in, consulta [File README utilizzo plug-in](https://github.com/magento/composer-root-update-plugin/blob/develop/src/Magento/ComposerRootUpdatePlugin/README.md).

1. Aggiornare le dipendenze.

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

### Esempio: patch di qualità

Le patch di qualità contengono principalmente _e_ correzioni di sicurezza. Tuttavia, a volte possono contenere nuove funzioni compatibili con le versioni precedenti. Utilizza Composer per scaricare una patch di qualità.

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.6 --no-update
```

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.6 --no-update
```

### Esempio: patch di sicurezza

Le patch di sicurezza contengono solo correzioni di sicurezza. Sono progettati per rendere il processo di aggiornamento più rapido e semplice. Le patch di sicurezza utilizzano la convenzione di denominazione del Compositore `2.4.x-px`.

_Adobe Commerce_:

```bash
composer require-commerce magento/product-enterprise-edition 2.4.6-p3 --no-update
```

_Magento Open Source_:

```bash
composer require-commerce magento/product-community-edition 2.4.6-p3 --no-update
```

## Aggiorna metadati

1. Aggiornare il `"name"`, `"version"`, e `"description"` campi in `composer.json` file in base alle esigenze.

   >[!NOTE]
   >
   >Aggiornamento dei metadati in `composer.json` il file è completamente superficiale, non funzionale.

1. Applicare gli aggiornamenti.

   ```bash
   composer update
   ```

1. Cancella `var/` e `generated/` sottodirectory:

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
   >Se si utilizza un archivio cache diverso dal file system, ad esempio Redis o Memcached, è necessario cancellare manualmente la cache anche in questo caso.

1. Aggiornare lo schema e i dati del database.

   ```bash
   bin/magento setup:upgrade
   ```

1. Disattiva la modalità di manutenzione.

   ```bash
   bin/magento maintenance:disable
   ```

1. _(Facoltativo)_ Riavviare la vernice.

   Se utilizzi Vernice per il caching delle pagine, riavviala:

   ```bash
   service varnish restart
   ```

## Verifica il tuo lavoro

Per verificare se l’aggiornamento è stato eseguito correttamente, apri l’URL della vetrina in un browser web. Se l&#39;aggiornamento non è riuscito, la vetrina non si carica correttamente.

Se l’applicazione non riesce e viene visualizzato un  `We're sorry, an error has occurred while generating this email.` errore:

1. Reimposta [proprietà e autorizzazioni del file system](../../installation/prerequisites/file-system/configure-permissions.md) come utente con `root` privilegi.
1. Cancella le directory seguenti:
   - `var/cache/`
   - `var/page_cache/`
   - `generated/code/`
1. Controlla di nuovo la vetrina nel browser.
