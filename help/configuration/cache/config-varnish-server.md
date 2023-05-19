---
title: Configurare il server web
description: Scopri come configurare il server web per l’utilizzo di Vernice.
exl-id: b31179ef-3c0e-4a6b-a118-d3be1830ba4e
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---

# Configurare il server web

Configurare il server Web per l&#39;ascolto su una porta diversa da quella predefinita 80, in quanto Vernice risponde direttamente alle richieste HTTP in ingresso, non al server Web.

Le sezioni seguenti utilizzano la porta 8080 come esempio.

**Per modificare la porta di ascolto di Apache 2.4**:

1. Apri `/etc/httpd/conf/httpd.conf` in un editor di testo.
1. Individua il `Listen` direttiva.
1. Modifica il valore della porta di ascolto in `8080`. È possibile utilizzare qualsiasi porta di ascolto disponibile.
1. Salva le modifiche apportate a `httpd.conf` ed esci dall’editor di testo.

## Modificare la configurazione del sistema di vernice

Per modificare la configurazione del sistema di vernice:

1. Come utente con `root` , apri il file di configurazione Vanish in un editor di testo:

   - CentOS 6: `/etc/sysconfig/varnish`
   - CentOS 7: `/etc/varnish/varnish.params`
   - Debian: `/etc/default/varnish`
   - Ubuntu: `/etc/default/varnish`

1. Impostare la porta di ascolto Vernice su 80:

   ```conf
   VARNISH_LISTEN_PORT=80
   ```

   Per la vernice 4.x, assicurarsi che DAEMON_OPTS contenga la porta di ascolto corretta per `-a` (anche se VARNISH_LISTEN_PORT è impostato sul valore corretto):

   ```conf
   DAEMON_OPTS="-a :80 \
      -T localhost:6082 \
      -f /etc/varnish/default.vcl \
      -S /etc/varnish/secret \
      -s malloc,256m"
   ```

1. Salvate le modifiche nel file di configurazione Vernice e uscite dall&#39;editor di testo.

### Modificare la VCL di default

Questa sezione illustra come fornire una configurazione minima in modo che Varish restituisca le intestazioni di risposta HTTP. Questo consente di verificare che la vernice funzioni prima di configurare [!DNL Commerce] applicazione per l’uso di vernice.

Per configurare la vernice in modo minimo:

1. Backup `default.vcl`:

   ```bash
   cp /etc/varnish/default.vcl /etc/varnish/default.vcl.bak
   ```

1. Apri `/etc/varnish/default.vcl` in un editor di testo.
1. Individua la seguente stanza:

   ```conf
   backend default {
       .host = "127.0.0.1";
       .port = "80";
   }
   ```

