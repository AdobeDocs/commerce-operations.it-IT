---
title: Intestazione X-Frame-Options
description: Utilizza le opzioni X-Frame per controllare i rendering delle pagine.
source-git-commit: db696b8ca501d128db655c5ebb161c654c6378a7
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---


# Intestazione X-Frame-Options

Per evitare [Clickjacking](https://owasp.org/www-community/attacks/Clickjacking) viene aggiunta un’opzione per utilizzare [Opzioni X-Frame](https://datatracker.ietf.org/doc/html/rfc7034) intestazione di richiesta HTTP nelle richieste alla vetrina.

La `X-Frame-Options` L’intestazione consente di specificare se un browser deve essere autorizzato a eseguire il rendering di una pagina in un `<frame>`, `<iframe>`oppure `<object>` come segue:

- `DENY`: Impossibile visualizzare la pagina in un frame.
- `SAMEORIGIN`: (Impostazione predefinita) La pagina può essere visualizzata solo in un frame nella stessa origine della pagina stessa.

>[!WARNING]
>
>La `ALLOW-FROM <uri>` Questa opzione è stata rimossa perché non è più supportata dai browser supportati da Commerce. Vedi [Compatibilità del browser](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility).

>[!WARNING]
>
>Per motivi di sicurezza, Adobe consiglia vivamente di non eseguire la vetrina Commerce in un frame.

## Implementare `X-Frame-Options`

Imposta un valore per `X-Frame-Options` in `<project-root>/app/etc/env.php`. Il valore predefinito viene impostato come segue:

```php
'x-frame-options' => 'SAMEORIGIN',
```

Ridistribuisci per eventuali modifiche al `env.php` per rendere effettivo il file.

>[!TIP]
>
>È più sicuro modificare il `env.php` per impostare un valore in Admin.

## Verifica l’impostazione per `X-Frame-Options`

Per verificare l’impostazione, visualizza le intestazioni HTTP su qualsiasi pagina della vetrina. Sono disponibili diversi modi per eseguire questa operazione, tra cui l’utilizzo di un ispettore del browser Web.

Nell&#39;esempio seguente viene utilizzato curl, eseguibile da qualsiasi computer in grado di connettersi al server Commerce tramite il protocollo HTTP.

```bash
curl -I -v --location-trusted '<storefront-URL>'
```

Cerca la `X-Frame-Options` nelle intestazioni.
