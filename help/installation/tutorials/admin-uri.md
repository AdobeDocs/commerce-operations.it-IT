---
title: Visualizza o modifica l’URI amministratore
description: Segui questi passaggi per visualizzare e modificare l’URI dell’applicazione Adobe Commerce o Amministratore di Magento Open Source.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '103'
ht-degree: 0%

---


# Visualizza o modifica l’URI amministratore

Prima di eseguire questo comando, è necessario [Creare o aggiornare la configurazione della distribuzione](deployment.md).

## Visualizza l&#39;URI amministratore

In questa sezione viene illustrato come utilizzare la riga di comando per visualizzare l’identificatore di risorsa uniforme dell’amministratore ([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)).

Opzioni di comando:

```bash
bin/magento info:adminuri
```

Segue un esempio di risultato:

```terminal
Admin Panel URI: /admin_1wgrah
```

Puoi anche visualizzare l’URI amministratore in `<magento_root>/app/etc/env.php`. Segue uno snippet:

```php?start_inline=1
  'backend' =>
  array (
    'frontName' => 'admin_1wgrah',
  ),
```

## Modificare l’URL amministratore

Per modificare l’URI di amministrazione, utilizza la variabile [`magento setup:config:set`](deployment.md) comando.
