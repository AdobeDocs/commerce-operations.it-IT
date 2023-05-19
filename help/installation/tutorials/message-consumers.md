---
title: Configurare i consumer di messaggi
description: Segui questi passaggi per configurare il comportamento dei consumer della coda di messaggi di Adobe Commerce o di Magento Open Source.
exl-id: df292301-f4bd-49df-a241-7467c35bf1d8
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '69'
ht-degree: 0%

---

# Configurare i consumer di messaggi

Prima di eseguire questo comando, è necessario effettuare le seguenti operazioni *o* devi [installare l’applicazione](../advanced.md):

* [Creare o aggiornare la configurazione della distribuzione](deployment.md)
* [Creare lo schema del database](database.md)

## Configurare il comportamento dei consumatori

La configurazione del comportamento del consumatore viene eseguita inviando coppie chiave/valore all’interno della funzione di configurazione:

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Descrizioni dei parametri

{{$include /help/_includes/cli-consumers.md}}
