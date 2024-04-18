---
title: Clona i dati di esempio Git archivi
description: Per installare i dati di esempio di Adobe Commerce clonando gli archivi Git, segui la procedura riportata di seguito.
exl-id: 748eee30-2821-457d-9c1c-62ede8bc0510
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 0%

---

# Clona i dati di esempio Git archivi

Questo argomento illustra come clonare e aggiungere dati di esempio se hai clonato l’archivio GitHub di Magento Open Source. Questo metodo è destinato solo agli sviluppatori che contribuiscono (ovvero, gli sviluppatori che pianificano di contribuire alla base di codice del Magento Open Source).

Se non sei uno sviluppatore, scegli una delle altre opzioni visualizzate nel sommario sul lato sinistro della pagina.

Gli sviluppatori partecipanti possono utilizzare questo metodo per installare dati di esempio *solo* se si verifica quanto segue:

* Usa il Magento Open Source
* Tu [clonato l’archivio GitHub](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

>[!WARNING]
>
>È possibile utilizzare dati di esempio con `develop` ramo (più corrente) o un ramo rilasciato (come `2.4` (più stabile). È consigliabile utilizzare un ramo rilasciato perché è più stabile. Se stai contribuendo al codice dell’archivio e hai bisogno del codice più recente, utilizza `develop` filiale. Indipendentemente dal ramo scelto, è necessario [clone](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) il ramo corrispondente dell’archivio GitHub di Magento Open Source. Ad esempio, dati di esempio per `develop` ramo utilizzabile *solo* con il Magento Open Source `develop` filiale.

## Clonare l’archivio dati di esempio

Questa sezione illustra come installare dati di esempio clonando l’archivio dati di esempio. Puoi clonare l’archivio dati di esempio in uno dei seguenti modi:

* Clona con [Protocollo SSH](#clone-with-ssh)
* Clona con [Protocollo HTTPS](#clone-with-https)

### Clona con SSH

Per clonare i dati di esempio dell’archivio GitHub utilizzando il protocollo SSH:

1. In un browser web, vai al [archivio dati di esempio](https://github.com/magento/magento2-sample-data).
1. Accanto al nome del ramo, fai clic su **SSH** dall&#39;elenco.
1. Clic **Copia negli Appunti**

   Nella figura seguente viene illustrato un esempio.

   ![Clonare l’archivio GitHub utilizzando SSH](../../assets/installation/install_mage2_clone-ssh.png)

1. Passare alla directory principale dei documenti del server Web.

   In genere, per Ubuntu, è `/var/www` e per CentOS è `/var/www/html`.

1. Invio `git clone` e incolla il valore ottenuto in precedenza.

   Di seguito è riportato un esempio:

   ```bash
   git clone git@github.com:magento/magento2-sample-data.git
   ```

1. Attendi che l’archivio venga clonato sul server.

   >[!NOTE]
   >
   >Se viene visualizzato il seguente errore, assicurati di [ha condiviso la tua chiave SSH](https://docs.github.com/articles/generating-ssh-keys/) con GitHub:<br>

   ```terminal
   Cloning into 'magento2'...
   Permission denied (publickey).
   fatal: The remote end hung up unexpectedly
   ```

1. Accertati di estrarre il ramo dell’archivio dati di esempio che corrisponde al ramo utilizzato dall’archivio principale `magento2` archivio.

   Ad esempio:

   Se è stato utilizzato il `2.4-develop` dell’archivio GitHub di Magento Open Source, il ramo Dati di esempio deve essere `2.4-develop`.

   Per estrarre il ramo corretto, eseguire il comando seguente dalla directory principale dell&#39;archivio dati di esempio (supponendo che sia necessario `2.4-develop` ramo):

   ```bash
   git checkout 2.4-develop
   ```

1. Cambia in `<app_root>`.
1. Immetti il comando seguente per creare collegamenti simbolici tra i file clonati in modo che i dati di esempio funzionino correttamente:

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

1. Attendere il completamento del comando.

1. Consulta [Impostare le autorizzazioni e la proprietà del file system](#set-file-system-ownership-and-permissions).

1. Esegui il comando seguente:

   ```bash
   bin/magento setup:upgrade
   ```

### Clona con HTTPS

Per clonare l’archivio GitHub dei dati di esempio utilizzando il protocollo HTTPS:

1. In un browser web, vai al [archivio dati di esempio](https://github.com/magento/magento2-sample-data).
1. Sul lato destro della pagina, sotto **URL clone** , fare clic su **HTTPS**.
1. Clic **Copia negli Appunti**.

   Nella figura seguente viene illustrato un esempio.

   ![Clonare l’archivio GitHub utilizzando HTTPS](../../assets/installation/install_mage2_clone-https.png)

1. Passare alla directory principale dei documenti del server Web.

   In genere, per Ubuntu, è `/var/www` e per CentOS è `/var/www/html`.

1. Invio `git clone` e incolla il valore ottenuto in precedenza.

   Di seguito è riportato un esempio:

   ```bash
   git clone https://github.com/magento/magento2-sample-data.git
   ```

1. Attendi che l’archivio venga clonato sul server.
1. Accertati di estrarre il ramo dell’archivio dati di esempio che corrisponde al ramo utilizzato dall’archivio principale `magento2` archivio.

   Ad esempio:

   Se è stato utilizzato il `2.4-develop` dell’archivio GitHub di Magento Open Source, il ramo Dati di esempio deve essere `2.4-develop`.

   Per estrarre il ramo corretto, eseguire il comando seguente dalla directory principale dell&#39;archivio dati di esempio (supponendo che sia necessario `2.4-develop` ramo):

   ```bash
   git checkout 2.4-develop
   ```

1. Cambia in `<magento_root>`.
1. Immetti il comando seguente per creare collegamenti simbolici tra i file clonati in modo che i dati di esempio funzionino correttamente:

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

   Ad esempio:

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="/var/www/magento2"
   ```

1. Attendere il completamento del comando.
1. Vedere la sezione successiva.

>[!WARNING]
>
>Se stai installando dati di esempio *dopo* durante l’installazione di Adobe Commerce, per aggiornare il database e lo schema devi anche eseguire il comando seguente:
>
>```bash
><magento_root>/bin/magento setup:upgrade
>```

## Impostare le autorizzazioni e la proprietà del file system

Perché il `php build-sample-data.php` script crea i symlink tra il repository dei dati di esempio e il repository di Magento Open Source. È necessario impostare le autorizzazioni e la proprietà del file system nel repository dei dati di esempio. In caso contrario, si verificheranno errori durante l’accesso alla vetrina.

Per impostare le autorizzazioni e la proprietà del file system nell&#39;archivio dati di esempio:

1. Passa alla directory dei cloni di dati di esempio.
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

## Completare l&#39;installazione dei dati di esempio

{{$include /help/_includes/sample-data-complete.md}}
