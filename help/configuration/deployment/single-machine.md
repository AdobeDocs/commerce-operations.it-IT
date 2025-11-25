---
title: Distribuzione di un singolo computer
description: Scopri come distribuire gli aggiornamenti a Commerce su un server di produzione utilizzando la riga di comando.
feature: Configuration, Deploy
exl-id: ca73309c-7584-4506-99de-dd933651eeb6
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 1%

---

# Distribuzione su un singolo computer

In questo argomento vengono fornite istruzioni per la distribuzione di aggiornamenti a Commerce in un server di produzione tramite la riga di comando. Questo processo si applica agli utenti tecnici responsabili degli archivi in esecuzione su un singolo computer con alcuni temi e impostazioni internazionali installati.

## Presupposti

- Hai installato Commerce utilizzando [Compositore](../../installation/composer.md).
- Gli aggiornamenti vengono applicati direttamente al server.

>[!WARNING]
>
>Questa guida non è applicabile se è stato utilizzato `git clone` per installare Commerce.
>Gli sviluppatori partecipanti devono utilizzare [questa guida][install] per aggiornare l&#39;installazione di Commerce.

## Passaggi della distribuzione

1. Accedi al server di produzione come [proprietario del file system](../../installation/prerequisites/file-system/overview.md) o passa a tale proprietario.

1. Cambia directory in directory base Commerce:

   ```bash
   cd <Commerce base directory>
   ```

1. Abilita la modalità di manutenzione tramite il comando:

   ```bash
   bin/magento maintenance:enable
   ```

1. Applica aggiornamenti a Commerce o ai suoi componenti utilizzando il seguente pattern di comando:

   ```bash
   composer require-commerce <package> <version> --no-update
   ```

   **pacchetto**: nome del pacchetto che si desidera aggiornare.

   Ad esempio:

   - `magento/product-community-edition`
   - `magento/product-enterprise-edition`

   **versione**: la versione di destinazione del pacchetto da aggiornare.

1. Aggiorna componenti con Compositore:

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

1. Distribuisci contenuto statico:

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

[install]: https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies
