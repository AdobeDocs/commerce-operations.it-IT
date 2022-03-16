---
title: Gestire moduli ed estensioni
description: Gestisci i moduli e le estensioni Adobe Commerce e Magenti Open Source tramite l’interfaccia a riga di comando e il gestore dei pacchetti Composer.
source-git-commit: 7bcfbc4483f4b6d4c1a5e852adbd1cd81bc136b7
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 2%

---


# Gestione di moduli ed estensioni

Gli sviluppatori che contribuiscono aggiornano moduli ed estensioni specificando le proprie versioni in Adobe Commerce o nel Magento Open Source `composer.json` file. Se non sei uno sviluppatore contributore, consulta [Eseguire un aggiornamento](../implementation/perform-upgrade.md).

Puoi aggiungere una `require` alla sezione `composer.json` oppure puoi utilizzare il `composer require` come segue:

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

## Utilizza la `composer require` command

Utilizzo comando:

```bash
composer require <vendor>/<name>:<version>
```

Ad esempio:

```bash
composer require example/module:1.0.0
```

Attendi che Compositore aggiorni le dipendenze e installi il modulo.

## Aggiungi un `require` al file compositer.json

1. Apri `composer.json` in un editor di testo.

1. Aggiungi un `require` sezione .

   ```json
   "require": {
     "<vendor>/<name>": "<version>",
     "<vendor>/<name>": "<version>"
   }
   ```

1. Salva le modifiche apportate al `composer.json` e esci dall’editor di testo.

1. Risolvere le dipendenze e scrivere versioni esatte nel `composer.lock` file.

   ```bash
   composer update
   ```
