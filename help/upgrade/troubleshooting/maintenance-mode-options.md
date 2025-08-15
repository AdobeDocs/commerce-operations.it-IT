---
title: Opzioni della modalità di manutenzione per l’aggiornamento
description: Crea una pagina personalizzata per la modalità di manutenzione che i clienti possono visualizzare nella vetrina di Adobe Commerce durante l’esecuzione di un aggiornamento.
exl-id: 77e6d82d-5cc6-4d14-8b5c-1d2108f27b29
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# Opzioni della modalità di manutenzione per l’aggiornamento

In questo argomento viene illustrato come creare una pagina di manutenzione personalizzata da visualizzare agli utenti durante l&#39;aggiornamento dell&#39;applicazione Magento. La creazione di una pagina personalizzata è facoltativa ma consigliata perché il sito è accessibile durante parte dell’aggiornamento.

La creazione di una pagina personalizzata a cui reindirizzare gli utenti impedisce l’accesso al sito e informa gli utenti che il sito è in fase di manutenzione.

>[!NOTE]
>
>È necessario eseguire le attività in questa sezione come utente con privilegi `root`. Impossibile impostare pagine di manutenzione personalizzate in modalità sviluppatore.

## Creare la pagina di manutenzione personalizzata

Per creare una pagina di manutenzione e reindirizzarla, crea innanzitutto una pagina di manutenzione denominata:

- Apache: `<web server docroot>/maintenance.html`
- indice: `<magento_root>/maintenance.html`

Aggiungi il seguente contenuto:

```html
<!DOCTYPE html>
<html>
<head>
<title>Temporarily Offline</title>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<style>
h1
{ font-size: 50px; }

body
{ text-align:center; font: 20px Helvetica, sans-serif; color: #333; }

</style>
</head>
<body>

# Temporarily offline

<p>We're down for a short time to perform maintenance on our site to give you the best possible experience. Check back soon!</p>
</body>
</html>
```

## Pagina di manutenzione personalizzata per Apache

Questa sezione illustra come creare una pagina di manutenzione personalizzata e come reindirizzare il traffico verso di essa.

L’esempio riportato in questa sezione mostra come modificare i seguenti file, il che rappresenta uno dei modi per impostare la pagina di manutenzione:

- Apache 2.4: `/etc/apache2/sites-available/000-default.conf`
- Apache 2.2: `/etc/apache2/sites-available/default` (Ubuntu), `/etc/httpd/conf/httpd.conf` (CentOS)

Per reindirizzare il traffico a una pagina di manutenzione personalizzata:

1. Aggiorna la configurazione di Apache per effettuare le seguenti operazioni:

   - Reindirizza tutto il traffico alla pagina di manutenzione
   - Inserire nell&#39;elenco Consentiti determinati IP in modo che un amministratore possa aggiornare il software Magento.

   Inserire nell&#39;elenco Consentiti L&#39;esempio seguente 192.0.2.110.

   Aggiungi quanto segue alla fine del file di configurazione Apache:

   ```
   RewriteEngine On
   RewriteCond %{REMOTE_ADDR} !^192\.0\.2\.110
   RewriteCond %{DOCUMENT_ROOT}/maintenance.html -f
   RewriteCond %{DOCUMENT_ROOT}/maintenance.enable -f
   RewriteCond %{SCRIPT_FILENAME} !maintenance.html
   RewriteRule ^.*$ /maintenance.html [R=503,L]
   ErrorDocument 503 /maintenance.html
   Header Set Cache-Control "max-age=0, no-store"
   ```

1. Riavvia Apache:

   - CentOS: `service httpd restart`
   - Ubuntu: `service apache2 restart`

1. Immetti il comando seguente:

   ```bash
   touch <web server docroot>/maintenance.enable
   ```

1. [Aggiorna il sistema](../implementation/perform-upgrade.md).
1. Verifica il sito per assicurarti che funzioni correttamente.
1. Al termine dell&#39;aggiornamento, eliminare `maintenance.enable`.

## Pagina di manutenzione personalizzata per l’indice

Questa sezione illustra come creare una pagina di manutenzione personalizzata e come reindirizzare il traffico verso di essa.

Per reindirizzare il traffico a una pagina di manutenzione personalizzata:

1. Utilizza un editor di testo per aprire il file di configurazione nginx che contiene il blocco server.
1. Aggiungere quanto segue al blocco del server (`server` viene visualizzato solo per chiarezza; non aggiungere un secondo blocco del server).

   I seguenti inseriscono nell&#39;elenco Consentiti l&#39;indirizzo IP 192.0.2.110 e 192.0.2.115 in un sistema in cui è installato Magento in `/var/www/html/magento2`:

   ```conf
   server {
        listen 80;
        set $MAGE_ROOT /var/www/html/magento2;
   
        set $maintenance off;
   
        if (-f $MAGE_ROOT/maintenance.enable) {
            set $maintenance on;
        }
   
        if ($remote_addr ~ (192.0.2.110|192.0.2.115)) {
            set $maintenance off;
        }
   
        if ($maintenance = on) {
            return 503;
        }
   
        location /maintenance {
        }
   
        error_page 503 @maintenance;
   
        location @maintenance {
        root $MAGE_ROOT;
        rewrite ^(.*)$ /maintenance.html break;
    }
   
        include /var/www/html/magento2/nginx.conf;
   }
   ```

1. Immetti il comando seguente:

   ```bash
   touch <magento_root>/maintenance.enable
   ```

1. Ricarica la configurazione nginx:

   ```bash
   service nginx reload
   ```

1. [Aggiorna il sistema](../implementation/perform-upgrade.md).
1. Verifica il sito per assicurarti che funzioni correttamente.
1. Al termine dell&#39;aggiornamento, eliminare o rinominare `maintenance.enable`
1. Ricarica la configurazione nginx:

   ```bash
   service nginx reload
   ```
