---
title: Visualizza o modifica l’URI amministratore
description: Segui questi passaggi per visualizzare e modificare l’URI dell’applicazione Adobe Commerce o Amministratore di Magento Open Source.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '106'
ht-degree: 0%

---


# Visualizza o modifica l’URI amministratore

Prima di eseguire questo comando, è necessario [Creare o aggiornare la configurazione della distribuzione](deployment.md).

## Visualizza l&#39;URI amministratore

Questa sezione illustra come utilizzare la riga di comando per visualizzare il [Amministratore](https://glossary.magento.com/admin) Identificatore risorsa uniforme ([URI](https://www.w3.org/Protocols/rfc2616/rfc2616-sec3.html#sec3.2)).

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
