---
title: Esporta impostazioni di configurazione
description: Esporta le impostazioni di configurazione di Adobe Commerce nei file di configurazione, noti anche come dump di configurazione.
exl-id: db680f5e-547a-48f3-b017-d77b8cb07bfd
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '204'
ht-degree: 0%

---

# Esporta impostazioni di configurazione

In Commerce 2.2 e versioni successive del [modello di distribuzione della pipeline](../deployment/technical-details.md), è possibile mantenere una configurazione coerente tra i sistemi. Dopo aver configurato le impostazioni in Admin sul sistema di sviluppo, esportale nei file di configurazione utilizzando il comando seguente:

```bash
bin/magento app:config:dump {config-types}
```

_config_types_ è un elenco separato da spazi dei tipi di configurazione da scaricare. I tipi disponibili sono `scopes`, `system`, `themes` e `i18n`. Se non viene specificato alcun tipo di configurazione, vengono sottoposte a dump tutte le informazioni di configurazione del sistema.

L’esempio seguente esegue il dump solo di ambiti e temi:

```bash
bin/magento app:config:dump scopes themes
```

A seguito dell’esecuzione del comando, vengono aggiornati i seguenti file di configurazione:

- `app/etc/config.php`

  Questo è il file di configurazione condiviso per tutte le istanze di Commerce.
Includi questo elemento nel controllo del codice sorgente in modo che possa essere condiviso tra i sistemi di sviluppo, generazione e produzione.

  Vedi [riferimento config.php](../reference/config-reference-configphp.md).

- `app/etc/env.php`

  Si tratta del file di configurazione specifico per l’ambiente.
Contiene impostazioni sensibili e specifiche per il sistema per singoli ambienti.

  _non_ includere il file nel controllo del codice sorgente.

  Vedi [riferimento env.php](../reference/config-reference-envphp.md).

## Impostazioni sensibili o specifiche del sistema

Per impostare le impostazioni sensibili scritte in `env.php`, utilizzare il comando [`bin/magento config:sensitive:set`](set-configuration-values.md#set-values).

I valori di configurazione sono specificati come sensibili o specifici del sistema facendo riferimento a [`Magento\Config\Model\Config\TypePool`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Config/Model/Config/TypePool.php) nel file [`di.xml`](https://developer.adobe.com/commerce/php/development/configuration/sensitive-environment-settings/#how-to-specify-values-as-sensitive-or-system-specific) del modulo.

Per esportare impostazioni di sistema aggiuntive quando si utilizza `config_types`, provare a utilizzare il comando [`bin/magento config:set`](set-configuration-values.md#set-values).
