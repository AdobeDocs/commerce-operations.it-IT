---
title: Cancellazione della cache con vernice
description: Scopri come funziona la cancellazione della cache con Varnish e come utilizzarla come acceleratore di memorizzazione nella cache web per l’applicazione Adobe Commerce.
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---


# Cancellazione della cache con vernice

Questo argomento illustra le nozioni di base sull’utilizzo di Varnish come acceleratore di memorizzazione nella cache web per Adobe Commerce e Magenti Open Source.

## Spuratura verniciosa

Secondo [Documentazione di vernice](https://www.varnish-cache.org/docs/trunk/users-guide/purging.html), &quot;A *purgare* è ciò che accade quando si sceglie un oggetto dal [cache](https://glossary.magento.com/cache) e lo scarti insieme alle sue varianti.&quot; Una eliminazione vernice è simile a un comando di eliminazione cache (o facendo clic su **Svuotare la cache del Magento** in Admin).

Infatti, quando pulisci, svuota o aggiorna la cache Commerce, anche Varnish elimina.

Dopo aver installato e configurato Varnish per lavorare con Commerce, le azioni seguenti possono causare una pulizia di Varnish:

- Mantenimento di un [sito web](https://glossary.magento.com/website).

   Ad esempio, tutte le operazioni eseguite nell’amministratore in:

   - **NEGOZI** > **Impostazioni** > **Configurazione** > GENERALE > **Generale**
   - **NEGOZI** > **Impostazioni** > **Configurazione** > GENERALE > **Impostazione valuta**
   - **NEGOZI** > **Impostazioni** > **Configurazione** > GENERALE > **Archivia indirizzi e-mail**

   Quando Commerce rileva tale modifica, viene visualizzato un messaggio per informarti di aggiornare la cache.

- Mantenimento di un negozio (ad esempio, aggiunta o modifica di categorie, prezzi, prodotti e regole di prezzo promozionali).

   La vernice viene eliminata automaticamente quando si esegue una di queste attività.

- Manutenzione del codice sorgente.

   Aggiorna la cache ed elimina periodicamente tutti gli elementi presenti nella `generated/code` e `generated/metadata` directory. Per informazioni sull’aggiornamento della cache, consulta la sezione successiva.

## Configurare Commerce per eliminare Varnish

Commerce elimina gli host Varnish dopo aver configurato gli host Varnish utilizzando [`magento setup:config:set`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#setupconfigset) comando.

È possibile utilizzare il parametro opzionale `--http-cache-hosts` per specificare un elenco di host e porte di ascolto separati da virgole. Configura tutti gli host di Varnish, indipendentemente dal fatto che ne abbia uno o più. (Non separare gli host con un carattere spazio.)

Il formato del parametro deve essere `<hostname or ip>:<listen port>`, in cui è possibile omettere `<listen port>` se si tratta della porta 80.

Ad esempio:

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:6081
```

È quindi possibile eliminare gli host Varnish quando si aggiorna la cache Commerce (noto anche come *pulizia* la cache) nell’amministratore o utilizzando la riga di comando.

Per aggiornare la cache utilizzando l’amministratore, fai clic su **[!UICONTROL SYSTEM]** > Strumenti > **Gestione cache**, quindi fai clic su **Svuotare la cache del Magento** nella parte superiore della pagina. È inoltre possibile aggiornare singoli tipi di cache.

Per aggiornare la cache utilizzando la riga di comando, in genere si utilizza il [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) come comando [proprietario del file system](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
