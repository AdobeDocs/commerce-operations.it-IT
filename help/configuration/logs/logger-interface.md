---
title: Interfaccia logger
description: Scopri come utilizzare l’interfaccia di registrazione in Adobe Commerce per la registrazione personalizzata. Scopri l’implementazione di PSR-3 e le funzioni di registro.
feature: Configuration, Logs
exl-id: fdb1b431-405a-4c32-aff1-9e50bf0a2c90
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '125'
ht-degree: 0%

---

# Interfaccia logger

Per iniziare a utilizzare un logger, è necessario creare un&#39;istanza di `\Psr\Log\LoggerInterface`. Con questa interfaccia, è possibile chiamare le seguenti funzioni per scrivere dati nei file di registro:

- [avviso()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L43)
- [critico()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L55)
- [debug()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L111)
- [emergenza()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L30)
- [errore()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L66)
- [info()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L101)
- [log()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L122)
- [avviso()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L89)
- [avviso()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L79)

Un modo per farlo è spiegato nell&#39;esempio dell&#39;[Attività del database di registro](../logs/database-activity.md).

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

L&#39;esempio precedente mostra che `SomeModel` riceve un oggetto `\Psr\Log\LoggerInterface` tramite l&#39;iniezione del costruttore. In un metodo `doSomething`, se si è verificato un errore, viene registrato in un metodo `critical` (`$this->logger->critical($e);`).

[RFC 5424](https://datatracker.ietf.org/doc/html/rfc5424) definisce otto livelli di registro (debug, informazioni, avviso, avviso, errore, critico, avviso ed emergenza).
