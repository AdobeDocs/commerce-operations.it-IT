---
title: Gestire le estensioni di terze parti
description: Segui questi passaggi per installare, abilitare, aggiornare e disinstallare le estensioni Adobe Commerce.
exl-id: b564662a-2e5f-4fa9-bae1-ca7498478fa9
source-git-commit: 6da0e70acc77d2171d6336ab632e6a9a8dd16c67
workflow-type: tm+mt
source-wordcount: '785'
ht-degree: 0%

---


# Gestire le estensioni di terze parti

Il codice che estende o personalizza il comportamento di Adobe Commerce è chiamato estensione. Facoltativamente, puoi creare un pacchetto e distribuire estensioni sul [Commerce Marketplace](https://commercemarketplace.adobe.com/) o un altro sistema di distribuzione delle estensioni.

Le estensioni includono:

- Moduli (estendere le funzionalità di Adobe Commerce)
- Temi (cambia l’aspetto della vetrina e dell’amministratore)
- Pacchetti di lingua (localizza la vetrina e Amministratore)

>[!TIP]
>
>Questo argomento spiega come utilizzare l’interfaccia della riga di comando per gestire le estensioni di terze parti acquistate da Commerci Marketplace. È possibile utilizzare la stessa procedura per installare _qualsiasi_ estensione; tutto ciò di cui hai bisogno è il nome e la versione del Compositore dell’estensione. Per trovarlo, apri il file dell’estensione `composer.json` e annota i valori per `"name"` e `"version"`.

## Installa

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

### Ottieni informazioni sull’estensione

Se conosci già il nome e la versione del Compositore dell&#39;estensione, salta questo passaggio e continua con [Aggiorna il tuo `composer.json` file](#update-composer-dependencies).

Per ottenere il nome e la versione del Compositore dell&#39;estensione dalla Commerce Marketplace:

1. Accedi a [Commerce Marketplace](https://commercemarketplace.adobe.com/) con il nome utente e la password utilizzati per acquistare l’estensione.

1. Nell’angolo superiore destro, fai clic su **Il tuo nome** > **Il mio profilo**.

   ![Accedi al tuo account Marketplace](../../assets/installation/marketplace-my-profile.png)

1. Clic **I miei acquisti**.

   ![Cronologia acquisti Marketplace](../../assets/installation//marketplace-my-purchases.png)

1. Trova l’estensione da installare e fai clic su **Dettagli tecnici**.

   ![I dettagli tecnici mostrano il nome del compositore dell’estensione](../../assets/installation/marketplace-extension-technical-details.png)

>[!TIP]
>
>In alternativa, puoi trovare il nome e la versione del Compositore di _qualsiasi_ (acquistata su Commerce Marketplace o altrove) nel file dell’estensione `composer.json` file.

### Aggiorna dipendenze compositore

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

### Verificare l&#39;installazione

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

### Abilita

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

## Aggiorna

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

## Disinstalla

Contatta il fornitore dell’estensione per istruzioni su come rimuovere un’estensione di terze parti. Le istruzioni devono contenere le seguenti informazioni:

- Ripristinare le modifiche alla tabella del database
- Ripristinare le modifiche ai dati del database
- Quali file rimuovere o ripristinare

>[!CAUTION]
>
>Eseguire i passaggi di disinstallazione in un ambiente non di produzione _primo_ ed esegui test approfonditi prima di implementare nell’ambiente di produzione.

Le istruzioni seguenti forniscono informazioni generali sulla disinstallazione di estensioni di terze parti:

1. Rimuovi l’estensione dall’archivio dei progetti Adobe Commerce.

   - Per le estensioni basate su Compositore, rimuovi l’estensione dall’Adobe Commerce `composer.json` file.

     ```bash
     composer remove <package-name>
     ```

   - Per le estensioni non basate su Compositore, rimuovi i file fisici dall’archivio dei progetti Adobe Commerce.

     ```bash
     rm -rf app/code/<vendor-name>/<module-name>
     ```

1. Se il `config.php` è incluso nel controllo del codice sorgente nell’archivio dei progetti Adobe Commerce, rimuovi l’estensione da `config.php` file.

1. Eseguire il test del database locale per verificare che le istruzioni fornite dal fornitore funzionino come previsto.

1. Verifica che l’estensione sia disabilitata correttamente e che il sito web funzioni come previsto nell’ambiente di staging.

1. Implementa le modifiche nell’ambiente di produzione.
