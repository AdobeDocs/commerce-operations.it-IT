---
title: Scrivi in un file di registro personalizzato
description: Scopri come impostare file di registro personalizzati.
badge: label="Contributo di Atwix" type="Informative" url="https://www.atwix.com/" tooltip="Atwix"
source-git-commit: d7f32690b25c61fa31a99e6d02f9f1025de2bb99
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---


# Scrivi in un file di registro personalizzato

La `Magento\Framework\Logger` Il modulo contiene le seguenti classi di handler:

| Classe | File di registro |
| ----- | -------- |
| [Magento\Framework\Logger\Handler\Base][base] | - |
| [Magento\Framework\Logger\Handler\Debug][debug] | `/var/log/debug.log` |
| [Magento\Framework\Logger\Handler\Exception][exception] | `/var/log/exception.log` |
| [Magento\Framework\Logger\Handler\Syslog][syslog] | - |
| [Magento\Framework\Logger\Handler\System][system] | `/var/log/system.log` |

Le puoi trovare nel `lib/internal/Magento/Framework/Logger/Handler` directory.

Puoi utilizzare uno dei seguenti approcci per accedere a un file personalizzato:

- Imposta un file di registro personalizzato nella `di.xml`
- Configurare un file personalizzato nella classe del gestore del logger personalizzato

## Imposta un file di registro personalizzato nella `di.xml`

Questo esempio mostra come utilizzare [tipi virtuali](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) al registro `debug` messaggi in un file di registro personalizzato anziché in un file standard `/var/log/debug.log`.

1. In `di.xml` file del modulo, definisci un file di registro personalizzato come [tipo virtuale](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types).

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomDebug" type="Magento\Framework\Logger\Handler\Base">
       <arguments>
           <argument name="fileName" xsi:type="string">/var/log/payment.log</argument>
        </arguments>
   </virtualType>
   ```

   La `name` valore `Magento\Payment\Model\Method\MyCustomDebug` deve essere univoco.

1. Definire il gestore in un altro [tipo virtuale](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) con un `name`:

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
           </argument>
       </arguments>
   </virtualType>
   ```

1. Inserisci `MyCustomLogger` [tipo virtuale](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) in `Magento\Payment\Model\Method\Logger` oggetto:

   ```xml
   <type name="Magento\Payment\Model\Method\Logger">
       <arguments>
           <argument name="logger" xsi:type="object">Magento\Payment\Model\Method\MyCustomLogger</argument>
       </arguments>
   </type>
   ```

1. Classe virtuale `Magento\Payment\Model\Method\MyCustomDebug` viene inserito nel `debug` gestore `$logger` nella `Magento\Payment\Model\Method\Logger` classe.

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
   </argument>
   ```

I messaggi di eccezione sono registrati nel `/var/log/payment.log` file.

## Configurare un file di registro personalizzato nella classe gestore logger

Questo esempio mostra come utilizzare una classe personalizzata del gestore logger per registrare `error` in un file di registro specifico.

1. Creare una classe che registri i dati. In questo esempio, la classe è definita in `app/code/Vendor/ModuleName/Logger/Handler/ErrorHandler.php`.

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

1. Definisci il gestore per questa classe come [tipo virtuale](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) nel modulo `di.xml` file.

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

1. In `type` Specifica il nome della classe in cui viene inserito il gestore di logger personalizzato. Utilizzare il nome del tipo virtuale del passaggio precedente come argomento per questo tipo.

   ```xml
   <type name="Vendor\ModuleName\Observer\MyObserver">
       <arguments>
           <argument name="logger" xsi:type="object">MyCustomLogger</argument>
       </arguments>
   </type>
   ```

   Codice sorgente di `Vendor\ModuleName\Observer\MyObserver` Classe:

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

1. Classe `Vendor\ModuleName\Logger\Handler\ErrorHandler` viene inserito nel `error` gestore `$logger` nella `Vendor\ModuleName\Observer\MyObserver`.

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
   </argument>
   ...
   ```

I messaggi di eccezione sono registrati nel `/var/log/my_custom_logger/error.log` file.

<!-- link definitions -->

[base]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Base.php
[debug]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Debug.php
[exception]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Exception.php
[syslog]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Syslog.php
[system]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/System.php
