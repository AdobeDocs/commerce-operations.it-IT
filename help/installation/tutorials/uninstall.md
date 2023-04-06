---
title: Disinstallare o reinstallare Adobe Commerce
description: Segui questi passaggi per disinstallare e reinstallare installazioni on-premise di Adobe Commerce e Magenti Open Source.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '281'
ht-degree: 0%

---


# Disinstallare o reinstallare Adobe Commerce

Prima di utilizzare questi comandi, è necessario [installare l&#39;applicazione](../tutorials/install.md).

## Aggiornare l’applicazione

Per aggiornare l&#39;applicazione:

* Se hai installato il software da un archivio o se hai utilizzato &quot;compositore-crea-progetto&quot;, consulta la [Guida all’aggiornamento](../../upgrade/overview.md).
* Se sei uno sviluppatore contributore (cioè hai usato `git clone`), vedi [Aggiornare l’applicazione](../../upgrade/developer/git-installs.md).

## Reinstallare l&#39;applicazione

La modalità di reinstallazione dell’applicazione dalla riga di comando dipende dal ruolo:

* Se hai installato il software da un archivio o se hai utilizzato &quot;compositore-crea-progetto&quot;, vedi [Aggiornare le dipendenze di installazione](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).
* Se sei uno sviluppatore contributore (ovvero, hai iniziato a utilizzare `git clone`), vedi [Aggiornare le dipendenze di installazione](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## Disinstalla l&#39;applicazione

La disinstallazione dell&#39;applicazione consente di rilasciare e ripristinare il database, rimuove la configurazione di distribuzione e cancella le directory in `var`.

Per disinstallare l&#39;applicazione, immettere il comando seguente:

```bash
bin/magento setup:uninstall
```

Viene visualizzato il seguente messaggio per confermare la corretta disinstallazione:

```terminal
[SUCCESS]: Magento uninstallation complete.
```

## Opzione di conservazione dei file generati

Per impostazione predefinita, `bin/magento setup:upgrade` cancella il codice compilato e la cache. In genere si utilizza `bin/magento setup:upgrade` per aggiornare i componenti e ogni componente può richiedere diverse classi compilate.

Tuttavia, in alcune situazioni (in particolare durante l&#39;implementazione in produzione), si potrebbe evitare di cancellare il codice compilato perché potrebbe richiedere del tempo. (La cache è ancora svuotata). Per aggiornare lo schema e i dati del database *senza* cancella il codice compilato, immetti:

```bash
bin/magento setup:upgrade --keep-generated
```

>[!WARNING]
>
>L&#39;opzione `--keep-generated` l&#39;opzione deve essere utilizzata in circostanze limitate da integratori di sistema esperti *only*. Questa opzione dovrebbe *mai* in un ambiente di sviluppo. L&#39;utilizzo improprio di questo parametro opzionale può causare errori durante l&#39;esecuzione del codice.

## Installare l’applicazione

* [Installare utilizzando la riga di comando](../advanced.md)
