---
title: Autorizzazioni di accesso ai file system
description: Scopri come configurare il proprietario o i proprietari del file system dell’applicazione Commerce per un sistema di sviluppo e produzione.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '895'
ht-degree: 0%

---


# Autorizzazioni di accesso ai file system

Questa sezione illustra come configurare il proprietario o i proprietari del file system Commerce per un sistema di sviluppo e produzione. Prima di continuare, esamina i concetti descritti in [Panoramica della proprietà e delle autorizzazioni del file system](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).

Questo argomento si concentra sullo sviluppo e sui sistemi di produzione Commerce. Se stai installando Commerce, consulta [Impostare la proprietà e le autorizzazioni pre-installazione](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-system-perms.html).

Nelle sezioni seguenti vengono illustrati i requisiti per uno o due proprietari di file system. Ciò significa:

- **Un utente**- Generalmente necessario sui provider di hosting condivisi, che ti consentono di accedere a un solo utente sul server Questo utente può accedere, trasferire file tramite FTP, e questo utente esegue anche il server web.

- **Due utenti**- Consigliamo due utenti se esegui il tuo server Commerce: uno per trasferire i file ed eseguire le utilità della riga di comando e un utente separato per il software del server web. Quando possibile, questo è preferibile perché è più sicuro.

   Invece, hai utenti separati:

   - Utente del server web, che esegue Admin e storefront.

   - A _utente della riga di comando_, che è un account utente locale che puoi utilizzare per accedere al server. Questo utente esegue i lavori Commerce cron e le utilità della riga di comando.

## Proprietà del file system di produzione per hosting condiviso (un utente)

Per utilizzare la configurazione proprietario unico, è necessario accedere al server Commerce come lo stesso utente che esegue il server web. Questo è tipico per l&#39;hosting condiviso.

Poiché un solo proprietario del file system è meno sicuro, ti consigliamo di distribuire Commerce in produzione su un server privato invece che su hosting condiviso, se possibile.

### Imposta un proprietario per la modalità predefinita o sviluppatore

In modalità predefinita o sviluppatore, l’utente deve scrivere le seguenti directory:

- `vendor`
- `app/etc`
- `pub/static`
- `var`
- Qualsiasi altra risorsa statica
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

Puoi impostare queste autorizzazioni utilizzando la riga di comando o un&#39;applicazione di gestione file fornita dal provider di hosting condiviso.

### Imposta un proprietario per la modalità di produzione

Quando sei pronto per distribuire il tuo sito in produzione, rimuovi l&#39;accesso in scrittura dai file nelle seguenti directory per una maggiore sicurezza:

- `vendor`
- `app/code`
- `app/etc`
- `pub/static`
- Qualsiasi altra risorsa statica
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

Per aggiornare i componenti, installare nuovi componenti o aggiornare il software Commerce, tutte le directory precedenti devono essere in lettura e scrittura.

#### Rendere i file di codice e le directory di sola lettura

Per rimuovere le autorizzazioni di scrittura a file e directory dal gruppo dell&#39;utente del server Web:

1. Accedi al tuo server Commerce.

1. Passa alla directory di installazione Commerce.

1. Passa alla modalità di produzione.

   ```bash
   bin/magento deploy:mode:set production
   ```

1. Rimuovi le autorizzazioni di scrittura per le seguenti directory.

   ```bash
   find app/code var/view_preprocessed vendor pub/static app/etc generated/code generated/metadata \( -type f -or -type d \) -exec chmod u-w {} + && chmod o-rwx app/etc/env.php
   ```

1. Eseguire lo strumento della riga di comando.

   ```bash
   chmod u+x bin/magento
   ```

#### Rendere scrivibili file di codice e directory

Per rendere scrivibili file e directory in modo da poter aggiornare i componenti e aggiornare il software Commerce:

1. Accedi al tuo server Commerce.
1. Passa alla directory di installazione Commerce.
1. Immetti i seguenti comandi:

   ```bash
   chmod -R u+w .
   ```

