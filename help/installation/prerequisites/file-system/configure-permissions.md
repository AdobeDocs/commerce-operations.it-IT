---
title: Configurare la proprietà e le autorizzazioni dei file
description: Per configurare le autorizzazioni del file system per le installazioni locali di Adobe Commerce, segui la procedura riportata di seguito.
exl-id: 2410ee4f-978c-4b71-b3f6-0c042f9f4dc4
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 0%

---

# Configurare la proprietà e le autorizzazioni dei file

Questo argomento illustra come impostare le autorizzazioni di lettura-scrittura per il gruppo di server Web prima di installare Adobe Commerce. Ciò è necessario affinché la riga di comando possa scrivere file nel file system.

La procedura utilizzata è diversa a seconda che si utilizzi [hosting condiviso](#set-permissions-for-one-user-on-shared-hosting) e si disponga di un utente oppure si utilizzi un [server privato](#set-ownership-and-permissions-for-two-users) e si disponga di due utenti.

## Impostare le autorizzazioni per un utente su hosting condiviso

In questa sezione viene illustrato come impostare le autorizzazioni di preinstallazione se si accede al server applicazioni come lo stesso utente che esegue anche il server Web. Questo tipo di configurazione è comune negli ambienti di hosting condivisi.

Per impostare le autorizzazioni prima di installare l&#39;applicazione:

1. Accedere al server applicazioni.
1. Utilizza un’applicazione di gestione file fornita dal provider di hosting condiviso per verificare che le autorizzazioni di scrittura siano impostate sulle seguenti directory:

   * `vendor` (installazione del compositore o dell&#39;archivio compresso)
   * `app/etc`
   * `pub/static`
   * `var`
   * `generated`
   * Qualsiasi altra risorsa statica

1. Se si dispone dell&#39;accesso alla riga di comando, immettere i seguenti comandi nell&#39;ordine indicato:

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

   Per immettere facoltativamente tutti i comandi su una riga, immettere quanto segue presupponendo che l&#39;applicazione sia installata in `/var/www/html/magento2`:

   ```bash
   cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod u+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod u+w {} + && chmod u+x bin/magento
   ```

1. Se non lo hai già fatto, ottieni l’applicazione in uno dei seguenti modi:

   * [Metapacchetto del compositore](../../composer.md)
   * [Clona l&#39;archivio (solo sviluppatori partecipanti)](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

1. Dopo aver impostato le autorizzazioni e la proprietà del file system, [installare l&#39;applicazione](../../advanced.md)

>[!NOTE]
>
>Per limitare ulteriormente le autorizzazioni dopo l&#39;installazione dell&#39;applicazione, è possibile [configurare una maschera](../../next-steps/set-umask.md).

## Impostare la proprietà e le autorizzazioni per due utenti

Questa sezione illustra come impostare la proprietà e le autorizzazioni per il proprio server o una configurazione di hosting privato. In questo tipo di installazione, in genere *non è possibile* accedere come utente del server Web o passare a tale utente. In genere si accede come un utente ed il server web viene eseguito come un altro utente.

Per impostare la proprietà e le autorizzazioni per un sistema a due utenti:

Completa le seguenti attività nell’ordine indicato:

* [Informazioni sul gruppo condiviso](#about-the-shared-group)
* [Creare il proprietario del file system e assegnare all&#39;utente una password sicura](#create-the-file-system-owner-and-give-the-user-a-strong-password)
* [Trova il gruppo dell’utente del server web](#find-the-web-server-user-group)
* [Inserisci il proprietario del file system nel gruppo di server web](#put-the-file-system-owner-in-the-web-server-group)
* [Ottieni il software](#get-the-software)
* [Imposta proprietà e autorizzazioni per il gruppo condiviso](#set-ownership-and-permissions-for-the-shared-group)

### Informazioni sul gruppo condiviso

Per consentire al server Web di scrivere file e directory nel file system ma anche di mantenere la proprietà *1* del proprietario del file system, entrambi gli utenti devono appartenere allo stesso gruppo. Ciò è necessario affinché entrambi gli utenti possano condividere l’accesso ai file (inclusi i file creati utilizzando l’Admin o altre utilità basate sul web).

Questa sezione illustra come creare un proprietario del file system e inserire tale utente nel gruppo del server web. Se lo si desidera, è possibile utilizzare un account utente esistente. Per motivi di sicurezza, è consigliabile che l&#39;utente disponga di una password sicura.

>[!NOTE]
>
>Passa a [Trova il gruppo di utenti del server Web](#find-the-web-server-user-group) se intendi utilizzare un account utente esistente.

### Creare il proprietario del file system e assegnare all&#39;utente una password sicura

Questa sezione illustra come creare il proprietario del file system. (il proprietario del file system è un altro termine per l&#39;*utente della riga di comando*.)

Per creare un utente su CentOS o Ubuntu, immettere il comando seguente come utente con privilegi `root`:

```bash
adduser <username>
```

Per assegnare all&#39;utente una password, immettere il comando seguente come utente con privilegi `root`:

```bash
passwd <username>
```

Seguire le istruzioni visualizzate per creare una password per l&#39;utente.

>[!WARNING]
>
>Se non si dispone dei privilegi di `root` sul server applicazioni, è possibile utilizzare un altro account utente locale. Assicurarsi che l&#39;utente disponga di una password sicura e continuare con [Inserire il proprietario del file system nel gruppo di server Web](#step-3-put-the-file-system-owner-in-the-web-servers-group).

Ad esempio, per creare un utente denominato `magento_user` e assegnare una password all&#39;utente, immettere:

```bash
sudo adduser magento_user
```

```bash
sudo passwd magento_user
```

>[!WARNING]
>
>Poiché lo scopo della creazione di questo utente è quello di fornire maggiore protezione, assicurarsi di creare una [password sicura](https://en.wikipedia.org/wiki/Password_strength).

### Trovare il gruppo di utenti del server web

Per trovare il gruppo dell&#39;utente del server Web:

* CentOS:

  ```bash
  grep -E -i '^user|^group' /etc/httpd/conf/httpd.conf
  ```

  o

  ```bash
  grep -Ei '^user|^group' /etc/httpd/conf/httpd.conf
  ```

In genere, l&#39;utente e il nome del gruppo sono entrambi `apache`.

* Ubuntu: `ps aux | grep apache` per trovare l&#39;utente Apache, quindi `groups <apache user>` per trovare il gruppo.

In genere, il nome utente e il nome del gruppo sono entrambi `www-data`.

### Inserisci il proprietario del file system nel gruppo di server web

Per inserire il proprietario del file system nel gruppo principale del server Web (supponendo il nome tipico del gruppo Apache per CentOS e Ubuntu), immettere il comando seguente come utente con privilegi `root`:

* CentOS: `usermod -a -G apache <username>`
* Ubuntu: `usermod -a -G www-data <username>`

>[!NOTE]
>
>Le opzioni `-a -G` sono importanti perché aggiungono `apache` o `www-data` come gruppo *secondario* all&#39;account utente, mantenendo il gruppo *primario* dell&#39;utente. L&#39;aggiunta di un gruppo secondario a un account utente consente a [limitare la proprietà e le autorizzazioni dei file](#set-ownership-and-permissions-for-two-users) per garantire che i membri di un gruppo condiviso abbiano accesso solo a determinati file.

Ad esempio, per aggiungere l&#39;utente `magento_user` al gruppo primario `apache` su CentOS:

```bash
sudo usermod -a -G apache magento_user
```

Per confermare che l&#39;utente è membro del gruppo di server Web, immettere il comando seguente:

```bash
groups magento_user
```

Il seguente esempio mostra i gruppi primario (`magento`) e secondario (`apache`) dell&#39;utente.

```bash
magento_user : magento_user apache
```

>[!NOTE]
>
>In genere, il nome utente e il nome del gruppo primario coincidono.

Per completare l&#39;operazione, riavviare il server Web:

* Ubuntu: `service apache2 restart`
* CentOS: `service httpd restart`

### Ottieni il software

Se non lo hai già fatto, ottieni il software in uno dei seguenti modi:

* [Metapacchetto del compositore](../../composer.md)
* [Clona l&#39;archivio (solo sviluppatori partecipanti)](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

### Imposta proprietà e autorizzazioni per il gruppo condiviso

Per impostare la proprietà e le autorizzazioni prima di installare l&#39;applicazione:

1. Accedere al server applicazioni come proprietario del file system o passare a tale proprietario.
1. Immettete i seguenti comandi nell&#39;ordine indicato:

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

Per immettere facoltativamente tutti i comandi su una riga, immettere quanto segue presupponendo che l&#39;applicazione sia installata in `/var/www/html/magento2` e che il nome del gruppo di server Web sia `apache`:

```bash
cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && chown -R :apache . && chmod u+x bin/magento
```

Nel caso in cui le autorizzazioni del file system non siano impostate correttamente e non possano essere modificate dal proprietario del file system, è possibile immettere il comando come utente con privilegi `root`:

```bash
cd /var/www/html/magento2 && sudo find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && sudo find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && sudo chown -R :apache . && sudo chmod u+x bin/magento
```

## Passa al proprietario del file system

Dopo aver eseguito le altre attività descritte in questo argomento, immettere uno dei seguenti comandi per passare all&#39;utente:

* Ubuntu: `su <username>`
* CentOS: `su - <username>`

Ad esempio:

```bash
su magento_user
```
