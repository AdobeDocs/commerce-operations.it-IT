---
title: Distribuzione di un singolo computer
description: Scopri come distribuire gli aggiornamenti a Commerce su un server di produzione utilizzando la riga di comando.
feature: Configuration, Deploy
exl-id: ca73309c-7584-4506-99de-dd933651eeb6
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '188'
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
>Gli sviluppatori partecipanti devono utilizzare [questa guida](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies) per aggiornare l&#39;installazione di Commerce.

## Passaggi della distribuzione

1. Accedi al server di produzione come [proprietario del file system](../../installation/prerequisites/file-system/overview.md) o passa a tale proprietario.

1. Cambia directory in directory base Commerce:

   ```shell
   cd <Commerce base directory>
   ```

1. Abilita la modalità di manutenzione tramite il comando:

   ```shell
   bin/magento maintenance:enable
   ```

1. Applica aggiornamenti a Commerce o ai suoi componenti utilizzando il seguente pattern di comando:

   ```shell
   composer require-commerce <package> <version> --no-update
   ```

   **pacchetto**: nome del pacchetto che si desidera aggiornare.

   Ad esempio:

   - `magento/product-community-edition`
   - `magento/product-enterprise-edition`

   **versione**: la versione di destinazione del pacchetto da aggiornare.

1. Aggiorna componenti con Compositore:

   ```shell
   composer update
   ```

1. Aggiornare lo schema e i dati del database:

   ```shell
   bin/magento setup:upgrade
   ```

1. Compila il codice:

   ```shell
   bin/magento setup:di:compile
   ```

1. Distribuisci contenuto statico:

   ```shell
   bin/magento setup:static-content:deploy
   ```

1. Pulisci la cache:

   ```shell
   bin/magento cache:clean
   ```

1. Esci dalla modalità di manutenzione:

   ```shell
   bin/magento maintenance:disable
   ```

