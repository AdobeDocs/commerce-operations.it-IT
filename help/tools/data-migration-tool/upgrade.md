---
title: Aggiorna  [!DNL Data Migration Tool]
description: Scopri come aggiornare  [!DNL Data Migration Tool]  per trasferire i dati tra il Magento 1 e il Magento 2.
exl-id: c0d56d1d-b15b-437f-be72-74282dbe85c1
topic: Commerce, Migration
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '238'
ht-degree: 0%

---

# Aggiorna [!DNL Data Migration Tool]

Per verificare che le versioni dell&#39;installazione corrente di Magento 2 e di [!DNL Data Migration Tool] corrispondano esattamente, potrebbe essere necessario aggiornare lo strumento.

## Prerequisiti

Prima di aggiornare [!DNL Data Migration Tool], è necessario:

* Aggiornare il software di Magento per ottenere la versione più recente

* Esegui backup della directory `vendor/magento/data-migration-tool`

* Verificare che la versione [!DNL Data Migration Tool] corrisponda alla versione dell&#39;applicazione di Magento

### Aggiornare il software del Magento

Se non lo hai già fatto, [aggiorna il software di Magento](../../upgrade/overview.md).

### Esegui backup della directory `vendor/magento/data-migration-tool`

Prima di aggiornare [!DNL Data Migration Tool], eseguire il backup almeno della directory `vendor/magento/data-migration-tool`. Durante l’aggiornamento, poteva essere eliminato e sostituito dal codice aggiornato.

È inoltre possibile eseguire il backup dell&#39;intero database e codebase di Magento utilizzando il comando seguente:

```bash
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>La directory `vendor/magento/data-migration-tool` contiene il codice personalizzato. Se non si esegue il backup, è possibile perdere le personalizzazioni durante l&#39;aggiornamento.


### Assicurati che le versioni corrispondano

Le versioni di [!DNL Data Migration Tool] e del software di Magento devono corrispondere esattamente. Il Magento 2.1.2 richiede ad esempio la versione 2.1.2 di [!DNL Data Migration Tool].

Consulta l&#39;argomento [Installa [!DNL Data Migration Tool]](install.md) per informazioni su come:

* [Verifica](install.md#check-your-version) la versione del tuo Magento 2

* [Trova](install.md#find-released-versions-of-data-migration-tool) versioni rilasciate di [!DNL Data Migration Tool]

* [Verifica](install.md#check-version-of-installed-data-migration-tool) la versione [!DNL Data Migration Tool]

## Aggiorna [!DNL Data Migration Tool]

1. Accedi al server applicazioni come [proprietario del file system](../../installation/prerequisites/file-system/overview.md) o passa a tale proprietario.
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
