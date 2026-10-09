---
title: Visualizzare o modificare l’URI amministratore
description: Per visualizzare e modificare l’URI dell’applicazione Adobe Commerce Admin, segui la procedura riportata di seguito.
feature: Install, Configuration
exl-id: 768f9ab4-7123-4460-9df8-a6c98ae55d95
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: 6388cf7b-8a81-5248-a1e4-7bb57bbe250f
    internal-label: Install
  - id: dac87252-6066-4d6e-a9d2-f6d84c323de7
    internal-label: Configuration
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
source-wordcount: '99'
ht-degree: 0%
---
# Visualizzare o modificare l’URI amministratore

Prima di eseguire questo comando, è necessario [creare o aggiornare la configurazione della distribuzione](deployment.md).

## Visualizza l&#39;URI amministratore

In questa sezione viene illustrato come utilizzare la riga di comando per visualizzare l&#39;identificatore di risorsa uniforme amministratore ([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)).

Opzioni comando:

```shell
bin/magento info:adminuri
```

Di seguito è riportato un esempio di risultato:

```text
Admin Panel URI: /admin_1wgrah
```

È inoltre possibile visualizzare l&#39;URI amministratore in `<magento_root>/app/etc/env.php`. Di seguito è riportato uno snippet:

```php?start_inline=1
  'backend' =>
  array (
    'frontName' => 'admin_1wgrah',
  ),
```

## Modificare l’URL dell’amministratore

Per modificare l&#39;URI amministratore, utilizzare il comando [`magento setup:config:set`](deployment.md).
