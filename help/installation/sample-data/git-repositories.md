---
title: Archiviazione Git dati di esempio clone
description: Segui questi passaggi per installare Adobe Commerce e Magento Open Source dati di esempio clonando archivi Git.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 0%

---


# Archiviazione Git dati di esempio clone

Questo argomento illustra come clonare e aggiungere dati di esempio se hai clonato l’archivio GitHub di Magento Open Source. Questo metodo è destinato solo agli sviluppatori contributori (ovvero, agli sviluppatori che pianificano di contribuire alla base di codice del Magento Open Source).

Se non sei uno sviluppatore contributore, scegli una delle altre opzioni visualizzate nel sommario sul lato sinistro della pagina.

Gli sviluppatori collaboratori possono utilizzare questo metodo per installare i dati di esempio *only* se:

* Utilizza il Magento Open Source
* You [clonato l’archivio GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

>[!WARNING]
>
>Puoi utilizzare dati di esempio con `develop` ramo (più corrente) o un ramo rilasciato (ad esempio `2.4` (più stabile). È consigliabile utilizzare un ramo rilasciato perché è più stabile. Se stai contribuendo al codice dell’archivio e hai bisogno del codice più recente, utilizza `develop` ramo. Indipendentemente dal ramo scelto, è necessario [clone](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) il ramo corrispondente dell’archivio GitHub di Magento Open Source. Ad esempio, dati di esempio per `develop` può essere utilizzato *only* con il Magento Open Source `develop` ramo.

## Clona l’archivio dati di esempio

Questa sezione illustra come installare i dati di esempio clonando l’archivio dati di esempio. Puoi clonare l’archivio dati di esempio in uno dei seguenti modi:

* Clona con [Protocollo SSH](#clone-with-ssh)
* Clona con [Protocollo HTTPS](#clone-with-https)

### Clona con SSH

Per clonare l’archivio GitHub dei dati di esempio utilizzando il protocollo SSH:

1. In un browser web, passa alla pagina [archivio dati di esempio](https://github.com/magento/magento2-sample-data).
1. Accanto al nome del ramo, fai clic su **SSH** dall&#39;elenco.
1. Fai clic su **Copia negli Appunti**

   Nella figura seguente viene illustrato un esempio.

   ![Clonare l’archivio GitHub utilizzando SSH](../../assets/installation/install_mage2_clone-ssh.png)

1. Passa alla directory docroot del server web.

   Tipicamente, per Ubuntu, è `/var/www` e per CentOS è `/var/www/html`.

1. Invio `git clone` e incolla il valore ottenuto in precedenza.

   Di seguito è riportato un esempio:

   ```bash
   git clone git@github.com:magento/magento2-sample-data.git
   ```

1. Attendi che l&#39;archivio si cloni sul server.

   >[!NOTE]
   >
   >Se viene visualizzato il seguente errore, assicurati di [ha condiviso la tua chiave SSH](https://docs.github.com/articles/generating-ssh-keys/) con GitHub:<br>

   ```terminal
   Cloning into 'magento2'...
   Permission denied (publickey).
   fatal: The remote end hung up unexpectedly
   ```

1. Assicurati di estrarre il ramo dell’archivio dati di esempio che corrisponde al ramo utilizzato dal principale `magento2` archivio.

   Ad esempio:

   Se hai utilizzato la `2.4-develop` ramo dell’archivio GitHub di Magento Open Source, il ramo Dati di esempio deve essere `2.4-develop`.

   Se hai utilizzato la `2.4.3` ramo dell’archivio GitHub di Magento Open Source, il ramo Dati di esempio deve essere `2.4.3`.

   Per estrarre il ramo corretto, esegui il seguente comando dalla directory principale dell’archivio dati di esempio (supponendo che sia necessario `2.4.3` filiale):

   ```bash
   git checkout 2.4.3
   ```

1. Cambia in `<app_root>`.
1. Immetti il seguente comando per creare collegamenti simbolici tra i file clonati in modo che i dati di esempio funzionino correttamente:

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

1. Attendere il completamento del comando.

1. Vedi [Impostare le autorizzazioni e la proprietà del file system](#set-file-system-ownership-and-permissions).

1. Esegui il comando seguente:

   ```bash
   bin/magento setup:upgrade
   ```

### Clona con HTTPS

Per clonare l’archivio GitHub dei dati di esempio utilizzando il protocollo HTTPS:

1. In un browser web, passa alla pagina [archivio dati di esempio](https://github.com/magento/magento2-sample-data).
1. Sul lato destro della pagina, sotto il **URL clone** campo, fai clic su **HTTPS**.
1. Fai clic su **Copia negli Appunti**.

   Nella figura seguente viene illustrato un esempio.

   ![Clona l’archivio GitHub utilizzando HTTPS](../../assets/installation/install_mage2_clone-https.png)

1. Passa alla directory docroot del server web.

   Tipicamente, per Ubuntu, è `/var/www` e per CentOS è `/var/www/html`.

1. Invio `git clone` e incolla il valore ottenuto in precedenza.

   Di seguito è riportato un esempio:

   ```bash
   git clone https://github.com/magento/magento2-sample-data.git
   ```

1. Attendi che l&#39;archivio si cloni sul server.
1. Assicurati di estrarre il ramo dell’archivio dati di esempio che corrisponde al ramo utilizzato dal principale `magento2` archivio.

   Ad esempio:

   Se hai utilizzato la `2.4-develop` ramo dell’archivio GitHub di Magento Open Source, il ramo Dati di esempio deve essere `2.4-develop`.

   Se hai utilizzato la `2.4.3` ramo dell’archivio GitHub di Magento Open Source, il ramo Dati di esempio deve essere `2.4.3`.

   Per estrarre il ramo corretto, esegui il seguente comando dalla directory principale dell’archivio dati di esempio (supponendo che sia necessario `2.4.3` filiale):

   ```bash
   git checkout 2.4.3
   ```

1. Cambia in `<magento_root>`.
1. Immetti il seguente comando per creare collegamenti simbolici tra i file clonati in modo che i dati di esempio funzionino correttamente:

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

   Ad esempio:

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="/var/www/magento2"
   ```

1. Attendere il completamento del comando.
1. Vedi la sezione successiva.

>[!WARNING]
>
>Se stai installando dati di esempio *dopo* installazione di Adobe Commerce o Magento Open Source, è inoltre necessario eseguire il comando seguente per aggiornare il database e lo schema:
>
>
```bash
><magento_root>/bin/magento setup:upgrade
>```

## Imposta proprietà e autorizzazioni del file system

Perché `php build-sample-data.php` lo script crea collegamenti simbolici tra l’archivio dati di esempio e l’archivio dati di Magento Open Source; è necessario impostare le autorizzazioni e la proprietà del file system nell’archivio dati di esempio. In caso contrario, si verificano degli errori durante l’accesso alla vetrina.

Per impostare le autorizzazioni e la proprietà del file system nell&#39;archivio dati di esempio:

1. Passa alla directory clone dei dati di esempio.
1. Imposta proprietà:

   ```bash
   chown -R :<your web server group name> .
   ```

   Esempi tipici:

   * CentOS: `chown -R :apache .`

   * Ubuntu: `chown -R :www-data .`

1. Impostare le autorizzazioni:

   ```bash
   find . -type d -exec chmod g+ws {} +
   ```

1. Cancella file statici:

   ```bash
   cd <your Magento Open Source install dir>
   ```

   ```bash
   rm -rf var/cache/* var/page_cache/* generated/*
   ```

## Completare l’installazione dei dati di esempio

{{$include /help/_includes/sample-data-complete.md}}
