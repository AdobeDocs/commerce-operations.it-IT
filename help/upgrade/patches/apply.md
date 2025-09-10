---
title: Applicare le patch
description: Scopri i metodi per applicare patch a un progetto Adobe Commerce.
exl-id: 1d5d81ad-0115-4575-adfd-dde7c2826d85
source-git-commit: c8a20ad1b0b57724f389cfa5c63f6ae542758c2b
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# Applicare le patch

È possibile applicare le patch utilizzando uno dei seguenti metodi:

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=it){target="_blank"}
- [Riga di comando](../patches/apply.md#command-line)
- [Compositore](../patches/apply.md#composer)


>[!TIP]
>
>Consulta [best practice](../../implementation-playbook/best-practices/maintenance/patching-at-scale.md) per informazioni sull&#39;applicazione centralizzata di patch per Adobe Commerce su scala aziendale.

## Compositore

{{custom-patches-disclaimer}}

Per applicare una patch personalizzata mediante Compositore:

1. Apri l’applicazione della riga di comando e passa alla directory del progetto.
1. Aggiungere il plug-in `cweagans/composer-patches` al file `composer.json`.

   ```bash
   composer require cweagans/composer-patches
   ```

1. Modificare il file `composer.json` e aggiungere la sezione seguente per specificare:
   - **Modulo:** *\&quot;magento/module-payment\&quot;*
   - **Titolo:** *\&quot;MAGETWO-56934: la pagina di pagamento si blocca quando si ordina con Authorize.net con carta di credito non valida\&quot;*
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

1. Applichi il cerotto. Utilizzare l&#39;opzione `-v` solo se si desidera visualizzare le informazioni di debug.

   ```bash
   composer -v install
   ```

1. Aggiornare il file `composer.lock`. Il file di blocco tiene traccia delle patch applicate a ciascun pacchetto Composer di un oggetto.

   ```bash
   composer update --lock
   ```

## Riga di comando

Per applicare le patch dalla riga di comando:

1. Caricare il file locale nella directory `<Magento_root>` sul server utilizzando FTP, SFTP, SSH o il normale metodo di trasporto.
1. Accedere al server come [utente amministratore](../../configuration/cli/config-cli.md#prerequisites) e verificare che il file si trovi nella directory corretta.
1. Nell’interfaccia della riga di comando, esegui i seguenti comandi in base all’estensione della patch:

   ```bash
   patch < patch_file_name.patch
   ```

   Il comando presuppone che il file di cui applicare la patch si trovi in relazione al file di patch.

   >[!NOTE]
   >
   >Se la riga di comando mostra: `File to patch:`, significa che non è possibile individuare il file desiderato, anche se il percorso sembra corretto. Nella casella visualizzata nel terminale della riga di comando, la prima riga mostra il file a cui applicare la patch. Copiare il percorso del file e incollarlo nel prompt `File to patch:`, quindi premere `Enter` per completare la patch.

1. Affinché le modifiche vengano applicate, aggiorna la cache nell&#39;amministratore in **Sistema** > Strumenti > **Gestione cache**.

   In alternativa, è possibile applicare localmente la patch con lo stesso comando, quindi eseguirne il commit e il push normalmente.
