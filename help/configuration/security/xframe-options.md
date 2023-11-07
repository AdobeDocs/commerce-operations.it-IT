---
title: Impedisci sfruttare il clickjacking
description: Impedisci gli exploit di clickjacking utilizzando l’intestazione "X-Frame-Options" per controllare i rendering della pagina.
feature: Configuration, Security
exl-id: 83cf5fd2-3eb8-4bd9-99e2-1c701dcd1382
source-git-commit: 6cc04211fedddab68087bcf2f3603ae0403862b9
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# Impedisci sfruttare il clickjacking

Previeni [Clickjacking](https://owasp.org/www-community/attacks/Clickjacking) sfruttare includendo [X-Frame-Options](https://datatracker.ietf.org/doc/html/rfc7034) Intestazione della richiesta HTTP nelle richieste alla vetrina.

Il `X-Frame-Options` intestazione consente di specificare se un browser può eseguire il rendering di una pagina in un `<frame>`, `<iframe>`, o `<object>` come segue:

- `DENY`: la pagina non può essere visualizzata in un frame.
- `SAMEORIGIN`: (impostazione predefinita) la pagina può essere visualizzata solo in un frame sulla stessa origine della pagina stessa.

>[!WARNING]
>
>Il `ALLOW-FROM <uri>` L’opzione è stata rimossa perché non è più supportata dai browser supportati da Commerce. Consulta [Compatibilità browser](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility).

>[!WARNING]
>
>Per motivi di sicurezza, Adobe consiglia vivamente di non eseguire la vetrina Commerce in un frame.

## Implementare `X-Frame-Options`

Imposta un valore per `X-Frame-Options` in `<project-root>/app/etc/env.php`. Il valore predefinito è impostato come segue:

```php
'x-frame-options' => 'SAMEORIGIN',
```

Ridistribuisci per qualsiasi modifica apportata a `env.php` per rendere effettivo il file.

>[!TIP]
>
>È più sicuro modificare `env.php` di un file per impostare un valore in Admin.

## Verifica l’impostazione per `X-Frame-Options`

Per verificare l’impostazione, visualizza le intestazioni HTTP su qualsiasi pagina storefront. Sono disponibili diversi modi per eseguire questa operazione, incluso l’utilizzo di un controllo browser Web.

L’esempio seguente utilizza curl, che può essere eseguito da qualsiasi computer in grado di connettersi al server Commerce tramite il protocollo HTTP.

```bash
curl -I -v --location-trusted '<storefront-URL>'
```

Cerca `X-Frame-Options` nelle intestazioni.
