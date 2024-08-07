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

In questo argomento viene descritto l&#39;approccio consigliato per lo sviluppo di moduli Composer sul posto (come archivi Git nella directory `vendor/`) e per l&#39;aggiunta di tali moduli al progetto Git principale.

>[!NOTE]
>
>Queste linee guida si applicano principalmente a [progetti GRA (Global Reference Architecture)](../overview.md).

## Preparare un ramo di sviluppo

1. Crea o estrai il ramo di sviluppo nell’archivio Git principale.
1. Richiedi le versioni di sviluppo per ogni modulo gestito.

   In questo esempio, ogni ramo nell’archivio Git principale rappresenta una versione del pacchetto Composer. La convenzione di denominazione consigliata per le versioni del Compositore in questo scenario è `dev-` seguita dal nome del ramo. Ad esempio:

   - `dev-develop`
   - `dev-qa`

   ```bash
   composer require client/module-example:dev-develop
   ```

1. Se un altro pacchetto Composer richiede una versione specifica di un modulo (ad esempio, `client/module-example 1.0.12`), installarlo con un alias:

   ```bash
   composer require 'client/module-example:dev-develop as 1.0.12'
   ```

   Per il ramo `qa`, sostituire `dev-develop` con `dev-qa`.

## Conversione di pacchetti in archivi Git

Per impostazione predefinita, i pacchetti non contengono una directory `.git/`. Il Compositore può estrarre i pacchetti da Git invece di utilizzare i pacchetti predefiniti del Compositore. Il vantaggio di questo approccio è che puoi modificare facilmente i pacchetti durante lo sviluppo.

1. Rimuovere il modulo dalla directory `vendor/`.

   ```bash
   rm -rf vendor/client/module-example
   ```

1. Reinstalla il modulo utilizzando l&#39;[origine Git specificata](#prepare-a-development-branch).

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

Aggiornare l&#39;archivio Git principale modificando il file `composer.lock`. Se il modulo è nuovo, attivalo.

```bash
# to update your packages and all dependencies of the package
composer update --with-all-dependencies client/module-example
# to update just your package
composer update client/module-example
 
bin/magento module:enable Client_ModuleExample
git add composer.lock app/etc/config.php
git commit
```
