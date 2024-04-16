---
title: Installare un’estensione
description: Per installare un’estensione Adobe Commerce o di Magento Open Source, segui la procedura riportata di seguito.
exl-id: b564662a-2e5f-4fa9-bae1-ca7498478fa9
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 0%

---

# Installare un’estensione

Il codice che estende o personalizza il comportamento di Adobe Commerce è chiamato estensione. Facoltativamente, puoi creare un pacchetto e distribuire estensioni sul [Commerce Marketplace](https://marketplace.magento.com) o un altro sistema di distribuzione delle estensioni.

Le estensioni includono:

- Moduli (estendere le funzionalità di Adobe Commerce)
- Temi (cambia l’aspetto della vetrina e dell’amministratore)
- Pacchetti di lingua (localizza la vetrina e Amministratore)

>[!TIP]
>
>Questo argomento spiega come utilizzare la riga di comando per installare le estensioni acquistate da Commerci Marketplace. È possibile utilizzare la stessa procedura per installare _qualsiasi_ estensione; tutto ciò di cui hai bisogno è il nome e la versione del Compositore dell’estensione. Per trovarlo, apri il file dell’estensione `composer.json` e annota i valori per `"name"` e `"version"`.

Prima dell&#39;installazione, è possibile:

1. Eseguire il backup del database.
1. Abilita modalità di manutenzione:

   ```bash
   bin/magento maintenance:enable
   ```

Per installare un&#39;estensione, è necessario:

1. Ottieni un’estensione da Commerci Marketplace o da un altro sviluppatore di estensioni.
1. Se installi un’estensione dalla Commerce Marketplace, assicurati che il `repo.magento.com` esiste nel tuo archivio `composer.json` file:

   ```bash
   "repositories": [
       {
           "type": "composer",
           "url": "https://repo.magento.com/"
       }
   ]
   ```

1. Ottieni il nome e la versione del Compositore dell’estensione.
1. Aggiornare il `composer.json` nel progetto con il nome e la versione dell’estensione.
1. Verifica che l’estensione sia installata correttamente.
1. Abilita e configura l&#39;estensione.

## Ottieni il nome e la versione del Compositore estensioni

Se conosci già il nome e la versione del Compositore dell&#39;estensione, salta questo passaggio e continua con [Aggiorna il tuo `composer.json` file](#update-your-composer-file).

Per ottenere il nome e la versione del Compositore dell&#39;estensione dalla Commerce Marketplace:

1. Accedi a [Commerce Marketplace](https://marketplace.magento.com) con il nome utente e la password utilizzati per acquistare l’estensione.

1. Nell’angolo superiore destro, fai clic su **Il tuo nome** > **Il mio profilo**.

   ![Accedi al tuo account Marketplace](../../assets/installation/marketplace-my-profile.png)

1. Clic **I miei acquisti**.

   ![Cronologia acquisti Marketplace](../../assets/installation//marketplace-my-purchases.png)

1. Trova l’estensione da installare e fai clic su **Dettagli tecnici**.

   ![I dettagli tecnici mostrano il nome del compositore dell’estensione](../../assets/installation/marketplace-extension-technical-details.png)

>[!TIP]
>
>In alternativa, puoi trovare il nome e la versione del Compositore di _qualsiasi_ (acquistata su Commerce Marketplace o altrove) nel file dell’estensione `composer.json` file.

## Aggiornare il file Composer

Aggiungi il nome e la versione dell&#39;estensione al tuo `composer.json` file:

1. Vai alla directory del progetto e aggiorna la `composer.json` file.

   ```bash
   composer require <component-name>:<version>
   ```

   Ad esempio:

   ```bash
   composer require j2t/module-payplug:2.0.2
   ```

1. Immetti il [chiavi di autenticazione](../prerequisites/authentication-keys.md). La chiave pubblica è il nome utente; la chiave privata è la password.

1. Attendi che Composer completi l’aggiornamento delle dipendenze del progetto e assicurati che non siano presenti errori:

   ```terminal
   Updating dependencies (including require-dev)
   Package operations: 1 install, 0 updates, 0 removals
     - Installing j2t/module-payplug (2.0.2): Downloading (100%)
   Writing lock file
   Generating autoload files
   ```

## Verificare l’estensione

Per verificare che l’estensione sia installata correttamente, esegui il seguente comando:

```bash
bin/magento module:status J2t_Payplug
```

Per impostazione predefinita, l’estensione è probabilmente disabilitata:

```terminal
Module is disabled
```

Il nome dell’estensione è nel formato `<VendorName>_<ComponentName>`: formato diverso dal nome del Compositore. Utilizza questo formato per abilitare l&#39;estensione. Se non sei sicuro del nome dell’estensione, esegui:

```bash
bin/magento module:status
```

E cerca l’estensione in &quot;Elenco dei moduli disabilitati&quot;.

## Abilitare l’estensione

Alcune estensioni non funzionano correttamente a meno che non si cancellino prima i file di visualizzazione statica generati. Utilizza il `--clear-static-content` per cancellare i file della vista statica quando abiliti un’estensione.

1. Abilita l’estensione e cancella i file della vista statica:

   ```bash
   bin/magento module:enable J2t_Payplug --clear-static-content
   ```

   Dovresti visualizzare il seguente output:

   ```terminal
   The following modules have been enabled:
   - J2t_Payplug
   
   To make sure that the enabled modules are properly registered, run 'setup:upgrade'.
   Cache cleared successfully.
   Generated classes cleared successfully. Please run the 'setup:di:compile' command to generate classes.
   Generated static view files cleared successfully.
   ```

1. Registra l&#39;estensione:

   ```bash
   bin/magento setup:upgrade
   ```

1. Ricompilare il progetto: in modalità di produzione, è possibile che venga visualizzato un messaggio indicante &quot;Esegui nuovamente il comando di compilazione del Magento&quot;. L&#39;applicazione non richiede di eseguire il comando di compilazione in modalità Sviluppatore.

   ```bash
   bin/magento setup:di:compile
   ```

1. Verifica che l’estensione sia abilitata:

   ```bash
   bin/magento module:status J2t_Payplug
   ```

   Dovresti vedere l’output che verifica che l’estensione non sia più disabilitata:

   ```terminal
   Module is enabled
   ```

1. Pulisci la cache:

   ```bash
   bin/magento cache:clean
   ```

1. Configura l&#39;estensione in Admin secondo necessità.

>[!TIP]
>
>Se riscontri errori durante il caricamento della vetrina in un browser, usa il seguente comando per cancellare la cache: `bin/magento cache:flush`.

## Aggiornare un’estensione

Per aggiornare un modulo o un’estensione:

1. Scarica il file aggiornato da Marketplace o da un altro sviluppatore di estensioni. Prendi nota del nome e della versione del modulo.

1. Esporta il contenuto nella directory principale dell’applicazione.

1. Se esiste un pacchetto Compositore per il modulo, esegui una delle seguenti operazioni.

   Nome aggiornamento per modulo:

   ```bash
   composer update vendor/module-name
   ```

   Aggiornamento per versione:

   ```bash
   composer require vendor/module-name ^x.x.x
   ```

1. Esegui i seguenti comandi per aggiornare, distribuire e pulire la cache.

   ```bash
   bin/magento setup:upgrade --keep-generated
   ```

   ```bash
   bin/magento setup:static-content:deploy
   ```

   ```bash
   bin/magento cache:clean
   ```
