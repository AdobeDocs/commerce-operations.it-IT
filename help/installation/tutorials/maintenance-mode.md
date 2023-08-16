---
title: Attiva o disattiva la modalità di manutenzione
description: Segui questi passaggi per personalizzare ciò che i clienti vedono quando l’implementazione di Adobe Commerce o di Magento Open Source non è disponibile per la manutenzione.
exl-id: 5d9f1493-e771-47b4-b906-3771026cf07a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 0%

---

# Attiva o disattiva la modalità di manutenzione

La guida seguente fa riferimento a una pagina della modalità di manutenzione standard. Se devi utilizzare una pagina di manutenzione personalizzata, consulta [Creare la pagina di manutenzione personalizzata](../../upgrade/troubleshooting/maintenance-mode-options.md) argomento.

Adobe Commerce e utilizzo del Magento Open Source [modalità di manutenzione](../../configuration/bootstrap/application-modes.md#maintenance-mode) per disattivare l&#39;avvio automatico. La disattivazione dell&#39;avvio automatico è utile durante la manutenzione, l&#39;aggiornamento o la riconfigurazione del sito.

L’applicazione rileva la modalità di manutenzione come segue:

* Se `var/.maintenance.flag` non esiste, la modalità di manutenzione è disattivata e l’applicazione funziona normalmente.
* In caso contrario, la modalità di manutenzione è attiva a meno che `var/.maintenance.ip` esiste.

  `var/.maintenance.ip` può contenere un elenco di indirizzi IP. Se si accede a un punto di ingresso tramite HTTP e l&#39;indirizzo IP del client corrisponde a una delle voci dell&#39;elenco, la modalità di manutenzione è disattivata.

## Installare l’applicazione

Prima di utilizzare questo comando per attivare o disattivare la modalità di manutenzione, è necessario [installare l’applicazione](../advanced.md).

## Attiva o disattiva la modalità di manutenzione

Utilizza il `magento maintenance` Comando CLI per attivare o disattivare la modalità di manutenzione.

Utilizzo comando:

```bash
bin/magento maintenance:enable [--ip=<ip address> ... --ip=<ip address>] | [ip=none]
```

```bash
bin/magento maintenance:disable [--ip=<ip address> ... --ip=<ip address>] | [ip=none]
```

```bash
bin/magento maintenance:status
```

Il `--ip=<ip address>` L’opzione è un indirizzo IP da esentare dalla modalità di manutenzione (ad esempio, sviluppatori che eseguono la manutenzione). Per esentare più di un indirizzo IP nello stesso comando, utilizza l’opzione più volte.

>[!NOTE]
>
>Utilizzo di `--ip=<ip address>` con `magento maintenance:disable` salva l’elenco degli IP per un utilizzo successivo. Per cancellare l’elenco degli IP esenti, utilizza `magento maintenance:enable --ip=none` o vedi [Gestisci l&#39;elenco di indirizzi IP esenti](#maintain-the-list-of-exempt-ip-addresses).

Il `bin/magento maintenance:status` Il comando visualizza lo stato della modalità di manutenzione.

Ad esempio, per abilitare la modalità di manutenzione senza esenzioni di indirizzi IP:

```bash
bin/magento maintenance:enable
```

Per attivare la modalità di manutenzione per tutti i client eccetto 192.0.2.10 e 192.0.2.11:

```bash
bin/magento maintenance:enable --ip=192.0.2.10 --ip=192.0.2.11
```

Dopo aver impostato l&#39;applicazione in modalità di manutenzione, è necessario arrestare tutti i processi consumer della coda di messaggi.
Un modo per trovare questi processi è quello di eseguire `ps -ef | grep queue:consumers:start` ed eseguire il comando `kill <process_id>` per ogni consumer. In un ambiente con più nodi, ripeti questa attività su ciascun nodo.

## Gestisci l&#39;elenco di indirizzi IP esenti

Per mantenere l’elenco degli indirizzi IP esenti, puoi utilizzare `[--ip=<ip list>]` nei comandi precedenti oppure è possibile utilizzare quanto segue:

```bash
bin/magento maintenance:allow-ips <ip address> .. <ip address> [--none]
```

Il `<ip address> .. <ip address>` La sintassi è un elenco facoltativo di indirizzi IP delimitati da spazi da esentare.

Il `--none` L&#39;opzione cancella l&#39;elenco.

## Configurazioni multi-store

<!-- To set up multiple stores, each with a different layout and localized content, create a skin for each and put it into `pub/errors/{name}` where `{name}` is the store code. To distinguish between stores and websites with the same instance, use `pub/errors/{type}-{name}` where `{type}` is either `store` or `website` and matches the `MAGE_RUN_TYPE` in your server configuration. Another option is to pass the `$_GET['skin']` parameter to the intended processor. This method requires a specific configuration on your server. -->
<!-- Replace the line below with the commented text after https://github.com/magento/magento2/pull/35095 is merged. -->

Se desideri impostare più store, ciascuno con un layout diverso e contenuti localizzati, passa il `$_GET['skin']` al processore previsto.

Nell’esempio seguente viene utilizzato un `503` digita il file del modello di errore, che richiede contenuto localizzato.

Costruttore di `Error_Processor` la classe accetta un `skin` Parametro GET per modificare il layout:

```php
if (isset($_GET['skin'])) {
    $this->_setSkin($_GET['skin']);
}
```

Questo può anche essere aggiunto a una regola di riscrittura nel `.htaccess` file che aggiunge un `skin` all&#39;URL.

### $_GET[&#39;pelle&#39;] parametro

Per utilizzare `skin` parametro:

1. Controlla se `.maintenance.flag` esiste.
1. Prendi nota dell’indirizzo host, che fa riferimento al `HTTP_HOST`, o qualsiasi altra variabile, ad esempio le variabili ENV.
1. Controlla se `skin` parametro esistente.
1. Imposta il parametro utilizzando le regole di riscrittura seguenti.

   Di seguito sono riportati alcuni esempi di regole di riscrittura:

   * RewriteCond `%{DOCUMENT_ROOT}/var/.maintenance.flag -f`
   * RewriteCond `%{HTTP_HOST} ^sub.example.com$`
   * RewriteCond `%{QUERY_STRING} !(^|&)skin=sub(&|$)` [NC]
   * RewriteRule `^ %{REQUEST_URI}?skin=sub` [L]

1. Copia i seguenti file:

   * `pub/errors/default/503.phtml` a `pub/errors/sub/503.phtml`
   * `pub/errors/default/css/styles.css` a `pub/errors/sub/styles.css`

1. Modifica questi file per fornire contenuto localizzato in `503.phtml` file e stile personalizzato in `styles.css` file.

   Assicurati che i percorsi puntino al tuo `errors` directory. Il nome della directory deve corrispondere al parametro URL indicato nella `RewriteRule`. Nell&#39;esempio precedente, il `sub` viene utilizzato, che viene specificato come parametro nel file `RewriteRule` (`skin=sub`)

>[!NOTE]
>
>Il [nginx](../../configuration/multi-sites/ms-nginx.md) è necessario aggiungere l&#39;impostazione per le impostazioni multi-store.
