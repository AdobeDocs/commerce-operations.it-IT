---
title: Eseguire unit test
description: Scopri come eseguire gli unit test definiti nel codebase di Adobe Commerce. Scopri i comandi di test, le opzioni di esecuzione e i rapporti sui risultati.
exl-id: 23200420-d15c-4910-8ce6-abd0cc070777
source-git-commit: 48624d70761117ed0b9f8a7be913fce0572577b6
workflow-type: tm+mt
source-wordcount: '152'
ht-degree: 0%

---

# Eseguire unit test

{{file-system-owner}}

Questo comando esegue un set di test definiti nella base di codice di Commerce 2. È possibile eseguire tutti i test o i test selezionati. Ogni volta che viene specificato un tipo non supportato, il programma termina ed elenca tutti i tipi disponibili. Dopo l’esecuzione, viene visualizzato un rapporto dettagliato che mostra l’esecuzione dei test e i relativi risultati.

## Prerequisiti

Prima di eseguire questo comando, _deve_ essere true:

- Il modulo `Magento_Developer` deve essere abilitato. Puoi abilitarlo come segue:

  ```shell
  bin/magento module:enable [--force] Magento_Developer
  ```

  Utilizzare l&#39;opzione `--force` solo se necessario.

- Il sistema deve essere configurato per eseguire i test desiderati.

Ad esempio, per eseguire gli integration test, è necessario copiare `dev/tests/integration/etc/install-config-mysql.php.dist` in `dev/tests/integration/etc/install-config-mysql.php` e modificarlo in base all&#39;ambiente.

## Esecuzione dei test

Utilizzo comando:

```shell
bin/magento dev:tests:run <test>
```

Per elencare i tipi di test disponibili:

```shell
bin/magento dev:tests:run --help
```

Esempio restituito:

```text
all, unit, integration, integration-all, static, static-all, integrity, legacy, default
```

Ad esempio, per eseguire gli integration test:

```shell
bin/magento dev:tests:run integration
```
