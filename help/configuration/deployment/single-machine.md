---
title: Distribuzione di singole macchine
description: Scopri come distribuire gli aggiornamenti a Commerce su un server di produzione utilizzando la riga di comando.
source-git-commit: 2e1a06b59fda7db4a9b32d000e1b2a3ca88926d3
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# Distribuzione a macchina singola

Questo argomento fornisce istruzioni per la distribuzione degli aggiornamenti a Commerce su un server di produzione utilizzando la riga di comando. Questo processo si applica agli utenti tecnici responsabili dei negozi in esecuzione su un singolo computer con alcuni temi e impostazioni internazionali installati.

## Ipotesi

- È stato installato Commerce utilizzando [Compositore](../../installation/composer.md).
- Stai applicando direttamente gli aggiornamenti al server.

>[!WARNING]
>
>Questa guida non si applica se hai utilizzato `git clone` per installare Commerce.
>Gli sviluppatori contributori devono utilizzare [questa guida][install] per aggiornare l’installazione Commerce.

## Passaggi di distribuzione

1. Accedi al tuo server di produzione come, o passa a [proprietario del file system](../../installation/prerequisites/file-system/overview.md).

1. Cambia directory nella directory di base Commerce:

   ```bash
   cd <Commerce base directory>
   ```

1. Attiva la modalità di manutenzione utilizzando il comando:

   ```bash
   bin/magento maintenance:enable
   ```

1. Applica gli aggiornamenti a Commerce o ai relativi componenti utilizzando il seguente pattern di comando:

   ```bash
   composer require-commerce <package> <version> --no-update
   ```

   **pacchetto**: Nome del pacchetto da aggiornare.

   Ad esempio:

   - `magento/product-community-edition`
   - `magento/product-enterprise-edition`

   **version**: Versione di destinazione del pacchetto da aggiornare.

1. Aggiorna i componenti con Compositore:

   ```bash
   composer update
   ```

1. Aggiornare lo schema e i dati del database:

   ```bash
   bin/magento setup:upgrade
   ```

1. Compila il codice:

   ```bash
   bin/magento setup:di:compile
   ```

1. Distribuzione di contenuto statico:

   ```bash
   bin/magento setup:static-content:deploy
   ```

1. Pulisci la cache:

   ```bash
   bin/magento cache:clean
   ```

1. Esci dalla modalità di manutenzione:

   ```bash
   bin/magento maintenance:disable
   ```

<!-- link definitions -->

[install]: https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/
