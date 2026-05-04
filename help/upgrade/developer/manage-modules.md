---
title: Gestire moduli ed estensioni (sviluppatore)
description: Gestisci i moduli e le estensioni di Adobe Commerce tramite l’interfaccia della riga di comando e il gestore di pacchetti del Compositore.
feature: Upgrade, Extensions
exl-id: 447eb317-83e1-4900-83a5-9ac1a008e752
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '132'
ht-degree: 3%

---

# Gestire moduli ed estensioni

Gli sviluppatori che collaborano aggiornano moduli ed estensioni specificando le loro versioni nel file Adobe Commerce `composer.json`. Se non sei uno sviluppatore che contribuisce, consulta [Eseguire un aggiornamento](../implementation/perform-upgrade.md).

È possibile aggiungere una sezione `require` al file `composer.json` oppure utilizzare il comando `composer require` come segue:

{{$include /help/_includes/server-login.md}}

Sono disponibili le seguenti opzioni:

## Ottieni versioni modulo disponibili

Utilizzo comando:

```shell
composer show --all <vendor>/<name>
```

Ad esempio:

```shell
composer show --all example/module
```

## Usa il comando `composer require`

Utilizzo comando:

```shell
composer require <vendor>/<name>:<version>
```

Ad esempio:

```shell
composer require example/module:1.0.0
```

Attendere. Aggiornamento delle dipendenze in corso e installazione del modulo.

## Aggiungi una sezione `require` al file compositore.json

1. Apri `composer.json` in un editor di testo.

1. Aggiungi una sezione `require`.

   ```json
   "require": {
     "<vendor>/<name>": "<version>",
     "<vendor>/<name>": "<version>"
   }
   ```

1. Salvare le modifiche apportate al file `composer.json` e uscire dall&#39;editor di testo.

1. Risolvere le dipendenze e scrivere versioni esatte nel file `composer.lock`.

   ```shell
   composer update
   ```

<!-- Last updated from includes: 2022-09-08 16:00:49 -->
