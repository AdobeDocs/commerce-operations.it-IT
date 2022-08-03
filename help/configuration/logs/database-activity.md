---
title: Attività del database di log
description: Configura Commerce per registrare l’attività del database utilizzando l’interfaccia Logger .
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---


# Attività del database di log

L’esempio seguente mostra come registrare l’attività del database utilizzando [`Magento\Framework\DB\LoggerInterface`][interface], che dispone di due implementazioni:

- Nessun registro (predefinito): [`Magento\Framework\DB\Logger\Quiet`][quiet]
- Accessi a `var/log` directory: [`Magento\Framework\DB\Logger\File`][file]

>[!TIP]
>
>Puoi utilizzare Commerce CLI per [abilitare e disabilitare la registrazione del database](../cli/enable-logging.md#database-logging).

Per modificare la configurazione predefinita di `\Magento\Framework\DB\Logger\LoggerProxy`, modifica il `app/etc/di.xml`.

Innanzitutto, modifica i valori predefiniti di `loggerAlias` e `logCallStack` argomenti a favore:

```xml
<type name="Magento\Framework\DB\Logger\LoggerProxy">
    <arguments>
        <argument name="loggerAlias" xsi:type="const">Magento\Framework\DB\Logger\LoggerProxy::LOGGER_ALIAS_FILE</argument>
        <argument name="logAllQueries" xsi:type="init_parameter">Magento\Framework\Config\ConfigOptionsListConstants::CONFIG_PATH_DB_LOGGER_LOG_EVERYTHING</argument>
        <argument name="logQueryTime" xsi:type="init_parameter">Magento\Framework\Config\ConfigOptionsListConstants::CONFIG_PATH_DB_LOGGER_QUERY_TIME_THRESHOLD</argument>
        <argument name="logCallStack" xsi:type="boolean">false</argument>
    </arguments>
</type>
```

Dopo di che, fornisci il percorso del file per `Magento\Framework\DB\Logger\File`:

```xml
<type name="Magento\Framework\DB\Logger\File">
    <arguments>
        <argument name="debugFile" xsi:type="string">log/db.log</argument>
    </arguments>
</type>
```

Infine, compila il codice con:

```bash
bin/magento setup:di:compile
```

E pulisci la cache con:

```bash
bin/magento cache:clean
```

<!-- link definitions -->

[file]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/Logger/File.php
[interface]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/LoggerInterface.php
[quiet]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/DB/Logger/Quiet.php
