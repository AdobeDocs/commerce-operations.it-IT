---
title: Registra attività database
description: Configura Commerce per registrare l’attività del database utilizzando l’interfaccia Logger.
feature: Configuration, Logs, Storage
exl-id: 2487c5ec-a01e-4d87-bc5e-c33643b032df
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 0%

---

# Registra attività database

Nell&#39;esempio seguente viene illustrato come registrare l&#39;attività del database utilizzando `[Magento\Framework\DB\LoggerInterface](https://github.com/magento/magento2/blob/2.4.8/lib/internal/Magento/Framework/DB/LoggerInterface.php)`, che ha due implementazioni:

- Non registra nulla (impostazione predefinita): [`Magento\Framework\DB\Logger\Quiet`](https://github.com/magento/magento2/blob/2.4.8/lib/internal/Magento/Framework/DB/Logger/Quiet.php)
- Registra nella directory `var/log`: [`Magento\Framework\DB\Logger\File`](https://github.com/magento/magento2/blob/2.4.8/lib/internal/Magento/Framework/DB/Logger/File.php)

>[!TIP]
>
>È possibile utilizzare Commerce CLI per [abilitare e disabilitare la registrazione del database](../cli/enable-logging.md#database-logging).

Per modificare la configurazione predefinita di `\Magento\Framework\DB\Logger\LoggerProxy`, modificare `app/etc/di.xml`.

Innanzitutto, modificare i valori predefiniti di `loggerAlias` e `logCallStack` argomenti in:

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

In seguito, specificare il percorso del file per `Magento\Framework\DB\Logger\File`:

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

