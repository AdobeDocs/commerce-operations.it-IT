---
title: Aggiornare un’installazione basata su Git
description: Aggiorna un’installazione di Adobe Commerce o Magento Open Source clonata da un archivio Git.
source-git-commit: 7bcfbc4483f4b6d4c1a5e852adbd1cd81bc136b7
workflow-type: tm+mt
source-wordcount: '122'
ht-degree: 0%

---


# Aggiornare un’installazione basata su Git

Questo argomento illustra come uno sviluppatore contributore può aggiornare Adobe Commerce o Magento Open Source senza reinstallarlo. Se non sei uno sviluppatore contributore, consulta [Eseguire un aggiornamento](../implementation/perform-upgrade.md).

Per eseguire l’aggiornamento se sei uno sviluppatore collaboratore:

{{$include /help/_includes/server-login.md}}

1. Salva le modifiche apportate al `composer.json` file perché i passaggi successivi lo sovrascrivono.

1. Crea un backup del tuo `composer.json` file.

   ```bash
   cp composer.json composer.json.old
   ```

1. Aggiorna il tuo archivio locale per ottenere il codice più recente:

   ```bash
   git pull origin develop
   ```

   >[!NOTE]
   >
   >Se `git pull origin develop` fallisce, vedi [risoluzione](https://support.magento.com/hc/en-us/articles/360034229872).

1. Differisci e unisci il tuo `composer.json.old` con il `composer.json` file.

1. Risolvere le dipendenze e scrivere versioni esatte nel `composer.lock` file.

   ```bash
   composer update
   ```

1. Aggiorna il database:

   ```bash
   bin/magento setup:upgrade
   ```

1. Pulisci la cache:

   ```bash
   bin/magento cache:clean
   ```
