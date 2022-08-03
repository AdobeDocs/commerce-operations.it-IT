---
title: Interfaccia logger
description: Inizia a usare l’interfaccia logger.
source-git-commit: f489c3e68c91c6f2e16bff233cf59472ed684b5c
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 0%

---


# Interfaccia logger

Per iniziare a lavorare con un logger, devi creare un&#39;istanza di `\Psr\Log\LoggerInterface`. Con questa interfaccia, è possibile chiamare le seguenti funzioni per scrivere dati sui file di log:

- [alert()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L43)
- [critical()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L55)
- [debug()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L111)
- [Emergency()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L30)
- [error()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L66)
- [info()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L101)
- [log()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L122)
- [Notice()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L89)
- [warning()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L79)

Un modo per farlo è spiegato nel [Attività del database di log](../logs/database-activity.md) esempio.

Segue un altro modo:

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

L&#39;esempio precedente mostra che `SomeModel` riceve un `\Psr\Log\LoggerInterface` oggetto che utilizza l&#39;iniezione del costruttore. In un metodo `doSomething`, se si è verificato un errore, viene registrato a un metodo `critical` (`$this->logger->critical($e);`).

[RFC 5424](https://datatracker.ietf.org/doc/html/rfc5424) definisce otto livelli di log (debug, informazioni, avviso, avviso, errore, critico, avviso e di emergenza).
