---
title: Tipi di cache
description: Associa i front-end della cache ai tipi di cache.
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '271'
ht-degree: 0%

---

# Tipi di cache

I passaggi seguenti descrivono come associare il front-end della cache a un tipo di cache.

## Passaggio 1: definire un front-end della cache

L’applicazione Commerce presenta una `default` cache front-end utilizzabile per qualsiasi [tipo di cache](../cli/manage-cache.md#clean-and-flush-cache-types). Questa sezione illustra come definire facoltativamente un front-end della cache con un nome diverso, che è preferibile se si prevede di personalizzare il front-end.

>[!INFO]
>
>Per utilizzare `default` tipo di cache, non è necessario modificare `env.php` affatto; puoi modificare il codice globale di Commerce `di.xml`. Consulta [Opzioni cache di basso livello](cache-options.md).

È necessario specificare una cache front-end personalizzata: `app/etc/env.php` o Commerce&#39;s global `app/etc/di.xml`.

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

Dove `<unique frontend id>` è un nome univoco per identificare il front-end e `<cache options>` sono opzioni descritte negli argomenti specifici di ciascun tipo di memorizzazione in cache (database, Redis e così via).

## Passaggio 2: configurare la cache

È possibile specificare le opzioni di configurazione della cache front-end e back-end in `env.php` o `di.xml`. Questa attività è facoltativa.

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

- `<frontend_type>` è il tipo di cache front-end di basso livello. Specificare il nome di una classe compatibile con `Zend\Cache\Core`.
Se ometti `<frontend_type>`, [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php) viene utilizzato.

- `<frontend_option>`, `<frontend_option_value>` sono il nome e il valore delle opzioni che il framework Commerce trasmette come array associativo alla cache front-end al momento della sua creazione.
- `<backend_type>` è il tipo di cache back-end di basso livello. Specificare il nome di una classe compatibile con `Zend_Cache_Backend` e che implementa `Zend_Cache_Backend_Interface`.
- `<backend_option>` e `<backend_option_value>` sono il nome e il valore delle opzioni passate dal framework Commerce come array associativo alla cache back-end al momento della sua creazione.

Consulta la [Documentazione di Laminas](https://docs.laminas.dev/) per informazioni aggiornate su Zend.
