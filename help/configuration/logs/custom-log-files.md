---
title: Scrivi in un file di registro personalizzato
description: Scopri come creare e configurare file di registro personalizzati in Adobe Commerce. Scopri i gestori di logger e l’implementazione di registrazione personalizzata.
feature: Configuration, Logs
badge: label="Contributo di Atwix" type="Informative" url="https://www.atwix.com/" tooltip="Atwix"
exl-id: 875f45e7-30c9-4b1b-afe9-d1a8d51ccdf0
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 0%

---

# Scrivi in un file di registro personalizzato

Il modulo `Magento\Framework\Logger` contiene le seguenti classi di gestori:

| Classe | File di registro |
| ----- | -------- |
| [Magento\Framework\Logger\Handler\Base](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Base.php) | - |
| [Magento\Framework\Logger\Handler\Debug](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Debug.php) | `/var/log/debug.log` |
| [Magento\Framework\Logger\Handler\Exception](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Exception.php) | `/var/log/exception.log` |
| [Magento\Framework\Logger\Handler\Syslog](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Syslog.php) | - |
| [Magento\Framework\Logger\Handler\System](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/System.php) | `/var/log/system.log` |

È possibile trovarli nella directory `lib/internal/Magento/Framework/Logger/Handler`.

Per l&#39;accesso a un file personalizzato è possibile utilizzare uno dei seguenti approcci:

- Configura un file di registro personalizzato in `di.xml`
- Configurare un file personalizzato nella classe del gestore di logger personalizzato

## Configura un file di registro personalizzato in `di.xml`

In questo esempio viene illustrato come utilizzare [tipi virtuali](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) per registrare `debug` messaggi in un file di registro personalizzato anziché un `/var/log/debug.log` standard.

1. Nel file `di.xml` del modulo, definisci un file di registro personalizzato come [tipo virtuale](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types).

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomDebug" type="Magento\Framework\Logger\Handler\Base">
       <arguments>
           <argument name="fileName" xsi:type="string">/var/log/payment.log</argument>
        </arguments>
   </virtualType>
   ```

   Il valore `name` di `Magento\Payment\Model\Method\MyCustomDebug` deve essere univoco.

1. Definisci il gestore in un altro [tipo virtuale](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) con un `name` univoco:

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
           </argument>
       </arguments>
   </virtualType>
   ```

1. Inserire il `MyCustomLogger` [tipo virtuale](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) nell&#39;oggetto `Magento\Payment\Model\Method\Logger`:

   ```xml
   <type name="Magento\Payment\Model\Method\Logger">
       <arguments>
           <argument name="logger" xsi:type="object">Magento\Payment\Model\Method\MyCustomLogger</argument>
       </arguments>
   </type>
   ```

1. La classe virtuale `Magento\Payment\Model\Method\MyCustomDebug` viene inserita nel gestore `debug` della proprietà `$logger` nella classe `Magento\Payment\Model\Method\Logger`.

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
   </argument>
   ```

Messaggi di eccezione registrati nel file `/var/log/payment.log`.

## Configurare un file di registro personalizzato nella classe del gestore logger

In questo esempio viene illustrato come utilizzare una classe gestore logger personalizzata per registrare `error` messaggi in un file di log specifico.

1. Crea una classe che registra i dati. In questo esempio, la classe è definita in `app/code/Vendor/ModuleName/Logger/Handler/ErrorHandler.php`.

   ```php
   <?php
   /**
    * @author Vendor
    * @copyright Copyright (c) 2019 Vendor (https://www.vendor.com/)
    */
   namespace Vendor\ModuleName\Logger\Handler;
   
   use Magento\Framework\Logger\Handler\Base as BaseHandler;
   use Monolog\Logger as MonologLogger;
   
   /**
    * Class ErrorHandler
    */
   class ErrorHandler extends BaseHandler
   {
       /**
        * Logging level
        *
        * @var int
        */
       protected $loggerType = MonologLogger::ERROR;
   
       /**
        * File name
        *
        * @var string
        */
       protected $fileName = '/var/log/my_custom_logger/error.log';
   }
   ```

1. Definisci il gestore per questa classe come [tipo virtuale](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) nel file `di.xml` del modulo.

   ```xml
   <virtualType name="MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
           </argument>
       </arguments>
   </virtualType>
   ```

   `MyCustomLogger` è un identificatore univoco.

1. Nella definizione `type`, specificare il nome della classe in cui viene inserito il gestore di logger personalizzato. Utilizzare il nome del tipo virtuale del passaggio precedente come argomento per questo tipo.

   ```xml
   <type name="Vendor\ModuleName\Observer\MyObserver">
       <arguments>
           <argument name="logger" xsi:type="object">MyCustomLogger</argument>
       </arguments>
   </type>
   ```

   Codice Source della classe `Vendor\ModuleName\Observer\MyObserver`:

   ```php
   <?php
   /**
    * @author Vendor
    * @copyright Copyright (c) 2019 Vendor (https://www.vendor.com/)
    */
   declare(strict_types=1);
   
   namespace Vendor\ModuleName\Observer;
   
   use Psr\Log\LoggerInterface as PsrLoggerInterface;
   use Exception;
   use Magento\Framework\Event\ObserverInterface;
   use Magento\Framework\Event\Observer;
   
   /**
    * Class MyObserver
    */
   class MyObserver implements ObserverInterface
   {
       /**
        * @var PsrLoggerInterface
        */
       private $logger;
   
       /**
        * MyObserver constructor.
        *
        * @param PsrLoggerInterface $logger
        */
       public function __construct(
           PsrLoggerInterface $logger
       ) {
           $this->logger = $logger;
       }
   
       /**
        * @param Observer $observer
        */
       public function execute(Observer $observer)
       {
           try {
               // some code goes here
           } catch (Exception $e) {
               $this->logger->error($e->getMessage());
           }
       }
   }
   ```

1. La classe `Vendor\ModuleName\Logger\Handler\ErrorHandler` viene inserita nel gestore `error` della proprietà `$logger` in `Vendor\ModuleName\Observer\MyObserver`.

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
   </argument>
   ...
   ```

Messaggi di eccezione registrati nel file `/var/log/my_custom_logger/error.log`.

