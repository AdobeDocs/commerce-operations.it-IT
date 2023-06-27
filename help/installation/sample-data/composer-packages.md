---
title: Scarica pacchetti del Compositore dati di esempio
description: Segui questi passaggi per installare i dati di esempio di Adobe Commerce e Magento Open Source utilizzando il Composer PHP Package Manager.
feature: Install, Deploy
exl-id: 735591af-a152-4476-9fa6-e31c4bab3ba8
source-git-commit: ce405a6bb548b177427e4c02640ce13149c48aff
workflow-type: tm+mt
source-wordcount: '307'
ht-degree: 0%

---

# Scarica pacchetti del Compositore dati di esempio

Questa sezione illustra come installare dati di esempio se si è ottenuto il software Adobe Commerce o di Magento Open Source in uno dei seguenti modi:

* Download di un archivio compresso da `https://magento.com/tech-resources/download`.

  Se hai scaricato un archivio da GitHub, questo metodo non funziona perché il `composer.json` il file non contiene `repo.magento.com` URL.

* Utilizzato `composer create-project`

Puoi utilizzare questo metodo per ottenere dati di esempio sia per Adobe Commerce che per Magenti Open Source, ma devi utilizzare lo stesso [chiavi di autenticazione](../prerequisites/authentication-keys.md) utilizzato per installare l’applicazione.

>[!NOTE]
>
>Se riscontri errori, ad esempio `Could not find package...` o `...no matching package found...`, verificare che nel comando non siano presenti errori di battitura. Se riscontri ancora errori, potresti non avere accesso ai giusti archivi del Compositore, soprattutto se utilizzi Adobe Commerce. Contatto [Supporto Adobe Commerce](https://support.magento.com/hc/en-us) per assistenza.

È possibile utilizzare Composer per installare i dati di esempio prima o dopo l&#39;installazione dell&#39;applicazione; tuttavia, è possibile che [attività aggiuntive](remove-or-update.md).

Se partecipi come sviluppatore, consulta [Installare mediante la clonazione degli archivi](git-repositories.md).

>[!WARNING]
>
>Non installare dati di esempio se l&#39;applicazione è impostata per [modalità di produzione](../../configuration/bootstrap/application-modes.md#production-mode). Passa a [modalità sviluppatore](../../configuration/bootstrap/application-modes.md#developer-mode) prima. Installazione dei dati di esempio in modalità di produzione [non riesce](https://support.magento.com/hc/en-us/articles/360033824571#symptom-production-mode-trouble-samp-prod-).

Per installare i dati di esempio tramite la riga di comando, immettere il comando seguente come proprietario del file system in `<app_root>` directory:

```bash
bin/magento sampledata:deploy
```

>[!WARNING]
>
>Se stai installando dati di esempio _dopo_ durante l&#39;installazione dell&#39;applicazione, è inoltre necessario eseguire il comando seguente per aggiornare il database e lo schema in `<app_root>` directory:

```bash
bin/magento setup:upgrade
```

È necessario: [autenticare](../prerequisites/authentication-keys.md) per completare l&#39;azione.

## Errore di autenticazione

È possibile che venga visualizzato il seguente errore di autenticazione:

```terminal
[Composer\Downloader\TransportException]
The 'https://repo.magento.com/packages.json' URL required authentication.
You must be using the interactive console to authenticate
```

Se viene visualizzato l&#39;errore, passare alla directory di installazione dell&#39;applicazione ed eseguire `composer update`, che richiede di specificare [chiavi di autenticazione](../prerequisites/authentication-keys.md).

## Completare l&#39;installazione dei dati di esempio

{{$include /help/_includes/sample-data-complete.md}}
