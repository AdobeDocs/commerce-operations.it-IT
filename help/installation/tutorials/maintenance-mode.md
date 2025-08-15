---
title: Attiva o disattiva la modalità di manutenzione
description: Segui questi passaggi per personalizzare ciò che i clienti vedono quando l’implementazione di Adobe Commerce non è disponibile per la manutenzione.
exl-id: 5d9f1493-e771-47b4-b906-3771026cf07a
source-git-commit: a5dbefda6b77d993756143ef0e7270425f824c44
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 0%

---

# Attiva o disattiva la modalità di manutenzione

La guida seguente fa riferimento a una pagina della modalità di manutenzione standard. Se devi utilizzare una pagina di manutenzione personalizzata, consulta [Creare la pagina di manutenzione personalizzata](../../upgrade/troubleshooting/maintenance-mode-options.md) argomento.

Adobe Commerce utilizza la [modalità di manutenzione](../../configuration/bootstrap/application-modes.md#maintenance-mode) per disabilitare l&#39;avvio automatico. La disattivazione dell&#39;avvio automatico è utile durante la manutenzione, l&#39;aggiornamento o la riconfigurazione del sito.

L’applicazione rileva la modalità di manutenzione come segue:

* Se `var/.maintenance.flag` esiste, la modalità di manutenzione è attiva e l&#39;applicazione restituirà una pagina di manutenzione 503.
* Se `var/.maintenance.ip` esiste e l&#39;IP client corrisponde a una delle voci di indirizzo IP all&#39;interno di questo file, la pagina di manutenzione verrà ignorata per la richiesta.

## Installare l’applicazione

Prima di utilizzare questo comando per attivare o disattivare la modalità di manutenzione, è necessario [installare l&#39;applicazione](../advanced.md).

## Attiva o disattiva la modalità di manutenzione

Utilizzare il comando CLI `magento maintenance` per attivare o disattivare la modalità di manutenzione.

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

L&#39;opzione `--ip=<ip address>` è un indirizzo IP da esentare dalla modalità di manutenzione (ad esempio, sviluppatori che eseguono la manutenzione). Per esentare più di un indirizzo IP nello stesso comando, utilizza l’opzione più volte.

>[!NOTE]
>
>L&#39;utilizzo di `--ip=<ip address>` con `magento maintenance:disable` consente di salvare l&#39;elenco degli IP per un utilizzo successivo. Per cancellare l&#39;elenco degli indirizzi IP esenti, utilizzare `magento maintenance:enable --ip=none` o vedere [Gestire l&#39;elenco degli indirizzi IP esenti](#maintain-the-list-of-exempt-ip-addresses).

Il comando `bin/magento maintenance:status` visualizza lo stato della modalità di manutenzione.

Ad esempio, per abilitare la modalità di manutenzione senza esenzioni di indirizzi IP:

```bash
bin/magento maintenance:enable
```

Per attivare la modalità di manutenzione per tutti i client eccetto 192.0.2.10 e 192.0.2.11:

```bash
bin/magento maintenance:enable --ip=192.0.2.10 --ip=192.0.2.11
```

Dopo aver impostato l&#39;applicazione in modalità di manutenzione, è necessario arrestare tutti i processi consumer della coda di messaggi.
Un modo per trovare questi processi consiste nell&#39;eseguire il comando `ps -ef | grep queue:consumers:start`, quindi eseguire il comando `kill <process_id>` per ogni consumer. In un ambiente con più nodi, ripeti questa attività su ciascun nodo.

## Gestisci l&#39;elenco di indirizzi IP esenti

Per mantenere l&#39;elenco degli indirizzi IP esenti, è possibile utilizzare l&#39;opzione `[--ip=<ip list>]` nei comandi precedenti oppure utilizzare quanto segue:

```bash
bin/magento maintenance:allow-ips <ip address> .. <ip address> [--none]
```

La sintassi `<ip address> .. <ip address>` è un elenco facoltativo delimitato da spazi di indirizzi IP da esentare.

L&#39;opzione `--none` cancella l&#39;elenco.

## Configurazioni multi-store

<!-- To set up multiple stores, each with a different layout and localized content, create a skin for each and put it into `pub/errors/{name}` where `{name}` is the store code. To distinguish between stores and websites with the same instance, use `pub/errors/{type}-{name}` where `{type}` is either `store` or `website` and matches the `MAGE_RUN_TYPE` in your server configuration. Another option is to pass the `$_GET['skin']` parameter to the intended processor. This method requires a specific configuration on your server. -->
<!-- Replace the line below with the commented text after https://github.com/magento/magento2/pull/35095 is merged. -->

Se si desidera impostare più archivi, ciascuno con un layout e un contenuto localizzato diversi, passare il parametro `$_GET['skin']` al processore desiderato.

Nell&#39;esempio seguente viene utilizzato un file di modello di errore di tipo `503` che richiede contenuto localizzato.

Il costruttore della classe `Error_Processor` accetta un parametro GET `skin` per modificare il layout:

```php
if (isset($_GET['skin'])) {
    $this->_setSkin($_GET['skin']);
}
```

Può essere aggiunto anche a una regola di riscrittura nel file `.htaccess` che aggiunge un parametro `skin` all&#39;URL.

### Parametro $_GET[&#39;skin&#39;]

Per utilizzare il parametro `skin`:

1. Verifica se `.maintenance.flag` esiste.
1. Prendere nota dell&#39;indirizzo host, che fa riferimento a `HTTP_HOST`, o di qualsiasi altra variabile come le variabili ENV.
1. Verificare se il parametro `skin` esiste.
1. Imposta il parametro utilizzando le regole di riscrittura seguenti.

   Di seguito sono riportati alcuni esempi di regole di riscrittura:

   * RewriteCond `%{DOCUMENT_ROOT}/var/.maintenance.flag -f`
   * RewriteCond `%{HTTP_HOST} ^sub.example.com$`
   * RewriteCond `%{QUERY_STRING} !(^|&)skin=sub(&|$)` [NC]
   * Riscrivi regola `^ %{REQUEST_URI}?skin=sub` [L]

1. Copia i seguenti file:

   * Da `pub/errors/default/503.phtml` a `pub/errors/sub/503.phtml`
   * Da `pub/errors/default/css/styles.css` a `pub/errors/sub/styles.css`

1. Modificare questi file per fornire contenuto localizzato nel file `503.phtml` e stile personalizzato nel file `styles.css`.

   Verificare che i percorsi puntino alla directory `errors`. Il nome della directory deve corrispondere al parametro URL indicato in `RewriteRule`. Nell&#39;esempio precedente viene utilizzata la directory `sub`, specificata come parametro in `RewriteRule` (`skin=sub`)

>[!NOTE]
>
>È necessario aggiungere l&#39;impostazione [nginx](../../configuration/multi-sites/ms-nginx.md) per le impostazioni multi-store.
