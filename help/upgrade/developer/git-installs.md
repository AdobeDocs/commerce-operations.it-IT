---
title: Aggiornamento di un’installazione basata su Git
description: Aggiorna un’installazione di Adobe Commerce clonata da un archivio Git.
exl-id: a8c42857-7221-4b21-8377-4bfb6308c418
source-git-commit: 55512521254c49511100a557a4b00cf3ebee0311
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---

# Aggiornare un’installazione basata su Git

Questo argomento illustra come uno sviluppatore che partecipa all’aggiornamento di Adobe Commerce senza reinstallarlo. Se non sei uno sviluppatore che contribuisce, consulta [Eseguire un aggiornamento](../implementation/perform-upgrade.md).

Per effettuare l&#39;aggiornamento se sei uno sviluppatore che contribuisce:

{{$include /help/_includes/server-login.md}}

1. Salvare le modifiche apportate al file `composer.json` perché i passaggi successivi lo sovrascrivono.

1. Crea un backup del file `composer.json`.

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

1. Differenziare e unire il file `composer.json.old` con il file `composer.json`.

1. Risolvere le dipendenze e scrivere versioni esatte nel file `composer.lock`.

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

<!-- Last updated from includes: 2022-09-08 16:00:49 -->
