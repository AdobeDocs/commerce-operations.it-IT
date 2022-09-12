---
title: Esporta impostazioni di configurazione
description: Esporta le impostazioni di configurazione di Adobe Commerce in file di configurazione, noti anche come dump di configurazione.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '222'
ht-degree: 0%

---


# Esporta impostazioni di configurazione

In Commerce 2.2 e versioni successive [modello di distribuzione della pipeline](../deployment/technical-details.md), puoi mantenere una configurazione coerente tra i diversi sistemi. Dopo aver configurato le impostazioni in Admin nel sistema di sviluppo, esportale tali impostazioni in file di configurazione utilizzando il seguente comando:

```bash
bin/magento app:config:dump {config-types}
```

_config_types_ è un elenco separato da spazi dei tipi di configurazione da scaricare. I tipi disponibili includono `scopes`, `system`, `themes`e `i18n`. Se non viene specificato alcun tipo di configurazione, il comando scarica tutte le informazioni di configurazione del sistema.

L&#39;esempio seguente scarica solo ambiti e temi:

```bash
bin/magento app:config:dump scopes themes
```

A seguito dell&#39;esecuzione del comando, vengono aggiornati i seguenti file di configurazione:

- `app/etc/config.php`

   Si tratta del file di configurazione condiviso per tutte le istanze Commerce.
Includilo nel controllo del codice sorgente in modo che possa essere condiviso tra i sistemi di sviluppo, generazione e produzione.

   Vedi [riferimento config.php](../reference/config-reference-configphp.md).

- `app/etc/env.php`

   Si tratta del file di configurazione specifico per l’ambiente.
Contiene impostazioni sensibili e specifiche del sistema per i singoli ambienti.

   Do _not_ includere questo file nel controllo del codice sorgente.

   Vedi [riferimento env.php](../reference/config-reference-envphp.md).

## Impostazioni sensibili o specifiche del sistema

Per impostare le impostazioni sensibili scritte in `env.php`, utilizza [`bin/magento config:sensitive:set`](set-configuration-values.md#set-values) comando.

I valori di configurazione sono specificati come sensibili o specifici del sistema facendo riferimento a [`Magento\Config\Model\Config\TypePool`](https://github.com/magento/magento2/blob/2.4/app/code/Magento/Config/Model/Config/TypePool.php) nel modulo [`di.xml`](https://developer.adobe.com/commerce/php/development/configuration/sensitive-environment-settings/#how-to-specify-values-as-sensitive-or-system-specific) file.

Per esportare impostazioni di sistema aggiuntive durante l&#39;utilizzo `config_types`, considera l&#39;utilizzo di [`bin/magento config:set`](set-configuration-values.md#set-values) comando.
