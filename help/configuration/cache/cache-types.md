---
title: Tipi di cache
description: Associare i front-end della cache ai tipi di cache.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 0%

---

# Tipi di cache

I passaggi seguenti attraversano l’associazione della cache front-end a un tipo di cache.

## Passaggio 1: Definire un front-end della cache

L’applicazione Commerce ha un `default` frontend della cache utilizzabile per qualsiasi [tipo di cache](../cli/manage-cache.md#clean-and-flush-cache-types). Questa sezione illustra come definire facoltativamente un front-end della cache con un nome diverso, che è preferibile se si prevede di personalizzare il front-end.

>[!INFO]
>
>Per utilizzare `default` tipo di cache, non è necessario modificare `env.php` a tutti; modifica di Commerce globale `di.xml`. Vedi [Opzioni cache a basso livello](cache-options.md).

È necessario specificare un fronte di cache personalizzato `app/etc/env.php` o globale di Commerce `app/etc/di.xml`.

L’esempio seguente mostra come definirlo nel `env.php` , che sostituisce il `di.xml` file:

```php?start_inline=1
'cache' => [
    'frontend' => [
        '<unique frontend id>' => [
             <cache options>
        ],
    ],
    'type' => [
         <cache type 1> => [
             'frontend' => '<unique frontend id>'
        ],
    ],
    'type' => [
         <cache type 2> => [
             'frontend' => '<unique frontend id>'
        ],
    ],
],
```

Dove `<unique frontend id>` è un nome univoco per identificare il tuo front-end e `<cache options>` sono opzioni discusse negli argomenti specifici per ogni tipo di memorizzazione in cache (database, Redis e così via).

## Passaggio 2: Configurare la cache

Puoi specificare le opzioni di configurazione della cache front-end e backend in `env.php` o `di.xml`. Questa attività è facoltativa.

`env.php` esempio:

```php?start_inline=1
'frontend' => <frontend_type>,
'frontend_options' => [
    <frontend_option> => <frontend_option_value>,
    ...
],
'backend' => <backend_type>,
'backend_options' => [
    <backend_option> => <backend_option_value>,
    ...
],
```

dove

- `<frontend_type>` è il tipo di cache front-end a basso livello. Specificare il nome di una classe compatibile con [Zend\Cache\Core](https://framework.zend.com/apidoc/1.7/Zend_Cache/Zend_Cache_Core.html).

   Se ometti `<frontend_type>`, [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) viene utilizzato.

- `<frontend_option>`, `<frontend_option_value>` sono il nome e il valore delle opzioni che il framework Commerce passa come array associativo alla cache front-end al momento della creazione.
- `<backend_type>` è il tipo di cache back-end di basso livello. Specificare il nome di una classe compatibile con [Zend_Cache_Backend](https://framework.zend.com/apidoc/1.7/Zend_Cache/Zend_Cache_Backend/Zend_Cache_Backend.html) e che attua [Interfaccia_Backend_Cache_Zend](https://framework.zend.com/apidoc/1.6/Zend_Cache/Zend_Cache_Backend/Zend_Cache_Backend_Interface.html).
- `<backend_option>` e `<backend_option_value>` sono il nome e il valore delle opzioni che il framework Commerce passa come array associativo alla cache di backend al momento della creazione.
