---
title: Gestire moduli ed estensioni (sviluppatore)
description: Gestisci i moduli e le estensioni di Adobe Commerce tramite l’interfaccia della riga di comando e il gestore di pacchetti del Compositore.
feature: Upgrade, Extensions
exl-id: 447eb317-83e1-4900-83a5-9ac1a008e752
last-update: 2026-04-28T00:00:00.000Z
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
feature_v2:
  - id: a8ae7a5a-6cdc-5922-bd0d-6feb44b04984
    internal-label: Upgrade
  - id: f08fa0de-a550-4acd-b570-f81cf1d03aaf
    internal-label: Commerce ecosystem
subfeature_v2:
  - id: dad884f1-e840-49a1-970e-2f965bdbc410
    internal-label: Extensions
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

<!-- Last updated from includes: 2026-04-17 13:49:36 -->
