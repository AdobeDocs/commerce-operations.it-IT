---
title: Gestire moduli ed estensioni (sviluppatore)
description: Gestisci i moduli e le estensioni di Adobe Commerce tramite l’interfaccia della riga di comando e il gestore di pacchetti del Compositore.
feature: Upgrade, Extensions
exl-id: 447eb317-83e1-4900-83a5-9ac1a008e752
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '131'
ht-degree: 3%

---

# Gestire moduli ed estensioni

Aiutando gli sviluppatori ad aggiornare moduli ed estensioni specificandone le versioni in Adobe Commerce `composer.json` file. Se non sei uno sviluppatore, consulta [Eseguire un aggiornamento](../implementation/perform-upgrade.md).

Puoi aggiungere una `require` sezione al `composer.json` o puoi utilizzare il `composer require` comando come segue:

{{$include /help/_includes/server-login.md}}

Sono disponibili le seguenti opzioni:

## Ottieni versioni modulo disponibili

Utilizzo comando:

```bash
composer show --all <vendor>/<name>
```

Ad esempio:

```bash
composer show --all example/module
```

## Utilizza il `composer require` comando

Utilizzo comando:

```bash
composer require <vendor>/<name>:<version>
```

Ad esempio:

```bash
composer require example/module:1.0.0
```

Attendere. Aggiornamento delle dipendenze in corso e installazione del modulo.

## Aggiungi un `require` al file compositore.json

1. Apri `composer.json` in un editor di testo.

1. Aggiungi un `require` sezione.

   ```json
   "require": {
     "<vendor>/<name>": "<version>",
     "<vendor>/<name>": "<version>"
   }
   ```

1. Salva le modifiche in `composer.json` e uscire dall&#39;editor di testo.

1. Risolvere le dipendenze e scrivere versioni esatte in `composer.lock` file.

   ```bash
   composer update
   ```