1. Sostituisci il valore di `.host` con il nome host o l&#39;indirizzo IP completo e la porta di ascolto della vernice _backend_ o _server di origine_ ovvero il server che fornisce il contenuto Vernice accelera.

   In genere, si tratta del server web. Consulta [Server back-end](https://varnish-cache.org/docs/trunk/users-guide/vcl-backends.html) nel _Guida alla vernice_.

1. Sostituisci il valore di `.port` con la porta di ascolto del server web (8080 in questo esempio).

   Esempio: Apache è installato sull’host 192.0.2.55 e Apache è in ascolto sulla porta 8080:

   ```conf
   backend default {
       .host = "192.0.2.55";
       .port = "8080";
   }
   ```

   >[!INFO]
   >
   >Se Vernice e Apache sono in esecuzione sullo stesso host, l’Adobe consiglia di utilizzare un indirizzo IP o un nome host e non `localhost`.

1. Salva le modifiche apportate a `default.vcl` ed esci dall’editor di testo.

1. Vernice di riavvio:

   ```bash
   service varnish restart
   ```

Se l&#39;avvio di Varning non riesce, provare a eseguirlo dalla riga di comando nel modo seguente:

```bash
varnishd -d -f /etc/varnish/default.vcl
```

Dovrebbero essere visualizzati messaggi di errore.


>[!INFO]
>
>Se Vernice non si avvia come servizio, è necessario configurare le regole SELinux per consentirne l&#39;esecuzione.

## Verifica che la vernice funzioni

Le sezioni seguenti spiegano come verificare che Varnish funzioni, ma _senza_ configurazione di Commerce per utilizzarlo. Prova prima di configurare Commerce.

Eseguire i task descritti nelle sezioni seguenti nell&#39;ordine indicato:

- [Inizia vernice](#start-varnish)
- [&#39;netstat&#39;](#netstat)

### Inizia vernice

Immetti: `service varnish start`

Se Varnish non si avvia come servizio, inizialo dalla riga di comando come segue:

1. Avvia CLI vernice:

   ```bash
   varnishd -d -f /etc/varnish/default.vcl
   ```

1. Avviare il processo di produzione di vernice:

   Quando richiesto, immetti `start`

   Per confermare un avvio riuscito, vengono visualizzati i seguenti messaggi:

   ```terminal
   child (29805) Started
   200 0
   
   Child (29805) said
   Child (29805) said Child starts
   ```

### netstat

Accedere al server Vernice e immettere il comando seguente:

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

Il precedente mostra la Vernice che corre sulla porta 80 e l&#39;Apache che sulla porta 8080.

Se non vedi l’output per `varnishd`, accertarsi che Vernice sia in esecuzione.

Consulta [`netstat` opzioni](https://tldp.org/LDP/nag2/x-087-2-iface.netstat.html).

## Installare il software Commerce

Installa il software Commerce, se non lo hai già fatto. Quando viene richiesto un URL di base, utilizzare l&#39;host e la porta 80 di Varnish (per Varnish) perché quest&#39;ultimo riceve tutte le richieste HTTP in entrata.

Possibile errore durante l’installazione di Commerce:

```terminal
Error 503 Service Unavailable
Service Unavailable
XID: 303394517
Varnish cache server
```

Se si verifica questo errore, modificare `default.vcl` e aggiungi un timeout al `backend` strofa come segue:

```conf
backend default {
   .host = "127.0.0.1";
   .port = "8080";
   .first_byte_timeout = 600s;
}
```

## Verificare le intestazioni di risposta HTTP

Ora è possibile verificare che Vernice distribuisca le pagine osservando le intestazioni di risposta dei HTML restituite da qualsiasi pagina.

Prima di poter esaminare le intestazioni, è necessario impostare Commerce per la modalità sviluppatore. Esistono diversi modi per farlo, il più semplice dei quali è modificare `.htaccess` nella directory principale dell’applicazione Commerce. È inoltre possibile utilizzare [`magento deploy:mode:set`](../cli/set-mode.md) comando.

### Impostare Commerce per la modalità sviluppatore

Per impostare Commerce per la modalità sviluppatore, utilizza [`magento deploy:mode:set`](../cli/set-mode.md#change-to-developer-mode) comando.

### Guardate il registro vernice

Verificare che Varnish sia in esecuzione, quindi immettere il seguente comando sul server di Varnish:

```bash
varnishlog
```

In un browser web, vai a qualsiasi pagina di Commerce.

Nella finestra del prompt dei comandi viene visualizzato un lungo elenco di intestazioni di risposta. Cerca intestazioni come le seguenti:

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

Se le intestazioni come queste lo fanno _non_ visualizzare, arrestare Vernice, controllare `default.vcl`e riprova.

### Esaminare le intestazioni di risposta di HTML

Esistono diversi modi per esaminare le intestazioni di risposta, incluso l’utilizzo di un plug-in del browser o di un controllo del browser.

L’esempio che segue utilizza `curl`. Puoi immettere questo comando da qualsiasi computer in grado di accedere al server Commerce utilizzando HTTP.

```bash
curl -I -v --location-trusted '<your Commerce base URL>'
```

Ad esempio:

```bash
curl -I -v --location-trusted 'http://192.0.2.55/magento2'
```

Cerca intestazioni come le seguenti:

```terminal
Content-Type: text/html; charset=iso-8859-1
X-Varnish: 15
Age: 0
Via: 1.1 varnish-v6
X-Magento-Cache-Debug: HIT
```
