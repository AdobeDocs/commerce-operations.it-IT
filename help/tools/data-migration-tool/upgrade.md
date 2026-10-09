---
title: Aggiorna [!DNL Data Migration Tool]
description: Scopri come aggiornare [!DNL Data Migration Tool] per trasferire i dati tra Magento 1 e Magento 2.
exl-id: c0d56d1d-b15b-437f-be72-74282dbe85c1
topic: Commerce, Migration
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
role_v2:
  - id: c66ffd68-0f65-42bb-aa23-b4020f12e0bd
    internal-label: Admin
  - id: ff6a42d2-313e-452e-93a6-792e4fad9ff8
    internal-label: Developer
level_v2:
  - id: d378ca77-2da1-4f39-ad92-1917fe974a38
    internal-label: Experienced
source-git-commit: 0c13885f16ac339066198329f38d5c5e2d4a06d1
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%
---
# Aggiorna [!DNL Data Migration Tool]

Per verificare che le versioni dell&#39;installazione corrente di Magento 2 e di [!DNL Data Migration Tool] corrispondano esattamente, potrebbe essere necessario aggiornare lo strumento.

## Prerequisiti

Prima di aggiornare [!DNL Data Migration Tool], è necessario:

* Aggiorna il software Magento per ottenere la versione più recente

* Esegui backup della directory `vendor/magento/data-migration-tool`

* Verificare che la versione [!DNL Data Migration Tool] corrisponda alla versione dell&#39;applicazione Magento

### Aggiornamento del software Magento

Se non lo hai già fatto, [aggiorna il software Magento](../../upgrade/overview.md).

### Esegui backup della directory `vendor/magento/data-migration-tool`

Prima di aggiornare [!DNL Data Migration Tool], eseguire il backup almeno della directory `vendor/magento/data-migration-tool`. Durante l’aggiornamento, poteva essere eliminato e sostituito dal codice aggiornato.

Puoi anche eseguire il backup dell’intera base di codice e del database di Magento utilizzando il seguente comando:

```shell
php <magento_root>/bin/magento setup:backup --code --db
```

>[!WARNING]
>
>La directory `vendor/magento/data-migration-tool` contiene il codice personalizzato. Se non si esegue il backup, è possibile perdere le personalizzazioni durante l&#39;aggiornamento.


### Assicurati che le versioni corrispondano

Le versioni di [!DNL Data Migration Tool] e del software Magento devono corrispondere esattamente. Ad esempio, Magento 2.1.2 richiede la versione 2.1.2 di [!DNL Data Migration Tool].

Consulta l&#39;argomento [Installa [!DNL Data Migration Tool]](install.md) per informazioni su come:

* [Verifica](install.md#check-your-version) la versione di Magento 2

* [Trova](install.md#find-released-versions-of-data-migration-tool) versioni rilasciate di [!DNL Data Migration Tool]

* [Verifica](install.md#check-version-of-installed-data-migration-tool) la versione [!DNL Data Migration Tool]

## Aggiorna [!DNL Data Migration Tool]

1. Accedi al server applicazioni come [proprietario del file system](../../installation/prerequisites/file-system/overview.md) o passa a tale proprietario.
1. Passare alla directory radice dell&#39;applicazione.
1. Immetti il comando seguente:

   ```shell
   composer require magento/data-migration-tool:<version>
   ```

   dove `<version>` deve corrispondere alla versione della base di codice di Magento 2.

   Ad esempio, per la versione 2.1.2, immettere:

   ```shell
   composer require magento/data-migration-tool:2.1.2
   ```

1. Attendere il completamento del comando.
