---
title: Applicare le patch
description: Scopri i metodi per applicare le patch a un progetto Adobe Commerce o Magento Open Source.
exl-id: 1d5d81ad-0115-4575-adfd-dde7c2826d85
source-git-commit: 454f586737292341b3e6dd9a57cc92b3472c4b31
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---

# Applicare le patch

È possibile applicare le patch utilizzando uno dei seguenti metodi:

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}
- [Riga di comando](../patches/apply.md#command-line)
- [Compositore](../patches/apply.md#composer)


>[!TIP]
>
>Consulta [best practice](../../implementation-playbook/best-practices/maintenance/patching-at-scale.md) per informazioni sull&#39;applicazione centralizzata di patch per Adobe Commerce su scala aziendale.

## Compositore

>[!IMPORTANT]
>
>Per applicare le patch di qualità ufficiali, utilizzare la [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}. Eseguire sempre test completi prima di distribuire qualsiasi patch personalizzata.

Per applicare una patch personalizzata mediante Compositore:

1. Apri l’applicazione della riga di comando e passa alla directory del progetto.
1. Aggiungi il `cweagans/composer-patches` plugin per `composer.json` file.

   ```bash
   composer require cweagans/composer-patches
   ```

1. Modifica il `composer.json` e aggiungi la seguente sezione per specificare:
   - **Modulo:** *\&quot;magento/module-payment\&quot;*
   - **Titolo:** *\&quot;MAGETWO-56934: La pagina di pagamento si blocca quando si ordina con Authorize.net con carta di credito non valida\&quot;*
   - **Percorso patch:** *\&quot;patches/composer/github-issue-6474.diff\&quot;*

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

1. Applichi il cerotto. Utilizza il `-v` solo se si desidera visualizzare le informazioni di debug.

   ```bash
   composer -v install
   ```

1. Aggiornare il `composer.lock` file. Il file di blocco tiene traccia delle patch applicate a ciascun pacchetto Composer di un oggetto.

   ```bash
   composer update --lock
   ```

## Riga di comando

Per applicare le patch dalla riga di comando:

1. Carica il file locale in `<Magento_root>` sul server utilizzando FTP, SFTP, SSH o il normale metodo di trasporto.
1. Accedi al server come [utente amministratore](../../configuration/cli/config-cli.md#prerequisites) e verificare che il file si trovi nella directory corretta.
1. Nell’interfaccia della riga di comando, esegui i seguenti comandi in base all’estensione della patch:

   ```bash
   patch < patch_file_name.patch
   ```

   Il comando presuppone che il file di cui applicare la patch si trovi in relazione al file di patch.

   >[!NOTE]
   >
   >Se la riga di comando mostra: `File to patch:`, significa che non è in grado di individuare il file desiderato, anche se il percorso sembra corretto. Nella casella visualizzata nel terminale della riga di comando, la prima riga mostra il file a cui applicare la patch. Copiare il percorso del file e incollarlo nella `File to patch:` richiedi e premi `Enter` e il cerotto deve essere completato.

1. Affinché le modifiche vengano applicate, aggiorna la cache in Admin in **Sistema** > Strumenti > **Gestione cache**.

   In alternativa, è possibile applicare localmente la patch con lo stesso comando, quindi eseguirne il commit e il push normalmente.
