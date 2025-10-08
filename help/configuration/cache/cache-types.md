---
title: Tipi di cache
description: Scopri come associare i front-end della cache ai tipi di cache in Adobe Commerce. Scopri le tecniche di configurazione e gestione della cache.
feature: Configuration, Cache
exl-id: 67d4ba06-b48b-4e1a-a7a8-9830490dfe3d
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 0%

---

# Tipi di cache

I passaggi seguenti descrivono come associare il front-end della cache a un tipo di cache.

## Passaggio 1: definire un front-end della cache

L&#39;applicazione Commerce dispone di una cache front-end `default` che è possibile utilizzare per qualsiasi tipo di [cache](../cli/manage-cache.md#clean-and-flush-cache-types). Questa sezione illustra come definire facoltativamente un front-end della cache con un nome diverso, che è preferibile se si prevede di personalizzare il front-end.

>[!INFO]
>
>Per utilizzare il tipo di cache `default`, non è necessario modificare `env.php`. Modificare il `di.xml` globale di Commerce. Consulta [Opzioni cache di basso livello](cache-options.md).

È necessario specificare un front-end di cache personalizzato `app/etc/env.php` o `app/etc/di.xml` globale di Commerce.

Nell&#39;esempio seguente viene illustrato come definirlo nel file `env.php`, che sostituisce il file `di.xml`:

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

Dove `<unique frontend id>` è un nome univoco per identificare il front-end e `<cache options>` sono opzioni discusse negli argomenti specifici di ciascun tipo di memorizzazione in cache (database, Redis e così via).

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
Se si omette `<frontend_type>`, verrà utilizzato [Magento\Framework\Cache\Core](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Cache/Core.php).

- `<frontend_option>`, `<frontend_option_value>` sono il nome e il valore delle opzioni passate dal framework Commerce come array associativo alla cache front-end al momento della creazione.
- `<backend_type>` è il tipo di cache back-end di basso livello. Specificare il nome di una classe compatibile con `Zend_Cache_Backend` che implementa `Zend_Cache_Backend_Interface`.
- `<backend_option>` e `<backend_option_value>` sono il nome e il valore delle opzioni passate dal framework Commerce come array associativo alla cache back-end al momento della creazione.

Per informazioni aggiornate su Zend, consulta la [documentazione di Laminas](https://docs.laminas.dev/).
