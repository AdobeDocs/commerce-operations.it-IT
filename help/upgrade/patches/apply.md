---
title: Applica patch
description: Scopri i metodi per applicare patch a un progetto Adobe Commerce o Magenti Open Source.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---


# Applica patch

È possibile applicare le patch utilizzando uno dei seguenti metodi:

- [Strumento Patch di qualità](https://devdocs.magento.com/quality-patches/tool.html)
- [Riga di comando](../patches/apply.md#command-line)
- [Compositore](../patches/apply.md#composer)

## Compositore

>[!IMPORTANT]
>
>Per applicare le patch di qualità ufficiali, utilizza il [Strumento Patch di qualità](https://devdocs.magento.com/quality-patches/tool.html). Esegui sempre test completi prima di distribuire qualsiasi patch personalizzata.

Per applicare una patch personalizzata utilizzando il Compositore:

1. Apri l’applicazione della riga di comando e passa alla directory del progetto.
1. Aggiungi il `cweagans/composer-patches` plug-in a `composer.json` file.

   ```bash
   composer require cweagans/composer-patches
   ```

1. Modifica le `composer.json` e aggiungi la sezione seguente per specificare:
   - **Modulo:** *\&quot;magento/module-payment\&quot;*
   - **Titolo:** *\&quot;MAGETWO-56934: La pagina di pagamento si blocca durante l&#39;ordine con Authorize.net con carta di credito non valida\&quot;*
   - **Percorso della patch:** *\&quot;patches/composer/github-issue-6474.diff\&quot;*

   Ad esempio:

   ```json
   "extra": {
       "composer-exit-on-patch-failure": true,
       "patches": {
           "magento/module-payment": {
               "MAGETWO-56934: Checkout page freezes when ordering with Authorize.net with invalid credit card": "patches/composer/github-issue-6474.diff"
           }
       }
   }
   ```

   Se una patch interessa più moduli, è necessario creare più file di patch destinati a più moduli.

1. Applicate la patch. Utilizza la `-v` solo se si desidera visualizzare le informazioni di debug.

   ```bash
   composer -v install
   ```

1. Aggiorna `composer.lock` file. Il file di blocco tiene traccia delle patch applicate a ciascun pacchetto Composer in un oggetto.

   ```bash
   composer update --lock
   ```

## Riga di comando

Per applicare le patch dalla riga di comando:

1. Carica il file locale nel `<Magento_root>` sul server utilizzando FTP, SFTP, SSH o il normale metodo di trasporto.
1. Accedi al server come [utente amministratore](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli.html#config-install-cli-first) e verifica che il file si trovi nella directory corretta.
1. Nell&#39;interfaccia della riga di comando, esegui i seguenti comandi in base all&#39;estensione della patch:

   ```bash
   patch < patch_file_name.patch
   ```

   Il comando presuppone che il file da sottoporre a patch si trovi in una posizione relativa al file della patch.

   >[!NOTE]
   >
   >Se la riga di comando mostra: `File to patch:`, significa che non è in grado di individuare il file desiderato, anche se il percorso sembra corretto. Nella casella visualizzata nel terminale della riga di comando, la prima riga mostra il file a cui applicare la patch. Copia il percorso del file e incollalo nel `File to patch:` premere `Enter` e la patch dovrebbe essere completata.

1. Affinché le modifiche si riflettano, aggiorna la cache nell’Admin in **Sistema** > Strumenti > **Gestione cache**.

   In alternativa, la patch può essere applicata localmente con lo stesso comando, quindi impegnata e spinta normalmente.
