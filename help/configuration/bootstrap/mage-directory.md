---
title: Personalizzare i percorsi delle directory di base
description: Utilizzare la variabile MAGE_DIRS per impostare una matrice di percorsi assoluti.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---


# Percorsi directory di base

La `MAGE_DIRS` la variabile di ambiente consente di specificare percorsi di directory di base personalizzati e frammenti degli URL di base utilizzati dall’applicazione Commerce per creare percorsi assoluti a vari file o per generare URL.

## Imposta MAGE_DIRS

Specifica un array associativo in cui le chiavi sono costanti di [\\Magento\\App\\Filesystem\\DirectoryList][directory-list] e sono percorsi assoluti di directory o percorsi URL rispettivamente.

È possibile impostare `MAGE_DIRS` in uno dei seguenti modi:

- [Imposta il valore dei parametri di bootstrap](../bootstrap/set-parameters.md)
- Utilizza uno script personalizzato per punti di ingresso, ad esempio:

   ```php
   <?php
   /**
    * Copyright © Magento, Inc. All rights reserved.
    * See COPYING.txt for license details.
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

Nell&#39;esempio precedente vengono impostati i percorsi per `[cache]` e `[media]` directory a `/mnt/nfs/cache` e `/mnt/nfs/media`, rispettivamente.

<!-- link definitions -->

[directory-list]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Filesystem/DirectoryList.php
