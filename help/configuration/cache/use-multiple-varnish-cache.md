---
title: Cancellazione della cache con più istanze di vernice
description: Scopri come funziona la cancellazione della cache con più istanze di Vernice.
feature: Configuration, Cache
exl-id: 289a4e54-9e73-454c-bfb9-e78e405af56c
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 1%

---

# Cancellazione della cache di più istanze di vernice

Adobe Commerce e Magento Open Source supportano più istanze di vernice pronte all’uso.

Questo argomento illustra le nozioni di base sulla configurazione di più istanze di Vernice con Commerce.

## Configurazione per eliminare più istanze di vernice

Commerce elimina gli host di vernice dopo aver configurato gli host di vernice utilizzando [`magento setup:config:set`](../../installation/tutorials/deployment.md) comando.

Dovresti utilizzare il `--http-cache-hosts` per specificare un elenco separato da virgole di host e porte di ascolto di Vernice. (Non separare gli host con uno spazio).

Il formato del parametro deve essere `<hostname or ip>:<listen port>`, dove è possibile omettere `<listen port>` se si tratta della porta 80.

Ad esempio:

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

È quindi possibile eliminare tutti gli host Vernice quando si aggiorna la cache di Commerce (nota anche come _pulizia_ cache) nell’Admin o utilizzando la riga di comando.

Per aggiornare la cache utilizzando Admin, fai clic su **SISTEMA** > Strumenti > **Gestione cache**, quindi fai clic su **Svuota cache Magento** nella parte superiore della pagina. (Puoi anche aggiornare singoli tipi di cache).

Per aggiornare la cache di più istanze di Vernice da cli, utilizza [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) comando come [proprietario del file system](../../installation/prerequisites/file-system/overview.md).
