---
title: Gestire le estensioni di terze parti
description: Segui questi passaggi per installare, abilitare, aggiornare e disinstallare le estensioni Adobe Commerce.
exl-id: b564662a-2e5f-4fa9-bae1-ca7498478fa9
source-git-commit: f057cf082eeab1e34957e284817c6b93517de21b
workflow-type: tm+mt
source-wordcount: '802'
ht-degree: 0%

---


# Gestire le estensioni di terze parti

Il codice che estende o personalizza il comportamento di Adobe Commerce è chiamato estensione. Facoltativamente, è possibile creare un pacchetto e distribuire estensioni sulla [Commerce Marketplace](https://commercemarketplace.adobe.com/) o su un altro sistema di distribuzione delle estensioni.

Le estensioni includono:

- Moduli (estendere le funzionalità di Adobe Commerce)
- Temi (cambia l’aspetto della vetrina e dell’amministratore)
- Pacchetti di lingua (localizza la vetrina e Amministratore)

Questo argomento spiega come utilizzare l&#39;interfaccia della riga di comando per gestire le estensioni di terze parti acquistate da Commerce Marketplace per _progetti locali_. Per i progetti di infrastruttura cloud, consulta [Gestione estensioni](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/configure-store/extensions).

È possibile utilizzare la stessa procedura per installare l&#39;estensione _any_; tutto ciò che serve è il nome e la versione del Compositore dell&#39;estensione. Per trovarlo, aprire il file `composer.json` dell&#39;estensione e prendere nota dei valori per `"name"` e `"version"`.

## Installa

Prima dell&#39;installazione, è possibile:

1. Eseguire il backup del database.
1. Abilita modalità di manutenzione:

   ```bash
   bin/magento maintenance:enable
   ```

Per installare un&#39;estensione, è necessario:

1. Ottieni un’estensione da Commerce Marketplace o da un altro sviluppatore di estensioni.
1. Se si installa un&#39;estensione dalla Commerce Marketplace, verificare che l&#39;archivio `repo.magento.com` esista nel file `composer.json`:

   ```bash
   "repositories": [
       {
           "type": "composer",
           "url": "https://repo.magento.com/"
       }
   ]
   ```

1. Ottieni il nome e la versione del Compositore dell’estensione.
1. Aggiorna il file `composer.json` nel progetto con il nome e la versione dell&#39;estensione.
1. Verifica che l’estensione sia installata correttamente.
1. Abilita e configura l&#39;estensione.

### Ottieni informazioni sull’estensione

Se conosci già il nome e la versione del Compositore dell&#39;estensione, salta questo passaggio e continua con [Aggiorna il file `composer.json`](#update-composer-dependencies).

Per ottenere il nome e la versione del Compositore dell&#39;estensione dalla Commerce Marketplace:

1. Accedi a [Commerce Marketplace](https://commercemarketplace.adobe.com/) con il nome utente e la password utilizzati per acquistare l&#39;estensione.

1. Nell&#39;angolo superiore destro fare clic su **Nome** > **Profilo**.

   ![Accedi al tuo account Marketplace](../../assets/installation/marketplace-my-profile.png)

1. Fai clic su **I miei acquisti**.

   ![Cronologia acquisti Marketplace](../../assets/installation//marketplace-my-purchases.png)

1. Trova l’estensione da installare e annota il nome e la versione del componente.

   ![I dettagli tecnici mostrano il nome del Compositore dell&#39;estensione](../../assets/installation/marketplace-extension-technical-details.png)

>[!TIP]
>
>In alternativa, è possibile trovare il nome del Compositore e la versione dell&#39;estensione _any_ (acquistata su Commerce Marketplace o altrove) nel file `composer.json` dell&#39;estensione.

### Aggiorna dipendenze compositore

Aggiungere il nome e la versione dell&#39;estensione al file `composer.json`:

1. Passa alla directory del progetto e aggiorna il file `composer.json`.

   ```bash
   composer require <component-name>:<version>
   ```

   Ad esempio:

   ```bash
   composer require j2t/module-payplug:2.0.2
   ```

1. Immetti le [chiavi di autenticazione](../prerequisites/authentication-keys.md). La chiave pubblica è il nome utente; la chiave privata è la password.

1. Attendi che Composer completi l’aggiornamento delle dipendenze del progetto e assicurati che non siano presenti errori:

   ```
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

```
Module is disabled
```

Il nome dell&#39;estensione è nel formato `<VendorName>_<ComponentName>`, che è diverso dal nome del Compositore. Utilizza questo formato per abilitare l&#39;estensione. Se non sei sicuro del nome dell’estensione, esegui:

```bash
bin/magento module:status
```

E cerca l’estensione in &quot;Elenco dei moduli disabilitati&quot;.

### Abilita

Alcune estensioni non funzionano correttamente a meno che non si cancellino prima i file di visualizzazione statica generati. Utilizza l&#39;opzione `--clear-static-content` per cancellare i file di visualizzazione statica quando abiliti un&#39;estensione.

1. Abilita l’estensione e cancella i file della vista statica:

   ```bash
   bin/magento module:enable J2t_Payplug --clear-static-content
   ```

   Dovresti visualizzare il seguente output:

   ```
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

   ```
   Module is enabled
   ```

1. Pulisci la cache:

   ```bash
   bin/magento cache:clean
   ```

1. Configura l&#39;estensione in Admin secondo necessità.

>[!TIP]
>
>Se si verificano errori durante il caricamento della vetrina in un browser, utilizzare il comando seguente per cancellare la cache: `bin/magento cache:flush`.

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
>Esegui i passaggi per la disinstallazione in un ambiente non di produzione _first_ ed esegui un test completo prima di implementare nell&#39;ambiente di produzione.

Le istruzioni seguenti forniscono informazioni generali sulla disinstallazione di estensioni di terze parti:

1. Rimuovi l’estensione dall’archivio dei progetti Adobe Commerce.

   - Per le estensioni basate su Compositore, rimuovere l&#39;estensione dal file Adobe Commerce `composer.json`.

     ```bash
     composer remove <component-name>
     ```

   - Per le estensioni non basate su Compositore, rimuovi i file fisici dall’archivio dei progetti Adobe Commerce.

     ```bash
     rm -rf app/code/<vendor-name>/<component-name>
     ```

1. Se il file `config.php` è incluso nel controllo del codice sorgente nell&#39;archivio dei progetti Adobe Commerce, rimuovere l&#39;estensione dal file `config.php`.

1. Eseguire il test del database locale per verificare che le istruzioni fornite dal fornitore funzionino come previsto.

1. Verifica che l’estensione sia disabilitata correttamente e che il sito web funzioni come previsto nell’ambiente di staging.

1. Implementa le modifiche nell’ambiente di produzione.
