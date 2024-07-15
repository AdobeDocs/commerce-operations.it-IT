---
title: Cancellazione della cache con più istanze di vernice
description: Scopri come funziona la cancellazione della cache con più istanze di Vernice.
feature: Configuration, Cache
exl-id: 289a4e54-9e73-454c-bfb9-e78e405af56c
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 1%

---

# Cancellazione della cache di più istanze di vernice

Adobe Commerce supporta più istanze di vernice pronte all’uso.

Questo argomento illustra le nozioni di base sulla configurazione di più istanze di Vernice con Commerce.

## Configurazione per eliminare più istanze di vernice

Commerce elimina gli host Varnish dopo aver configurato gli host Varnish utilizzando il comando [`magento setup:config:set`](../../installation/tutorials/deployment.md).

È necessario utilizzare il parametro `--http-cache-hosts` per specificare un elenco separato da virgole di host e porte di ascolto di Microsoft. (Non separare gli host con uno spazio).

Il formato del parametro deve essere `<hostname or ip>:<listen port>`, dove è possibile omettere `<listen port>` se si tratta della porta 80.

Ad esempio:

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

È quindi possibile eliminare tutti gli host Vernice quando si aggiorna la cache di Commerce (nota anche come _pulizia_ della cache) nell&#39;Admin o utilizzando la riga di comando.

Per aggiornare la cache utilizzando l&#39;amministratore, fare clic su **SYSTEM** > Strumenti > **Gestione cache**, quindi fare clic su **Svuota cache di Magento** nella parte superiore della pagina. (Puoi anche aggiornare singoli tipi di cache).

Per aggiornare la cache di più istanze di Microsoft da cli, utilizzare il comando [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) come [proprietario del file system](../../installation/prerequisites/file-system/overview.md).
