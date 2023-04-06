---
title: Configurare il server web
description: Scopri come configurare il server web in modo che funzioni con Varnish.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---


# Configurare il server web

Configura il tuo server web per ascoltare su una porta diversa da quella predefinita 80 perché Varnish risponde direttamente alle richieste HTTP in arrivo, non al server web.

Le sezioni seguenti utilizzano la porta 8080 come esempio.

**Per modificare la porta di ascolto Apache 2.4**:

1. Apri `/etc/httpd/conf/httpd.conf` in un editor di testo.
1. Individua il `Listen` direttiva.
1. Modifica il valore della porta di ascolto in `8080`. È possibile utilizzare qualsiasi porta di ascolto disponibile.
1. Salva le modifiche in `httpd.conf` e esci dall’editor di testo.

## Modificare la configurazione del sistema Varnish

Per modificare la configurazione del sistema Varnish:

1. Come utente con `root` privilegi, apri il file di configurazione Vanish in un editor di testo:

   - CentOS 6: `/etc/sysconfig/varnish`
   - CentOS 7: `/etc/varnish/varnish.params`
   - Debian: `/etc/default/varnish`
   - Ubuntu: `/etc/default/varnish`

1. Imposta la porta di ascolto Varnish su 80:

   ```conf
   VARNISH_LISTEN_PORT=80
   ```

   Per Varnish 4.x, assicurati che DAEMON_OPTS contenga la porta di ascolto corretta per `-a` (anche se VARNISH_LISTEN_PORT è impostato sul valore corretto):

   ```conf
   DAEMON_OPTS="-a :80 \
      -T localhost:6082 \
      -f /etc/varnish/default.vcl \
      -S /etc/varnish/secret \
      -s malloc,256m"
   ```

1. Salva le modifiche nel file di configurazione Varnish e esci dall’editor di testo.

### Modificare la VCL predefinita

Questa sezione illustra come fornire una configurazione minima in modo che Varnish restituisca intestazioni di risposta HTTP. Questo ti consente di verificare che Varnish funzioni prima di configurare il [!DNL Commerce] applicazione per utilizzare Varnish.

Per configurare in modo minimo la vernice:

