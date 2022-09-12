---
title: Aggiornare [!DNL Data Migration Tool]
description: Scopri come aggiornare il [!DNL Data Migration Tool] trasferire i dati tra il Magento 1 e il Magento 2.
source-git-commit: d263e412022a89255b7d33b267b696a8bb1bc8a2
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---


# Aggiornare [!DNL Data Migration Tool]

Per verificare che le versioni dell&#39;installazione corrente del Magento 2 e [!DNL Data Migration Tool] corrispondono esattamente, potrebbe essere necessario aggiornare lo strumento.

## Prerequisiti

Prima di aggiornare [!DNL Data Migration Tool], devi:

* Aggiornare il software di Magento per ottenere la versione più recente

* Eseguire il backup `vendor/magento/data-migration-tool` directory

* Assicurati che il [!DNL Data Migration Tool] La versione corrisponde alla versione dell&#39;applicazione Magento

### Aggiornare il software di Magento

Se non l&#39;hai già fatto, [aggiornare il software di Magento](../../upgrade/overview.md).

### Eseguire il backup `vendor/magento/data-migration-tool` directory

Prima di aggiornare [!DNL Data Migration Tool], effettua almeno il backup `vendor/magento/data-migration-tool` directory. Durante l’aggiornamento, potrebbe essere eliminato e sostituito dal codice aggiornato.

È inoltre possibile eseguire il backup dell&#39;intero database e codebase di Magento utilizzando il seguente comando:

```bash
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>La `vendor/magento/data-migration-tool` contiene il codice personalizzato. Se non esegui il backup, potresti perdere le personalizzazioni durante l’aggiornamento.


### Assicurati che le versioni corrispondano

Le versioni di [!DNL Data Migration Tool] e il software di Magento deve corrispondere esattamente. Ad esempio, Magento 2.1.2 richiede la versione 2.1.2 della [!DNL Data Migration Tool].

Consulta la sezione [Installa [!DNL Data Migration Tool]](install.md) argomento per scoprire come:

* [Controlla](install.md#check-your-version) la versione del Magento 2

* [Trova](install.md#find-released-versions-of-data-migration-tool) versioni rilasciate [!DNL Data Migration Tool]

* [Controlla](install.md#check-version-of-installed-data-migration-tool) la [!DNL Data Migration Tool] version

## Aggiornare [!DNL Data Migration Tool]

1. Accedi al server delle applicazioni come o passa a [proprietario del file system](../../installation/prerequisites/file-system/overview.md).
1. Passa alla directory principale dell&#39;applicazione.
1. Immetti il seguente comando:

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   dove `<version>` deve corrispondere alla versione del codebase Magento 2.

   Ad esempio, per la versione 2.1.2, immetti:

   ```bash
   composer require magento/data-migration-tool:2.1.2
   ```

1. Attendere il completamento del comando.
