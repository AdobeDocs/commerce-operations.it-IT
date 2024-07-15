---
title: Autorizzazioni di accesso ai file system
description: Come impostare il proprietario o i proprietari del file system dell'applicazione Commerce per un sistema di sviluppo e produzione.
feature: Configuration, Roles/Permissions
exl-id: 95b27db9-5247-4f58-a9af-1590897d73db
source-git-commit: dcc283b901917e3681863370516771763ae87462
workflow-type: tm+mt
source-wordcount: '864'
ht-degree: 0%

---

# Autorizzazioni di accesso ai file system

Questa sezione illustra come impostare il proprietario o i proprietari del file system Commerce per un sistema di sviluppo e produzione. Prima di continuare, esaminare i concetti descritti in [Panoramica sulla proprietà e sulle autorizzazioni del file system](../../installation/prerequisites/file-system/overview.md).

Questo argomento si concentra sui sistemi di sviluppo e produzione Commerce. Se stai installando Commerce, vedi [Impostare le autorizzazioni e la proprietà per la preinstallazione](../../installation/prerequisites/file-system/configure-permissions.md).

Nelle sezioni seguenti vengono descritti i requisiti per uno o due proprietari del file system. Ciò significa che:

- **Un utente**: in genere necessario nei provider di hosting condivisi, che consentono di accedere a un solo utente sul server. L&#39;utente può accedere, trasferire file tramite FTP e questo utente esegue anche il server Web.

- **Due utenti**. Si consiglia di eseguire due utenti se si esegue il proprio server Commerce: uno per trasferire file ed eseguire utilità della riga di comando e un altro per il software del server Web. Quando possibile, è preferibile perché è più sicuro.

  Sono invece disponibili utenti separati:

   - L’utente del server web, che esegue l’amministrazione e la vetrina.

   - Un _utente della riga di comando_, che è un account utente locale che è possibile utilizzare per accedere al server. Questo utente esegue i processi cron di Commerce e le utilità della riga di comando.

## Proprietà del file system di produzione per l&#39;hosting condiviso (un utente)

Per utilizzare la configurazione con un solo proprietario, è necessario accedere al server Commerce come lo stesso utente che esegue il server Web. Questo è tipico per l&#39;hosting condiviso.

Poiché avere un proprietario del file system è meno sicuro, ti consigliamo di distribuire Commerce in produzione su un server privato invece che su un hosting condiviso, se possibile.

### Imposta un proprietario per la modalità predefinita o sviluppatore

In modalità predefinita o sviluppatore, le seguenti directory devono essere scrivibili dall’utente:

- `vendor`
- `app/etc`
- `pub/static`
- `var`
- Qualsiasi altra risorsa statica
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

Puoi impostare queste autorizzazioni utilizzando la riga di comando o un’applicazione di gestione file fornita dal provider di hosting condiviso.

### Imposta un proprietario per la modalità di produzione

Quando si è pronti per distribuire il sito in produzione, è necessario rimuovere l&#39;accesso in scrittura dai file nelle seguenti directory per una maggiore sicurezza:

- `vendor`
- `app/code`
- `app/etc`
- `pub/static`
- Qualsiasi altra risorsa statica
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

Per aggiornare i componenti, installare nuovi componenti o aggiornare il software Commerce, è necessario che tutte le directory precedenti siano di lettura/scrittura.

#### Rendi i file di codice e le directory di sola lettura

Per rimuovere le autorizzazioni di scrittura per file e directory dal gruppo dell&#39;utente del server Web:

1. Accedi al server Commerce.

1. Passare alla directory di installazione di Commerce.

1. Passa alla modalità di produzione.

   ```bash
   bin/magento deploy:mode:set production
   ```

1. Rimuovi le autorizzazioni di scrittura per le directory seguenti.

   ```bash
   find app/code var/view_preprocessed vendor pub/static app/etc generated/code generated/metadata \( -type f -or -type d \) -exec chmod u-w {} + && chmod o-rwx app/etc/env.php
   ```

1. Rende eseguibile lo strumento della riga di comando.

   ```bash
   chmod u+x bin/magento
   ```

#### Rendi i file di codice e le directory scrivibili

Per rendere i file e le directory scrivibili in modo da poter aggiornare i componenti e il software Commerce:

