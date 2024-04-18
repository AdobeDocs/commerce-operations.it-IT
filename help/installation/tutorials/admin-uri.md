---
title: Visualizzare o modificare l’URI amministratore
description: Per visualizzare e modificare l’URI dell’applicazione Adobe Commerce Admin, segui la procedura riportata di seguito.
feature: Install, Configuration
exl-id: 768f9ab4-7123-4460-9df8-a6c98ae55d95
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '91'
ht-degree: 0%

---

# Visualizzare o modificare l’URI amministratore

Prima di eseguire questo comando, è necessario [Creare o aggiornare la configurazione della distribuzione](deployment.md).

## Visualizza l&#39;URI amministratore

Questa sezione illustra come utilizzare la riga di comando per visualizzare l&#39;identificatore di risorsa uniforme amministratore ([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)).

Opzioni comando:

```bash
bin/magento info:adminuri
```

Di seguito è riportato un esempio di risultato:

```terminal
Admin Panel URI: /admin_1wgrah
```

Puoi anche visualizzare l’URI amministratore in `<magento_root>/app/etc/env.php`. Di seguito è riportato uno snippet:

```php?start_inline=1
  'backend' =>
  array (
    'frontName' => 'admin_1wgrah',
  ),
```

## Modificare l’URL dell’amministratore

Per modificare l’URI di amministrazione, utilizza [`magento setup:config:set`](deployment.md) comando.
