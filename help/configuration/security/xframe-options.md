---
title: Impedisci sfruttare il clickjacking
description: Impedisci gli exploit di clickjacking utilizzando l’intestazione "X-Frame-Options" per controllare i rendering della pagina.
feature: Configuration, Security
exl-id: 83cf5fd2-3eb8-4bd9-99e2-1c701dcd1382
source-git-commit: 6cc04211fedddab68087bcf2f3603ae0403862b9
workflow-type: tm+mt
source-wordcount: '209'
ht-degree: 0%

---

# Impedisci sfruttare il clickjacking

Impedisci le attività di [Clickjacking](https://owasp.org/www-community/attacks/Clickjacking) includendo l&#39;intestazione di richiesta HTTP [X-Frame-Options](https://datatracker.ietf.org/doc/html/rfc7034) nelle richieste alla vetrina.

L&#39;intestazione `X-Frame-Options` consente di specificare se un browser può eseguire il rendering di una pagina in `<frame>`, `<iframe>` o `<object>` come segue:

- `DENY`: impossibile visualizzare la pagina in un frame.
- `SAMEORIGIN`: (predefinita) la pagina può essere visualizzata solo in un frame nella stessa origine della pagina stessa.

>[!WARNING]
>
>L&#39;opzione `ALLOW-FROM <uri>` è stata rimossa perché i browser supportati da Commerce non la supportano più. Vedi [Compatibilità browser](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility).

>[!WARNING]
>
>Per motivi di sicurezza, Adobe consiglia vivamente di non eseguire la vetrina Commerce in un frame.

## Implementa `X-Frame-Options`

Imposta un valore per `X-Frame-Options` in `<project-root>/app/etc/env.php`. Il valore predefinito è impostato come segue:

```php
'x-frame-options' => 'SAMEORIGIN',
```

Ridistribuisci per rendere effettive le modifiche al file `env.php`.

>[!TIP]
>
>È più sicuro modificare il file `env.php` che impostare un valore in Admin.

## Verifica l&#39;impostazione per `X-Frame-Options`

Per verificare l’impostazione, visualizza le intestazioni HTTP su qualsiasi pagina storefront. Sono disponibili diversi modi per eseguire questa operazione, incluso l’utilizzo di un controllo browser Web.

Nell&#39;esempio seguente viene utilizzato curl, che può essere eseguito da qualsiasi computer in grado di connettersi al server Commerce tramite il protocollo HTTP.

```bash
curl -I -v --location-trusted '<storefront-URL>'
```

Cerca il valore `X-Frame-Options` nelle intestazioni.
