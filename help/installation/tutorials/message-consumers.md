---
title: Configurare i consumer di messaggi
description: Per configurare il comportamento dei consumer della coda di messaggi di Adobe Commerce, segui la procedura riportata di seguito.
exl-id: df292301-f4bd-49df-a241-7467c35bf1d8
last-update: 2026-04-28T00:00:00Z
source-git-commit: 1166b8fbfeef21a51ad6e4e695aed2b25006230e
workflow-type: tm+mt
source-wordcount: '65'
ht-degree: 0%

---

# Configurare i consumer di messaggi

Prima di eseguire questo comando, è necessario eseguire *o* [installare l&#39;applicazione](../advanced.md):

* [Creare o aggiornare la configurazione della distribuzione](deployment.md)
* [Creare lo schema del database](database.md)

## Configurare il comportamento dei consumatori

La configurazione del comportamento del consumatore viene eseguita inviando coppie chiave/valore all’interno della funzione di configurazione:

```shell
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Descrizioni dei parametri

{{$include /help/_includes/cli-consumers.md}}

<!-- Last updated from includes: 2022-09-12 09:38:25 -->
