---
title: Disinstallare o reinstallare Adobe Commerce
description: Per disinstallare e reinstallare le installazioni locali di Adobe Commerce, segui la procedura riportata di seguito.
exl-id: fbaeee2c-8da0-4c89-a6d1-882a65014520
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%
---
# Disinstallare o reinstallare Adobe Commerce

Prima di utilizzare questi comandi, è necessario [installare l&#39;applicazione](../tutorials/install.md).

## Aggiornare l’applicazione

Per aggiornare l&#39;applicazione:

* Se il software è stato installato da un archivio o se è stato utilizzato &quot;compositore-create-project&quot;, vedere la [Guida all&#39;aggiornamento](../../upgrade/overview.md).
* Se sei uno sviluppatore (ovvero hai utilizzato `git clone`), consulta [Aggiornare l&#39;applicazione](../../upgrade/developer/git-installs.md).

## Reinstalla l’applicazione

La modalità di reinstallazione dell&#39;applicazione dalla riga di comando dipende dal ruolo:

* Se il software è stato installato da un archivio o se è stato utilizzato &quot;compositore-create-project&quot;, vedere [Aggiorna dipendenze di installazione](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies).
* Se sei uno sviluppatore collaborante (ovvero hai iniziato a utilizzare `git clone`), consulta [Aggiornare le dipendenze di installazione](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies).

## Disinstallare l’applicazione

La disinstallazione dell&#39;applicazione provoca l&#39;eliminazione e il ripristino del database, la rimozione della configurazione di distribuzione e la cancellazione delle directory in `var`.

Per disinstallare l&#39;applicazione, immettere il comando seguente:

```shell
bin/magento setup:uninstall
```

Per confermare la disinstallazione corretta viene visualizzato il seguente messaggio:

```text
[SUCCESS]: Magento uninstallation complete.
```

## Facoltativamente, conservazione dei file generati

Per impostazione predefinita, `bin/magento setup:upgrade` cancella il codice compilato e la cache. In genere si utilizza `bin/magento setup:upgrade` per aggiornare i componenti e ogni componente può richiedere classi compilate diverse.

Tuttavia, in alcune situazioni (in particolare, la distribuzione in produzione), potrebbe essere opportuno evitare di cancellare il codice compilato perché potrebbe richiedere un po’ di tempo. (La cache viene ancora cancellata). Per aggiornare lo schema e i dati del database *senza* cancellare il codice compilato, immettere:

```shell
bin/magento setup:upgrade --keep-generated
```

>[!WARNING]
>
>L&#39;opzione opzionale `--keep-generated` deve essere utilizzata in circostanze limitate dagli integratori di sistema esperti *only*. Questa opzione deve *mai* essere utilizzata in un ambiente di sviluppo. L&#39;utilizzo non corretto di questo parametro opzionale può causare errori durante l&#39;esecuzione del codice.

## Installare l’applicazione

* [Eseguire l’installazione tramite la riga di comando](../advanced.md)
