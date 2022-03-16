---
title: Opzioni della modalità di manutenzione per l'aggiornamento
description: 'Crea una pagina in modalità di manutenzione personalizzata che i clienti visualizzano sulla vetrina Adobe Commerce o Magenti Open Source durante l’esecuzione di un aggiornamento. '
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---


# Opzioni della modalità di manutenzione per l&#39;aggiornamento

Questo argomento illustra come creare una pagina di manutenzione personalizzata da visualizzare agli utenti durante l’aggiornamento dell’applicazione del Magento. La creazione di una pagina personalizzata è facoltativa ma consigliata perché il sito è accessibile durante una parte dell’aggiornamento.

La creazione di una pagina personalizzata a cui reindirizzare gli utenti impedisce qualsiasi accesso al sito e informa gli utenti che il sito è in fase di manutenzione.

>[!NOTE]
>
>È necessario eseguire le attività di questa sezione come utente con `root` privilegi. Impossibile impostare pagine di manutenzione personalizzate in modalità sviluppatore.

## Creare la pagina di manutenzione personalizzata

Per creare una pagina di manutenzione ed effettuare il reindirizzamento, crea innanzitutto una pagina di manutenzione denominata:

- Apache: `<web server docroot>/maintenance.html`
- nginx: `<magento_root>/maintenance.html`

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

L&#39;esempio di questa sezione mostra come modificare i file seguenti, che è uno dei modi per impostare la pagina di manutenzione:

- Apache 2.4: `/etc/apache2/sites-available/000-default.conf`
- Apache 2.2: `/etc/apache2/sites-available/default` (Ubuntu), `/etc/httpd/conf/httpd.conf` (CentOS)

Per reindirizzare il traffico a una pagina di manutenzione personalizzata:

1. Aggiorna la configurazione Apache per effettuare le seguenti operazioni:

   - Reindirizza tutto il traffico alla pagina di manutenzione
   - Inserire nell&#39;elenco Consentiti alcuni IP in modo che un amministratore possa aggiornare il software di Magento.

   L’esempio seguente inserire nell&#39;elenco Consentiti 192.0.2.110.

   Aggiungi quanto segue alla fine del file di configurazione Apache:

   ```terminal
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

1. Immetti il seguente comando:

   ```bash
   touch <web server docroot>/maintenance.enable
   ```

1. [Aggiornare il sistema](../implementation/perform-upgrade.md).
1. Verifica che il sito funzioni correttamente.
1. Al termine dell’aggiornamento, elimina `maintenance.enable`.

## Pagina di manutenzione personalizzata per l&#39;allegato

Questa sezione illustra come creare una pagina di manutenzione personalizzata e come reindirizzare il traffico verso di essa.

Per reindirizzare il traffico a una pagina di manutenzione personalizzata:

1. Utilizza un editor di testo per aprire [nginx](https://glossary.magento.com/nginx) file di configurazione che contiene il blocco del server.
1. Aggiungi quanto segue al blocco del server (`server` è indicato solo a fini di chiarezza; non aggiungere un secondo blocco server).

   I seguenti inseriscono nell&#39;elenco Consentiti gli indirizzi IP 192.0.2.110 e 192.0.2.115 su un sistema in cui è installato il Magento in `/var/www/html/magento2`:

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

1. Immetti il seguente comando:

   ```bash
   touch <magento_root>/maintenance.enable
   ```

1. Ricarica la configurazione dell&#39;nginx:

   ```bash
   service nginx reload
   ```

1. [Aggiornare il sistema](../implementation/perform-upgrade.md).
1. Verifica che il sito funzioni correttamente.
1. Al termine dell’aggiornamento, elimina o rinomina `maintenance.enable`
1. Ricarica la configurazione dell&#39;nginx:

   ```bash
   service nginx reload
   ```
