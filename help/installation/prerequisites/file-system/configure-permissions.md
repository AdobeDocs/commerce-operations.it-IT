---
title: Configurare la proprietà e le autorizzazioni dei file
description: Segui questi passaggi per configurare le autorizzazioni del file system per le installazioni on-premise di Adobe Commerce e Magenti Open Source.
source-git-commit: 61638d373408d9a7c3c3a935eee61927acfac7a6
workflow-type: tm+mt
source-wordcount: '1005'
ht-degree: 0%

---


# Configurare la proprietà e le autorizzazioni dei file

Questo argomento illustra come impostare le autorizzazioni di lettura e scrittura per il gruppo di server web prima di installare Adobe Commerce o Magenti Open Source. Questo è necessario in modo che la riga di comando possa scrivere file al file system.

La procedura utilizzata è diversa, a seconda che si utilizzi o meno [hosting condiviso](#set-permissions-for-one-user-on-shared-hosting) e dispongono di un utente o se utilizzi un [server privato](#set-ownership-and-permissions-for-two-users) e hanno due utenti.

## Impostare le autorizzazioni per un utente in hosting condiviso

Questa sezione illustra come impostare le autorizzazioni di preinstallazione se si accede al server applicazioni come lo stesso utente che esegue anche il server web. Questo tipo di configurazione è comune negli ambienti di hosting condivisi.

Per impostare le autorizzazioni prima di installare l&#39;applicazione:

1. Accedi al server delle applicazioni.
1. Utilizza un&#39;applicazione di gestione file fornita dal provider di hosting condiviso per verificare che le autorizzazioni di scrittura siano impostate sulle seguenti directory:

   * `vendor` (Compositore o installazione di archivi compressi)
   * `app/etc`
   * `pub/static`
   * `var`
   * `generated`
   * Qualsiasi altra risorsa statica

1. Se si dispone dell&#39;accesso alla riga di comando, immettere i seguenti comandi nell&#39;ordine mostrato:

   ```bash
   cd <app_root>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod u+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod u+w {} +
   ```

   ```bash
   chmod u+x bin/magento
   ```

   Per immettere facoltativamente tutti i comandi su una riga, immettere quanto segue supponendo che l&#39;applicazione sia installata in `/var/www/html/magento2`:

   ```bash
   cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod u+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod u+w {} + && chmod u+x bin/magento
   ```

1. Se non lo hai già fatto, ottieni l&#39;applicazione in uno dei seguenti modi:

   * [Metapackage compositore](../../composer.md)
   * [Clona l’archivio (solo per sviluppatori contributori)](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

1. Dopo aver impostato la proprietà e le autorizzazioni del file system, [installare l&#39;applicazione](../../advanced.md)

>[!NOTE]
>
>Per limitare ulteriormente le autorizzazioni dopo l&#39;installazione dell&#39;applicazione, puoi [configurare una umask](../../next-steps/set-umask.md).

## Impostare proprietà e autorizzazioni per due utenti

Questa sezione illustra come impostare la proprietà e le autorizzazioni per il proprio server o una configurazione di hosting privata. In questo tipo di configurazione, tipicamente *impossibile* effettua l&#39;accesso come utente del server web o passa a . In genere si effettua l&#39;accesso come un utente e si esegue il server web come un altro utente.

Per impostare proprietà e autorizzazioni per un sistema a due utenti:

Completa le attività seguenti nell’ordine visualizzato:

* [Informazioni sul gruppo condiviso](#about-the-shared-group)
* [Creare il proprietario del file system e fornire all&#39;utente una password sicura](#create-the-file-system-owner-and-give-the-user-a-strong-password)
* [Trova il gruppo dell&#39;utente del server web](#find-the-web-server-user-group)
* [Inserire il proprietario del file system nel gruppo del server Web](#put-the-file-system-owner-in-the-web-server-group)
* [Ottenere il software](#get-the-software)
* [Imposta proprietà e autorizzazioni per il gruppo condiviso](#set-ownership-and-permissions-for-the-shared-group)

### Informazioni sul gruppo condiviso

Per consentire al server web di scrivere file e directory nel file system ma anche di mantenere *proprietà* dal proprietario del file system, entrambi gli utenti devono trovarsi nello stesso gruppo. È necessario in modo che entrambi gli utenti possano condividere l’accesso ai file (inclusi i file creati utilizzando l’amministratore o altre utilità basate su Web).

Questa sezione illustra come creare un proprietario di file system e inserire tale utente nel gruppo del server web. Puoi utilizzare un account utente esistente, se lo desideri; per motivi di sicurezza, consigliamo all’utente di utilizzare una password complessa.

>[!NOTE]
>
>Passa a [Trova il gruppo utenti del server web](#find-the-web-server-user-group) se prevedi di utilizzare un account utente esistente.

### Creare il proprietario del file system e fornire all&#39;utente una password sicura

Questa sezione illustra come creare il proprietario del file system. (il proprietario del file system è un altro termine per *utente della riga di comando*.)

Per creare un utente su CentOS o Ubuntu, immetti il seguente comando come utente con `root` privilegi:

```bash
adduser <username>
```

Per assegnare all&#39;utente una password, immetti il seguente comando come utente con `root` privilegi:

```bash
passwd <username>
```

Segui le istruzioni visualizzate sullo schermo per creare una password per l’utente.

>[!WARNING]
>
>Se non hai `root` privilegi sul server dell&#39;applicazione, è possibile utilizzare un altro account utente locale. Assicurati che l&#39;utente disponga di una password complessa e continua con [Inserire il proprietario del file system nel gruppo del server Web](#step-3-put-the-file-system-owner-in-the-web-servers-group).

Ad esempio, per creare un utente denominato `magento_user` e assegna all&#39;utente una password, immetti:

```bash
sudo adduser magento_user
```

```bash
sudo passwd magento_user
```

>[!WARNING]
>
>Poiché lo scopo della creazione di questo utente è quello di fornire ulteriore sicurezza, assicurati di creare un [password sicura](https://en.wikipedia.org/wiki/Password_strength).

### Trova il gruppo utenti del server web

Per trovare il gruppo dell&#39;utente del server web:

* CentOS:

   ```bash
   grep -E -i '^user|^group' /etc/httpd/conf/httpd.conf
   ```

   o

   ```bash
   grep -Ei '^user|^group' /etc/httpd/conf/httpd.conf
   ```

In genere, il nome utente e il nome del gruppo sono entrambi `apache`.

* Ubuntu: `ps aux | grep apache` per trovare l&#39;utente Apache, quindi `groups <apache user>` per trovare il gruppo.

In genere, il nome utente e il nome del gruppo sono entrambi `www-data`.

### Inserire il proprietario del file system nel gruppo del server Web

Per inserire il proprietario del file system nel gruppo principale del server Web (partendo dal nome del gruppo Apache tipico per CentOS e Ubuntu), immettere il comando seguente come utente con `root` privilegi:

* CentOS: `usermod -a -G apache <username>`
* Ubuntu: `usermod -a -G www-data <username>`

>[!NOTE]
>
>La `-a -G` le opzioni sono importanti perché aggiungono `apache` o `www-data` come *secondario* all&#39;account utente, che ne conserva le proprietà *primario* gruppo. L&#39;aggiunta di un gruppo secondario a un account utente aiuta [limitare la proprietà e le autorizzazioni dei file](#set-ownership-and-permissions-for-two-users) per garantire che i membri di un gruppo condiviso abbiano accesso solo a determinati file.

Ad esempio, per aggiungere l’utente `magento_user` al `apache` gruppo principale su CentOS:

```bash
sudo usermod -a -G apache magento_user
```

Per confermare che l&#39;utente è membro del gruppo di server Web, immettere il comando seguente:

```bash
groups magento_user
```

Il risultato di esempio seguente mostra il principale dell’utente (`magento`) e secondaria (`apache`).

```bash
magento_user : magento_user apache
```

>[!NOTE]
>
>In genere, il nome utente e il nome del gruppo primario sono gli stessi.

Per completare l&#39;attività, riavviare il server Web:

* Ubuntu: `service apache2 restart`
* CentOS: `service httpd restart`

### Ottenere il software

Se non lo hai già fatto, ottieni il software in uno dei seguenti modi:

* [Metapackage compositore](../../composer.md)
* [Clona l’archivio (solo per sviluppatori contributori)](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

### Imposta proprietà e autorizzazioni per il gruppo condiviso

Per impostare proprietà e autorizzazioni prima di installare l&#39;applicazione:

1. Accedi al server delle applicazioni come proprietario del file system o passa a tale proprietario.
1. Immetti i seguenti comandi nell&#39;ordine mostrato:

   ```bash
   cd <app_root>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :<web server group> .
   ```

   ```bash
   chmod u+x bin/magento
   ```

Per immettere facoltativamente tutti i comandi su una riga, immettere quanto segue supponendo che l&#39;applicazione sia installata in `/var/www/html/magento2` e il nome del gruppo del server web è `apache`:

```bash
cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && chown -R :apache . && chmod u+x bin/magento
```

Nell&#39;evento le autorizzazioni del file system sono impostate in modo improprio e non possono essere modificate dal proprietario del file system, è possibile immettere il comando come utente con `root` privilegi:

```bash
cd /var/www/html/magento2 && sudo find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && sudo find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && sudo chown -R :apache . && sudo chmod u+x bin/magento
```

## Passa al proprietario del file system

Dopo aver eseguito le altre attività in questo argomento, immettere uno dei seguenti comandi per passare a tale utente:

* Ubuntu: `su <username>`
* CentOS: `su - <username>`

Ad esempio:

```bash
su magento_user
```
