---
title: Interfaccia logger
description: Introduzione all’interfaccia logger.
exl-id: fdb1b431-405a-4c32-aff1-9e50bf0a2c90
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---

# Interfaccia logger

Per iniziare a utilizzare un logger, è necessario creare un&#39;istanza di `\Psr\Log\LoggerInterface`. Con questa interfaccia, è possibile chiamare le seguenti funzioni per scrivere dati nei file di registro:

- [alert()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L43)
- [critical()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L55)
- [debug()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L111)
- [emergenza()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L30)
- [error()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L66)
- [info()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L101)
- [log()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L122)
- [notice()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L89)
- [warning()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L79)

Un modo per farlo è spiegato nel [Registra attività database](../logs/database-activity.md) esempio.

Un altro metodo è il seguente:

```php
class SomeModel
 {
     private $logger;

     public function __construct(\Psr\Log\LoggerInterface $logger)
     {
         $this->logger = $logger;
     }

     public function doSomething()
     {
         try {
             //do something
         } catch (\Exception $e) {
             $this->logger->critical('Error message', ['exception' => $e]);
         }
     }
 }
```

L’esempio precedente mostra che `SomeModel` riceve un `\Psr\Log\LoggerInterface` oggetto utilizzando l&#39;iniezione del costruttore. In un metodo `doSomething`, se si è verificato un errore, viene registrato in un metodo `critical` (`$this->logger->critical($e);`).

[RFC 5424](https://datatracker.ietf.org/doc/html/rfc5424) definisce otto livelli di registro (debug, informazioni, avviso, avviso, errore, critico, avviso e emergenza).
