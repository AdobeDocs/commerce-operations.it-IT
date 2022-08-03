---
title: Cancellazione della cache con più istanze vernish
description: Scopri come la cancellazione della cache funziona con più istanze di Varnish.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '194'
ht-degree: 1%

---


# Cancellazione della cache di più istanze verniciate

Adobe Commerce e Magenti Open Source supportano più istanze di Varnish preconfigurate.

Questo argomento illustra le nozioni di base per la configurazione di più istanze di Varnish con Commerce.

## Configurazione per eliminare più istanze di vernice

Commerce elimina gli host Varnish dopo aver configurato gli host Varnish utilizzando [`magento setup:config:set`](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-deployment.html) comando.

Utilizza la `--http-cache-hosts` per specificare un elenco di host e porte di ascolto separati da virgole. (Non separare gli host con un carattere spazio.)

Il formato del parametro deve essere `<hostname or ip>:<listen port>`, in cui è possibile omettere `<listen port>` se si tratta della porta 80.

Ad esempio:

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:8080
```

È quindi possibile eliminare tutti gli host Varnish quando si aggiorna la cache Commerce (noto anche come _pulizia_ la cache) nell’amministratore o utilizzando la riga di comando.

Per aggiornare la cache utilizzando l’amministratore, fai clic su **SISTEMA** > Strumenti > **Gestione cache**, quindi fai clic su **Svuotare la cache del Magento** nella parte superiore della pagina. È inoltre possibile aggiornare singoli tipi di cache.

Per aggiornare la cache di più istanze di Varnish da cli, utilizza il [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) come comando [proprietario del file system](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
