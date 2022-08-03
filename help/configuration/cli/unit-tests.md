---
title: Esecuzione di test di unità
description: Esegui unit test definiti nella base di codice Adobe Commerce.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---


# Esecuzione di test di unità

{{file-system-owner}}

Questo comando esegue un set di test definiti nella base di codice Commerce 2. Puoi eseguire tutti i test o i test selezionati. Ogni volta che viene specificato un tipo non supportato, il programma termina ed elenca tutti i tipi disponibili. Dopo l’esecuzione, viene visualizzato un rapporto dettagliato che mostra l’esecuzione del test e i risultati.

## Prerequisiti

Prima di eseguire questo comando, effettuare le seguenti operazioni _deve_ true:

- La `Magento_Developer` Il modulo deve essere abilitato. È possibile abilitarlo come segue:

   ```bash
   bin/magento module:enable [--force] Magento_Developer
   ```

   Utilizza la `--force` solo se necessario.

- Il sistema deve essere configurato per eseguire i test desiderati.

Ad esempio, per eseguire i test di integrazione, devi copiare `dev/tests/integration/etc/install-config-mysql.php.dist` a `dev/tests/integration/etc/install-config-mysql.php` e modificalo in base alle esigenze del tuo ambiente.

## Prove in corso

Utilizzo comando:

```bash
bin/magento dev:tests:run <test>
```

Per elencare i tipi di test disponibili:

```bash
bin/magento dev:tests:run --help
```

Restituzione del campione:

```terminal
all, unit, integration, integration-all, static, static-all, integrity, legacy, default
```

Ad esempio, per eseguire i test di integrazione:

```bash
bin/magento dev:tests:run integration
```
