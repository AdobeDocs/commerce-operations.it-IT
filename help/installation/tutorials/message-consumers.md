---
title: Configurare i consumer di messaggi
description: Per configurare il comportamento dei consumer della coda di messaggi di Adobe Commerce, segui la procedura riportata di seguito.
exl-id: df292301-f4bd-49df-a241-7467c35bf1d8
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '65'
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
