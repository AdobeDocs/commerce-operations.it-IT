---
title: Disinstallare o reinstallare Adobe Commerce
description: Segui questi passaggi per disinstallare e reinstallare le installazioni locali di Adobe Commerce e Magento Open Source.
exl-id: fbaeee2c-8da0-4c89-a6d1-882a65014520
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---

# Disinstallare o reinstallare Adobe Commerce

Prima di utilizzare questi comandi, è necessario [installare l’applicazione](../tutorials/install.md).

## Aggiornare l’applicazione

Per aggiornare l&#39;applicazione:

* Se il software è stato installato da un archivio o se è stato utilizzato &quot;compositore-crea-progetto&quot;, vedere [Guida all’aggiornamento](../../upgrade/overview.md).
* Se hai collaborato come sviluppatore (ovvero hai utilizzato `git clone`), vedi [Aggiornare l’applicazione](../../upgrade/developer/git-installs.md).

## Reinstalla l’applicazione

La modalità di reinstallazione dell&#39;applicazione dalla riga di comando dipende dal ruolo:

* Se il software è stato installato da un archivio o se è stato utilizzato &quot;compositore-crea-progetto&quot;, vedere [Aggiornare le dipendenze di installazione](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).
* Se sei uno sviluppatore contribuente (ovvero, hai iniziato a utilizzare `git clone`), vedi [Aggiornare le dipendenze di installazione](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## Disinstallare l’applicazione

La disinstallazione dell’applicazione fa cadere e ripristina il database, rimuove la configurazione di distribuzione e cancella le directory in `var`.

Per disinstallare l&#39;applicazione, immettere il comando seguente:

```bash
bin/magento setup:uninstall
```

Per confermare la disinstallazione corretta viene visualizzato il seguente messaggio:

```terminal
[SUCCESS]: Magento uninstallation complete.
```

## Facoltativamente, conservazione dei file generati

Per impostazione predefinita, `bin/magento setup:upgrade` cancella il codice compilato e la cache. In genere, si utilizza `bin/magento setup:upgrade` per aggiornare i componenti e ogni componente può richiedere classi compilate diverse.

Tuttavia, in alcune situazioni (in particolare, la distribuzione in produzione), potrebbe essere opportuno evitare di cancellare il codice compilato perché potrebbe richiedere un po’ di tempo. (La cache viene ancora cancellata). Per aggiornare lo schema e i dati del database *senza* cancellazione del codice compilato, immettere:

```bash
bin/magento setup:upgrade --keep-generated
```

>[!WARNING]
>
>L&#39;opzione `--keep-generated` l&#39;opzione deve essere utilizzata in circostanze limitate da integratori di sistemi esperti *solo*. Questa opzione dovrebbe *mai* essere utilizzato in un ambiente di sviluppo. L&#39;utilizzo non corretto di questo parametro opzionale può causare errori durante l&#39;esecuzione del codice.

## Installare l’applicazione

* [Eseguire l’installazione tramite la riga di comando](../advanced.md)