### Impostazione facoltativa `magento_umask`

Vedi [Facoltativamente impostare una maschera](https://devdocs.magento.com/guides/v2.4/install-gde/install/post-install-umask.html) in _Guida all’installazione_.

## Proprietà del file system di produzione per hosting privato (due utenti)

Se utilizzi il tuo server (inclusa la configurazione del server privato di un provider di hosting), ci sono due utenti:

- La **utente web server**, che esegue Admin e storefront.

   I sistemi Linux generalmente non forniscono una shell per questo utente; non è possibile accedere al server Commerce come utente del server web o passare a tale utente.

- La **utente della riga di comando**, a cui si accede al server Commerce come o si passa a .

   Commerce utilizza questo utente per eseguire i comandi CLI e cron.

   >[!INFO]
   >
   >L’utente della riga di comando viene indicato anche come _proprietario del file system_.

Poiché questi utenti richiedono l’accesso agli stessi file, ti consigliamo di creare un [gruppo condiviso](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-system-perms.html#mage-owner-about-group) a cui appartengono entrambi. Le seguenti procedure presuppongono che l’utente abbia già eseguito questa operazione.

Vedere una delle sezioni seguenti:

- Due proprietari di file system in modalità sviluppatore o predefinita
- Due proprietari di file system in modalità di produzione

### Imposta due proprietari per la modalità predefinita o sviluppatore

I file nelle seguenti directory devono essere scrivibili da entrambi gli utenti in modalità sviluppatore e predefinita:

- `var`
- `generated`
- `pub/static`
- `pub/media`
- `app/etc`

Imposta la [`setgid`](https://linuxg.net/how-to-set-the-setuid-and-setgid-bit-for-files-in-linux-and-unix/) bit sulle directory in modo che le autorizzazioni ereditino sempre dalla directory principale.

>[!INFO]
>
>`setgid` si applica solo alle directory, _not_ in file.

Inoltre, le directory devono essere scrivibili dal gruppo di server web. Poiché il contenuto potrebbe esistere in queste directory, aggiungi le autorizzazioni in modo ricorsivo.

#### Impostare le autorizzazioni e `setgid`

Per impostare `setgid` e autorizzazioni per la modalità sviluppatore:

1. Accedi al tuo server Commerce come proprietario del file system o passa a .
1. Immetti i seguenti comandi nell&#39;ordine mostrato:

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

Quando sei pronto per distribuire il tuo sito in produzione, rimuovi l&#39;accesso in scrittura dai file nelle seguenti directory per una maggiore sicurezza:

- `vendor`
- `app/code`
- `app/etc`
- `lib`
- `pub/static`
- Qualsiasi altra risorsa statica
- `generated/code`
- `generated/metadata`
- `var/view_preprocessed`

#### Rendere i file di codice e le directory di sola lettura

Per rimuovere le autorizzazioni scrivibili a file e directory dal gruppo dell&#39;utente del server web:

1. Accedi al tuo server Commerce.
1. Passa alla directory di installazione Commerce.
1. Come proprietario del file system, immettere il comando seguente per passare alla modalità di produzione:

   ```bash
   bin/magento deploy:mode:set production
   ```

1. Immetti il seguente comando come utente con `root` privilegi:

   ```bash
   find app/code lib pub/static app/etc generated/code generated/metadata var/view_preprocessed \( -type d -or -type f \) -exec chmod g-w {} + && chmod o-rwx app/etc/env.php
   ```

#### Rendere scrivibili file di codice e directory

Per rendere scrivibili file e directory in modo da poter aggiornare i componenti e aggiornare il software Commerce:

1. Accedi al tuo server Commerce.
1. Passa alla directory di installazione Commerce.
1. Immetti il seguente comando:

   ```bash
   find app/code lib var generated vendor pub/static pub/media app/etc \( -type d -or -type f \) -exec chmod g+w {} + && chmod o+rwx app/etc/env.php
   ```
