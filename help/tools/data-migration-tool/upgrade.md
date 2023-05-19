---
title: Aggiornare [!DNL Data Migration Tool]
description: Scopri come aggiornare [!DNL Data Migration Tool] trasferire dati tra il Magento 1 e il Magento 2.
exl-id: c0d56d1d-b15b-437f-be72-74282dbe85c1
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '227'
ht-degree: 0%

---

# Aggiornare [!DNL Data Migration Tool]

Per assicurarsi che le versioni dell&#39;installazione corrente del Magento 2 e [!DNL Data Migration Tool] corrisponde esattamente, potrebbe essere necessario aggiornare lo strumento.

## Prerequisiti

Prima di aggiornare [!DNL Data Migration Tool], è necessario:

* Aggiornare il software di Magento per ottenere la versione più recente

* Eseguire il backup di `vendor/magento/data-migration-tool` directory

* Assicurati che il [!DNL Data Migration Tool] la versione corrisponde alla versione dell&#39;applicazione di Magento

### Aggiornare il software del Magento

Se non lo hai già fatto, [aggiornare il software del Magento](../../upgrade/overview.md).

### Eseguire il backup di `vendor/magento/data-migration-tool` directory

Prima di aggiornare [!DNL Data Migration Tool], esegui il backup almeno del `vendor/magento/data-migration-tool` directory. Durante l’aggiornamento, poteva essere eliminato e sostituito dal codice aggiornato.

È inoltre possibile eseguire il backup dell&#39;intero database e codebase di Magento utilizzando il comando seguente:

```bash
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>Il `vendor/magento/data-migration-tool` contiene il codice personalizzato. Se non si esegue il backup, è possibile perdere le personalizzazioni durante l&#39;aggiornamento.


### Assicurati che le versioni corrispondano

Le versioni di [!DNL Data Migration Tool] e il software del Magento deve corrispondere esattamente. Il Magento 2.1.2, ad esempio, richiede la versione 2.1.2 del [!DNL Data Migration Tool].

Consulta la [Installa [!DNL Data Migration Tool]](install.md) argomento per sapere come:

* [Verifica](install.md#check-your-version) la versione del Magento 2

* [Trova](install.md#find-released-versions-of-data-migration-tool) versioni rilasciate di [!DNL Data Migration Tool]

* [Verifica](install.md#check-version-of-installed-data-migration-tool) il [!DNL Data Migration Tool] version

## Aggiornare [!DNL Data Migration Tool]

1. Accedi al server applicazioni come oppure accedi a [il proprietario del file system](../../installation/prerequisites/file-system/overview.md).
1. Passare alla directory radice dell&#39;applicazione.
1. Immetti il comando seguente:

   ```bash
   composer require magento/data-migration-tool:<version>
   ```

   dove `<version>` deve corrispondere alla versione del codebase Magento 2.

   Ad esempio, per la versione 2.1.2, immettere:

   ```bash
   composer require magento/data-migration-tool:2.1.2
   ```

1. Attendere il completamento del comando.
