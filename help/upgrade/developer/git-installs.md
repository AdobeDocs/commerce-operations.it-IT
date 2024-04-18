---
title: Aggiornamento di un’installazione basata su Git
description: Aggiorna un’installazione di Adobe Commerce clonata da un archivio Git.
exl-id: a8c42857-7221-4b21-8377-4bfb6308c418
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---

# Aggiornare un’installazione basata su Git

Questo argomento illustra come uno sviluppatore che partecipa all’aggiornamento di Adobe Commerce senza reinstallarlo. Se non sei uno sviluppatore, consulta [Eseguire un aggiornamento](../implementation/perform-upgrade.md).

Per effettuare l&#39;aggiornamento se sei uno sviluppatore che contribuisce:

{{$include /help/_includes/server-login.md}}

1. Salva eventuali modifiche apportate al `composer.json` perché i passaggi successivi lo sovrascrivono.

1. Crea un backup del `composer.json` file.

   ```bash
   cp composer.json composer.json.old
   ```

1. Aggiorna l’archivio locale per ottenere il codice più recente:

   ```bash
   git pull origin develop
   ```

   >[!NOTE]
   >
   >Se `git pull origin develop` non riesce, vedi [risoluzione dei problemi](https://support.magento.com/hc/en-us/articles/360034229872).

1. Differenza e unione `composer.json.old` file con `composer.json` file.

1. Risolvere le dipendenze e scrivere versioni esatte in `composer.lock` file.

   ```bash
   composer update
   ```

1. Aggiornare il database:

   ```bash
   bin/magento setup:upgrade
   ```

1. Pulisci la cache:

   ```bash
   bin/magento cache:clean
   ```
