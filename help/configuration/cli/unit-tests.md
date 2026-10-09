---
title: Eseguire unit test
description: Scopri come eseguire gli unit test definiti nel codebase di Adobe Commerce. Scopri i comandi di test, le opzioni di esecuzione e i rapporti sui risultati.
exl-id: 23200420-d15c-4910-8ce6-abd0cc070777
product_v2:
  - id: eadea719-cf89-469b-a6fd-a236a7138047
    internal-label: Commerce
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
