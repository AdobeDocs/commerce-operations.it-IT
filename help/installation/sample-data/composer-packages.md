---
title: Download di pacchetti Compositore dati di esempio
description: Segui questi passaggi per installare Adobe Commerce e i dati di esempio del Magento Open Source utilizzando Composer PHP Package Manager.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---


# Download di pacchetti Compositore dati di esempio

Questa sezione illustra come installare i dati di esempio se si ottiene il software Adobe Commerce o Magenti Open Source in uno dei seguenti modi:

* Download di un archivio compresso da `https://magento.com/tech-resources/download`.

   Se hai scaricato un archivio da GitHub, questo metodo non funziona perché il `composer.json` il file non contiene `repo.magento.com` URL.

* Utilizzato `composer create-project`

È possibile utilizzare questo metodo per ottenere dati di esempio sia per Adobe Commerce che per Magenti Open Source, ma è necessario utilizzare lo stesso [chiavi di autenticazione](../prerequisites/authentication-keys.md) che hai usato per installare l&#39;applicazione.

>[!NOTE]
>
>In caso di errori, ad esempio `Could not find package...` o `...no matching package found...`, assicurati che non ci siano errori di battitura nel tuo comando. Se si verificano ancora degli errori, è possibile che non si disponga dell&#39;accesso agli archivi di Composer corretti, soprattutto se si utilizza Adobe Commerce. Contatto [Supporto Adobe Commerce](https://support.magento.com/hc/en-us) per aiuto.

È possibile utilizzare Composer per installare i dati di esempio prima o dopo l&#39;installazione dell&#39;applicazione; tuttavia, potrebbe [attività aggiuntive](remove-or-update.md).

Se sei uno sviluppatore contributore, consulta [Installare clonando archivi](git-repositories.md).

>[!WARNING]
>
>Non installare dati di esempio se l&#39;applicazione è impostata per [modalità di produzione](../../configuration/bootstrap/application-modes.md#production-mode). Passa a [modalità sviluppatore](../../configuration/bootstrap/application-modes.md#developer-mode) prima. Installazione di dati di esempio in modalità di produzione [fallire](https://support.magento.com/hc/en-us/articles/360033824571#symptom-production-mode-trouble-samp-prod-).

Per installare dati di esempio utilizzando la riga di comando, immettere il comando seguente come proprietario del file system nel `<app_root>` directory:

```bash
bin/magento sampledata:deploy
```

>[!WARNING]
>
>Se stai installando dati di esempio _dopo_ installazione dell&#39;applicazione, è inoltre necessario eseguire il comando seguente per aggiornare il database e lo schema nel `<app_root>` directory:

```bash
bin/magento setup:upgrade
```

È necessario [autenticare](../prerequisites/authentication-keys.md) per completare l’azione.

## Errore di autenticazione

Potrebbe essere visualizzato il seguente errore di autenticazione:

```terminal
[Composer\Downloader\TransportException]
The 'https://repo.magento.com/packages.json' URL required authentication.
You must be using the interactive console to authenticate
```

Se viene visualizzato l&#39;errore, passare alla directory di installazione dell&#39;applicazione ed eseguire `composer update`, che richiede la [chiavi di autenticazione](../prerequisites/authentication-keys.md).

## Completare l’installazione dei dati di esempio

{{$include /help/_includes/sample-data-complete.md}}
