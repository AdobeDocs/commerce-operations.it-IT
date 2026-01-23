---
title: Personalizzare i percorsi delle directory di base
description: Utilizzare la variabile MAGE_DIRS per impostare una matrice di percorsi assoluti.
exl-id: ee8e1a3a-f1d4-412c-8767-16447113f0cd
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '116'
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

