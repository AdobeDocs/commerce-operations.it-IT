---
title: Configurare i consumatori di messaggi
description: Segui questi passaggi per configurare il comportamento dei consumatori della coda dei messaggi di Adobe Commerce o Magento Open Source.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 0%

---


# Configurare i consumatori di messaggi

Prima di eseguire questo comando, è necessario effettuare le seguenti operazioni *o* devi [installare l&#39;applicazione](../advanced.md):

* [Creare o aggiornare la configurazione della distribuzione](deployment.md)
* [Creare lo schema del database](database.md)

## Configurare il comportamento dei consumatori

La configurazione del comportamento del consumatore viene effettuata inviando coppie chiave/valore all&#39;interno della funzione di configurazione:

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Descrizioni dei parametri

{{$include /help/_includes/cli-consumers.md}}
