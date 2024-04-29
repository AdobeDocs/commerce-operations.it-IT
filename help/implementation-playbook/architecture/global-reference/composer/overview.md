---
title: Sviluppo del composizione
description: Scopri come sviluppare i moduli Composer direttamente nella directory "vendor/".
feature: Best Practices
role: Developer
hide: true
hidefromtoc: true
exl-id: 7664ffb5-2e46-49c3-b2e6-c133c35d2f6b
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# Sviluppo del composizione

Questo argomento descrive l’approccio consigliato per lo sviluppo di moduli Compositore sul posto (come archivi Git in `vendor/` e aggiungendo tali moduli al progetto Git principale.

>[!NOTE]
>
>Le presenti linee guida riguardano principalmente [architettura di riferimento globale (GRA)](../overview.md) progetti.

## Preparare un ramo di sviluppo

1. Crea o estrai il ramo di sviluppo nell’archivio Git principale.
1. Richiedi le versioni di sviluppo per ogni modulo gestito.

   In questo esempio, ogni ramo nell’archivio Git principale rappresenta una versione del pacchetto Composer. In questo scenario, la convenzione di denominazione consigliata per le versioni del Compositore è `dev-` seguito dal nome della filiale. Ad esempio:

   - `dev-develop`
   - `dev-qa`

   ```bash
   composer require client/module-example:dev-develop
   ```

1. Se un altro pacchetto Compositore richiede una versione specifica di un modulo (ad esempio, `client/module-example 1.0.12`), installarlo con un alias:

   ```bash
   composer require 'client/module-example:dev-develop as 1.0.12'
   ```

   Per `qa` branch, replace `dev-develop` con `dev-qa`.

## Conversione di pacchetti in archivi Git

Per impostazione predefinita, i pacchetti non contengono `.git/` directory. Il Compositore può estrarre i pacchetti da Git invece di utilizzare i pacchetti predefiniti del Compositore. Il vantaggio di questo approccio è che puoi modificare facilmente i pacchetti durante lo sviluppo.

1. Rimuovi il modulo da `vendor/` directory.

   ```bash
   rm -rf vendor/client/module-example
   ```

1. Reinstallare il modulo utilizzando [origine Git specificata](#prepare-a-development-branch).

   ```bash
   composer install --prefer-source
   ```

1. Verifica che il pacchetto Composer sia ora un archivio Git:

   ```bash
   cd vendor/client/module-example
   git remote -v
   ```

1. Per convertire in batch più moduli in archivi Git (ad esempio moduli &quot;client&quot;):

   ```bash
   rm -rf vendor/client
   composer install --prefer-source
   ```

## Avvia sviluppo

1. Creare o estrarre una feature o un ramo di lavoro. L’esempio seguente mostra un ramo con lo stesso nome di un ticket Jira.

   ```bash
   cd vendor/client/module-example
   git checkout master
   git checkout -b JIRA-1200
   ```

1. Dopo aver modificato i rami in un modulo, consulta le modifiche scaricando la cache di Adobe Commerce e il contenuto statico.

   ```bash
   bin/magento cache:flush
   bin/magento module:enable --all --clear-static-content
   ```

## Aggiornare il progetto principale con il tuo sviluppo

Aggiornare l’archivio Git principale modificando il file `composer.lock` file. Se il modulo è nuovo, attivalo.

```bash
# to update your packages and all dependencies of the package
composer update --with-all-dependencies client/module-example
# to update just your package
composer update client/module-example
 
bin/magento module:enable Client_ModuleExample
git add composer.lock app/etc/config.php
git commit
```
