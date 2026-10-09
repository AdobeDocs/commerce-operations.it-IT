---
title: Personalizzare i percorsi delle directory di base
description: Utilizzare la variabile MAGE_DIRS per impostare una matrice di percorsi assoluti.
exl-id: ee8e1a3a-f1d4-412c-8767-16447113f0cd
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
source-wordcount: '128'
ht-degree: 0%
---
# Percorsi directory base

La variabile di ambiente `MAGE_DIRS` consente di specificare percorsi di directory di base personalizzati e frammenti di URL di base utilizzati dall&#39;applicazione Commerce per creare percorsi assoluti a vari file o per generare URL.

## Imposta DIRS_IMMAGINE

Specifica un array associativo in cui le chiavi sono costanti di [\\Magento\\App\\Filesystem\\DirectoryList](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Filesystem/DirectoryList.php) e i valori sono rispettivamente percorsi assoluti delle directory o dei relativi percorsi URL.

È possibile impostare `MAGE_DIRS` in uno dei modi seguenti:

- [Imposta il valore dei parametri di bootstrap](../bootstrap/set-parameters.md)
- Utilizza uno script di punto di ingresso personalizzato come il seguente:

  ```php
  <?php
  /**
   * Copyright [first year code created] Adobe
   * All Rights Reserved.
   */
  
  use Magento\Framework\App\Bootstrap;
  use Magento\Framework\App\Filesystem\DirectoryList;
  use Magento\Framework\App\Http;
  
  require __DIR__ . '/app/bootstrap.php';
  $params = $_SERVER;
  $params[Bootstrap::INIT_PARAM_FILESYSTEM_DIR_PATHS] = [
       DirectoryList::PUB => [DirectoryList::URL_PATH => ''],
       DirectoryList::MEDIA => [DirectoryList::PATH => '/mnt/nfs/media', DirectoryList::URL_PATH => ''],
       DirectoryList::STATIC_VIEW => [DirectoryList::URL_PATH => 'static'],
       DirectoryList::UPLOAD => [DirectoryList::URL_PATH => '/mnt/nfs/media/upload'],
       DirectoryList::CACHE => [DirectoryList::PATH => '/mnt/nfs/cache'],
  ];
  $bootstrap = Bootstrap::create(BP, $params);
  /** @var Http $app */
  $app = $bootstrap->createApplication(Http::class);
  $bootstrap->run($app);
  ```

L&#39;esempio precedente imposta i percorsi per le directory `[cache]` e `[media]` rispettivamente su `/mnt/nfs/cache` e `/mnt/nfs/media`.

