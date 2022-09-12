---
title: Configurazione del sistema di produzione
description: Scopri come configurare un sistema di produzione per l’applicazione Commerce.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---


# Configurazione del sistema di produzione

Potete avere un sistema di produzione. Deve essere vero quanto segue:

- Tutto il codice Commerce si trova nel controllo del codice sorgente nello stesso archivio dei sistemi di sviluppo e creazione
- Assicurati che tutti i seguenti elementi siano _incluso_ nel controllo della sorgente:

   - `app/etc/config.php`
   - `generated` directory (e sottodirectory)
   - `pub/media` directory
   - `pub/media/wysiwyg` directory (e sottodirectory)
   - `pub/static` directory (e sottodirectory)

- Commerce 2.2 o successivo deve essere installato e impostato per [modalità di produzione](../bootstrap/application-modes.md#production-mode)
- Possiede la proprietà e le autorizzazioni del file system impostate come descritto in [Prerequisito per i sistemi di sviluppo, generazione e produzione](../deployment/prerequisites.md).

## Imposta una macchina di produzione

Per impostare una macchina di produzione:

1. Dopo aver installato Commerce o averlo estratto dal controllo del codice sorgente, accedi al server di produzione come o passa a [proprietario del file system](https://glossary.magento.com/magento-file-system-owner).
1. Crea `~/.ssh/.composer/auth.json` se non l&#39;hai già fatto.

   Crea la directory:

   ```bash
   mkdir -p ~/.ssh/.composer
   ```

   Crea `auth.json` in quella directory.

   `auth.json` deve contenere [chiavi di autenticazione](../../installation/prerequisites/authentication-keys.md).

   Segue un esempio:

   ```json
   {
      "http-basic": {
         "repo.magento.com": {
            "username": "<your public key>",
            "password": "<your private key>"
         }
      }
   }
   ```

1. Salva le modifiche in `auth.json`.
1. Copia `<Commerce root dir>/app/etc/env.php` dal sistema di sviluppo al sistema di produzione.
1. Apri `env.php` in un editor di testo e modificare i valori necessari (ad esempio, informazioni sulla connessione al database).
1. Esegui il [`magento config:set`](../cli/set-configuration-values.md) o [`magento config:set-sensitive`](../cli/set-configuration-values.md) per impostare i valori di qualsiasi valore di configurazione specifico del sistema o sensibile, rispettivamente.

   Nella sezione seguente viene illustrato un esempio.

## Imposta i valori di configurazione sul sistema di produzione

Questa sezione illustra come impostare valori sensibili sul sistema di produzione utilizzando `magento config:sensitive:set` comando.

Per impostare valori sensibili:

1. Trova un valore da impostare utilizzando la variabile [riferimento a valori sensibili](../reference/config-reference-sens.md).
1. Tieni presente il percorso di configurazione per l’impostazione.
1. Accedere al sistema di produzione come proprietario del file system o passare a tale proprietario.
1. Passare alla directory di installazione Commerce.
1. Immetti il seguente comando:

   ```bash
   bin/magento config:sensitive:set {configuration path} {value}
   ```

   Ad esempio, per impostare il valore della chiave API di YouTube su `1234`, inserisci

   ```bash
   bin/magento config:sensitive:set catalog/product_video/youtube_api_key 1234
   ```

   Puoi anche impostare uno o più valori in modo interattivo come segue:

   ```bash
   bin/magento config:sensitive:set -i
   ```

   Quando richiesto, immetti un valore per ogni impostazione sensibile oppure premi Invio per saltare un valore e passare a quello successivo.

1. Per verificare che il valore sia stato impostato, accedi all’amministratore.
1. Individua l’impostazione in Amministratore.

   Ad esempio, l’impostazione della chiave API di YouTube si trova in **Negozi** > Impostazioni > **Configurazione** > **Catalogo** > **Catalogo** > **Video del prodotto**.

   L’impostazione viene visualizzata in Admin e non può essere modificata. Nella figura seguente viene illustrato un esempio.

   ![Impostazione sensibile in Amministratore](../../assets/configuration/sensitive-set.png)