1. Accedi al server Commerce.
1. Passare alla directory di installazione di Commerce.
1. Immettete i seguenti comandi:

   ```bash
   chmod -R u+w .
   ```

### Imposta facoltativamente `magento_umask`

Vedere [Facoltativamente impostare un umask](../../installation/next-steps/set-umask.md) nella _Guida all&#39;installazione_.

## Proprietà del file system di produzione per l&#39;hosting privato (due utenti)

Se utilizzi un server personalizzato (inclusa la configurazione del server privato di un provider di hosting), ci sono due utenti:

- L&#39;**utente del server Web**, che esegue Admin e storefront.

  I sistemi Linux in genere non forniscono una shell per questo utente; non è possibile accedere al server Commerce come utente del server web o passare ad esso.

- L&#39;**utente della riga di comando**, a cui si accede al server Commerce come o a cui si passa.

  Commerce utilizza questo utente per eseguire i comandi CLI e cron.

  >[!INFO]
  >
  >L&#39;utente della riga di comando è anche indicato come _proprietario del file system_.

Poiché questi utenti richiedono l&#39;accesso agli stessi file, è consigliabile creare un [gruppo condiviso](../../installation/prerequisites/file-system/configure-permissions.md#about-the-shared-group) al quale entrambi appartengono. Le procedure seguenti presuppongono che tu abbia già eseguito questa operazione.

Vedere una delle sezioni seguenti:

- Due proprietari del file system in modalità sviluppatore o predefinita
- Due proprietari di file system in modalità di produzione

### Imposta due proprietari per la modalità predefinita o sviluppatore

I file nelle directory seguenti devono essere scrivibili sia dagli utenti in modalità sviluppatore che da quelli in modalità predefinita:

- `var`
- `generated`
- `pub/static`
- `pub/media`
- `app/etc`

Impostare il bit [`setgid`](https://linuxg.net/how-to-set-the-setuid-and-setgid-bit-for-files-in-linux-and-unix/) sulle directory in modo che le autorizzazioni ereditino sempre dalla directory padre.

>[!INFO]
>
>`setgid` si applica solo alle directory, _non_ ai file.

Inoltre, le directory devono essere scrivibili dal gruppo del server web. Poiché in queste directory potrebbe esistere del contenuto, aggiungi le autorizzazioni in modo ricorsivo.

#### Imposta autorizzazioni e `setgid`

Per impostare `setgid` e le autorizzazioni per la modalità sviluppatore:

1. Accedi al server Commerce come proprietario del file system o passa a tale proprietario.
1. Immettete i seguenti comandi nell&#39;ordine indicato:

   ```bash
   cd <magento_root>
   ```

   ```bash
   find var generated pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

### Due proprietari di file system in modalità di produzione

Quando si è pronti per distribuire il sito in produzione, è necessario rimuovere l&#39;accesso in scrittura dai file nelle seguenti directory per una maggiore sicurezza:

- `vendor`
- `app/code`
- `app/etc`
- `lib`
- `pub/static`
- Qualsiasi altra risorsa statica
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

#### Rendi i file di codice e le directory di sola lettura

Per rimuovere le autorizzazioni scrivibili per file e directory dal gruppo dell&#39;utente del server Web:

1. Accedi al server Commerce.
1. Passare alla directory di installazione di Commerce.
1. Come proprietario del file system, immettere il seguente comando per passare alla modalità di produzione:

   ```bash
   bin/magento deploy:mode:set production
   ```

1. Immettere il comando seguente come utente con privilegi `root`:

   ```bash
   find app/code lib pub/static app/etc generated/code generated/metadata var/view_preprocessed \( -type d -or -type f \) -exec chmod g-w {} + && chmod o-rwx app/etc/env.php
   ```

#### Rendi i file di codice e le directory scrivibili

Per rendere i file e le directory scrivibili in modo da poter aggiornare i componenti e il software Commerce:

1. Accedi al server Commerce.
1. Passare alla directory di installazione di Commerce.
1. Immetti il comando seguente:

   ```bash
   find app/code lib var generated vendor pub/static pub/media app/etc \( -type d -or -type f \) -exec chmod g+w {} + && chmod o+rwx app/etc/env.php
   ```
