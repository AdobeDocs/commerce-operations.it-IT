---
title: Attiva o disattiva la modalità di manutenzione
description: Segui questi passaggi per personalizzare ciò che i clienti vedono quando la distribuzione di Adobe Commerce o Magento Open Source è inattiva per la manutenzione.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 0%

---


# Attiva o disattiva la modalità di manutenzione

La guida seguente fa riferimento a una pagina in modalità di manutenzione standard. Se devi utilizzare una pagina di manutenzione personalizzata, consulta [Creare la pagina di manutenzione personalizzata](../../upgrade/troubleshooting/maintenance-mode-options.md) argomento.

Utilizzo di Adobe Commerce e Magenti Open Source [modalità di manutenzione](../../configuration/bootstrap/application-modes.md#maintenance-mode) per disabilitare l&#39;avvio. La disattivazione dell&#39;avvio è utile durante la manutenzione, l&#39;aggiornamento o la riconfigurazione del sito.

L&#39;applicazione rileva la modalità di manutenzione come segue:

* Se `var/.maintenance.flag` non esiste, la modalità di manutenzione è disattivata e l&#39;applicazione funziona normalmente.
* In caso contrario, la modalità di manutenzione è attiva a meno che `var/.maintenance.ip` esiste.

   `var/.maintenance.ip` può contenere un elenco di indirizzi IP. Se si accede a un punto di ingresso tramite HTTP e l’indirizzo IP client corrisponde a una delle voci di tale elenco, la modalità di manutenzione è disattivata.

## Installare l’applicazione

Prima di utilizzare questo comando per attivare o disattivare la modalità di manutenzione, è necessario [installare l&#39;applicazione](../advanced.md).

## Attiva o disattiva la modalità di manutenzione

Utilizza la `magento maintenance` Comando CLI per attivare o disattivare la modalità di manutenzione.

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

La `--ip=<ip address>` è un indirizzo IP da escludere dalla modalità di manutenzione (ad esempio, gli sviluppatori che eseguono la manutenzione). Per esentare più di un indirizzo IP nello stesso comando, utilizza l’opzione più volte.

>[!NOTE]
>
>Utilizzo `--ip=<ip address>` con `magento maintenance:disable` salva l’elenco degli IP per un utilizzo successivo. Per cancellare l’elenco degli IP esentati, utilizza `magento maintenance:enable --ip=none` o consultare [Gestisci l&#39;elenco degli indirizzi IP esentati](#maintain-the-list-of-exempt-ip-addresses).

La `bin/magento maintenance:status` visualizza lo stato della modalità di manutenzione.

Ad esempio, per abilitare la modalità di manutenzione senza esenzioni per gli indirizzi IP:

```bash
bin/magento maintenance:enable
```

Per abilitare la modalità di manutenzione per tutti i clienti eccetto 192.0.2.10 e 192.0.2.11:

```bash
bin/magento maintenance:enable --ip=192.0.2.10 --ip=192.0.2.11
```

Dopo aver inserito l&#39;applicazione in modalità di manutenzione, è necessario arrestare tutti i processi consumer della coda messaggi.
Un modo per trovare questi processi è quello di eseguire il `ps -ef | grep queue:consumers:start` e quindi eseguire il comando `kill <process_id>` per ogni consumatore. In un ambiente a più nodi, ripeti questa attività su ciascun nodo.

## Gestisci l&#39;elenco degli indirizzi IP esentati

Per mantenere l’elenco degli indirizzi IP esentati, puoi utilizzare il `[--ip=<ip list>]` nei comandi precedenti oppure è possibile utilizzare quanto segue:

```bash
bin/magento maintenance:allow-ips <ip address> .. <ip address> [--none]
```

La `<ip address> .. <ip address>` La sintassi è un elenco facoltativo delimitato da spazi di indirizzi IP da esentare.

La `--none` cancella l’elenco.

## Configurazione di più store

Per impostare più store, ciascuno con un layout diverso e contenuti localizzati, crea uno skin per ciascuno di essi e inseriscilo in `pub/errors/{name}` dove `{name}` è il codice del negozio. Per distinguere tra negozi e siti web con la stessa istanza, utilizza `pub/errors/{type}-{name}` dove `{type}` è `store` o `website` e corrisponde al `MAGE_RUN_TYPE` nella configurazione del server.

Un&#39;altra opzione consiste nel trasmettere `$_GET['skin']` al processore previsto. Questo metodo richiede una configurazione specifica sul server.

Nell’esempio seguente, stiamo utilizzando un `503` Digitare un file modello di errore, che richiede contenuto localizzato.

Il costruttore del `Error_Processor` la classe accetta un `skin` Parametro GET per modificare il layout:

```php
if (isset($_GET['skin'])) {
    $this->_setSkin($_GET['skin']);
}
```

Può essere aggiunto anche a una regola di riscrittura nel `.htaccess` file che aggiunge un `skin` all&#39;URL.

### $_GET[&#39;skin&#39;] parameter

Per utilizzare `skin` parametro:

1. Controlla se la `.maintenance.flag` esiste.
1. Nota l&#39;indirizzo host, che fa riferimento al `HTTP_HOST`o qualsiasi altra variabile, come le variabili ENV.
1. Controlla se la `skin` parametro esistente.
1. Imposta il parametro utilizzando le regole di riscrittura riportate di seguito.

   Di seguito sono riportati alcuni esempi di regole di riscrittura:

   * RewriteCond `%{DOCUMENT_ROOT}/var/.maintenance.flag -f`
   * RewriteCond `%{HTTP_HOST} ^sub.example.com$`
   * RewriteCond `%{QUERY_STRING} !(^|&)skin=sub(&|$)` [NC]
   * RewriteRule `^ %{REQUEST_URI}?skin=sub` [L]

1. Copia i file seguenti:

   * `pub/errors/default/503.phtml` a `pub/errors/sub/503.phtml`
   * `pub/errors/default/css/styles.css` a `pub/errors/sub/styles.css`

1. Modifica questi file per fornire contenuto localizzato nel `503.phtml` file e stile personalizzato nella `styles.css` file.

   Assicurati che i percorsi puntino al tuo `errors` directory. Il nome della directory deve corrispondere al parametro URL indicato nel `RewriteRule`. Nell’esempio precedente, la variabile `sub` viene utilizzata, specificata come parametro nel `RewriteRule` (`skin=sub`)

>[!NOTE]
>
>La [nginx](../../configuration/multi-sites/ms-nginx.md) deve essere aggiunta per le impostazioni per più store.
