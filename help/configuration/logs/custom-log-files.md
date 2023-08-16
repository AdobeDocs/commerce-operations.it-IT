---
title: Scrivi in un file di registro personalizzato
description: Scopri come impostare file di registro personalizzati.
feature: Configuration, Logs
badge: label="Contributo di Atwix" type="Informative" url="https://www.atwix.com/" tooltip="Atwix"
exl-id: 875f45e7-30c9-4b1b-afe9-d1a8d51ccdf0
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# Scrivi in un file di registro personalizzato

Il `Magento\Framework\Logger` Il modulo contiene le seguenti classi di gestori:

| Classe | File di registro |
| ----- | -------- |
| [Magento\Framework\Logger\Handler\Base][base] | - |
| [Magento\Framework\Logger\Handler\Debug][debug] | `/var/log/debug.log` |
| [Magento\Framework\Logger\Handler\Exception][exception] | `/var/log/exception.log` |
| [Magento\Framework\Logger\Handler\Syslog][syslog] | - |
| [Magento\Framework\Logger\Handler\System][system] | `/var/log/system.log` |

È possibile trovarli nel `lib/internal/Magento/Framework/Logger/Handler` directory.

Per l&#39;accesso a un file personalizzato è possibile utilizzare uno dei seguenti approcci:

- Configurare un file di registro personalizzato in `di.xml`
- Configurare un file personalizzato nella classe del gestore di logger personalizzato

## Configurare un file di registro personalizzato in `di.xml`

Questo esempio mostra come utilizzare [tipi virtuali](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) per registrare `debug` messaggi in un file di registro personalizzato anziché standard `/var/log/debug.log`.

1. In `di.xml` del modulo, definire un file di registro personalizzato come [tipo virtuale](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types).

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomDebug" type="Magento\Framework\Logger\Handler\Base">
       <arguments>
           <argument name="fileName" xsi:type="string">/var/log/payment.log</argument>
        </arguments>
   </virtualType>
   ```

   Il `name` valore di `Magento\Payment\Model\Method\MyCustomDebug` deve essere univoco.

1. Definisci il gestore in un altro [tipo virtuale](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) con un `name`:

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
           </argument>
       </arguments>
   </virtualType>
   ```

1. Inietti il `MyCustomLogger` [tipo virtuale](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) nel `Magento\Payment\Model\Method\Logger` oggetto:

   ```xml
   <type name="Magento\Payment\Model\Method\Logger">
       <arguments>
           <argument name="logger" xsi:type="object">Magento\Payment\Model\Method\MyCustomLogger</argument>
       </arguments>
   </type>
   ```

1. La classe virtuale `Magento\Payment\Model\Method\MyCustomDebug` viene iniettato nel `debug` handler del `$logger` proprietà in `Magento\Payment\Model\Method\Logger` classe.

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
   </argument>
   ```

I messaggi di eccezione vengono registrati in `/var/log/payment.log` file.

## Configurare un file di registro personalizzato nella classe del gestore logger

Questo esempio mostra come utilizzare una classe gestore logger personalizzata per registrare `error` messaggi in un file di registro specifico.

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

1. Definisci il gestore per questa classe come [tipo virtuale](https://developer.adobe.com/commerce/php/development/build/dependency-injection-file/#virtual-types) nel file del modulo `di.xml` file.

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

1. In `type` specifica il nome della classe in cui viene inserito il gestore di logger personalizzato. Utilizzare il nome del tipo virtuale del passaggio precedente come argomento per questo tipo.

   ```xml
   <type name="Vendor\ModuleName\Observer\MyObserver">
       <arguments>
           <argument name="logger" xsi:type="object">MyCustomLogger</argument>
       </arguments>
   </type>
   ```

   Codice sorgente di `Vendor\ModuleName\Observer\MyObserver` classe:

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

1. La classe `Vendor\ModuleName\Logger\Handler\ErrorHandler` viene iniettato nel `error` handler del `$logger` proprietà in `Vendor\ModuleName\Observer\MyObserver`.

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
   </argument>
   ...
   ```

I messaggi di eccezione vengono registrati in `/var/log/my_custom_logger/error.log` file.

<!-- link definitions -->

[base]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Base.php
[debug]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Debug.php
[exception]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Exception.php
[syslog]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Syslog.php
[system]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/System.php
