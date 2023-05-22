---
title: Cancellazione della cache con vernice
description: Scopri come funziona il clearing della cache con Varnish e come utilizzarlo come acceleratore di web-caching per l’applicazione Adobe Commerce.
feature: Configuration, Cache
exl-id: 866da415-c428-4092-a045-c3079493cdc4
source-git-commit: a2bd4139aac1044e7e5ca8fcf2114b7f7e9e9b68
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# Cancellazione della cache con vernice

Questo argomento illustra le nozioni di base sull’utilizzo di Varnish come acceleratore di web-caching per Adobe Commerce e Magenti Open Source.

## Spurgatura vernice

Secondo [Documentazione di vernice](https://www.varnish-cache.org/docs/trunk/users-guide/purging.html), &quot;A *svuota* è ciò che accade quando si estrae un oggetto dalla cache e lo si elimina insieme alle relative varianti.&quot; Un&#39;eliminazione di vernice è simile a un comando di pulitura della cache (o a un clic **Svuota cache Magento** in Admin).

Infatti, quando pulisci, svuota o aggiorni la cache di Commerce, anche le purghe di vernice si spolverano.

Dopo aver installato e configurato la vernice per funzionare con Commerce, le seguenti azioni possono causare un’eliminazione della vernice:

- Gestione di un sito Web.

   Ad esempio, tutte le operazioni eseguite nell’amministratore in:

   - **NEGOZI** > **Impostazioni** > **Configurazione** > GENERALE > **Generale**
   - **NEGOZI** > **Impostazioni** > **Configurazione** > GENERALE > **Impostazione valuta**
   - **NEGOZI** > **Impostazioni** > **Configurazione** > GENERALE > **Memorizza indirizzi e-mail**

   Quando Commerce rileva tale modifica, viene visualizzato un messaggio che ti informa di aggiornare la cache.

- Gestione di un negozio (ad esempio, aggiunta o modifica di categorie, prezzi, prodotti e regole di prezzo promozionali).

   La vernice viene eliminata automaticamente quando si esegue una di queste operazioni.

- Gestione del codice sorgente.

   È necessario aggiornare la cache ed eliminare periodicamente tutto ciò che si trova nel `generated/code` e `generated/metadata` directory. Per informazioni sull’aggiornamento della cache, consulta la sezione successiva.

## Configurare Commerce per eliminare la vernice

Commerce elimina gli host di vernice dopo aver configurato gli host di vernice utilizzando [`magento setup:config:set`](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html#setupconfigset) comando.

Puoi utilizzare il parametro opzionale `--http-cache-hosts` per specificare un elenco separato da virgole di host e porte di ascolto di Vernice. Configurare tutti gli host Vernice, indipendentemente dal fatto che ne siano presenti uno o più. (Non separare gli host con uno spazio).

Il formato del parametro deve essere `<hostname or ip>:<listen port>`, dove è possibile omettere `<listen port>` se si tratta della porta 80.

Ad esempio:

```bash
bin/magento setup:config:set --http-cache-hosts=192.0.2.100,192.0.2.155:6081
```

È quindi possibile eliminare gli host di vernice quando si aggiorna la cache di Commerce (nota anche come *pulizia* cache) nell’Admin o utilizzando la riga di comando.

Per aggiornare la cache utilizzando Admin, fai clic su **[!UICONTROL SYSTEM]** > Strumenti > **Gestione cache**, quindi fai clic su **Svuota cache Magento** nella parte superiore della pagina. (Puoi anche aggiornare singoli tipi di cache).

Per aggiornare la cache utilizzando la riga di comando, in genere si utilizza [`magento cache:clean <type>`](../cli/manage-cache.md#clean-and-flush-cache-types) comando come [proprietario del file system](../../installation/prerequisites/file-system/overview.md).
