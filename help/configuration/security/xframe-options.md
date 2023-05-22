---
title: Intestazione X-Frame-Options
description: Utilizza X-Frame-Options per controllare i rendering delle pagine.
feature: Configuration, Security
exl-id: 83cf5fd2-3eb8-4bd9-99e2-1c701dcd1382
source-git-commit: 56a2461edea2799a9d569bd486f995b0fe5b5947
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Intestazione X-Frame-Options

Per prevenire [Clickjacking](https://owasp.org/www-community/attacks/Clickjacking) exploit, è stata aggiunta un’opzione per utilizzare il [X-Frame-Options](https://datatracker.ietf.org/doc/html/rfc7034) Intestazione della richiesta HTTP nelle richieste alla vetrina.

Il `X-Frame-Options` consente di specificare se un browser deve essere autorizzato a eseguire il rendering di una pagina in un `<frame>`, `<iframe>`, o `<object>` come segue:

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
