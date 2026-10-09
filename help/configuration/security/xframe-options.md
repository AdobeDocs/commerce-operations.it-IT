---
title: Impedisci sfruttare il clickjacking
description: Impedisci gli exploit di clickjacking utilizzando l’intestazione "X-Frame-Options" per controllare i rendering della pagina.
feature: Configuration, Security
exl-id: 83cf5fd2-3eb8-4bd9-99e2-1c701dcd1382
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
  - id: ba9e5be9-7de1-4f71-a5d2-baead0e425ee
    internal-label: Security
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '234'
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

```shell
curl -I -v --location-trusted '<storefront-URL>'
```

Cerca il valore `X-Frame-Options` nelle intestazioni.