1. Backup `default.vcl`:

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak
   ```

1. Apri `/etc/varnish/default.vcl` in un editor di testo.
1. Individua la seguente strofa:

   ```conf
   backend default {
       .host = "127.0.0.1";
       .port = "80";
   }
   ```

1. Sostituisci il valore di `.host` con l&#39;hostname o l&#39;indirizzo IP completo e il porto di ascolto della Varnish _backend_ o _server di origine_; cioè, il server che fornisce il contenuto Varnish accelererà.

   In genere, si tratta del server web. Vedi [Server back-end](https://varnish-cache.org/docs/trunk/users-guide/vcl-backends.html) in _Guida alla vernice_.

1. Sostituisci il valore di `.port` con la porta di ascolto del server web (8080 in questo esempio).

   Esempio: Apache è installato sull&#39;host 192.0.2.55 e Apache è in ascolto sulla porta 8080:

   ```conf
   backend default {
       .host = "192.0.2.55";
       .port = "8080";
   }
   ```

   >[!INFO]
   >
   >Se Varnish e Apache sono in esecuzione sullo stesso host, Adobe consiglia di utilizzare un indirizzo IP o un nome host e non `localhost`.

1. Salva le modifiche in `default.vcl` e esci dall’editor di testo.

1. Riavvia vernice:

   ```bash
   service varnish restart
   ```

Se l&#39;avvio di Varnish non riesce, provate a eseguirlo dalla riga di comando come segue:

```bash
varnishd -d -f /etc/varnish/default.vcl
```

Dovrebbe essere visualizzato un messaggio di errore.


>[!INFO]
>
>Se Varnish non si avvia come servizio, è necessario configurare le regole SELinux per consentirne l&#39;esecuzione.

## Verifica che Varnish funzioni

Nelle sezioni seguenti viene illustrato come verificare che Varnish funzioni ma _senza_ configurazione di Commerce per utilizzarlo. Prova questo prima di configurare Commerce.

Esegui le operazioni descritte nelle sezioni seguenti nell’ordine mostrato:

- [Inizia vernice](#start-varnish)
- [&quot;netstat&quot;](#netstat)

### Inizia vernice

Inserisci: `service varnish start`

Se Varnish non si avvia come servizio, avviarlo dalla riga di comando come segue:

1. Avvia l&#39;interfaccia CLI di Varnish:

   ```bash
   varnishd -d -f /etc/varnish/default.vcl
   ```

1. Avviare il processo figlio Vernish:

   Quando richiesto, immetti `start`

   Vengono visualizzati i seguenti messaggi per confermare l’avvio corretto:

   ```terminal
   child (29805) Started
   200 0
   
   Child (29805) said
   Child (29805) said Child starts
   ```

### netstat

Accedi al server Varnish e immetti il seguente comando:

```bash
netstat -tulpn
```

Cerca in particolare il seguente output:

```terminal
tcp        0      0 0.0.0.0:80                  0.0.0.0:*                   LISTEN      32614/varnishd
tcp        0      0 127.0.0.1:58484             0.0.0.0:*                   LISTEN      32604/varnishd
tcp        0      0 :::8080                     :::*                        LISTEN      26822/httpd
tcp        0      0 ::1:48509                   :::*                        LISTEN      32604/varnishd
```

Il precedente mostra Varnish in esecuzione sulla porta 80 e Apache in esecuzione sulla porta 8080.

Se non visualizzi l&#39;output per `varnishd`Assicurati che Varnish sia in funzione.

Vedi [`netstat` options](https://tldp.org/LDP/nag2/x-087-2-iface.netstat.html).

## Installare il software Commerce

Se non lo hai già fatto, installa il software Commerce. Quando viene richiesto un URL di base, utilizza l&#39;host Varnish e la porta 80 (per Varnish) perché Varnish riceve tutte le richieste HTTP in ingresso.

Possibile errore durante l&#39;installazione di Commerce:

```terminal
Error 503 Service Unavailable
Service Unavailable
XID: 303394517
Varnish cache server
```

Se si verifica questo errore, modifica `default.vcl` e aggiungi un timeout al `backend` strofa come segue:

```conf
backend default {
   .host = "127.0.0.1";
   .port = "8080";
   .first_byte_timeout = 600s;
}
```

## Verificare le intestazioni di risposta HTTP

Ora puoi verificare che Varnish stia servendo le pagine guardando le intestazioni di risposta di HTML restituite da qualsiasi pagina.

Prima di poter esaminare le intestazioni, è necessario impostare Commerce per la modalità sviluppatore. Ci sono diversi modi per farlo, il più semplice dei quali è quello di modificare `.htaccess` nella directory principale dell’applicazione Commerce. È inoltre possibile utilizzare [`magento deploy:mode:set`](../cli/set-mode.md) comando.

### Impostare Commerce per la modalità sviluppatore

Per impostare Commerce per la modalità sviluppatore, utilizza la funzione [`magento deploy:mode:set`](../cli/set-mode.md#change-to-developer-mode) comando.

### Guarda il registro di Varnish

Assicurati che Varnish sia in esecuzione, quindi inserisci il seguente comando sul server Vernish:

```bash
varnishlog
```

In un browser web, vai a qualsiasi pagina Commerce.

Nella finestra del prompt dei comandi viene visualizzato un lungo elenco di intestazioni di risposta. Cerca intestazioni come quelle seguenti:

```terminal
-   BereqHeader    X-Varnish: 3
-   VCL_call       BACKEND_FETCH
-   VCL_return     fetch
-   BackendOpen    17 default(10.249.151.10,,8080) 10.249.151.10 60914
-   Backend        17 default(10.249.151.10,,8080)
-   Timestamp      Bereq: 1440449534.261791 0.000618 0.000618
-   ReqHeader      Host: 10.249.151.10
-   ReqHeader      Connection: keep-alive
-   ReqHeader      Content-Length: 86
-   ReqHeader      Cache-Control: max-age=0
-   ReqHeader      Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
-   ReqHeader      Origin: http://10.249.151.10
```

Se intestazioni come queste lo fanno _not_ display, stop Varnish, controlla il tuo `default.vcl`e riprova.

### Osserva le intestazioni di risposta di HTML

Esistono diversi modi per esaminare le intestazioni di risposta, tra cui l&#39;utilizzo di un plug-in per browser o di un ispettore del browser.

Nell&#39;esempio seguente viene utilizzato `curl`. È possibile immettere questo comando da qualsiasi computer in grado di accedere al server Commerce utilizzando HTTP.

```bash
curl -I -v --location-trusted '<your Commerce base URL>'
```

Ad esempio:

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

Cerca intestazioni come quelle seguenti:

```terminal
Content-Type: text/html; charset=iso-8859-1
X-Varnish: 15
Age: 0
Via: 1.1 varnish-v6
X-Magento-Cache-Debug: HIT
```
